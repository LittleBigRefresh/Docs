# Using Refresher to patch a game on RPCS3

Refresher has native support for decrypting and patching RPCS3 games. This guide aims to show you how to operate Refresher's RPCS3 patcher.

It also assumes that you've already downloaded Refresher. If you haven't, head on over to the [GitHub page](https://github.com/LittleBigRefresh/Refresher) to grab yourself a copy.

![A Screenshot of Refresher's RPCS3 patching screen](https://docs.littlebigrefresh.com/patching/images/refresher-rpcs3.png)

## Step 1: Enter the location of RPCS3's filesystem

Every copy of RPCS3 has a folder titled `dev_hdd0` containing game files and digital licenses required for Refresher to modify the game. Obviously, you can't patch anything without knowing what anything is, so we need to tell Refresher where this is!

If you are on Linux or macOS, this will be automatically detected for you, and you do not need to do anything. On Windows, however, the files aren't at any particular known location. Refresher is unable to read minds at this current point in time, so you'll have to provide this directory.

Here's where it should be:

![A screenshot of Windows File Explorer, browsed to an installation of RPCS3. The dev_hdd0 folder is highlighted.](https://docs.littlebigrefresh.com/patching/images/rpcs3-directory.png)

Once you've found this folder, head back to Refresher and click 'Browse' in the top field. Navigate to this directory and click Select Folder. Click 'Game To Patch' and all the games loaded into RPCS3 should appear.

## Step 2: Fill in the server URL

<include from="Library.topic" element-id="fill-in-server-url"></include>

## Step 3: Set the identifier

The identifier field can be anything you want. It determines the filename of the EBOOT that will be saved upon patching, in the case that you want to connect to multiple custom servers for a game.

For example, if you set that field to `test`, the final name will be `EBOOT.test.elf`.

## Step 4: Patch!

When all is set and ready to go, click the patch button. It should decrypt the game, and spit out a working .ELF file. Note the path of this file - you will need it later.

Open up RPCS3, click `File`, `Boot (S)Elf`, and then `Boot SELF/ELF`. Browse to where the EBOOT you just made is, and double-click the ELF file. The game should fire up, and you'll be ready to go.

![A screenshot of RPCS3, indicating where to go.](https://docs.littlebigrefresh.com/patching/images/rpcs3-boot.png)