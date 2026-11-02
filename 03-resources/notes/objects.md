---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/javascript
---

## 12. Objects
+ keyed collections of various data and more complex entities.
+ We can implement a hashmap using object literals :D: in, delete
+ empty object
```javascript
let user = new Object(); // "object constructor" syntax
let user = {};  // "object literal" syntax
```
+ Delete property `delete user.age;`
### Multi-word properties
+ We can use multi-word property names (must be quoted) `"likes birds": true`
+ Access multi-word property names, use square bracket notation
```javascript
let user = {};
// set
user["likes birds"] = true;
// get
alert(user["likes birds"]); // true
// delete
delete user["likes birds"];
```
### Computed properties
```javascript
let fruit = prompt("Which fruit to buy?", "apple");
let bag = {
  [fruit]: 5, // the name of the property is taken from the variable fruit
};
alert( bag.apple ); // 5 if fruit="apple"
```

Works the same as:
```javascript
let fruit = prompt("Which fruit to buy?", "apple");
let bag = {};

// take property name from the fruit variable
bag[fruit] = 5;
```

We can use more complex expressions inside square brackets:
```javascript
let fruit = 'apple';
let bag = {
  [fruit + 'Computers']: 5 // bag.appleComputers = 5
};
```

### Property value shorthand
Instead of name:name we can just write name, like this:
```javascript
function makeUser(name, age) {
  return {
    name, // same as name: name
    age,  // same as age: age
    // ...
  };
}
```

### Test Existence
`"key" in object`

### For in Loop
+ To walk over all keys of an object
```javascript
for (key in object) {
  // executes the body for each key among object properties
}

for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // values for the keys
  alert( user[key] ); // John, 30, true
}
```
## 13. Object References and copying
### Reference vs Primitives 
+ objects versus primitives is that objects are stored and copied “by reference”
+ primitive values: strings, numbers, booleans, etc – are always copied “as a whole value”.

> [!WARNING]
> Objects are not like that.

> A variable assigned to an object stores not the object itself, but its “address in memory” – in other words “a reference” to it.

+ When an object variable is copied, the reference is copied, but the object itself is not duplicated.
```javascript
let user = { name: "John" };
let admin = user; // copy the reference
```
+ Now we have two variables, each storing a reference to the same object
+ If we make changes to the object properties in one of its variables, we are modifying the same object
### Comparison by reference
+ Two objects are equal only if they are the same object.
```javascript
let a = {};
let b = a; // copy the reference

alert( a == b ); // true, both variables reference the same object
alert( a === b ); // true
```

```javascript
let a = {};
let b = {}; // two independent objects

alert( a == b ); // false
```

> [!IMPORTANT]
> An important side effect of storing objects as references is that an object declared as const can be modified.

### Cloning and Merging objects
+ We can clone an object by iterating
+ Or we can use `Object.assign(dest, ...sources)`
	+ dest is a target object
	+ Further arguments is a list of source objects.
	+ If the copied property name already exists, it gets overwritten
+ For nested objects use **structured cloning** to clone them 
## 14. Garbage Collection
+ The main concept of memory management in JavaScript is reachability.
## 15. Object methods, "this"
+ Since objects represents real world entities, we can use its properties to define behavior (functions)
+ Functions that are stored in object properties are called “methods”.
```javascript
let user = {
  name: "John",
  age: 30
};

user.sayHi = function() {
  alert("Hello!");
};

user.sayHi(); // Hello!
```
### Method Shorthand
```javascript
// these objects do the same

user = {
  sayHi: function() {
    alert("Hello");
  }
};

// method shorthand looks better, right?
user = {
  sayHi() { // same as "sayHi: function(){...}"
    alert("Hello");
  }
};
```
### This
+ Open recursion in OOP
+ A method access a method or property of itself
+ **Unbound this**: In JavaScript, `this` keyword this behaves unlike most other programming languages. It can be used in any function, even if it’s not a method of an object.

