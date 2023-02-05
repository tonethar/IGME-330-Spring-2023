# More JavaScript (DRAFT)


## I. Array destructuring


<hr>

## II. Object destructuring

- declaring/initializing
- initializing only - a special case

<hr>

## III. Named parameters in functions

```js
const orderTaco = (type,size,price,meat,cheese,supreme,spicy,glutenFree) => {
  console.log("Taco order: ", type,size,price,meat,cheese,supreme,spicy,glutenFree);
};

// Lot's of parameters!
orderTaco("Extreme","Large",9.99,"Chicken","mex-mix",true,true,false);
```

- We can use object destructuring to simulate named function parameters

```js
// just need to add `{...}` around the parameter list
const orderTaco2 = ({type,size,price,meat,cheese,supreme,spicy,glutenFree}) => {
  console.log(`Taco order: type=${type}, size=${size}, price=${price}, meat=${meat}, cheese=${cheese},  supreme=${supreme}, spicy=${spicy}, glutenFree=${glutenFree}`);
};

// and instead of 7 parameters, here we pass in a single object literal as a parameter
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
