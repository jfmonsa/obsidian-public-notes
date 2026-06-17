---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

# Inversion-of-Control (IoC) - Design Principle

> Discourages a Developer from creating the object and dependencies his program needs to run directly. Rather he outsources it to a ==framework or an external entity==. Inversion of control (IoC) is where control is inverted, rather than the programmer controls the flow of the program, the framework takes control instead.

+ If you have a component that does something, as soon as it’s also responsible for creating its dependencies… it’s doing multiple things.
+ With this Design Principle. we just know what interfaces/APIs we want to code against, but someone else can give us the implementation of those.
---
+ the flow depends on the object graph that is built up during program execution.
+ Framework or external entity calls your custom code

+ Is the base for the following patterns
	+ Envent Handling (Event-driven programming)
	+ Dependency Injection Pattern
	+ Factory Pattern
	+ Template Method
	+ Strategy Pattern
	+ Service Locator

## Types
1. **Type 1 (Principio Holywood)**: the system will call the dependent objects when it needs them, rather than the dependent objects calling the system when they need something. ==No llames, nosotros te llamamos==
2. **Type 2**: also called "template method" pattern, defines the skeleton of an algorithm in a base class, and allows derived classes to fill in specific details.
## Pros
- Your code gets decoupled so you can easily exchange implementations of an interface with alternative implementations
- It is a strong motivator for coding against interfaces instead of implementations
- **Reducing code complexity**: Consider the amount of duplicated code for having many separate locations create their dependencies…
- **Making code more testable**: This is because we can alter the concrete implementations of the dependencies of the system we’re testing.
- **Improving code maintainability**: This is because we can make changes to a dependency without having to potentially break open another class (i.e. just pass in a different implementation if needed)
## Cons
> IoC is not without challenges. One notable disadvantage is that while IoC can be beneficial in large applications, it may add unnecessary complexity to smaller projects.

# Resources
+ https://es.wikipedia.org/wiki/Inversi%C3%B3n_de_control
