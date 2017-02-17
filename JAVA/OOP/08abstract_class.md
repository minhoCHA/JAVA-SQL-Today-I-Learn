#Abstract Class

An abstract class is a Java's special class that acts as an interface, but also has an inplementation. 

Let's turn our ```Predator``` interface into an abstract class.

It should be changed as follows in order to maintain the original function

Predator.java
```java
public abstract class Predator extends Animal {
  public abstract String getName();
}
```

We should add ```abstract``` in front of a class to make an abstract class. 

We should also add ```abstract``` to the method that acts like the interface's method(```getName``` method in here).

An abstract method has no body just like an interface method.

In other words, classes that inherit abstract classes must implement their abstract methods.

The ```Tiger``` and ```Lion``` classes should also changed as follows if we change the ```Predator``` interface to an abstract class like above.

Tiger.java
```java
public class Tiger extends Predator implements Barkable { 
  public String getName() {
    return this.name;
  }
  
  public void Bark() {
    System.out.println("Bow");
  }
}
```
Lion.java
```java
public class Lion extends Predator implements Barkable {
  public String getName() {
    return this.name;
  }
  
  public void bark() {
    System.out.println("Meow");
  }
}
```

The ```Tiger``` and ```Lion``` classes have been modified to extends the ```Predator``` abstract class rather than implements ```Predator``` interface.

And the ```getName``` method declared as a abstract method in ```Predator``` absract is implemented as above.

A method declared abstract in an abstract class(```getName``` method) is a method that must be implemented in a class that inherits an abstract class, just like an interface method.

The ```ZooKeeper``` class has no changes. 

The ```getName``` method implemented in the existing ```Animal``` class is now useless so should be removed.

Animal.java
```java
public class Animal {
  String name;
  
  public void setName(String name) {
    this.name = name;
  }
}
```

We can add not only abstract methods but also actual methods to abstract classes. 

Adding an actual method to an abstract class makes all of those methods available to objects created with ```Tiger```, ```Lion``` ...

For example, if we add a method named ```isPredator``` to the ```Predator``` abstract class as shown below, we can use it in ```Tiger```, ```Lion``` ... that inherit this class.

```java
public abstract class Predator extends Animal {
  public abstract String getName();
    
  public boolean isPredator() {
    return true;
  }
}
```

It's possibly be very complex in design since Java does not support mutiple inheritance(inheriting multiple classes at the same time)(Java only supports single inheritance) if we use abstract classes.
