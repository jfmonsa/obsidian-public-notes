---
mocs:
    - "[[public-notes/03-resources/foundations.moc.md|Foundations]]"
tags:
    - cs/foundations
---

Programming paradigm based on ***Objects*** which can contain ***Data*** (Fields) and ***Code*** (Procedures a.k.a methods, messages, member functions)

## Main concepts 
1. ***Class*** -> ***Object***: (Metodos y propiedades)
2. Difference between Class variables and methods vs Instance ones. (static java)
3. Open recursion: Object methods can call other object methods or properties of themselves: ***this*** & ***self***
### 2. Object & Class
+ Class is the blueprint for an object
+ Each object is required to be an ***Instance*** of a particular class
+ Objects are created by calling a special type of method in the class known as a ***Constructor***.
+ Objects are the run-time entities in an object-oriented system
+ Data structure or Abstract Data Type (ADT) containing fields (***State*** variables a.k.a members, attributes, or properties) and methods
+ Objects can contain other objects in their instance variables (known as **Object Composition**
	+ **Inheritance vs Composition** use Is-a or Has-a thinking
+  A method call is also known as ***Message passing***

### 3. Difference between Class vars and methods and Instance ones. (static)

Static in java? ***Procedures and variables can be specific to either the class or the instance***

+ ***Class variables and Methods***: belong to the _class as a whole_; there is only one copy of each variable & methods (have access to only class variables), shared across all instances of the class
+ ***Instance variables or attributes:*** data that belongs to individual _objects_ & and methods (have access to instance variables for the specific object they are called on, inputs, and class variables); every object has its own copy of each one

## 4. The Core of OOP (4 Principles)
1.  Inheritance
2. Abstraction
3. Encapsulation
4. Polymorphism

### 1. Data Abstracción
+ Data abstraction is the concept of exposing only the essential features of an object while hiding the complex implementation details.
+ It allows the programmer to focus on what an object does instead of how it does it.
Consider a Car class. When you interact with a car, you don't need to know how the engine works internally to drive it. You just need to know the essential features like starting the car, accelerating, and braking.

```java
public abstract class Car {
    // Abstract methods
    public abstract void start();
    public abstract void accelerate();
    public abstract void brake();
}
```
### 2. Inheritance
+ Code reuse and extensibility
+ **super** keyword to access parent class constructor or method
+ **Abstract classes** cannot be instantiated into objects [when to use Abstract class over Interface?](https://www.java67.com/2017/08/difference-between-abstract-class-and-interface-in-java8.html) they're merely represent a template (using **extends** keyword)
+ **Interface**  (using **implements** keyword), interfaces can inherit other interfaces and abstract classes
+ You also need to learn to make a trade-off,  like _[Why Composition is better than Inheritance](https://javarevisited.blogspot.com/2013/06/why-favor-composition-over-inheritance-java-oops-design.html)_
### 3. Encapsulation (access modifiers)
+ Involves bundling data and methods together and restricting access to the inner workings of the object to protect its state and promote modular design.
+ access restrictions to internal data: `private`, `protected` & `public` (in java) or by convention (underscore prefix in Python)
### 4. Polymorphism
+ occurs when a child class modifies or reshapes the inherited properties or methods
+ Enables separation of concerns
+ two ways to achieving polymorphism: **Method Overriding** and **Method Overloading**
#### Method Overriding
Method overriding allows us to redefine a method from the superclass within the child class.

#### Method Overloading
Defining the same method with different number of parameters or different type
## Other 
+ [between relational databases and object oriented paradigm there is a general need to bridge the two worlds](https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch)
+ SOLID Principles and GRASP guidelines