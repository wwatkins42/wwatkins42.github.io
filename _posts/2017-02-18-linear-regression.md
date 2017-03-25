---
layout: post
categories: algorithm
tags: [Python]
---

`1 day`
`1 person`

---
__Subject:__
##### Introduction:
```
Machine learning is a growing field of computer science that may seem a bit complicated
and reserved only to mathematicians. You may have heard of neural networks or
k-means clustering and don’t undersdand how they work or how to code these kinds of
algorithms...

But don’t worry, we are actually going to start with a simple, basic machine learning
algorithm.
```
##### Objectives:
```
The aim of this project is to introduce you to the basic concept behind machine learning.
For this project, you will have to create a program that predicts the price of a car
by using a linear function train with a gradient descent algorithm.

We will work on a precise example for the project, but once you’re done you will be
able to use the algorithm with any other dataset.
```
```
You will implement a simple linear regression with a single feature - in this case, the
mileage of the car.

To do so, you need to create two programs :
  • The first program will be used to predict the price of a car for a given mileage.
    When you launch the program, it should prompt you for a mileage, and then give
    you back the estimated price for that mileage. The program will use the following
    hypothesis to predict the price :
    
    estimatePrice(mileage) = theta0 + (theta1 * mileage)

    Before the run of the training program, theta0 and theta1 will be set to 0.
    
  • The second program will be used to train your model. It will read your dataset
    file and perform a linear regression on the data.
    Once the linear regression has completed, you will save the variables theta0 and
    theta1 for use in the first program.

Note that the estimatePrice is the same as in our first program, but here it uses
your temporary, lastly computed theta0 and theta1.
```
##### Constraints:
```
In this project you are free to use whatever language you want.

You are also free to use any libraries you want as long as they do not do all the work
for you. For example, the use of python’s numpy.polyfit is considered cheating.
```
---
__Installation:__

* `git clone https://github.com/wwatkins42/linear_regression.git`
* `cd ./linear_regression`
* `python train.py`
* `python predict.py`

**Usage:**

Training phase:
* `python train.py [-p] [-r]`

Prediction phase:
* `python predict.py`

**Options:**
* `-p` plot training result.
* `-r` plot training animation.

![linear_regression_screenshot_1](/images/linear-regression-1.png?raw=true "linear_regression")
