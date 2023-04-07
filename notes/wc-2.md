# Web Components II


## I. The Shadow DOM
- ***Shadow DOM*** - encapsulates HTML/CSS - style rules, class names etc are scoped to the component
  - https://developers.google.com/web/fundamentals/web-components/shadowdom
- Althought the *Shadow DOM* sounds kind of mysterious, it is simply a "scoped" DOM that components have that is separate from the main DOM of the document
- For example, if our component had an `<h1>` in it,  and we wrote a `document.querySelector("h1")` call, or wrote a style rule like this `h1{color:red}` - our component's `<h1>` would be unaffected
