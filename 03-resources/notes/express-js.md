---
mocs:
    - "[[public-notes/03-resources/backend.moc.md|Backend]]"
tags:
    - dev/backend
---

+ En el corazón de Express está Connect. Este es un framework de middleware
## Middleware
+ El middleware es básicamente una función que acepta objetos de request y response y una función next
+ Cada middleware puede decidir responder utilizando un objeto de response o pasar el flujo a la siguiente función llamando a next de vuelta.
![[Pasted image 20240814224850.png]]
