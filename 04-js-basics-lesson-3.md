# Orientation Course - Basics of JavaScript Programming 3

MP 9/2020

## JavaScript basics, lesson 3

### Defining a function

There are three different ways to construct a function.

[Function declaration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function) (is hoisted):

```js
function getRandomInteger(minInclusiveValue, maxInclusiveValue) {
  const randomInt =
    Math.floor(Math.random()*(maxInclusiveValue+1)) + minInclusiveValue;
  return randomInt;
}
getRandomInteger(2,5); // returns 2, 3, 4 or 5


function getSum(value1, value2) {
  return value1 + value2;
}
getSum(2, 4); // returns 6
```

[Function expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function) (is not hoisted):

```js
const getRandomInteger = function(minInclusiveValue, maxInclusiveValue) {
  const randomInt =
    Math.floor(Math.random()*(maxInclusiveValue+1)) + minInclusiveValue;
  return randomInt;
};
getRandomInteger(2,5); // returns 2, 3, 4 or 5

const getSum = function(value1, value2) {
  return value1 + value2;
};
getSum(2, 4); // returns 6
```

[Arrow function expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions):

```js
const getRandomInteger = (minInclusiveValue, maxInclusiveValue) => {
  const randomInt =
    Math.floor(Math.random()*(maxInclusiveValue+1)) + minInclusiveValue;
  return randomInt;
};
getRandomInteger(2,5); // returns 2, 3, 4 or 5

// return keyword not necessary, if only one statement is used to get the value
const getSum = (value1, value2) => value1 + value2;
getSum(2, 4); // returns 6
```

