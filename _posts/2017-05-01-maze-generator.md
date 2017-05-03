---
layout: post
categories: other
tags: [Python]
pspecs: [1 day, 1 person]
links:
 - source: https://gist.github.com/wwatkins42/1626bbd090e0dbb6a480d22167bc634b
 - download: https://gist.github.com/wwatkins42/1626bbd090e0dbb6a480d22167bc634b/archive/550e36a3a3cdf1247996fd54a9b99ebcf9481c1c.zip
header: ["https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/mazeGenerator_4.png", 50]
---

##### Objective:
```
Following the last small project (chaos game), I wanted to implement a simple
backtracking algorithm to generate random "perfect" mazes fast enough and with
good complexity.
```
##### Source code:
``` python
import matplotlib.pyplot as plt
import matplotlib.patches as patches
import matplotlib.collections as mc
import numpy as np
import sys

N = 0
S = 1
E = 2
W = 3

def convertDirToVector(direction):
    if direction == N:
        return [0, -1]
    elif direction == S:
        return [0, 1]
    elif direction == E:
        return [1, 0]
    elif direction == W:
        return [-1, 0]

def invertDirAxis(direction):
    if direction in [N, E]:
        return direction + 1
    return direction - 1

class Cell:
    def __init__(self):
        self.walls = np.array([1, 1, 1, 1])
        self.explored = 0

class Maze:
    def __init__(self):
        self.size = None
        self.maze = None
        self.pos = None
        self.openList = []

    def generate(self, size):
        self.size = size
        self.createGoalPoints()
        self.cellAmount = size[0] * size[1]
        self.maze = [[Cell() for i in range(size[0])] for j in range(size[1])]
        self.recursiveBacktracking()

    def createGoalPoints(self):
        axis = np.random.randint(0, 2)
        self.start = np.full(2, np.random.randint(0, self.size[abs(axis - 1)] - 1))
        self.start[axis] = np.random.choice([0, self.size[axis] - 1])
        self.goal = np.full(2, np.random.randint(0, self.size[abs(axis - 1)] - 1))
        self.goal[axis] = abs(self.start[axis] - self.size[axis] + 1)

    def isPassageValid(self, pos, d):
        if ((pos[0] == 0 and d == W) or (pos[1] == 0 and d == N) or
            (pos[0] == self.size[0] - 1 and d == E) or
            (pos[1] == self.size[1] - 1 and d == S)):
            return False
        v = convertDirToVector(d)
        if (self.maze[pos[1] + v[1]][pos[0] + v[0]].explored == 1):
            return False
        return True

    def isDeadEnd(self, pos):
        adjacent = [self.isPassageValid(pos, i) for i in range(4)]
        return not (1 in adjacent)

    def hasUnexploredAdjacentCells(self, pos):
        adjacent = [0, 0, 0, 0]
        if pos[1] != 0:
            adjacent[N] = 1 + self.maze[pos[1] - 1][pos[0]].explored
        if pos[1] != self.size[1] - 1:
            adjacent[S] = 1 + self.maze[pos[1] + 1][pos[0]].explored
        if pos[0] != self.size[0] - 1:
            adjacent[E] = 1 + self.maze[pos[1]][pos[0] + 1].explored
        if pos[0] != 0:
            adjacent[W] = 1 + self.maze[pos[1]][pos[0] - 1].explored
        return (2 in adjacent)

    def createPassageFrom(self, pos):
        d = np.random.randint(4)
        while not self.isPassageValid(pos, d):
            d = np.random.randint(4)
        newPos = pos + convertDirToVector(d)
        self.maze[pos[1]][pos[0]].walls[d] = 0
        self.maze[newPos[1]][newPos[0]].walls[invertDirAxis(d)] = 0
        self.maze[newPos[1]][newPos[0]].explored = 1
        return newPos

    def recursiveBacktracking(self):
        self.pos = np.array([np.random.randint(self.size[0]), np.random.randint(self.size[1])])
        for i in range(self.cellAmount):
            while self.isDeadEnd(self.pos):
                if len(self.openList) > 0:
                    self.pos = self.openList.pop()
            self.pos = self.createPassageFrom(self.pos)
            if self.hasUnexploredAdjacentCells(self.pos):
                self.openList.append(self.pos)

    def plot(self):
        lines = np.empty([self.size[0] * self.size[1] * 4, 2, 2], dtype=float)
        w = 0
        lines[:self.size[0] + 1] = [[(x, 0), (x + 1, 0)] for x in range(self.size[0] + 1)]
        w += x
        lines[w:w + self.size[1] + 1] = [[(0, y), (0, y + 1)] for y in range(self.size[1] + 1)]
        w += y
        for j in range(self.size[1]):
            for i in range(self.size[0]):
                if self.maze[j][i].walls[S] == 1:
                    lines[w] = [(i, j + 1), (i + 1, j + 1)]
                    w += 1
                if self.maze[j][i].walls[E] == 1:
                    lines[w] = [(i + 1, j), (i + 1, j + 1)]
                    w += 1
        fig, ax = plt.subplots(figsize=(16, 9))
        ax.add_collection(mc.LineCollection(lines[:w], color='black', linewidths=1))
        ax.add_patch(patches.Rectangle(self.start, 1, 1, color="#56c10c", alpha=0.8))
        ax.add_patch(patches.Rectangle(self.goal, 1, 1, color="#da0f52", alpha=0.8))
        ax.set_xlim(0, self.size[0])
        ax.set_ylim(0, self.size[1])
        fig.subplots_adjust(left=0.01, right=0.99, bottom=0.01, top=0.99)
        ax.get_xaxis().set_visible(False)
        ax.get_yaxis().set_visible(False)
        plt.show()

size = [64, 36]
if len(sys.argv) > 1 and sys.argv[1].isdigit():
    size[0] = int(sys.argv[1])
if len(sys.argv) > 2 and sys.argv[2].isdigit():
    size[1] = int(sys.argv[2])
maze = Maze()
maze.generate(size)
maze.plot()
```
---
**Usage:**
* `python mazeGenerator.py [width] [height]`

**Options:**
* `width`: is an integer specifying the width of the generated maze.
* `height`: is an integer specifying the width of the generated maze.

**Example:**
* `python mazeGenerator.py 256 144`

![](https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/mazeGenerator_3.png)
![](https://raw.githubusercontent.com/wwatkins42/wwatkins42.github.io/master/images/mazeGenerator_2.png)
