## 1.  What are Events in JS or DOM events? 

### Events in JavaScript

Events are actions or occurrences that happen in the browser, such as a 
- button click
- mouse movement
- keyboard input
- loading a webpage
- submitting form

These events can be used to trigger JS code to execute.

```html
<button id="myButton">Click Me</button>
```

```js
// Get the reference of button in a variable
var button = document.getElementById("myButton");

//Attach an event handler to the button
button.addEventListener("click", handleClick);

// Event handler function
function handleClick() {
	alert("Button Clicked");
}
```
---
## 2. What are the types of events in JavaScript?

### Types of Events

There are several types of events in JavaScript, including:

* **Mouse Events**: click, dblclick, mousedown, mouseup, mouseover, mouseout

```
Click Event : addEventListener('click', handeler)
Mouseover Event : addEventListener('mouseover', handler)
```
* **Keyboard Events**: keydown, keyup, keypress

```
Keydown Event : addEventListener('keydown', handler)
Keyup Event : addEventListener('keyup', handler)
```
* **Form Events**: submit, reset, change, input, focus, blur,

```
Submit Event : addEventListener('submit', handler)
```
* **Window Events**: load, unload, resize, scroll

 ```
 Load Event : addEventListener('load', handler)
 ```
* **Touch Events**: touchstart, touchend, touchmove, touchcancel

---
## 3. How Events are Triggered in JavaScript

Events are triggered in JavaScript through the following process:

1. **Event Creation**: The browser creates an event object when an event occurs.
2. **Event Target**: The event object is targeted at a specific element in the DOM, known as the event target.
3. **Event Propagation**: The event object is propagated through the DOM tree, allowing parent elements to capture and handle the event.
4. **Event Handling**: The event object is passed to an event handler function, which is a JavaScript function that is designed to handle the event.

---
## Event Handling Mechanisms

There are two main event handling mechanisms in JavaScript:

* **Event Listeners**: Also known as event handlers, these are functions that are attached to an element and are triggered when an event occurs.
* **Event Delegation**: This is a technique where an event listener is attached to a parent element, and the event is handled based on the target element.

---
## 4. What is **`addEventListener()`** ?

### Adding Event Listeners

Event listeners can be added to an element using the following methods:

* **addEventListener()**: This method allows you to add an event listener to an element without overwriting the existing ones.
* **attachEvent()**: This method is used in older versions of Internet Explorer.

### Example


```javascript
// Get the button element
const button = document.getElementById('myButton');

// Add an event listener to the button
button.addEventListener('click', function() {
  console.log('Button clicked!');
});
```

---

##  5. What is Event Object in JS?

Whenever any event is triggered, the browser automatically creates an event object and **passes it as an argument** to the event handler function.

The event object contains various properties and methods that provide information about the event, such as the type of event, the element that triggered the event.

### Event Object Properties

The event object passed to an event handler function has several properties, including:

* **target**: The element that triggered the event.
* **currentTarget**: The element that is currently handling the event.
* **type**: The type of event that occurred.
* **timestamp**: The time at which the event occurred.

### Example

```html
<button id="myButton">Click Me</button>
```

```javascript
// Get the button element
const button = document.getElementById('myButton');

// Add an event listener to the button
button.addEventListener('click', function(event) {
  // Accessing properties of the event object
  console.log(`Event type: ${event.type}`);
  console.log(`Target element: ${event.target}`);
});
```

---
## 6. What is Event Delegation in JS?

Event delegation is a technique where you attach a single event listener to a parent element to handle events on its child elements

```html
<ul id="list">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

```js
var parentList = document.getElementById("list");

//Attach event handler to the parent element
parentList.addEventListener("click", handleItemClick);

//Event handler function
function handleItemClick(e) {
	console.log("You Clicked", e.target.textContext);
}
```

---
## 7. What is Event Bubbling in JS?
## What is Event Capturing in JS?

These define the **order of event propagation** in the DOM.

### **Event Bubbling (Default)**:

- It is the process in JS where an event triggered on a child element **propagates up the DOM tree**, triggering event handlers on its parent elements
- The event starts at the target element and bubbles up to the root.

**Example**

```html
<div id = "outer">
	<div id = "inner">
		<button id = "myButton">Click Me</button>
	</div>
</div>
```

```js
//Get the reference of the elements

var outer = document.getElementById("outer");
var inner = document.getElementById("inner");
var button = document.getElementById("myButton");

