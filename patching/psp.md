# Using Refresher to setup Allefresher on PSP/Vita

Refresher has support for automatically deploying Allefresher onto a PSP or Vita, with the relavent configuration automatically filled out. This will let you connect to a custom server on LittleBigPlanet for the PSP (on PSP, this would be through Adrenaline).

It also assumes that you've already downloaded Refresher. If you haven't, head on over to the [GitHub page](https://github.com/LittleBigRefresh/Refresher) to grab yourself a copy.

![A Screenshot of Refresher's PSP patching screen](https://littlebigrefresh.github.io/Docs/patching/images/refresher-psp.png)

## Step 1: Jailbreak your device and install a CFW

We can't help you with this, but there are various guides out there you can go out and find. We personally recommend the guides on [pspunk](https://www.pspunk.com/psp-cfw/) and [vita.hacks.guide](https://vita.hacks.guide/), for PSP and Vita respectively.

### PSP

Try to use the latest firmware, and we reccomend PRO C over other CFWs, as they have not been thoroughly tested with Allefresher yet. It is possible to dual-boot CFWs, so if you need a CFW such as ARK-4 for other homebrew, we'd reccomend dual-booting PRO C as well until Allefresher is guarenteed to work well on ARK-4.

### Vita

You'll need to setup Adrenaline, and use the latest version of the Adrenaline ePSP firmware (as with PSP, ARK-4 is untested).

## Step 2: Connect your PSP/Vita or Memory Stick to your computer

Connect your console to your computer over USB, or plug your Memory Stick into a card reader.

Mount the drive and open it in your file explorer.

## Step 3: Setup Refresher

Open Refresher, and select "PSP Setup".

Inside Refresher you should see at a dropdown labeled "PSP Drive". In that dropdown, select the correct path. If your console's drive does not appear there, check to make sure it is mounted, and contains a `PSP` or `PSPEMU` folder on it.

> **Note:**
> On Windows, the `PSPEMU` folder is marked as hidden by default, to view it in file explorer you will need to enable viewing hidden files and system folders.

## Step 4: Fill in the server URL

You should have been given a URL by the person operating the server you're trying to connect to. Copy this URL into the second field - the one named 'Server URL'.

Next, hit the button that says 'Autodiscover'. This will trigger Refresher to attempt to connect to the remote server to gather more details and extra patching instructions from it.

Most servers based on Bunkum, most notably Refresh, should support this protocol. Other servers such as Project Lighthouse do not support this protocol.

If successful, Refresher will open a pop-up presenting the information it gathered from the server. Click 'Yes' to accept these settings, and Refresher will automatically do the rest when you patch.

![A dialog box from Refresher, indicating that Autodiscover has been performed sucessfully.](https://littlebigrefresh.github.io/Docs/patching/images/autodiscover-success.png)

> **Note**
> If you are a developer of a custom server for any game, you can read up on our Autodiscover protocol's documentation [here](https://littlebigrefresh.github.io/Docs/autodiscover-api).
>
> We recommend you support it, as it helps users ensure that they are following the correct procedures before they launch the game.

## Step 5: Finalize the setup!

When all is set and ready to go, click the patch button. It should spit out the relavent files onto your console.

Now, safely eject the drive from your computer.

Head on over to your device, and start the game! With some luck and given that you've registered an account on the server, you should now connect.
