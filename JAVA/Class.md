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

So, if I make cs instance like this, ```java University cs = new University()```

I can use name which is the instance variable of cs like this.

```java
cs.name
```


