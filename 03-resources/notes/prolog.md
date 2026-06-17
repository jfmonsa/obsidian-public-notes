---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
---

+ Programming in Logic
+ lenguaje declarativo
+ Desarrollado a partir de trabajos de demostración automática de teoremas
+ `.pl`
## Procesos Básicos
1. Declarar **hechos**
2. Declarar **reglas**
3. Hacer **preguntas** (tiempo de ejecución)
## Sintaxis
1. minuscula (funciones (predicados) y hechos)
2. mayuscula (variables logicas)
3. Cada sentencia termina en punto
## Declarar Hechos y Reglas (escribir programas)
Los programas `.pl` contienen la combinación de hechos y reglas, se caragan en la consola de prolog con el comando `nombreArchivo` 
### Hechos
Representan afirmaciones simples y terminan con un
```pl
progenitor(juan, maria).
```

### Reglas
Se escriben con el operador `:-` para expresar "si". El lado izquierdo es el **consecuente**, y el derecho son los **antecedentes**.
```pl
abuelo(X, Z) :- progenitor(X, Y), progenitor(Y, Z).
```
## Hacer preguntas a prolog (consultas)
### Consulta Simple
Para verificar si un hecho es cierto o falso, simplemente se escribe el hecho (prolog responde Yes o No)
```pl
?- progenitor(juan, maria).
```

### Consulta con variables
Para buscar valores que satisfagan una relación, se utilizan nombres en mayúscula como variables.
```pl
?- progenitor(X, maria).
```
Prolog devuelve todos los valores de `X` que cumplen la relación.
### Consultas compuestas
La "," representa conjunciones
```pl
?- progenitor(X, Y), progenitor(Y, Z).
```
Esto busca valores de `X`, `Y` y `Z` que cumplan ambas condiciones.
## Proceso de búsqueda en Prolog para responder preguntas
+ Algoritmo de Backtracking para explorar la BC
+ **Cuando hay conjunciones**: Prolog resuelve los predicados de izquierda a derecha

### Ejemplo
Dada la BC:
```pl
progenitor(pedro, teresa).
progenitor(maria, teresa).
progenitor(maria, elena).
progenitor(teresa, jorge). % (banderita para el backtracking)
progenitor(teresa, raquel).
progenitor(raquel, miguel).

/*
          pedro   maria
             \   /     \
             teresa     elena
             /    \
           jorge  raquel
                     /
                  miguel
*/
```

1. **Primer Predicado**: Prolog busca en la BC el primer hecho o regla que matchee con `progenitor(X, jorge)` primer resultado `X = teresa` 
2. **Segundo Predicado**: como en el anterior fue encontrado `X = teresa` entonces ahora prolog busca el hecho o regla que matchee `progenitor(Y, teresa)`  (==Arranca desde el inicio de la BC==) encuentra `Y = pedro` entonces produce como output `X = teresa, Y = pedro`
3. Continua la busqueda con `X = teresa` y encuentra `Y = maria` produce el output `X = tersa, Y = maria`
4. **Backtracking** prolog sigue buscando a ver si hay mas hechos o reglas que matcheen con la busqueda. prolog arranca desde donde dejó la bandera (no encuentra nada más y termina el output). Nota: antes de hacer backtracking continua buscando

> [!WARNING]
> El orden de clausulas afecta el orden de ejecución del programa (al defnir reglas y hacer consultas)

## Regla Recursiva

> [!WARNING]
> tener siempre el caso base antes del recursivo

```pl
antepasado(X,Z) :- progenitor(X, W), antepasado(W, Z)
```


