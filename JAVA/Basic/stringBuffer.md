#StringBuffer

```StringBuffer``` is a type which is commonly used when adding or modifying strings.

```StringBuffer``` is used as follows.

###Append
Test.java
```java
public class Test {
  public static void main(String[] args) {
    StringBuffer sb = new StringBuffer();
    sb.append("hello");
    sb.append(" ");
    sb.append("jump to java");
    System.out.println(sb.toString());
  }
}
```
The output is
```java
hello jump to java
```

The ```StringBuffer``` datatype makes us to keep add strings by using the ```append``` method.

As in the example above, we can use the ```toString()``` method to chagne to the String type.

We can write a code like this if the above example is expressed only by a String data type.

```java
public class Test {
  public static void main(String[] args) {
    String temp = "";
    temp += "hello";
    temp += " " ;
    temp += "jump to java";
    System.out.println(temp);
  }
}
```
The output is
```java
hello jump to java
```

The process of creating an object internally and using memory is different even though the outputs for both code are same.

The ```StringBuffer``` object is created only once in the first example.

The second example creates a new String object whenver ther is a ```+``` operation on the String type.

(Java automatically creates a new String object if there is an operation between strings.)

4 String date type obects are created in the second example.



















