---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
# 3. Components
+ Are the building blocks of our app, just like legos
+ named in uppercase (function and file name)
+ It's a JS function that returns markup (JSX)
+ **react fragment**
## Props and Children
- To pass props, add them to the JSX, just like you would with HTML attributes.
- To read props, use the `function Avatar({ person, size })` destructuring syntax.
- You can specify a default value like `size = 100`, which is used for missing and `undefined` props.
- You can forward all props with `<Avatar {...props} />` JSX spread syntax, but ==don’t overuse it!==
- Nested JSX like `<Card><Avatar /></Card>` will appear as `Card` component’s `children` prop.
- Props are read-only snapshots in time: every render receives a new version of props. (**immutability**)
- You can’t change props. When you need interactivity, you’ll need to set state. (**immutability**)
## Tipos de Componentes
### a) Stateless (dummy components)
+ Don't have Business Logic
+ For Titles e.g Design system components
	+ Mucho mejor que poner clases css repetidas en lugares distintos

> Nota: no usar estilos como en el ejemplo, mala practica, mejor usar modulos o styled-components

```js
const myComponentStyle = {
	color: 'blue',
	padding: '1.5rem'
} 

const HeadingTitle = ({ title }) => {
	return (
		<h1 style={myComponentStyle}>{title}</h1>
	);
}

export default HeadingTitle;
```

## b) Stateful
+ Have BL (requirements)

![[Pasted image 20240817184832.png]]

# Keep Components Pure
+ React assumes that every component you write is a pure function.
+ React components you write must always return the same JSX given the same inputs
+ You should not mutate any of the inputs that your components use for rendering. That includes props, state, and context. To update the screen, [“set” state](https://react.dev/learn/state-a-components-memory) instead of mutating preexisting objects.

## Side Effects
+  Components should only return their JSX, and not change any objects or variables that existed before rendering

### Impure component (BAD)
```js
let guest = 0;

function Cup() {
  // Bad: changing a preexisting variable!
  guest = guest + 1;
  return <h2>Tea cup for guest #{guest}</h2>;
}

export default function TeaSet() {
  return (
    <>
      <Cup />
      <Cup />
      <Cup />
    </>
  );
}
```

This component is reading and writing a guest variable declared outside of it. This means that calling this component multiple times will produce different JSX! And what’s more

> You can fix this component by passing guest as a prop instead

## Local Mutation
+ However, **it’s completely fine to change variables and objects that you’ve _just_ created while rendering**
+ In this example, you create an [] array, assign it to a cups variable, and then push a dozen cups into it:

```js
function Cup({ guest }) {
  return <h2>Tea cup for guest #{guest}</h2>;
}

export default function TeaGathering() {
  let cups = [];
  for (let i = 1; i <= 12; i++) {
    cups.push(<Cup key={i} guest={i} />);
  }
  return cups;
}
```

## ¿Where you can cause side effects?
+ side effects usually belong inside event handlers
+ Even though **event handlers** are defined inside your component, they don’t run during rendering! So event handlers don’t need to be pure.
+ or `useEffect`
