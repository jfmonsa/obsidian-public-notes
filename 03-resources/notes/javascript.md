---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/javascript
---

+ High level
+ Single Threaded (Or multi threaded also: using workers in node and web workers in browser)
+ Garbage collected
+ interpreted and compiled (just-in-time JIT)
+ Prototype-based, multi-paradigm (OOP, imperative, declarative e.g functional 
+ Dynamic Language, Weak Typed
+ Non-blocking event loop
---
+ ==First-class Functions==, This means:
	+ Functions are treated like any other variable
	+ we can pass it as arguments, we can return them
+ Run time environments (Javascript engines): ==Browser and Node.js== )

# 1 - [[core-language]]
+ strict, vars, data types, casting, operators, comparisons, conditional branching, ??, loops, functions
# 2. [[objects]]
+ Objects: computed properties, methods; Object references and copying, memory management (reachability),  this and method shorthands, constructor operator (new), Optional chaining (?.), Symbol, object to primitive conversion (to number or strings)
# - [[asynchronous-javascript]]
# Event Loop
+ El event loop es el que se encarga de implementar las operaciones asíncronas o el non-blocking. El event loop corre en el único hilo que existe en Node y como mencionamos anteriormente, al bloquear el único hilo de node, estamos bloqueando el event loop.
+ **Call Stack**: Cada vez que una función va a ser ejecutada pasa por el call stack.
+ **Callback Queue**: Aquí se agregan los callback o funciones que se ejecutan una vez las operaciones asíncronas hayan terminado

> El event loop es el que se encarga de revisar que el call stack este vacío para añadir lo que está dentro del callback queue y ejecutarlo.
# Browser
## Console
+ If we use `Shift + Enter`we can write multi-line code in the console

# Web Workers  / Wokers
## Concurrency vs Parallelism
+ Both refer to doing things at the same time

![[Pasted image 20241012101331.png]]
### Concurrency
+ JS can run code concurrently usign a single thread thanks to the ==event loop==
+ use only one cpu core

### Paralelism
+ Uses multiple cpu cores that otherwise will block the main thread
+ Ideal when you have multiple cpu-intensive work at the same time
+ not useful for I/O output operations (reading / writing from DB or disks) because it no depends on cpu
+ n available cores depends on ==actual physical cores of cpu==


# Quick Methods to learn
+ **num.toFixed(n)** truncates num to n decimals
+ **arr.splice(a, b)**: remove elems from elms[a] to elms[b-1] and returns and array of removed elems
+ arr.slice(a,b) returns new arr copying all items from elms[a] to elms[b-1]
+ arr.forEach( fn(item, idx, arr))
+ **arr.find(fn )** return the elm if found it
+ arr.sort(): sort array in place, items are sorted as strings by default, so provide a function arg arr.sort( (a,b) => a-b )
+ arr.reverse() reverse the order of elements in an array
+ str.split(), arr.join('')
+ arr.reduce( fn(acc, item, idx, arr), acc): used to calc a single value

```javascript
function compare(a, b) {
  if (a > b) return 1; // if the first value is greater than the second
  if (a == b) return 0; // if values are equal
  if (a < b) return -1; // if the first value is less than the second
}
```

arr.some( )
arr.sort()
arr.reduce( fn, acc)

**Tarea**: recrear estas funciones en golang

# DOM
+ `document` object is the entry point
![[Pasted image 20250522111131.png]]
+ DOM collections are no arrays but array-like iterable objects, so we can use for of
	+ are **read-only**
	+ collections are live
+ `Array.from` to create a “real” array from the collection, if we want array methods:

### Access Elements, exercise
+ For each tag provide a way to access it

```html
<html>
<body>
  <div>Users:</div>
  <ul>
    <li>John</li>
    <li>Pete</li>
  </ul>
</body>
</html>
```

```js
// div
document.body.firstElementChild
document.body.children[0]
document.body.childNodes[1] // becachuse childNodes[0] is "\n" char

// ul
document.body.lastElementChild
document.body.children[1]

// li
document.body.lastElementChild.lastElementChild
```

### Query
+ getElementById <- return the element
+ querySelectorAll(<css selector (string)>) <- return a collection
+ querySelector <- first coincidence
---
+ querySelectorAll: return static collection
+ getElementBy*: return live collection

### DOM Node Classes
+ Class hierarchy
![[Pasted image 20250522120948.png]]