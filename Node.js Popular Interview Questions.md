---
excalidraw-plugin: parsed
tags:
  - excalidraw
excalidraw-open-md: true
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



%% 

==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'

# Excalidraw Data

## Text Elements
## Element Links
JAKjFMqS: https://github.com/becodewala-youtube/130-Nodejs-Interview-Questions-with-Answer

GohGmGP5: https://www.youtube.com/watch?v=Vdpx-9Oehdk&list=PL3aZbxdSiCbOBbNqpsFmn9aUQUcYmg7Kz

%%

%%
## Drawing
```compressed-json
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=
```
%%