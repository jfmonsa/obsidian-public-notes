---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
+ Manage side effects in our functional components
+ executes callback after a component is rendered

> [!NOTE]
> Use `useLayoutEffect` to do it after component renders

> [!WARNING]
> Trata de evitar el uso de efectos en cuanto sea posible, en lugar usar handlers/callbacks o estados
## ¿Que se puede hacer con el?
- **Hacer solicitudes HTTP** (como obtener datos de una API).
- **Suscribirse a eventos** o flujos de datos.
- **Configurar y limpiar recursos** (como intervalos, timers, o listeners).

## Components Life-cycle
El `useEffect`  nos da la capacidad de manejar el ciclo de vida de un componente
+ **Life Cycle?** refers to: Creation, update and destruction of a component
### ¿Como se manejaba antes? - Class Components
+ Antes manejábamos el ciclo de vida por medio de OOP con Class Components, con metodos heredados de react como: `componentDidMount(), componentDidUpdate(), componentWillUnmount()`

![[Pasted image 20240817185517.png]]

### ¿Como se maneja ahora? - Functional components
+ Ahora react introduce los componentes funcionales (literal functional programming), that allow us to reduce boilerplate-oop code
+ now we use hooks like useState and useEffect to manage life-cycle

![[Pasted image 20240817190418.png]]

## Dependency Array
+ El comportamiento del `useEffect` y el manejo del ciclo de vida depende del array de dependencias

### 1 - Sin array de dependencias
+ Se ejecuta **después de cada render** del componente (inicial y posteriores).
+ El efecto se dispara después de que React ha actualizado el DOM.
+ En la mayoría de los casos es mala practica:
	1. **Rendimiento:** El efecto se ejecuta en cada render, lo que puede ser innecesario y costoso.
	2. **Confusión:** Es fácil olvidar que este comportamiento ocurre, lo que lleva a efectos secundarios inesperados.
	3. **Comportamiento redundante:** Si el efecto no depende de valores dinámicos, es mejor usar un array de dependencias vacío `[]` para ejecutarlo solo una vez.

Un caso válido podría ser: **Sincronización que depende del DOM actualizado**:
+ Si necesitas que el código se ejecute **después** de que React haya renderizado el DOM y no durante el proceso de renderizado.
+ Ejemplo: manipulación del DOM con librerías externas o cálculos basad

```tsx
useEffect(() => {
  const element = document.getElementById('my-element');
  if (element) {
    console.log('Altura del elemento:', element.offsetHeight);
  }
});
```

### 2- Array de dependencias vacio `[]` (mount)
- Se ejecuta **solo una vez**, después del primer render. Similar a `componentDidMount`.
- Útil para inicializar datos o configurar algo al montar el componente. Sin embargo, siempre que se pueda se pueden usar estados o callbacks / handlers para cargar el estado inicial de algo

+ ==Ejemplo== analizar el problema del fragmento 1 vs el fragmento 2
#### Fragmento 1
```tsx
asycn function apiFetch() {
	const res = await fetch(url);
	const data = await res.json();
}

function TodoListComponent(){
	const data = api();

	return (
		<p>{data.message}</p>
	)
}
```

#### Fragmento 2
```tsx
function TodoMessage(){

	[todoItems, setTodoItems] = useState(null)

	useEffect(async ()=>{
		const data = await api();
		seTodoItems(data)
	},[])

	if(!data) return <p> Cargando .... </p>
	
	return (
		<ul>{setTodoItems.map(
			(item, index) => {
				<li>{item}</li>	
			}
		)}</ul>
	)
}
```

### 3- Con un array de dependencias específicas (`[dependency1, dependency2]`) (Update)
- Se ejecuta **solo cuando cambian** las dependencias especificadas.
- Útil para responder a cambios en props, estado o valores externos.

```tsx
useEffect(() => {
  console.log('Cambio en dependencia');
}, [dependency1, dependency2]);
```

### 4- Cleanup (unmount)
- Se ejecuta **antes** de desmontar el componente.
- Se ejecuta **antes de volver a ejecutar el efecto** si las dependencias cambian.

#### ¿Porque es importante?
- **Evitar fugas de memoria:** Por ejemplo, si inicias un intervalo o timer, este continuará ejecutándose incluso si el componente ya no está en el DOM, ocupando recursos innecesariamente.
- **Desuscripción de eventos o listeners:** Listeners de eventos en el `window`, `document` o WebSockets deben eliminarse para evitar interacciones no deseadas.
- **Evitar conflictos en renderizados posteriores:** Si no limpias un efecto que depende de props o estado, puedes trabajar con datos desactualizados.

```tsx
import { useEffect } from 'react';

function WebSocketComponent() {
  useEffect(() => {
    const socket = new WebSocket('wss://example.com/socket');

    socket.onopen = () => console.log('WebSocket conectado');
    socket.onmessage = (event) => console.log('Mensaje recibido:', event.data);

    // Cleanup: cerrar la conexión al desmontar
    return () => {
      socket.close();
      console.log('WebSocket cerrado');
    };
  }, []); // Solo se ejecuta al montar

  return <div>WebSocket activo</div>;
}
```

## Errores Comunes
1. **Dependencias omitidas:** Esto puede causar que los efectos trabajen con valores obsoletos.
2. **Efectos no limpios:** No limpiar correctamente puede provocar fugas de memoria.
3. **Ejecución innecesaria:** Usar efectos sin dependencias o con demasiadas dependencias puede causar renders o cálculos innecesarios.

---
