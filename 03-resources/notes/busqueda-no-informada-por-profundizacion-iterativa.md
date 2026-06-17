---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - meta/lang/es
---

# Algo Profundización Iterativa
+ Prueba todos los límites de profundidad posibles, inicialmente toma como límite 0 y lleva a cabo búsqueda limitada por profundidad, luego aumenta a 1 y realiza el procedimiento, así hasta encontrar alguna solución

## Ejemplo
![[Pasted image 20240916231449.png]]
![[Pasted image 20240916231506.png]]
![[Pasted image 20240916231513.png]]
![[Pasted image 20240916231522.png]]
![[Pasted image 20240916231539.png]]


## Analisis del algoritmo

![[Pasted image 20240916231609.png]]
+ Hay nodos que se vuelven a expandir en cada nivel, el nodo raíz se expande $d+1$ veces, sus $b$ hijos se expanden $d$ veces, los hijos de los hijos que son $b²$ se expanden $d-1$ 

+ **Complejidad Temporal**: $(d+1)*1 + (d)*b + (d-1)*b² + \dots 1*d^b = O(b^d)$
+ **Complejidad espacial**: $O(b*d)$
