---
mocs:
    - "[[public-notes/03-resources/discrete-math.moc.md|Discrete Math]]"
tags:
    - math/discrete
---

# Intro
+ a.k.a: (Propositional calculus, first-order propositional logic, statement logic, setential calculus, sentential logic, zeroth-order logic)
+ Deals with **propositions** (which can be true or false) and relations between propositions
+ is typically studied with a [formal language](https://en.wikipedia.org/wiki/Formal_language "Formal language"), in which propositions are represented by letters (**propositional variables** or **atomic formulas**). **compound propositions** or **molecular sentences**  are created by combining propositions with connectives
+ **Main  oprators**: $A \land B$ , $A \lor B$, $\lnot A$, $A \rightarrow B$ 
---
+ otros conceptos: **formulas bien formadas**, **metavariables**
# Arguments
e.g.
1.  Mañana es miércoles **o** mañana es jueves.
2.  Mañana **no** es jueves.
3.  **Por lo tanto**, mañana es miércoles
---
+ **Valid argument**: Es imposible que las **premisas** (1) y (2) sean verdaderas y la conclusión sea falsa
+ **valid argument !== true conclusion (_soundness_)**  si las premisas son falsas, entonces la conclusión también podría serlo.

# Notable Rules
+ doble negación
+ Idempotencia (Tautology) $V \land V = V$ y  $V \lor V = V$
+ Asociatividad
+ conmutativa
+ distributivas 
	+ $\alpha \land (\beta \lor \gamma) = (\alpha \land \beta) \lor (\alpha \land \gamma)$
	+ $\alpha \land (\beta \lor \gamma) = (\alpha \lor \beta) \land (\alpha \lor \gamma)$
+ Leyes de Morgan
+ Material Implication $\alpha \rightarrow \beta = \neg \alpha \lor \beta$ 
+ Transposition (contraposition) $\alpha \rightarrow \beta = \neg \beta \rightarrow \neg \alpha$
# Reglas de Inferencia
Una [regla de inferencia](https://es.wikipedia.org/wiki/Regla_de_inferencia "Regla de inferencia") es una [función](https://es.wikipedia.org/wiki/Funci%C3%B3n_matem%C3%A1tica "Función matemática") que va de conjuntos de fórmulas a fórmulas. 
+ **premisas**: conunto de formulas que la función toma como argumento
+ **conclusión**: conjunto de formulas que la función retorna

>On the basis of asumptions you derive conclusions
---
+ Use Gentzen notation 
$${\displaystyle {\frac {P\to Q,P}{Q}}} = \displaystyle P\to Q,P\vdash Q$$
---

![[Pasted image 20241125211938.png]]
![[Pasted image 20241125222142.png]]
![[Pasted image 20241125223020.png]]
+ Note:
	+ Addition == O-Introducción
	+ Conjunction == y-introducción
	+ Simplification == y-eliminación

## Examples
1. Convierta a notación de conjuntos y demuestre

+ > para convertir a notación de conjuntos: 1. reemplazar las disyunciones por **","**, cada formula agruparla en **parentesis**, convertir **implicaciones**.
1. $a \lor c \lor m \lor s \lor e \lor n$
2. $(a \lor c) \rightarrow v$
3. $(m \lor s) \rightarrow b$
4. $(e \lor n) \rightarrow p$
5. $( \lnot e \rightarrow \lnot s)$
6. $\lnot c$
7. $\lnot a  \rightarrow \lnot v$
8. $\lnot c \rightarrow \lnot p$
9. $\lnot n \rightarrow ( \lnot m \lor \lnot e)$
# Prueba por contradicción
+ resuelve limitaciones de la logica proposicional
+ Probar $BC \vDash \alpha$ , consiste en demostrar una contradicción $BC \land \lnot \alpha \vDash \square$  
	+ $\square$ es la clausula vacia (representa contradicción
### Ejemplo
+ Nota:. la BC original es la de 1 a 4, la regla 5 se adiciona para hacer la contradicción
![[Pasted image 20241129233914.png]]
![[Pasted image 20241129234516.png]]

# Árbol de derivación
Permite ver la secuencia de pasos que hacen parte de la
demostración en una estructura de árbol
+ Demostrar $\lnot r$ por contradicción
![[Pasted image 20241130001131.png]]
![[Pasted image 20241130001150.png]]
# Resources
+ https://es.wikipedia.org/wiki/L%C3%B3gica_proposicional#Dos_sistemas_formales_de_l%C3%B3gica_proposicional (ver como se construye un sistema formal de logica: alfabeto, Gramatica (gramatica bien formada, ¿como debería usar el alfabeto?), axiomas (verdades, para construir demostraciones ulteriores), Reglas de Inferencia
+ https://youtu.be/HcS4lqXxrV4?si=f8729RGjzcGm3r2P Reglas de Inferencia (Good, short video)
