# JavaScript Code Style

- For your "solo" RIT coding projects, you are the only one writing the code, so code style might not be something you think about very often (but you should!)
- And when working on a group project, there will likely be many others working on the same codebase:
  - in these cases, a consistent code *style* can improve the readability and quality of your code
  - ideally, this shared code follows consistent idioms so that it appears that one person wrote it

## I. Some elements of good JS code style
- Elements of a code style that improve the readability of code (but not necessarily the quality):
  - consistent indenting of code blocks (2-spaces, 4-spaces, or tabs)
  - consistent use of quotes around strings (either all single-quoted, or all double-quoted)
  - consistent spacing when declaring and assigning variables
  - allowing (or not) "one-liner" if statements like this - `if(true) doStuff();`
  - and many others
- Code practices that can improve quality:
  - using "Strict equality" `===` instead of `==` because `console.log("0" == 0); // is true` and `console.log("0" === 0); // is false`
  - disallowing duplicate object property keys
  - making sure that any declared variable is actually used
  - and many others ...

<hr>

## II. Code snippet
- Try running the code below in the Chrome dev console
- It should run fine, but there are some potential style and quality issues, can you see any of them?

```js
const counter = 0;
const car = {
  'make':"Ford",
  "model":"Pinto",
  cylinders:4,
  "model":"Escort"
};

if(car.cylinders == 4){
  speed = "slow";
}else{
  speed = "not slow";
  counter++;
}

if (car.model = "Pinto") console.log("It's a Pinto");

console.log(`The ${car.model} is ${speed}`);
console.log("counter =",counter);
```

<hr>

## III. "lint" the code snippet
- What is *linting* code? - https://www.perforce.com/blog/qac/what-lint-code-and-why-linting-important
- Now try running the code through a *linter*:
  - https://eslint.org/demo
  - tick the "impliedStrict" checkbox
  - now tick "Enable all rules"
  - you should now see quite a few "suggestions" on how to improve your code!
  - try fixing all the errors (and unchecking a few unneeded rules here and there will also be a good idea!)

<hr>

## IV. FAQ

- **Is there an easier way to lint your code that copy/pasting it into a tool like the one linked above?**
  - *Yes! One thing you can do is to set up VSCode to automatically lint your code - https://www.digitalocean.com/community/tutorials/linting-and-formatting-with-eslint-in-vs-code*
- **Is code linting required in IGME-330?**
  - No, but it might be a good idea to run your project code through a linter at some point to catch any potential issues
  - But we **DO** have a written [IGME-330 - Course Code Style Requirements](330-code-style.md) though
  
