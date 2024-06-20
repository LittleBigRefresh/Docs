# Using Allefresher to connect LBP Vita/LBP PSP to custom servers on Vita

<include from="Library.topic" element-id="supported-version-notice"/>

Allefresher is a set of CFW plugins which patches LBP to custom servers. 
This guide aims to show how to set it up on a modded Vita using AutoPlugin2.

## Step 1: Jailbreak your device and install a CFW

We can't help you with this directly, but there are various guides out there you can go out and find. We personally recommend the guide on [vita.hacks.guide](https://vita.hacks.guide/). 
We recommend installing the HENkaku Ensō CFW, as that is what we officially support.

## Step 2: Install AutoPlugin2

<note>If you already have AutoPlugin2 installed, you can skip right to <a anchor="step-3-install-allefresher">Step 3</a>.</note>

After you have jailbroken your Vita, we need to install [AutoPlugin2](https://github.com/ONElua/AutoPlugin2/releases/latest). 
We will be doing this using [VitaShell](https://github.com/TheOfficialFloW/VitaShell/releases/latest), which you can download through VitaDeploy.

Open VitaShell, and press <shortcut>← + O</shortcut>, this will open up the camera to scan the QR code below. 
After scanning the QR code, it should ask "Do you want to install this package?" with a URL starting with `https`.

<warning>
If it does not say exactly "Do you want to install this package", 
then try to scan again after lowering your display's brightness, 
you can also try placing the QR code on a different display, such as your phone.
</warning>

<img alt="images/autoplugin-qr-code.png" height="512" src="autoplugin-qr-code.png" width="512" style="block"/>

When it asks you if you want to install this package, say "Yes."
Once it is done downloading, it will ask if you want to allow this app to have extended permissions, say "Yes."

## Step 3: Install Allefresher

Close VitaShell and open AutoPlugin2. It should now be in your Live Area. Open it and install any updates it asks you to install.

### Patching LBP Vita

Navigate to the installation menu by selecting `Vita plugins` → `Miscellaneous Plugins` → `LittleBigPlanet Custom Server`.

On this menu, you should see every installed copy of LittleBigPlanet Vita. 
Select the one you want to patch. 
It will install the plugin for that specific copy only. 
Afterward, a green dot should appear at the right of the screen corresponding to the game you patched.
If you don't see your game on this list, make sure the game's updates are installed and then try again.

### Patching LBP PSP

Install the plugin by selecting `PSP plugins` → `PSP plugins for Adrenaline` → `Allefresher by Beyley`.

## Step 4: Finalize the setup!

Exit out of AutoPlugin2 editor by pressing the back button, then select `Exit` on AutoPlugin2's menu.
Finally, restart your Vita.

Now, ensure your game is fully up to date. 

### Updating LBP Vita

Press triangle twice with the game's bubble selected in the Live Area. 
If the Update History button is present and shows Version 1.22, then your game is fully up to date. 
When pressing the refresh button, a yellow arrow button should appear. Press the yellow arrow button to install all the updates for your game.

### Updating LBP PSP

<include from="Library.topic" element-id="check-lbppsp-version" />

<include from="Library.topic" element-id="final-patching-message" />