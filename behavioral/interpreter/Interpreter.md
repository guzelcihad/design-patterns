### Concepts
* Represent grammar
* Interpret sentence
* Map a domain
```
java.util.Pattern
javax.text.Format
```

### Design
* Object per command
* Command Interface
* Execute method
* Unexecute Method
* The best used implementation uses Reflection

### Uml
![alt text](D:\Repositories\DesignPatterns\src\main\resources\images\3.PNG)

### Pitfalls
* Complexity
* Class per rule

### Contrast
Interpreter
> Access to properties
> Functions as methods

Visitor
> Needs observer functionality
> Functionality found in one place