// Attach event handler with elements

outer.addEventListener("click", handleBubbling);
inner.addEventListener("click", handleBubbling);
button.addEventListener("click", handleBubbling);

function handleBubbling (event) {
	console.log("Bubbling :" + this.id);
}
```

### **Event Capturing:**

- It is the process in JS where an event is handled starting from the highest-level ancestor (the root of the DOM tree ) and moving down to the target element.
- The event is captured from the **root** to the **target**.

**Example**

```html
<div id = "outer">
	<div id = "inner">
		<button id = "myButton">Click Me</button>
	</div>
</div>
```

```js
//Get the reference of the elements

var outer = document.getElementById("outer");
var inner = document.getElementById("inner");
var button = document.getElementById("myButton");

// Attach event handler with elements

outer.addEventListener("click", handleCapture, true);
inner.addEventListener("click", handleCapture, true);
button.addEventListener("click", handleCapture, true);

function handleBubbling (event) {
	console.log("Capturing :" + this.id);
}
```
---
## 8. How can you stop event propagation or event bubbling in JS?

- Use `event.stopPropagation()` method to **stop bubbling** or **capturing** on the event object.

```js
function handleBubbling (event) {
	console.log("Bubbling :" + this.id);
	event.stopPropogation(); //Stop event propogation
}
```
---
## 9. What is the purpose of the `event.preventDefault()` method in JS?

## Preventing Default Behavior

The `event.preventDefault()` method is used to **prevent the default behavior** of an event and the link click will be be prevented.

OR

Some events have a default behavior associated with them, such as submitting a form or following a link. You can prevent this default behavior using the **event.preventDefault()** method.

### Example

```html
<a href ="https://akhilsin.com/" id ="myLink"> Click Me</a>
```

```javascript
// Get the link element
const link = document.getElementById('myLink');

// Add an event listener to the link
link.addEventListener('click', function(event) {
  event.preventDefault(); // Prevent default action 
  
  // Perform cluster before
  console.log('Link clicked, but default behavior prevented!');
});
```

## 10. What is the use of `this` keyword in the context of event handling in JS?

`this` keyword refers to the element that the event handler is attached to 

```html
<button id="myButton">Click Me</button>
```

```js
// Get the reference of button in a variable
var button = document.getElementById("myButton");

//Attach an event handler to the button
button.addEventListener("click", handler);

// Event handler function
function handler(event) {
	console.log("Clicked :", this.id)
	this.disabled = true;
}
```
---

## 11. How to remove an event handler from an element in JS?

`removeEventListner()` method is used to remove event handler from element


```html
<button id="myButton">Click Me</button>
```

```js
// Get the reference of button in a variable
var button = document.getElementById("myButton");

//Attach an event handler to the button
button.addEventListener("click", handleClick);

// Event handler function
function handleClick() {
	alert("Button Clicked");
}

// Remove the event handler
button.removeEventListener("click", handleClick);
```




# ✅ Common Interview Coding Challenges


## Reverse a String

```js
const reverseString = (str) => {
	return str.split('').reverse().join('');
}

console.log(reverseString("hello")); // "olleh"
```


## Check if a String is a Palindrome

```js
const isPalindrome = (str) => {
	return str === str.split("").reverse().join("");
}
console.log(isPalindrome("racecar")) // true
```

## Factorial of a Number

```js
const factorial = (n) => {
	if (n===0) || (n===1) {
		return 1;
	}
	return n * factorial(n - 1);
}

console.log(factorial(5)); // 120
```


### Find the largest/smallest number in an array

```js
const findMinMax = (arr) {
	if (arr.length == 0) {
		return {smallest : null, largest : null};
	}
	
	let minX = arr[0];
	let maxX = arr[0];
	
	for (let i=1; i <= arr.length ; i++){
		if (arr[i] < minX) minX = arr[i];
		if (arr[i] > maxX) maxX = arr[i];
	}
	
	return {minX, maxX}
	
}

const arr = [4, 2, 9, 1, 7, 5, 12, 3]; 
const result = findMinMax(arr);
```

OR

```js
const arr = [5, 2, 9, 1];
console.log(Math.max(...arr)); // 9
console.log(Math.min(...arr)); // 1
```
## References

https://github.com/becodewala-youtube/200-JavaScript-Interview-Questions-with-Answer


https://www.youtube.com/watch?v=AUTO7ALJk2U&t=9936s

