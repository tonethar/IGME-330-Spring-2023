# JS Functions

- Functions are one of the fundamental building blocks in JavaScript
- A function is a "subprogram" that can be called by code external to the function
- Like the program itself, a function is composed of a sequence of statements called the function body
- Values can be passed to a function as parameters, and the function will return a value
- In JavaScript, every function is actually a `Function` object
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions
  - the "super power" of a function object is that (unlike other objects) it can be *called* or *invoked* with `()`

<hr>

## I. Simple function, no parameters

```js
let counter = 0;
function incrementCounter(){
  counter ++;
}

console.log(incrementCounter(), counter); // undefined, 1
```

- The above function takes no parameters
- Because it lacks a `return` statement, the return value will default to `undefined`
- A function can access all variables and functions defined inside the scope in which it is *defined* (meaning, the "parent scope")
  - the function above has access to and is modifying the global `counter` variable
  - in some languages the above function would be called a *procedure* because it does not return a value and instead relies on the "side effect" of modifying a part of the program that is outside of its own scope
  - functions that have *side effects* are sometimes called *impure functions* - https://www.freecodecamp.org/news/pure-function-vs-impure-function/

<hr>

## II. A function that takes a parameter and returns a value

```js
function doubleIt(num){
  return num * 2;
}

const doubleTen = doubleIt(10);
console.log(doubleTen); // 20
```

- Specifying default values for parameters is easy

```js
function doubleIt(num=0){
  return num * 2;
}

console.log(doubleIt()); // returns 0 * 2, which is 0
```

- Because the above function does NOT have any *side effects*, it can be called a *pure function*
  - https://www.freecodecamp.org/news/pure-function-vs-impure-function/
- Note that `n` above is *defined* inside the `doubleIt()` function and cannot be accessed from anywhere outside the `doubleIt()` function
 
<hr>

## III. Functions declared with the `function` keyword can be called *before* they are declared

- ... so long as they are declared in the same file and scope

```js
console.log(doubleIt(10)); // 20

// ...

function doubleIt(num=0){
  return num * 2;
}
```

<hr>

## IV. Functions can be declared *inside* of other functions

- In the example below, `capitalize()` is "private" to the `sayHello()` function and not visible outside of it (and `name` and `capFirstLetter` are similarly not visible from outside the `sayHello()` function)

```js
function sayHello(name,capFirstLetter){
  function capitalize(str){
    return str.charAt(0).toUpperCase() + str.slice(1);
  }
	
  if(capFirstLetter){
    name = capitalize(name);
  }
	
  return "Hello " + name;
}

console.log(sayHello("ace"));
console.log(sayHello("ace", true));
console.log(capitalize("billy")); // Uncaught ReferenceError: capitalize is not defined
```

- Why would you do something like this?
  - *Encapsulation* and *information hiding* and a *stable interface* generally makes for better software
  - https://en.wikipedia.org/wiki/Information_hiding

<hr>

## V. Recursion - functions can "call themselves"

- The act of a function calling itself, recursion is used to solve problems that contain smaller sub-problems
- Recursion is limited by the call stack size limit of the JS run-time (which varies by machine & browser, but is usually over 10,000 on modern browsers)
- https://developer.mozilla.org/en-US/docs/Glossary/Recursion
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Too_much_recursion
- https://dev.to/thawkin3/recursion-vs-loops-in-javascript-14em
- https://en.wikipedia.org/wiki/Recursion_(computer_science)

```js
function factorial(n){
  if (n === 0) {
    return 1;
  } else {
    return n * factorial(n - 1);
  }
}
console.log(factorial(10)); // 3628800
```

- Let's run tis code in the browser, open the debugger, and pop in a breakpoint so that we can see the *call stack* in action

<hr>

## VI. Arrow functions

- Arrow functions are a compact alternative to a traditional function expression where a function is declared with the `function` keyword
- ***The major difference between an arrow function and a regular function (other than the compact syntax) is that arrow functions do not bind to JS [this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)***
  - we will explore what the above statement means - and where this behavior really comes in handy - once we are working with ES6 classes and web components 
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions


### VI-A. Declarations with `function`

- "Old school" function declaration
- Note that we can call it *before* it is declared

```js
console.log(doubleIt(10)); // 20

function doubleIt(num=0){
  return num * 2;
}
```

- Also note that we can assign a function to a variable as an *expression*
- Although now (because we are using `const` or `let`) we can only call the function AFTER we have declared it

```js
const doubleIt = function(num=0){
  return num * 2;
};

console.log(doubleIt(10)); // 20
```

<hr>

### VI-B. Arrow Functions

- We have to assign them to a variable or constant
- Here's **version #1** of `doubleIt()` as an arrow function

```js
const doubleIt = (num=0) => {
  return num * 2;
};

console.log(doubleIt(10)); // 20
```

- **Version #2**
- If we only have one line of code in the function body we can get rid of the curly braces
- And we can get rid of `return` as well, and whatever that line of code evaluates to will be returned

```js
const doubleIt = (num=0) => num * 2;
```

- **Version #3**
- If there is only one parameter, and we get rid of the default value, we can also get rid of the paretheses around the arguments
- It's worth noting though, the many JS style guides require parentheses for arrow functions
  - https://github.com/airbnb/javascript#arrows--one-arg-parens

```js
const doubleIt5 = num => num * 2;
```

- **A real example**

```js

```
