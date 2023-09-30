# Using Refresher to patch a game on RPCS3

Refresher has native support for decrypting and patching RPCS3 games. This guide aims to show you how to operate Refresher's RPCS3 patcher.

It also assumes that you've already downloaded Refresher. If you haven't, head on over to the [GitHub page](https://github.com/LittleBigRefresh/Refresher) to grab yourself a copy.

![A Screenshot of Refresher's RPCS3 patching screen](https://littlebigrefresh.github.io/Docs/patching/images/refresher-rpcs3.png)

## Step 1: Enter the location of RPCS3's filesystem

Every copy of RPCS3 has a folder titled `dev_hdd0` containing game files and digital licenses required for Refresher to modify the game. Obviously, you can't patch anything without knowing what anything is, so we need to tell Refresher where this is!

If you are on Linux or MacOS, this will be automatically detected for you, and you do not need to do anything. On Windows, however, the files aren't at any particular known location. Refresher is unable to read minds at this current point in time, so you'll have to provide this directory.

Here's where it should be:

![A screenshot of Windows File Explorer, browsed to an installation of RPCS3. The dev_hdd0 folder is highlighted.](https://littlebigrefresh.github.io/Docs/patching/images/rpcs3-directory.png)

Once you've found this folder, head back to Refresher and click 'Browse' in the top field. Navigate to this directory and click Select Folder. Click 'Game To Patch' and all the games loaded into RPCS3 should appear.

## Step 2: Fill in the server URL

You should have been given a URL by the person operating the server you're trying to connect to. Copy this URL into the second field - the one named 'Server URL'.

Next, hit the button that says 'Autodiscover'. This will trigger Refresher to attempt to connect to the remote server to gather more details and extra patching instructions from it.

Most servers based on Bunkum, most notably Refresh, should support this protocol. Other servers such as Project Lighthouse do not support this protocol.

If successful, Refresher will open a pop-up presenting the information it gathered from the server. Click 'Yes' to accept these settings, and Refresher will automatically do the rest when you patch.

![A dialog box from Refresher, indicating that Autodiscover has been performed sucessfully.](https://littlebigrefresh.github.io/Docs/patching/images/autodiscover-success.png)

> **Note**
> If you are a developer of a custom server for any game, you can read up on our Autodiscover protocol's documentation [here](https://littlebigrefresh.github.io/Docs/autodiscover-api).
>
> We recommend you support it, as it helps users ensure that they are following the correct procedures before they launch the game.


## Step 3: Set the identifier

The identifier field can be anything you want. It determines the filename of the EBOOT that will be saved upon patching, in the case that you want to connect to multiple custom servers for a game.

For example, if you set that field to `test`, the final name will be `EBOOT.test.elf`.

## Step 4: Patch!

When all is set and ready to go, click the patch button. It should decrypt the game, and spit out a working .ELF file. Note the path of this file - you will need it later.

Open up RPCS3, click `File`, `Boot (S)Elf`, and then `Boot SELF/ELF`. Browse to where the EBOOT you just made is, and double-click the ELF file. The game should fire up, and you'll be ready to go.

![A screenshot of RPCS3, indicating where to go.](https://littlebigrefresh.github.io/Docs/patching/images/rpcs3-boot.png)