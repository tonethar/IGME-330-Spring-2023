# HW-1 - Technobabble - Ultimate Version

## Overview
- The ultimate version of Technobabble with external JS in an ES6 module, template strings, arrow functions, Ajax, JSON and still mobile friendly
- Your starting point is the "done" version of [PE-01 - Technobabble](../pe/pe-01.md)

<hr>

## I. Be sure that your start code from PE-01 is 100% correct
- See the rubric here:  [PE 01 - Technobabble#iv-rubric](../pe/pe-01.md#iv-rubric)
  - HW grade will be reduced for any missing features, per rubric above

<hr>

## II. Add another button that's only visible at `1408px` width or higher

- See the requirements here: [Technobabble Generator III](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-technobabble-3.md)
  - For the requirement "both buttons MUST call the SAME function - named something like `generateTechno(num)`"
    - you can use the "wrapper function" technique we demoed in class and that you used on the final version of "Greeter"
  - Also, you MUST use a loop to build each line of babble
  - Also, you MUST use [*template strings*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) when building each line of babble
  - PS - When the app starts up, it still needs to show a single random Technobabble to the user. Meaning - don't forget to call `generateTechno(1)` right after the page loads

<hr>

## III. Refactor your HTML/CSS/JS (and Test it!)
- Rename the HTML file to **technobabble-final.html**
- Make sure that your HTML element `id` and `class` values are following the [course coding standards](../notes/code-style-required-330.md), for example:
  - buttons should have ids such as `btn-gen-1` and `btn-gen-5` - NOT ~~`btnGen1`~~ or ~~`btnGen5`~~
  - file and folder names and are all lower case, no spaces, etc
  - variable, function, method and parameter names all begin in a lower case letter
  - `document.querySelector()` and `document.querySelectorAll()` ONLY, NOT ~~`document.getElementById()`~~ etc
- Don't forget to update your CSS and JS to match any `id` values that were changed!
- ***Test the app thoroughly to be sure it still works! Fix things as necessary. And then move on.***

<hr>

## IV. Additional Requirements

1) Convert all JS functions - `init()`, `generateTechno()`, `randomElement()` etc to ES6 arrow functions. You also may need to move your functions to before you call them.

    - ***Test the app thoroughly to be sure it still works! Fix things as necessary. And then move on.***

2) Move the `<script src="src/main.js"></script>` tag to the `<head>` section of the HTML file, and make it `type="module"`

    - In **main.js**, get rid of `"use strict";` - you don't need it anymore
    - ***Test the app thoroughly to be sure it still works! Fix things as necessary. And then move on.***

3) Move the `randomElement()` function to an external JS file named **utils.js** and `export` it from that file

    - At the top of **main.js**, you will `import` the `randomElement()` function
    - Note: `randomElement()` is a good function to move to **utils.js** because it is easily reused, and a "pure function" that does not have any *dependencies* or produce any *side effects*  (unlike `generateTechno()`, which depends on the babble arrays and modifies the DOM)
    - ***Test the app thoroughly to be sure it still works! Fix things as necessary. And then move on.***

4) Delete the contents of the "babble" arrays and move that data to an external JSON file named **babble-data.json**
   
    - Place this JSON file in a folder named **data/**, so that the path to it is **data/babble-data.json**
      - do NOT put this JSON file into your **src/** folder
    - Use a JSON validation tool - like https://jsonlint.com/ - to be sure that your JSON is valid and well-formed
    - Important: structure your JSON data to be a simple as possible - it just needs to contain the 3 arrays of babble - so it can look very similar to the **simple-pet-names.json** in [Ajax-4](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-ajax-4.md#ii-start-files)
    - Use `XHR` to load the  **data/babble-data.json** file - and assign the data to the `words1`, `words2` and `words3` arrays
      - You will probably have a `loadBabble()` function that will be called just ONCE, *after* the page has loaded
        - `loadBabble()` will initiate the download of the JSON file with `xhr.send()`
      - You will probably have a `babbleLoaded()` callback function - which is called later on when `xhr.onload` fires: 
        - `babbleLoaded()` parses the JSON
        - `babbleLoaded()` will initialize the values of the "words" arrays
        - `babbleLoaded()` will then initialize the button click events
        - `babbleLoaded()` will also display some initial "start up" babble when the user first loads the app

<hr>

## V. Submission 

- Name the top level folder that contains all the files **lastName-firstInitial-hw1**
- ZIP and POST to myCourses dropbox

<hr>

## VI. Rubric

| Deduction  | Reason  |
|---|---|
| -1% to ??%  | Section I. see rubric linked above |
| -20%  | Section II. above not complete |
| -5%  | Section III. per code standard violation |
| -5%  | Section IV-1. per function not converted |
| -10%  | Section IV-2. not done |
| -10%  | Section IV-3. not done |
| -30%  | Section IV-4. not done |
| -20%  | Clicking button does not show random babble |
| -20%  | Errors in console  |
| -20%  | App does not display babble when page first loads  |
| -10%  | App loads JSON data every time a button is clicked (instead of just loading it ONCE)  |
| -10%  | App folder is not named **lastName-firstInitial-hw1**  |

