---
mocs:
    - "[[public-notes/03-resources/patterns.moc.md|Design Patterns & Principles]]"
tags:
    - dev/patterns
    - dev/practices
---


## Intro
+ Robert C. Martin
+ Architecture is Important but details are important too
	+ ==Clean Code == attentiveness to detail==
+ Focus on maintenance rather than Production
+ 5S, Lean, an agile
	+ 5S (Japanese manufacturing method):
		+ **Seiri (Sort)**: Knowing where things are (suitable naming)
		+ **Seiton (Systematize)**: A piece of code should be where you expect to find it. and if not you should refactor to get it there
		+ **Seiso (shine)**: keep workple free of waste, grease, scrap, haging wires:get rid of bad comments
		+ **Seiketsu (Standarization)**: The group agrees about how to keep the workplace clean ==Consistent coding style==
		+ **Shutsuke (discipline)**: discipline to follow the practices

> We’ve all said we’d go back and clean it up later. Of course, in those days we didn’t know LeBlanc’s law: _Later equals never_

> we want the reading of code to be easy, even if it makes the writing harder (when talking 10:1 ratio between reading vs writing code)

**Boy Scout Rule**
> leave the campground cleaner than you found it

## Chapter 2: Naming
+ Good names revel intent
+ Good Name should tell you why it exists, what it does, and how it is used
+ hide magic: numbers, strings
+ consistent naming
+ avoid similar naming for things that do different things
+ Avoid Abbreviate Names
> single-letter names can ONLY be used as local variables inside short methods. _The length of a name should correspond to the size of its scope_.
+ Avoid Prefixes
+ Methods:
	+ Methods should have verb or verb phrase in their names
	+ Accessors, mutators, and predicatives should be named for their value prefixed with `get`, `set`, and `is`
+ keep consistent lexicon (one word, per concept). e.g don't have: fetch, get and retrieve to express the same
+ When is appropriate prefer technical names rather than domain names (your co-workers are programmers too)

## Chapter 3: Functions
+ Should be Small
+ indent level should be less than one or two (==guard clauses)
+ A function should contain only statements at the same level of abstraction (**One level Of abstraction Per function**)
	+ So we make sure functions do one thing
	+ Mixing levels of abstraction within a function is always confusing, Readers may not be able to tell wether a particular expression is an essential concept or a detail
+ **Stepdown Rule** We want the code to read like a top-down narrative. We want every function to be followed by those at the next level of abstraction
+ Short number of arguments (max. three) (larger number of arguments require very special justification) -> more testable code (test combination of arguments)
+ don't use output arguments, instead use `returns` -> **Avoid Side-effects**
+ avoid flag arguments

+ Reducing the number of arguments by creating objects ==Value Object Pattern )
```Java
 Circle makeCircle(double x, double y, double radius);  
 Circle makeCircle(Point center, double radius); //Cleaner
```

**Argument lists are valid**
```Java
String.format(”%s worked %.2f hours.”, name, hours);
public string format(String format, Object... args);
```

**Side Effects Are lies, avoid them**:
```Java
public class UserValidator {  
     private Cryptographer cryptographer;  
  
     public boolean checkPassword(String userName, String password) {  
       User user = UserGateway.findByName(userName);  
       if (user != User.NULL) {  
         String codedPhrase = user.  
         getPhraseEncodedByPassword();  
         String phrase = cryptographer.decrypt(codedPhrase, password);  
         if ("Valid Password".equals(phrase)) {  
           Session.initialize();  
           return true;  
         }  
       }  
       return false;  
     }  
   }
```
+ The side effect is calling `Session.initializer()` it wasn't expected to happend due to the method name `checkPassword`
+ **Separe Command from Queries**:
	+ Functions should answer something  or do something not both
	+ It should change the state of a and object or ir should return some information about
+ Prefer exceptions to returning, returning error values tends to deeply nested code
+ Extract try / catch blocks
```java
public void delete(Page page) {  
     try {  
       deletePageAndAllReferences(page);  
     }  
     catch (Exception e) {  
       logError(e);  
     }  
   }
```

