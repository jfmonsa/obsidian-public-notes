---
mocs:
    - "[[public-notes/03-resources/frontend.moc.md|Frontend]]"
tags:
    - dev/frontend
    - meta/lang/es
---


+ Puede implementarse en casi cualquier proyecto
> The back-end should decide what to return, and the front-end should decide what to render with the data it has


## Arquitectura clásica - Capas:****
+ Domain: entidades
+ Casos de uso: (applicacion): logica de negocios sobre esas entidades
![[Pasted image 20240817173720.png]]

## Dependency Rule
+ El domino de ser independiente
+ La capa application puede depender del dominio
+ Las capas externas pueden depender de cualquier cosa

## Arquitectura clean en front-end
+ **Modelos/State (Dominio)**: Representan entidades dentro de nuestra app: Redux, interfaces, contextos (datos del usuario)

## Estructura de Carpetas
Carpetas dentro de src

![[Pasted image 20240817174044.png]]
+ interceptors: intercepta peticiones (e.g. axios)
+ adapters: formateo y transformación de datos
	+  formatean los datos de las requests (Comunican con servicios externos)
	+ Los servicios externos dependen de nuestras necesidades. no nosotros de ellos.
+ hooks: contiene custom hooks
+ Models: interfaces
+ pages: vistas
+ services: business logic (llamadas al api)
+ styled-components: componentes que no tienen ningun tipo de lógica (stateless)
+ utilities
+ assets: multimedia, tipografias, imagenes

Aplicada a la clean architecture
![[Pasted image 20240817174406.png]]

+ Cada Pagina tiene cosas que no son reutilizables por otros paginas, entonces para mejorar la modularización, cada pagina será una carpeta que contenga la pagina en si, y todo lo relacionado que solo use ella
+ Mientras que las carpetas en el root solo las usamos para cosas que vamos a reutilizar en varias partes

![[Pasted image 20240817174701.png]]

Adapter
![[Pasted image 20240817175041.png]]

Components
![[Pasted image 20240817175256.png]]

Context:
![[Pasted image 20240817175349.png]]

hooks (Custom hooks)
![[Pasted image 20240817175451.png]]

interceptors
+ Ej: revisa la peticion para ver si tiene token
![[Pasted image 20240817175603.png]]

models (mas que nada para typescript)
![[Pasted image 20240817175629.png]]

Pages:
![[Pasted image 20240817175725.png]]

Servicios:
![[Pasted image 20240817175811.png]]

styled-components:
![[Pasted image 20240817175828.png]]

utilities:
![[Pasted image 20240817175917.png]]

API: (services)
> The component shouldn’t be aware if we’re using fetch, axios, or another HTTP client to retrieve data. It shouldn’t be aware if that data is fetched via HTTP, gRPC if it comes from a web socket or any other kind of source. It should only be responsible for rendering that data. And the developer making changes to this component doesn’t need to read through all of our HTTP logic to work on the markup.

```tsx
export default function PromptPage() {
  const [prompt, setPrompt] = useState(emptyPrompt)

  useEffect(() => {
    fetch('http://localhost:3000/api/v1/prompts')
      .then((res) => res.json())
      .then((data) => setPrompt(data))
  })

  return (
    <Layout>
      <h1>{prompt.title}</h1>
      {prompt.answered ? (
        <AnswersList answers={prompt.answers} />
      ) : (
        <AnswerForm />
      )}
    </Layout>
  )
}
```

```ts
// prompt-client.ts

const getActivePrompt = () => {
  return fetch('http://localhost:3000/api/v1/prompts').then((res) =>
    res.json()
  )
}

export default {
  getActivePrompt,
}
```

```tsx
export default function PromptPage() {
  const [prompt, setPrompt] = useState(emptyPrompt)

  useEffect(() => {
    promptClient.getActivePrompt().then((data) => setPrompt(data))
  })

  return (
    <Layout>
      <h1>{prompt.title}</h1>
      {prompt.answered ? (
        <AnswersList answers={prompt.answers} />
      ) : (
        <AnswerForm />
      )}
    </Layout>
  )
}
```

hooks: usePrompt()

```tsx
export default function PromptPage() {
  const { prompt, handleSubmit } = usePrompt()

  return (
    <Layout>
      <h1>{prompt.title}</h1>
      {prompt.answered ? (
        <AnswersList answers={prompt.answers} />
      ) : (
        <AnswerForm handleSubmit={handleSubmit} />
      )}
    </Layout>
  )
}
```

> I’d call this a clean component. It has a single responsibility - render content on the screen based on the data it receives. Pay attention to how many details our custom hook is hiding from the component. It’s not aware if it’s coming from an HTTP call if it’s hardcoded, or read from a file.

```ts
export default function usePrompt() {
  const queryClient = useQueryClient()

  // Fetching prompt data
  const prompt = useQuery({
    queryKey: 'prompt',
    queryFn: promptClient.getActivePrompt,
    initialData: emptyPrompt,
  })

  // Handling answer submission
  const mutation = useMutation({
    mutationFn: promptClient.createAnswer,
    onSuccess: () => {
      // Invalidate and refetch
      queryClient.invalidateQueries('prompt')
    },
  })

  const handleSubmit = (answer) => {
    mutation.mutate(answer)
  }

  return {
    prompt,
    handleSubmit,
  }
}
```


## Resources
+ Guide to react architectures - https://medium.com/@livajorge7/a-comprehensive-guide-to-react-architecture-building-scalable-web-applications-with-cronj-5ce9f9f6130a
+ https://medium.com/stackanatomy/react-architecture-patterns-for-your-projects-6f495448f04b
+ Architecture patterns - https://medium.com/stackanatomy/react-architecture-patterns-for-your-projects-6f495448f04b
+ **Video Recomendado** - Cómo estructurar tu project de ReactJs? Aplicamos Clean Architecture en Front End https://youtu.be/5LqhlCd2_nE?si=eIKeCqP9BEyxuFvw
+ https://alexkondov.com/full-stack-tao-clean-architecture-react/ (Recomendado)