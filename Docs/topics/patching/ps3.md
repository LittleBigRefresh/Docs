# Using Refresher to patch a game on PS3

<include from="Library.topic" element-id="supported-version-notice"/>

Refresher has native support for decrypting, encrypting and patching PS3 games. This guide aims to show you how to operate Refresher's PS3 patcher.

<include from="Library.topic" element-id="download-refresher"/>

![A Screenshot of Refresher's PS3 patching screen](refresher-ps3.png)

## Step 1: Jailbreak your PS3 and install webMAN

We can't help you with this, but there are various guides out there you can go out and find. We personally recommend [MrMario2011's guides](https://www.youtube.com/c/MrMario2011).

In general, though, try to use the latest firmware, use HEN for super slims, CFW for other models, etc., etc.

Once you've gotten a modded firmware up and running, head on over to GitHub and [download the webMAN-MOD installer](https://github.com/aldostools/webMAN-MOD/releases/latest).

![webman-download.png](webman-download.png)

Move the installer .pkg onto your PS3, and use your PS3's package manager to get the installer on your PS3, then run it to install webMAN-MOD onto your system.

## Step 2: Find your PS3's IP Address

Head on over to your PS3, head to settings, then network settings, and open 'Settings and Connection Status List'.

![A screenshot of the PS3, showing the mentioned menu.](ps3-ip.png)

Look for your 'IP Address', and write it down under the 'PS3s IP' field in Refresher.
Click the 'Connect' button, and Refresher should connect to your PS3. It may take a couple of seconds for it to download all the game icons and metadata.

## Step 3: Fill in the server URL

<include from="Library.topic" element-id="fill-in-server-url"/>

## Step 4: Patch!

Now, click the patch button. It should decrypt the game, patch, then place a working EBOOT onto your PS3.

<include from="Library.topic" element-id="final-patching-message" />