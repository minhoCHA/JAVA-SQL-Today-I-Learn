# Generics

I only cover how to use generics in here.

This is generics.
```java
ArrayList<String> aList = new ArrayList<String>();
```

The generic expression ```<String>``` in the first code means that "the only type can be contatined in an ```ArrayList``` is a ```String```.

In other words, using ```generic``` allows us to do more explicit type checking.



In other words, using generic allows you to check the type more clearly and it gives us some advantages when we writing codes.

First, let's take a look at the case of not using generics.

```java
ArrayList aList = new ArrayList();
aList.add("hello");
aList.add("java");

String hello = (String) aList.get(0);
String java = (String) aList.get(1);
```

The objects added in ```ArrayList``` are recognized as object type if we don't use generics like above.

An object type is the most basic type that all objects inherit.

Therefore, there's no problem when we put a value in ```aList``` of ```ArrayList``` object, 

but we should change the type(= called casting) from Object type to String type when we take the value.

```java
String hello = (String) aList.get(0); // cast object to String. (String)
```

Morever, since ```aList``` can contain objects other thatn String objects,

there's a can be an error due to invaild casting during the casting process.

This is why we need to use generic.

The code looks like this if we change the above code by using generics.

```java
ArrayList<String> aList = new ArrayList<String>();
aList.add("hello");
aList.add("java");

String hello = aList.get(0);
String java = aList.get(1);
```
We don't need to change a type once we declare a data type as a generic.

This is because the complier already knows that only a String type must be added to ```aList```.

Generics make us to avoid unnecessary coding by casting and runtime error by wrong casting.
