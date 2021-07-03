# Read: 06 - Inheritance and Interfaces

**Object-Oriented Programming Concepts**

* What is inheritance?
  - *Inheritance* - different kinds of objects having a certain amount in common with each other, but also defines additional features that make them different
  - Object-oriented programming allows classes to inherit commonly used state and behavior from other classes.
  - Each class is allowed to have one direct superclass, and each superclass can have subclasses.
  - Syntax for creating a subclass: 
    * first put the extends keyword at the beginning of the class declaration,and then put the name of the class to inherit from

* What is an interface?
  - *Interface* - methods form the object's interface with the outside world. An interface allows a class to become more formal about the behavior it promises to provide, and it forms a contract between the class and the outside world.  

* What is a package?
  - *Package* - a namespace that organizes a set of related classes and interfaces, and acts like a folder you keep files in
  - Application Programming Interface (API) - library that contains a set of packages, and these packages represent the tasks most commonly associated with general-purpose programming
    *  String object - contains state and behavior for character strings
    * File object - create, delete, inspect, compare, or modify a file on the filesystem
    *  Socket object - allows for the creation and use of network sockets
    * GUI objects - control buttons and checkboxes and anything else related to graphical user interfaces



**Interfaces and Inheritance**
* *Interfaces* - are contracts that spell out how the software will interact
  - Java's interface is a reference type that contain only constants, method signatures, default methods, static methods, and nested types.
  - APIs are common in commercial software products.
* *Inheritance* - classes can be derived from other classes, which means that they inherit fields and methods from those classes 
  - *Subclass* -  a class that is derived from another class
    * Subclass inherits all of the public and protected members of its parent, inherits the package-private members of the parent, and can use the inherited members as is, replace them, hide them, or supplement them with new members. Subclass doesn't inherit the private members of its parent class. 
  - *Superclass* - class from which the subclass is derived
    * Superclass has public or protected methods for accessing its private fields, which can be used by the subclass.
  - Object class - defines and implements behavior common to all classes, and defined in the java.lang package. 
  - Object is the most general of all classes and at the top of the heirarchy. The classes at the bottom have a more specialized behavior.
  - Casting objects - casting shows the use of an object of one type in place of another type, among the objects permitted by inheritance and implementations
