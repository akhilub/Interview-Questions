
## 1. What is Callback Hell ? How can you avoid it?

## 2. What is the difference between Promise and Callbacks?

Callbacks and Promisese are two popular approaches to handling asynchronous operations in programming. While they share some similarities they have distinct differences in their design, usage and benefits

**Callbacks**

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

**Promises**

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

**Comparison**

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






 

