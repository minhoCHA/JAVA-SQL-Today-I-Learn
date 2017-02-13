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
