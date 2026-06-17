---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
---

# Factory Method Pattern
+ Provides an interface for creating objects in a superclass (base class) but allow subclasses to alter the type of objects that will be created
+ the subclasses are the ones that actually define how those objects are instantiated
+ a.k.a. as virtual constructor
+ Use with inheritance from subclasses to superclass (**Is a relation**)
## When To use
+ You don't know the exact type of object at compiled time
+ Clases muy similares en las cuales solo varia un poco la implementación de propiedades o metodos
+ your object creation process is complex or varies under different conditions, using a factory method can make your client code simpler and promote reusability.
+ Allows you to create objects through an interface or abstract class, hiding the details of concrete implementations. This reduces dependencies and makes it easier to modify or expand the system without affecting existing code.
+ - If your application needs to create different versions of a product or may introduce new types in the future,
## Components
+ **Creator**: This is an abstract class or an interface that declares the factory method. It may also contain other methods that work with the created objects.
+ **Concrete Creator**: Concrete Creator classes are subclasses of the Creator that implement the factory method to create specific types of objects. Each Concrete Creator is responsible for creating a particular product.
+ **Product**: This is the interface or abstract class for the objects that the factory method creates. The Product defines the common interface for all objects that the factory method can create.
+ **Concrete Product**: Concrete Product classes are the actual objects that the factory method creates. Each Concrete Product class implements the Product interface or extends the Product abstract class.

## Example 1
```ts
export default interface Computer {
  getName(): string;
  getColor(): string;
  getRam(): string;
  getCpu(): string
}


```
## Resources
+ https://youtu.be/phTXrJqRgnI?si=l7-k1eKoL68ZQ425 - Neetcode Factory Method Design Pattern 