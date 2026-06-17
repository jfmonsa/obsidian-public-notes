---
mocs:
    - "[[public-notes/03-resources/databases.moc.md|Databases]]"
tags:
    - dev/databases
---

# Normalization

+ La normalización es el proceso de refinar, mediante un conjunto de reglas (formas normales), un esquema de base de datos relacional, con el fin de resolver problemas de redundancia e integridad presentes luego de la transformación del modelo conceptual
+ Antes de hacer la normalización, debemos obtener todas las dependencias funcionales
![[Pasted image 20240904124132.png]]
## Concepto de Dependencia Funcional

+ **Dependencia Funcional**: Propiedad inherente a las interrelaciones de los atributos de una relación (tabla). en la que un grupo de atributos  (**Determinante**) define un único conjunto de valores (**Dependiente**)

### Definición Formal de Dependencia Funcional
Sean A y B conjuntos de atributos, entonces A -> B es una D.F. si dado un conjunto de valores para A, se tiene un único conjunto de valores para B.
+ **A determinan funcionalmente a B**
+ **B depende funcionalmente de A** 
+ A -> B iff A es una llave candidata
+ Los casos triviales se excluyen: $B \subseteq A$ ej. ISBN -> TituloLibro, ISBN (ISBN se exlcluye porque ya sabemos implícitamente que se determina funcionalmente así mismo)
### Ejemplos
ISBN -> TituloLibro
DNI -> Nombre, Sexo, FechaNacimiento

### Tipos de Dependencia Funcional
#### 1. Parcial
+ AX -> B, es una D.F. parcial si A->B es también una D.F, de lo contrario es **total**
+ En otras palabras (ejemplo): Si en el determinante tengo 2 a tributos y elimino uno y esa relación sigue siendo una D.F. entonces es una D.F parcial

**Ejemplo**
1. {Id, ~~nombre~~} -> {sexo, fecha nacimiento, dirección} <- D.F. parcial, si elimino nombre sigue siendo una D.F.
2. {Id} -> {sexo, fecha nacimiento, }
#### 2. Transitiva
+ A->B es transitiva si A->C y C->B son también D.F

**Ejemplo**:
{IdEmpleado} -> {nombre, sucursal, ciudad}
{sucrusal} -> {ciudad}
### Ejercicio 
Dado el siguiente enunciado (modelo lógico) obten sus dependencias funcionales

INMUEBLE (InmCod, InmIdPropietario, InmDirecc, InmNomPropietario,
InmCodCiudad, InmCodDepartamento, InmNumEscritura)

Dependencias Funcionales:

1- D.F Básica
{InmCod, InmIdPropietario} -> {InmDirecc, InmNomPropietario, InmCodCiudad,
InmCodDepartamento, InmNumEscritura}

2- DF Parciales
{InmCod} -> {InmDirección}
{InmIDPropietario} -> {Nombre Propietario}

3- Tramsitiva
{InmCiudad} -> {InmCodeDepartamento}

## Formas Normales
![[Pasted image 20240904143206.png]]

**Dependencias Funcionales:**
+ 1FN
+ 2FN
+ 3FN
+ Boyce-Codd
+ 4FN
+ 5FN

### 1FN
+ Una relación R está en 1FN iff no hay atributos multivalorados
+ Esto ya está garantizado por la conversión que hicimos
### 2FN
+ Una relación R esta en 2FN iff esta en 1FN y todos sus atributos no primos dependen funcionalmente de manera total de la llave primaria
+ No hay DF parciales

**Paso a 2FN**
+ Separar el determinante y los datos dependientes en su propia tabla

### 3FN
+ Una relación R esta en 3FN iff esta en 2FN y no hay dependencias funcionales transitivas desde la llave primaria hacia atributos no primos

**Ejemplo**: La relación SALES no está en 3FN
+ SALES(==Cust_Id==, Name, SalesPerson, Region)
+ {Cust_Id} -> {Name, SalesPerson, Region}
+ {SalesPerson} -> {Region}

**Paso a 3FN**
Para pasar de 2FN a 3FN, se deben quitar las
dependencias entre atributos no primos, dividiendo los datos
afectados en una nueva tabla

![[Pasted image 20240904144223.png]]

![[Pasted image 20240904144231.png]]

### Boyce-Codd FN (BCFN)
+ Una relación R está en BCFN si todo determinante de dependencias funcionales es una clave (llave

**Ejemplo**: La relación STUDENT no está en BCFN
+ STUDENT(==IDStudent==, ==Subject==, Teacher, Score)
+ {IDStudent} -> {Subject, Teacher, Score}
+ {Teacher} -> {Subject}
![[Pasted image 20240904144458.png]]
# Denormalization
+ Ejemplo Likes de Ig
	+ https://youtube.com/shorts/OW85ZAaQBSE?si=fqLI_QgHSqW_PcJW 
