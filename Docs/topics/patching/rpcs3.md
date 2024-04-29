# Using Refresher to patch a game on RPCS3

Refresher has native support for decrypting and patching RPCS3 games. This guide aims to show you how to operate Refresher's RPCS3 patcher. At the end of this, you will be able to select your server of choice inside the game patches menu of RPCS3.

To download Refresher, you must first visit the [Github Page](https://github.com/LittleBigRefresh/Refresher). Once you have opened it in your browser,
navigate to the "Releases" section on the website.

![Where to find the Releases Section on the GitHub.](Refresher-Release-Highlight.png)

Then, pick the download option corresponding to the operating system that is running on your computer.
Refresher currently does not provide built binaries for MacOS due to issues with code signing. To run Refresher on MacOS,
you must build the project yourself via the dotnet toolset.

![Refresher Artifacts](Refresher-Artifacts.png)

Once you have downloaded the built binaries for your operating system,
simply unzip the archive, and you should have an executable.

## Step 1: Enter the location of RPCS3's filesystem

Every copy of RPCS3 has a folder titled `dev_hdd0` containing game files and digital licenses required for Refresher to modify the game. Obviously, you can't patch anything without knowing where anything is, so we need to tell Refresher where this folder is!

If you are on Linux or macOS, this will be automatically detected for you, and you do not need to do anything. On Windows, however, the files aren't at any particular known location. Refresher is unable to read minds at this current point in time, so you'll have to provide this directory.

Here's where it should be:

![A screenshot of Windows File Explorer, browsed to an installation of RPCS3. The dev_hdd0 folder is highlighted.](rpcs3-directory.png)

Once you've found this folder, head back to Refresher and click 'Browse' in the top field. Navigate to this directory and click Select Folder. Click 'Game To Patch' and all the games loaded into RPCS3 should appear.

## Step 2: Fill in the server URL

<include from="Library.topic" element-id="fill-in-server-url"></include>

## Step 3: Set the PPU hash

The PPU hash is how RPCS3 knows which game the patch is meant for, to acquire it, you need to boot up the game, then after it has loaded a bit, search in the RPCS3 log for "PPU executable hash". If it isn't visible in the integrated log window, look for it in your RPCS3.log file.

You can find this log file in the following locations:
- Windows: Right next to `rpcs3.exe`
- Linux: `~/.cache/rpcs3/`
- MacOS: `~/Library/Caches/rpcs3/`

Before placing the PPU hash in Refresher, make sure to remove the `PPU-` prefix. An example of a correct hash would be `a74423ca913fc18e46cfe926db1d48e41f9858a9`, an incorrect hash would look like `PPU-a74423ca913fc18e46cfe926db1d48e41f9858a9`.

## Step 4: Set the game version

This is visible directly in the RPCS3 Game List, and can be copied from there, ex. `01.33`. Make sure to copy it exactly, don't remove leading 0s.

## Step 5: Patch!

When all is set and ready to go, click the patch button. It should decrypt the game, and add a new entry to your game patches menu.

Open up RPCS3, right-click the game and select "Manage Game Patches". Enable the patch titled "Refresher". Now save, apply, and open your game!

![A screenshot of RPCS3, indicating where to go.](rpcs3-patch-manager.png)
