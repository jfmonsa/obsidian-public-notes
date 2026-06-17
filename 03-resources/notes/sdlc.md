---
mocs:
    - "[[public-notes/03-resources/practices.moc.md|Practices]]"
tags:
    - dev/practices
---

+ an SDLC aims to produce high-quality systems that meet or exceed expectations, based on requirements, by delivering systems within scheduled time frames and cost estimates
+ SDLC Methodologies: Waterfall, Spiral, Agile.
+ SDLC methodologies fit within a flexibility spectrum ranging from agile to iterative to sequential
+ SDLC is not a methodology per se, but rather a description of the phases that a methodology should address
## Agile
+ methodologies, such as [XP](https://en.wikipedia.org/wiki/Extreme_Programming "Extreme Programming") and [Scrum](https://en.wikipedia.org/wiki/Scrum_(development) "Scrum (development)"), focus on lightweight processes that allow for rapid changes
## Desarrollo Tradicional  - Waterfall

![[Pasted image 20240904081117.png]]

**Problemas con waterfall**
+ No hay disposición de cambio, resulta muy complicado cambiar los requisitos o el diseño
+ No sabemos si lo que estamos construyendo funcionara, sino unicamente al final del proceso
+ No existen entregas inmediatas lo que dificulta el feedback. Desarrollo de meses y al final se testea y despliega

## XP - Extreme Programming
+ Kent Beck (1996)
+ **XP stands for**: takes "[best practices](https://en.wikipedia.org/wiki/Best_practices "Best practices")" to extreme levels.
+ advocates frequent [releases](https://en.wikipedia.org/wiki/Software_release_life_cycle "Software release life cycle") in short development cycles
**Other elements of XP**
+ pair programming
+ unit test (**TDD**)
+ not programming features util they are actually needed (YAGNI)
+ flat management structure
+ expecting changes in the customer's requirements as time passes and the problem is better understood, and frequent communication with the customer and among programmers
### TDD
+ offers more than just simple validation of correctness, but can also drive the design of a program.
+ TDD can lead to more modularized, flexible, and extensible code