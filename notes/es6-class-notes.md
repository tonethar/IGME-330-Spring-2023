# ES6 Class Notes

- *"Classes are a template for creating objects."*
- [MDN - ES6 Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

<hr>

## I. A Simple `class`

```js
// Define the class
class Thing{
  constructor(type){
    this.type = type;
  }
}

// Create an instance of that class
let thing = new Thing("Slimy");
console.log(thing); // Thing {type: 'Slimy'}
```

<hr>

### I-A. More ways to define a class

```js
// Assign an anonymous class to a variable
const Thing2 = class{
  constructor(type){
    this.type = type;
  }
};

// gives us the same thing
let thing2 = new Thing2("Smelly");
console.log(thing2); // Thing {type: 'Smelly'}
```
