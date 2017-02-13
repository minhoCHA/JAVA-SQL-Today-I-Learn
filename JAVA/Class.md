# Class

## What is Class?

I can make a class named "University" like this.

```java
public class University {

}
```
It's a basic form of the class. I've just declared the class and there's no contents in it. 

But it also has a important function; **can make an object**


This is how to make an object.
```java
University student = new University();
```
```new``` is a keyword which let you make an object.

so like this, I've made an object of University; student is an instance of class named University.




>**An object and an instance**

>Another name of an object which is made by a class is an instance. Then what is the difference between those?

>```University student = new University()``` in this case, student is an object. And also, it's an instance of University.

>So, in term instance is used to explain the relation of specific object(student) between the class(University).

>It's better to use "student is an object" rather than "student is an instance" 

>and "student is an instance of University" rather than "student is an object of University".



It's easy to think like this.

* Ice cream tool ==> class

* Ice cream made with the tool ==> object



So I can easily make lots of objects with University class.

```java
University cs = new University();
University physics = new University();
University history = new University();
...
```

## Instance Variable
Now, I can put some stuff in my class. I can make my University class to give some names like cs, physics which are made by the class.

University.java
```java
public class University {
  String name;
}
```

I put String variable named 'name' in the University class. So I call it as an instance variable which is added to the class.(or a member variable)

>I can declare an instance variable as many as I want. 

I can use an instance variable like this

```java
instance.variable
```

So, if I make cs instance like this, 
```java 
University cs = new University()
```

I can use name which is the instance variable of cs like this.

```java
cs.name
```

Moreover, I can add main method to check if class is working.
```java
public class University {
    String name;
    
    public static void main(String[] args) {
        University cs = new University();
        System.out.println(cs.name);
    }
}
```

the output will be like this if I run this code
```java
null
```

The output comes out 'null' from cs.name. 'null' comes out when thers's no value assigned. 
I added instance variable 'name' in the class named University but I didn't put any value in there and that's why the output is 'null'.


## Method

There's a method in class too. It's just like a function in the class but we just call it method.
I can put some value in the instance variable named 'name' which is in the class 'Univeristy' by using a method.

```java
public class University {
    String name;
    
    public void setName(String name) {
        this.name = name;
    }
    
    public static void main(String[] args) {
        University cs = new University;
        cs.setName("Java");
        System.out.println(cs.name);
    }
}
```

> 'void' means there's no return value.

So setName method sets string which is from input in the instance variable 'name'.
```java
public void setName(String name) {
    this.name = name;
}
```

**this** from the above code indicates the instance which is made by the class 'Univeristy'. 
If I make 'cs' instance like this, ```University cs = new University()```,  then 'this' indicates 'cs'.

'setName' method is used like this in main method.
```java 
cs.setName("Java"); 
```
so this following line will be perform if I run the code above.
```java 
this.name = name; 
```

>Step-by-step

Input is "Java" as a string.
```java
this.name = "Java" 
```


It performs
```java
cs.name = "Java"
``` 
since 'this' means the instance named 'cs'.

So "Java" is going to be in the instance variable 'name' of 'cs' when I call 'setName' method.

Finally, when I run the 'University' class, the output will be
```Java ```





<hr/>
DONE
