---
mocs:
    - "[[public-notes/03-resources/discrete-math.moc.md|Discrete Math]]"
tags:
    - math/discrete
---

# Predicate Logic - Intro
+ a.k.a. First-order logic, predicate calculus, quatificational logic
+ First-order logic uses quantified variables over non-logical objects, and allows the use of sentences that contain variables.
+ Propositional Logic is the basis of First-order logic, First-order logic adds **predicates** and  **quatifiers**

## Predicate (formula)
statements involving variables, que puede conectar con una o varias expresiones para formar una oración. Los predicados son ==Tratados como funciones==. e.g $\text{isPhilosopher}(x)$

+ **Thre truth value of a formula ...** The truth of a formula such as "_x_ is a philosopher" depends on which object is denoted by _x_ and on the interpretation of the predicate "is a philosopher". (==variables = subjects==)
+ Relationships between predicates can be stated using logical connectives. e.g. "if _x_ is a philosopher, then _x_ is a scholar"
## Quantifiers
are applied to variables in a formula
+ **Existencial**: $\exists$ (exists) $\exists x P(x)$ There exists an element x in the domain such that $P(x)$ is true
+ **Universal**: $\forall x P(x)$, $P(x)$ is true for all values of $x$ in the domain. to prove false find a counter example
## Domain of Discourse
+ **Domain of discourse**: the entities that can instantiate the variables

