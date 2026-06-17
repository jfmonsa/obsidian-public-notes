---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - lang-es
---

## Algoritmo Búsqueda de Costo Uniforme
+ Se expande el nodo raíz
+ En cada nodo n del árbol se calcula el costo de la ruta $g(n)$
	+ costo acumulado desde el nodo actual hasta la raíz
+ Se expande el nodo de menor costo, sin importar a qué profundidad esté

![[Pasted image 20240910072835.png]]

![[Pasted image 20240910072847.png]]

![[Pasted image 20240910072903.png]]

![[Pasted image 20240910072917.png]]

---

+ ==Nota==: Si el ejercicio no indica criterio de desempate, se utiliza la amplitud
+ ==Nota==: Cuando aplicamos este algoritmo en problemas donde el costo es uniforme (cada operador = 1), esta técnica se comporta como El Algoritmo de Búsqueda Preferente por amplitud
+ ==Nota==: Es util cuando el costo de las operaciones varia bastante

**Ejemplo 1**
![[Pasted image 20240910073842.png]]
+ ==Nota==: La primera solución encontrada será la más barata puesto que si hubiera una más barata habría sido expandida anteriormente

**Ejemplo 2**
![[Pasted image 20240910075304.png]]
![[Pasted image 20240910075313.png]]
![[Pasted image 20240910075321.png]]
![[Pasted image 20240910075331.png]]
![[Pasted image 20240910075340.png]]![[Pasted image 20240910075405.png]]
![[Pasted image 20240910075421.png]]

vs

![[Pasted image 20240910075442.png]]
+ ==Nota==: Los ciclos no afectan la búsqueda por costo uniforme porque al repetir estados se acumula el costo de ruta

### Implementación
+ La lista de nodos a expandir como una ==cola de prioridad==, la prioridad es el costo, se selecciona aquellas con menor prioridad
### Analísis del algoritmo
+ **Completitud**: Si
+ **Complejidad Temporal**: Numero de nodos con costo menor al de la solución optima
+ **Complejidad espacial**: número de nodos con costo menor al de la solución optima
+ **Solución optima**: Si
