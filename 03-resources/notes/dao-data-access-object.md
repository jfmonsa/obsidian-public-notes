---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

+ structural patern
+ Separates Business Logic from Data Access Logic
+ Provides an abstraction layer over the data sources allowing the app to interact with the data without being tightly coupled to the underlying data storage mechanism
+ Esencialmente, DAO actúa como un adaptador entre los componentes y la fuente de datos
**Benefint**
+ If you decide to switch from one database vendor to another, you only need to update the DAO implementations, leaving the rest of the application untouched.
---
+ En muchos casos se encuentra que existe un Data Access Object por cada tabla en la base de datos, sin embargo también es posible hacer un DAO que interactue con más tablas
## Example
+ **Interfaz**: define el contrato que debemos seguir
```java
public interface UserDao {  
    User findById(int id);  
    void save(User user);  
    void update(User user);  
    void delete(User user);  
}
```
+ **Implementación**: implementamos las operaciones dependiendo del vendor o orm que usemos (incluso puede ser un archivo o operaciones en una estructura de datos en memoria), ==cumpliendo el contrato==

```java
public class UserDaoImpl implements UserDao {  
    // Implementation of CRUD operations using JDBC, JPA, or any other ORM framework  
}
```

# Repository Pattern
+ Structural Pattern
+ Dos definiciones 1. **Martin Fowler** y 2. **Erick Evans**

1
> un Repositorio encapsula el conjunto de objetos persistidos en un almacén de datos y las operaciones realizadas sobre ellos, proveyendo una concepción mas orientada a objetos de la capa de persistencia. Ademas, apoya el objetivo de lograr una separación limpia y una dependencia en un solo sentido entre el dominio y la capa de acceso a datos. (…) Un Repository reduce la cantidad de código necesitada para tratar con todas las consultas que se llevan a cabo. - ***Martin Fowler, Patterns of Enterprise Application Architecture***

+ un repository puede tener más de una tabla asociada