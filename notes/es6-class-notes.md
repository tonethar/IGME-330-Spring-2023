# ES6 Class Notes

- [MDN - ES6 Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) - *"Classes are a template for creating objects."*

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

- OR, just create an *object literal* instead of a class

```js
const thing4 = {
  "type" : "Slippery",
  sayHello(){
    console.log(`I am a ${this.constructor.name} of type=${this.type}`);
  }
};

console.log(thing4); // {type: 'Slippery', sayHello: ƒ}
console.log(thing4.sayHello()); // I am a Object of type=Slippery
```

### I-B. These 4 versions look and behave similarly

```js
console.log(thing);
console.log(thing2);
console.log(thing3);
console.log(thing4);
```

![screenshot](_images/objects-classes-2.png)

- For today we'll just use the regular `class` way (`Thing` above)

<hr>

## II. Inheritance

- Briefly, because we won't be using it this semester (but if you want to use inheritance on an assignment, have at it!)

```js
class Thing{
  constructor(type){
    this.type = type;
  }
  sayHello(){
    console.log(`I am a ${this.constructor.name} of type=${this.type}`);
  }
}

// NEW
class AlienThing extends Thing{
  constructor(type, alignment){
    super(type); // call superclass constructor in Thing
    this.alignment = alignment;
  }
  fireDeathRay(){
     console.log(`Feel the power of my ${this.alignment} ray!`);
  }
}

let alien = new AlienThing("Slinky","Evil");
console.log(alien); // AlienThing {type: 'Slinky', alignment: 'Evil'}
console.log(alien.sayHello()); // I am a AlienThing of type=Slinky
console.log(alien.fireDeathRay()); // Feel the power of my Evil ray!
```

<hr>

## III. Building a `CircleSprite` class

### III-A. Start code

**sprites-start.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title>Sprites Start</title>
	<style>canvas{ border: 1px solid black; }</style>
	<script>
	
	"use strict";
	const canvasWidth = 400, canvasHeight = 300;
	
	let ctx;

	const loop = () => {
    setTimeout(loop,1000/30);
		ctx.fillRect(0,0,canvasWidth,canvasHeight);
	}
	
	const init = () => {
		ctx = canvas.getContext("2d");
		canvas.width = canvasWidth;
		canvas.height = canvasHeight;
		loop();
	};
	
	window.onload = init;

	</script>
</head>
<body>
<canvas id="canvas"></canvas>

</body>
</html>
```
