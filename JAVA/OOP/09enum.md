# ENUM

열거 타입 enum
 * 자바에서 열거타입 ```enum```을 정의할 수 있으며, 변수를 선언할 때, 변수 타입으로 사용 가능
 * ```enum```은 그 타입 변수의 모든 가능한 값을 열거함으로써 지정할 수 있다.
 
 * ```enum Season {winter, spring, summer, fall}```
 * ```enum``` 에서 나열할 수 있는 값들의 수는 제한이 없다.
 
 * ```Season time;```
 * 변수 ```time```은 가질 수 있는 값이 제한되어 ```Season```의 4개 값 중 하나만 가질 수 있다.
 * 그 외의 값을 가지게 되면 compile error가 발생.
 
 * ```time = Season.spring;```
 * ```enum```은 변수가 가실 수 있는 값의 수가 적을 때 꽤 도움이 된다.
 * ex - 학생이 받을 수 있는 학점.
 * ```enum Grade { A, B, C, D, F}```
 * ```Grade```는 이 학정 중의 하나의 값만 가질 수 있다.
 
 -------------

 * ```enum```의 methods
 * ```< static methods >```
 * - ```valueOf(String arg)``` : ```String``` 값을 ```enum```에서 가져온다. 값 없으면 ```exception``` 발생.
 * - ```valueOf(Class<T> class, String arg)``` :넘겨받은 ```class```에서 ```String```을 찾아, ```enum```에서 가져온다.
 *   ```valueOf(String arg)```는 내부적으로 자기 자신의 ```class```를 가져오는 것이다.
 * - ```values()``` : enum의 요소들을 순서대로 enum 타입의 배열로 return.
 *	 ```ENUM$VALUES```의 copy이므로, 너무 자주 call 하지 않는 것이 좋다.
 * ```< Non-Static Methods >```
 * - ```name()``` : 호출된 값의 이름을 ```String```으로 나타낸다.
 * - ```ordinal()``` : 해당 값이 enum에 정의된 순서를 return.
 * - ```compareTo(E o)``` : 이 ```enum```과 지정된 객체의 순서를 비교한다.
 * - 지정된 객체보다 작은 경우 음의 정수, 동일하면 0, 크면 양의 정수 return
 * - ```equals(Object other)``` : 지정된 객체가 이 ```enum``` 정수와 같은 경우, ```true```를 return
 



enumTest.java
```java
public class enumTest {

	public enum City { Seoul, Busan, SF, LA }
	
	public enum Season {
		
		Spring ("March through May"),
		Summer ("June through August"),
		Fall ("September through Noverber"),
		Winter ("December through February");
		
		private String span;
		
		Season(String months) {
			span = months;
		}
		
		public String getSpan() {
			return span;
		}
	}
	
	public enum Country {
		
		Korea ("The country where I am from"),
		US ("The country where I currently live"),
		NZ ("The country where I used to live");
		
		private String span;
		Country(String status) {
			span = status;
		}
		
		public String getSpan() {
			return span;
		}
	}
	
	public static void main(String[] args) {
		City city1 = City.valueOf("Seoul");
		
		System.out.println("city1: " + city1.name());
		System.out.println("city1's order: " + city1.ordinal());
		System.out.println();
		
		City city2 = City.valueOf("SF");
		
		System.out.println("city2: " + city2.name());
		System.out.println("city2's order: " + city2.ordinal());
		System.out.println();
		
		for(Season time: Season.values()) {
			System.out.println(time + "- " + time.getSpan());
		}
		
		for(Country list: Country.values()) {
			System.out.println(list+ "- " + list.getSpan());
		}
	}
```


 * - ```enum City``` : 위의 예제에서 ```City```와 ```Season``` 두 가지 열거형 ```enum``` 사용.
 * 기본적으로 ```City```와 같은 ```enum```을 많이 사용한다. 이렇게 제한된 값만을 처리할 때, ```enum``` 사용.
 * 만약 ```City```에 없는 ```Seattle```과 같은 값을 호출하면, ```java.lang.IllegalArgumentException```이 발생.
 * 
 * - ```enum Season : enum Season```과 같이 기본적인 열거형 데이터 외에도, 연관된 데이터를 같이 선언할 수 있고,
 * ```enum```안에 함수도 선언할 수 있다. 각 데이터에 연관된 값을 가져오려면 위의 예제와 같이 함수를 선언하여 값을 처리하고,
 * ```get``` 함수를 선언해야 ```enum```에서 가져올 수 있다.
 * 
 * - ```enum```은 한정된 데이터를 다루므로, 조건문 사용 시 ```Switch```문 사용하면 유용하다.
 *
----------------------
 * ```< 암묵적으로 정의되는 method >```
 * 이것은 아래와 같이 compile이 된다.
 

enum.java
```java
final class City extends Enum<City> {
	private City(String name, int ordinal) {
		super(name, ordinal);
	}
	
	public static final Status Seoul = new Status("Seoul", 0);
	public static final Status LA = new Status("LA", 1);
	public static final Status SF = new Status("SF", 2);
	
	private static final Status ENUM$VALUES[] = { Seoul, LA, SF };
}
```
-------------------
 * ```< enum의 특이사항 >```
 * ```enum```은 생성자가 ```private``` 이므로, ```new```로 새로운 ```instance``` 를 만들 수 없다.
 * ```newInstance()```에 의해 ```instance``` 를 만들 수 없다. ```newInstance()```를 호출하면 ```InstantiationException```이 발생한다.
 * ```clone()```을 만들 수 없다. ```Enum class```를 상속받고 있지만, ```clone() method```가 ```final```로 지정 되어 있어 사용하면 ```CloneNotSupporedException```이 발생한
 * ```Serialize : enum``` 의 값이 수정되어 순서가 변경되어도, ```ordinal``` 값이 재정의 된다. 
