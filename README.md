# SOLID
## Single Responsibility Principle
- There should never be more than one reason for a class to change

> A class prodivides a single functionality and addresses a specific concern.

Example: A class sending messages to a server. What are possible reasons to change this class?
Protocol may change, message format can change etc. This is what we avoid.
<br>
If you have more than one responsibility in the class, you need to separate them.

## Open Closed Principle
- Software entities (classes, methods etc.) should be open for extension, but closed for modification.

## Liskov Substitution Principle
- Child class object shouldn't alter the behavior/characteristics of a base class.
Overriding doesn't violate this rule. Because think that you have a print method in base class.
If child class overrides it then it prints another thing. But the behavior is the same.<br>
Most popular example is extending square from rectangle. Because of squre width and height is equal, 
if we use rectangle as a base class when we set square width and height each time we fail.<br>
That's why this relation is not proper in OOP. We create shape class as base.

## Interface Segregation Principle
Clients shouldn't be forced to depend upon interfaces that they don't use.<br>
This is related with interface pollution which is about we shouldn't create large interfaces that
contains unrelated methods.
<br>
Signs of Interface Pollution
- Classes have empty method implementation
- Method implementations throw UnsupportedOperationException or similar
- Method implementations return null or default values

We should avoid that.<br>
Write highly cohesive interfaces.

## Dependency Inversion Principle
- High level modules should not depend upon low level modules. Both should depend upon abstractions
- Abstractions should not depend upon details. Details should depend upon abstractions.

Low level modules mean that provides functionality that can be used anywhere for ex, writing disk, accept json<br>
High level module means that the functionality that we implement, our business logic.
<p>
When we instantiate objects, we tightly coupled to particular implementations.<br>
Think about you are creating a formatter which uses xml. Then in someplace you need to replace it with
json formatter. In this case we create tightly coupled code. So instead of depend on concrete classes,
we need to depend on abstractions. 
<br>
Instead of instantiating of dependencies, let somebody injects it.
We are not creating instance of dependencies, somebody creates it and gives us.

# Behavioral Patterns
Its about how objects interact with each other.

## Observer Pattern
Used for one many relations. 

### Concepts
* One to many
* Decoupled
* Event handling
* Pub / Sub
* Examples: java.util.Observer, java.util.EventListener

### Design
* Subjects
* Observer
* Observable

### UML
![alt text](images/observer/1.PNG)

### Pitfalls
* Unexpected updates
* Large sized consequences
* Debugging difficult

### Contrast
| Observer   | Mediator  |
|---|---|
| One to many | one to one to many  |
| Decoupled | Decoupled  |
| Broadcast communication  | Complex communication  |

### Summary
* Decoupled communication
* Built in functionality
* Used with mediator

## State Pattern
Used when we need to represent a state in application

### Concepts
* Localize state behavior
* State object
* Separates what from where
* Open Closed Principle
* Examples: none , there is no a good example in java core api. some people says that iterator is a state pattern.

### Design
* Abstract class / interface
* Class based

### UML
![alt text](images/state/1.PNG)

### Pitfalls
* Simplifies cyclomatic complexity
* Adding additional states made easier
* More classes 
* Similar implementation to strategy

### Contrast
| Strategy   | State  |
|---|---|
| Interface based | Interface based  |
| Algorithms are independent  | Transitions  |
| Class per algorithm  | Class per state  |

### Summary
* Externalizes algorithms
* Client know different strategies
* Class per strategy
* Reduces conditional statements

## Stragety Pattern
Used when you enable the strategy or algorithm to be selected at runtime.

### Concepts
* Eliminate conditional statements
* Behavior encapsulated in classes
* Difficult to add new strategies
* Client aware of strategies
* Client chooses strategy
* Examples: Comparator => it enables client to choose proper stragety for its usage

### Design
![alt text](images/strategy/1.PNG)

### UML
![alt text](images/strategy/2.PNG)

