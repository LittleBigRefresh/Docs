# Setting up a production server using Bunkum

This guide will go over setting up a server using Bunkum in production. This includes things like [Refresh](https://github.com/LittleBigRefresh/Refresh), and [SoundShapesServer](https://github.com/turecross321/SoundShapesServer).

We will be targeting a Linux server running an already configured nginx server as the reverse proxy.

## Step 1: Download the software

First up, you need to obtain a copy of the server you will be running. Some servers like Refresh will provide a release on GitHub, others will have it as a GitHub Actions artifact. Generally, there should be download instructions in the server's README.

If all else fails, you can compile it yourself using the .NET SDK.

## Step 2: Create a new user

Create a new user on the Linux server. Bunkum does not require root permissions (or really any permissions apart from filesystem and opening ports), so it's best to create a new user to limit the scope of which Bunkum can operate.

This user can be named after the server software (e.g. `refresh`), but for this guide we will be naming it `bunkum`. Let's create the user's home folder in the directory `/var/lib`.

```
# useradd --system --shell /bin/nologin --create-home --base-dir /var/lib bunkum
# echo $?
0
```

If successful, there should be no output. Try accessing the new user's home folder:

```
$ ls /var/lib/bunkum/
ls: cannot open directory '/var/lib/bunkum/': Permission denied
```

Next, lets log in as the new user to verify that it can't access other user's files.

```
$ sudo -u bunkum /bin/bash -i
$ ls /root
ls: cannot open directory '/root': Permission denied
$ ls /home/jvyden
ls: cannot open directory '/home/jvyden': Permission denied
```

The user will not be able to log in as they do not have a password, and their shell points to a program that will immediately exit.

With the user created, we can begin extracting the server we downloaded earlier.

## Step 3: Deploying the software

Generally, programs like this should be deployed in `/opt/`, (with a data directory set with `BUNKUM_DATA_FOLDER`), but for simplicity's sake we will be doing it in our new user's home folder.

It should be as easy as extracting the `.zip` you downloaded earlier. Make sure the executables are in the root folder of the home partition, like so:

```
$ pwd
/var/lib/bunkum
$ ls
librealm-wrappers.so  Refresh.GameServer  Refresh.GameServer.pdb  web
```
Once you've extracted it, you can run the software like so:

```
$ chmod +x Refresh.GameServer
$ ./Refresh.GameServer
```

Once the server has properly initialized, it will generate configuration files. The number can vary depending on the software, but in this guide we will focus on `bunkum.json`, since it will be present for every software based on Bunkum.

This file contains information about hosting the server. It should look something like this:

```json
{
  "Version": 4,
  "ExternalUrl": "http://127.0.0.1:10061",
  "ListenHost": "0.0.0.0",
  "ListenPort": 10061,
  "ThreadCount": 4,
  "UseForwardedIp": false
}
```

The defaults are more oriented for private use cases - across a local home network and such. These are unsuitable for what we will be doing, so let's change and review them.

### Changing the configuration

- Change `ExternalUrl` to wherever you'll be hosting the server. For example, I could change it to `https://bunkum.example.com`.

- `ThreadCount` is the number of worker threads that will be initialized on startup. Tweak this to your liking depending on your expected load.

- `UseForwardedIp` tells Bunkum that it's safe to read client IP addresses from the requests forwarded via the reverse proxy. Set this to `true`.

- Change `ListenHost` to `127.0.0.1`, as we do not want to listen outside the current machine. Our reverse proxy will handle connections from the internet.

The rest are self-explanatory. Once you're satisfied with your configuration, and you've taken a look at the other configurations the server generated, proceed to the next step.

## Step 4. Writing a systemd unit

Let's hook up our Bunkum service to systemd, so we can have the init daemon handle Bunkum instead of running it ourselves. Pop open a text editor, and copy this template:

```ini
[Unit]
Description=<server name>
Documentation=<github url>

[Service]
Type=simple
ExecStart=/var/lib/bunkum/<executable_name>
TimeoutStopSec=15
User=bunkum
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Modify the service to your heart's content, replacing everything in the brackets. For example, one for Refresh might look something like this, saved as `refresh.service`:

```ini
[Unit]
Description=Refresh - A second-generation custom server for LittleBigPlanet.
Documentation=https://github.com/LittleBigRefresh/Refresh

[Service]
Type=simple
ExecStart=/var/lib/bunkum/Refresh.GameServer
TimeoutStopSec=15
User=bunkum
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Save this as `<server-name>.service`. As root, copy this file to `/usr/lib/systemd/system/`. Then, invoke `systemctl` to trigger a reload to tell systemd to parse and register our new service.

```
# systemctl daemon-reload
```

Once again, there should be no output. We can then start the service, and tell it to run on startup:

```
# systemctl enable <server-name>
# systemctl start <server-name>
```

### Step 4.5. Checking if it works

Do a test ping to check that the server is running. Everything should be healthy.

<note>
<p>Some servers might not use Bunkum's health service, so this may not work depending on the server software.</p>
</note>

`$ curl localhost:10061/_health`
```json
{
    "StatusType": "Healthy",
    "Checks":
    [
        {
            "CheckName": "Database",
            "StatusType": "Healthy",
            "Description": "Test took 0ms"
        },
        {
            "CheckName": "General",
            "StatusType": "Healthy",
            "Description": ""
        }
    ]
}
```

## Step 5. Writing an NGINX configuration

TODO, here's an example:

```nginx
server {
        server_name refresh.example.com;

        location / {
                proxy_http_version 1.1;
                proxy_pass http://127.0.0.1:10061;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }

        keepalive_timeout 0;


        listen 443 ssl;

        ssl_certificate /etc/letsencrypt/live/refresh.example.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/refresh.example.com/privkey.pem;
        include /etc/letsencrypt/options-ssl-nginx.conf;
        ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;
}

server {
        server_name refresh.example.com;
        listen 80;

        location / {
                return 301 https://refresh.example.com$request_uri;
        }

        location /lbp/ {
            proxy_http_version 1.1;
            proxy_pass http://127.0.0.1:10061;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
}
```