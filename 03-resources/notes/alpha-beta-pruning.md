---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
---

+ Jhon McCarthy
+ Técnica para calcular decisión minimax sin examinar todos los nodos del árbol
## Poda alpha

**Regla**
> Si mi abuelo (soy un nodo) MAX es mayor o igual que yo puedo podar a mis hermanos a la derecha

![[Pasted image 20240927101014.png]]

Como MIN va a escoger el menor entre sus hijos, se encontró un nodo con valor menor a 3 y MAX va a escoger el valor máximo, no se necesita explorar a sus hermanos

![[Pasted image 20240927152048.png]]
### Ejemplo
![[Pasted image 20240927141819.png]]

### Visualización Implementación
![[Pasted image 20240927140232.png]]![[Pasted image 20240927140239.png]]


## Poda beta

**Regla**
> Si mi abuelo (soy un nodo) MIN es ==menor o igual== que yo puedo podar a mis hermanos a la derecha

![[Pasted image 20240927172348.png]]

## Alpha-Beta <- combinar
**Ej 1**
![[Pasted image 20240927175605.png]]
