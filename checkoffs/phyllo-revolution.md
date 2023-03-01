# Checkoff - "Phyllo-Revolution"

## I. Overview
- Mission: Modify the "Phyllo-Classy" assignment to utilize rotation
- Resource: [Canvas 2D Essential Skills #8 - Canvas Transformations](https://github.com/tonethar/IGME-330-Master/blob/master/notes/8-canvas-transformations.md)

<hr>


## II. Create a `RotatingPhylloFlower` class
- Make a copy of your `PhylloFlower` class and name it `RotatingPhylloFlower`
  - if you really want to, you can use class inheritance instead of just copying the entire class (but you don't have to)
  - update the rest of your code (replace `PhylloFlower` with `RotatingPhylloFlower`) and be sure that everything still works
- To get rotations working right, you must first translate the drawing context to the proper location:
  - in your `draw()` functionality, don't add  `this.centerX` and `this.centerY` to the `x` and `y` variables - instead, `ctx.translate()` to `this.centerX` and `this.centerY` BEFORE calling your `drawCircle()` code
- Once the translation is working right, go ahead and `ctx.rotate()`, right BEFORE calling `drawCircle()`

<hr>

## III. Screenshot


<hr>

![screenshot](_images/phyllo-revolution-1.gif)

<hr>


## IV. Submission

- You are free to put the `RotatingPhylloFlower` class in the HTML file, or in a separate JS file
  - if you have multiple HTML & JS files, name your root folder ***lastName-firstInitial*-phyllo-revolution**
  - if you have everything in just 1 HTML file, name the file ***lastName-firstInitial*-phyllo-revolution.html**
- ZIP and post the folder (or file) to myCourses

