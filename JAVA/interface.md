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

