---
mocs:
    - "[[public-notes/03-resources/languages.moc.md|Languages]]"
tags:
    - lang/java
---

+ Strongly-typed language
+ Dynamic binding?
+ A real Java application is nothing but objects talking to other objects
+ Java is pass by value? (creates a copy)

 **Table Of Contents: (p. 86 - 120)**
 
- [[#1. How Java Works?|1. How Java Works?]]
- [[#2. First App: main method, compile & run|2. First App: main method, compile & run]]
- [[#3. Variables: Primitive & Reference|3. Variables: Primitive & Reference]]
	- [[#3. Variables: Primitive & Reference#1. Primitive (lowercase)|1. Primitive (lowercase)]]
	- [[#3. Variables: Primitive & Reference#2. Hold References to Objects|2. Hold References to Objects]]
- [[#4. Arrays & ArrayList|4. Arrays & ArrayList]]
- [[#5. Encapsulation: Getters and Setters:|5. Encapsulation: Getters and Setters:]]
- [[#6. Comparing Variables: primitives & Reference|6. Comparing Variables: primitives & Reference]]
- [[#7. Garbage Collector|7. Garbage Collector]]
- [[#8. Inheritance|8. Inheritance]]
- [[#9. Process to design Java program (logic oop)|9. Process to design Java program (logic oop)]]
- [[#10. Java API (Java Library), import|10. Java API (Java Library), import]]
- [[#11. Polymorphism (Method Overriding) & method Overriding|11. Polymorphism (Method Overriding) & method Overriding]]
	- [[#11. Polymorphism (Method Overriding) & method Overriding#1. Method overriding|1. Method overriding]]
		- [[#1. Method overriding#Super keyword|Super keyword]]
	- [[#11. Polymorphism (Method Overriding) & method Overriding#2. Method overloading|2. Method overloading]]
- [[#12. Serious Polymorphism: Abstract classes and interfaces|12. Serious Polymorphism: Abstract classes and interfaces]]
	- [[#12. Serious Polymorphism: Abstract classes and interfaces#1. Abstract Class|1. Abstract Class]]
	- [[#12. Serious Polymorphism: Abstract classes and interfaces#2. Abstract methods|2. Abstract methods]]
	- [[#12. Serious Polymorphism: Abstract classes and interfaces#3. Interfaces|3. Interfaces]]
- [[#n. Syntax Mix|n. Syntax Mix]]

## 1. How Java Works?
![[assets/Pasted image 20240625122839.png]]
1. Write one application and run it anywhere
2. Write your java program -> Compile it (javac)
3. The compiler creates a new document coded into Java ***Bytecode*** (.class files)
4. The Java Virtual Machine will interpret it

## 2. First App: main method, compile & run

+ A main method for each application (psvm snippet)
```java
public class MyFirstApp{
	public static void main (String[] args){
	//code here
	}
	//Other clases go here
}
```

```bash
# Save it: as MyFirstApp.java
# Compile
javac MyFirstApp.java
# Run
java MyFirstApp
```


## 3. Variables: Primitive & Reference
+ Variable declaration and initialization
### 1. Primitive (lowercase)
```java
int x;
x = 231;
byte b = 89;
char c = 'f';
```
+ boolean
+ Char
+ ***Numeric***: byte, short, int, long
+ ***floating point***: float, double
### 2. Hold References to Objects
```java
Dog d = new Dog();
d.bark();

Book b = new Book();
Book c = new Book();
```

What you store in a Reference variable is a **Reference** not a the object itself. Example:
```java
Book b = new Book();
Book c = new Book();
```
1. Ex: 2 objects, 2 references
![[assets/Pasted image 20240625162626.png]]
2. Ex: 3 References, 2 objects. Note: 2 variables (c and d) refers to the same object
```java
Book d = c;
```
![[assets/Pasted image 20240625162901.png]]
3. Ex: Changing the reference: (c and b) refers to the same object
```java
c = b;
```
![[assets/Pasted image 20240625163146.png]]
## 4. Arrays & ArrayList
+ Arrays are objects too
```java
import java.util.ArrayList;

int[] nums
nums = new int[7]

String[] names = {"John", "Mary", "David", "Sarah"};

ArrayList<Egg> myList = new ArrayList<Egg>();
Egg s = new Egg();
myList.add(s);
```
## 5. Encapsulation: Getters and Setters: 
+ Getters and setters is the naming convention for ***accessors and mutators*** in java
+ Are accesors and mutators for instance variables
+ By forcing everybody to call a setter method, we can protect the cat from unacceptable size changes.
```java
public void setHeight(int ht) {
	if (ht > 9) {
		height = ht;
	}
}
```
+ Basic strategy: Mark instance variable ***private***, Mark getters and setters ***public***
## 6. Comparing Variables: primitives & Reference
+ `==`: Use`==` to compare two primitives or to see if two references refer to the same object
+ `equals()`:  Use `equals()` to check if two different objects are equal
## 7. Garbage Collector
+ Gestiona la memoria de manera automática
+ Elimina objectos que ya no son reverenciados
## 8. Inheritance

```java
class Vehicle {
  protected String brand = "Ford";         // Vehicle attribute
  public void honk() {                     // Vehicle method
    System.out.println("Tuut, tuut!");
  }
}

class Car extends Vehicle {
  private String modelName = "Mustang";    // Car attribute
  public static void main(String[] args) {

    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (from the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand attribute (from the Vehicle class) and the value of the modelName from the Car class
    System.out.println(myCar.brand + " " + myCar.modelName);
  }
}
```

## 9. Process to design Java program (logic oop)
1. Figure out what the class is suposed to do
2. List the instance variables and methods
3. write prepcode (pseudocodigo)
4. write testcode for the methods (Extreme Programming - XP technique)
5. implement the class
6. test de methods
7. debung
## 10. Java API (Java Library), import
+ Pre-built classes ready to use (e.g. ArrayList)
+ In the Java API, classes are grouped into packages, Every class in the Java library belongs to a package: `javax.swing`, `java.util`
+ `System.out.println()`, `String`, `Math` all belong to `java.lang` package
+ importing: `java.util.ArrayList` <- `packageName.className`
+ When you import you don’t have to worry about your code becoming bloated, or slower, from too many imports. An import is simply the way you give Java the full name of a class.
+ **Package**: Is a **namespace** for organizing classes and interfaces in a logical manner

## 11. Polymorphism (Method Overriding) & method Overriding
### 1. Method overriding
We override methods when a subclass has a different behavior from its super class, we use the decorator `@Override`
+ the method must return the same type
+ the access modifier of the method should be equal of its super class
+ You cannot override a method marked as `final`
```java
	@Override
	public void hunt() {
		System.out.println("*The fish is hunting*");
```
#### Super keyword
+ Used to extent the functionality of a Class instead of overwriting it
```java
public void roam() {
super.roam();
// my own roam stuff
}
```
### 2. Method overloading
+ Method overloading its different from polymorphism
+ method overloading is having two methods with the same name but different argument list
+ You can’t change ONLY the return type.

## 12. Serious Polymorphism: Abstract classes and interfaces
![[Pasted image 20240629230405.png]]
+ Some classes should not be instantiated
### 1. Abstract Class
+ A class that cannot be instantiated
+ An abstract class has virtually* no use, no value, no purpose in life, unless it is extended
+ Tip: Every class of java extends the class Object, this can be use to implement a method that takes as input Any type, Any class that doesn’t explicitly extend another class, implicitly extends Object.
```java
abstract class Canine extends Animal {
	public void roam() { }
}
```
![[Pasted image 20240629232747.png]]
### 2. Abstract methods
+ an abstract method means the method must be overridden. 
+ If you declare an abstract method, you MUST mark the class abstract as well. 
+ An abstract class can have both abstract and non-abstract methods
```java
public abstract void eat();
```
### 3. Interfaces
+ A 100% abstract class
## n. Syntax Mix

```java
//print in new line -> sout
System.out.println(i)
//print in the same line
System.out.print(x)

//casting Reference vars
Integer.parseInt("3");

// Random number between 0 and 4.999 and casting primitives (float to int)
int randomNum = (int) (Math.random() * 5)

// enhanced for loop
for (int elm : array){} // el arrray puede ser cualquier iterable

//Short circuit operators && ||
//Non short circuit operators & |
```