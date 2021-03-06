MCNSAChat
=========

Cross-server, multi-channel chat plugin.

# Commands

## Player commands

|**Command**|**Permission Node**|**Description**|
|------|:--------------|:----------|
|`/me [message]`|`mcnsachat.player.me`|Emotes your message (will appear as `* you <message>`). Example: `/me needs more diamonds`|
|`/c [channel]`|`mcnsachat.player.move`|Switches to a channel.|
|`/listen [channel]`||Allows to listen to more channels, while typing in another.|
|`/msg [player] [message]`|`mcnsachat.player.msg`|Sends a private message to a player. Works across servers. Aliases: `/w`, `/tell`, `/whisper`|
|`/r [message]`|`mcnsachat.player.msg`|Replies to the last person who messaged you (or whom you messaged)|
|`/cmute [player]`|`mcnsachat.player.mute`|Ignore player's chat and private messages Aliases: `/mute`, `/ignore`.|
|`/list`|`mcnsachat.player.list`|Lists everyone online. Aliases: `/who`, `/playerlist`, `/online`, `/players`|
|`/csearch [player]`||Finds the channel a player is in.|
|`/clist`|`mcnsachat.player.list`|List available channels.|
    
## Moderator commands

|**Command**|**Permission Node**|**Description**|
|------|:--------------|:----------|
|`/cto`|`mcnsachat.admin.timeout`|Get a list of players in timeout|
|`/cto [player]`|`mcnsachat.admin.timeout`|Remove `[player]` from timeout manually|
|`/cto [player] [time] [reason]`|`mcnsachat.admin.timeout`|Put `[player]` in timeout for `[time]` minutes with `[reason]`|
|`/say [message]`|`mcnsachat.admin.say`|Send `[message]` as the server console|
|`/chansay [channel] [message]`|`mcnsachat.admin.console`|Send a message to channel as console.|
|`/clock [player]`|`mcnsachat.admin.lock`|Lock a player in a channel|
|`/cmove [player] [channel]`|`mcnsachat.admin.move`|Move `[player]` into `[channel]`|
|`/creload`|`mcnsachat.admin.reload`|Reload the configuration file|
|`/cnet [on,off,reset]`|`mcnsachat.admin.csccontrol`|`on` turns on multi server mode, `off` turns it off, `reset` resets the connection|

##Channel management

|**Command**|**Permission Node**|**Description**|
|------|:--------------|:----------|
|`/cmode [add,del] [rave,boring,local]`|`mcnsachat.admin.mode`|Add or remove a mode to the channel your in, if registeres. See modes for details.|
|`/cedit alias [string]`|`mcnsachat.admin.modify`|Changes the alias of the channel you’re in. Alias is a short command invoked to send messages to that channel. Example: `/cedit alias m` invoked in `<MOD>` will make `/m` switch to that channel and `/m message` send messages there.|
|`/cedit [readperm,writeperm] [string]`|`mcnsachat.admin.modify`|Changes read and write permissions of the channel you’re in. Example: `/cedit readperm pillowtalk` will require `mcnsachat.read.pillowtalk`. For `writeperm` it would be `mcnsachat.write.pillowtalk`.|
|`/cedit color [colorcode]`|`mcnsachat.admin.modify`|Changes the [color](http://www.minecraftwiki.net/wiki/Formatting_codes#Color_codes) of the name of the channel you’re in.|
|`/cregister [channel]`|`mcnsachat.admin.register`|Registers a channel with the channel manager.|
|`/cdelete [channel]`|`mcnsachat.admin.register`|Delete `[channel]` from the channel manager.|

##MCNSA Fun Commands

Not Implemented yet

# Configuration

config.yml, Main plugin configuration

|**Config**|**Default**|**Description**|
|:------|:--------------|:----------|
|`ShortCode`|`S`|Set the short name of the server. This is displayed in next to the channel name by default|
|`ServerName`|`Survival`|Set the long name for the server. Usually displayed when a player joins and quits|
|`defaultChannel`|`s`|Set the channel a player should be in on first join|
|`defaultListen`|`[S, Server, Global]`|Set the default list of channels a player should be listening to on first join|
|`multiServer`|`false`|Check whether the plugin should attempt to connect to a chatserver|
|`chatServer`||Specify the chatserver address.|
|`chatServerPort`||Specify the chatserver port.|
|`chatServerPassword`||Specify the password for the chatserver.|
|`consoleLogChat`|`true`|Whether to log the chat in the console as well as the chatlog file|
|`consoleLogServers`|`true`|Whether to log chat messages from other servers in console as well as the chatlog file|
|`consoleLogServerInfo`|`true`|Whether to display player joins and quits from another server|
|`hideJoinPlayerList`|`false`|Hide the list of players dsiplayed on join.|
|`displayWelcome`|`true`|Display the welcome prompt for new players.|
|`consoleSender-colour`|`&4`|What colour the console messages are to be displayed in|
|`consoleSender`|`CONSOLE`|What the name of the console is when using `/say`|

# Permissions

|**Permission Node**|**Description**|
|:------|:----------|
|`mcnsachat.read`|Allows players to read chat.|
|`mcnsachat.write`|Allows players to chat.|
|`mcnsachat.read.<name>`|Allows players to chat in a special channel. Permission name is declared in `channels.yml`, via `read_permission`.|
|`mcnsachat.write.<name>`|Allows players to chat in a special channel. Permission name is declared in `channels.yml`, via `write_permission`.|
|`mcnsachat.forcelisten.<name>`|Force players to listen to a channel (example: useful for moderator channel, so mods don't have to explicitly do `/clisten mod`). Permission name is declared in `channels.yml`, via `name`.|
|`mcnsachat.player.cancolour`|Allows to use color (ie: `&c`) and formatting (ie: `&o`) codes in chat. Cannot overwrite `/cmode <channel> BORING`.|
