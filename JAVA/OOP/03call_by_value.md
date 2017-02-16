# Call by value

There's a big difference between passing a ```value``` to a ```method``` and passing an ```object```. 

If you pass an ```object``` to a ```method```, you can change the ```value``` of the ```object```'s property.

Let's see the following example.

Counter.java
```java
class Updator {
  public void update(int count) {
      count++;
  }
}

public class Counter {
  int count = 0;
  public static void main(String[] args) {
    Counter myCounter = new Counter();
    System.out.println("before update: " + myCounter.count);
    Updator myUpdator = new Updator();
    myUpdator.update(myCounter.count);
    System.out.println("after update: " + myCounter.count);
    }
}
```

This example attempts to increment the ```myCounter```'s ```count``` value by passing the ```count``` value of the ```Counter``` object

to the ```Updator``` object ```myUpdator```'s ```update``` function.

The output will be like
```
before update : 0
after update : 0
```

There's no change even if we change the ```count``` value; instance variable by passing the ```update``` method.

This is because the ```update``` method has been passed the value, as I wrote in the previous text.

Now, we can change the example like this,

```java
class Updator {
  public void update(Counter counter) {
    counter.count++;
  }
}

public class Counter {
  int count = 0;
  public static void main(String[] args) {
    Counter myCounter = new Counter();
    System.out.println("before update: " + myCounter.count);
    Updator myUpdator = new Updator();
    myUpdator.update(myCounter);
    System.out.println("after update: " + myCounter.count);
  }
}
```

The difference between the previous example is that input fields for the ```update``` method.

We had a value like ```int count``` previously, but now we changed it to recieve an object like ```Counter counter```.

Moreover, the part that calling ```update``` method is also changed like this.

```java
myUpdator.update(myCounter);
```

Now if we run the code, the output will be :

```
before update : 0
after update : 1
```

The value ```counter``` of the object ```myCounter``` incremented my 1. 

> We also called ```call my value``` as ```call by reference```,
> but even though we pass an object, it goes over another reference pointing to the same object.
> So in fact, ```call by value``` is better way to say than ```call by reference```.
> But we only need to know that we can change the value of an ```object```'s property if it is passed to a ```method```.
