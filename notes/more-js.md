# More JavaScript


## I. Array destructuring

- We saw *array destructuriing* in [Ajax-2](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-ajax-2.md);
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment
- *The destructuring assignment syntax (for arrays and objects) is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.*

```js
let a, b, rest;
[a, b] = [10, 20];

console.log(a);
// Expected output: 10

console.log(b);
// Expected output: 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest);
// Expected output: Array [30, 40, 50]
```

- More examples: [Destructuring_assignment#array_destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#array_destructuring)

<hr>

## II. Object destructuring

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#object_destructuring

```js
const user = {
  id: 42,
  isVerified: true,
};

const { id, isVerified } = user;

console.log(id); // 42
console.log(isVerified); // true
```

- OR, if the variables have already been previously declared, we'll need to wrap parentheses around the destructuring assignment

```js
const user = {
  id: 42,
  isVerified: true,
};

let id, isVerified;
({ id, isVerified } = user);

console.log(id); // 42
console.log(isVerified); // true
```

<hr>

## III. Named parameters in functions

- Once you get up to 5 or more parameters in a function, getting the order right can get problematic - see below:

```js
const orderTaco = (type,size,price,meat,cheese,supreme,spicy,glutenFree) => {
  console.log("Taco order: ", type,size,price,meat,cheese,supreme,spicy,glutenFree);
};

// Lot's of parameters - what is the order of the last 3 booleans again?
orderTaco("Extreme","Large",9.99,"Chicken","mex-mix",true,true,false);
```

- But we can instead use *object destructuring* to simulate named function parameters

```js
// just need to add `{...}` around the parameter list
const orderTaco2 = ({type,size,price,meat,cheese,supreme,spicy,glutenFree}) => {
  console.log(`Taco order: type=${type}, size=${size}, price=${price}, meat=${meat}, cheese=${cheese},  supreme=${supreme}, spicy=${spicy}, glutenFree=${glutenFree}`);
};

// and instead of 7 parameters, here we pass in a single object literal as a parameter
// which meaans that our parameters are each individually *named*
// which also means that the parameter *order* does not matter!
// which one is easier to read?
orderTaco2({
  type: "Extreme",
  size: "Large",
  price: 9.99,
  meat: "Chicken",
  cheese: "mex-mix",
  supreme: true,
  spicy: true,
  glutenFree: false});
```

<hr>

## IV. Conditions & assignment
- Never use `if(myBool == false)`
- `if/else` statement
- Ternary Operator
- Logical OR - `||`
- Null-colasecing operator - `??`

<hr>

## V. Method chaining
