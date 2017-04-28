---
layout: post
categories: other
tags: [Python]
pspecs: [1 day, 1 person]
links:
 - source: https://gist.github.com/wwatkins42/6c1d128391c47e4b8e46bd828f8a086c
 - download: https://gist.github.com/wwatkins42/6c1d128391c47e4b8e46bd828f8a086c/archive/38ab364229e9dba0643a4b1a2c4b96339ceef08c.zip
header: ["https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/poly_3_.png", 98.9]
---

##### Objective:
```
Inspired by this video by Numberphile (https://www.youtube.com/watch?v=kbKtFN71Lfs&t=0s),
I wanted to implement the algorithm to play around with the interesting mathematic
properties that it yields.
```
##### Source code:
``` python
import numpy as np
import math
import matplotlib.pyplot as plt

def convertToPyplotHex(color):
    return '#' + "{0:0{1}x}".format(color, 6)

def setPlotParams(bg):
    color = convertToPyplotHex(0xffffff - bg)
    plt.rcParams['axes.facecolor'] = convertToPyplotHex(bg)
    plt.xlim((-1, 1))
    plt.ylim((-1, 1))
    return color

def createPolygon(sides, radius):
    polygon = np.array([[0, 1]]) * radius
    for n in range(1, sides):
        t = 2.0 * math.pi * (float(n) / sides) + math.pi * 0.5
        x = radius * math.cos(t)
        y = radius * math.sin(t)
        apex = np.array([x, y])
        polygon = np.vstack([polygon, apex])
    polygon = np.vstack([polygon, polygon[0]])
    return polygon

def chaosGame(iterations, sides=3, radius=1, bg="black"):
    color = setPlotParams(bg)
    polygon = createPolygon(sides, radius)
    choice_set = np.random.random_integers(sides, size=(iterations))
    coor = polygon[0]
    observations = np.array([coor])
    for p in choice_set:
        coor = coor + (polygon[p - 1] - coor) * 0.5
        observations = np.vstack([observations, coor])
    plt.scatter(observations[:,0], observations[:,1], s=0.1, color=color, alpha=0.33)
    plt.plot(polygon[:,0], polygon[:,1], linewidth=0.5, color=color)
    plt.show()

chaosGame(50000, sides=6, radius=1, bg=0x0)
```
---
**Usage:**
* `python chaosGame.py`

**Parameters:**

To play around with the program parameters you can edit this line:
``` python
chaosGame(50000, np.array([0, 1]), sides=6, radius=1, bg=0x0)
```
the first argument of the function is the `iterations` of the algorithm,
the second is the `origin` i.e. the initial position at iteration 0, the third
is the number of `sides` of the generated polygon, the fourth the `radius` of
the generated polygon and the fifth and final argument is the `background color`
between "white" and "black".

![](https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/poly_5_.png)
![](https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/poly_6_.png)
