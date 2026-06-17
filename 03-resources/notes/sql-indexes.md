---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
---

# Indexes
+ Is a data structure that you build, you assign, o top of an existing table that looks through your table and can create kind of shortcuts. ej: phone book guide example

postgres docs:
> Indexes are a common way to enhance database performance. An index allows the database server to find and retrieve specific rows much faster than it could do without an index. But indexes also add overhead to the database system as a whole, so they should be used sensibly.

+ Every PK has an index by default 
+ `EXPLAIN ANALYZE <query>` for postgresql

## Buenas Practicas
+ Evita usar índices en columnas que se actualizan constantemente, como el número de partidas jugadas o coins ganados, ya que los índices se deben mantener actualizados en cada modificación, lo que afecta el rendimiento.
+ En tablas con pocos registros, los índices no aportan una mejora significativa y podrían incluso ralentizar las operaciones de inserción o actualización
+ **Uso de indices compuestos**: Si tu consulta utiliza múltiples condiciones (por ejemplo, filtrar por jugador y por modo de juego), es mejor usar un índice compuesto en lugar de índices separados en cada columna
+ Evita crear índices en columnas con pocos valores únicos (por ejemplo, columnas booleanas o con pocas opciones), ya que el motor de la base de datos no podrá aprovechar bien esos índices
+ **joins** Asegúrate de tener índices en las columnas que se utilizan como claves foráneas, ya que los `JOIN` se ejecutarán mucho más rápido con estos índices.
+ 1. - Usa herramientas de monitoreo de bases de datos (como `EXPLAIN` en SQL) para evaluar el rendimiento de tus consultas. Si un índice no mejora el rendimiento o lo empeora, puede ser necesario eliminarlo.
+ To keep your database efficient, it's important to find and ==remove any unused indexes==
## Resources
+ https://youtu.be/-qNSXK7s7_w?si=jTl0K2PstTzhO2jw - # Explicación de la indexación de bases de datos (con PostgreSQL) - Hussein Nasser (English)
+ https://www.postgresql.org/docs/current/indexes-intro.html
+ https://medium.com/scalereal/demystifying-database-indexes-in-postgres-5c1a6d949943
+ https://www.youtube.com/watch?v=Nr6KRZuh3Cg - You're wrong about foreign key indexes
