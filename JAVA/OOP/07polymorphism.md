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

```java
public void barkAnimal(Animal animal) {
    if (animal instanceof Tiger) {
        System.out.println("Bow");
    } else if (animal instanceof Lion) {
        System.out.println("Meow");
    } else if (animal instanceof Crocodile) {
        System.out.println("Lala");
    } else if (animal instanceof Leopard) {
        System.out.println("Yoyo");
    }
}
```

Well, not good.

Since we've covered the ```interface``` we can find a better solution.

Let's create an interface named ```Barkable``` like this

Barkable.java

```java
public interface Barkable {
  public void bark();
}
```
also make ```Tiger``` and ```Lion``` classes to execute the ```Barkable``` interface.

Tiger.java
```java
public class Tiger extends Animal implements Predator, Barkable {
  public void bark() {
    System.out.println("Bow");
  }
}
```

The interface can implements several things by , like above.

The ```Tiger``` class implements ```Predator``` interface and ```Barkalbe``` interface.

We made ```Tiger``` class to print ```Bow``` when it executes ```bark``` method.

Lion.java
```java
public class Lion extends Animal implements Predator, Barkable {
  public void bark() {
    System.out.println("Meow");
  }
}
```

```Lion``` class prints ```Meow``` when it executes ```bark``` method.

We can change ```barkAnimal``` method of ```Bouncer``` class like the following if we implement ```bark``` method in ```Tiger``` and ```Lion``` classes.

Before changed,

```java
public void barkAnimal(Animal animal) {
  if (animal instanceof Tiger) {
    System.out.println("Bow");
  } else if (animal instance of Lion) {
    System.out.println("Meow");
  }
}
```
after changed,

```java
public void barkAnimal(Barkable animal) {
  animal.bark();
}
```

The input datatype of the ```barkAnimal``` method has changed from ```Animal``` to ```Barkable```.

We also changed the part which check the object type of the ```animal``` and prints ```Bow``` or ```Meow``` to just call the ```bark``` method.

The complicated conditional branch statement is 







The input datatype of the barkAnimal method has changed from Animal to Barkable. I checked the object type of the animal and changed the "bark" or "growl" output to just call the bark method. I made this change, and the complicated conditional branch statement disappeared, and it became clear code for anyone. Amazing !!

If you use polymorphism, you can easily process the conditional statements of complex if else as shown in the above example.
The tiger and lion objects used in the above example are objects of the Tiger and Lion classes, respectively, and objects of the Animal class and objects of the Barkable and Predator interfaces. For this reason, you can use the input datatype of the barkAnimal method from Animal to Barkable.

In the object-oriented world, polymorphism refers to the fact that an object can have multiple data type types.

In other words, an object of the Tiger class can be expressed in various data types as follows.
  
