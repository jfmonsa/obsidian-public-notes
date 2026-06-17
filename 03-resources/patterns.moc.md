---
mocs:
    - "[[public-notes/03-resources/software-development.moc.md|Software Development]]"
tags:
    - graph-view-markers/moc
---
# Design Patterns & Principles

+ **Coupling vs Cohesion** — tightly coupled components ripple changes; aim for low coupling, high cohesion
+ Basic principles: **KISS** (Keep It Simple), **YAGNI** (You Ain't Gonna Need It)

## Start here

### Principles
+ [[abstraction-principles-dry-wet-aha]] — DRY, WET, AHA
+ [[solid]] — the five SOLID principles
+ [[inversion-of-control-ioc]] — same idea as the Dependency Inversion principle

### Creational (object creation)
+ [[factory-pattern]]
+ Singleton, Builder *(pending)*

### Structural (assembling objects/classes)
+ [[data-transfer-object-dto]]
+ [[dao-data-access-object]]
+ [[repository-pattern]]
+ Facade, Decorator *(pending)*

### Behavioral (algorithms & responsibilities)
+ [[value-object-vo]]
+ Strategy, Observer, Template, Specification *(pending)*

### Other
+ [[bff-backend-for-frontend]]
+ [[dependency-injection-pattern]]
+ [[error-and-exception-handling]]

### Code good practices (idioms)
+ [[clean-code]] — summary of the Clean Code book

## Full index

```dataview
LIST FROM #dev/patterns AND -"templates"
SORT file.name ASC
```
