#Inheritance

Inheritance literally means that inherit something.

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

We didn't make a method named ```setName``` or a variable named ```name``` in ```Dog``` class,

but we could use it since we've inherited it.

Now we can write ```main``` method and run it.

```java
public class Dog extends Animal {
  public static void main(String[] args) {
      Dog dog = new Dog();
      dog.setName("poppy");
      System.out.println(dog.name);
  }
}
```

The output will be ```poppy``` as we expected.

So, inheritance means that child classes inherit all the funtinoality of the parent class.

Now, we can add new method in ```Dog``` class.

```java
public class Dog extends Animal {
  public void sleep() {
      System.out.println(this.name + " zzz");
  }
  
  public static void main(String[] args) {
      Dog dog = new Dog();
      dog.setName("poppy");
      System.out.println(dog.name);
      dog.sleep();
   }
 }
 ```
 
 We've just added method named ```sleep```. Noe ```Dog``` class has more funtions than ```Animal``` class.
 
 >```public``` keyword which is at the beginning of ```sleep``` method is one of the access controllers to control access.
 >```public``` makes any kinds of classes to access ```sleep``` method.
 
##Method overriding

Now, let's create a ```HouseDog``` class that makes ```Dog``` more specific.

The ```HouseDog``` class inherits the ```Dog``` class and can be created as follows

HouseDog.java
```java
public class HouseDog extends Dog {
  public static void main(String[] args) {
      HouseDog houseDog = new HouseDog();
      houseDog.setName("happy");
      houseDog.sleep();
  }
}
```

We implemented the ```sleep``` method in the ```Dog``` class in the same way in ```HouseDog``` and tried to execute it.

```happy zzz in house```





If we implement the ```sleep``` method of the same type as the ```Dog``` class in the ```HouseDog``` class, 

the ```sleep``` method of the ```HouseDog``` class will have a higher priority than the ```sleep``` method of the ```Dog``` class, 

and the ```sleep``` method of the ```HouseDog``` class will be called.

>The method of re-implementing the methods of the parent class in the same form as the child class is called method overriding. 
>(※Overwrite method)


##Multiple inheritance

Multiple inheritance means that a class inherits one or more classes.

Many languages, including C++ and Python, support multiple inheritence, but Java does not support multiple inheritance.

If Java supports multiple inheritance, the following code could be created.

```java
class A {
  public void msg() {
      System.out.println("A message");
  }
}

class B {
  public void msg() {
      System.out.println("B message");
  }
}

class C extends A, B {
    public void static main(String[] args) {
        C test = new C();
        test.msg();
    }
}
```


Assuming that Java supports multlple inheritance, we inherited ```A``` and ```B``` classes at the same time as follows.
(This is code that can't actually work)

In the main method above, when we use ```test.msg()```, should we run ```msg``` method of class ```A``` at runtime?
Or should we run the ```msg``` method of class ```B```?
Supporting multiple inheritance will result in ambiguity.
Java is the language that originally cut out those uncertainties.

>In other langueages that support multiple inheritance, they resolve it by applying priority or simething if they inherit the same method.
