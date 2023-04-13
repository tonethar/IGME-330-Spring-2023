# Notes "A" - for [*HW-3 - Link Buddy!*](hw-3.md)


## I. Get Started

- Copy your completed **wc-3** folder (and all the files in it) and name it ***lastName*-*firstInitial*-hw3**
- In the HTML page:
  - 1) change the `<title>` and `<h1>` to "HW-3 - Link Buddy!" (or similar)
  - 2) change the `<h2>` to "Save your links for later!" (or similar)
- In **main.js**:
  - 1) comment out ALL of the existing code except for the "import MyBookmark" code that the top
  - 2) declare a `submitClicked()` arrow function:
    - with a `console.log("submitClicked");` in it
    - and `return false` at the very bottom of the function (IMPORTANT!)
    - note - ALL your functions will be arrow functions
    - write code so that when the **Submit** button is clicked,  `submitClicked()` is called and the log is visible in the console
      - test it
      - why `return false`? Because this button is in a form, we need to stop the default behavior of that form, which is to "submit" the data by reloading the page - https://www.geeksforgeeks.org/when-to-use-preventdefault-vs-return-false-in-javascript/
   - 3) declare a `clearFormFields()` arrow function
     - write code that "clears" any values that were typed into the form fields (hint: `.value=""`)
     - write code so that when the **Cancel** button is clicked, `clearFormFields()` is called
