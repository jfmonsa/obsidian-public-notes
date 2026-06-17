---
mocs:
    - "[[public-notes/03-resources/vue.js.md|Vue.js]]"
tags:
    - dev/frontend/vue
---

+ JavaScript Framework for building frontend UIs
+ Progressive Framework: Progressively add new features (core view layer, router, state management, CLI)
+ Components: encapsulate data or state in JS and connect that state reactively to a template in html
+ declarative use
+ using a virtual dom
+ Vue 3 (Last version)
---
**Approchable**
+ Builds on top of standard HTML, CSS and JS with intuitive API.
**Performant**
+ A reactive, compiler-optimized rendering system that rarely requires manual optimization
**Versatile**
+ A rich, incrementally adoptable ecosystem that scales between a library and a full-featured framework. can be used in the following ways:
	+ Enhancing static HTML without a build step
	- Embedding as Web Components on any page
	- Single-Page Application (SPA)
	- Fullstack / Server-Side Rendering (SSR)
	- Jamstack / Static Site Generation (SSG)
	- Targeting desktop, mobile, WebGL, and even the terminal
---
## Resources:
+ https://roadmap.sh/vue
+ https://youtube.com/playlist?list=PLDllzmccetSNgykILXnHMeuO-y-gRcF-i&si=zDeJ63aJxiJ3HDNo - Excelente curso de vue 3 en español
# Notes

## 1 -  Intro
### Reactivity
There are two ways writing vue:
#### 1. Composition API
+ allow more flexibility, more complex patterns
+ Better TS integration
+ escalability
#### 2. Options API
+  more OO like:
	+ data method returns and object
	+ methods object
	+ computed
