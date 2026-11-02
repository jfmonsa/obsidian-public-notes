---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/typescript
---

## Interface vs Type
+ interaface: extensible via `extends`
+ type: via type intersection `&`
## Type Assertion `as`
Sometimes you will have information about the type of a value that TypeScript can’t know about.

> [!WARNING]
> type asssertions are removed at compile-time, there is no runtime checking associated with type assertion

+ Only works for _more specific_ or _less specific_ version of a type
## Literal Types
```ts
function printText(s: string, alignment: "left" | "right" | "center") { 
	// ...
}
```

### Literal Types: `as const`
+ Following example will raise an error: `Argument of type 'string' is not assignable to parameter of type '"GET" | "POST"'`
+ since req.method could be any string not only "GET" | "POST"
```ts
declare function handleRequest(url: string, method: "GET" | "POST"): void;

const req = { url: "https://example.com", method: "GET" };

handleRequest(req.url, req.method);
```
+ To handle this:
	+ we can use **type narrowing** `handleRequest(req.url, req.method as "GET")`
	+ Or use `as const` to **convert the entire object to be type literals**: `const req = { url: "https://example.com", method: "GET" } as const;` 

The `as const` suffix acts like `const` but for the type system, ensuring that all properties are assigned the literal type instead of a more general version like `string` or `number`.
## how to handle strictNullChecks: on
1. use type assertions
2. use Non-null Assertion operator (Postfix `!`)

### Non-null Assertion Operator `!`
+ only use `!` when you know that the value _can’t_ be `null` or `undefined`

```ts
function liveDangerously(x?: number | null) {
// No error
console.log(x!.toFixed());
}
```

## Enums
+ Recently added, no at type-level but at runtime, for this use it with precaution