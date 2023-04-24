# HW-4 - *NY State Park Buddy* - Starter 

## I. Get started
- Download the start files from myCourses
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
- The following code goes in the "private" section of **map.js**

![screenshot](_images/HW-4F.png)

<hr>

### III-B. Test the `addMarker()` helper function

- Put the following test code into the end of the `initMap()` function in **map.js**
- We are using the "features" data for Letchworth park - `geojson.features[0]` - which is hard-coded onto **map.js** as test data


```js
// test
const clickHandler = (id) => alert(`${id} was clicked!`);
addMarker(geojson.features[0], "poi", clickHandler);
```

<hr>

- When you are done there should be a single marker that looks like the screenshot below
- Clicking the marker will show the popup and also run our test `clickHandler`, which "alerts" the `id` of the marker to a browser modal dialog box

<hr>

![screenshot](_images/HW-4G.png)

<hr>

### III-C. DO THIS

- Add the park phone number to the popup:
  - modify the marker HTML
  - pull the `.phone` property from the feature
  - it should look similar to the screenshot below
  - ***PS - Once you have confirmed everything works, "comment out" or delete the test code from `initMap()`***

<hr>

![screenshot](_images/HW-4H.png)

<hr>

## IV. Load the park data from a JSON file

### IV-A. Declare a variable to hold the JSON

- In the "Variables & Constants" section of **main.js**, declare a `geojson` variable

```js
let geojson;
```

<hr>

### IV-B. Load the JSON file

- Let's go ahead and load the **data/parks.geojson** file and log it out to the console
- Make `init()` in **main.js** look like the following:

<hr>

![screenshot](_images/HW-4I.png)

<hr>

- Reload the page, and open the console, you should see the contents of **parks.geojson** logged out
- What you are inrterested in is the `features` array - which is the array that contains all of the NYS park data

<hr>

![screenshot](_images/HW-4J.png)

<hr>

### IV-C. Head over to map.js

- In **map.js**, in the "public" section, implement the `addMarkersToMap()` function, and `export` it
- ***Don't forget to `export` it!***

<hr>

![screenshot](_images/HW-4K.png)

<hr>

### IV-D. Head back to main.js

- In **main.js**, we are going to call `addMarkersToMap()` in the ajax callback function - right after the JSON is loaded, but before `setupUI()` is called

<hr>

![screenshot](_images/HW-4L.png)

<hr>

- Note that we have not yet implemented `showFeatureDetails()` - this will be the function that is called when each marker is clicked
- Here is the starter implementation of `showFeatureDetails()` (this goes in **main.js**):

```js
const showFeatureDetails = (id) => {
	console.log(`showFeatureDetails - id=${id}`);
};
```

- Go ahead and reload the page and test the code
  - all the parks in the JSON file should have markers on the map
  - clicking a marker should give you a popup showing the park name, address and phone humber
  - when a marker is clicked, you should also see a log in the console:
    - something like - `main.js:36 showFeatureDetails - id=p84`
    - which is the `showFeatureDetails()` function above, getting called when the marker in clicked on
  
<hr>

![screenshot](_images/HW-4M.png)

<hr>

## V. Showing feature details when a marker is clicked on

- When a marker is clicked on, we want to show the park name, address, phone number and description in the "Info" row of the app
- To do this, we will need to write code that searches the `features` array for the park that matches the `id` of the marker that was clciked on 

### V-A. Add HTML for the bottom "Info" row

- In **index.html**, make the bottom row (the one right above `<div class="footer" ...`. shown below) appear as below
- NB - when you are done, you may wish to validate your HTML to help determine if you typed it in properly

<hr>

![screenshot](_images/HW-4N.png)

<hr>

### V-B. Keep working on `showFeatureDetails()`

- Here are the next 2 lines of code for `showFeatureDetails()`

```js
const feature = getFeatureById(id);
document.querySelector("#details-1").innerHTML = `Info for ${feature.properties.title}`;
```

