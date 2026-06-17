---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
---

Tipo de contrincantes
+ Humano vs Humano
+ Humano vs Maquina
+ Maquina vs Maquina

## Estrategias
+ The Theory of Games Beahavior, Von Neumann, 1944
+ Dilema del prisionero. Abert Tucker
![[Pasted image 20240927082000.png]]
+ Equilibrio de Nash
	+ Si un juego tiene un unico equilibrio de Nash y los jugadores son completamente racionales, escogerán las estrategias que forman el equilibrio
	+ Tic Tac Toe: si ambos juegan racionalmente siempre termina en empate (9!)

## Teoria de Juegos
+ Construir el árbol de juego
+ Analizar el árbol


# Algo minimax
+ Juegos de dos participantes
+ Permite encontrar la acción que debería realizar MAX para minimizar la perdida en el juego

> La salida del algo es la jugada que debería realizar MAX


**Formalmente**
+ Definición formal de juego requiere:
	+ Estado Inicial
	+ Conjunto de Operadores
	+ Prueba Terminal
	+ Función de utilidad -> asigna valor númerico al resultado obtenido de MAX
---
+ En juegos donde se gana o se pierde:
	+ f=1 si gana
	+ f=-1 si pierde

![[Pasted image 20240927082836.png]]
![[Pasted image 20240927083203.png]]
![[Pasted image 20240927083329.png]]

+  **Desición minimax**
	+ Es la respuesta que debe dar el algo (camino a escoger)
		+ la que proporcione mayor utilidad
		+ si todas las opciones tienen la misma utilidad ==no hay desición minimax==

### Ejemplo 1
![[Pasted image 20240927090644.png]]
### Analisis
+ Complejidad Temporal: $O(b^m)$
+ Complejidad espacial: $O(b*m)$
### Implementación
+ **Nodos**: Cada nodo guarda:
	+ tipo: MIN, MAX
	+ profundidad
	+ utilidad: inicializada en $\infty$ y $-\infty$
+ Construcción del arbol:
	+ explorar árbol en profundidad
	+ uso de una pila
	+ Cuando se expande una hoja se calcula su profundidad
	+ Una vez terminada la construcción se recorren los nodos en un arreglo desde los más profundos hasta la raíz
	+ Cada nodo informa al padre su utilidad
	+ Cuando se llegue a la raíz se tendrá el valor minimax

![[Pasted image 20240927094512.png]]

**Pasos**
1. Se busca un nodo en la profundidad máxima presente en el vector
2. El nodo seleccionado informa a su padre el valor de su utilidad
3. Se actualiza la utilidad del padre (dependiendo si es MIN o MAX)
4. Se elimina el nodo del vector

![[Pasted image 20240927094643.png]]

Nota: como se puede observar la estructura de la parte baja es una pila