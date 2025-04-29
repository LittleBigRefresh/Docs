# Using Refresher to patch a game on RPCS3

<include from="Library.topic" element-id="supported-version-notice"/>

Refresher has native support for decrypting and patching RPCS3 games. This guide aims to show you how to operate Refresher's RPCS3 patcher. 
At the end of this, you will be able to select your server of choice inside the game patches menu of RPCS3.

<warning>
    <p>
        If you're intending to play on <b>Bonsai</b>, you do not need to follow this guide.
        Instead, follow these steps:
    </p>
    <list>
    <li>
        Run through Step 1 and Step 5, ignoring the steps between.
    </li>
    <li>
        Head to Manage -> Game Patches. If asked to update patches, click Yes.
    </li>
    <li>
        Click the box named "Only show owned games" and search for LittleBigRefresh
        <i>(or search Bonsai, if none are shown)</i>
    </li>
    <li>
        Expand and check all the boxes available.
    </li>
    <li>
        You are now able to play on <b>Bonsai!</b>
    </li>
    </list>
</warning>

<include from="Library.topic" element-id="download-refresher"/>

![A Screenshot of Refresher's RPCS3 patching screen](refresher-rpcs3.png)

## Step 1: Update your game to the latest version

Refresh requires your game to be on the latest version. This is trivial on a real PS3, but not so trivial for RPCS3.

Thankfully, the RPCS3 developers have provided a helpful guide on how to do this:

<a href="https://wiki.rpcs3.net/index.php?title=Help:Installing_Game_Updates>">RPCS3 Wiki: Installing Game Updates</a>

## Step 2: Enter the location of RPCS3's filesystem

<warning>
    <p>
    Ensure your game is on the latest version before proceeding.
    Not updating can cause strange, random issues that are difficult to understand.
    </p>
</warning>

Every copy of RPCS3 has a folder titled `dev_hdd0` containing game files and digital licenses required for Refresher to modify the game. 
Obviously, you can't patch anything without knowing where anything is, so we need to tell Refresher where this folder is!

If you are on Linux or macOS, this will be automatically detected for you, and you do not need to do anything. 
On Windows, however, the files aren't at any particular known location. 
Refresher is unable to read minds at this current point in time, so you'll have to provide this directory.

Here's where it should be:

![A screenshot of Windows File Explorer, browsed to an installation of RPCS3. The dev_hdd0 folder is highlighted.](rpcs3-directory.png)

Once you've found this folder, head back to Refresher and click 'Browse' in the top field. 
Navigate to this directory and click Select Folder. Click 'Game To Patch' and all the games loaded into RPCS3 should appear.

## Step 3: Fill in the server URL

<include from="Library.topic" element-id="fill-in-server-url"/>

## Step 4: Patch!

Now, click the patch button. It should decrypt the game, and add a new entry to your game's patches menu.

Open up RPCS3, right-click the game and select "Manage Game Patches". Enable the patch titled "Refresher".

![A screenshot of RPCS3, indicating where to go.](rpcs3-patch-manager.png)

<include from="Library.topic" element-id="final-patching-message" />

## Step 5: Enable RPCN in RPCS3

To actually *enable* RPCN, you need to adjust some settings in RPCS3. Here's how:

1. Click 'Config' at the top of the RPCS3 main window.
<note>
<p>
If you're using a custom config for your game (marked by a symbol next to the game's name),
right click the game and click 'Change Custom Configuration' instead.
</p>
</note>
2. Go to the 'Network' tab.
3. Set PSN Status to RPCN.
4. Set Network Status to Connected.
5. Set DNS to 8.8.8.8 or 1.1.1.1.
6. Click the checkbox to Enable UPNP.
7. Click Apply and Save.

Your network settings should look like this now:

![A screenshot of RPCS3's network settings, showing the correct options.](rpcs3-network-settings.png)