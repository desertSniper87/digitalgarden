---
{"dg-publish":true,"permalink":"/javascript/promise/","tags":"gardenEntry"}
---



## Docs

### 1. [Promise - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

The **`Promise`** object represents the _eventual completion (or failure)_ of an asynchronous operation and its resulting value.

A **`Promise`** is a _proxy_ for a value not necessarily known when the _promise is created_. It allows you to associate _handlers_ with an asynchronous action's eventual success value or failure reason. This lets _asynchronous methods_ return values like synchronous methods: instead of _immediately_ returning the final value, the asynchronous method _returns a_ __promise__ to supply the value at some point in the future.

2. [JavaScript Promises](https://www.w3schools.com/js/js_promise.asp)

### 3. [Promise](https://javascript.info/promise-basics)



## Videos

### [JavaScript Promises In 10 Minutes - YouTube](https://www.youtube.com/watch?v=DHvZLI7Db8E)

```js
let p = new Promise((resolve, reject) => {
	let a = 1+1;
	if (a == 2) {
		resolve ('Success')
	} else {
		reject ('Failure')
	}
})

p.then(message => console.log('Hello there ' + message))

```

