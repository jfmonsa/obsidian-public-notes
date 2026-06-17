---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
**concepts**: states vs variables, immutability
+  It triggers re-renders in the component and its children when the state changes, ensuring the UI reflects the latest value of the state

> [!WARNING]
> Only use useState when the following conditions are meet:
> 1. it can be computed each render
> 2. it need to be re-redered

## Pass a callback to set update state
+ when update an state depends on previous state
+ Asegura actualizaciones del estado seguras y predecibles, especialmente en aplicaciones con estados que cambian rápidamente o de manera asíncrona.

```js
const [count, setCount] = useState(0);

const increment = () => {
  setCount((prevCount) => prevCount + 1);
};
```

```js
const handleRightClick = useCallback(
    (square: Square) => {
      setRightClickedSquares((prevSquares) => {
        if (prevSquares.includes(square)) {
          // if the square is already right clicked, remove it
          return prevSquares.filter((s) => s !== square);
        } else {
          // if not add it
          return [...prevSquares, square];
        }
      });
    },
    [setRightClickedSquares],
  );
```

## Pass a callback to set initial state
+ is preferable than a useEffect that runs after component mounts
+ used for read localstorage (initialize an state with this value)
```js
/**
 * Reads the game data from session storage.
 * @returns The parsed game data, or null if no data is found.
 */
const readGameData = () => {
  if (typeof window === "undefined") return null;
  const storedGameData = sessionStorage.getItem("gameData");
  if (!storedGameData) return null;
  return JSON.parse(storedGameData);
};

  /**
   * This state holds the game data, which is initially read from session storage.
   */
  const [gameData, setGameData] = useState<any>(readGameData);
  ```

## Derived data from state

> [!WARNING]
> You should not store in states what can be derived from other state variables
### Local Storage
Acceder a los valores del `localStorage` dentro del componente es muy pesado en cuanto al rendimiento, ya que se **ejecuta sincrónicamente en cada re-renderizado** esto permitirá acceder a la información una sola vez al momento que se crea el componente, esto por la definición de `useState`.
