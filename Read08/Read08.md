# Read: 08 - OO Design

**SOLID - First 5 Principles of Object Oriented Design**
* *SOLID* - acronym for the first five object-oriented design principles, and it stands for:
  - S - Single-responsiblity Principle - This principle states that a class should have one and only one reason to change, in other words a class should have only one job.
  - O - Open-closed Principle - This principle states that objects or entities should be open for extension but closed for modification. A class should be extendable without modifying the class itself.
  - L - Liskov Substitution Principle - This principle states that let q(x) be a property provable about objects of x of type T. Then q(y) should be provable for objects y of type S where S is a subtype of T. The meaning of this statement is that every subclass or derived class should be substitutable for their base or parent class.
  - I - Interface Segregation Principle - This principle states that a client should never be forced to implement an interface that it doesn’t use, or clients shouldn’t be forced to depend on methods they do not use.
  - D - Dependency Inversion Principle - This principle states that entities must depend on abstractions, not on concretions. It states that the high-level module must not depend on the low-level module, but they should depend on abstractions. Also this allows for decoupling. 


**SOLID principles in real life**
* S - single responsibility principle - class or module should have only one reason to change
  - Real life example - the "duck" vehicle are street legal and water-capable, and they only change from driving on land to going out on the water, and from being driven in the water to land.
* O - open/closed principle -  a class that does what it needs to flawlessly and does not need to be changed later, but can be extended.
  - Real life example - a smart phone that doesn't need to be changed itself, but you can add apps on the phone.
* L - liskov substitution principle - any child type of a parent type should be able to stand in for that parent 
  - Real life example - Cooking stew with various ingredients in the stew, while asking if the ingredients are edible or not.
* I - interface segregation principle - don't want to force clients to depend on things they don't actually need
  - Real life example - The soup of the day on a menu at a restuarant. The reason why it only says soup of the day is because it changes everyday.
* D - dependency inversion - depends upon abstractions rather than upon concrete details
  - Real life example - Using a credit card to pay groceries with, and the clerk swiping your credit card with a visa machine.