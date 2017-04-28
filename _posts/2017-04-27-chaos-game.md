---
layout: post
categories: other
tags: [Python]
pspecs: [1 day, 1 person]
links:
 - source: https://gist.github.com/wwatkins42/6c1d128391c47e4b8e46bd828f8a086c
 - download: https://gist.github.com/wwatkins42/6c1d128391c47e4b8e46bd828f8a086c/archive/38ab364229e9dba0643a4b1a2c4b96339ceef08c.zip
---

##### Objective:
```
Inspired by this [video](https://www.youtube.com/watch?v=kbKtFN71Lfs&t=0s) by Numberphile, I wanted
to implement the algorithm to play around with the interesting mathematic properties it yields.
```
##### Source code:
``` python
import numpy as np
import math
import matplotlib.pyplot as plt

def setPlotParams(bg):
    color = "white"
    if bg == "black":
        plt.rcParams['axes.facecolor'] = 'black'
    else:
        plt.rcParams['axes.facecolor'] = 'white'
        color = "black"
    plt.xlim((-1, 1))
    plt.ylim((-1, 1))
    return color

def createPolygon(sides, radius):
    polygon = np.array([[0, 1]])
    for n in range(1, sides):
        t = 2.0 * math.pi * (float(n) / sides) + math.pi * 0.5;
        x = radius * math.cos(t)
        y = radius * math.sin(t)
        apex = np.array([x, y])
        polygon = np.vstack([polygon, apex])
    polygon = np.vstack([polygon, polygon[0]])
    return polygon

def chaosGame(iterations, coor, sides=3, radius=1, bg="black"):
    color = setPlotParams(bg)
    polygon = createPolygon(sides, radius)
    choice_set = np.random.random_integers(sides, size=(iterations))
    observations = np.array([coor])

    for p in choice_set:
        coor = coor + (polygon[p - 1] - coor) * 0.5
        observations = np.vstack([observations, coor])

    print(polygon)
    plt.scatter(observations[:,0], observations[:,1], s=0.5, color=color, alpha=0.33)
    plt.plot(polygon[:,0], polygon[:,1], linewidth=0.5, color=color)
    plt.show()

chaosGame(50000, np.array([0, 1]), sides=6, radius=1, bg="black")
```
---
**Usage:**
* `python chaosGame.py`

**Options:**

To play around with the program parameters you can edit this line:
``` python
chaosGame(50000, np.array([0, 1]), sides=6, radius=1, bg="black")
```
the first argument of the function is the `iterations` of the algorithm,
the second is the `origin` i.e. the initial position at iteration 0, the third
is the number of `sides` of the generated polygon, the fourth the `radius` of
the generated polygon and the fifth and final argument is the `background color`
between "white" and "black".


![](https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/poly_3.png)
![](https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/poly_5.png)
![](https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/poly_6.png)

