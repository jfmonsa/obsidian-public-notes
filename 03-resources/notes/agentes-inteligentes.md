---
mocs:
    - "[[public-notes/03-resources/ai.moc.md|Artificial Intelligence]]"
tags:
    - cs/ai
    - meta/lang/es
---

## Agentes Inteligentes
+ **Agente**: Biologico, Mecatronico o Sofware
	+ Percibe cosas de el ambiente
	+ En base a eso efectua acciones
+ Sistemas de control
> entidad capaz de percibir su entorno, procesar tales percepciones y responder o actuar en dicho entorno de manera [racional](https://es.wikipedia.org/wiki/Racionalidad "Racionalidad"), es decir, logrando objetivos, tendiendo a maximizar un resultado esperado

![[Pasted image 20240818205702.png]]

### Tipos de Agentes Inteligentes
+ Agente de reflejo simple
	+ Cada percepción se asocia con una acción (tabla de reglas)
+ Agente con modelo del entorno
	+ El agente crea un modelo del entorno
	+ Se basa en las percepciones y acciones previas
+ Agente basado en metas
	+ Se tiene dos nuevos elementos:
		+ **Meta**: Estado final deseado del sistema
		+ **Modelo del efecto**: (estado, acción) -> efecto
+ Agente basado en utilidad
	+ Se encarga de encontrar la solución óptima según el costo
	+ Se define un valor de utilidad para cada estado