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
  fparams.AddResolutionLevel(1920f, )
}
