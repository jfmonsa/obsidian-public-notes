---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/go
---

+ **Statically Typed Language**: types must be declare explicitly or can be inferred, variables cannot change typing afterwards.
+ **Strongly Typed Language**
+ Go is compiled
+ Garbage Collection
## File Organization
+ **Package**: Collection of go files (folders)
+ **Module**: Collection of go packages stored in a file tree with a `go.mod` file at its root
	+ When you init a project, you are iniiting a module
+ Each go file is part of a package 
```sh
# location
go mod init  github.com/user/repo/

go mod get <url> # add lib packages
go mod tidy # update deps
```
+ Symbols (function names, variables, constants, etc) which starts with lower case are only accesible in the package (**private**). to be public must start with upper-case.
## Functions
```go
package main
import "fmt"

func main(){
	fmt.Prinln("Hello World")
	var tempVariable int = "hola"
	// Shorthand and inferred type
	tempVar2 := "Holi"
}

func printMe(value string){
	fmt.Println(value)
}

func sum(a int, b int) int {
	return a + b
}
```

to compile it
```sh
go build cmd/tutorial_1/main.go
./main
```

Or
```
go run cmd/tutorial_1/main.go
```

## Variables and Datatypes
+ variables `var` keyword
+ const uses `const` keyword
### Datatypes
+ int, int8, int16, int32 and int64 or uint, uint8, uint16, uint64. for only positive integers
+ float32, float64

## Error Handling
+ Go uses a weird design pattern
```go
import ("errors")

fun main(){
  var result, reaminder, err = intDivision(11, 0)
  if err!=nil{
    fmt.Printf(err.Error())
  }
}

func intDivision(a int, b int) (int, int, error) {
	var err error
	if denomiator == 0 {
		err = errors.New("Cannot Divide by Zero")
		return 0, 0, err
	}
	result := a/b
	remainder := a%b
	return result, remainder
}
```

## Arrays
+ Fixed size
```go
var intArr [3]int32
# shorthands
var intArr [3]int32 = [3]int32{1,2,3}
intArr := [3]int32{1,2,3}

// or
intArr := [...]int32{1,2,3}
```

### Slices
+ An array has a fixed size. A slice, on the other hand, is a dynamically-sized
+ A slice does not store any data, it just describes a section of an underlying array. **Slices are like references to arrays**
+ Changing the elements of a slice modifies the corresponding elements of its underlying array.
+ A slice has both a _length_ and a _capacity_.
	+ The capacity of a slice is the number of elements in the underlying array, counting from the first element in the slice.
	+ You can extend a slice's length by re-slicing it, provided it has sufficient capacity.
+ Slices can be created with the built-in `make` function; this is how you create dynamically-sized arrays.
### Slice Literals
+ A slice literal is like an array literal without the length. https://go.dev/tour/moretypes/9
```go
s := []int{2, 3, 5, 7, 11, 13}
printSlice(s)
```
## Map
```go
var myMap map[string]unit8 = make(map[string]uint8)
// or
var muMap2 = map[string]uint8{"Adam": 23, "Sarah":45}
```

+ Be careful because in go, if you try to access a non existant key, it will return de default value of de type, to know if the value really exists:
```go
var age, ok = myMap2["Jason"]
if !ok {
	fmt.Println("Value don't exists")
}
```

## Loops
```go
for name, age := range myMap2{
	fmt.Printf("Name: %v, Age:%v \n", name, age)
}
```

## Pointers
+  A pointer holds the memory address of a value. 
```go
var p *int32 #use * 
// asign a free memory location, if not assign will give us a nil pointer exception
p = new(int32)

// To get the referenced value
p* // the value that is store in the address store by the pointer

// To reassinng the value
p* = 20;

// To assign the memory adddress of other variable to a pointer
var i int32;
&p = i
```

## Structs and Interfaces

