# Determining the URL to patch with

In order for LittleBigPlanet to connect to Refresh (or any other custom gameserver), the game's EBOOT must be patched with a http(s) url.

This guide demonstrates how to get this url.

<tldr>
<p><b>TL;DR</b></p>
<p>The URL is your computer's IP at port 10061, e.g. `http://10.0.0.100:10061/lbp`.</p>
<p>If you are running a public instance, then you probably already know what you're doing and can safely skip the rest of the guide.
Just replace your computer's IP with your public IP.</p>
</tldr>

## Grabbing your IP

### Windows

1. Open the Start Menu, type "Network and Sharing Center" and click the first result.
2. In this new window, click on the "Change adapter settings" link on the left side.
3. Right-click on the adapter that you're currently using (e.g. Ethernet or Wi-Fi) and open "Status".
4. In the Status window that opens, click on "Details".
5. Look for the "IPv4 Address" entry in the list of information. This is your computer's local IP address.

### Linux

You should be able to do this through the GUI depending on your desktop environment.
On KDE, it's as easy as clicking the Network icon, expanding your adapter and clicking Details.

Otherwise, at the terminal to grab your IP you can run `ip addr` (or `ifconfig` if you're running an older distribution)

It will print something like this:

```
[jvyden@the-overcooler ~]$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.100/24 brd 10.0.0.255 scope global noprefixroute enp5s0
       valid_lft forever preferred_lft forever
```

You are looking for your IPv4 address of your main network adapter. In my case, it's `enp5s0` as I am on ethernet. It can also be `wlan0` if you are on WiFi. The IP address will be listed next to the `inet` text, in my case `10.0.0.100`. Ignore the `/24` part - that is not relevant.

## Constructing the URL

Refresh by default runs on port 10061 and listens via HTTP. 

So, assuming no configuration changes were made (you'll know if you changed anything) the URL should be `http://(ip):10061/lbp`. 

`/lbp` is where Refresh listens for gameserver requests. It's important to leave this in the url - otherwise Refresh will not understand that LBP clients are trying to talk to it.