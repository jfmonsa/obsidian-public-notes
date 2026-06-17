---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

+ represent related things as a compund (Object)
+ e.g:
	+ A 2D coordinate consists of an x value and y value
	+ An amount of money consists of a number and a currency.
	+ Address

> (…) Objects that are equal due to the value of their properties, in this case their x and y coordinates, are called value objects. - Martin Fowler

+ Are use to model concepts in our system
+ - Encapsula en una clase dos atributos que por si solos no tienen sentido

## Entidades vs Value Objects
No hay que confundir nunca una entidad con un value object. La principal diferencia es que las primeras poseen una _identidad,_ un identificador que las hace únicas de cara a otra instancia de la misma clase.
+ e.g. A 2D coordinate doesn't have a unique id
+ las comparaciones entre value objects deben hacerse basándose en su contenido, y no un identificador o referencia.

## Inmutabilidad: Entidad vs Value Object

+ Los VO se conciben como objetos inmutables -> no se debe modificar su estado interno. la idea es que se comporten como tipos de datos primitivos (por ejemplo para hacer operaciones como `Obj1==Obj2`)

Si por ejemplo nuestra clase `Temperature` que representa la temperatura tuviese un método `increase(Temperature $temperature)`, tendríamos que asegurarnos de que después de llamar al método, la instancia no ha sido modificada, sino que ha devuelto un nuevo VO Temperature con el nuevo valor incrementado.

## Constructores
+ la unica "logica" que contienen son las validaciones en sus constructores cuando definimos un rango de valores limitado para sus propiedades
+ Se válida en la construcción, con lo que siempre tendrá un estado válido. En caso de no ser valida se lanza una excepción

## Examples
```Python
from dataclasses import dataclass

@dataclass(frozen=True)
class StreetAddress:
    """Represents a street address."""

    street: str
    city: str
```

## Resources
+ https://medium.com/all-you-need-is-clean-code/value-objects-d4c24115fa69
+ https://youtu.be/q_biZCsoloU?si=WVguWv-GpBG5Q6fD - # Mejora la Calidad de tu Código utilizando Value Objects - CodelyTV