### How To Write Good Functions
When I write functions, they come out long and complicated. They have lots of indenting and nested loops. They have long argument lists. The names are arbitrary, and there is duplicated code. But I also have a suite of unit tests that cover every one of those clumsy lines of code.

So then I massage and refine that code, splitting out functions, changing names, eliminating duplication. I shrink the methods and reorder them. Sometimes I break out whole classes, all the while keeping the tests passing.

## Chapter 4: Comments
+ A necessary evil
+ Comments lie
+ Prefer clear and expressive code with few comments
### Good Comments
+ **Legal Comments**:
	+ Copyright, authorship, license
+ Comment complex methods that are not self explanatory
+ Sometimes you need to explain some decisions implemented in the code
+ When you apply crazy optimizations
+ javadocs / jsdocs / docstrings in public APIs (But they can lie too)
+ Mandate comments clutter the code, mandate javadoc for every function, only obfuscate

## Chapter 5: Formatting
+ Concepts that are closely related should be kept vertically close to each other
+ instance vars at the top of the class, functions vars close where they're use or at the top of the scope
+ **Dependent Functions.** If one function calls another, they should be vertically close
+ caller should be above the callee
+ Agree on team rules and stuck with them

## Chapter 6: Objects and Data Structures
### Data Abstractions
+ Why getters and setters?
	+ > Hiding implementation is not just a matter of putting a layer of functions between the variables. Hiding implementation is about abstractions
	+ > A class does not simply push its variables out through getters and setters. Rather it exposes abstract interfaces that allow its users to manipulate the _essence_ of the data, without having to know its implementation.

**Difference between Data Structures and Objects**
> the difference between objects and data structures. Objects hide their data behind abstractions and expose functions that operate on that data. Data structure expose their data and have no meaningful functions.

### Law of Demeter
+ (**LoD**) or **principle of least knowledge**
+ It suggests that a given object should have limited knowledge of other objects.
+ promoting loose coupling and enhancing modularity.
+ The main idea is that an object should only communicate with its immediate "friends" and not with distant "strangers."

- **An object should only invoke methods of:**
    - Itself
    - Its direct member objects
    - Objects passed as arguments to its methods
    - Objects it creates or instantiates within its methods
    - Its direct components
+ law can be stated simply as "use only one dot"
+ `a.m().n()` breaks the law where `a.m()` does not.
+ when one wants a dog to walk, one does not command the dog's legs to walk directly; instead, one commands the dog which then commands its own legs.
---
+ When dealing with "pure data structures" law of Demeter doesn't applies:
	+ `car.owner.address.street;` `// Using direct access to fields` (dont violate LoD)
	+ `car.getOwner().getAddress().getStreet();` violates LoD
+ avoid setters and getters for pure Data Structures

Objects expose behavior and hide data. This makes it easy to add new kinds of objects without changing existing behaviors. It also makes it hard to add new behaviors to existing objects. Data structures expose data and have no significant behavior. This makes it easy to add new behaviors to existing data structures but makes it hard to add new data structures to existing functions.

In any given system we will sometimes want the flexibility to add new data types, and so we prefer objects for that part of the system. Other times we will want the flexibility to add new behaviors, and so in that part of the system we prefer data types and procedures. Good software developers understand these issues without prejudice and choose the approach that is best for the job at hand.

---
**Resources**
+ Good article https://javadevguy.wordpress.com/2017/05/14/the-genius-of-the-law-of-demeter/

## Chapter 7: Error Handling
+ pag 317 example of "Extract try / catch" blocks
+ Wrap third party APIs exceptions so you can throw your own exceptions and define a handler above your code.
	+ Separating between bussiness logic and error handling
	+ More scalability and ease of testing
+ Special Case Object ?
+ avoid null returns when possible (example i you don'f find a list of somthing return empty list not null)
+ avoid at all passing null to functions

## Chapter 8: Boundaries
+ integrating external libs to our systems
+ learning tests: write test for external apis
	+ learning tests verify that third-party packages we are using work the way we expect them to even in new releases
+ Using code that does not exits (Adapter)
	+ Good software designs accommodate change without huge investments and rework