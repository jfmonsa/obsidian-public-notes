---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - meta/lang/es
---

## 1- Algoritmo - Preferente por amplitud
+ Expandir el nodo raíz, esto genera los nodos de profundidad 1
+ Expandir de izq a der, cada nodo de profundidad 1
+ Continuar expandiendo de izq a der, cada uno de los nodos de la profundidad $d$ y luego los de $d+1$

> De arriba hacia abajo, de izq a der (Prof Joshua)

+ Classic BFS
+ Lista nodos creados y lista nodos expandidos
+ Expandir: verificar si es meta, si lo es acaba el algo, si no lo es crea a sus hijos

### Ejemplo 1
![[Pasted image 20240910064838.png]]

+ Lista nodos creados = `[Z,W,X,T,P,Y,F,E,A,C,Q,R,K,L,G]`
+ Lista nodos expandidos = `[Z,W,X,T,P,Y,F,E,A]`

En otras Palabras:
1. expando Z, es meta? No ->  creo sus hijos W,X,T
2. expando W, es meta? No -> creo sus hijos P, Y  - Lista creados `[Z,W,X,T,P,Y]`
3. expando X, es meta? No -> creo sus hijos F,E - Lista creados `[Z,W,X,T,P,Y,F,E]`
4. expando T, es meta? No -> creo sus hijos A,C Lista creados `[Z,W,X,T,P,Y,F,E,A,C]`
5. expando P, es meta? No -> creo sus hijos Q,R ->Lista creados `[Z,W,X,T,P,Y,F,E,A,C,Q,R]`
6. expando Y, es meta? No -> creo sus hijos K,L -> Lista creados `[Z,W,X,T,P,Y,F,E,A,C,Q,R,K,L,G]`
 y así sucesivamente hasta llegar al pas donde se expande A la cual es la primera meta:
 n. expando A, es meta? Si -> Termino (No tengo que crear nada)

---

+ ==Nota==: siempre se arranca creando la raíz en ambas listas
+ ==Nota==: Evite deovolverse = no devolverse al nodo padre del nodo actual


### Ejemplo 2
![[Pasted image 20240910070810.png]]
![[Pasted image 20240910070823.png]]

## Implementación
+ Cuando tenemos un mapa o un grafo, es importante guardar los nodos visitados para no volver a expandirlos
![[Pasted image 20240910071454.png]]
![[Pasted image 20240910071505.png]]

## Análisis del algoritmo
+ **Completitud**: Si existe una solución, la encuentra? Si
+ **Complejidad temporal** $O(b^d)$
+ **Complejidad espacial** $O(b^d)$
+ **Solución óptima**: en caso de que existan varias soluciones encuentra la mejor? no
---
+ $b$ <- factor de ramificación
+ $d$ <- depth (profundidad o altura) la raiz es el nivel 0
### Explicación

+ En el peor caso tendremos que recorrer todos los nodos:
	+ Formula para calcular el numero de nodos de un arbol n-ario  $b^{d+1}-1$ 
	+ Pero en clase se usa $O(b^d)$ no es toda la sumatoria, pero $b^d$ es el termino más significativo en la función al interior de la cota asintotica
	
![[Pasted image 20240916211941.png]]