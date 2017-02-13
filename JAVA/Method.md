# Method

The difference between other languages and Java is that Java has a ```function``` in a class.

We called it ```Method```.

Since I'd already talked about ```method``` in the other text, I'd like to focus on In/Output here.

>Just think about a mixer.
>We put some fruits in there to make a cup of juice. 

>So ```Input``` is fruits, and ```Output```(or a ```return``` value) is a cup of juice.
>Then what is the mixer?

The mixer is a ```method```. Do something and returns some an ```output```. This is what ```method``` do.

## Why do we need to use a ```method```?

When we coding, sometimes we write same thing for several times, and that's the time we need to use a ```method```.
Moreover, one of the other reasons is that we can easily see the structure of a program.

> Imagine a product comes from a factory, it passes some kinds of processes
> and just like that, we can easily see the processes how the return value changing while passing through the processes.

It makes us to notice where an err comes from and easily see the flow of codes.

Let's see the example below.

```java
public int sum(int a, int b) {
    return a + b;
}
```
It means, the ```method``` get two ```values```(```int a```, ```int b```) and ```return value``` is ```a + b```.

Test.java
```java
public class Test {

    public int sum(int a, int b) {
        return a + b;
    }
    
    public static void main(String[] args) {
        int a = 3;
        int b = 5;
        
        Test myTest = new Test();
        int c = myTest.sum(a, b);
        
        System.out.println(c);
    }
}
```
We can easily see the process.

## An ```Input value``` and a ```return value``` in ```method```

> ```Input value``` ---> ```method``` ---> ```return value```

### A structure of a ```method```
```java
public type method_name(type1 variable1, type2 variable2) {
        return return value; // Don't need to use return if return value is ```void```
}
```

We can classify a method in 4 cases.
* A ```method``` with ```Input value``` and ```return value```.
* A ```method``` without ```Input value``` and ```return value```.
* A ```method``` without ```Input value``` and has ```return value```.
* A ```method``` with ```Input value``` and has no ```return value```.

### A normal ```method```
A normal ```method``` has both ```Input value``` and ```return value```.

```java
public int sum(int a , int b) {
    return a + b;
}
```

The type of ```Input``` and ```return values``` in ```sum``` method is 
* ```Input value``` - ```int type a, int type b```
* ```return value``` - ```int type```

The method ```sum``` accepts two ```Input values``` and returns ```return value``` which is ```a + b```.
We use the method which has both ```Input value``` and ```return value``` like this

``` a_value_which_is_going_to_get_return_value = instance.name_of_method(input_argument1, input_argument2, ...)```


The code for it is
```java
Test myTest = new Test();
int c = myTest.sum(a, b);
```

Like this, ```c``` 's type should be ```int``` since the return type of the method ```sum``` is already sets as an ```int```.
