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
  sayHello(){
    console.log(`I am a ${this.constructor.name} of type=${this.type}`);
  }
}

// Create an instance of that class
let thing = new Thing("Slimy");
console.log(thing); // Thing {type: 'Slimy'}
console.log(thing.sayHello()); // I am a Thing of type=Slimy
```

<hr>

### I-A. More ways to define a class

- Assign an anonymous class to a *variable*

```js
const Thing2 = class{
  constructor(type){
    this.type = type;
  }
  sayHello(){
    console.log(`I am a ${this.constructor.name} of type=${this.type}`);
  }
};

// gives us the same thing
let thing2 = new Thing2("Smelly");
console.log(thing2); // Thing2 {type: 'Smelly'}
console.log(thing2.sayHello()); // I am a Thing2 of type=Smelly
```

- [Function constructors](https://javascript.info/constructor-new) - the usual JS way to simulate classes before ES6

```js
function Thing3(type){
  this.type = type;
}

Thing3.prototype.sayHello = function(){
  console.log(`I am a ${this.constructor.name} of type=${this.type}`);
};

let thing3 = new Thing3("Stinky");
console.log(thing3); // Thing3 {type: 'Stinky'}
console.log(thing3.sayHello()); // I am a Thing3 of type=Stinky
```
