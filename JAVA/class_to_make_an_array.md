## Class

Use your new Cat class to make an array of 25 Cat(s), such that every 3rd cat has a hat. Use this array to produce the answer to last week's problem:

There are 25 cats.

Cat 1: No hat

Cat 2: No hat

Cat 3: Has a hat

Cat 4: No hat

.

.

.

Cat 25: No Hat




	  public class cat {
	
	     public static void main(String[] args) {

		  int[] catArray = new int[25];
		  findHat(catArray);
	     }
	
       	     public static void findHat(int[] array) {
  
	  	  System.out.println("There are " + array.length + " cats.");
		  
		  for(int i = 1; i <= 25; i++) {
		      System.out.println("Cat " + i + ": ");
		  	
		  	if(i % 3 == 0)
		            System.out.println("Has a hat");
		  	else
		  	    System.out.println("No hat");
	          }
	     } 
	  }