### Quickstart
1. Use `pnpm create vue@latest`
2. use a CDN (No build proccess but you wouldn't be able to use SFC syntax)
### Create App Instance
```vue
<template>
	<div id="app">
	   <h1>{{ product }}</h1>
	</div>
</template>

<script>
import {createApp} from 'vue'

const app = createApp({
	data: () => ({
	   product: 'Socks'
	})

}).mount('#app)
</script>
```
+ the object we pass to app is the ==root component==
+ exposes config object `app.config`to e.g. erro handling logic
+ register components
## 2 - Template Sintax
+ declaratively bind the rendered DOM to the underlying component instance's data.
+ template is like react fragment
### Text Interpolation
+ `{{}}` sintax run js expressios or access reactive properties
### 3 - Directives
+ Prefixed with `v-`
+ some directives can take arguments denotated by `:`. e.g. `v-on:click`
	+ wrap the argument with `[]`to use a js expressión to get dynamic arguments
+ Modifiers ??
![[Pasted image 20250120221927.png]]
---
+ v-if
+ v-else
+ v-for
+ v-on
+ v-bind:htmlAttr="value": Bind dynamically property
## 3 - Reactivity Fundamentals
![[Pasted image 20250121205817.png]]
### Composition API
+ `ref(<initial value>)` to declare reactive state
```ts
import { ref } from 'vue'
const count = ref(0)
console.log(count.value)
count.value++
```

To access them in component template declare it in setup() hook a return from it
```ts
import { ref } from 'vue'

export default {
  // `setup` is a special hook dedicated for the Composition API.
  setup() {
    const count = ref(0)
    }

	increment(){
		count.value++;
	}
    // expose the ref to the template
    return {
      count,
      increment
    }
  }
}
```

+ you can declare functions that mutates refs and declare and return in the same scope, exposed methods can be event handlers
```vue
<button @click="increment">
  {{ count }}
</button>
```

+ we can use `<scritpt setup>` to be less verbose
+ When you mutate reactive state, DOM is updated
+ update state is no sync you can make it like `sync` by using `Vue.nextTick()`
---
- **`ref`**: Se utiliza para valores primitivos (números, cadenas, booleanos) y crea una referencia reactiva con una propiedad `.value`.
- **`reactive`**: Se utiliza para objetos y crea un objeto reactivo completo.

## 4 - Computed Properties
+ de-clutter templates
+ are cached
+ son como los derivad state de react?
	+ son derivados de otras dependencias reactivas, cuando estas cambian el valor cambia
+ by default getter only
+ getter functions should only perform pure computation and be free of side effects. For example, **don't mutate other state, make async requests, or mutate the DOM inside a computed getter!**
```vue
<script setup>
import { reactive, computed } from 'vue'

const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})
</script>

<template>
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
</template>
```

+ to implement writable you have to set setter and getter
```vue
<script setup>
import { ref, computed } from 'vue'

const firstName = ref('John')
const lastName = ref('Doe')

const fullName = computed({
  // getter
  get() {
    return firstName.value + ' ' + lastName.value
  },
  // setter
  set(newValue) {
    // Note: we are using destructuring assignment syntax here.
    [firstName.value, lastName.value] = newValue.split(' ')
  }
})
</script>
```

## 5 - Conditional Rendering
```vue
<script setup>
import { ref } from 'vue'

const awesome = ref(true)
</script>

<template>
  <button @click="awesome = !awesome">toggle</button>

	<h1 v-if="awesome">Vue is awesome!</h1>
	<h1 v-else>Oh no 😢</h1>
</template>
```
+ to wrap multiple elements in a if block
```vue
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

+ `v-if` (add an remove element from the DOM) vs `v-show` display or hide using CSS visibility
## 6 - List Rendering
```vue
<script setup>
import { ref } from 'vue'

const parentMessage = ref('Parent')
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
</script>

<template>
	<li v-for="(item, index) in items">
  	{{ parentMessage }} - {{ index }} - {{ item.message }}
	</li>
</template>
```
+ key property :key
## 7 - Form Input Bindings
+ sync the state of form input elements with corresponding state in JavaScript.
```vue
<input
  :value="text"
  @input="event => text = event.target.value">
```
v-model simplify the above to:
```vue
<input v-model="text">
```

## 8 - Event Handling
+ `v-on:click="<expression to be called>"`
+ `@` atajo para directiva `v-on` `@click="<js expression to be called>"

+ event modifiers
+ mouse and key modifiers
## 9 - Class and Style Binding
+ permiten aplicar dinamicamente clases css y estilos a elementos HTML en función de los datos del componente

**Class Binding**
se utiliza para agregar o eliminar clases CSS en un elemento HTML de manera dinámica, basada en los datos del componente.

```vue
<div :class="{ active: isActive }"></div>
```

**Style Binding**
se utiliza para aplicar estilos en línea (inline styles) a un elemento HTML de manera dinámica, basada en los datos del componente
```vue
<div :style="{ 'font-size': fontSize + 'px' }"></div>
```
## 10 - Components
+ split UI into independent and reusable pieces
+ When a build step is involved we usually use  SFC with `.vue`

```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <button @click="count++">You clicked me {{ count }} times.</button>
</template>
```

+ When not using a build step a vue component can be defined as a plain javascript
```ts
import { ref } from 'vue'

export default {
  setup() {
    const count = ref(0)
    return { count }
  },
  template: `
    <button @click="count++">
      You clicked me {{ count }} times.
    </button>`
  // Can also target an in-DOM template:
  // template: '#my-template-element'
}
```

+ We have to import our component a use it
```vue
<script setup>
import ButtonCounter from './ButtonCounter.vue'
</script>

<template>
  <h1>Here is a child component!</h1>
  <ButtonCounter />
</template>
```
---
+ event emission to comunicate events between components
+ props
+ slots (children)
## 11. Communication between components
 1. Using Props (Parent to Child Communication)
2. Using Events (Child to Parent Communication)
3. Using Event Bus (Communication between any comp

## 12. Component Lifecycle
+ `created` make api calls
+ `mounted` aplicaciones que necesitan acceso al DOM, manipular elementos de terceros
+ `update`
+ `beforeUnmount` realizar tareas de limpieza
![[Pasted image 20250122152757.png]]

## 13. Watchers
+ Perform side effects in reaction to state changes: e.g. mutating DOM, save data to LocalStorage
+ triggers a callback whenever a piece of reactive state changes
```vue
<script setup>
const question = ref('')
const answer = ref('')
watch(question, async () => {
 // fetch data from api when a question is made and save it on answer ref
})
</script>
```

### `watchEffect`
+ utomatically tracks any reactive properties accessed within its callback function and re-runs the effect whenever those properties change.
+ can perform any side effects, such as updating the DOM, making API calls, or logging data.
### Deep and Shallow watch
+ by default create a deep watcher for reactive object, if not you can:
```js
watch(
  () => state.someObject,
  () => {
    // fires only when state.someObject is replaced
  }
)
```

### Eager and Lazy watchers
+ by default callback will be fired lazy (before watched state updates)
+ you can change this using `{ inmediate: true}` as 3rd arg of `watch()`

### Clean-up
```js
import { watch, onWatcherCleanup } from 'vue'

watch(id, (newId) => {
  const controller = new AbortController()

  fetch(`/api/${newId}`, { signal: controller.signal }).then(() => {
    // callback logic
  })

  onWatcherCleanup(() => {
    // abort stale request
    controller.abort()
  })
})
```
## Composables
+ reusing stateful logic
+ helper or aux functions are used for stateless logic

## Fallthrought attrs
 `v-bind="$attrs"` is used to explicitly pass "fallthrough attributes" from a parent component to a specific element within a child component's template.

Understanding Fallthrough Attributes:

- Fallthrough attributes are attributes (and event listeners) applied to a component's tag in the parent, but which are not declared as `props` or `emits` within the child component.
- Examples include `class`, `style`, `id`, `data-*` attributes, and `v-on` listeners for events not explicitly emitted by the child

## Custom Directives
+ intended for reusing logic that involves low-level DOM access on plain elements.
+ should only be used when the desired functionality can only be achieved via direct DOM manipulation.

# Quasar
+ Vue.js Framework
+ various build modes SPA, SSR, PWA, Mobile app, Desktop app & Browser Extension
+ tree-shakable automatically
+ Powerful CLI
+ powerful UI library
# Pinia
+ Global State Management
+ scalability