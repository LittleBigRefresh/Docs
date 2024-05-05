# Using Allefresher Vita to connect LBP Vita to custom servers

<include from="Library.topic" element-id="supported-version-notice"/>

Allefresher Vita is a CFW plugin which patches LBP Vita to custom servers. This guide aims to show how to set it up on a modded Vita.

To download Allefresher, you must first visit the [Releases Page](https://github.com/LittleBigRefresh/Allefresher/releases/latest). 
Once you've opened that in your browser, select `Allefresher_vita.suprx` in the files listed.

![Allefresher Artifacts](allefresher-artifacts.png)

Once you have downloaded the CFW plugin, keep it on hand for later.

## Step 1: Jailbreak your device and install a CFW

We can't help you with this directly, but there are various guides out there you can go out and find. We personally recommend the guide on [vita.hacks.guide](https://vita.hacks.guide/). 
We recommend installing the HENkaku Ensō CFW, as that is what we officially support.

After you have jailbroken your Vita, install [VitaShell](https://github.com/TheOfficialFloW/VitaShell/releases/latest).

## Step 2: Start and connect to an FTP server on your Vita

In VitaShell, press "Start", and change the "SELECT button" option to FTP. Press start again and then press select. 
This will tell you the IP you need to type into Windows Explorer's address bar. (e.g. `ftp://192.168.0.100:1337/`).
After pressing enter, you should see the list of files on your Vita.

![vita-windows-ftp.png](vita-windows-ftp.png)

## Step 3: Install iTLS

iTLS is a plugin which enables TLS 1.2 (a more modern encryption standard) on Vita CFW. This is required for Allefresher Vita to function.

Download iTLS from [here](https://github.com/SKGleba/iTLS-Enso/releases/latest/) and transfer it to your Vita through VitaShell, then install it. 
Alternatively, you can also download it using [VitaDeploy](https://vita.hacks.guide/installing-vitadeploy.html).

Run the iTLS installer, and select `Install the full iTLS package`.

## Step 4: Setup Allefresher

In Windows, double-click on `ur0:`, then on `tai`. Copy the downloaded `Allefresher_vita.suprx` file into this folder. 
Next, you want to identify the title ID of your game. This can be done in multiple ways. 
- On the stem of the box, you'll see something along the lines of "PCSF00516" (4 letters followed by 5 numbers), this is your title ID. 
- Look in `ux0:app/` (or wherever your Vita is configured to install games) for one of the following title IDs. If you see one of these items in that folder, then that is your title ID. 
Note that this list is non-exhaustive, if your game's title ID is missing, please let us know!
  - PCSA22018 - US Cartridge
  - PCSA00017 - US Digital
  - PCSA00549 - US Digital (Marvel Super Hero Edition)
  - PCSF00021 - EU Cartridge & EU Digital
  - PCSF00516 - EU Cartridge (Marvel Super Hero Edition)
  - PCSA22106 - Canada Cartridge
  - PCSD00006 - Asia Cartridge
  - VCAS32010 - Asia Cartridge
  - PCSC00013 - JP Digital
  - VCJS10006 - JP Cartridge
  - VCKS62003 - Korea Cartridge

Now that you know your game's title ID, you can go on to the next step. On your Vita, 
stop the FTP server and return to VitaShell's menu.  Then, navigate to `ur0:tai/` and select `config.txt`.

With the file open, scroll to the bottom using the D-Pad, then press triangle, and select "Insert empty line". 
On this new empty line, put an asterisk followed by **your** title ID, this should look something like `*PCSC00013`. 
After you have placed that, make a new line again, and put the following text: `ur0:tai/Allefresher_vita.suprx`

After you are done, you should see something like this, but with your title ID.

![2024-05-04-210838.png](vitashell-after-config-edit.png)

<warning>
Make sure that you do not place the plugin's name under <code>*main</code> or <code>*KERNEL</code>, this could cause your Vita to not turn on. 
If this happens, hold the <code>L</code> button on boot to disable any plugins, then fix the config in VitaShell.
</warning>

### Changing the server you are connecting to

If you are connecting to the official LittleBigRefresh instance, you can ignore this segment, and skip to [Step 5](#step-5-finalize-the-setup).

Allefresher Vita allows the user to specify another server to connect to, although it requires a bit more setup. 

Allefresher will read from a text file named `allefresher.txt` from `ux0:` on your Vita to get the URL to connect with, 
defaulting to the LittleBigRefresh instance if not found. 
This file contains the patching URL for the server you want to connect to. You can get this URL from the server owner.

However, for the game to be able to read this file, you need to install the [ioPlus](https://www.gamebrew.org/wiki/IoPlus_Vita) plugin.
This is because the Vita disallows the game to access files outside its own directory, and Allefresher has the same permissions as the game itself.
ioPlus expands the permissions of the game to allow read/write to arbitrary files, allowing Allefresher to find your config.

## Step 5: Finalize the setup!

Exit out of the VitaShell editor by pressing the correct back button for your region, save the file, then exit VitaShell.
Finally, restart your Vita.

Ensure your game is fully up-to-date, you can do so by pressing triangle twice with the game's bubble selected in the Live Area. 
If the Update History button is present and shows Version 1.22, then your game is fully up-to-date, if not, open the game's live area, 
and press the refresh button at the top of the screen, this will install all the updates for your game.

<include from="Library.topic" element-id="final-patching-message" />