> A theory about a topic, such as set theory, a theory for groups, or a formal theory of [arithmetic](https://en.wikipedia.org/wiki/Arithmetic "Arithmetic"), is usually a first-order logic together with a specified [domain of discourse](https://en.wikipedia.org/wiki/Domain_of_discourse "Domain of discourse")

> The domain of discourse _D_ is a ==nonempty set of "objects"== of some kind. Intuitively, given an interpretation, a first-order formula becomes a statement about these objects; for example, $\exists x P(x)$ states the existence of some object in _D_ for which the predicate _P_ is true

## Términos Base
Pueden ser:
1. constantes que representan entidades especificas del dominio del discurso. e.g `Juan`,`3`, `rojo`
2. predicados aplicados sobre valores: e.g `mayorQue(3,2)`, `hermano(Juan,Pedro)
# Rules of Inference
+ Usa todas la reglas de la logica proposicional pero además la **Eliminación universal, Eliminación existencial, Modus Ponens Generalizado**
## Eliminación Universal
$$ \frac{\forall x \ \alpha}{\text{SUST}(\{x / g\}, \alpha)} $$
Donde: 
+ $x$ es una variable
+ $g$ es un termino base
+ $\alpha$ es una formula lógica
### Ejemplo
#### 1)
BC:
1.  $\forall x \ \text{leGusta}(x, \text{ElHelado})$
---
Aplicando eliminación universal:
2. $\text{leGusta}(\text{Juan},\text{ElHelado})$ <- Elim-Universal(1), $\theta = \{ x / \text{Juan} \}$
#### 2)
![[Pasted image 20241126000536.png]]
+ Nota: ignorar linea 3, 1. aplicar 4 = elim-universal(1) y luego 5 = ModusPonens(4,2)
![[Pasted image 20241126000559.png]]


## Eliminación Existencial
$$ \frac{ \exists x \ \alpha}{\text{SUST}(x/k),\alpha} $$
Donde:
+ $x$ es una variable
+ $k$ es una constante que ==NO APARECE== en la base de conocimientos original
### Ejemplo
1. BC: $\exists x \ \text{Matar}(x,\text{Juan})$
2. $\text{Amigo}(\text{Luis},\text{Juan})$
---
Aplicando eliminación existencial
4. $\text{Matar}(\text{Pedro},\text{Juan})$ -> Elim-Existencial(1), $\theta = \{ x / Pedro \}$ 

## Modus Ponens Generalizado
Logra en un solo paso lo que se requería al aplicar
Eliminación universal, Y-Introducción y Modus ponens

$$ \frac{ p_1' \:  p_2' \dots \: (p_1 \land p_2 \land \dots p_n \to q)}{\text{SUST}(\theta,q)} $$
1. $p_i'$ son términos base, es decir, proposiciones específicas sin variables.
2. $p_i$ son proposiciones que pueden contener variables cuantificadas.
3. Si existe una sustitución $\theta$ que convierte $p_i$ en $p_i'$ entonces podemos usar la regla de Modus Ponens generalizado:
	+ Si sabemos que todas las proposiciones $p_i'$ son verdaderas y que $p_1 \land p_2 \land \dots \land p_n$ también es verdadera tras sustituir $\theta$ . Entonces $q$

### Condiciones
+ ==La implicación debe ser una **Sentencia de horn**==: conjunciones a la izquierda y a la derecha un solo atomo
### Ejemplo
#### 1)
**Usando MPG**
BC:
1. $P(a)$
2. $Q(a)$
3. $\forall x \, ((P(x) \land Q(x)) \to R(x))$ 
---
4. $R(a)$, MPG(1,2,3) $\theta = \{ x / a \}$
**Sino usaramos MPG** sería así (Mas largo)
BC:
1. $P(a)$
2. $Q(a)$
3. $\forall x \, ((P(x) \land Q(x)) \to R(x))$ 
---
4. $(P(a) \land Q(a)) \to R(a)$ Elim-universal(3) $\theta = \{x, a\}$
5. $P(a) \land Q(a)$ y-introducción(1,2)
6. $R(a)$ ModusPonens(4,5)
#### 4)
Demostrar F(a) usando MPG
![[Pasted image 20241130183118.png]]

## Forma Canónica
Cuando la base de conocimientos se forma exclusivamente
de **sentencias Horn** se dice que está en **forma canónica**

Pasos
+ Eliminar cuatificadores existenciales
+ Omitir cuantificadores universales
![[Pasted image 20241130182430.png]]

## Resolución Generalizada
$$ \frac{ p_1 \lor \dots \lor p_j \lor \dots \lor p_m \qquad \qquad q_1 \lor \dots \lor q_j \lor \dots \lor q_n}{\text{SUST}(\theta,p_1 \lor \dots p_{j-1} \lor p_{j+1} \dots \lor p_m \lor q_1 \lor \dots q_{j-1} \lor q_{j+1} \dots q_n)}$$
Donde:
1. $p_i$ son los terminos base
2. $q_i$ son los predicados cuantificados universalmente
3. existe una sustitución $\theta$ tal que unifiquen $p_i$ y $\lnot q_i$ 
### Ejemplo
1. Sin usar Resolución Generalizada
![[Pasted image 20241130185538.png]]
2. Usando Resolución Generalizada
![[Pasted image 20241130185614.png]]
## Forma Normal Conjuntiva (CNF)
+ Una fórmula está en CNF si es una **conjunción de cláusulas**, donde **cada cláusula es una disyunción de literales** (un literal es un predicado o su negación).
+ Ej: (P(x)∨Q(x))∧(¬R(x)∨S(x))
Pasos:
1. Eliminar implicaciones
2. Empujar negaciones: Leyes de morgan y doble negación
3. Eliminar cuantificadores existenciales

## Eliminar Cuantificadores Existenciales
### Caso 1
![[Pasted image 20241130190744.png]]

**Ejemplos**
+ $\exists x P(x)$ entonces: $P(a)$
+ $\exists x \forall y P(x) \lor Q(y)$  entonces: $\forall P(a) \lor Q(y)$
**Solución**
+ aplicar eliminación existencial: reemplazar variable por una constante que no esta presente en la BC original
### Caso 2
![[Pasted image 20241130220132.png]]

**Ejemplos**:
+ $\forall x \exists y (E(y) \land R(x,y)) \to A(x)$ entonces: $\forall E(f(x)) \land R(x, f(x))$
