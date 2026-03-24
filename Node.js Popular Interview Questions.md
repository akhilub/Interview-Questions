---
excalidraw-plugin: parsed
tags:
  - excalidraw
---
# Node.js Basics

## 1. What is Node.js ?

Node/Node.js is a runtime enviroment for executing JS code on the server side.

It is neither a language nor a framework

## 2. How Node is a runtime enviroment on server side? What is V8?

Like Browsers executes JS on the client side, Similarly Node.js executes JS on the server-side.

V8 is a JS engine for the JS language.

## 3. What is the difference between runtime environment and frameworks?









## 1. What is Callback Hell ? How can you avoid it?

## 2. What is the difference between Promise and Callbacks?

Callbacks and Promises are two popular approaches to handling asynchronous operations in programming. While they share some similarities they have distinct differences in their design, usage and benefits

### **Callbacks**

A callback is a function passed as an argument to another function, which is executed when a specific operation is completed. 
Callbacks are often used in asynchronous programming to handle the result of operation.

**Key characteristics:**

- A function is passed as an argument to another function
- The callback function is executed when the operation is completed
- Error handling is typically done through a separate error callback or` try-catch` block

Example

```js
const fs = require('fs/promises');

fs.readFile('file.txt', (err, data) => {
	if (err){
		console.log(err);
	} else {
		console.log(data)
	}
});
```

### **Promises**

A promise is an object that represents a value that may not be available yet, but will be resolved at some point in the future. 
Promises provide a way to handle asynchronous operations in a more structured and readable way.

**Key Characteristics**

- A promise object is returned by a function.
- The promise has three states: pending, fulfilled(resolved), and rejected.
- The `.then()` method is used to handle the resolved values, and the `catch()` method is used to handle errors.

Example

```js
const fs = require('fs').promises;

fs.readFile('file.txt')
	.then((data) => console.log(data))
	.catch((err) => console.log(err));
```

### **Comparison**

| Features       | Callbacks                                                    | Promises                                                                      |
| -------------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| Design         | A function is passed as an argument                          | A promise object is returned                                                  |
| Error Handling | is done through a separate error callback or try-catch block | is done through the `catch()`                                                 |
| Readability    | can lead to callback hell if not managed properly            | provides a more structured and readable way to handle asynchronous operations |
| Chaining       | difficult to chain multiple asynchronous operations          | easy to chain multiple asynchronous operations using `then()`.                |

### **When to use**

| Callbacks                                                              | Promises                                                                          |
| ---------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| when you're working with a legacy codebase that uses callback          | when you need to handle a simple asynchronous operation without a single callback |
| when you're working with modern JS or a language that support promises | when you need to handle complex asynchronous operations with multiple callbacks   |

### **In summary** 

Promises are a modern and recommended approach to handling asynchronous operations, as they provide a more structured and readable way to write code.

However, callbacks are still widely used, and its essential to understand both concepts to work efficiently with asynchronous programming.


## What is Event Loop in Node.js?


References

![Reference|595](https://www.youtube.com/watch?v=Vdpx-9Oehdk&list=PL3aZbxdSiCbOBbNqpsFmn9aUQUcYmg7Kz)

This directly works on Obsidian-Markdown to embed a url

<iframe
border=0
crossborder=0
height=400
width=600
src = "https://github.com/becodewala-youtube/130-Nodejs-Interview-Questions-with-Answer">
</iframe>



References on  How To Embed

<iframe 
width="560" 
height="315" 
src="https://www.youtube.com/embed/HE8Sp41_XnQ?si=qoSWeIg5joasEB_n" 
title="YouTube video player" 
frameborder="0" 
allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
referrerpolicy="strict-origin-when-cross-origin" 
allowfullscreen>
</iframe>




![[Node.js Popular Interview Questions#^eab5a1]]






==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
## Element Links
JAKjFMqS: https://github.com/becodewala-youtube/130-Nodejs-Interview-Questions-with-Answer ^eab5a1

GohGmGP5: https://www.youtube.com/watch?v=Vdpx-9Oehdk&list=PL3aZbxdSiCbOBbNqpsFmn9aUQUcYmg7Kz

## Drawing
```compressed-json
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
```
%%