# Using Refresher to patch a game on PS3

Refresher has native support for decrypting, encrypting and patching PS3 games. This guide aims to show you how to operate Refresher's PS3 patcher.

It also assumes that you've already downloaded Refresher. If you haven't, head on over to the [GitHub page](https://github.com/LittleBigRefresh/Refresher) to grab yourself a copy.

![A Screenshot of Refresher's PS3 patching screen](https://littlebigrefresh.github.io/Docs/patching/images/refresher-ps3.png)

## Step 1: Jailbreak your PS3 and install webMAN

We can't help you with this, but there are various guides out there you can go out and find. We personally recommend MrMario2011's guides.

In general, though, try to use latest firmware, use HEN for super slims, CFW for other models, etc., etc.

Once you've gotten a modded firmware up and running, head on over to GitHub and [Download webMAN](https://github.com/aldostools/webMAN-MOD/releases).

Drop the installer .pkg on your PS3, and you should be all set after you run it.

## Step 2: Find your PS3's IP Address

Head on over to your PS3, head to settings, then network settings, and open 'Settings and Connection Status List'.

![A screenshot of the PS3, showing the mentioned menu.](https://littlebigrefresh.github.io/Docs/patching/images/ps3-ip.png)

Look for your 'IP Address', and write it down under the 'PS3s IP' field in Refresher.
Click away from the textbox, and Refresher should start connecting. It may take a couple of seconds for it to download all the game icons and metadata.

## Step 3: Fill in the server URL

You should have been given a URL by the person operating the server you're trying to connect to. Copy this URL into the second field - the one named 'Server URL'.

Next, hit the button that says 'Autodiscover'. This will trigger Refresher to attempt to connect to the remote server to gather more details and extra patching instructions from it.

Most servers based on Bunkum, most notably Refresh, should support this protocol. Other servers such as Project Lighthouse do not support this protocol. Other servers such as Project Lighthouse do not support this protocol.

If successful, Refresher will open a popup presenting the information it gathered from the server. Click 'Yes' to accept these settings, and Refresher will automatically do the rest when you patch.

![A dialog box from Refresher, indicating that Autodiscover has been performed sucessfully.](https://littlebigrefresh.github.io/Docs/patching/images/autodiscover-success.png)

> **Note**
> If you are a developer of a custom server for any game, you can read up on our Autodiscover protocol's documentation [here](https://littlebigrefresh.github.io/Docs/autodiscover-api).
>
> We recommend you support it, as it helps users ensure that they are following the correct procedures before they launch the game.

## Step 4: Patch!

When all is set and ready to go, click the patch button. It should decrypt the game, and spit out a working EBOOT onto your PS3.

Head on over to your PS3, and start the game! With some luck and given that you've registered an account on the server, you should now connect.
