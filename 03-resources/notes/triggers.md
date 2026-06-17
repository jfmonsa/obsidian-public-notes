---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
---

# Triggers

+ son bloques de código SQL que se ejecutan automáticamente en respuesta a ciertos eventos en una tabla, como inserciones (`INSERT`), actualizaciones (`UPDATE`), o eliminaciones (`DELETE`). Están ligados directamente a eventos de las tablas
+ Usarlos únicamente para lógica que este relacionada con la integridad de los datos o acciones muy específicas que siempre deban ocurrir junto con una operación de base de datos.
+ Para otra lógica, que no dependa tan estrictamente de los datos, es mejor manejarla en el backend.
+ Los triggers deben ser simples y eficientes. No abuses de ellos para realizar cálculos o tareas muy pesadas, ya que se ejecutan automáticamente y pueden afectar el rendimiento
