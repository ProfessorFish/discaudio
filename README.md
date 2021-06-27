# discaudio

# ~~THIS PACKAGE IS BEING DEVELOPED, COME BACK LATER. TO SEE THE FEATURES IT WILL HAVE READ BELOW~~

# This package is in an early open alpha stage

**EXAMPLE CODE:**

            const Discord = require("discord.js");
            
            const disbut = require("discord-buttons");
            
            const discaudio = require("discaudio");
            
            const client = new Discord.Client();
            
            disbut(client);
            
            client.login(process.env.token);


            client.on("ready", ()=>{
                console.log("i am ready")
            })


            client.on("message", async message=>{
            if(message.author.bot)return;
            
            if(message.channel.type === "dm")return;

            discaudio.music(message, client, "]")
            })

**Function:**
This pacakge has one function.

**discaudio.music(message, client, prefix, options)**

**message:** This is the discord message that is defined in the message event listener
**client:** This is your Discord.Client()
**prefix:** This is the prefix that your bot responds to
**options:** There are a variety of options, see below. Options is a JSON.

# Options

**options.defaultVolume:** The volume the music is set to by default
**options.colour:** The colour of all non-customised embeds
**options.timeout:** The amount of time (in milliseconds) that an embed will wait to respond for.

**options.noVCMessage:** Either an embed or a string that is sent when the user is not in a VC and tries to run a command
**options.differentVCMessage:** Either an embed or a string that is sent when the user is in a different VC to the bot and tries to run a command
**options.noSongPlayingMessage:** Either an embed or a string that is sent when the user tries to run a command (e.g. skip) but there is no song playing
**options.noQueueMessage:** Either an embed or a string that is sent when the user runs a command but there is no queue
**options.queueOverMessage:** Either an embed or a string that is sent when the queue finishes
**options.pausedMessage:** Either an embed or a string that is sent when the song is paused
**options.resumedMessage:** Either an embed or a string that is sent when the song is resumed
**options.noURLMessage:** Either an embed or a string that is sent when the user runs the play command but does not provide a query/link to search for
**options.noSongFoundMessage:** Either an embed or a string that is sent when the user runs the play command and the bot cannot find a song matching the query
**options.noVolumeToChangeToMessage:** Either an embed or a string that is sent when the user runs the volume command but doesn't provide a volume to change to
**options.noIndexOfSongToRemoveMessage:** Either an embed or a string that is sent when the user runs the remove command and doesn't provide an index to remove
**options.invalidIndexToRemoveMessage:** Either an embed or a string that is sent when the user runs the remove command and the index they provide is invalid
**options.triedToRemoveTheCurrentSongMessage:** Either an embed or a string that is sent when the user runs the remove command and tries to remove the song that is currently playing
**options.removedSongMessage(songURL, songName):** A function that is executed when the user runs the remove command and successfully removes a song (MUST RETURN AN EMBED OR STRING)
**options.nowPlayingMessage(ytdlJSONofSongData):** A function that is executed when the user runs the nowPlaying command (MUST RETURN AN EMBED OR STRING)
**options.changeVolume(volumeToChangeTo):** A function that is executed when the user runs the volume command (MUST RETURN AN EMBED OR STRING)

# OPTIONS EXAMPLE

This is an example for the options.changeVolume() function:

            function volumeMessage(newVolume){
                return `This is a custom response. The new volume is ${newVolume}`
            }
            options.changeVolume = volumeMessage;

**To see an example of what the options.nowPlayingMessage() ytdlJSONofSongData is then view the following link:**
https://github.com/ProfessorFish/discaudio/blob/main/exampleReturn.json

**FEATURES TO ADD:**
+ ~~Automatic command detection~~
+ ~~Buttons for interaction with embeds~~
+ ~~YouTube searcher (no api key required)~~
+ ~~Customisable emebds~~
+ Playlists
+ Possibly lyrics

**COMMANDS TO DO**:
+ ~~Play - plays a song from link or searches youtube. if no arguments provided it unpauses the music.~~
+ ~~Stop - stops playback and makes the bot leave the voice channel.~~
+ ~~Queue - shows the list of songs in the queue~~
+ ~~Skip - skips the current playing song (There will be an option to make the skip a voteskip by default)~~
+ VoteSkip - starts a vote to skip the current playing song
+ ~~Pause - pauses the currently playing song~~
+ ~~Resume - does the same as play when no arguments provided~~
+ ~~Volume - changes the volume of the player~~
+ And more! I just can't be bothered to write them down.
