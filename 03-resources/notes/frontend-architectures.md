---
mocs:
    - "[[public-notes/03-resources/frontend.moc.md|Frontend]]"
tags:
    - dev/frontend
    - dev/system-design
---


> [!IMPORTANT]
> Folder structures impact how your app scales

Principles:
+ units should be near were there are used
	+ if you write code (interfaces, hooks, services, components) relalated only to a specific page or part of the app, the it should be inside of page's folders
+ scope + group by routes (app router)
	+ folders in the `root` are used globally by different scopes in the app
---
+ if not usign app router structure, use a flat folder which stores each page, each page has its own scope
---
**Code practices**
+ prefer absolute paths instead of relative (better for refactor). ==use path aliases==
+ prefer named exports instead of default ones (better for refactor)
+ don't use barrel files (they make worse bundle size)
# Basic architectures
## Type based
  One folder for components, for services, for hooks, etc. (small project)
## Feature / Module based
any required structure in the scope of the feature / module folder

# My Opinion for big projects
```
app
  (auth)
    login
    register
    forgot-password
  profile
    settings
  game
    join-game
    game:id
```


Folders
+ services
	+ providers: custom context / third party context
	+ api: function + interfaces. you can have adapters / dtos
	+ i18n
	+ store: state manager: redux / zustand. (Only for global scope)
		+ reducers
		+ actions
+ components
	+ primitive_ui # small, low level components
+ assets
	+ brand
	+ images
+ models
+ config / setup
	+ context-manager # global context setup
	+ routes-manager
+ styles // only for global
+ utils // helper functions (a file for each function) , hardcoded arrays, etc.
+ lib / vendor: (optional) the implementatio of the facade pattern, make third party libraries easy to replace or modify without altering existing code that depens on this libraries
	+ axios-instance.ts
---
+ Nota: En lugar de poner estos folders en la raíz, es valido agruparlos en un folder `common` o `shared` para mayor organización en el código
## Resources
La elección es el resultado del analisis pragmatico de distintas propuestas
+ https://youtu.be/Mm6_DlO5vvs?si=JOxGx2zqGK17XkPz - # React Folder Structure Best Practices - For Large Projects
+ https://youtu.be/ANrYhHN8Dl4?si=3DKQreGCirbhFHog # Folder structure in React - Complete Guide
+ https://github.com/alan2207/bulletproof-react/blob/master/docs/project-structure.md feature based approach
+ https://timdeschryver.dev/bits/enforce-module-boundaries-with-no-restricted-imports - enforce module boundaries using a linter
![[Pasted image 20240817174701.png]]

![[Pasted image 20250127122359.png]]
![[Pasted image 20250127122501.png]]
