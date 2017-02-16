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

With these chagne, the complicated conditional branch statement disappeared and it became clear code.

> We can easily control the conditional statement(complex ```if else```) as shown in the above if we use polymorphosm.

The ```tiger``` and ```lion``` objects in the above example are objects for the ```Tiger``` and ```Lion``` classes, and also the objects of the ```Animal``` class and the objects of the ```Barkable``` and ```Predator``` interfaces.

For this reason, we can use the input datatype of the ```barkAnimal``` method from ```Animal``` to ```Barkable```.

> Polimorphism refers that an object can have multiple data types.

So, the object of the ```Tiger``` class can be expressed in various data types as follows.

```java
Tiger tiger = new Tiger();
Animal animal = new Tiger();
Predator predator = new Tiger();
Barkable barkable = new Tiger();
```

But note that the ```predator``` object declared as ```Predator``` and the ```barkable``` object declared as ```Barkable``` have different methods to use.

```predator``` method can only call ```getName``` method since it's the object of ```Predator``` interface which the ```getName()``` method is declared.

Likewise, the object ```barkable``` can only call ```bark``` method since it's declared by ```Barkable```

What if we want to use both the ```getName``` and ```bark``` methods?

We can use a ```tiger``` object declared in ```Tiger``` which implements the ```Predator```, ```Barkable``` interface, 

or create a new interface which includes both the ```getName``` and ```bark``` methods as follows


BarkablePredator.java
```java
public interface BarkablPredator {
  public void bark();
  public String getName();
}
```
or
```java
public interface BarkablePredator extends Predator, Barkable {
}
```
The second way is to utilize the existing interface.

We can inherit the ```getName``` method of ```Predator``` and the ```bark``` method of ```Barkable``` by using the second way.

Unlike a normal class, an interface can inherit nultiple interfaces (```Predator```, ```Barkable```) by using extends.

So it's possible to use multiple inheritance. 
(* In general class, only single inheritance is possible.)


Here are the final ```Barkable``` interfaces and the ```Tiger```, ```Lion```, and ```Bouncer``` classes.

Barkable.java
```java
public interface Barkable {
  public void bark();
}
```
Tiger.java
```java
public class Tiger extends Animal implements Predator, Barkable {
  public void bark() {
    System.out.println("Bow");
  }
}
```
Lion.java
```java
public class Lion extends Animal implements Predator, Barkable {
  public void bark() {
    System.out.println("Meow");
  }
}
```
Bouncer.java
```java
public class Bouncer {
  public void barkAnimal (Barkable animal) {
    animal.bark();
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