- **DO THIS** - Note that we did not give you the implementation of the `getFeatureById(id)` function - so go ahead and implement that yourself:
  - you need to "search" the `geojson.features` array for the park feature (object) that has a `.id` that matches the passed in `id` argument, and `return` it
  - an optimal solution uses `array.find()` and can be done in one line of code (but get it working however you can)
- Once you have it properly working, you should see the "Info" row displaying the name of the park that was just clicked on

<hr>

![screenshot](_images/HW-4O.png)

<hr>


### V-C. DO THIS - Complete `showFeatureDetails()`

- Go ahead and get `#details-2` displaying the clicked park's address, phone number, and web site:
  - the website must be a clickable link
  - the phone number must also be a clickable link - use the `tel:` protocol - google it if you are not familiar with how to use it
- Get `#details-3` displaying the clicked park's description
- See example screenshot below

<hr>

![screenshot](_images/HW-4P.png)

<hr>

## VI. Showing user Favorites

- We are going to add a new panel to the right columm, under the map controls
- This panel is going to show the user's "favorited" NYS parks
- When these favorites are clicked, the map will zoom to their location, and all of the data about them will be displayed in the "Info" area
- Eventually, you will write code that allows users to add and delete these favorites

### VI-A. Add HTML for the "Favorites Panel"

- In **index.html** go ahead and add the bottom "favorites" panel to the right column
  - the HTML goes right after "panel 1"
  - note that each "favorite" is a separate `<a>` tag that has been extensively styled
  - see screenshot below:

<hr>

![screenshot](_images/HW-4Q.png)

<hr>

- When you are done, it should look as below
- Note that the 2 "favorites" are placeholders and are not functional - and it's fine if you only want to type in one of them

<hr>

![screenshot](_images/HW-4R.png)

<hr>

### VI-B. Set up a "favorites" array in main.js

- Here is the array that will hold the ids of the user's favorite NYS parks
- This goes in the "Variables & constants" section of **main.js**

```js
let favoriteIds = ["p20","p79","p180","p43"];
```

<hr>

### VI-C. Implement `refreshFavorites()` in main.js

- `refreshFavorites()` will be called when the app first loads, and (later on) whenever the user utilizes controls to add or remove favorite Ids from the `favoriteIds` array
- Go ahead an implement `refreshFavorites()` (see below)
- And call `refreshFavorites()` from the bottom of `setupUI()`

<hr>

![screenshot](_images/HW-4S.png)

<hr>

- When we call `refreshFavorites()` - we will get an error message:
  - `Uncaught ReferenceError: createFavoriteElement is not defined`
  - because `createFavoriteElement(id)` is not yet implemented - so let's move on!

<hr>

### VI-D. Implement `createFavoriteElement(id)` in main.js

- `createFavoriteElement(id)` looks like this
- Note that we are again using `getFeatureById(id)` (which you wrote)
- Also note that each "favorite" is containd in an `<a>` tag that we are creating dynamically

<hr>

![screenshot](_images/HW-4T.png)

<hr>

- Reload the page, the code should run and create links for all 4 of your favorites
- Clicking on a park in the favorites panel will scroll the map to the location of the park, and will also display its data in the "Info" area

<hr>

![screenshot](_images/HW-4U.png)

<hr>

## VII. All done with the *NY State Park Buddy* "starter"

- You are done with the starter. You should now have an app that:
  - displays a Mapbox map, centered on NY State, with controls for panning and zooming the map
  - loads NYS park data from a JSON file and displays it on a map as individual markers, one for each park
  - clicking on a marker shows a popup, and displays more details about that park on the "Info" section of the HTML page
  - a list of hard-coded favorites is loaded in and displayed on th HTML pag. Clicking a favorite pans the map to that location and displays information about the park
- And there's more to do for HW-4:
  - adding and deleting favorites
  - porting some of the HTML and JS to Web Components
