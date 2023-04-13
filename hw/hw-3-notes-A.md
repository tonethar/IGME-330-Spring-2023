# Notes "A" - for [*HW-3 - Link Buddy!*](hw-3.md)


## I. Get Started

- Copy your completed **wc-3** folder (and all the files in it) and name it ***lastName*-*firstInitial*-hw3**
- In the **HTML page**:
  - 1) change the `<title>` and `<h1>` to "HW-3 - Link Buddy!" (or similar)
  - 2) change the `<h2>` to "Save your links for later!" (or similar)
- In **main.js**:
  - 1) comment out ALL of the existing code except for the "import MyBookmark" code at the top
  - 2) declare a `submitClicked(evt)` arrow function:
    - with a `console.log("submitClicked");` in it
    - and `evt.preventDefault();` in the 2nd to last line of the function (IMPORTANT!)
    - and `return false;` at the very bottom of the function (IMPORTANT!)
    - note - ALL your functions will be arrow functions
    - write code so that when the **Submit** button is clicked,  `submitClicked()` is called and the log is visible in the console
      - test it
      - why `return false;` and  `evt.preventDefault();` at the bottom of the function? Because this button is in a form, we need to stop the default behavior of that form, which is to "submit" the data by reloading the page - https://www.geeksforgeeks.org/when-to-use-preventdefault-vs-return-false-in-javascript/
   - 3) declare a `clearFormFields()` arrow function
     - write code that "clears" any values that were typed into the form fields (hint: `.value=""`)
     - write code so that when the **Cancel** button is clicked, `clearFormFields(evt)` is called
     - also put `return false;` and  `evt.preventDefault();` at the bottom of that function

<hr>

## II. Creating Favorite instances, showing `<my-bookmark>` elements

- Create **favorite.js**
  - and the `Favorite` "model" class - see hints here: [HW-3 - Hints - **favorite.js**](hw-3.md#hints)
  - don't forget to `export`/`import` it
- In **main.js**:
  - 1) declare a variable named `favorites` and have it point at an empty array
  - 2) create a single `Favorite` instance and put it in the `favorites` array - you can use the following values for its 4 properties
  - 3) when you are done, `console.log(favorites);` or use the debugger to verify that you successfully in created the `Favorite` instance

```js
{
  fid: crypto.randomUUID(), // or just hard-code "d2e7e357-1b1f-4eea-b8f9-25af8aa17138"
  text: "RIT", 
  url: "https://www.rit.edu", 
  comments: "A private university located near Rochester, NY."
}
```

- Still in **main.js**: 
  - 1) Implement `createBookmarkComponent(fid, text, url, comments)`
        - this will create a new `<my-bookmark>` element, set its attributes, and add it to `#bookmarks` on the HTML page
        - write some code to test it (when **main.js** loads), and you should see a working `<my-bookmark>` component on the page
        - once it's working, comment out your test code
  - 2) Implement `loadFavoritesFromStorage()`
        - this version will loop through your `favorites` array (which only has one favorite right now) and will call `createBookmarkComponent()`
        - call `loadFavoritesFromStorage()` when **main.js** loads, you should see a working `<my-bookmark>` component on the page (that uses that favorite's data)

<hr>

## III. Get the Submit button working

- Write code in `submitClicked()` that:
  - grabs the input from the 3 form fields, validates it (see HW-3 FAQ), and prints out an error message if anything is missing
  - if all 3 form values are present:
    - make a new `Favorite` instance
    - add it to the `favorites` array (this not necessary and does nothing now, but it will be needed later on when we utilize localStorage)
    - create a new bookmark component and add it to the page by calling `createBookmarkComponent()`
  - test it to be sure it works - you should be able to add new favorites and see them on the screen as `<my-bookmark>` elements
  - if you click on a link and then "go back" to the app page, you will notice that any new `<my-bookmark>` elements are GONE
  - this is normal, because we have not yet used `localStorage` to persist the data
  - to get around this for now and make testing easier, add `target="_blank"` to the opening `<a>` tag of the `<my-bookmark>` element
