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






HouseDog 클래스에 Dog 클래스와 동일한 형태의 sleep 메소드를 구현하면 HouseDog 클래스의 sleep 메소드가 Dog 클래스의 sleep 메소드보다 더 높은 우선순위를 갖게 되어 HouseDog 클래스의 sleep 메소드가 호출되게 된다.

이렇게 부모클래스의 메소드를 자식클래스가 동일한 형태로 또다시 구현하는 행위를 메소드 오버라이딩(Method Overriding)이라고 한다. (※ 메소드 덮어쓰기)
