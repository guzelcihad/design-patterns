### Concepts
* Encapsulates request as an OBject
* Object oriented callback
* Decouple sender from processor
* Often used for undo functionality
```
java.lang.Runnable
javax.swing.Action
```

### Design
* Object per command
* Command Interface
* Execute method
* Unexecute Method
* The best used implementation uses Reflection

### Uml
![alt text](D:\Repositories\DesignPatterns\src\main\resources\images\2.PNG)

### Pitfalls
* Dependence of other patters
* Multiple commands

### Contrast
Command
> Object per command
> Class contains what
> Encapsulates action

Strategy
> Object per strategy
> Class contains how
> Encapsulates algorithm
