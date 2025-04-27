# Custom-Generics



Custom Generics 
---------------

Traditional Approach :

	1. IntegerCount.java
	---------------------

			public class IntegerCount{
			    Integer i;
				
				IntegerCount(Integer i){
				this.i = i;
				}
				
				public void print(){
				   System.out.println(i);
				}
			}
			
    2. DoubleCount.java
	---------------------

			public class DoubleCount{
			    Integer i;
				
				DoubleCount(Double i){
				this.i = i;
				}
				
				public void print(){
				   System.out.println(i);
				}
			}
			
    3. Main.java 
	-------------
	
	public class GenericExample{
	  public static void main(Strig args[]){
	  
	  IntegerCount intCount = new IntegerCount(1);
	  intCount.print();
      
      DoubleCount doubleCount = new DoubleCount(1.0);
	  doubleCount.print();
	  
      }
			   
	}
	
	
	Create your own Generic.
	------------------------
	
	a. Counter.java
	----------------

			public class Counter <T> {    //  <- what ever we are passing from the class, that type we need to create the instance variable.
			    
				T t;
				
				Counter(T t){
				this.t = t;
				}
				
				public void print(){
				   System.out.println(t);
				}
			}
	
	b. CounterMain.java 
	-------------------
	
	public class GenericExample{
	  public static void main(Strig args[]){
	  
	   Counter<Integer> iCounter  = new Counter(1);
	   iCounter.print();
	  
	  Counter<Double> dCounter  = new Counter(2.0);
	   dCounter.print();
      }
			   
	}
	
	output : 
	
	1
	2.0
	
	
	C. Bounded Example 
	------------------
	        public class Counter <T extends Number> {    //  <- what ever we are passing from the class, that type we need to create the instance variable.
			    
				T t;
				
				Counter(T t){
				this.t = t;
				}
				
				public void print(){
				   System.out.println(t);
				}
			}
	
	D.
	
	public class GenericExample{
	  public static void main(Strig args[]){
	  
	   Counter<String> iCounter  = new Counter("1");    // -> getting compiletime error.getting the erorr message
	   // Type parameter "java.lang.string" is not within its bound.should extends java.lang.Number.
	   iCounter.print();
	  
	  Counter<Double> dCounter  = new Counter(2.0);
	   dCounter.print();
      }
			   
	}
	
	
	Solution :
	
	public class GenericExample{
	  public static void main(Strig args[]){
	  
	   // -> getting compiletime error.getting the erorr message
	   // Type parameter "java.lang.string" is not within its bound.should extends java.lang.Number.
	   
	   Counter<Integer> iCounter  = new Counter("1");   
	   iCounter.print();
	  
	  Counter<Double> dCounter  = new Counter(2.0);
	   dCounter.print();
      }
			   
	}
	
	
	Note:
	
	If you are using Interface , here will support only extends keyword. No implements keyword. And if you are using few more interfaces use '&" 
	
		Example:
		
		public class Counter <T extends Serializable & Cloneable>
	  
	If you are using class and interface below example use, class always comes first and next will come interface.

		Example:
		
		public class Counter <T extends Number & Serializable>
		
		You can extend only one class and implements multiple interfaces.
		
		if you are using Number after interface getting compiletime error.
		
			Compile time error -> public class Counter <T extends Serializable & Number>
	
	Bounded Example 
	---------------
	        public class Counter <T extends Number> {    //  <- what ever we are passing from the class, that type we need to create the instance variable.
			    
				T t;
				
				Counter(T t){
				this.t = t;
				}
				
				public void print(){
				   System.out.println(t);
				}
			}
	
	Solution :
	
	public class GenericExample{
	  public static void main(Strig args[]){	  
	 
	   Counter<Integer> iCounter  = new Counter("1");   
	   iCounter.print();
	  
	  Counter<Double> dCounter  = new Counter(2.0);
	   dCounter.print();
	   
	   ArrayList<Object> intList = new ArrayList<>();
	   intList.add(1);
	   intList.add("1");
	   
	   // -> getting compile error, bcoz ArrayList<Object> , if you are trying to add Integer getting error.You need to explicity convert to interger here.
	   
	   //Integer i = intList.get(0);  
	   
	   Integer i = (Integer)intList.get(0);  
	   
      }
			   
	}
	
	-----------------------------------
	
	public class GenericExample{
	  public static void main(Strig args[]){	  
	  
	   print(1);
	   print("Dowlath");
      }
	  
	  private static <T> void print(T t){
	     Sytem.out.println(t);
		
			
	}
	}
	
	
		   
	// if you are using multiple values in print method how to handle. see below the syntax.
	  
	
	
	public class GenericExample{
	  public static void main(Strig args[]){	  
	  
	   print(1,2);
	   print("Dowlath","Basha");
      }
	  
	  private static <T,U> void print(T t, U u){
	     Sytem.out.println(t);
	     Sytem.out.println(u);
	}
	}
	
	
	// alsow return type , instead of void
	
	
	
	public class GenericExample{
	  public static void main(Strig args[]){	  
	  
	   print(1,2);
	   print("Dowlath","Basha");
      }
	  
	  private static <T,U> T print(T t, U u){
	     Sytem.out.println(t);
	     Sytem.out.println(u);
		 return t;
	}
	}
	
	
	// List ....
	
	public class GenericExample{
	  public static void main(Strig args[]){	  
	  
	   print(1,2);
	   print("Dowlath","Basha");
	   
	   List<Integer> intList = new ArrayList<>();
	   intList.add(1);
	   print(intList);   // <- compile time errror.  Object - Integer  differ. In that case we need to take wild card <?> 
	   
      }
	  
	  private static <T,U> T print(T t, U u){
	     Sytem.out.println(t);
	     Sytem.out.println(u);
		 return t;
	  }
	
	  private static void print(List<Object> list){	  
	    System.out.println(list);
      }
	}
	
	Solution :
	
	public class GenericExample{
	  public static void main(Strig args[]){	  
	  
	   print(1,2);
	   print("Dowlath","Basha");
	   
	   List<Integer> intList = new ArrayList<>();
	   intList.add(1);
	   print(intList);   
	   
      }
	  
	  private static <T,U> T print(T t, U u){
	     Sytem.out.println(t);
	     Sytem.out.println(u);
		 return t;
	  }
	
	  private static void print(List<?> list){	    // <- wild card...now it will work with out compiletime error.
	    System.out.println(list);
      }
	}
	


