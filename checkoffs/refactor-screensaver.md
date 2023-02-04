# Checkoff - Refactor the Canvas Screensaver

## I. Start code
- Your starting point will be the completed version. of [PE-04 - Canvas Screensaver](../pe/04/pe-04.md)
- This app is aready up to 200+ lines of code - we need to "clean it up" and do some refactoring

<hr>

## II. Refactor the code!

- Create a folder named ***lastName-firstInitial*-screensaver-refactored**
- Make a copy of ***lastName-firstInitial*-cs-canvas-5.html**
  - name this copy ***lastName-firstInitial*-screensaver-done.html**
  - put the copy in the above folder you just created

### II-A. Meet the 330 coding standard

- Make sure that your HTML and JS is following our [IGME-330 class code standards](../notes/code-style-required-330.md)
  - examples:
  - `<button id="btnPlay">Play</button>` needs to be `<button id="btn-play">Play</button>`
  - `<button id="btnPause">Pause</button>` needs to be `<button id="btn-pause">Pause</button>`
  - `<input type="checkbox" id="cbRectangles">`needs to be `<input type="checkbox" id="cb-rectangles">`
  - etc
- Be sure to refactor your JS (and CSS if necessary) to match the new `id` values
- ***Test the app thoroughly to be sure it still works! Fix things as necessary. And then move on.***

<hr>

### II-B. Arrow functions

- Convert ALL of the functions in the app to [arrow functions](../notes/js-functions.md#vi-b-arrow-function-examples)
  - this included any anonymous and/or "wrapper" functions
- ***Test the app thoroughly to be sure it still works! Fix things and move code as necessary. And then move on.***

<hr>

### II-C. Template Strings

- Replace all instances of *string concatenation* with [template strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
  - for example - in the `getRandomColor()` function (this might be the only ocurrence of *string concatenation* you need to fix)
- ***Test the app thoroughly to be sure it still works! Fix things as necessary. And then move on.***

<hr>

### II-D. External CSS
- Create a folder named **styles**
- Inside of this folder create a file named **default-styles.css**
- `<link>` to this file, and move all of the CSS styles into it

<hr>

### II-E. ES6 Modules

- Convert the app over to ES6 module syntax
  - move all of the JavaScript to **src/main.js**
  - link to this file from your HTML file with a script tad that is type="module" 
    - ex. `<script src="src/main.js" type="module"></script>`
    - get rid of `"use strict"` - you don't need it anymore
    - replace `window.onload=init` with `init()` (the call to `init()` will probably be at the bottom of **main.js**)
    - test the app and be sure it still works
- Now create **utils.js** and move the folling functions to it
  - `getRandomColor()` 
  - `getRandomInt()`
  - `drawRectangle()`
  - `drawArc()`
  - `drawLine()`
