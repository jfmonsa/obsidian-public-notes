---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
---

+ Translate data between tuples / rows (flat) and objects (nested)
+ Allow you to focus on Business Logic
+ for converting data between a [relational database](https://en.wikipedia.org/wiki/Relational_database "Relational database") and the [heap](https://en.wikipedia.org/wiki/Memory_management#HEAP "Memory management") of an [object-oriented](https://en.wikipedia.org/wiki/Object-oriented "Object-oriented") programming language.
+ This creates, in effect, a virtual object database that can be used from within the programming language. 
+ Relational DB uses Tuples instead of Objects, we need to translate that data
+ ORM exposes API with methods to interact with the DB abstracting from raw SQL

## Drawbacks (cons)
+ high level of [abstraction](https://en.wikipedia.org/wiki/Database_abstraction_layer "Database abstraction layer") obscuring what is actually happening in the implementation code

## Object-oriented DBs
+ Another approach is to use an object-oriented database management system (OODBMS) or document-oriented databases such as native XML databases that provide more flexibility in data modeling

## ORMS for Postgresql
+ Sequelize (Typescript / Javascript)
+ SQLAlchemy (Python)
+ TypeORM (Typescript / Js)
+ Django ORM (Python)
+ Eloquent (PHP)
+ Hibernate (Java)
+ Knex.js (Javascript) <- allows developers to work directly with raw SQL or utilize its query builder functions.

## Data Access Object - DAO (Patrón Arquitectónico)
+ permite separar la lógica de acceso a datos de los Bussines Objects u Objetos de negocios, de tal forma que el DAO encapsula toda la lógica de acceso de datos al resto de la aplicación.
+ Implementar la lógica de acceso a datos en la capa de lógica de negocio puedes ser un gran problema, pues tendríamos que lidiar con la lógica de negocio en sí, más la implementación para acceder a los datos, adicional, si tenemos múltiples fuentes de datos o estas pueden variar, tendríamos que implementar las diferentes lógicas para acceder las diferentes fuentes de datos, como podrían ser: bases de datos relacionales, No SQL, XML, archivos planos, Webservices, etc).

### Functionalities
- The DAO pattern abstracts and encapsulates the details of how data is saved, retrieved, updated, or deleted in a database. This abstraction shields the rest of the application from the specific database implementation.
- It centralizes all database-related code within dedicated DAO classes. This means that the rest of the application doesn’t need to scatter database operations throughout its codebase; instead, it interacts with DAO methods.
- The DAO pattern promotes code reusability by providing a set of generic methods that can be applied to different entities. As a result, you can use similar database access patterns across various parts of your application.
### Dudas?
+ Esto es similar al repository layer en el MVC ? o al Modelo?
### Resources
+ https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://reactiveprogramming.io/blog/es/patrones-arquitectonicos/dao&ved=2ahUKEwiKuLz7y6eIAxVHSzABHWIaJh0QFnoECBEQAQ&usg=AOvVaw2nnGRME8S2O9JlzctFAkWN
+ https://www.geeksforgeeks.org/data-access-object-pattern/
