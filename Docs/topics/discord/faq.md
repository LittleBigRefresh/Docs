---
channelId: 1115713043163263027
---
# FAQ

This channel contains answers frequently asked questions we see. If your question isn't answered in this channel, take a peek at our docs site online: <https://docs.littlebigrefresh.com/>

## Q: Does Refresh have an official server?

Yes! On August 26th, 2023, LittleBigRefresh launched. If you'd like to connect, head on over to <#1144875410786623568>

## Q: How do I make my own Refresh server?

You can download the latest release from our GitHub. It's as easy as extracting a .zip to a comfortable spot, and running it.

Refresh can't update itself, although we announce new releases in <#1049226545916551188>.

If you use RPCS3, we do have a guide for it available here: <https://docs.littlebigrefresh.com/patching/rpcs3>

## Q: What are Bunkum and Refresher?

Bunkum is the name of the server software that runs Refresh - developed by us. It's designed to be easier to use than ASP.NET, while allowing flexibility for games that do strange things.

It was born out of frustration when LBP kept violating several internet standards - as a result Bunkum will be more lenient than other servers with these.

Refresher is the patcher that lets you modify your game to connect to custom servers. It can technically work for other games than just the LBP series, but it is still a work in progress.

It aims to be smart, communicating with the server for proper patching instructions via our "AutoDiscover" protocol.

## Q: Is PPSSPP supported by Refresh?

Not at the moment. PPSSPP support is in the works, but is currently not possible.

## Q: I followed the PSP guide, but my game wont connect, how do I fix it?

Make sure to update your game to the latest version v2.0.5, as that is the only version we support. LBP PSP Alpha, or a non-updated version will not work. Also make sure to update your PSP to a CFW based on 6.61. If you still cannot connect, ask for help in <#1049223665998372947>.

## Q: My PSP can't connect to my WiFi network, is there any way to still connect?

You can setup a 2.4G hotspot on your phone or computer with no password, then use that on your PSP.

## Q: The Vita web browser crashes when trying to go to a website, how do I fix this?

You should try disabling the `reScaler` plugin, as it conflicts with the PSP web browser.
