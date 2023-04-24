# HW-4 Starter 
## *(Not done yet! - I will send out a Slack message Sunday night when it is!)*

## I. Download the start files
- Rename the folder to ***lastName*-*firstInitial*-hw4**
- Look over the HTML/CSS/JS files to be sure that you understand the structure of the app
- Add your Mapbox API key to **map.js**
- Change the name and year in the HTML footer to appropriate values
- Reload the HTML page - the map should be displaying now
  - note the helpful zoom controls we added to the upper-right corner of the map
  - the user can also use their mouse to pan the map and zoom in and out


<hr>

![screenshot](_images/HW-4A.png)

<hr>

## II. Get the buttons working
- We are going to add a [Bulma "panel"](https://bulma.io/documentation/components/panel/) and 3 buttons to the right column of the page. These buttons will allow the user to control the viewable area of the map

### II-A. The HTML for the buttons looks like this:

- Make these changes in **index.html**

![screenshot](_images/HW-4B.png)

![screenshot](_images/HW-4C.png)

<hr>

### II-B. The JS for the buttons looks like this:

- Make these changes in **main.js**

![screenshot](_images/HW-4D.png)

<hr>

- And go ahead and call `setupUI()` at the bottom of `init()`
- When you are done the buttons should function and the map should look like this

<hr>

![screenshot](_images/HW-4E.png)

<hr>

## III. Add Markers to the map

- Let's go ahead and write the code that will add State park *markers* to the map
- These markers will display a popup when clicked
- They will also (very soon) display other information about each park, in the "Info" section of the HTML page

### III-A. Implement the `addMarker()` helper function
- The following code goes in the "public" section of **map.js**

![screenshot](_images/HW-4F.png)

<hr>

### III-B. Test the `addMarker()` helper function

- Put the following test code into the end of the `initMap()` function in **map.js**
- We Are using the "features" data for Letchworth park, which is hard-coded onto **map.js** as test data


```js
// test
const clickHandler = (id) => alert(`${id} was clicked!`);
addMarker(geojson.features[0], "poi", clickHandler)
```

<hr>

- When you are done there should be a single marker that looks like the screenshot below
- Clicking the marker will show the popup and also run our test `clickHandler`, which "alerts" the `id` of the marker to a browser modal dialog box

![screenshot](_images/HW-4G.png)

<hr>

### III-C. DO THIS

- Add the park phone number to the popup:
  - modify the marker HTML
  - pull the `.phone` property from the feature
  - it should look similar to the screenshot below
  - PS - Once you have confirmed everything works, "comment out" or delete the test code from `initMap()`

![screenshot](_images/HW-4H.png)

<hr>

## IV.
