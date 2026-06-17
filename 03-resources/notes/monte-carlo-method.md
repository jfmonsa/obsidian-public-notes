---
mocs:
    - "[[public-notes/03-resources/simulation.moc.md|Computational Simulation]]"
tags:
    - cs/simulation
---

+ **Monte Carlo Methods**, or **Monte Carlo experiments** are a broad class of computational algorithms that rely on ==repeated random sampling== to obtain numerical results
+ Aplicado en escenarios donde los metodos analiticos son impracticables
+ The underlying concept is to use [randomness](https://en.wikipedia.org/wiki/Randomness "Randomness") to solve problems that might be [deterministic](https://en.wikipedia.org/wiki/Deterministic_system "Deterministic system") in principle

![[Pasted image 20241120112751.png]]
## Pasos generales:
1. Define a domain of possible inputs
2. Generate inputs randomly from a [probability distribution](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution") over the domain
3. Perform a [deterministic](https://en.wikipedia.org/wiki/Deterministic_algorithm "Deterministic algorithm") computation of the outputs
4. Aggregate the results
## Ventajas:
- Aplicable a problemas multidimensionales.
- No depende de restricciones lineales o analíticas.
## Limitaciones:
- Puede ser computacionalmente costoso.
- La precisión depende de la cantidad de simulaciones.

Usa Monte Carlo cuando no exista una solución exacta y la simulación sea viable.