---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/javascript
---

## 1. Hello World
```JavaScript
console.log('Hello, World!');
```

## 2. Strict
+ we can se `'use strict';` at the start of our script or at  the top of a block o code, this means that the js engine will ignore the old javascript and use only the new
+ However if we use Classes or modules this automatically behaves if we are using `'use strict';`
## 3. Vars
+ `let`,`const`,`var`. (`var`has no block scope)
## 4. Data Types
### Primitives
+ String
+ Number
+ BigInt, we have to append `n` to the end of the number
	+ Was created to avoid overflow errors
	```JavaScript
	console.log(9007199254740991 + 1); // 9007199254740992
	console.log(9007199254740991 + 2); // 9007199254740992
	```
	+ `const bigInt = 1234567890123456789012345678901234567890n;`
+ Boolean
+ null
+ undefined -> value is not assigned
+ Symbol -> Unique identifier
### Non-primitive
+ Objects
	+ use `typeof`  operator

## 5. Type Conversion
+ Using type constructors `Number()`, `String()`
+ Implicit conversion, applying number operators e.g
```JavaScript
let apples = "2";
let oranges = "3";

// both values converted to numbers before the binary plus
alert( +apples + +oranges ); // 5
```
## 6. Operators
+ **Precedence**: Unary Operators > Binary Ones. e.g: +a (unary) > (binary) a+b
+ **Assignment**: any javascript expression returns a value
```Javascript
let a = 1;
let b = 2;
let c = 3 - (a = b + 1);

alert( a ); // 3
alert( c ); // 0
``` 
+ Hence, we have chaining assignments
```javascript
let a, b, c;

a = b = c = 2 + 2;

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```
+ Bitwise ops: `&,|,~,^,<<,>>,>>>`
+ **Comma** -> Evaluates several expressions dividing them with a comma `,`. Each of them is evaluated, only the result of the last is returned
	+ **Caution** -> comma has very low precedence, parentheses matters
	+ Without them: `a = 1 + 2, 3 + 4` evaluates `+` first, summing the numbers into `a = 3, 7`, then the assignment operator `=` assigns `a = 7`, (the last value between 3,7 is 7) and the rest is ignored. It’s like `(a = 1 + 2), 3 + 4`.
	+ Sometimes its useful to put several actions in one line
```Javascript
// three operations in one line
for (a = 1, b = 3, c = a * b; a < 10; a++) {
 ...
}
```
## 7. Comparisons
+ Strict equality to avoid unexpected behavior
+ Don’t use comparisons >= > < <= with a variable which may be null/undefined, unless you’re really sure of what you’re doing. If a variable can have these values, check for them separately.
## 8. Conditional Branching
+ `if`,`else`,`else if`,`swith-case`,`&&`
+ **Ternary operator**: `let result = condition ? value1 : value2;`
+ **Multiple ternaries**:
```javascript
let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';
```
+ **Logical Operators**: Short circuit evaluation
	+ `||` returns the first truthy value or the last value if the exp is false
	+ `&&` returns the first falsy value or the last value if the exp is true
	+ **Double not** sometimes is used to converts a value to Boolean
	+ `!`> `&&`>`||` precendence
## 9. Nullish Coalescing Operator "??"
+ `a ?? b`
+ Returns the first value if is neither `null` nor `undefined`
```javascript
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// shows the first defined value:
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder
```
+ important difference with logical OR, OR doesn't distinguish between `false`,`0`,`""` and `null / undefined`
```javascript
let height = 0;
alert(height || 100); // 100
alert(height ?? 100); // 0
```
## 10. Loops
+ while
+ for
+ do-while
+ keywords: break, continue
+ breaking multiple-nested loops, label a loop
## 11. Functions
### a. Function Declarations
```javascript
function sayHi() {
  alert( "Hello" );
}
```
### b. Function Expressions
It allows us to create a new function in the middle of any expression.
```javascript
let sayHi = function() {
  alert( "Hello" );
};
```
### c. Call Back Functions
The idea is that we pass a function as an argument and expect it to be “called back”
### Function Declarations vs Function Expressions
+ A Function Expression is created when the execution reaches it and is usable only from that moment.
+ A Function Declaration can be called earlier than it is defined.
### d. Arrow Functions
+ `let func = (arg1, arg2, ..., argN) => expression;`


