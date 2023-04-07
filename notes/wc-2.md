# Web Components-2


## I. The Shadow DOM
- ***Shadow DOM*** - encapsulates HTML/CSS - style rules, class names etc are scoped to the component
  - https://developers.google.com/web/fundamentals/web-components/shadowdom
- Althought the *Shadow DOM* sounds kind of mysterious, it is simply a "scoped" DOM that components have that is separate from the main DOM of the document. 
- For example, if our component had an `<h1>` in it,  and we wrote a `document.querySelector("h1")` call, or wrote a style rule like this `h1{color:red}` - our component's `<h1>` would be unaffected
- From [MDN/Web_Components/Using_shadow_DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM):
  - *... none of the code inside a shadow DOM can affect anything outside it, allowing for handy encapsulation*
  - *Note that the shadow DOM is not a new thing by any means — browsers have used it for a long time to encapsulate the inner structure of an element. Think for example of a `<video>` element, with the default browser controls exposed. All you see in the DOM is the <video> element, but it contains a series of buttons and other controls inside its shadow DOM. The shadow DOM spec has made it so that you are allowed to actually manipulate the shadow DOM of your own custom elements.*
