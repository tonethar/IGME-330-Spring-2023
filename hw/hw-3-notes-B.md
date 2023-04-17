# Notes "B" - for [*HW-3 - Link Buddy!*](hw-3.md)


## I. The `deleteFavorite(fid)` function

- In **main.js*, implement the `deleteFavorite(fid)` function
- This function will be called when the "Delete" button in the component is clicked
- This function takes a `fid` ("favorites ID") as a parameter and:
  - 1) will remove that `Favorite` from the `favorites` array
      - how to do the removal from the array is up to you 
      - a good use of google! - "how to remove a specific element from array js"
      - be sure to document (as a code comment) the url where you got your technique from 
  - 2) will update the "Number of Favorites" count on the screen (PS - make sure that you are also doing this at app start up, and every time a new favorite is added)
  - 3) the component that is displaying that favorite will also be removed from DOM using the `.remove()` method
      - this removal can be done either in the component code (in `MyBookmark`, easier to do here), or in **main.js**
- You can test the `deleteFavorite(fid)` function with code like this:

```js
 deleteFavorite("123"); // give your starting bookmark a .fid of "123"
 console.log(favorites.length);
```

- Now pass in `deleteFavorite` as a `.callback` property to every bookmark that you create (see lecture notes for help on this)

<hr>

## II. The `MyBookmark` component
- Modify the code to get the "Delete" button working (see lecture notes for help on this)
- Don't forget to disable and "gray out" the "Favorite" button. You can do this with the `disabled` attribute
