---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/javascript
---

# Asynchronous JavaScript
+ Since js is single-threaded we need Asynchronous JavaScript to manage functions or code that takes long time in order to don't block the thread
## Callback hell or callback piramid
![[Pasted image 20240815111623.png]]
## Promises
+ Foundation of asynchronous programming in modern JavaScript
+ forma en la que javascript gestiona el asincronismo
+ Is an object returned by an asynchronous function, which represents the current state of the operation
+ promise object provides methods to handle the eventual success or failure of the operation.
+ ej: `fetch` return a promise
+ Alternativa para solucionar el callback hell

## .then() y .catch()
+ Forma de gestionar las promesas
+ Después de una función que retorna una promesa
+ Una vez que la promesa se resuelva (de forma exitosa) se va a ejecutar lo que esta en el `.then()`
+ Dentro del then() pasamos un callback (generalmente arrow function) para que se ejecute cuando la promesa se resuelva
	+ Si la función que esta retornando la promesa retorna datos, el callback tendrá un parámetro
## Chaining promises
To avoid "called back hell" We should rewrite it as:
```javascript
fetchPromise
  .then((response) => response.json())
  .then((data) => {
    console.log(data[0].name);
  });
```

> Instead of calling the second then() inside the handler for the first then(), we can return the promise returned by json(), and call the second then() on that return value. This is called promise chaining and means we can avoid ever-increasing levels of indentation when we need to make consecutive asynchronous function calls.

## Handling Errors `.catch()`
+ To support error handling, `Promise` objects provide a [`catch()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/catch) method
+ add catch() to the end of a promise chain
## Combining multiple promises
+ Different from promise chain which is what you need when your operation consists of several asynchronous functions, and you need each one to complete before starting the next one

> there are other ways you might need to combine asynchronous function calls, and the Promise API provides some helpers for them.

#### `Promise.all()`
+ The promise returned by Promise.all() is:
	+ **Fulfilled** when and if _all_ the promises in the array are fulfilled. In this case, the `then()` handler is called with an array of all the responses, in the same order that the promises were passed into `all()`
	+ **rejected** when and if _any_ of the promises in the array are rejected. In this case, the `catch()` handler is called with the error thrown by the promise that rejected.
	
```javascript
const fetchPromise1 = fetch(
  "https://mdn.github.io/learning-area/javascript/apis/fetching-data/can-store/products.json",
);
const fetchPromise2 = fetch(
  "https://mdn.github.io/learning-area/javascript/apis/fetching-data/can-store/not-found",
);
const fetchPromise3 = fetch(
  "https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json",
);

Promise.all([fetchPromise1, fetchPromise2, fetchPromise3])
  .then((responses) => {
    for (const response of responses) {
      console.log(`${response.url}: ${response.status}`);
    }
  })
  .catch((error) => {
    console.error(`Failed to fetch: ${error}`);
  });

```

#### `Promise.any()`
+ is like Promise.all(), except that it is fulfilled as soon as any of the array of promises is fulfilled, or rejected if all of them are rejected:

##  `async` and `await`
+ Adding async at the start of a function makes it an async function
+ Inside an async function, you can use the await keyword before a call to a function that returns a promise.
+ We can even use a try...catch block for error handling, exactly as we would if the code were synchronous.
+ note that you can only use await inside an async function, unless your code is in a JavaScript module.
+ just like a promise chain, await forces asynchronous operations to be completed in series. This is necessary if the result of the next operation depends on the result of the last one
	+ but if that's not the case then something like Promise.all() will be more performant.
### Resources
+ https://www.youtube.com/watch?v=RvYYCGs45L4 - JavaScript Promise in 100 Seconds (Fireship)
