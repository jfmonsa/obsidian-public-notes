---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
+ Abstracts business logic from the ui
+ starts with `use`
+ abstracting component's logic into custom hooks help with ==separation of concerns==
+ use other hooks
+ Muy importante tener en cuenta SRP
---
+ Cada vez que tengas un useEffect piensa si es mejor encapsularlo en un custom hook

# Casos de uso comunes
+ useLocalStorage
+ useFetch
+ useSocketioConnection
# Ejemplos
## `useLocalStorage`

```ts

// 1. Define custom hook
export function useLocalStorage(nameOfItem: string, initialValue: any){

	const [item, setItemState] = useState(() => {
		const parsedItem = localStorage.getItem(nameOfItem)
		if (!parsedItem) return initialValue
		return JSON.strigify(parsedItem);
	})

	const saveItem = useCallback((newItem)=>{
		localstorage.setItem(nameOfItem, JSON.strigify(newItem))
		setItem(newItem)
	},[nameOfItem])

	return [item, saveItem]
}

// 2. use it in a component or other hook

function App(){
	const [item, saveItem] = useSessionStorage("my-item")
	// etc...
}
```
