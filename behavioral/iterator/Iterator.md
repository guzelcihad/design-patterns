### Concepts
* Traverse a container
* Don't expose underlying structure
* Decouples algorithm
```
java.util.Iterator
```

### Design
* Iterator based
* Factory method based

### Uml
![alt text](D:\Repositories\DesignPatterns\src\main\resources\images\4.PNG)

### Pitfalls
* Access to index
* Directional

### Contrast
Iterator
> Interface based
> No index

For-loop
> Exposes an index
> Typically slower 
