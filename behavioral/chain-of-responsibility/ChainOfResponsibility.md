### Concepts
* Decoupling of sender and receiver
* Receiver contains reference to next receiver
* Promotes loose coupling
* Examples
```
java.util.logging.Logger#log()
javax.servlet.Filter#doFilter()
Spring Security Filter Chain
```

### Design
* Chain of receiver objects
* Handler is interface based
* ConcreteHandler for each implementation

### Uml
![alt text](../images/1.PNG)

### Pitfalls
* Handling/Handler guarantee

### Contrast
Chain Of Responsibility
> Handler is unique
> Can utilize Command

Command
> Commands also unique
> Encapsulates function

They both similar