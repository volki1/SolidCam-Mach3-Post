# SolidCam-Mach3-Post
## A SolidCam postprocessor for Mach3, supporting 4x and 5x operations

**Use this post at your own risk! Always check the produced code before running it on a real machine!**

Inspired by **bogan**.

Special thanks to **Bruno Silva** - test part modelling and code testing.

CNCZone [discussion link](http://www.cnczone.com/forums/solidcam/255556-cnc.html).


Setup: standard 3 axis mill. A axis rotary, along X or Y.

## Current status :

Here's a video of a part being cut with code generated by this post : 

<a href="http://www.youtube.com/watch?feature=player_embedded&v=4jaPCg0YltA
" target="_blank"><img src="http://img.youtube.com/vi/4jaPCg0YltA/0.jpg" 
alt="video" width="480" height="360" border="10" /></a>

 - 3 axis - working
 - 4 axis - working / for both repositioning moves and 4x toolpaths
 - 5 axis - working
 - Drill cycles - G81 (drill), G82 (drill+dwell), G83 (peck drilling), Cannes: G85, G86, G89 
 - Tapping seems to work
 
## TODO :
 - 4x indexial use may need some more work to avoid unnecessary retracts to clearance. As of now it's safe but can be made faster w/o retracts.
 - Tool offsets and compensation

## Installation and usage notes :
 - Put the .gpp and .vmid files in `C:\Users\Public\Documents\SolidCAM\SolidCAMXXXX\Gpptool`. You need to restart SolidWorks for it to pick up the new files.
 - Usage in SolidCam - Select `Mach3_4X_Y` for CNC-Machine
 - Mach3 setup:
  * Config > General Config - tick `A-axis is angular`, set `IJ mode` to incremental, uncheck all in `Rotational`, possibly also check `G04 dwell in ms`
  * Config > Toolpath - Check `Y-axis` for axis of rotation and enable `A-rotations`. `3d compass` also helps. I recall having issues with `360 wrap around` so check by curring air before destroying an important part.

**Usage : Do set your CoordSyses so that the CS origin is **on** the pivot point (axis of rotation) and X/Y is the axis around which the part revolves**

## PostDevTestMachine
Is a completely new implementation of the post, that uses SolidCam's new kinematics (pos_to_machine=Y).

This is now the one to use. Files in the `/old` directory are kept just for reference. The only version currently available is for machine that has the 4th axis along Y. Should there be interest I will make a version that has the 4th axis parallel to machine X.

*Testers needed - any feedback appreciated.*
