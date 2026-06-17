---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
    - lang-es
---

# Diseño Conceptual (ERD) - Modelo Entidad Relación
+ Describe un conjunto de conceptos de una realidad y cómo se relacionan entre ellos (Información requerida por el negocio)
+ Descripción de alto nivel de la DB
+ Modelos conceptuales más usados
	1. ERD  / MER (Chen)
	2. Class Diagram UML
![[Pasted image 20240823173138.png]]

## Conceptos
+ Entidades (sustantivo / noun) - rectangulo
+ Relaciones (verbs) - rombos
+ Cardinalidad
+ Correspondencia (cardinaliad maxima) (1,n) != (n,1)
![[Pasted image 20240823173416.png]]
+ Dominio de atributos (No se modela dentro del diagrama): conjunto de valores que el atributo puede tomar
+ Tipos de atributos
	+ Mono / multivalorados
	+ Almacenados / derivados
	+ compuestos / atomicos
	+ Llave primaria
+ Redundancia:
	+ Ojo con los ciclos (condición necesaria pero no suficiente para redundancía)

