# Creating Dialogue Cutscenes

## Dialogue Cutscene Assets

The dialogue assets required should be placed into the `assets/data/dialogue` folder within your mod.

We'll end up with something like this.

```
-mods
 |-myMod
   |-assets
     |-data
       |-dialogue
         |-boxes
           |-myBox.json
         |-conversations
           |-mySong.json
         |-speakers
           |-myCharacter.json
   |-scripts
     |-songs
       |-mySong.hxc
     |-dialogue
       |-boxes
         |-myBox.hxc
   |-_polymod_metadata.json
```

### Dialogue Speakers

A custom dialogue speaker requires creating a new JSON file in the `data/dialogue/speakers` folder. Below is an example of BF-pixel's speaker file, from `data/dialogue/speakers/bf-pixel.json`[^bfspeakersource]

```json
{
  "version": "1.0.0",
  "name": "BF (Pixel)",
  "assetPath": "weeb/bfPortrait",
  "flipX": false,
  "isPixel": true,
  "scale": 5.4,
  "offsets": [-20, 17],
  "animations": [
    {
      "name": "talkEnter",
      "prefix": "Boyfriend portrait enter instance 1",
      "offsets": [0, 0],
      "frameRate": 12
    },
    {
      "name": "talk",
      "prefix": "Boyfriend portrait idle instance 10",
      "offsets": [0, 0],
      "frameRate": 12
    }
  ]
}
```

The available fields are:
- `version`: The version number for the Portrait data file format. Leave this at `1.0.0`.
- `name`: The readable name for the Portrait.
- `assetPath`: The asset to use for the level name in the list of level, relative to the `images` folder in your mod folder.
- `flipX`: Whether to flip the sprites of this animation horizontally in-game.
- `flipY`: Whether to flip the sprites of this animation vertically in-game.
- `isPixel`: Specify whether to display this image as a pixel speaker (disabling texture smoothing). Optional, defaults to `false`.
- `scale`: Specify the size of the speaker relative to the original size. For example, `2.0` makes the sprite twice as big. Defaults to `1.0` if unspecified.
- `offsets`: Some animations may need their positions to be corrected relative to the idle animation.
  - Use an array of two decimal values, the first for horizontal position and the second for vertical position.
- `animations`: A list of animation data objects for the character portrait.

Animation data is structured like so:
- `name`: The internal animation name for the game to use.
- `prefix`: The animation name as specified by your spritesheet.
  - For Sparrow or Packer, check inside the data file to see what each set of frames is named, and use that as the prefix, excluding the frame numbers at the end.
  - For Animate Atlases, use either the frame label or the symbol name of the animation you want to play.
- `offsets`: Some animations may need their positions to be corrected relative to the idle animation.
  - Use an array of two decimal values, the first for horizontal position and the second for vertical position.
- `looped`: Whether to loop this animation in-game. If false, the animation will pause when it ends, until the game commands the character to do something else.
- `flipX`: Whether to flip the sprites of this animation horizontally in-game.
- `flipY`: Whether to flip the sprites of this animation vertically in-game.
- `frameRate`: A frame rate value, defaulting to `24`.
- `frameIndices`: Optionally specify an array of frame numbers (starting at frame 0!) to use from a given prefix for this animation.
  - For example, specifying `[0, 1, 2, 3]` will make this animation only use the first 4 frames of the given prefix.

### Dialogue Conversations

### Dialogue Boxes


[^bfspeakersource]: <https://github.com/FunkinCrew/funkin.assets/blob/main/preload/data/dialogue/speakers/bf-pixel.json>
[^senpaiconvosource]: <https://github.com/FunkinCrew/funkin.assets/blob/main/preload/data/dialogue/conversations/senpai.json>
[^defaultboxsource]: <https://github.com/FunkinCrew/funkin.assets/blob/main/preload/data/dialogue/boxes/default.json>