# Method

Write a method that takes an array of integers and returns the sum of all the integers.

```java
public class sum {
	
  public static void main(String[] args) {
		
	int[] sumArray = {1, 2, 3};
	System.out.print(findSum(sumArray));
  }
		
  public static int findSum(int[] array) {
		
	int sum = 0;
	for(int i : array) {
	  sum += i;
	}
	return sum;
  }
}
```
