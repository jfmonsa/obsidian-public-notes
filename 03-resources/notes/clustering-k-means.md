---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
---

# Clustering
+ agrupar objetos por similitud, en grupos o conjuntos de manera que los miembros del mismo grupo tengan características similares
+ Tarea principal de la **mineria de datos** exploratoria

# K-means (naive)
+ **Propósito**: Es un algoritmo de _clustering_ no supervisado que agrupa datos en $k$ clústeres basándose en la similitud de los puntos.
+ computationally difficult ([NP-hard](https://en.wikipedia.org/wiki/NP-hardness "NP-hardness")); however, efficient [heuristic algorithms](https://en.wikipedia.org/wiki/Heuristic_algorithm "Heuristic algorithm") converge quickly to a [local optimum](https://en.wikipedia.org/wiki/Local_optimum "Local optimum"). These
+ sub-optimal

## Limitaciones
- Sensible a la inicialización de los centroides.
- requiere que los datos sean númericos
- Puede converger a un óptimo local.
- No maneja bien clústeres no esféricos ni con tamaños muy diferentes.
- Requiere definir el número de clústeres (kkk) de antemano.

## Pasos
- **Seleccionar $k$**:
    - Elegir el número de clústeres deseados ($k$).
- **Inicializar los centroides**:
    - Elegir $k$ puntos aleatorios como centroides iniciales de los clústeres.
- **Asignar puntos a los clústeres más cercanos**:
    - Para cada punto de datos, calcular la distancia a cada centroide.
    - Asignar cada punto al clúster con el centroide más cercano.
- **Recalcular los centroides**:
    - Para cada clúster, calcular el nuevo centroide como la media de todos los puntos asignados al clúster.
- **Repetir pasos 3 y 4**:
    - Asignar puntos numente según los nuevos centroides.
    - Actualizar los centroides.
    - Continuar hasta que los centroides ya no cambien significativamente o se alcance el límite de iteraciones.
# K-means++
+ variante (mejora) de k-means que busca abordar el problema de la **sensibilidad a la inicialización de los centroides**
+ **objetivo**: elegir los centroides iniciales de manera que estén bien distribuidos y se reduzcan las probabilidades de converger a un óptimo loca. centroides iniciales se eligen con un ==criterio probabilistico==

