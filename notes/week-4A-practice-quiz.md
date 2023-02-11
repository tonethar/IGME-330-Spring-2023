# Week 4A - Practice Take-home Quiz


## I. Instructions
- This is for practice, not for a grade
- Copy the code below and open it in a web browser to be sure it works
  - Pop in a breakpoint at the bottom of `init()` - you should see that we have 7 functions and 1 variable in what Chrome calls "script scope" - which is basically a *global* scope where things declared with `let` and `const` show up
  - Putting all your variables and functions in the global scope works fine for simple apps, but becomes potentially problematic with larger apps
  - For example you will see that **HW-2 Audio Visualizer** will end up having a large amount of JS code, and being able to break it into discrete modules with well-defined functionality and interfaces will make it a lot easier to debug while you are implementing it

<hr>

## I-A. ES6 Modules
- Go ahead and convert the app over to ES6 module syntax
- Come up with a **utils.js** module that contains all of the "pure" functions with no dependencies
- Then import those functions into a **main.js**
- Don't forget to write a `<script>` tag of `type="module"` that points at **main.js**
- And get rid of any code you don't need anymore

<hr>

## I-B. Sounds "Iffy" to me
- Make a copy of **quote-app.html** named **quote-app-IIFE.html**
- Get ALL of the variables and functions out of "script scope" by wrapping everything in a single anonymous function
- Remember the [IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)? - "Immediately Invoked Function Expression"
- Go ahead and wrap everything in an anonymous function
  - get rid of any code you don't need anymore
  - invoke the function
  - put in a breakpoint at the bottom of the IIFE and check the debugger - no more "script scope" variables at all!
  - put a breakpoint in `nextQuote()` and click the "Next Quote" button - you can see the [Closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures) variables and functions in the debugger

```js
(() => {
    //... put the code here ...
})();
```

---

## II. The start code

**quote-app.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title>Quotes</title>
	<style>
		body{
			font-family: sans-serif;
		}
                /* https://www.w3schools.com/css/css3_buttons.asp */
		button{
			background-color: #4CAF50; /* Green */
			border: none;
			color: black;
			padding: 15px 32px;
			text-align: center;
			text-decoration: none;
			display: inline-block;
			font-size: 16px;
			margin-right: 1em;
			width:180px;
		}
		
		button {
			transition-duration: 0.4s;
		}

		button:hover {
			color: white;
			box-shadow: inset 0 0 10px #0f0;
		}
		
		p{
			font-style:italic;
		}
	</style>
	<script>
	
	// START CODE
	"use strict";
	
        // https://www.brainyquote.com/topics/education-quotes
	const quotes = [
	"It is the mark of an educated mind to be able to entertain a thought without accepting it. - Aristotle",
	"In the first place, God made idiots. That was for practice. Then he made school boards. - Mark Twain",
	"The whole purpose of education is to turn mirrors into windows. - Sydney J. Harris",
	"Education is a progressive discovery of our own ignorance. - Will Durant"];
	
	let quoteIndex = 0;
	
	const getQuote = (index) => {
		return quotes[index];
	}
	
	const displayQuote = (index) => {
		document.querySelector("#lbl-output").innerHTML = getQuote(index);
	};
	
	const displayPagination = (index) => {
		document.querySelector("#lbl-pagination").innerHTML = `${index+1} of ${quotes.length}`;
	};
	
	const nextQuote = () => {
		quoteIndex += 1;
		if (quoteIndex >= quotes.length){
			quoteIndex = 0;
		}
		displayQuote(quoteIndex);
		displayPagination(quoteIndex);
	};
	
	const prevQuote = () => {
		quoteIndex -= 1;
		if (quoteIndex < 0){
			quoteIndex = quotes.length - 1;
		}
		displayQuote(quoteIndex);
		displayPagination(quoteIndex);
	};
	
	const init = () => {
		displayQuote(quoteIndex);
		displayPagination(quoteIndex);
		document.querySelector("#btn-prev").onclick = prevQuote;
		document.querySelector("#btn-next").onclick = nextQuote;
	};
	
	
	window.onload = init;
	
	</script>
</head>
<body>
  <h2>QUOTES</h2>
  <button id="btn-prev">Previous Quote</button><button id="btn-next">Next Quote</button>
  <p id="lbl-pagination">? of ?</p>
  <p id="lbl-output">???</p>
</body>
</html>
```
