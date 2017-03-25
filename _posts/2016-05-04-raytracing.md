---
layout: post
categories: graphical
---

`8 weeks`
`4 persons`

---
__Subject:__
##### Introduction:
```
When it comes to render 3 dimensions computer generated images there is 2 possible
approaches: “rasterization”, which is used by almost all graphic engines because of it’s
efficiency and “ray tracing.” The ray tracing method is more extensive and as a result
not adapted to real time but it produces a high degree of visual realism.

Since you mastered the basics with the last project: RT opens the door of your second
ray tracer coded in C, normed, awesome and functionnal.
And if you are all depressed reading this topic, think of the long way already paved by
the lunatics from ILM, Pixar (or any other computer-generated images studio) that all
have deployed infinite creativity to get better in that art) relax, take life easy.
```
##### Objectives:
```
Your goal is to be able, with the help of your program, to generate images according to
Raytracing protocol.

Those computer generated images will each represent a scene, as seen from a specific
angle and position, defined by simple geometric objects, and each with its own lighting
system.

This project will have a mandatory part and many additional options. The mandatory
part is worth 0 points and the options will only bring you points IF the mandatory part
is 100% complete. The project will only be validated if a substantial volume of options
is present when you defend the project.

The elements you need to create are as follows:
• Implement the Ray-Tracing method to create a computer generated image.
• You need at least 4 simple geometric objects as a base (not composed): plane,
  sphere, cylinder and cone.
• Your program must be able to apply translation and rotation transformation to
  objects before displaying them. For example a sphere declared at (0, 0, 0) must
  be able to successfully translate to (42, 42, 42).
• Manage the redraw view without recalculating (basically with MinilibX, you can
  manage the expose properly): if a part of the window needs to be redrawn, it is
  best if you don’t have to recalculate everything.
• Position and direction of any point of vision and of simple objects.
• Light management: different brightness, shadows. multi-spot, shine effect.

Those elements are required in the RTv1 project, that we STRONGLY recommend
that you do prior. For the RT, you won’t have any point (and so no chance to validate
the project) if you only do this.
```
##### Constraints:
```
Within the mandatory part, you are allowed to use only the following libc functions:
◦ open
◦ read
◦ write
◦ close
◦ malloc
◦ free
◦ perror
◦ strerror
◦ exit
◦ All functions of the math library (-lm man man 3 math)
◦ All functions of the MinilibX or their equivalent in another graphic library.
```
##### Bonuses:
```
Now, let’s get to the real deal: the options.

There are many and they don’t really have any limits. We can give as examples:
• Ambiance light
• Direct light
• Parallel light
• Limited objects: parallelograms, disks, half-spheres, tubes etc...
• Bump mapping and color disruption
• External files for scene description
• Reflection
• Transparency
• Shadow modification according to transparency of the elements
• Composed elements: cubes, pyramids, tetrahedrons...
• Textures
• Negative elements
• Limit disruption / transparency / reflection, depending on texture
• More native elements: paraboloid, hyperboloid, tablecloth, toroid...
• ...

Those are the basics stuff, naturally you can be more exotic! You can think for example
of multiple calculations spread over multiple cumputers or you can use quadrics
or quartics, videos clips created from your own images, a stereoscopic version for Oculus
Rift etc...

However, for those of you that might want to parse some .pov or .3ds files, your raytracer
must to be able to manage correctly the simple objects of the mandatory part from
equations and not from facets.

In addition, your defense will require that you do some live manipulations of your
scenes. That will need to be done with your tools and not with 3DS (you will need to have
your own configuration files basically).

A special bonus will be given to the first group that can create a raytracing image
of the Moebius strip (Möbius if you’d rather). From the mathematical equation and not
from facets.
```
---
__Installation:__

* `git clone https://github.com/wwatkins42/RT.git`
* `cd ./RT`
* `./install.sh`
* `make`

**Usage:**
* `./rt [-s file_path] [-w width] [-h height] [--help]`

**Example:**
* `./rt -s resource/scene/bonus/reflection.yml -w 1920 -h 1080`

**Keys:**
* `w` `a` `s` `d`: move around.
* `shift` `space`: move down/up.
* `m`: switch mouse mode.
* `mouse` or  `i` `j` `k` `l`: rotate view.
* `1` `2`: filters invert/gray.
* `numpad +` `numpad -`: zoom in/out.
* `+` `-`: change light intensity.
* `mouse left`: select object (on cursor).
* `ctrl + mouse` or &#8593; &#8592; &#8595; &#8594;: move selected object.
* `cmd + mouse`: rotate selected object.
* `delete`: delete selected object.
* `[` `]`: save scene/screenshot.
* `` ` ``: display stats.
* `esc` quit program.

![objects](https://cloud.githubusercontent.com/assets/16082039/15098030/c97af69c-1530-11e6-9d6f-1b840b07828a.png)
![bump](https://cdn.rawgit.com/wwatkins42/RT/master/resource/images/triplesphere_06_03_2017_10-11-12_06_03_2017_11-50-23.bmp)
![jupiter](https://cloud.githubusercontent.com/assets/16082039/15098031/cc4db0da-1530-11e6-8ddc-bca5896da6c2.png)
![cornellbox_30_03_2016_10-22-45](https://cloud.githubusercontent.com/assets/16082039/14136368/d1102126-f662-11e5-901d-69fbb50cdba8.png)
![wolf](https://cloud.githubusercontent.com/assets/16082039/14987222/633f6cee-114f-11e6-992f-93b768990583.png)
![mirror](https://cloud.githubusercontent.com/assets/16082039/14987224/65d5249e-114f-11e6-8d31-6fe1935c9fbe.png)
![glossy](https://cloud.githubusercontent.com/assets/16082039/14081611/d9028cdc-f50b-11e5-9df1-8a36d23051e8.png)
![triplesphere_17_03_2016_10-08-39](https://cloud.githubusercontent.com/assets/16072194/13849567/0298bb6a-ec57-11e5-95d9-4c392deb8df5.jpg)
![screen shot 2016-04-28 at 11 41 32 am](https://cloud.githubusercontent.com/assets/16082039/14881965/b00bb2c0-0d36-11e6-94da-3c9ab804f484.png)
__Bonus:__
- • Multi cameras
- • Multi lights
- • Reflexion
- • Refraction
- • Specular
- • .yml scene parsing
- • Changeable window width/height
- • Image filters (invert, grayscale, gamma, ...)
- • Exporter yml
- • Exporter bmp
- • Importer bmp (texture loading)
- • Perlin noise (procedural textures)
- • Texture mapping (plane, sphere)
- • Changeable field of view
- • Super-sampling (anti-aliasing)
- • Beer law
- • Error log
- • Texture bilinear filtering
- • Loading infos
- • Loading percentage
- • Line loading display
- • Generate normal-map from texture (sobel filter)
- • Normal mapping
- • Light attenuation with distance
- • Camera movement
- • Camera orientation with mouse
- • Mouse smooth (linear interpolation)
- • Frame per second display
- • Progressive loading
- • Glossy reflection/refractions
- • Soft shadows
- • Stereoscopic camera for 3D view
- • Texture rotation
- • Ascii shell display (--shell option)