create own generic in java and use generic other programs?

Let’s break it down step-by-step with examples 👇

✅ 1. Create a Generic Class

			public class Box<T> {
				private T value;

				public void set(T value) {
					this.value = value;
				}

				public T get() {
					return value;
				}
			}
			
T is a type parameter (can be anything like T, E, K, V)

You can now create a box of any type

✅ 2. Use It in Another Program

			public class Main {
				public static void main(String[] args) {
					Box<String> stringBox = new Box<>();
					stringBox.set("Hello Generics");
					System.out.println(stringBox.get());

					Box<Integer> intBox = new Box<>();
					intBox.set(123);
					System.out.println(intBox.get());
				}
			}
✅ 3. Generic Method Example

			public class Utils {
				public static <T> void printArray(T[] array) {
					for (T element : array) {
						System.out.println(element);
					}
				}
			}
			Usage:


			public class Main {
				public static void main(String[] args) {
					String[] names = {"Alice", "Bob", "Charlie"};
					Integer[] numbers = {1, 2, 3, 4};

					Utils.printArray(names);
					Utils.printArray(numbers);
				}
			}
✅ 4. Generic Interface Example

			public interface Calculator<T> {
				T add(T a, T b);
			}
			
Implementation:


			public class IntegerCalculator implements Calculator<Integer> {
				@Override
				public Integer add(Integer a, Integer b) {
					return a + b;
				}
			}
Use it:

			public class Main {
				public static void main(String[] args) {
					Calculator<Integer> calc = new IntegerCalculator();
					System.out.println(calc.add(10, 20));
				}
			}
			
💡 Summary
✅ Use <T> to define generic types

✅ Reuse logic for different data types

✅ Keeps your code type-safe, clean, and reusable

