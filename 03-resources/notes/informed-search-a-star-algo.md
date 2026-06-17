---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
---

+ por cada nodo calcula $f(n)=g(n)+h(n)$
	+ $h(n)$ función heuristica
	+ $g(n)$  es el costo acumulado (costo uniforme)
+ Expandir el nodo con menor $f(n)$

### Ejemplo 1
Agente minero
![[Pasted image 20240917081751.png]]

### Ejemplo 2
![[Pasted image 20240917081816.png]]
![[Pasted image 20240917081833.png]]

### Implementación
+  la lista de nodos a expandir como una cola de prioridad, donde la prioridad es el valor de f(n) y se selecciona aquel con menor prioridad

### Analysis
+ **Completa**: si
+ **Complejidad temporal**: n nodos con una f(n) menor que el costo optimo
+ **Complejidad espacial**: n nodos con una f(n) menor que el costo optimo
+ **Optima**: Si

> Si los valores de la heurística son muy pequeños, A* se vuelve como costo uniforme

----
Mas sobre desempeño:
+ $b^*$ Es el factor de ramificación efectiva
+ $N$ Número de nodos: $1+b^*+(b^*)²+...+(b^*)^d=N$ 
> En una heuristica bien diseñada, b* se aproxima a 1

---
A* es completo y optimo si se cumple con que la heuristica $h(n)$ sea admisible

# Resources
+ https://youtu.be/A60q6dcoCjw?si=h8Ib0G3QcB5edQ7V - The hidden beauty of the A* algorithm
+ http://theory.stanford.edu/~amitp/GameProgramming/index.html (Good respirce for pahtfinding in general)
+ https://www.redblobgames.com/pathfinding/a-star/introduction.html