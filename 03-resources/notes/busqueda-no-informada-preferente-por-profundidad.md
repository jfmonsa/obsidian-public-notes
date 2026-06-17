---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - lang-es
---


# Algoritmo Búsqueda Preferente por Profundidad
+ DFS
+ Se expande el nodo raíz
+ De izq a der, el nodo con mayor profundidad
+ Depende del orden de operaciones, con el orden incorrecto podría caer en ==ciclos infinitos==

### Ejemplo 1
![[Pasted image 20240910081218.png]]

+ Lista Nodos creados = `[H,A,B,C,D,E,K,L,P,Q,F,W,Y,R,J]`
+ Lista Nodos expandidos = `[H,A,D,K,L,P,Q,E,B,F,W,Y,R,J]

En otras Palabras:
1. Creamos nodo H
2. Expandimos H, ¿Es meta? No -> Creamos los hijos A,B,C. Lista creados = `[H,A,B,C]`
3. Expandimos A, ¿Es meta? No -> creamos los hijos D,E. Lista Creados `[H,A,B,C,D,E]`
4. Expandimos D, ¿Es meta? No -> creamos los hijos K,L. Lista creados `[H,A,B,C,D,E,K,L]`
5. Expandimos K ¿Es meta? No -> (No tiene hijos)
6. Expandimos L ¿Es meta? No -> creamos los hijos P,Q. Lista Creados = `[H,A,B,C,D,E,K,L,P,Q]`
7. Expandimos E ¿es meta? No -> No tiene hijos
8. Expandimos B ¿Es meta? No -> creamos los hijos F. Lista creados `[H,A,B,C,D,E,K,L,F]`
9. Expandimos F ¿Es meta? No -> creamos los hijos W,Y. Lista creados `[H,A,B,C,D,E,K,L,F,W,Y]`
10. Expandimos W ¿Es meta? No -> no tiene hijos
11. Expandimos Y ¿Es meta? No -> creamos sus hijos R, J. Lista Creados `[H,A,B,C,D,E,K,L,F,W,Y,R,J]`
12. Expandimos R ¿Es meta? No -> No tiene hijos
13. Expandimos J ¿Es meta? Si -> terminamos

### Ejemplo 2

+ En el siguiente ejemplo vemos que con un orden de operaciones diferente podemos caer en un ==ciclo infinito==
![[Pasted image 20240916223122.png]]
![[Pasted image 20240916223136.png]]

## Implementación
![[Pasted image 20240916223231.png]]
![[Pasted image 20240916223246.png]]

## Análisis del algoritmo
+ **Completitud**: no, puede caer en un ciclo infinito
+ **Complejidad Temporal**: peor caso $O(b^d)$
+ **Complejidad espacial**: $O(b*d)$ por que no es necesario guardar cada nodo, cada subarbol del árbol principal
+ **Solución optima**: no

## 2 - Búsqueda Preferente Por Profundidad Evitando Ciclos
+ Se evita un nodo que conduzca a un ciclo (Que sobre una misma rama se alcance un estado previo)
+ Evitar ciclo es un concepto más completo que evitar devolverse
	+ Evitar ciclo: Que sobre la linea directa no se repita estado
	+ Evitar devolverse: no puedo generar un hijo igual a mi padre

### Ejemplo y la solución que brinda
Con este algoritmo se evita el siguiente ciclo infinito generado por el algoritmo de Profundidad
![[Pasted image 20240916225751.png]]
Aquí está el ciclo:
![[Pasted image 20240916225702.png]]
Con este este algoritmo (Búsqueda por profundidad evitando ciclos lo superamos)
![[Pasted image 20240916225730.png]]