### Struct
+ Collection of fields
+ Like object literals in js, even for achieving what a class could achieve
```go
type gasEngine struct{
	mpg uint8
	gallons uint8
}

func (e gasEngine) milesLeft() uint8 {
	return e.gallons*e.mpg
}
```

#### Methods
+ Go does not have classes. However, you can define methods on types.
+ receiver argument
+ You can declare a method on non-struct types, too.
```go
type Vertex struct {
	X, Y float64
}

func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}
```
+ https://go.dev/tour/methods/4
### Interfaces
```go
type engine interface {
	milesLeft() uint8
}
```
## Punteros / Paso Por Valor y Paso por Referencia
+ Por defecto si las funciones tienen como parametro un objeto se pasa por valor (se realiza una copia)
	+ Con el objetivo de evitar side-effects
+ Para cambiar este comportamiento usamos punteros
+ To acces the field X of a struct when we have the struct pointer `p` https://go.dev/tour/moretypes/4
---
There are two reasons to use a pointer receiver.

The first is so that the method can modify the value that its receiver points to.

The second is to avoid copying the value on each method call. This can be more efficient if the receiver is a large struc

## Type Assertions
+ code can panic, ok is used to avoid it
```go
strAsserted, ok := emptyInterface.(string) ; ok {
	// do things with asserted type
}
```
+ **type switch** can be use to check against multiple types
```go
switch v := value.(type){
	case int:
	case string:
	case float64:
}
```
### Reflection
```go
import "reflect"

alumno := "Jose"
reflect.TypeOf(alumno)
```

## Goroutines
+ Implementation of concurrency
+ Concurrency != Parallelism
+ Las goroutines son unidades de ejecución que se ejecutan de forma concurrente gestionadas por el **runtime de Go**, no por el sistema operativo.
+ **Multiplexado de hilos**, muchas go-routines sin el costo de crear hilos reales

## Channels
+ pass data through goroutines
+ Channels avoid race conditions "Thread safe"
+ Listen when data is added or removed from a channel
```go
func main(){
	var c = make(chan, int)
	c <- 1 // add data to the channel
	value := <-channel // read data from chanell
}
```

```go
package main

import "fmt"

func main() {
    c := make(chan int) // Canal sin búfer

    go func() {
        c <- 42 // Se bloquea hasta que el valor sea recibido
    }()

    fmt.Println(<-c) // Recibe el valor del canal
}
```
+ Buffered channels
```go
package main

import "fmt"

func main() {
    c := make(chan int, 3) // Canal con capacidad para 3 valores

    c <- 1 // No se bloquea
    c <- 2 // No se bloquea
    c <- 3 // No se bloquea

    fmt.Println(<-c) // Recibe: 1
    fmt.Println(<-c) // Recibe: 2
    fmt.Println(<-c) // Recibe: 3
}
```

### Select
En **Go**, el **`select`** es una construcción de control que permite trabajar con múltiples **canales** en una goroutine. Es útil para manejar la **concurrencia** y coordinar tareas entre diferentes canales.

El `select` actúa como un **switch** para operaciones de canal. Permite que una goroutine espere múltiples operaciones de envío o recepción en canales y ejecute la que esté lista primero.
```go
select {
case valor := <-canal1:
    // Ejecuta si hay un valor disponible en canal1
case canal2 <- dato:
    // Ejecuta si canal2 está listo para enviar el dato
default:
    // Ejecuta si ninguno de los casos anteriores está listo
}
```

```go
import (
	"sync"
)

var wg = sync.WaitGroup{}
var m = sync.Mutex{}
dbData = []strin{"id1", "id2", "id3"}
results = []string{}

func main(){
	// danger multiple go-runtines are modifying the same data structure use mutex here
	for i:=0; i<len(dbData), i++{
		wg.Add(1)
		go dbCall() # go is like await
	}
}

func dbCall(i int){
	// do call db things
	m.Lock()
	// nothe that we are usign slices
	results = append(results, dbData[i])
	m.Unlock()
	wg.Done()
}
```

