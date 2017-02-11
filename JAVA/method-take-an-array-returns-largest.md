## Method

Write a method that takes an array of integers and returns the largest integer.

  public class largest{
  
    public static void main(String[] args)
    {
       int[] largestArray = {1, 5, 99, 0};
       System.out.print(findLargest(largestArray));
    }
    
    public static int findLargest(int[] array)
    {
      int largest = array[0];
      
      for(int i = 0; i < array.length; i++)
      {
        if(array[i] > largest)
            largest = array[i];
      }
      
      return largest;
    }
  }
