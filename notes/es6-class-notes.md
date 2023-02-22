# ES6 Class Notes

- *"Classes are a template for creating objects."*
- [MDN - ES6 Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

<hr>

## I. A Simple `class`

```js
// Define the class
class Thing{
  constructor(type){
    this.name = type;
  }
}

// Create an instance of that class
let thing = new Thing("Slimy");
console.log(thing); // Thing {name: 'Slimy'}
```

