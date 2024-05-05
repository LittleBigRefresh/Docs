# Using Refresher to patch a game on RPCS3

<include from="Library.topic" element-id="supported-version-notice"/>

Refresher has native support for decrypting and patching RPCS3 games. This guide aims to show you how to operate Refresher's RPCS3 patcher. 
At the end of this, you will be able to select your server of choice inside the game patches menu of RPCS3.

<include from="Library.topic" element-id="download-refresher"/>

![A Screenshot of Refresher's RPCS3 patching screen](refresher-rpcs3.png)

## Step 1: Enter the location of RPCS3's filesystem

Every copy of RPCS3 has a folder titled `dev_hdd0` containing game files and digital licenses required for Refresher to modify the game. 
Obviously, you can't patch anything without knowing where anything is, so we need to tell Refresher where this folder is!

If you are on Linux or macOS, this will be automatically detected for you, and you do not need to do anything. 
On Windows, however, the files aren't at any particular known location. 
Refresher is unable to read minds at this current point in time, so you'll have to provide this directory.

Here's where it should be:

![A screenshot of Windows File Explorer, browsed to an installation of RPCS3. The dev_hdd0 folder is highlighted.](rpcs3-directory.png)

Once you've found this folder, head back to Refresher and click 'Browse' in the top field. 
Navigate to this directory and click Select Folder. Click 'Game To Patch' and all the games loaded into RPCS3 should appear.

## Step 2: Fill in the server URL

<include from="Library.topic" element-id="fill-in-server-url"/>

## Step 3: Patch!

Now, click the patch button. It should decrypt the game, and add a new entry to your game's patches menu.

Open up RPCS3, right-click the game and select "Manage Game Patches". Enable the patch titled "Refresher".

![A screenshot of RPCS3, indicating where to go.](rpcs3-patch-manager.png)

<include from="Library.topic" element-id="final-patching-message" />