### Pitfalls
* Client aware of strategies
* Increases number of classses

### Contrast
| Strategy   | State  |
|---|---|
| Interface based | Interface based  |
| Algorithms are independent  | Transitions  |
| Class per algorithm  | Class per state  |

### Summary
* Externalizes algorithms
* Client know different strategies
* Class per strategy
* Reduces conditional statements


# Structural Patterns
* Its about how you use or utilize objects.
* It could be something like performance or refactoring or memory utilization.

Structural Patterns are:
- Adapter
- Bridge
- Composite
- Decorator
- Facade
- Flyweight
- Proxy

## Adapter Pattern
Its a great pattern for connecting new code legacy code without having to change
the working contract that was produced from the legacy code originally.

### Concepts
* Convert interface into another interface
* Legacy
* Examples: Arrays to Lists

### Design
![alt text](images/adapter/1.PNG)

### Example
![alt text](images/adapter/2.PNG)

### Pitfalls
* Not a lot 
* Multiple adapters
* Do not add functionality consider using decorator patterns instead.

### Contrast
| Adapter   | Bridge  |
|---|---|
| Works after code is designed | Designed upfront  |
| Legacy  | Abstraction and implementation vary  |
| Retrofitted  | Built in advance  |
| Provides different interface  | Both adapt multiple systems   |

### Summary
* Simple solution
* Easy to implement
* Integrate with legacy
* Can provide multiple adapters

## Bridge Pattern
Very similar to Adapter pattern. Tha main difference is that bridge works with new code, whereas the adapter works with
legacy code.

### Concepts
* It decouples abstraction and implementation
* To do this use Encapsulation, composition, inheritance
* Changes in abstraction wont affect the client
* Details may not be right
* If you aren't quite sure of what the end product of what you're building will be, the bridge is great
for giving us flexibility without breaking things with change
* Examples => Driver, JDBC

### UML
![alt text](images/bridge/1.PNG)

### Example
![alt text](images/bridge/2.PNG)

### Pitfalls
* Increases complexity
* Conceptually difficult to plan

## Facade Pattern
Very similar to Adapter pattern. Tha main difference is that bridge works with new code, whereas the adapter works with
legacy code.

### Concepts
* Make an API easier to use
* Reduce dependencies on outside code
* Simplify the interface or client usage
* Usually a refactoring pattern
* Examples: java.net.URL

### UML
![alt text](images/facade/1.PNG)


### Pitfalls
* Typically used to clean up code
* Should think about API design

### Contrast
| Facade   | Adapter  |
|---|---|
| Simplifies interface | Also a refactoring pattern  |
| Works with composites  | Modifies behavior  |
| Cleaner API  | Provides a different interface |

## Flyweight Pattern
Is a pattern that minimizes memory used by sharing data with similarly type objects.

### Concepts
* More efficient use of memory
* Large number of similar objects
* Immutable
* Most of the object states can be extrinsic
* Examples: java.lang.String and all other wrapper classes

### Design
* Patterns of patterns
* Utilizes a factory
* Encompasses creation and structure

### UML
![alt text](images/flyweight/1.PNG)


### Pitfalls
* Complex pattern
* Must understand factory

### Contrast
| Flyweight   | Facade  |
|---|---|
| Memory optimization | Refactoring pattern  |
| Optimization pattern  | Simplified client  |
| Immutable objects  | Provides a different interface |

## Flyweight Pattern
Is a pattern that acts as a interface to something else

### Concepts
* Interface by wrapping
* Can add functionality
* Security, simplicity, remote
* Proxy called to access real object
* Examples: java.lang.reflect.Proxy, java.rmi.*

### UML
![alt text](images/proxy/1.PNG)


### Pitfalls
* Complex pattern
* Must understand factory

### Contrast
| Flyweight   | Facade  |
|---|---|
| Memory optimization | Refactoring pattern  |
| Optimization pattern  | Simplified client  |
| Immutable objects  | Provides a different interface |