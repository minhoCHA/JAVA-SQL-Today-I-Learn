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
 
