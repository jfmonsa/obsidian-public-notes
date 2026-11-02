---
mocs:
    - "[[public-notes/03-resources/frontend.moc.md|Frontend]]"
tags:
    - dev/frontend
---

# Reactivity
+ Its a "Black Box" that monitor changes in ==state== and ==update the ui==
+ Reactivity is achieve in frameworks in a different way
	1. Values with dirty checking (e.g compare virtual dom with real one, React)
	2. Observables: Hold specific values and notify subscribers (Angular)
	3. Signals (Quirk and Solid)
	4. Proxy object: vue (similar to observables?)
# SSR core concepts
+ concepts:
	+ **Rendering**: process of generating HTML content from templates
	+ **CSR (Client-Side Rendering)**: browser download minimal HTML and Js -> Js fetches data and dynamically generates the HTML
	+ **SSR (Server-Side Rendering or Universal Rendering)**: server pre-renders minimal HTML and sends it to the client
		+ allow clients to run efficiently the app with low hardware resources
	+ **Hydratation**: - After SSR sends the initial HTML, JavaScript on the client can "hydrate" the page, attaching event listeners and making it interactive.
		1. The server compiles code and generates static **HTML.**
		2. The **HTML,** along with **CSS** and **JavaScript,** is sent to the client (browser).
		3. The browser runs **JavaScript** files from the server and transforms the static page into an **interactive HTML page.**
	+ **SSG (Static Site Generation)**: This is a variation of SSR where HTML pages are pre-rendered at build time, rather than on each request. This is suitable for content that doesn't change often. Static site generators like Gatsby and Next.js support SSG.
		+ build time is a way long
	+ **ISR (Incremental Static Regeneration)**: combines SSG and SSR, some pages are static and others are dynamic
	+ metrics improved by SSR improving SEO:
		+ TTI (Time To Interactivity)
		+ FCP (Fisrt Content Page)

# Frameworks / Libraries
+ [[react.moc]]
	+ [[next-js]]
+ [[vue-intro]]
+ Solid: signals
# Mix Notes
+ [[css]]
+ [[tailwind]]
+ [[frontend-architectures]]
# Modern React
+ zustand
+ useHookForm
+ react query
## Resources
+ https://github.com/alan2207/bulletproof-react - bullet proof react¨