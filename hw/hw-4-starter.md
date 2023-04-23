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
