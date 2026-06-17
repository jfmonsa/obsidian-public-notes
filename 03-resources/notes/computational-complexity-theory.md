---
mocs:
    - "[[public-notes/03-resources/theory.moc.md|Theory]]"
tags:
    - cs/theory
---

[]()+ determine the practical limits on what computers can and cannot do.
+ Studies Computational Complexity of problem solutions using Asymptotic notation [[asymptotic-notations]]
+ P vs NP (milenium prize problems)
---
+ A [computational problem](https://en.wikipedia.org/wiki/Computational_problem "Computational problem") can be viewed as an infinite collection of _instances_ together with a set (possibly empty) of _solutions_ for every instance.

# Clasification of problems (Classes)
+ Solution problems: e.g. Find all posible combinations of $S$ set such as the sum of all elements is equal to $P$
+ Decision problems: e.g. find if there is a hamiltonian path in a graph
+ Optimization problems: e.g. Travelling salesman problem
# Decidability and Tractability
## Decidability
**Decidability** refers to the question of whether a given problem can be solved by an algorithm in a finite amount of time. A problem is said to be decidable if there exists an algorithm that can provide a yes or no answer for every input instance of the problem.

> Existe una maquina de turing determinista que puede procesar cualquier entrada válida

**Some indecidible problems**:
+ The Halting Problem
## Tractability
deals with the practicality of solving a problem efficiently. A problem is considered tractable if it can be solved in **polynomial time**

# Turing Machines
+ A Turing machine is a mathematical model of a general computing machine.
+ The Device behaves like an Finte Automata
+ theoretical device that manipulates symbols contained on a strip of tape
+ Turing machines are not intended as a practical computing technology, but rather as a general model of a computing machine—anything from an advanced supercomputer to a mathematician with a pencil and paper.
+ It is believed that if a problem can be solved by an algorithm, there exists a Turing machine that solves the problem
+ Many types of Turing machines: deterministic, probabilistic, non-deterministic, quatum, etc.
---
## Formally
![[Pasted image 20250325203215.png]]

+ Maquina de Turing Determinista (DTM)
+ Maqunia de Turing No Determinista (permite ejecución paralela) (NDTM)

## Resources
+ https://www.matesfacil.com/automatas-lenguajes/Maquina-Turing.html
## Complexity Measure
+ the time required by a deterministic Turing machine $M$ on input $x$  is the total number of state transitions, or steps, the machine makes before it halts and outputs the answer ("yes" or "no").

# Complexity Classes
+ Many important complexity classes can be defined by bounding the time or space used by the algorithm.
![[Pasted image 20250224231552.png]]
A problem that can theoretically be solved, but requires impractical and finite resources (e.g., time) (NP-hard, exponential)
Conversely, a problem that can be solved in practice is called a _**tractable problem**_ P-TIME

----
+ **P (P-TIME)**:
	+ ==can be solve by a DTM in polynomial time==
+ **NP (Nondeterministic Polynomial time)**: 
	+ Cannot be solved by a DTM in polynomial time
	+ ==Is solvable by a NDTM in  polynomial time??
+ **NPC (NP-Complete)**:
	+ No polynomial solution is known but, it has be proved that cannot be solved in polynomial time
	+ ==Una solución puede ser probada en tiempo polinomial==
	+ ==Se debe construir un algoritmo que transforme cualquier instancia de $P_1$​ en una instancia de $P_2$​ **en tiempo polinómico**.==
	+ ejemplos: (Problemas de desición)
		+  **SAT** (satisfacibilidad booleana)
		+ **3-SAT** (satisfacibilidad con cláusulas de 3 literales)
		+ **Clique** (dado un grafo, existe un subconjunto de $k$ vértices todos conectados entre sí)
		+ otros: **Vertex Cover**, **Subset-Sum**, etc.
+ **NP-HARD**:
	+ Cannot be reduce to a NPC
	+ Cannot be verified by a DTM
	+ problemas de optimización
	+ **ejemplos**:
		+ TSP: Traveling Salesman Person

---
+ Un problema **NP-Completo** es un caso especial de problema **NP-Hard** que además pertenece a NP (es decir, sus soluciones se pueden verificar en tiempo polinomial).
+ Un problema **NP-Hard** puede ser más general, abarcando problemas que podrían ser incluso “más difíciles” que NP, o que no se pueden verificar en tiempo polinomial porque no son de decisión.
---

## $P=NP$ ?
+ No se sabe si $P=NP \lor P \neq NP$. Este es uno de los problemas abiertos más importantes en matemáticas e informática.
+ **$P=NP$**: Es una conjetura famosa en teoría de la complejidad. Si fuera cierta, significaría que cualquier problema cuya solución pueda verificarse eficientemente (en tiempo polinómico) también puede resolverse eficientemente (en tiempo polinómico).
+ El problema clave en la conjetura $P=NP$ es si **todos** los problemas en NP (especialmente los NP-completos) pueden resolverse en tiempo polinómico, no solo verificarse. Hasta ahora, no se ha encontrado ningún algoritmo polinómico para problemas NP-completos como el **Problema del Viajante de Comercio (TSP)** o **SAT (Satisfiabilidad Booleana)**, lo que sugiere que $P \neq NP$, pero aún no se ha demostrado formalmente.
+ **$NPC \subset NP$**, pero no necesariamente **$NPC=NP$**.
	- Los problemas NP-completos son los **más difíciles** dentro de NP porque cualquier problema en NP se puede reducir a ellos en tiempo polinómico.
	- Si **uno** de estos problemas tuviera una solución en $P$, entonces $P=NP$.
# Common Problems
## SAT (Problema de la Satisfactibilidad booleana)
+ Determinar si una expresión booleana sin cuantificadores, tiene asignada una asignación de valores
+ Primer problema en ser probado que es NPC por Stephen Cook 1971
+ El metodo de las tablas de verdad tiene una complejidad de $o(2^n)$
+ El problema puede simplificarse con la forma normal conjuntiva
---
# Reduction
+ La reducción se usa para demostrar que un problema es al menos tan difícil como otro problema conocido.
+ Se trata de reducir $P1$ que ya sabemos que es NPC a $P2$
+ consiste en transformar instancias de un problema $A$ en instancias de otro problema $B$
+ Para los problemas NP la reducción se realiza en tiempo polinomial
+ Se construye una función que, dada una instancia del problema $A$, genera una instancia del problema $B$ en tiempo polinomial.
+ Instancias positivas son mapeadas a positivas y negativas a negativas
---
- Si se puede reducir un problema conocido como (NP-Completo) a otro problema $B$ en tiempo polinomial, se demuestra que $B$ es al menos tan difícil como el problema original.
- Si se demuestra que $P1_1 \leq_p P_2$​ (es decir, $P_1$ se reduce a $P2$​), significa que si $P2$ se pudiera resolver en tiempo polinómico, entonces también se podría resolver $P1$​ en tiempo polinómico.
- Si $P1$​ ya es NP-completo y $P2$​ está en NP, entonces $P2$​ es NP-completo.

## Pasos para reducir un NPC conocido a otro NPC
1. $P_1$ Tiene que ser un NP (Obtener la complejidad)
2. Se debe poder hacer la reducción en tiempo polinomial desde el NPC conocido
3. Las salidas positivas ma mapean a salidas positivas, las negativas a negativas correctamente

## Algunas reducciones
### Reducir SAT a 3-SAT
+ k es el número de literales
|v| = k -3 => 6-3 =3 = {v1, v2, v3}
|c| = k-2 =>6-2 =4 
+  Pasar S = (¬X1 V ¬X2 V ¬X3 V X4 V X5 V X6) a 3-SAT
**Solución**
> (-x1, -x2, v1), (v1-, -x3, v2), (-v2, x4, v3), (v3-, x5, x6)
---
La transformación es lineal (por tanto polinomial) ya que se hace en función de $k$, $O(k)$
+ 4-SAT es lo mismo pero |v| = k - 4 y |c| = k - 3
---


+ Anotar las distintas complejidades de: 3-SAT, SAT, IP, Vertex Cover, Clique, SS, hamiltoniano, etc...