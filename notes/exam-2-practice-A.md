# Exam #2 - Practice A

- The questions below will help you practice for exam #2
- You should try to write these out on paper first, and then live code the solution to see how close you were
- Concepts covered:
  - `array.map()` and `array.join()` with an array of object literals (mostly a review of what we saw on exam #1
  - creating an ES6 class, and an instance of that class)
  - `Object.create()` and the prototype chain

<hr>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>Exam #2 - Practice A</title>
</head>
<body>
<h1>Exam #2 - Practice A</h1>
<ol>
  <!—- The generated HTML will go here -—>
</ol>
<script>
  "use strict";
  
/*
	1) Use array.map() and array.join() to step through the pets array below and put the name and
		the age of each dog in an <li> tag, and then add it to the existing <ol> tag on the page.
	
	The final HTML will look like this after it is added:

	<ol>
		<li>Luna - age 5</li>
		<li>Niko - age 2</li>
	</ol>
*/
 const pets = [{name: "Luna", age: 5}, {name: "Niko", age: 2}];




/*
	2) Create an ES6 class named Dog. 

	2A) In the constructor of Dog initialize the 2 passed in arguments -
	`name` and `age` - as properties.

	2B) Give the Dog class a `bark()` method, when called this method will log out 
	"Woof, Woof my name is XXX" where XXX is the value of the `.name` property of the dog instance

	3) Create a new instance of Dog named `dog1`. Pass in "Wags" and 5 for the name and age.
	3A) Write code that calls the `bark` method of `dog1` 
	
	4) Create a new object literal named `fancyDog` and set its prototype object to dog1 above.
	Hint: Use Object.create()
	4A) Add a `breed` property to `fancyDog` and give it a value of "Bichon Frisé"
	4B) Call the `bark` method of `fancyDog` - it should log out "Woof, Woof my name is Wags"


*/

  
	
  </script>


</body>
</html>
```
