---
mocs:
    - "[[public-notes/03-resources/foundations.moc.md|Foundations]]"
tags:
    - cs/foundations
---

## Pure Functions
+ a pure function is a function that:
	1. function return values are identical for identical arguments (no variation with local static variables, non-local variables, mutable reference arguments or input streams, i.e., referential transparency
	2. The function has no side-effects (no mutation of local static variables, non-local variables, mutable reference arguments or input/output streams).
## High Order Functions - HoF
+ Funciones de orden superior
+ Son funciones que pueden:
	+ Recibir otras funciones como argumentos
	+ y/o devolver otras funciones como resultados
+ e.g.: map, filter,

## Closures
+ A closure is a function value that references variables from outside its body.
+ Un **closure** es una función que puede capturar y referenciar variables del entorno en el que fue declarada.
- Estas variables no se pierden cuando la función externa termina, porque el closure "recuerda" y sigue accediendo a ellas.
```go
func adder() func(int) int {
	sum := 0
	return func(x int) int { // Closure
		sum += x // Captura y modifica la variable `sum`
		return sum
	}
}

func main() {
	pos, neg := adder(), adder() // Cada llamada a adder crea un nuevo closure
	for i := 0; i < 10; i++ {
		fmt.Println(
			pos(i),       // Usa la primera instancia del closure
			neg(-2*i),    // Usa la segunda instancia del closure
		)
	}
}
```

Cada llamado de adder() es una instancia independiente

```go
// fibonacci is a function that returns
// a function that returns an int.
func fibonacci() func() int {
	val_0 := 0
	val_1 := 1
	return func() int {
		result := val_0 + val_1
		val_0 = val_1
		val_1 = result
		return result
	}
}

func main() {
	f := fibonacci()
	for i := 0; i < 10; i++ {
		fmt.Println(f())
	}
}
```