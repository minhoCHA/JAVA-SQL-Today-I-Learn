#Inheritance

Inheritance is literally means that inherit something.

We can make a ```dog``` class which inherits from the ```Animal```.

Animal.java
```java
public class Animal {
  String name;
  
  public void setName(String name) {
      this.name = name;
  }
}
```

Dog.java
```java
public class Dog extends Animal {
  
}
```

To inherit a ```class```, we use ```extends``` keyword.

The example above shows the way of ```Dog``` class inherits ```Animal``` class.
