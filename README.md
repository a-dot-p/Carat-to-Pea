# Carat-to-Pea

Using the Discord bot [YAGPDB](https://yagpdb.xyz/) to recreate commands for Blood on the Clocktower text games.

Credit goes to the [Carat](https://github.com/JackKBroome/Carat_BOTC) bot in the Blood on the Clocktower [unofficial server](https://discord.com/invite/botc) for the structure syntax of commands. Commands here mostly follow its formatting for consistency. 

# Features
* manage recruiting and game setup
* track alive/dead status and vote tokens of all players
* run voting & nominations
* set reminders, count votes, send messages to all threads
*Currently only supports 1 game per server*


# Setup

### I. Add YAGPDB
If you haven't already, add [YAGPDB](https://yagpdb.xyz/) to your server. This uses the Custom Commands feature: `17 ` are currently implemented, so 17 custom command slots need to be open. 

### II. Discord Setup
Create a role for the players and note down its ID. Do the same for the Storyteller. Create a channel for each new text game and one permanent channel for the kibitz (spectator chat). 

### III. Adding commands
1. Login to [the bot's control panel](https://yagpdb.xyz/manage)
2. Go to `Custom Commands` > `Commands` . Create a command group for text games to stay organized (and if you have other CCs).
3. For each command you want to add, copy+paste the code exactly as in the files (the ones below need some changes)

