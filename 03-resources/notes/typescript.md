---
mocs:
    - "[[public-notes/03-resources/languages.moc.md|Languages]]"
tags:
    - lang/typescript
---

+ Compilado
+ superset of javascript, ts offers an additional layer on top of js features: TypeScript's type system
+ `.ts`
+ intellisence in code editor, improved static code analysis  to avoid type related run time errors

> The goal of TypeScript is to be a static typechecker for JavaScript programs - The Typescript Handbook
# References
+ https://www.typescriptlang.org/docs/handbook/intro.html
# Notes
## 1 - [[typescript-intro]]
+ Primitive types, type inference, explicit type declaration: (interfaces, type unions and generics), structural type sustem (duck typing)
## 2 - [[typescript-more-on-types]]
+ Interfaces vs Types, Type assertions `as`, Literal Types and `as const`, how to handle strictNullChecks: on (Non-null assertion operator `!`)
## 3 - [[#Narrowing]]

# Narrowing
explicitly check if a type is correct when we have union types and one operations is incompatible with some types of the union

+ typeof type guards

```ts
function padLeft(padding: number | string, input: string): string {
if (typeof padding === "number") {
	return " ".repeat(padding) + input;
	}
return padding + input;
}
```

+ truthiness narrowing (check if something not-boolean) is not `null` or `undefined`
+ `in` operator narrowing: check if and object or its prototype chain has a property with a name
+ `instanceof` narrowing: x instanceof Foo checks whether the prototype chain of x contains Foo.prototype
+ control flow analysis
## type predicates

# Especifico para react
+ `tsx` para componentes
## Props
```typescript
type Props = {
	name: string,
	age: number
}

export default function PersonCard({name, age}: Props){
	//...
}
```

## Hooks
```typescript
const [person, setPerson] = useState<Person>({
	name: "Alberto",
	age: 16
})
```

## Eventos
+ Change event de react
+ para el handleChange

```typescript
function handleChange(event: ChangeEvent<HTMLInputElement>){
	setInputValue(event.target.value);
}
```



# Satisfies Operator
