---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

# Dependency Injection (DI)
+ Is a more specific version of ==IoC Pattern==
+ It Means: Giving an object its instance variables
+ allow components to receive their dependencies from an external source rather than creating them internally
+ **Dependencies:** Are objects which specific class depends on
## ¿What Solves this pattern?
+ **Problem** Solves around a simple principle: **inverting the control of dependency creation**. Traditionally, components within an application would directly create the dependencies they rely on. This approach, however, leads to tight coupling between components and hinders modularity and testability.
+ **Soluction** Instead of creating dependencies themselves, components rely on an external source to provide them. This external source can be a simple function argument, an object literal, or a dedicated dependency injection container. By receiving their dependencies through injection, components become loosely coupled and more independent.
## Pros

+ ==We create abstraction, which means we control what version or which implementation we pass as dependencies==
+ Loose coupling between components and Modularity
+ modular, testable, and maintainable codebase
+ You can easily replace components without affecting others. (ease of refactor)

## ¿How?
+ Constructor Injection
+ Setter Injection
+ Method Injection
+ Function Injection (DI is no exclusive to OOP)
+ Object Literal Injection
+ Dependency Injection Containers

## Examples
If you have a computer: its CPU, HDD, Memory, and Graphics cards are its dependencies

![[Pasted image 20240830171738.png]]

## Constructor Injection
+ We pass the objects in the constructor
+ Allow us to give each computer instance different components
```java
class Computer(
	private val processor: Processor,
	private val ram: RAM,
	private val hardDrive: HardDrive,
	private val graphicsCard: GraphicsCard
){
// implementation
}
```

## DI Container / Resolver
+ abstract away the complexities of manual dependency management
+ Should be use always when you have a large code base and you want to use DI
+ e.g: @Module the nestjs, include InversifyJS, Awilix, and TypeDI
### Example from scratch
```js
class DependencyContainer {
    constructor() {
        this.dependencies = {};
    }

    // Method to register dependencies with the container
    register(name, dependency) {
        this.dependencies[name] = dependency;
    }

    // Method to resolve dependencies by name
    resolve(name) {
        if (!(name in this.dependencies)) {
            throw new Error(`Dependency '${name}' not registered.`);
        }

        return this.dependencies[name];
    }
}

// Usage:

// Create an instance of the dependency container
const container = new DependencyContainer();

// Register dependencies with the container
container.register('logger', new Logger());
container.register('userService', new UserService());

// Resolve and use dependencies
const logger = container.resolve('logger');
const userService = container.resolve('userService');
```
## Use Cases
1. To create transactions, passing db object as a dependency injection

# Resources
+ https://dev.to/abuhasib/software-design-principle-inversion-of-controlioc-and-dependency-injection-5e5l
+ https://youtu.be/0hflBUXpkx8?si=JVTJ24lurfxI55ny # Dependency Injection Part 2: The Container and advatages of testing
+ https://youtu.be/TxxdqfhMUnI?si=C2BMCwrWNplNByqW - (==Mega Recomendada esta serie de 4 videos de +-10min)==  # Dependency Injection in Node with awilix #1