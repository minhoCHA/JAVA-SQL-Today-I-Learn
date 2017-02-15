#Constructor

There are some classes like this,

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
  public void sleep() {
      System.out.println(this.name + " zzz");
  }
}
```

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

Instead of setting the name with the ```setName```method on an instance created with the ```HouseDog``` class, try to call like this:

```java
HouseDog dog = new HouseDog();
System.out.println(dog.name);
```


Since no value is set for the  ```name``` instance variable, output will be  ```null```.

Like this, the ```HouseDog``` class can or may not set the value of the instance variable ```name``` as you code it.

If so, is there any way to make the compiler to compile only when we set the value in the instance variable ```name```?

Yes, we can use a **constructor**.

Now let's change the ```HouseDog``` class like this,

```java
public class HouseDog extends Dog {
  public HouseDog(String name) {
      this.setName(name);
  }
  
  public void sleep() {
    System.out.println(this.name + "zzz in house");
  }
  
  public static void main(String[] args) {
    HouseDog dog = new HouseDog("happy");
    System.out.println(dog.name);
  }
}
```
