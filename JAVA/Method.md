# Method

The difference between other languages and Java is that Java has a ```function``` *in a class*.*

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


### A ```method``` without an ```input value```

```java
public String say() {
    return "Hi";
}

The type of ```Input``` and ```return values``` in ```say``` method is 
* ```Input value``` - NONE
* ```return value``` - ```String type```

We can use this ```method``` like this

```java
Test myTest = new Test();
String a = myTest.say();
System.out.println(a);
```

We shouldn't put anyting in ```()``` to use this method.
There's no ```Input value``` but it returns ```Hi```.
So if we use ```String a = myTest.say()``` then ```Hi``` is going to be in ```a```.

``` a_value_which_is_going_to_get_return_value = instance.name_of_method()```



### A ```method``` without a ```return value```

```java
public void sum(int a, int b) {
    System.out.println(a + " + " + b + " is " + (a + b));
}

The type of ```Input``` and ```return values``` in ```say``` method is 
* ```Input value``` - int type a, int type b
* ```return value``` - ```void```

We can use this ```method``` like this

```java
Test myTest = new Test();
myTest.sum(3, 5);
```
So we can use the method like this if there's no return value
```instance.name_of_method(input argument1, input argument2, ...)```

The output for the code will be
```3 + 5 is 8```

>But why we say that there's no return value even though there's the sentence ```3 + 5 is 8```?
>Because ```System.out.println``` is just a sentence which can be used in a method, there's no return value.
>A return value can be returned only with ```return``` command





### A ```method``` without an ```Input value``` and a ```return value```

```java
public void say() {
    System.out.println("Hi");
}

The type of ```Input``` and ```return values``` in ```say``` method is 
* ```Input value``` - Node
* ```return value``` - ```void```

We can only use this ```method``` like this

```java
Test myTest = new Test();
myTest.say();
```
So we can only use the method like this if there's no an input value and a return value
```instance.name_of_method()```


### Another way of using ```return```
We can use ```return``` when we want to get out from a method immidiately.

```java
public void say_nick(String nick) {
    if("fool".equals(nick)) {
        return;
    }
    System.out.println("My nickname is " + nick);
}
```
This method gets an input value ```nick``` and just prints it. There's no return value.
Meaning that prints string value is completely different from a method which has a return value.
A return value generates only by ```return``` command.
So this method gets out from the method if an input value is ```fool```. 
We can use ```return``` like this when we want to get out from a method with special cases.

###The scope of a variable declared in a method

What if the name of the variable used in the method is the same as the name used outside the method? 
If you have a question like this, you will know for sure.

```java
public void vartest(int a) {
    a++;
}

public static void main(String[] args) {
     int a = 1;
     Test myTest = new Test();
     myTest.vartest(a);
     System.out.println(a);
}

First, create a variable a and substitute ```1```. 

We also incremented the input value by ```1``` and gave the value of ```a``` as the input value to the ```vartest``` method that does not return the return value. 

Next, the value of ```a``` is output. Of course, I added a ```1``` in ```vartest```, so ```2``` seems to be output, but if you create a program source and run it, the result is ```1```.


This is because the newly created variable in the method is a variable that is written only within the method. 
In other words, in the statement ```public void vartest (int a) {``` ,
the variable ```a``` means the variable used only in the method, not the variable ```a``` outside the method.

The above ```vartest``` method with the variable name as ```a``` is exactly the same as ```vartest``` with the variable name ```b``` as follows.

```java
public void vartest(int b) {
    b++;
}
```
In other words, the ```variable``` used in the method has no relation to the ```variable``` name outside the method. 
```Variables``` that are used only in this method are also referred to as **local variables**.

>If the input value of ```vartest``` is not an ```int``` like the above example, it is different. 
>If we pass an object to the input of a method, and the method changes the object received as input, 
>the object retains the changed value even after the method executes. 
>The reason for this difference is due to the value you pass to the method, 
>depending on whether you pass the value to the ```method``` or the ```object```.

Then is there any way to increase a outsise of a method by 1 using a method called ```vartest```?
Let's see the following code.

```java
public int vartest(int a) {
    a++;
    return a;
}

public static void main(String[] args) {
    int a = 1;
    Test myTest = new Test();
    a = myTest.varTest(a);
    System.out.println(a);
}
```

The solution is to use ```return```.
The ```vartest``` method returns a value that is one greater than the input value.
So if ```a = myTest.vartest(a)```, then ```a``` will be replaced my the ```reutrn value``` of the ```vartest``` method.
Of course, the variable ```a``` in the ```vartest``` method is not the same as ```a```outside the method.


<hr/>
DONE
