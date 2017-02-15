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
Just like ```public HouseDog(String name) { ... ``` is a constructor, which the method name is same as the class's, 
and has no return type.

>Rules of a **constructor**

>1. The name of method and class are same.

>2. There's no return type.


If we define a constructor in the ```HouseDog``` class like above and then write it like the following, an compile error occurs.

```HouseDog dog = new HouseDog();```

The reason for the error is that the constructor is declared.

When a constructor is declared, it is possible to create an object only according to the rules of the constructor.

To solve the compile error, we must pass the string to the constructor as shown below.

```HouseDog dog = new HouseDog("happy");```

The above changes will automatically call the constructor method and pass the string ```happy``` to the constructor's input variable.

The ```happy``` which is  passed to the constructor will be set to the instance variable name by the ```setName``` method.

The benefir of using the constructor in this way is that we can control essential behaviors such as ```setName("happy")``` when we create an instance.

You can see that it prints the same result as the following when you execute the main method of the ```HouseDog``` class.

```happy```


## Default Constructor

Let's see the following code,

```java
public class Dog extends Animal {
  public void sleep() {
      System.out.println(this.name + " zzz");
   }
}
```

and this code,

```java
public class Dog extends Animal {
  public Dog() {
  }
  
  public void sleep() {
      System.out.println(this.name + " zzz");
  }
}
```

What's the difference between the first and the second code? 

There's a constructor in the second one. 

The constructor which has no input field just like the above is called the ```default constructor```.


If we implement the ```default constructor``` above, the above ```default constructor``` will be executed when the ```Dog``` object is created with ```new Dog()```.

If there's no ```constructor``` in the ```class```, the compiler automatically adds the ```default constructor``` as above.

However, the compiler does not add a ```default constructor``` is any of the user-written constructors are implemented.

> For this reason, ```new HouseDog()``` can't be used after creatring a constructor which accepts ```name``` as input in the ```HouseDog``` class.
