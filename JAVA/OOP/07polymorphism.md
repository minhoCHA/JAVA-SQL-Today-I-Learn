#Polymorphism

There's polymorphism in the features of object-oriented programming.

What is polymorphism and why is it necessary?

Let's look at an example.

Let's make a ```Bouncer``` class. The ```Bouncer``` class makes ```Animal``` bark and protect a building.

Bouncer.java
```java
public class Bouncer {
  public void barkAnimal(Animal animal) {
    if(animal instanceof Tiger) {
      System.out.println("Bow");
    } else if (animal instanceof Lion) {
        System.out.println("Meow");
    }
  }
  
  public static void main(String[] args) {
    Tiger tiger = new Tiger();
    Lion lion = new Lion();
    
    Bouncer bouncer = new Bouncer();
    bouncer.barkAnimal(tiger);
    bouncer.barkAnimal(lion);
  }
}
```

If the animal object received input ```Tiger``` then the ```barkAnimal``` method prints out ```bow```, and ```Meow``` if it is a ```Lion``` object.

> ```instanceof``` is a Java's built-in keyword which used to check if a specific object is an object of a certain class.

> ```Animal instanceof Tiger``` is a conditional expression which asks "Is ```animal``` object made by ```new Tiger```?"

When you create and execute the main method as above, the following output value is displayed.

```java
Bow
Meow
```

Do you like the ```barkAnimal``` method of this ```Bouncer``` class?

When ```Crocodile```, ```Leopard```, etc. are added, the ```barkAnimal``` method should be modified as follows.

