---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/typescript
---

## Primitive Types
+ Javascript: `boolean`, `bigint`, `null`, `number`, `string`, `symbol`, and `undefined`, which you can use in an interface.
+ TypeScript extends this list with a few more, such as `any` (allow anything), [`unknown`](https://www.typescriptlang.org/play#example/unknown-and-never) (ensure someone using this type declares what the type is), [`never`](https://www.typescriptlang.org/play#example/unknown-and-never) (it’s not possible that this type could happen), and `void` (a function which returns `undefined` or has no return value).
## Type inference
+ Una vez declaras una variable con un tipo primitivo, TS infiere el tipo y vigila que nunca usemos otro
```typescript
const text = "This is text";
```
## Explicit Type Declaration
```typescript
const n1: number = 123;
```

+ you can use interfaces or types
### Interfaces
```ts
interface User {  name: string;  id: number;}
```
1. Define the shape of an object

**In a more OOP way...**
1. Also, Acts as a contract by enforcing a particular shape on a class or a specific type on a function or variable. Classes that “implement” another class must declare all the properties present in the class they implement.

```ts
interface User {  name: string; id: number;}

class UserAccount {
	name: string;
	id: number;
constructor(name: string, id: number) {
	this.name = name;
	this.id = id;}
}

const user: User = new UserAccount("Murphy", 1);
```

You can use interfaces to annotate parameters and return values to functions:
```ts
function deleteUser(user: User) {
// ...
}

function getAdminUser(): User {
//...
}
```

### Types
+ create complex types by combining simple ones

#### Unions
```ts
type WindowStates = "open" | "closed" | "minimized";
type LockStates = "locked" | "unlocked";
```

#### Generics
Generics in TypeScript enable writing code that can work with a variety of data types while maintaining type safety. They allow the creation of reusable components, functions, and data structures without sacrificing type checking.

+ represente by `<>`
```typescript
function identity<T>(arg: T): T {
    return arg;
}

let output = identity<string>("hello");
console.log(output); // Output: hello
```

Aquí, `T` es el tipo genérico que representa cualquier tipo que le pases. Si llamas a esta función con un `number`, `T` se convierte en `number`; si la llamas con un `string`, `T` será `string`.
## Structural Type System
One of TypeScript’s core principles is that type checking focuses on the _shape_ that values have. This is sometimes called “duck typing” or “structural typing”.

In a structural type system, if two objects have the same shape, they are considered to be of the same type.

## Compiler `tsc`
+ Static check types in code
+ tranform ts to js code
	+ Downleveling (like babel)
---
+ You can set strictness settings
	+ `noImplicitAny` -> on, issue an error on variables where type is implicitly inferred as `any`
	+ `strictNullChecks` -> only access something properties when is not null or undefiend