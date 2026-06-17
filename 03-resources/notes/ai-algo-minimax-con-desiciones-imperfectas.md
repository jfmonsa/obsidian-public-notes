---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - meta/lang/es
---

Existen juegos que son muy complejos, de tal manera que sería imposible explorar todos los estados posibles: ej: ajedrez, go. En la practica necesitaríamos memoria infinita

---
Esta estrategia:
+ Tenemos una profundida limite
+ bajamos hasta esa profundidad y en su nodo calculamos su utilidad y comenzamos a aplicar el minimax
	+ **Función de utilidad heuristica**

---
Algunas funciones de utilidad heuristica:
+ Tic tac toe: (n filas, columnas o diagonales libres para MAX) - (lo mismo pero para MIN)

**Ejemplo**: Profundidad 2
![[Pasted image 20240927230343.png]]

+ Ajedrez: combina varias funciones de utilidad heuristicas
	+ piezas MAX - MIN
	+ pares de caballos MAX - MIN
	+ etc.