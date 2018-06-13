# ArrayList

#### Create an ```object```

Create an ```object``` named ```ArrayList```


ArrayList.java
```java
public class ArrayList {
  private int size = 0;
  private Object[] elementData = new Object[100];
}
```

Main.java
```java
public class Main {
  public static void main(String[] args)
    ArrayList numbers = new ArrayList();
}
```

-------------------------

##### Add data

###### at the last position
```java 
public boolean addLast(Object element) {
  elemetnData[size] = element;
  size++;
  return true;
}
```

Now using the above method in Main.java

```java
public static void main(String[] args) {

  ArrayList numbers = new ArrayList();
  numbers.addLast(10);
  numbers.addLast(20);
  numbers.addLast(30);
  numbers.addLast(40);
}
```

##### at the middle of the data
```java
public boolean add(int index, Object elemet) {

  // we should move from the last element to the index node to one position back in order to add an element in the middle of the data
  for (int i = size -1; i >= index; i--) {
    elementData[i + 1] = elementData[i];
  }
  
  // add node to index
  elementData[index] = element;
  // increment the number of element
  size++;
  return true;
}
```
--------------------------------
We should be careful to find out a first and a last positions in order to make loop.

* a first position : the starting index in a loop, we can find this with  ```size - 1```.
* a last position : we can use the first element of ```add``` method
* loop : decrement operator ```i--```
  
You can move all the elements to one position back through this process. 
Now you can add an element in an empty position.

```java
elementData[index] = element;
````
Now we added the element, increase the size.
```java
size++;
```

Main.java
```java
ArrayList numbers = new ArrayList();
numbers.addLast(10);
numbers.addLast(20);
numbers.addLast(30);
numbers.addLast(40);
numbers.add(1, 15);
```


##### at the first of the data
```java
public boolean addFirst(Object element) {
  return add(0, element);
}
```

Main.java
```java
ArrayList numbers = new ArrayList();
numbers.addLast(10);
numbers.addLast(20);
numbers.addLast(30);
numbers.addLast(40);
numbers.add(1, 15);
numbers.addFirst(5);
```

 --------------------------
 #### Check the data
 
 to check the data, we'll going to inherit ```toString``` object
 
 ```java
 public String toString() {
  String str = "[";
  for(int i = 0; i < size; i++) {
    str += elementData[i];
    if(i < size - 1) {
      str += ",";
    }
  }
  return str + "]";
}
```

Now we can see elements in the list by executing Main.java
```java
public static void main(String[] args) {
  ArrayList numbers = new ArrayList();
  numbers.addLast(10);
  numbers.addLast(20);
  numbers.addLast(30);
  numbers.addLast(40);
  numbers.add(1, 15);
  numbers.addFirst(5);
  System.out.println(numbers);
}
```

-----------------
#### Delete 

It's similar to adding element in the middle.
```java
public Object remove(int index) {

  // save data in ```removed``` variable before deleting the element
  Object removed = elementData[index];
  
  // Fill the positions by moving one by one from the deleted element to the last element.
  for (int i = index + 1; i <= size - 1; i++) {
    elementData[i - 1] = elementData[i];
  }
  
  // decrese the size
  size--;
  
  // delete the last element
  elementData[size] = null;
  return removed;
}
```
