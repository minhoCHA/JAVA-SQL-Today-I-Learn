#Interface

Interfece is an advenced feature of Java that is difficult to find in other languages.

But why we need an interface?

Consider the following scenario.

> I am a zookeeper.

> I throw a meat when a predator comes in.

> I don't care if it's a tiger of a lion.

Let's code this case.

Animal.java
```java
public class Animal {
   String name;
   
   public void setName(String name) {
      this.name = name;
   }
}
```

Tiger.java
```java
public class Tiger extends Animal {
}
```

Lion.java
```java
public class Lion extends Animal {
}
```

ZooKeeper.java
```java
public class ZooKeeper {
  public void feed(Tiger tiger) {
      System.out.println("feed tiger");
  }
  
  public void feed(Lion lion) {
      System.out.println("feed lion");
  }
}
```

Like the ```Dog``` class we saw in the other chapter, ```Tiger``` and ```Lion``` inherited ```Animal```.

And the ```ZooKeeper``` class is defined as above.

The ```ZooKeeper``` class calls different ```feed``` methods when the ```tiger``` comes in and when the ```lion``` comes in.

> If the date type of the input value is different(like `feed` mathod from ```ZooKeeper``` class, ```Tiger``` and ```Lion``` in the

above), we can use the same method name. This is called method overloading.

```ZooKeeper``` class will be perfect only if there are only a tiger and a lion in the zoo.

But the ```ZooKeeper``` should add the following ```feed``` method every time if a crocodile, leopard... are added continuously.

```java
...

public void feed(Crocodile crocodile) {
   System.out.println("feed crocodile) {
   }
}

public void feed(Leopard leopard) {
   System.out.println("feed leopard) {
   }
}

...
```

How annoying would it be if ```ZooKeeper``` has to add a ```feed``` method every time when an animal is added?

Now, it's time to use the interface.

Let's create the Predator interface as follows.

Predator.java
```java
public interface Predator {
}
```

We use ```interface``` keyword rather than ```class``` keyword just like the above.

Moreover we should change ```Tiger``` and ```Lion``` to implement the interface we've written.

Tiger.java
```java
public class Tiger extends Animal implements Predator {
}
```

Lion.java
```java
public class Lion extends Animal implements Predator {
}
```

We use ```implements``` keyword to implement the interface.

When ```Tiger``` and ```Lion``` implement the ```Predator``` interface, we can change the ```feed``` method of the ```ZooKeeper``` class as follows.

Before change
```java
public void feed(Tiger tiger) {
   System.out.println("feed tiger");
}

public void feed(Lion lion) {
   System.out.println("feed lion");
}
```

After change
```java
public void feed(Predator predator) {
   System.out.println("feed tiger");
}
```

We need ```Tiger``` and ```Lion``` as inputs to the ```feed``` method respectively,

but now we can replace it with an interface called ```Predator```.

Since not only ```tiger``` and ```lion``` are objects of ```Tiger``` and ```Lion```, but they are also objects of ```Predator``` 

interface, ```Predator``` can be used as a type of date type.

* ```Tiger``` - an object of the ```Tiger``` class, an object of the ```Predator``` interface.

* ```Lion``` - an object of the ```Lion``` class, an object of the ```Predator``` interface.


> The property that an object has several date types is called polymorphosm.


No matter what Predator is added, ```ZooKeeper``` no longer needs to add a ```feed``` method.

Every time when a predator is added, all we need to do is that just create a class that implements the ```Predator``` interface as follows.



Crocodile.java
