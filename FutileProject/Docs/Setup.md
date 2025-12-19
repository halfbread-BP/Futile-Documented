# Introduction
Futile is a code-centric 2D framework for Unity that provides a Flash/Cocos2D-like API.

* Pure code workflow; no Editor usage (or at most little to none)
* Simple scene hierarchy
* Custom sprite-batching for performance
* Heavy use of texture atlases for reducing draw calls

Futile treats Unity as a runtime engine rather than a development environment, Unity is already 'code-centric' which allows you to utilize Unity's performance and cross-platform capabilities while having full control over your game

You'll rarely actually be using Unity's scripting API, so if you dont know much or at all of Unity Scripting, that's totally fine; Futile is very different (unless you're modifying Futile)

NOTE: This documentation assumes you know a solid amount of C#

# Setup
Futile is a deprecated framework however if you fix the various warnings and compile errors you *can* get it to work.
I won't list the fixes and only reserve that for the far future when i actually have a computer, im making this documentation just looking at the source-code, so don't expect *everything* to be given :')
*don't mind how counter-intuitive it is not having a computer and spending so much of my time learning programming...*

## Installation
1. Clone the git repo
2. Create a new 2D Unity project (i recommend Unity 2022.3 or 6.x)
3. Copy the Assets folder into your Unity project
4. Make these folders in Assets/Resources: Atlases, Fonts (you can add more like Images, Audio, ParticleTextures, etc.)
5. Create a Scripts and Shaders folder at the root (Assets/)


## Initial Setup
Ceate your main game script (i like to just call it the name of the game/project). In this example we'll call it `Game.cs`

```
public class Game : MonoBehaviour
{
  void Start()
  {
    FutileParams fparams = new(true, true, false, false);

    fparams.AddResolutionLevel(480f, 1f, 1f, "");
    fparams.AddResolutionLevel(1024f, 2f, 1f, "_2X");
    fparams.AddResolutionLevel(2048f, 4f, 1f, "_4X");

    fparams.origin = new Vector2(0.5f, 0.5f);

    fparams.targetFrameRate = 60;

    fparams.backgroundColor = Color.black;

    Futile.instance.Init(fparams);
    Debug.Log(Futile.instance._futileParams.backgroundColor.ToString()); // make sure Futile initialized
  }
}
```

Then make a GameObject in the scene hierarchy (e.g: Futile), then attach the Script to the GO, and if you included the Log function, you should see the color code for fparams.backgroundColor in the console when running the game

Let's go over these different elements:


`FutileParams fparams = new(bool supportLandscapeLeft, bool supportsLandscapeRight, bool supportsPortrait, bool supportsPortraitUpsideDown)`

We're creating a new field called fparams of the FutileParams object, the parameters are booleans of the different display modes your game supports from mobile, we won't be covering mobile here tho


`fparams.AddResolutionLevel(float maxLength, float displayScale, float resourceScale, string resourceSuffix);`

This creates a new Resolution Level of the parameters you setup, what this does is the game chooses different textures depending on what resolution the display is set to (or something like that)


`fparams.origin = new Vector2(0.5f, 0.5f);`

This sets the origin of the scene. `Vector2.Zero` / `new Vector2(0f, 0f)` means the origin of the scene is at the top left (like MonoGame/FNA), `new Vector2(0.5, 0.5f)` means the origin is at the middle of the screen (like Unity), and `new Vector2(1f, 1f)` is at the bottom right, etc.


`fparams.targetFrameRate = 60;`

This sets the FPS Cap of the game. To simulate Vsync, you can do: `fparams.targetFrameRate = Display.main.systemDisplayInfo.refreshRate.value;`


`fparams.backgroundColor = Color.black;`

This sets the background color of the scene


`Futile.instance.Init(fparams);`

And this initializes futile with the parameters

If everything works fine, congratulations! You now know how to initialize Futile :D
