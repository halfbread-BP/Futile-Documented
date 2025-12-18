# Starters
For starters, Futile is a 2D framework built-ontop of Unity for performance reasons, not to actually use the engine in any way (you'd only use Unity's tools for stuff like `Mathf` and low-level API's like `CommandBuffer`, `GL`, `Graphics`, etc.)


This means that if you dont know any Unity scripting, you're completely fine since Futile has almost nothing to do with Unity code-wise (unless you're modifying Futile which you'll most likely do

# Setup
Futile is a deprecated framework however if you fix the various warnings and compile errors you *can* get it to work.
I won't list the fixes and only reserve that for the far future when i actually have a computer, im making this documentation just looking at the source-code, so don't expect *everything* to be given :')
*don't mind how counter-intuitive it is not having a computer and spending so much of my time learning programming...*

* Firstly, you need to copy futile's git repo and drop everything from the Assets folder into your Project file hierarchy.
* Next you have to fix all the compile errors and i also recommend fixing the warnings
* Pray it works
* ...

So to make sure futile works, we have to actually initialize Futile;

Create a MonoBehaviour script:
```
public class ThisScript : MonoBehaviour
{
  FutileParams fparams = new(true, true, false, false); // declares and initializes fparams field of FutileParams object, params in the constructor are just mobile stuff

  fparams.AddResolutionLevel(1920f, 1f, 1f, ""); // this changes what atlas is used depending on the resolution and resourceSuffix (scaling can be applied)

  fparams.origin = new Vector2(0.5f, 0.5f); // sets up origin on coordinate plane. 0.5, 0.5 is set to the middle of the scene, Vector2.Zero is the top left, and 1,1 is the bottom right

  fparams.targetFrameRate = 60; // set the target framerate / FPS Cap. You can do: fparams.targetFrameRate = Display.main.systemDisplayInfo.refreshRate.value; to simulate vsync

  fparams.backgroundColor = Color.black; // background color

  Futile.instance.Init(fparams); initialize FutileParams
  Debug.Log(fparams.backgroundColor.ToString()); // make sure it works
}
```

Then make a GameObject in the scene hierarchy (e.g: Futile), then attach the Script to the GO, and if you included the Log function, you should see the color code for fparams.backgroundColor in the console
