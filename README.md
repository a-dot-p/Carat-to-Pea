# Carat-to-Pea

Using the Discord bot [YAGPDB](https://yagpdb.xyz/) to recreate commands for Blood on the Clocktower text games.

Credit goes to the [Carat](https://github.com/JackKBroome/Carat_BOTC) bot in the Blood on the Clocktower [unofficial server](https://discord.com/invite/botc) for  the command names and what they are meant to do. Commands here mostly follow its formatting for consistency. 

# Features
* manage recruiting and game setup
* track alive/dead status and vote tokens of all players
* run voting & nominations
* set reminders, count votes, send messages to all threads
*Currently only supports 1 game per server*


# Setup

### I. Add YAGPDB
If you haven't already, add [YAGPDB](https://yagpdb.xyz/) to your server. This uses the Custom Commands feature: `17 ` are currently implemented, so 17 custom command slots need to be open. The built-in database is used to store game info. Any previous data with the userID `1` will be overwritten!

### II. Discord Setup
1. Create a role for the players and note down its ID. Do the same for the Storyteller.
2. Create a channel for each new text game
3. Create a permanent channel for the kibitz (spectator chat). 

### III. Adding commands
1. Login to [the bot's control panel](https://yagpdb.xyz/manage)
2. Go to `Custom Commands` > `Commands` . Create a command group for text games to stay organized (and if you have other CCs).
3. For each command you want to add, copy+paste the code exactly as in the files (the ones below need some changes)
<img width="847" height="367" alt="image" src="https://github.com/user-attachments/assets/99ebe0eb-b27b-4632-8b1d-fb64f735f489" />

(1-1)
* replace all `/1/` with the role ID of the player role (e.g. `/1/` becomes `123456789`)
* replace all `/2/` with the role ID of the ST role

(3-2)
* replace all `/1/` with the role ID of the player role
* replace `/2/` with the channel ID of your kibitz channel

4. Set the trigger type of all commands ***except*** 2-1, 2-3b, 2-3c, 3-4b, 3-4c to `Regex`. The `Trigger` should be `^>commandname`
Feel free to change `>` in the trigger to any prefix of your choice, and `commandname` to any name.
*(e.g. if you want a `!` prefix and the name `nominate`,  make the trigger `^!nominate`)*

(2-1)

* set trigger type to Slash command and call it whatever you want. Set response to `Ephemeral Message Response` . Set up the options like so
  
<img width="1268" height="775" alt="image" src="https://github.com/user-attachments/assets/6aaf7d5f-ef6c-4a0b-84d9-fe5d554e3ae1" />

(2-3b)

* set trigger type to `None`
  
(3-4b)

* set trigger type to `Message Component` and the trigger `^cv-` exactly.
  
(3-4c)

* set trigger type to `Modal Submission` and the trigger `cvModal=` exactly.

5. Make sure YAGPDB has the appropriate permissions to send messages, create threads, pin, etc. Restrict any commands by setting the required roles (your ST role, for example for some of them). 

# Commands Guide
1. Game Setup
   
  1-1: `>text play` or `text st`
  
  adds you to the text game & gives you the role. type again to remove.
    
  1-2: `>list`
  
  see current Storyteller and players list (from 1-1)
     
  1-3: `>setuptownsquare @player1 @player2 ...`
  
  set the order of seats in the town square. **Votes and nominations will not work without this**. Players cannot be added after this point.
     
  1-4: `>kibitz @user1 @user2 ...`
  
  add/remove specified players from kibitz channel.
   
  1-5: `>resettextgame`
  
  resets current game data to start a new one. **Recommended to set required roles of this to the Storyteller role**
     
2. In-Game
   
  2-1: `/privatechat`

  main way to create private threads for whispers. Players should make their own ST thread by marking the ST thread option - necessary to use (2-2).
     
  2-2: `>sendtothreads`
  
  for the ST to send messages inside of all ST threads created by the _player_ using 2-1.
     
  2-3: `>setreminder X`
  
  set a reminder X hours from now & pinging the players 24 - X hours remain. (ex. >setreminder 14 -> ping when 10hrs left
     
  2-3b: command response for the reminders. (need both to work)

  2-4: `>ts (kill | revive | vt) name`
    * kill: marks the player as dead in the town square
    * revive: resets the player to alive
    * vt: removes the (dead) player's vote token
    * name should be exactly as it appears in the town square. Use " " for names with spaces
      e.g. >ts kill "Bob Jones"

3. Voting & Nominations
   
  3-1: `>createnomthread`
  
  for the Storyteller to create a nomination thread each game day.
    
  3-2: `>nom @player accusation`
  
  nominate a player and send an accusation.
    
  3-3: `adddefense nomID defense`
  
  add a defense when you're nominated. nomID is the number at the bottom of each nomination.
    
  3-4: `>countvotes nomID`
  
  for the ST: see & count votes for a particular nomination in kibitz channel.
    
  3-4b: count votes button response
  
  3-4c: count votes modal response (all 3 needed to work).

  3-5: `>privatevote nomID message`
  
  same as normal vote but done privately in ST thread 

  3-6: `>vote nomID message`
  
  vote for a player with the given nomination ID (at the bottom of each nom) and a message ("yes", "no" ...)
  

   
