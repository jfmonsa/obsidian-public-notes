---
mocs:
    - "[[public-notes/03-resources/system-design.moc.md|System Design]]"
tags:
    - dev/system-design
---

+ Software Architecture exposes a system's structure while hiding implementation details.
+ focuses on how the elements and components within a system interact with one another.

# Resources
## Express.js
+ https://medium.com/@ramsesndame34/best-express-js-architecture-folder-for-biggest-project-best-pratice-8131401b1c80: cli automation (like nestjs)
# MVC (3 Layer Approach)
![[Pasted image 20241019131739.png]]
+ 3 capas express, como ya lo vengo trabajando
+ http layer: controller + route; BL layer: services y data access layer: models, entities o repositories
# Hexagonal
+ **Infraestructura**: BD connection, axios calls
+ **Aplicación**: Casos de uso
+ **Domain**: Modelos o entidades

![[Pasted image 20240929172057.png]]

Combinandolo un poco con las arquitecturas clean
+ Regla de dependencias

---
Terminología extra:
+ puerto = repositorie
+ service functions = adapters
## Resources
+ https://www.youtube.com/watch?v=bdnpXzgj1oY&list=TLPQMjkwOTIwMjQIVCpNRnssjQ&index=1&pp=gAQBiAQB Clean Architecture and Hexagonal
# DDD - Domain Driven Design

# Clean Architectures
+ Architecture is an architectural style created by _Robert C. Martin_
+ Separan el dominio (BL) de la infraestructura
+ Pasamos de estar acoplados a ser independientes del framework, de la libreria, de la ui
+ Mejor escalabilidad
![[Pasted image 20241019125312.png]]
![[Pasted image 20240929173919.png]]


## Dependency Rule
![[Pasted image 20241019125301.png]]

## Four Layers
1. Entities (Data Access Layer: Orms models, entities or repositories)
2. Use Cases: (Bussines Logic Layer)
3. Interface Adapters (Http Layer: Controllers + routes)
4. Frameworks and Drivers
![[Pasted image 20240929174027.png]]


## Resources
+ https://youtu.be/1OLSE6tX71Y?si=j0Z5GfdJeA3VN-cG - Understand Clean Architecture in 7 Minutes

