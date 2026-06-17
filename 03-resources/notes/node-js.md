---
mocs:
    - "[[public-notes/03-resources/backend.moc.md|Backend]]"
tags:
    - dev/backend
---

## 1. Intro
+ cross-platform JavaScript runtime environment
+ runs the V8 JavaScript engine
+ A Node.js app runs in a single process, without creating a new thread for every request
+  Node.js provides a set of asynchronous I/O primitives in its standard library
### Blocking vs Non-Blocking Behavior
+ **Blocking Model**: I/O operations are executed sequentially. This means the program waits for an operation to complete before moving on to the next one.
+ **non-Blocking (Node.js)**: I/O operations are executed asynchronously. This means the program can continue executing while waiting for an I/O operation to complete.
## Global Variables
`__dirname`,`__filename`,`require`,`process`,`console.log`,`setInterval`, `setTimeout`,`module` 

## Modules
+ **CommonJs**: `require()`, `module.exports = { }` or `module.exports = x`(export default)
+ **ES6**: `import x from y`, `export`

## Built-in Modules
+ os
+ path
+ **fs**:  Functionalities to interact with the file ssytem
+ http