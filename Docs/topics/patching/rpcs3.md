# Using Refresher to patch a game on RPCS3

<include from="Library.topic" element-id="supported-version-notice"/>

Refresher has native support for decrypting and patching RPCS3 games, including the LittleBigPlanet series.
This guide aims to show you how to operate Refresher's RPCS3 patcher.

<note>
    For the LBP games, Refresher will instead use a new patching method called Patchwork to hook into the game to provide extra security patches.
    It comes with the benefit that it is configurable without a full repatch, with the downside that it only works for select games. 
</note>

<include from="Library.topic" element-id="download-refresher"/>

![A Screenshot of Refresher's RPCS3 patching screen](refresher-rpcs3.png)

## Step 1: Update your game to the latest version

Refresh requires your game to be on the latest version. This is trivial on a real PS3, but not so trivial for RPCS3.

Thankfully, the RPCS3 developers have provided a helpful guide on how to do this:

<a href="https://wiki.rpcs3.net/index.php?title=Help:Installing_Game_Updates>">RPCS3 Wiki: Installing Game Updates</a>

<warning>
    <p>
        It's important that you install each update <b>IN ORDER, ONE AT A TIME</b>. Each update depends on the last.
    </p>
</warning>

## Step 2: Enter the location of RPCS3's filesystem

<warning>
    <p>
        Ensure your game is on the latest version and boots before proceeding.
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

Next, go to Refresher and click either 'Patch LBP1/2/3 for RPCS3' or 'Patch any RPCS3 game' depending on if you're patching an LBP game.
The latter will not work for LBP as it does not include critical security fixes through Patchwork, so beware!
The former creates a patch file. It does not replace the EBOOT - you will have to enable the patch in RPCS3's patch manager!

<include from="Library.topic" element-id="fill-in-server-url"/>

## Step 3.5: Lobby passwords

<include from="Library.topic" element-id="lobby-password"/>

## Step 4: Patch!

Now, click the patch button. It should decrypt the game, patch, then place a new EBOOT and a copy of Patchwork into RPCS3!

<note>
    Other game patches (such as the one to disable score bubbles) will not work for the time being.
</note>

## Step 4.5: Reconfiguring the patch

<include from="Library.topic" element-id="reconfigure-patch" />

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

## Step 6: Connect!
<include from="Library.topic" element-id="final-patching-message" />