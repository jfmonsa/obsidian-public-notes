---
mocs:
    - "[[public-notes/03-resources/react.moc.md|React]]"
tags:
    - dev/frontend/react
---
## 1. Crear proyecto React
+ usar vite
	+ es un bundler
	+ mejor que webpack
## folder / project structure
+ Feature Based
+ scope rule
## 2. project structure, good practices and architecture
+ https://dev.to/itswillt/folder-structures-in-react-projects-3dp8
+ name exports y exports default

Practicas Generales:
+ Separate Business logic from UI (BL in /services)
+ Avoid a single Context for everything
+ CSS in JS

Arquitecturas Recomendadas (Muy similares entre si)
+ clean
+ hexagonal
+ onion
### Arquitectura Clean apuntes
+ [[Arquitectura CLEAN para front (React.js)]]
## 4. Hook
+ Fragmento de lógica que representa el ==ciclo de vida== de un componente ==(se crea, ejecuta y muere)== y es reutilizable
	+ built-in hooks como: useState, useEffect, etc.
	+ custom hooks
+ Empiezan por la palabra `use`
