# Notes "C" - for [*HW-3 - Link Buddy!*](hw-3.md)

## I. `localStorage` demo

- See **local-storage-demo-start.zip** in myCourses

<hr>

## II. storage.js
- Copy over **storage.js** from the example and `import` it into **main.js**
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
- Save an updaetd version of `favorites`
