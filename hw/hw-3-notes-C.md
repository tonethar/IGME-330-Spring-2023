# Notes "C" - for [*HW-3 - Link Buddy!*](hw-3.md)

## I. `localStorage` demo

- See **local-storage-demo-start.zip** in myCourses
- The magic happens in **storage.js**:
  - contains methods for reading from & writing to `localStorage`
  - will use `JSON.parse()` and `JSON.stringify()`
  - will use `localStorage.getItem()` and `localStorage.setItem()`
- **storage.js** is all done for you
- Go ahead and write code in **main.js** to get everything working
- Then move on to finishing up [HW-3 - Link Buddy](hw-3.md)

<hr>

## II. storage.js
- Copy over **storage.js** from the example above and `import` it into **main.js**
- Change the `storeName` variable to something meaningful - example `<yourActualBanjoID>-hw3-data`
- Here's some default `Favorite` data you could use

```js
{
      fid: "1234",
      text: "CIA", 
      url: "https://cia.gov", 
      comments: "The Agency."
    }
```

<hr>

## III. main.js
- Get rid of any default `Favorite` data and instead just initialize `favorites` as an empty array
- Modify `loadFavoritesFromStorage()` to actually load in the `Favorite` from `localStorage`
- Save an updated version of `favorites` to `localStorage` when appropriate
