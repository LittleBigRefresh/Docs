---
channelId: 1115713043163263027
---
# FAQ

This channel contains answers frequently asked questions we see. If your question isn't answered in this channel, take a peek at our docs site online: <https://docs.littlebigrefresh.com/>

## Does Refresh have an official server?

Yes! On August 26th, 2023, we launched LittleBigRefresh. If you'd like to connect, head on over to <#1144875410786623568>!

## How do I make my own Refresh server?

You can download the latest release from our GitHub. It's as easy as extracting a .zip to a comfortable spot, and running it. Refresh can't update itself, although we announce new releases on its GitHub and communicate releases in our dev channels.

If you'd like to patch for your own server, our own guides should work. See <#1144875410786623568>.

## What are Bunkum and Refresher?

Bunkum is the name of the server software that runs Refresh - developed by us. It's designed to be easier to use than ASP.NET, while allowing flexibility for games that do strange things. It was born out of frustration when LBP kept violating several internet standards - as a result Bunkum will be more lenient than other servers with these.

Refresher is the patcher that lets you modify your game to connect to custom servers. It can technically work for other games than just the LBP series, but it is still a work in progress. It aims to be smart, communicating with the server for proper patching instructions via our "AutoDiscover" protocol.

## Is PPSSPP supported by Refresh?

Not at the moment. PPSSPP support is in the works, but is currently not possible.

## I followed the PSP guide, but my game won't connect!

Make sure to update your game to the latest version v2.0.5, as that is the only version we support. LBP PSP Alpha, or a non-updated version will not work. Additionally, PSN will only work on PSPs running a CFW based on the latest firmware (6.61 is the latest official version as of writing) so make sure your custom firmware is up to date.

If you still can't connect, try asking for help in <#1229318345891778581>!

## My PSP can't connect to my WiFi network, is there any way to still connect?

The PSP does not support modern WPA/WPA2 networks.

You can setup a 2.4Ghz hotspot on your phone or computer with no password, and then use that on your PSP. You can also set up a WEP network if you want to use a password, although you should still use caution as it's still not as secure as WPA2.

## The PSP web browser crashes in Adrenaline when trying to go to a website!

You should try disabling the `reScaler` plugin, as it conflicts with the PSP web browser.
