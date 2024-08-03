# Cutscene Types

Friday Night Funkin' supports several formats of cutscene types for the game to use them:

- `video`: Pre-rendered video sequences. Videos must be saved in MP4 format. This type of cutscenes can be seen throughout `Week 7` and `Weekend 1`.

- `dialogue`: Interactive text-based cutscenes that utilizes dialogue boxes, character portraits and the dialogue itself. This type of cutscenes can be seen throughout `Week 6`.

- `in-game`: Real-time cutscenes using the game's engine scripting system, either making the player play a specific animation, have a specific sound played, etc. This type of cutscenes can be seen in songs like `Darnell` showing Pico shooting a can Darnell has thrown at him.

The next part of this chapter will describe where to specifically place assets for each of these cutscene types, as well as how to trigger them with scripting.

## Video Cutscene Types

- `STARTING`: The default cutscene type. Plays before the song starts. Starts the countdown after the video is done.

- `MIDSONG`: Plays during the song itself. Currently has no set logic implemented into the base game.

- `ENDING`: Plays after the song is played. Ends the song after the video is done.