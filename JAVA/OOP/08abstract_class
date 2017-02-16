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




















