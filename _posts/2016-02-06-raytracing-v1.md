---
layout: post
categories: graphical
tags: [C]
pspecs: [2 weeks, 1 person]
links:
 - source: https://github.com/wwatkins42/42_C_Projects/tree/master/RTv1
 - download: https://github.com/wwatkins42/42_C_Projects/archive/master.zip
 - clone: https://github.com/wwatkins42/42_C_Projects.git
---

__Subject:__
##### Introduction:
```
For once, the topic is related to the foreword. To succeed, you must fail. That’s why
you will start with some sort of proof-of-concept on the theory of Raytracing. It’s the
objective of RTv1: to get familiar with Ray-Tracing, geometric elements that you will
need to manipulate, the description of the scene... You will therefore succeed or fail this
project, with the end goal to do it again later bigger, better, more beautiful with all
sorts of additional features (it will be the RT, do not start RT if you did not do RTv1,
it would not be reasonable.)

When it comes to render 3 dimensions computer generated images there is 2 possible
approaches: “rasterization”, which is used by almost all graphic engines because of it’s
efficiency and “ray tracing.” The ray tracing method is more extensive and as a result
not adapted to real time but it produces a high degree of visual realism.

Before you can even begin to produce such high quality graphics, you must master
the basics: RTv1 is your first ray tracer coded in C, normed, humble but functionnal.
At least you’ll then be able to show off nice looking pictures to justify the amount of
hours you’re spending at school instead of spending time with your special person :-).
```
##### Objectives:
```
Your goal is to be able, with the help of your program, to generate images according to
Raytracing protocol.
Those computer generated images will each represent a scene, as seen from a specific
angle and position, defined by simple geometric objects, and each with its own lighting
system.
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
• Smallest light management : different brightness, shadows.
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
---
__Installation:__

* `git clone https://github.com/wwatkins42/42_C_Projects.git`
* `cd ./42_C_Projects/RTv1`
* `make`
* `./rtv1`

**Usage:**
* `./rtv1 [file_path] [-w width] [-h height] [-s supersampling] [-g gamma] [-f fov] [-m maxdepth] [-x angle] [-y angle] [-z angle] [--help]`

**Options:**
* `-w` [`window_width`] loads with defined window width.
* `-h` [`window_height`]  loads with defined window height.
* `-s` [`supersampling`] set specified supersampling value.
* `-g` [`gamma`] set specified gamma value.
* `-f` [`fov`] set specified field of view value.
* `-m` [`max_depth`] set specified maximum reflection depth value.
* `-x` [`angle(deg)`] set specified camera angle on x axis.
* `-y` [`angle(deg)`] set specified camera angle on y axis.
* `-z` [`angle(deg)`] set specified camera angle on z axis.
* `--help`  display help text.

**Example:**
* `./rtv1 resource/scene/circlebox.scene -w 1920 -h 1080 -g 0.71 -f 70 -x 38 -y 34 -z 30 -s 2`

**Keys:**
* `esc` quit program.

![rtv1_screenshot_2](https://cdn.rawgit.com/wwatkins42/42_C_Projects/master/screenshots/screenshot_rtv1_2.png "rtv1")
![rtv1_screenshot_1](https://cdn.rawgit.com/wwatkins42/42_C_Projects/master/screenshots/screenshot_rtv1_1.png "rtv1")
![rtv1_screenshot_3](https://cdn.rawgit.com/wwatkins42/42_C_Projects/master/screenshots/screenshot_rtv1_3.png "rtv1")
