# Refresh Commands

Refresh has the ability to let users type commands into LittleBigPlanet's in-game chat to perform certain actions without bringing up the website.

This page contains a list of them and what they do.

## Command List

- `/forcematch [player name]`: Tells the dive-in system to try to join you with a given player.
- `/clearforcematch`: Restores default dive-in functionality.
  This is done automatically when a room is found, or if you have connected.
- `/griefphotoson`: Enables the ability to use the grief report system to upload photos.
- `/griefphotosoff`: Restores the ability to submit grief reports.
- `/unescapexmlon`: Un-escapes the XML sent to the `/filter` endpoint, 
this allows you to use XML sequences in-game not normally possible, such as putting player icons in magic mouths
- `/unescapexmloff`: Restores normal `/filter` functionality
- `/play [level id]`: Tells the server that you want to play a particular level by the level's ID.
- `/beta`: Switches the token to be `TokenGame.BetaBuild`. Can be used for builds that do not properly identify themselves as beta builds, e.g. deploy.
- `/revoketoken`: Revokes the token in use by the client, essentially forcing the game to redo the handshake with the server. 
This can be used to switch away from beta mode, can also just be generally useful.

## Debug Command List
These are debugging commands for developers that are not available in production instances of Refresh (e.g. LittleBigRefresh).

- `/tokengame [game]`: Sets the requesting token's `TokenGame` to the given id.
  See [the source code](https://github.com/LittleBigRefresh/Refresh/blob/main/Refresh.GameServer/Authentication/TokenGame.cs#L5) for a list of games.
- `/tokenplatform [platform]`: Sets the requesting token's `TokenPlatform` to the given id.
  See [the source code](https://github.com/LittleBigRefresh/Refresh/blob/main/Refresh.GameServer/Authentication/TokenPlatform.cs#L5) for a list of platforms.
- `/notif`: Sends the user an example notification for testing purposes.
