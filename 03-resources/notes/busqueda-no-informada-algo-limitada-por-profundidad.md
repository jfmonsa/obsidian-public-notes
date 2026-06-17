---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - lang-es
---

# Algo Búsqueda Limitada Por Profundidad
+ Se establece una ==profundidad máxima== hasta la que se explora, cuando se llegue a ésta, se continúa con las profundidades anteriores
+ El límite a usar depende del problema en particular
+ El ciclo se detiene en la profundidad máxima y se explora otra rama
## ¿Que limite elegir?
+ Depende del problema
+ Cual sería un buen limite?
![[Pasted image 20240916230721.png]]

+ En muchos problemas no es fácil conocer el limite
+ Que pasaría si se selecciona un límite que es menor a la profundidad donde se encuentra la solución real?

## Analisis del Algoritmo
+ **Completitud?**: Si, siempre que se elija un limite que incluya alguna solución
+ **Complejidad temporal** $O(b^l)$ donde $l$ es el limite o profundidad máxima
+ **Complejidad espacial**:  $O(b*l)$
+ No es optimo
---
Intenta tomar lo bueno de preferente por profundidad que consiste en que se puede llegar más rápido a una solución que amplitud y se intenta solucionar el problema de los bucles infinitos