[Hoisting is JavaScript's default behavior of moving declarations to the top.](https://www.w3schools.com/js/js_hoisting.asp)

---

### Document Object Model (DOM)

- [The DOM](https://en.wikipedia.org/wiki/Document_Object_Model) is a document model loaded in the browser and representing the document as a node tree, where each node represents part of the document (e.g. an element, text string, or comment).
- The DOM allows JavaScript code running in a browser to access and interact with every node in the HTML document. Nodes can be created, moved and changed. Event listeners can be added to nodes and triggered on occurrence of a given event.
- [DOM tutorial in w3schools.com](https://www.w3schools.com/js/js_htmldom.asp)
- [Document Object Model documentation in MDN web docs](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

![Dom structure](https://www.w3schools.com/js/pic_htmltree.gif)
(source: w3schools.com)

```html
<html> <!-- Root element -->
  <head>
    <title>My title</title> <!-- text node in element node -->
  </head>
  <body>
    <h1>My header</h1>
    <a href="example.com">My link</a>
  </body>
</html>
```

- Node types: _element node_, _text node_, _attribute node_
- terms _parent_, _child_, and _sibling_ are used to describe the relationships:
  - every node has exactly one parent, except the root (which has no parent)
  - a node can have a number of children
  - siblings (brothers or sisters) are nodes with the same parent
- Using JavaScript you can access the properties and use the methods of DOM Objects (like Node, Document, Element Body, Button, etc.)
- You can modify DOM
  - Get contents of nodes from the DOM
  - Create and add nodes to the DOM
  - Remove nodes from the DOM

#### Using the Document interface

The `document` interface provides properties and methods for accessing and manipulating the contents and structure (DOM nodes) of a web page (html document).

Some common methods:

```js
getElementById()           // Return the element using id attribute
getElementsByTagName()     // Return array of nodes with a specified tag name
getElementsByClassName()   // Return array of nodes with a specified class
querySelector()            // Return the element using CSS selector
querySelector()            // Return array of elements using CSS selector

append()       // Add a new child node as the last child node
prepend()       // Add a new child node as the first child node
appendChild()       // Add a new child node as the last child node
removeChild()       // Remove a child node
replaceChild()      // Replace a child node
remove()            // Remove a node

createAttribute()   // Create an attribute node
createElement()     // Create an element node
createTextNode()    // Create a text node
getAttribute()      // Get the attribute value
setAttribute()      // Set the attribute value
```

Some common properties:

```js
innerHTML   // Content of an element, text or HTML
innerText   // All text Content of an element (only human readable elements)
textContent // All text Content of an element
nodeName    // Name of an element
nodeValue   // Value of an element
parentNode  // Parent node of an element
childNodes  // All child nodes
children    // Element child nodes
firstChild  // First child of an element
lastChild   // First child of an element
attributes  // Attribute nodes
```

Examples:

```html
...
  <img id="logo">
  <div id="my-div">
    <p class="box">first</p>
    <p class="box">second</p>
    <p class="box">third</p>
  </div>
...
```

```js
document.querySelector('#logo');        // Get refence to element with an id value "logo"
document.getElementById('logo');        // Get refence to element with an id value "logo"
document.querySelectorAll('.box');      // Get an array of refences to all elements with a class value "box"
document.getElementsByClassName('box'); // Get an array of refences to all elements with a class value "box"

const someNode = document.querySelector('#my-div'); // Assign the node ref to variable if found (id "my-div")
someNode.getElementsByTagName("p");                 // Get an array of refences to all p elements that are someNode children

const someOtherNode = document.createElement('p'); 
someOtherNode.innerText = 'Some new text content in my new element.';
someNode.appendChild(someOtherNode);    // add a new child node to someNode

someNode.removeChild(someOtherNode);    // remove the child node from someNode

document.getElementById("my-div").style.display= "none"; // hide div by changing the style
```

NOTE: The DOM must be ready (loaded completely by the browser) before we manipulate it. That's why we are using the `defer` keyword in our html from now on: `<script defer src="script.js" />`. ([Read more](https://javascript.info/script-async-defer).)

---

### Events & event handling

[MDN Event reference](https://developer.mozilla.org/en-US/docs/Web/Events)

- Event interface represents an event which takes place in the [DOM](https://developer.mozilla.org/en-US/docs/Glossary/DOM)
- [`EventTarget.addEventListener()`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) method is used to bind certain type of an event to a function that will be called whenever the specified event is delivered to the target
- Common event targets are DOM _elements_, _document_ object, and browser _window_
- almost everything happening on the web page generates an event and whenever there is an event, there is an opportunity for JavaScript to handle it, for example:
  - button clicked
  - user pressing key
  - user releasing key
  - mouse entering over an element
  - mouse moving
  - mouse double click
  - timer going off
  - data available
  - window resized or scrolled
  - etc...

#### Examples

```html
<html>
  <div id="my-div">Click here</div>
</html>
```

```js
// Get reference to element node we want to bind some event handling to
const targetElement = document.querySelector('#my-div');

// Create a function that gets called when an event occurs
function elementWasClicked() {
  console.log('Clicking the div');
}
// Bind the element and function for click event 
 targetElement.addEventListener('click', elementWasClicked);

// shorter version of the same thing using anonymous arrow function syntax
targetElement.addEventListener('click', () => {
  console.log('Clicking the div');
});
```

#### Event object

- An [event](https://developer.mozilla.org/en-US/docs/Web/API/Event) object holds data about the occurring event
- [List of Events and types](https://developer.mozilla.org/en-US/docs/Web/Events)

```js
// MouseEvent
document.querySelector('#theDiv').addEventListener('click', (event) => {
  console.log('event object', event);

// KeyboardEvent
document.addEventListener('keydown', event => {
  console.log('keydown:', event.key, event.keyCode);
  if (event.keyCode === 13) {
    console.log('You hit enter!');
  }
});
```

---

## Exercises

Create separate `.html` and `.js` files for the tasks.

### Task 1 - DOM

Just playing with the DOM nodes.

1. Create an html file that contains an ordered list of countries (5 or more) and an empty text paragraph to display some country related information. (Hint: use `ol` and `li` html elements for the list.)
2. Create a JS file and write code that does the following:
    1. Remove third item from list
    2. Add some new country to the list
    3. Change the backroud color of the html to light blue/red/green or something else
    4. Change the backround color of every other item in the list to grey (Hint: use a loop)
    5. Use array and loop to add alt least three more countries to the list

### Task 2 - Events

Continue from the previous task and add following functionalities to your code:

1. Hide the info paragraph at start
2. Find out the populations of the countries you have on your list and save the data to the application
3. User can select a country by pointing with mouse cursor (`mouseover` event). Display the population of the selected country in the info paragraph.
4. Create an image element for displaying the flag of selected country
   - Display the flag of country only when user is pointing to it (just like population text)
   - Hide otherwise
   - you can use [Flagpedia](https://flagpedia.net/download/api) for flag image (e.g. `<img src="https://flagcdn.com/72x54/fi.png" />` in html displays the flag of Finland)
