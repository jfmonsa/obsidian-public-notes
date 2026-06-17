---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - lang-es
---


+ Expandir el nodo con menor $h(n)$
+ ==No es optima==
+ ==No es completa==
+ Es la PEOR entre informadas y no informadas

### Ejemplo 1
![[Pasted image 20240917075019.png]]

![[Pasted image 20240917075043.png]]

+ Pero esta solución no es la optima, el camino óptimo es:  Arad->Sibiu->Rimnicu->Pitesti->Bucarest porque tiene costo 418
### Ejemplo 2
+ Como observamos en este ejercicio esta estrategia no es completa
![[Pasted image 20240917075348.png]]
Qudá en un ciclo entre Neamt y Iasi
![[Pasted image 20240917075409.png]]

### Ejemplo 3
+ Complete el arbol de busqueda, no evite devolverse

![[Pasted image 20240917075548.png]]
### Ejemplo 4
![[Pasted image 20240917075649.png]]

### Implementation
+ La lista de nodos a expandir como una cola de prioridad, donde la prioridad es el valor de la heuristica (menor valor mejor)

### Analisis
+ **Completitud**: No
+ **Comp Temporal**: $O(b^d)$
+ **Comp Espacial**: $O(b^d)$
+ no es la función optima

### ¿Cual es la diferencia entre Avara y Costo Uniforme?
+ Radica en como seleccionan el próximo nodo a expandir
+ Costo uniforme usa el ==costo acumulado== lo que garantiza que el algo es completo
+ Avara usa una heuristica, el nodo con la distancia más corta estimada (puede llevar a ciclos, no es completa)
