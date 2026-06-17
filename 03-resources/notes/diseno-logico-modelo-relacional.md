---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
    - lang-es
---

# Diseño Lógico - Modelo Relacional
+ Propuesto por Edgar Frank Codd (1970)
+ Modelo lógico basado en teoria de conjuntos
+ Los datos se almacenan en relaciones (relación = tabla, no confundir con relaciones en el ERD)
+ Se apoya en algebra y calculo de relaciones

## Relación
Estructura matricial
+ **Tuplas = filas = registros**: Sirve para representar una instancia de una entidad en el modelo E-R
+ **Atributos** (columnas)

### Propiedades de una Relación
+ **Cardinlidad o extención de una relación**: Número de tulpas
+ Conjunto de tuplas
+ Cada columna tiene un nombre unico dentro de la relación
+ tuplas y columnas no tienen orden
+ No hay tuplas repetidas
### Propiedades de los atributos
+ Cada campo o columna de una relación
+ **Grado o aridad**: numero de atributos
+ Cada atributo tienen asociado un Dominio
### Llaves
+ **superllave**: Formada por los atributos de la relación
+ **Llave candidata**: Cumple con los principios de **unicidad** e **irreducibilidad**
+ **Llave primaria (PK)**: Una de las llaves candidatas elegidas para represetnar las tuplas
+ **Llave Secundaria**: Alternativa, llave no elegida como parte de las primarias
+ **Llave foranea**: Es un atributo o conjunto de atributos, de una relación cuyos valores coinciden con los valores de la llave primaria de alguna otra relación

#### Restricción de integridad de la Entidad
+ Ningún componente de una PK puede tomar el valor de NULL
+ Necesaria para la diferenciación de tuplas

#### Restricción de Integridad Referencial
+ Ningún componente de una FK puede contener valores que no esten presentes en la llave primaria a la que referencia
+ No acepta valores de NULL
+ Garantiza la consistencia entre las tuplas de dos relaciones

### Estrategias de Modificación relaciones
+ Cascada
+ Restringido
+ Nulificación

## Transformación ERD (Modelo conceptual - MER) a Modelo Relacional
+ Para esto es importante tener en cuenta la correspondencia del ERD
+ En general cada Entidad se convierte en una tabla (relación del modelo lógico)
### Relaciones (1,1)
+ Dos tablas una por cada entidad, se debe inferir cual tendrá la FK
![[Pasted image 20240903160513.png]]
### Relaciones (1,n)
+ Dos tablas, una por cada entidad.
+ En el lado del muchos se pone la FK
+ Ej: a una Editorial le pertenecen muchos libros, FK en libros
![[Pasted image 20240903160732.png]]
### Relaciones (n,m) y (n-arias)
+ Crea dos tablas por cada entidad
+ Crea tercera tabla representando la relación que contiene las dos llaves FKs y atributos de la relación
### Subptipo / Supertipo - Entidades de Generalización / Especialización
+ Crear tabla para el supertipo
+ Crear tantas tablas como subtipos y se agrega la llave del supertipo que a la vez es foranea
![[Pasted image 20240903161605.png]]
### Multivalorados
+ Se crea una tabla adicional para representar los multivalorados
+ La PK es la FK de la entidad a la que le pertenece el atributo multivalorado con el valor de ese atributo
+ Alternativamente se puede usar un id auto-incremental como PK de la tabla creada por el atributo multivalorado
![[Pasted image 20240903161746.png]]

## Recursos
+ https://medium.com/@ashleylynnrapone/database-design-from-entity-relationship-diagrams-to-physical-diagrams-16da210d01e9 - Repaso modelo logico / conceptual / fisico
+ https://miro.com/diagramming/er-diagram-vs-relational-diagram/
