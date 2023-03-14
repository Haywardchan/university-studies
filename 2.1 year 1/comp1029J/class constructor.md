You can create a special method, called _constructor_, for a class. Here, we add a constructor for the new **Dog4** class:
```java
/** * This is the definition of the Dog4 class. */ 
public class Dog4 { 
			int weight; // the weight of the dog 
			
			// The constructor of the class 
			public Dog4(int initialWeight) { 
				weight = initialWeight; 
			} // Ask the dog to bark 
			void bark() { 
				System.out.println("Woof!"); 
			} // Feed the dog with a certain amount of food 
			void feed(int food) {
				 weight = weight + food; 
			 } // Get the current weight of the dog 
			int getWeight() { 
				 return weight; 
			 } 
			 }
```
```java
// The constructor of the class 
public Dog4(int initialWeight) {
	weight = initialWeight;
}
```
the constructor does not have a data type and the name of the method is the same as the name of the class, in this case, **Dog4**. The constructor is automatically run when an instance of the class is created (i.e. constructed). That means it will only be run once for each object and you don't explicitly call the method in your code. Typically a constructor is used to do some initializations for the class. For example, the above constructor of the **Dog4** class initializes the **weight** attribute using the given parameter.

you can give the initial weight by this line of code:
```java
Dog4 cookie = new Dog4(10);
```