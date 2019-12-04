# DemoFX
Oldschool demo effects in C#

Look ma no frameworks!

A project of dubious value to recreate some classic demo effects in C#, mainly ones you don't see very often. Done entirely in GDI+, no frameworks or OpenGL, just oldschool pixel pushing.

Salient points:
- this is a mess
- we use reflection to pull out all demo classes that inherit from iDemo. Thus the interface's only purpose is to allow me to identify which classes are effects and which aren't. Once we have the classes, we create an instance of them and invoke the necessary methods. So that part is at least kind of extensible
- the problem is that all drawing is done from the DrawScreen class, so each effect class needs delegates to that class. Not so extensible
- we roll our own texture methods. Stick a texture in the resources file, then read the pixel values into a [,] array, stick them wherever you want and live with the bounds checks
- we avoid frameworks (except GDI+) because the old method of demo coding was to push your own pixels
- that being said, we use a standard cast-a-picturebox-to-a-bmp but then we use the FastBitmap class which uses pointers to manipulate the pixels
- few of these effects (or none) are originally mine. Most are collected from the internet over many years and translated from whatever language (usually C or some flavor of pascal with embedded asm, much from HornetArchive) into C#. I'll take credit for the translation and getting them to work, but otherwise full credit for the original algorithms goes to the original authors (whoever those were).
- Caveat: in the old demoscene, figuring out who or what group actually came up with an effect first was not easy to determine. In most cases the PC demoscene reused older effects that had originated in the Amiga scene
- I don't do copper bars. There is no way to do those in managed code, and not really a way to do them in assembly. Those were peculiar to the Amiga copper chip and drawing the bars is not how these were done. Even in assembly the closest I can get is to wait for in al,dx; and al,08h; and change the palette. It produces some cool effects but not really the same thing

Effects include:
- bobs
- rotozoomer
- plasma clouds
- tri-layer plasma
- xor
- waving landscape
- dot tunnel
- fractal
- rotating balls
- shadebobs

<img src="land.png" width="350px"></img> 
<img src="bobs.png" width="350px"></img> 
<img src="rotato.png" width="350px"></img> 
<img src="clouds.png" width="350px"></img> 
<img src="shade.png" width="350px"></img> 
<img src="roto.png" width="350px"></img> 
<img src="triplas.png" width="350px"></img> 
<img src="XOR.png" width="350px"></img> 