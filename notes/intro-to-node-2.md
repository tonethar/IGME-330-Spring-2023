# Intro to Node.js - 2

## Overview


- we are going to create a **package.json** file this time


## Contents

<!--- Local Navigation --->

I. [Working with the package.json file](#section1)


V. [Homework](#section5)

<hr>

<a id="section1"></a>

## I. Working with the package.json file

### A. Get started:

- create a new folder named **hello-2**
- copy over your completed **index.js** file from Part I


### B. Create a node project the usual way
- this time we are going to follow the standard Node.js development practice and create a node project with **npm** - go ahead and change directory into the **hello-2** folder and type:

```js
npm init -y
```

This will create your **package.json** file with the default metadata about your project, which is stored in an object literal, and will look something like this:

```js
{
  "name": "hello-2",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

### C. Download the **request** module 

This time, we are going to download the **request** module, and then *save this dependency* into the **package.json** file. Type the following in:

```js
npm install request --save
```

- This will download and install the **request** module and other dependencies to the **node_modules** folder just like last time
- The `--save` flag is what tells npm to add a `"dependencies":` key to **package.json**, which you can see if you open the file:

```js
"dependencies": {
    "request": "^2.88.0"
  }
```

- note that we didn't get the warnings about the missing **package.json** file like we did last time
- PS: the `--save` flag has been *optional* for a few years now and can be omitted. npm now adds the `"dependencies":` key to **package.json** automatically whenever you install new packages 


### D. Download the **cowsay** module 


### E. Test the script

- Run the script to be sure that it still works as before:

```js
node index.js
```
 
 - Which should print out another "geek" joke such as:
 
 ```
"Chuck Norris can do a roundhouse kick faster than the speed of light. This means that if you turn on a 
light switch, you will be dead before the lightbulb turns on."
 ```
 
### E. Test package.json

- delete your **node_modules** folder
- if you run your script again - go ahead an type `node index.js` - it fails! - because the **request** module is nowhere to be found
- to re-install the **request** module files - just type `npm install` - which will re-download the **request** module and its dependencies because it is listed in the `"dependencies":` key of **package.json**
- run your script again - `node index.js` - it succeeds!


<a id="section5"></a>

## V. Homework
Out of 10 points.
- Make sure that everything we asked for in Section IV. is working:
  - Display the activity (1 point)
  - Display the type (1 point)
  - Display the number of participants (1 point)
  - Parse the first command line argument, and show actitivites for that number of participants (2 points)
  - Make **index.js** a command line script (tool) named **i-am-bored** that we can run from anywhere just by typing `i-am-bored` (2 points)
- Also be sure that everything is formatted nicely - add spacing where appropriate - and recall that `\n` in a string is the new line character (3 points)


**ZIP and POST to Dropbox**
<hr><hr>

**[Previous Chapter <- Intro to Node.js (chapter 1)](intro-to-node-1.md)**

