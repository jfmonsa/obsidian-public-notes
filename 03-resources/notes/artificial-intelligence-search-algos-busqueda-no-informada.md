---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - lang-es
---


+ Búsqueda sin heuristicas, no hay caminos prioritarios
## Metodología para solucionar un problema
1. **Formulación del problema**: Un problema bien definido, definir:
	+ **1. conjunto de estados**
		+ como se ==representa== el estado actual
		+ cuales son los posibles estados
		+ estado inicial
	+ **2. operadores**
		+ Aplicados sobre un estado particular genera un conjunto de estados posibles
	+ **3. Prueba de meta**
		+ Permite saber si el estado actual es un estado meta
	+ **4. Costo asociado** (==Función de costo de ruta==)
		+ Se le asigna un costo a una ruta determinada
		+ El costo es la suma de los costos de cada una de las acciones individuales a lo largo de la ruta
		+ denotado por la letra $g$
1. **Búsqueda**: Evaluar acciones posibles y decidir la más apropiada
2. **Ejecución**: Una vez encontrada la solución, se  procede a ejecutar la secuencia de acciones

+ ==Nota==: Cuando nos indican que los costos de todos los movimientos (operadores) son iguales, el costo es 1 (por cada movimiento) ==entonces el costo total será la cantidad de movimientos==

+ ==Nota==: ver en diapositivas ejemplos de: 8-puzzle, el mundo de la aspiradora, misioneros y caníbales ==como representar estados==

### Árboles de Búsqueda
+ Permite facilitar la comprensión de las exploraciones
	+ Estado inicial = nodo raíz
	+ Se expande el nodo raíz al aplicar los operadores sobre el nodo
	+ En cada paso el algo de búsqueda escoge un nodo hoja y lo expande
![[Pasted image 20240910064019.png]]

## Nodo
Cada nodo del árbol guarda lo siguiente:
+ El estado del problema
+ Una referencia la nodo padre
+ El operador que se aplicó para generar el nodo
+ Profundidad del nodo
+ El costo de ruta desde la raíz hasta el nodo

Métodos de un nodo:
+ aplicarOperador()
+ esMeta()

# Algoritmos de búsqueda no informada
## 1 -  [[busqueda-no-informada-algo-preferente-por-amplitud]]
## 2 - [[busqueda-no-informada-algo-de-costo-uniforme]]
## 3 - [[busqueda-no-informada-preferente-por-profundidad]]
## 4 - [[busqueda-no-informada-algo-limitada-por-profundidad]]
+ 1. Busqueda Preferente Por Profundidad Evitando Ciclos
## 5. [[busqueda-no-informada-por-profundizacion-iterativa]]
