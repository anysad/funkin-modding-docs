
# Creating Video Cutscenes

## Video Cutscene Assets

The cutscene assets required should be placed into the `videos` folder within your mod, ideally somewhere organized like a subfolder with the name of the cutscene, however, it is not required to do so.

We'll end up with something like this.

```
-mods
 |-myMod
   |-videos
     |-videos
       |-myCutscene.mp4
   |-_polymod_metadata.json
```

## Using the Cutscene

A custom video cutscene requires creating a new Haxe Script file in the `scripts/songs` folder. Below is an example of a [script](../20-using-hscript/20-02-scripted-classes.md) that utilizes this cutscene type.

```haxe
import funkin.play.song.Song;
import funkin.play.PlayState;
import funkin.Paths;
import funkin.play.cutscene.VideoCutscene;
import funkin.play.cutscene.CutsceneType;

import funkin.play.PlayStatePlaylist;

class MySongSong extends Song {
  var hasPlayedCutscene:Bool;

  public function new() {
    super('mysong');

    hasPlayedCutscene = false;
  }

  public override function onCountdownStart(event:CountdownScriptEvent):Void {
    super.onCountdownStart(event);

    if (!PlayStatePlaylist.isStoryMode) hasPlayedCutscene = true;

    if (!hasPlayedCutscene) {

      hasPlayedCutscene = true;

      event.cancel(); // CANCEL THE COUNTDOWN!

      startVideo();
    }
  }

  function startVideo() {
    VideoCutscene.play(Paths.videos('myCutscene'));
  }

  /**
   * Don't replay the cutscene between restarts.
   */
  function onSongRetry(event:ScriptEvent)
  {
    super.onSongRetry(event);

    hasPlayedCutscene = true;
  }

  /**
   * Replay the cutscene after leaving the song.
   */
  function onCreate(event:ScriptEvent):Void
  {
    super.onCreate(event);

    hasPlayedCutscene = false;
  }
}
```

## Changing Video Cutscene Type

In case you want to change the type of you video cutscene, whether it's `MIDSONG` or `ENDING`, you can easily make it by changing a few lines of code.

1. First of all, you will have to add