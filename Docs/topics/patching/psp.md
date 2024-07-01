# Using the PSP web browser to install Allefresher PSP

<include from="Library.topic" element-id="supported-version-notice"/>

It is possible to install Allefresher PSP using the PSP's built-in web browser. 
This will allow you to connect to LittleBigRefresh on a modded PSP.

If you prefer a video guide, you can view the video form of this guide [here](https://www.youtube.com/watch?v=Y0Oj16YzQzY).

<warning>This guide is for PSP hardware only! If you are intending to play under Adrenaline, please follow our <a href="vita.md">Vita guide</a>.</warning>

## Step 1: Jailbreak your device and install a CFW

We can't help you with this directly, but there are various guides out there you can go out and find. We personally recommend the guides on [pspunk](https://www.pspunk.com/psp-cfw/).

### Notes on Jailbreaking a PSP

Try to use the latest firmware (6.61 as of writing). 
We recommend PRO-C over other CFWs, as they have not been thoroughly tested with Allefresher yet. 
It is possible to dual-boot CFWs, so if you need a CFW such as ARK-4 for other homebrew, 
we'd recommend dual-booting PRO-C as well until Allefresher is guaranteed to work well on ARK-4.

## Step 2: Go to the browser on your PSP

<note>If you cannot connect your PSP to your main network, try using a password-less hotspot from your computer or phone.</note>

On your PSP's XMB, select `Network` → `Internet Browser`. 
Navigate to the `Address` bar at the top of the screen, and type in `http://psp.littlebigrefresh.com:2095`.
Select `Download Allefresher`, then select `Memory Stick`. If `Memory Stick` is unavailable, select `System Storage` instead.
Do the same for `LittleBigRefresh (Domain)` and `LittleBigRefresh (Format)`. 
This installs the plugin, and sets it up to connect to LittleBigRefresh.

If you are running PRO-C or ME firmware and cannot edit your plugin list, 
you can scroll down on the website and download the `game.txt` file, a pre-setup config file for Allefresher. 
Please note that doing this will clear out all of your enabled plugins.
If you *can* easily edit your plugin list, you can add a new line containing `ms0:/SEPLUGINS/Allefresher.prx 1` to your `game.txt` file located in the `ms0:/SEPLUGINS/` folder to enable the plugin.
If the `ms0:/SEPLUGINS/` directory or the `game.txt` file within doesn't exist, you can create them yourself.

On ARK-4, you can install the plugin using the built-in file manager. 
Navigate to the ARK-4 custom launcher, press <shortcut>△</shortcut>, then go to `Files`. 
Select `SEPLUGINS`, find `Allefresher.prx`, select it to install, and then click on `Game`.

## Step 3: Finalizing the setup

Now, we need to check the version of the game and update if necessary.

<include from="Library.topic" element-id="check-lbppsp-version" />

<include from="Library.topic" element-id="final-patching-message" />