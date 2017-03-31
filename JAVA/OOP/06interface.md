# Interface

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
```java
public class Crocodile extends Animal implements Predator {
}
```

We should now know that why we need an interface.

Normally, if we are writing an important class(```ZooKeeper``` will be an important class here), we must write an importance class based on the interface, regardless of the implementation of the class.

Because the implementation(```Tiger```, ```Lion```, ```Crocodile```, ...) increases, but the interface(```Predator```) in only one.

Now there's a problem in the ```ZooKeeper``` class. 

The ```feed``` method of the ```ZooKeeper``` class unconditionally make an output ```feed tiger```.

If ```lion``` comes, we should print ```feed lion``` !

```java
public void feed(Predator predator) {
   System.out.println("feed tiger");
}
```

Now, we can change the interface.

Add the following method in the ```Predator``` interface.

Predator.java
```java
public interface Predator {
   public String getName();
}
```

We've just added ```getName``` method. But there's no contents in it!

Interface method only have a name and no content.

It's one of the rules of the interface. 

The method ```getName``` should be implemented by the classes that implements the interface.

If we add methods to the interface above will cause compile error in the classes which implement ```Predator``` interface such as ```Tiger```, ```Lion```. 

To solve the error, let's implement the ```getName``` method in ```Tiger```, ```Lion```.

Tiger.java
```java
public class Tiger extends Animal implements Predator {
   public String getName() {
      return this.name;
   }
}
```

Lion.java
```java
public clsas Lion extends Animal implements Predator {
   public String getName() {
      return this.name;
   }
}
```

The ```getName``` methos was created to return the instance variable ```name```. It will comlile without any problems.

Now, the ```ZooKeeper``` class can be changed as follows:

```java
public class ZooKeeper {
   public void feed(Predator predator) {
      System.out.println("feed" + predator.getName());
   }
}
```

The ```feed``` method was changed to print ```"feed" + predator.getName()``` from the output ```feed tiger```.


When we call ```predator.getName()```,  ```getName()``` on the implementation (```Tiger```, ```Lion```) that implements the 

```Predator``` interface will be called.

Let's create the ```main``` method as follows and execute the ```ZooKeeper``` class.

```java
public class ZooKeeper {
   public void feed(Predator predator) {
      System.out.println("feed " + predator.getName());
   }
   
   public static void main(String[] args) {
      Tiger tiger = new Tiger();
      tiger.setName("tiger");
      
      Lion lion = new Lion();
      lion.setName("lion");
      
      ZooKeeper zooKeeper = new ZooKeeper();
      zooKeeper.feed(tiger);
      zooKeeper.feed(lion);
   }
}
```

The output will be

```java
feed tiger
feed lion
```

But we can see that the ```Tiger``` and ```Lion``` in ```getName``` method is duplicated.

The ```getName``` method might be better to drag it to ```Animal```.

Move the ```Tiger```'s ```getName``` method to the ```Animal``` class and remove the ```getName``` method from ```Tiger``` and ```Lion```.

> Refactoring is the act of combining these duplicate methods and moving its position.

Let's take a look at the classes that have been created and finished with refactoring.

Animal.java
```java
public class Animal {
   String name;
   
   public void setName(String name) {
      this.name = name;
   }
   
   public String getName() {
      return this.name;
   }
}
```

Predator.java
```java
public interface Predator {
   public String getName();
}
```

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

ZooKeeper.java
```java
public class ZooKeeper {
   public void feed(Predator predator) {
      System.out.println("feed " + predator.getName());
   }
   
   public static void main(String[] args) {
      Tiger tiger = new Tiger();
      tiger.setName("tiger");
      
      Lion lion = new Lion();
      lion.setName("lion");
      
      ZooKeeper zooKeeper = new ZooKeeper();
      zooKeeper.feed(tiger);
      zooKeeper.feed(lion);
   }
}
```

Now the ```ZooKeeper``` class can execute ```feed``` methods regardless of ```Tiger```, ```Lion```, ```Crocodile``` by using the ```Predator``` interface.

The most important part of this chapter is understanding why interfaces are needed.

Of course, we can create a program without knowing the interface, but it's far from an object-oriented program.

Let's think about the interface more conceptually this time.

We know about the USB ports on our computer. 

The devices that can be connected to the USB port are hard disk, memory stick, digital camera and so on.

This USB port is the real world's interface.

We can make any device knowing the specifications of the USB port. 

Also, the computer only provides a USB port and the computer don't need to worry about which device is made. 

This is the main points of the interface.

Like the ```ZooKeeper```, which does not matter what kind of ```Predator``` (```Tiger```, ```Lion``` ...) it is feeding.


1. Computer == ZooKeeper
2. USB Port == Predator
3. Hard disk, camera == Tiger, Lion, Crocodile



> The USB port has various rules that electronic devices must observe. (methods of the interface)

