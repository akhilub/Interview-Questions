
## 1. What is Callback Hell ? How can you avoid it?

## 2. What is the difference between Promise and Callbacks?

Callbacks and Promisese are two popular approaches to handling asynchronous operations in programming. While they share some similarities they have distinct differences in their design, usage and benefits

**Callbacks**

A callback is a function passed as an argument to another function, which is executed when a specific operation is completed. 

- Callbacks are often used in asynchronous programming to handle the result of operation.
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

**Promises**

A promise is an object that represents a value that may not be available yet, but will be resolved at some point in the future. 
Promises provide a way to handle asynchronous operations in a more structured and readable way.

**Key Characteristics**

- A promise object is returned by a function.
- The promise has three states: pending, fulfilled(resolved), and rejected.
- The




 

