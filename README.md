IsoVoxel
========

Generates isometric pixel art from MagicaVoxel .vox files.

Usage
=====

IsoVoxel is a command-line program (though you don't need to be familiar with the command line to use it), and
can be downloaded from this project's [Releases section](https://github.com/tommyettinger/IsoVoxel/releases).

The simplest way to make a bunch of renders (at least on Windows) is to drag and drop a MagicaVoxel .vox file
onto `IsoVoxel.exe` in the File Explorer, which will make a new folder that shares a name with the .vox file.
There will be at least 44 images in that folder once the program finishes rendering in a few seconds. They will
all use "light" outlining, where there is an outline around the image's silhouette and between gaps in space
inside the image, but the color is not a cartoon-style black and is instead a darker version of the nearby voxel
color. You can drag and drop animated .vox files, which will produce multiple frames in the same folder. Frames
will have their file names end with "_00.png", "_01.png", and so on up to the maximum 24 frames with "_23.png".

MagicaVoxel saves its .vox files in the vox/ subfolder of the MagicaVoxel install directory.
You should, of course, have unzipped IsoVoxel.exe from the .zip it is distributed inside before running it.
 
Alternatively, you can customize the rendering somewhat from the command line.
For this, use `IsoVoxel.exe file.vox x y z o`, where the arguments are:
  - file.vox was saved from MagicaVoxel, in the vox/ subfolder usually as mentioned before
  - x, y, and z are the bounds of the model, which can be up to 128, and don't have to match the dimensions given in MagicaVoxel; 
    this can be useful to render multiple models at the same position in the images
  - o is an outline mode, which can be omitted and defaults to `outline=light`:
    - `outline=full` (this makes black outlines around the edge of the model and shading on inner gaps)
	- `outline=light` (which uses the shaded color instead of black for outer outlines)
	- `outline=partial` (which has no outer outlines but keeps shaded inner outlines)
	- `outline=none` (which has no inner or outer outlines).
  - if you don't include x y z it will use the size of the model as set in MagicaVoxel
  - if you don't give a .vox file it defaults to Zombie.vox , which is included
  - if you don't include o it will use light outlining.
  - o can be placed as the last argument even if some or all of x y z have not been included.
  
IsoVoxel will create a subdirectory named after the model (running on Truck.vox will create a folder called Truck, or on
Zombie.vox will make a folder called Zombie) and fill it with 36 images:
  - four for north/south/east/west
  - four for the diagonals between them, rendered at a slightly different perspective (isometric)
  - eight more for a mostly-top-down view of all eight directions, rendered at close to a 45 degree oblique angle as opposed to the "standard isometric pixel art"  26.565 degree angle; an advantage here is that all directions are about the same size and perspective
  - twelve images that are specially-smoothed versions of the N/S/E/W renders at 3 sizes, with Size1, Size2, or Size3 in the name
  - four diagonal-direction (isometric) renders at the normal size but with sloped voxels used to make the hard edges seem softer
  - four more diagonal-direction renders at a much smaller size, but still with sloped voxels; these may be harder to recognize if you have single-voxel details in the original models
If the .vox model is *not* animated, then 8 more renders will be produced:
  - eight images that are each double-sized versions of one of the original eight, with some extra voxels added to smooth jagged areas; these have Big in their name
If the .vox model is animated (and has multiple frames), then the 36 images listed above will be rendered for each frame.

This comes with some .vox models to test on; Red_Fish_Animated.vox allows you to test the animation rendering.

IsoVoxel needs .NET 3.5 or higher (as of the time of writing, the current version available on Windows is at least 4.6), and has been confirmed at least once to work on Mono.

Results
=======

![Tank](http://i.imgur.com/4dHLspK.png)
![Tank](http://i.imgur.com/BCe7tFl.png)
![Tank](http://i.imgur.com/P4H7W7Q.png)
![Tank](http://i.imgur.com/Fr6QpcR.png)
![Truck](http://i.imgur.com/eyKMYSu.png)
![Truck](http://i.imgur.com/RVa17b8.png)
![Truck](http://i.imgur.com/HxFCaaz.png)
![Truck](http://i.imgur.com/G6dkG2J.png)


![Tank](http://i.imgur.com/m2bjFBG.png)
![Tank](http://i.imgur.com/InLx1F4.png)
![Tank](http://i.imgur.com/iSlsC39.png)
![Tank](http://i.imgur.com/d8ubLGe.png)
![Truck](http://i.imgur.com/Vqm9K4a.png)
![Truck](http://i.imgur.com/7m3NETe.png)
![Truck](http://i.imgur.com/0f6jUdQ.png)
![Truck](http://i.imgur.com/Z6kjLN9.png)
![Red Fish](https://raw.githubusercontent.com/tommyettinger/IsoVoxel/master/RedFish.gif)
