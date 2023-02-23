# ES6 Object Notes

## Overview
- A software *object* is an entity which defines:
  - the "states" the object can exist in (i.e. properties)
  - and a set of functions that define the behavior of that object (i.e. methods)
- [IGME-235 - Object Literals Reference Material](https://github.com/tonethar/IGME-235-Shared/blob/master/tutorial/web-apps-7.md)

<hr>

## I. Objects in ES6

### I-A. Creation & Overview
- Objects are *"used to store various keyed collections and more complex entities."*
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
- Objects can be created using the [Object()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/Object) constructor or the [object initializer / literal syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer).
- For example:

```js
// we could use the Object() constructor to make a new object
let a = new Object();
a.job = "Ambulance Driver";
console.log(a); // {job: 'Ambulance Driver'}

// but more commonly we'll use object literal syntax
let b = {};
b.job = "Baker";
console.log(b); // {job: 'Baker'}

// we can also give the object properties when we declare it
let c = { "job" : "Criminal" };
console.log(c); // {job: 'Criminal'}
```

- Object keys (e.g. property names) are usally quoted strings - `"job"`
  - or they can be identifiers that are not quoted (as long as the identifier does not have spaces) - `job`
  - they can also be variables that are references to other objects - `jobRef`
- One very powerful (and potentially hazardous) feature of JS is that we can add more properties and even methods after an object is created:


```js
let d = {
  "name": "Danny",
  "sayHello": function(){ console.log(`Hello - my name is ${this.name}`); }
};

d.job = "Dog Walker";
d.sayGoodbye = function(){ console.log(`Goodbye - my job is ${this.job}`); };

console.log(d);
d.sayHello();
d.sayGoodbye();
```

- Note that in the console, we can see that both properties and both methods are present on the `d` object, regardless of whether they were there when the object was created, or added later on:

```
{name: 'Danny', job: 'Dog Walker', sayHello: ƒ, sayGoodbye: ƒ}
```

<hr>

### I-B. Handy `Object` "class" methods

- If we "misspell" a property - it will get added to the object as a new property!

```js
d.joob = "Donut Maker"; // should be .job, not .joob
console.log(d); // {name: 'Danny', job: 'Dog Walker', joob: 'Donut Maker', sayHello: ƒ, sayGoodbye: ƒ}
```

- [`Object.seal()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/seal) will make it so we can't add properties to an existing object
  - new properties cannot be added to the passed in object
  - *"Attempting to delete or add properties to a sealed object, or to convert a data property to accessor or vice versa, will fail, either silently or by throwing a TypeError"*

```js
Object.seal(d);
d.naame = "Donut Maker"; // should be .name, not .naame - gives an ERROR or fails silently
console.log(d); // no .naame property was added
```

- [`Object.freeze()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze) will make it so we can't add properties to an existing object OR modify existing ones
- *"Freezing an object prevents extensions and makes existing properties non-writable and non-configurable. A frozen object can no longer be changed: new properties cannot be added, existing properties cannot be removed, their enumerability, configurability, writability, or value cannot be changed, and the object's prototype cannot be re-assigned. freeze() returns the same object that was passed in. Freezing an object is the highest integrity level that JavaScript provides."*

```js
Object.freeze(d);
d.job = "Ditch Digger"; // cannot modify existing property
d.age = 55; // NOR add a new property
console.log(d); // no changes or new properties
```

- BTW: In JavaScript, arrays are objects too - and can be sealed and frozen

```js
const e = ["red","green","blue"];
e.push("cyan"); // WHY DOES THIS WORK?
console.log(e); // ['red', 'green', 'blue', 'cyan']

Object.seal(e);
e.push("yellow"); // fails because we can't add index `4` (which is a property key) 
e[0] = "Maroon"; // but we CAN do this
console.log(e); // ['Maroon', 'green', 'blue', 'cyan']

Object.freeze(e);
e[1] = "Emerald"; // now this will fail too
console.log(e); // ['Maroon', 'green', 'blue', 'cyan']
```

<hr>

### I-C. Object Prototypes

- Note that the first 3 objects we made above, each look the same in the console/debugger, no matter how they were created:

```js
{job: 'Ambulance Driver'}
{job: 'Baker'}
{job: 'Criminal'}
```

<hr>

- And if we take a look inside each object, we'll see that these objects have other methods that they "inherited" from the object *prototype*
-  *"A typical object inherits properties (including methods) from `Object.prototype`, although these properties may be shadowed (a.k.a. overridden)"* 
- Meaning that these object literals have default `toString()` and `toValue()` methods, ways to define setters and getter, and so on

![screenshot](_images/objects-classes-1.png)

<hr>

- Let's test out the built-in `.toString()` method
- And then implement our own `.toString()` method

```js
console.log(a.toString()); // '[object Object]'

// Let's add our own .toString() method
// this will override (or "shadow") the existing .toString()
a.toString = function(){ console.log(`My job is ${this.job}`); };
console.log(a.toString()); // My job is Ambulance Driver
```

<hr>

#### I-C-i. Setting the object `prototype` to `null`
- Why would we do this? 
- What if we just needed the key:value associative properties of an object, but none of its other capabilities?

```js
const colorEnum = Object.create(null); // enum has no protoype
console.log(colorEnum); // {} - missing the prototype methods
//console.log(colorEnum.toString()); // ERROR

colorEnum.REDDISH_COLOR = "rgb(200,0,0)";
colorEnum.GREENISH_COLOR = "rgb(0,200,0)";
Object.freeze(colorEnum); 

console.log(colorEnum); // {REDDISH_COLOR: 'rgb(200,0,0)', GREENISH_COLOR: 'rgb(0,200,0)'}
console.log(colorEnum.REDDISH_COLOR); // rgb(200,0,0)
console.log(colorEnum.GREENISH_COLOR); // rgb(0,200,0)
```

- [`Object.create()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
- NB - `Object.create()` can also be used to create object inheritance hierarchies, but most developers will utilize ES6 classes and the `extends` keyword instead
 
<hr>

### I-D. Setting and getting properties

- We typically use dot notation
- But can also use square brackets - `[]` - which are required when our property names have spaces
- If the property name does not exist, the value is `undefined`

```js
console.log(d.job); // Dog Walker
console.log(d["job"]); // Dog Walker
console.log(d.jawb); // undefined because .jawb property does not exist (but this is an ERROR in most languages)

// Handling a property name with spaces requires square brackets
d["dream job"] = "Lion Tamer";
console.log(d["dream job"]); // Lion Tamer
console.log(d.dream job); // SYNTAX ERROR
```

<hr>

### I-E. More about Object properties

- Object properties can point at primitive values ("value types") such as strings, numbers, booleans
- They can also point at objects ("reference types") - for example another object literal, or a reference to a DOM element
- They can even point at function references - because in JS functions are objects

```js
const h2 = document.querySelector("h2");
const sayHello = function(){ console.log("Hello!"); };

const obj = {
  "title" : "My Object", // String
  "rating" : 5, // Number
  "active" : true, // Boolean
  "created" : new Date(), // Object reference
  "last-edited" : undefined,
  "deleted" : null,
  "h2-ref": h2, // DOM object reference
  "info" : {}, // Object literal (also a reference)
  "stuff" : ["thing 1", "thing 2"], // Array (also an object reference)
  "sayHello" : sayHello, // Function - also an object - also a reference
};

console.log(obj.title);
console.log(obj.rating);
console.log(obj.active);
console.log(obj["last-edited"]);
console.log(obj.deleted);
console.log(obj["h2-ref"]);
console.log(obj.info);
console.log(obj.stuff);
console.log(obj.sayHello); // function reference
console.log(obj.sayHello()); // call the function
```

<hr>

### I-F. Function properties
- When an object has a property that points at a function, we usually call that a *method*
- These are all valid ways to initialize methods on an object

```js
let d = {
  "name": "Danny",
  "sayHello": function(){ 
    console.log(`Hello - my name is ${this.name}`); // note that `this` is required to access the `name` property
   },
   job: "Door-to-door Salesperson"
};

console.log(d.sayHello());

// Most developers prefer this newer syntax though
let d2 = {
  "name": "Denny",
  sayHello(){ 
    console.log(`Hello - my name is ${this.name}`); 
  },
  job: "Ding-dong Ditcher"
};

console.log(d2.sayHello());
```

- You can also have arrow functions as methods of object literals
- But because they don't have access to the object's `this` keyword, `sayHello()` will not function as expected in this case
- Occasionally though, an arrow function as an object property does have its uses

```js
let d3 = {
  "name": "Denny",
  sayHello: () => {
    console.log(`Hello - my name is ${this.name}`); 
  },
  job: "Ding-dong Ditcher"
};

// this.name will be undefined
console.log(d3.sayHello()); // Hello - my name is 
```

<hr>

### I-G. Initializing object properties

```js
// The traditonal way to initialize object properties
let city = "Chicago";
let founded = 1837;

let obj = {
  "city" : city,
  "founded" : founded,
  "population" : 2697000
};

// E6 "shorthand" way to initialize object properties
let obj2 = {
  city, // "city" will be the name of the property, and the value of the city variable will be the value of the property
  founded, // ditto
  "population" : 2697000 // we can still assign properties the usual way
};

console.log(obj); // {city: 'Chicago', founded: 1837, population: 2697000}
console.log(obj2); // {city: 'Chicago', founded: 1837, population: 2697000}
```

<hr>

## II. Other nice stuff to know about JS objects (we'll cover some of this later on on course)

- getter/setter syntax:
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set
  - https://javascript.info/property-accessors
  - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty
- [JS Object prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [Object Property Privacy](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Private_class_fields)
