# Web Components-2 - Shadow DOM and HTML Templates

## I. Start Code

- Create this file and open it up in the browser
- Look over the code and be sure that you understand how it works
- **DO THIS:** - Add a new `<my-bookmark>` and `<li>` to the bottom of the `<ul>` - in the HTML - have it link to the *MDN Web component docs* (use google to get the link)

**wc-2.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Web Components - Shadow DOM & HTML Templates</title>
  <style>
    body{
      font-family: sans-serif;
    }
    /* Note that we can style custom elements just like any other built-in element such as a <p>, <h1> etc*/
    my-bookmark{
      border: 1px dashed black;
      padding: 2px;
    }
  </style>
  <script>


  class MyBookmark extends HTMLElement {
    // called when the component is first created, but before it is added to the DOM
    constructor(){
      super();
      this._title = "RIT";
      this._url = "https://www.rit.edu/";
    }

    // tell the component what attributes to "watch"
    static get observedAttributes() {
      return ["data-title", "data-url"];
    }

    // ** lifecycle events **

    // called when the component is inserted into the DOM
    connectedCallback(){
      this.render();
    }

    // this method is invoked each time one of the component's "watched" attributes changes
    attributeChangedCallback(attributeName, oldValue, newValue) {
      console.log(attributeName, oldValue, newValue);
      if(oldValue === newValue) return;
      if(attributeName == "data-title"){
        this._title = newValue;
      }
      if(attributeName == "data-url"){
        this._url = newValue;
      }
      this.render();
    }

    // helper method
    render(){
      this.innerHTML = `<span><a href="${this._url}">${this._title}</a></span>`;
    }
  }

  customElements.define('my-bookmark', MyBookmark);

  window.onload = () => {
    // Create a MyBookmark and add it to the list
    const bing = document.createElement("my-bookmark");

    // ANOTHER way to set custom attributes, the .dataset property
    // note that these 2 lines of code will also trigger attributeChangedCallback()
    bing.dataset.title = "Bing";
    bing.dataset.url = "https://www.bing.com/";

    const newLI = document.createElement("li");
    newLI.appendChild(bing);
    document.querySelector("#bookmarks").appendChild(newLI);
  };

  </script>
</head>
<body>
  <h1>Web Components - Shadow DOM & HTML Templates</h1>
  <ul id="bookmarks">
    <li><my-bookmark></my-bookmark></li>
    <li><my-bookmark data-title="Google" data-url="https://www.google.com/"></my-bookmark></li>
  </ul>
</body>
</html>
```

<hr>

## II. The Shadow DOM
- ***Shadow DOM*** - encapsulates HTML/CSS - style rules, class names etc are scoped to the component
  - https://developers.google.com/web/fundamentals/web-components/shadowdom
- Althought the *Shadow DOM* sounds kind of mysterious, it is simply a "scoped" DOM that components have that is separate from the main DOM of the document. 
- For example, if our component had an `<h1>` in it,  and we wrote a `document.querySelector("h1")` call, or wrote a style rule like this `h1{color:red}` - our component's `<h1>` would be unaffected
- From [MDN/Web_Components/Using_shadow_DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM):
  - *... none of the code inside a shadow DOM can affect anything outside it, allowing for handy encapsulation*
  - *Note that the shadow DOM is not a new thing by any means — browsers have used it for a long time to encapsulate the inner structure of an element. Think for example of a `<video>` element, with the default browser controls exposed. All you see in the DOM is the `<video>` element, but it contains a series of buttons and other controls inside its shadow DOM. The shadow DOM spec has made it so that you are allowed to actually manipulate the shadow DOM of your own custom elements.*
- https://blog.revillweb.com/open-vs-closed-shadow-dom-9f3d7427d1af

<hr> 
