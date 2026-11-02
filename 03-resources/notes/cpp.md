---
mocs:
  - "[[programming-languages.moc|Languages]]"
tags:
  - lang/cpp
---

+ Created in 1979 by Bjarne Stroustrup extending C
+ Multi-paradigm: Functional, structured and OOP
+ Compiled

# Intro
## 1 Hello World
1. ***`include`***: Using I/O stream from the c++ standard library
2. ***`std::cout << "Hello, world!" << std::endl;`***:  input output with the standard library, `<<`  is an operator which receives 3 params; `::` **scope operator** used to indicated that `cout` and `endl` are functions (manipulators) that belong to`std` namespace, so it establishes the scope which we are using 
4. ***`return 0`***: Indicate successful execution, any other value return error

```c++
#include <iostream>
//This is a comment

int main(){
std::cout << "Hello, world!" << std::endl;
return 0;
}
```

### Details
1. ***Types***: 
	+ define data structures and operations on those data structures
	+ there are 2 types of types: 1. **core language**, such as `int`; 2. defined outside core language such as `std:iostream`
1. ***Namespaces***: 
	+ mechanism for grouping related names.
	+ Names from the standard library are defined in the namespace called `std`.
1. ***Definitions and headers***:
	+ Every name used in a c++ program must have been defined. 
	+ The standard library defines its names in headers, which programs access through `#include`
### Compile
```sh
g++ -o hello hello.cpp
./hello
```

## 2 Input
+ `const` for constants
+ `+` concatenation and the concept that the operator is overloaded
+ `std::string spaces(greeting.size(), ' ');`
	+ `' ' ` : We enclosed a character literal within single quotes
	+ construct a string from an integer value and a char value, the result has as many copies of the char value as the value of the integer
```c++
#include <iostream>
#include <string>

int main()
{
   
	//...
    // build the message
    const std::string greeting = "Hello, " + name + "!";
    const std::string spaces(greeting.size(), ' ');
    const std::string second = "* " + spaces + " *";
    const std::string first(second.size(), '*');
	//...
}
```


```c++
std::string hello = "Hello"; // define the variable with an explicit initial value
std::string stars(100, '*'); // construct the variable
// according to its type and the given expressions
std::string name; 
```

## 3 - Counting and Looping
1. `string::size_type`: Data type used to stored length of strings
2. logical operators use short-circuit evaluation
3. compound-assignment: ` c += greeting.size();`
4. using-declaration: allow us to indicate that we are using `cout` from `std`
5. `x++`: Increments x , returning the original value of x
6. `++x`: Increments x , returning the incremented value of x
```c++
#include <iostream>
#include <string>
using std::cin;
using std::cout;
using std::endl;
using std::string;
int main()
{
    cout << "Please enter your first name: ";
    string name;
    cin >> name;

    // build the message
    const string greeting = "Hello, " + name + "!";
    // the number of rows and columns to write
    const int pad = 1;
    const int rows = pad * 2 + 3;
    const string::size_type cols = greeting.size() + pad * 2 + 2;
    // write a blank line to separate the output from the input
    cout << endl;
    
    // write rows rows of output
    for (int r = 0; r != rows; ++r)
    {
        string::size_type c = 0;
        // invariant: we have written c characters so far in the current row
        while (c != cols)
        {
            // is it time to write the greeting?
            if (r == pad + 1 && c == pad + 1)
            {
                cout << greeting;
                c += greeting.size();
            }
            else
            {
                // are we on the border?
                if (r == 0 || r == rows - 1 ||
                    c == 0 || c == cols - 1)
                    cout << "*";
                else
                    cout << " ";
            }
        }
        cout << endl;
    }
    return 0;
}
```


## OOP: Access modifiers
+ `public`: accessed from anywhere
+ `private`: only by function members of the class. They are not allowed to be accessed directly by any object or function outside the class
+ `protected`: accessed by any subclass (derived class) of that class as well. 
# Resources
## Accelerated C++
Se centra en explicar cosas a alto nivel e ignorar muchas cosas base del lenguaje y cosas base de C.

> We define abstraction as selective ignorance—concentrating on the ideas that are relevant to the task at hand, and ignoring everything else

**Chapters**
1. Hello world
2. Input
3. Counting and Looping