What happens if several goroutines are trying to modify the same data structure (danger), for this use mutex (mutual exclusion)

+ wait Group
## Marshall / Unmarshall
+ convert json to string
## Context 
+ Is like a bucket that have extra funcionality like controll cancellation and the ability to store key/value pairs
+ Only use context for things that need to be propagated
![[Pasted image 20250410145705.png]]

## Architecture / Design Patterns
### Repository Pattern
+ https://youtu.be/eE8nqgryW_8?si=ZcTYU9KgLLhun4tk
![[Pasted image 20250410151605.png]]

# Learning Path
### 🔹 **ETAPA 1: Fundamentos sólidos de Go (1-2 semanas)**

**Objetivo:** Dominar lo esencial de Go para escribir y mantener microservicios.

#### 📘 Aprende lo esencial:
- Punteros (concepto clave en Go)
- Concurrencia: `goroutines`, `channels`, `sync`, `context`
---
### 🔹 **ETAPA 2: Microservicios con Go (2-3 semanas)**

**Objetivo:** Entender los patrones y herramientas comunes para microservicios en Go.
#### 🧱 Conceptos clave:

- Qué es un microservicio
- Comunicación: HTTP (REST), gRPC
- Manejo de errores, logging, timeouts, retries
- Separación por capas (handlers, servicios, repositorios)
- Middlewares
- Validaciones, DTOs
- Workers y jobs (como el que ya estás tocando)
---
### 🔹 **ETAPA 3: AWS Lambda + Infraestructura (3-4 semanas según dedicación)**

**Objetivo:** Entender cómo empaquetar y desplegar microservicios Go en AWS Lambda.

#### ☁️ Aprende:

- ¿Qué es Lambda y cómo se ejecuta Go allí?
- Uso de `aws-lambda-go` SDK
- Estructura de una función Lambda en Go
- Despliegue usando:
    - **SAM (Serverless Application Model)** o
    - **Serverless Framework** o
    - **Terraform** (más escalable)

---

# Resources
+ https://youtu.be/8uiZC0l4Ajw?si=yNGj-CdsuEjVVuIy - Learn Go in one hour
+ https://quii.gitbook.io/learn-go-with-tests Learn Go with tests
+ Let's Go further - Advanced patterns for building APIs and web applications in Go
+ 100 Go mistakes and how to avoid them
+ golang project structure (layout)
+ https://threedots.tech/post/list-of-recommended-libraries/
+ https://threedots.tech/go-in-one-evening/?utm_source=blog-content
+ https://microservices.io/
+ https://go.dev/tour/basics/1
## Project structure / architecture
+ https://leonardqmarcq.com/posts/go-project-structure-for-api-gateway-lambda-with-aws-sam
# Dudas
+ Linters in go?
	+ https://github.com/fzipp/gocyclo?ref=hackernoon.com for cyclomatic complexity
	+ https://go.dev/wiki/CodeTools
+ references, objetcs, opp 

---
1. Al usuario le llega un recordatorio de pago con un enlace a nuestro front (con un query param que incluye el pago que debería renovar)
	1. Esta pagina tiene un selector para que puede elegir renovar el mismo plan u otro en lugar del mismo
2. entra a ese enlace y aterriza en una pagina donde puede renovar el pago, le al botón de renovar y eso lo lleva a payu (configurarias a que lambda debe apuntar)
3. en la lambda pues ya recibes el id del pago que va a renovarse + la info de payu y creas el nuevo pago con la información
---
+inicio = fecha exp + los dias que faltan para vecerse, y el payment quede en inactivo u otro estado que sea para este tipo de casos
+ Si 

---
Dos posibilidades:
1. Si yo renuevo el pago de una comieza ese mismo día
2. Si yo renuevo el pago comience el día que vence el otro:
