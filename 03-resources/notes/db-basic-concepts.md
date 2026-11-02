---
mocs:
    - "[[public-notes/03-resources/foundations.moc.md|Foundations]]"
tags:
    - cs/foundations
---

# 1 - Basic Concepts
+ **Dato**: valor de alguna característica de una entidad, con significado implicito
+ **Información**: Conjunto ordenado de datos
	+ Con contexto
+ **Base de datos**: Conjunto de información agrupada (relacionada)

## What's a Data Base?
+ Represents aspects of the real world: ***mini world***, ***Universe of Discourse (UoD)***
+ logically coherente collection of data with inherent meaning
+ Designed, built and populate for a specific purpouse
## Data Base Management Systems (DBMS / SGBD)
+ Is a collection of programs that enables users to create and maintain a database
+ **Features**: CRUD,  Guarantee data integrity, security, dictionary of metadata, transactions, data independence, backup and recovery subsystem, Storage Structures and Search Techniques for Efficient Query Processing (indexes, caching and buffering), Multiple users, enforcing Integrity Constraints (business rules.)
+ **Instructions**: DML, DDL, DCL, Data Dictionary, TCL
+ **Objectives**: Reduce Redundancy and inconsistency solving problems such as: duplication of effort (logical updates in multiple files), storage space wasted, inconsistent repeated data (Problems related to storing registers in separated files approach)
+ **Controlled Redundancy (denormalization)**: In practice, it is sometimes necessary to use controlled redundancy to improve the performance of queries. E.g. Likes of Instagram Problem
## DB Design Methodology
1. **Requirements**: Funcionales y no funcionales
2. **Conceptual Design**: Esquema conceptual (Modelo Entidad Relación / UML) - Nivel de abstracción mayor, modela la lógica del negocio
3. **Logic Design**: Modelo relacional y normalización
4. **Diseño Físico**: depende del DBMS estructuras de datos y técnicas de acceso - definimos tipos de datos, constraints, datos a insertar en ciertas tablas por default, triggers, indexes

