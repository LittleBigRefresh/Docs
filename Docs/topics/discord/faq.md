---
channelId: 1115713043163263027
---
# FAQ

This channel contains answers frequently asked questions we see. If your question isn't answered in this channel, take a peek at our docs site online: <https://docs.littlebigrefresh.com/>

## Does Refresh have an official server?

Yes! On August 26th, 2023, we launched LittleBigRefresh. If you'd like to connect, head on over to <#1144875410786623568>!

## How do I make my own Refresh server?

You can download the latest release from [our GitHub](<https://github.com/LittleBigRefresh/Refresh/releases/latest>). It's as easy as extracting a .zip to a comfortable spot, and running it. Refresh can't update itself, although we announce new releases on its GitHub and communicate releases in our dev channels.

If you'd like to patch to your own server, our own guides should work for that as well. See <#1144875410786623568>.

## What are Bunkum, Refresher, and Allefresher?

[Bunkum](<https://github.com/LittleBigRefresh/Bunkum>) is the name of the server software that runs Refresh - developed by us. It's designed to be easier to use than ASP.NET, while allowing flexibility for games that do strange things. It was born out of frustration when LBP kept violating several internet standards - as a result Bunkum will be more lenient than other servers with these.

[Refresher](<https://github.com/LittleBigRefresh/Refresh>) is the patcher that lets you modify your game to connect to custom servers. It can technically work for other games than just the LBP series, but it is still a work in progress. It aims to be smart, communicating with the server for proper patching instructions via our "AutoDiscover" protocol.

[Allefresher](<https://github.com/LittleBigRefresh/Allefresher>) is a set of CFW plugins which automatically patch a game at startup, this removes the need for you to manually re-patch your game from a PC whenever you want to switch server, allowing you to switch server entirely on-console. Right now, Allefresher exists for PSP and Vita.

## Is PPSSPP supported by Refresh?

Not at the moment, PPSSPP does not support the networking features that LBP uses, so it is unable to connect to custom servers.

## I followed the PSP guide, but my game won't connect!

Make sure to update your game to the latest version v2.0.5, as that is the only version we support. LBP PSP Alpha, or a non-updated version will not work. Additionally, PSN will only work on PSPs running a CFW based on the latest firmware, of which 6.61 is the latest as of writing, so make sure your custom firmware is up-to-date.

If you still can't connect, try asking for help in <#1229318345891778581>!

## My PSP can't connect to my Wi-Fi network, is there any way to still connect?

The PSP does not support modern WPA2 networks.

You can set up a 2.4Ghz hotspot on your phone or computer with no password, and then use that on your PSP. You can also set up a WEP network if you want to use a password, although you should still exercise caution as WPA is still not as secure as WPA2, you should only have that Wi-Fi network on when you are online.

## The PSP web browser crashes in Adrenaline when trying to go to a website!

Try disabling the `reScaler` plugin, as it conflicts with the PSP web browser.

## I get a 403 on connecting!

Make sure you have an account registered [on our website](<https://lbp.littlebigrefresh.com/>).

## Whenever I press the button to accept the EULA, nothing happens!

Make sure RPCN is enabled in RPCS3's settings, the network is connected, and you have an RPCN account, you can find the RPCN setting in the "Network" tab.

## I cant view/publish levels, and the game acts strangely on LBP1 and LBP3, even though I can connect fine!

You likely forgot to use AutoDiscover, which is required on LBP1 and LBP3.

## I can't log in on the site, and I am not receiving any password reset requests!

Your account is likely unactivated, make sure you are able to log in from LBP before trying to log in on the site.

## When I open the patcher, I get strange warnings about cool levels, and I don't see the GUI!

You downloaded Refresh, not Refresher, please read one of our patching guides in <#1144875410786623568>.

## On RPCS3, my game constantly diverges/I cant connect to anyone!

In RPCS3 options, make sure to enable UPnP, you can find this setting in the "Network" tab in RPCS3's config.