```javascript
let user = { name: "John" };
let admin = { name: "Admin" };

function sayHi() {
  alert( this.name );
}

// use the same function in two objects
user.f = sayHi;
admin.f = sayHi;

// these calls have different this
// "this" inside the function is the object "before the dot"
user.f(); // John  (this == user)
admin.f(); // Admin  (this == admin)

admin['f'](); // Admin (dot or square brackets access the method – doesn't matter)
```

> [!DANGER]
> Calling without an object: this == undefined

+ If you come from another programming language, then you are probably used to the idea of a "bound this", where methods defined in an object always have this referencing that object.
+ In JavaScript this is “free”, its value is evaluated at call-time and does not depend on where the method was declared, but rather on what object is “before the dot”
+ The concept of run-time evaluated `this` has both pluses and minuses. On the one hand, a function can be reused for different objects. On the other hand, the greater flexibility creates more possibilities for mistakes.

> [!WARNING]
> Arrow Functions don't have this

An use case of `this` is allow method chaining
```javascript
let ladder = {
  step: 0,
  up() {
    this.step++;
    return this;
  },
  down() {
    this.step--;
    return this;
  },
  showStep() {
    alert( this.step );
    return this;
  }
};

ladder.up().up().down().showStep().down().showStep(); // shows 1 then 0
```
## 16. Constructor, operator "new"
+ Object literals allow us to create objects, but sometimes we need to create similar objects
+ That can be done using constructor functions, to implement reusable object creation code.
### Constructor functions
+ Technically are regular functions
conventions:
+ They're name with capital letter first
+ They should be executed only with `"new"` operator

```javascript
function User(name) {
  this.name = name;
  this.isAdmin = false;
}

let user = new User("Jack");

alert(user.name); // Jack
alert(user.isAdmin); // false
```

When a function is executed with `new`, it does the following steps:

1. A new empty object is created and assigned to `this`.
2. The function body executes. Usually it modifies `this`, adds new properties to it.
3. The value of `this` is returned.

> [!DANGER]
> We cannot use arrow functions, since they don´t have `this`

> [!NOTE]
> We there is a function definition with: `new function() { … }` then This constructor can’t be called again, because it is not saved anywhere, just created and called. So this trick aims to encapsulate the code that constructs the single object, without future reuse.
## 17. Optional Chaining "?."
+ safe way to access nested object properties
+ stops the evaluation if the value before ?. is undefined or null and returns undefined.
+ Other variants `?.()` for methods, `?.[]` if we’d like to use brackets [] to access properties instead of dot 

```javascript
delete user?.name; // delete user.name if user exists
```

> [!WARNING]
> We should use ?. only where it’s ok that something doesn’t exist.
## 18. Symbol
+ Only two primitive types can be object property keys: **string**, **symbol**
+ Symbol is a primitive unique value with an optional description that can be used as the key for an objetct
+ Symbol represents a unique identifier

> Symbols are guaranteed to be unique. Even if we create many symbols with exactly the same description

### Hidden properties
```javascript
let id = Symbol("id");

let user = {
  name: "John",
  [id]: 123 // not "id": 123
};
```
+ Also ==Symbols are skipped in `for .. in`== only direct access works
+ But `Object.assing` copies both string
### Global Symbols
+ We can have the same symbol for the same description with `Symbol.for()`, like Ruby Symbols
+ Symbol.keyFor(sym) given a symbol, it return its key (description)
## 19. Object to primitive conversion
+ no conversion to boolean. All objects are true
+ only numeric and string conversion
When it ocurrs?
+ The numeric conversion happens when we subtract objects or apply mathematical functions. for instance, Date objs can be subtracted date1 - date2
+ For string conversion usually happens wen `alert(obj)`
**We can implement this kinds of conversions by ourselves, using special object methods**
To do the conversion, JavaScript tries to find and call three object methods:
1. Call `obj[Symbol.toPrimitive](hint)` – the method with the symbolic key Symbol.toPrimitive (system symbol), if such method exists,
2.  if hint is "string" -> try calling obj.toString() or obj.valueOf(), whatever exists.
3. If hint is "number" or "default" -> try calling obj.valueOf() or obj.toString(), whatever exists.
