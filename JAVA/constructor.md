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




Instead of setting the name with the setName method on an instance created with the HouseDog class, you can call it like this:
