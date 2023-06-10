# Using Refresher to patch a game on RPCS3

Refresher has native support for decrypting and patching RPCS3 games. This guide aims to show you how to operate Refresher's RPCS3 patcher.

It also assumes that you've already downloaded Refresher. If you haven't head on over to the [GitHub page](https://github.com/LittleBigRefresh/Refresher) to grab yourself a copy.

![A Screenshot of Refresher's RPCS3 patching screen](https://littlebigrefresh.github.io/Docs/patching/images/refresher-rpcs3.png)

## Step 1: Enter the location of RPCS3's filesystem.

Every copy of RPCS3 has a folder titled `dev_hdd0` containing game files and digital licenses required for Refresher to modify the game. Obviously, you can't patch anything without knowing what anything is, so we need to tell Refresher where this is!

If you are on Linux or MacOS, this will be automatically detected for you, and you do not need to do anything. On Windows, however, the files aren't at any particular known location. Refresher is unable to read minds at this current point in time, so you'll have to provide this directory.

Here's where it should be:

![A screenshot of Windows File Explorer, browsed to an installation of RPCS3. The dev_hdd0 folder is highlighted.](https://littlebigrefresh.github.io/Docs/patching/images/rpcs3-directory.png)

Once you've found this folder, head back to Refresher and click 'Browse' in the top field. Navigate to this directory and click Select Folder. Click 'Game To Patch' and all the games loaded into RPCS3 should appear.