# Online Reading: 03 - Maps, primitives, File I/O

## [Primitives vs. Objects](https://www.baeldung.com/java-primitives-vs-objects) 

**Java Type System**
* Java has a two-fold type system consisting of primitives and reference type. Primitives correspond to a reference type.Every object contains a single value of the corresponding primitive type. 
  - Examples of primative: int, boolean
  - Examples of reference: Integer, Boolean
* Autoboxing - process of converting a primitive type to a reference type 
* Unboxing - opposite process of autoboxing
* Primitive type variables live in the stack and can be accessed fast. They have the following impact on the memory:
  - boolean – 1 bit
  - byte – 8 bits
  - short, char – 16 bits
  - int, float – 32 bits
  - long, double – 64 bits
* Reference types are objects that live in the heap and slow to access.
* Default values of the primitive types are 0 for numeric types, false for the boolean type, \u0000 for the char type, and null for the wrapper classes. 
  - Primitive types may acquire values only from their domains.
  - Reference types might acquire a value that doesn't belong to their domains.  

## [Exceptions in Java (read the first three sections on the left: What is an Exception, The Catch or Specify Requirement, Catching and Handling Exceptions)](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html)

**What is an Exception?**
* Exception - is an event that disrupts the normal flow of the program's instructions during the execution of a program. Exception short hand for exceptional event.
* Exception object - object contains information about the error
* Throwing an exception - creating an exception object and handing it to the runtime system
* Call stack - list of methods
* Exception handler - block of code that can handle and catch the exception

**The Catch or Specify Requirement**
* Catch or Specify Requirement - code that might throw certain exceptions must be enclosed by either a try statement that catches the exception or a method that specifies that it can throw the exception
* 3 kinds of execeptions 
 - Checked exception - are conditions that a well-written application should anticipate and recover from, and are subject to the Catch or Specify Requirement.
 - Error - are conditions that are external to the application, and that the application usually cannot anticipate or recover from, and are not subject to the Catch or Specify Requirement.
 - Runtime exception - are exceptional conditions that are internal to the application, and that the application usually cannot anticipate or recover from, and are not subject to the Catch or Specify Requirement.
 - Unchecked exceptions - errors and runtime exceptions 

**How to Throw Exceptions**
* Any code can throw an exception. 
*  Throwable class - All the classes are descendants of it, and all allow programs to differentiate among the various types of exceptions that can occur during the execution of a program.
* throw statement - Requires a single argument called a throwable object, which is a instance of any subclass of the Throwable class. 
* Subclasses - error class and execption class

## [Using Scanner to read in a file in Java](https://docs.oracle.com/javase/tutorial/essential/io/scanning.html)

**Scanning**
*  Scanner - an objects of type useful for breaking down formatted input into tokens and translating individual tokens according to their data type.
* Breaking Input into Tokens
  - a scanner uses white space to separate tokens
  - white space characters - blanks, tabs, and line terminators
* Translating Individual Tokens
  - Scanner supports tokens for all of the Java language's primitive types with the exception of char.
  - Numeric values can use thousands separators.