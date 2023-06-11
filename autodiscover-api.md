# Autodiscover API Documentation

## Rationale

To verify if a URL points to a custom server and if it is working, Refresher will contact the server.

While this API originated from Refresh, it is intended to be used by any custom server using HTTP.

The Autodiscover API has two main purposes:

1. Verify that the URL the user has given in patching software is correct.
2. Provide extra information on how the patcher should work, and show metadata about the server to the user.
3. Reassure the user that the settings they have chosen are correct.

## Example

Here's an example request to the Autodiscover API:

```http
GET /autodiscover HTTP/1.1
Host: localhost:10061
User-Agent: curl/8.0.1
Accept: */*
 
HTTP/1.1 200 OK
Server: Bunkum
Connection: close
Date: Thu, 11 May 2023 23:22:16 GMT
Content-Type: application/json
Content-Length: 100
 
{"version":2,"serverBrand":"Refresh","url":"http://127.0.0.1:10061/lbp/","usesCustomDigestKey":true}
```

The server MUST reply with JSON data.

The client can also specify a titleId in the request:

`GET /autodiscover?titleId=NPUA80662 HTTP/1.1`

If the server wants to, it can change the output of the `url` parameter based on the given titleId. For example a LBP3 client may require HTTPS, but other clients may not be able to connect via HTTPS. In this case you would want to change to a http(s) URL for those clients.

## Parameters
`version` refers to the schema version of the Autodiscover API. This is not a server version.

### Version 1
`serverBrand`: A friendly name of the server. For Refresh it is simply `Refresh`, but you can put anything you want here. Generally it's the same as `lbpEnvVer`.

`url`: The URL that should be recommended to the client. This is the URL that you or your players will be patching and connecting with.

### Version 2

This version is the same as version 1, with the following addition:

`usesCustomDigestKey`: A boolean, when true it represents that the LBP server will only accept the digest key `CustomServerDigest`. Otherwise, the server is using the default digest key.

## Implementations

So far, there are only a few known implementations of Autodiscover.

- [Bunkum.AutoDiscover](https://www.nuget.org/packages/Bunkum.AutoDiscover), a service for Bunkum to implement the protocol.
- Refresh (via `Bunkum.AutoDiscover`)
- SoundShapesServer (via `Bunkum.AutoDiscover`)
- [ctbxserver](https://github.com/catboxteam/ctbxserver/blob/631adb1a2e08f5afd4663dcff567e3127e9be578/src/routes/Website/main.py#L122) (archived project, commented out)