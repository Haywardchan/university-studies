objects have two kinds of characteristics: _attributes_ and _behaviours_. Let's take a dog as an example. A dog has _attributes_ such as colour, weight, name, date of birth. It has _behaviours_ such as eating, barking and running.
 In computer science we usually call the definition of an object a _class_. A class has its own attributes and behaviours. Behaviours of an object is usually called _methods_.
 
 Java is a language specifically designed for object-oriented programming. _Almost_ everything in the Java language is an object.
For instance, you can use the method **.next()** from a scanner and you can use the method **.length()** from a string.
```java
// Create a scanner object 
Scanner scanner = new Scanner(System.in); 
// Use the next() method of the scanner object to get a string from the user 
String name = scanner.next(); 
// Use the length() method to show the length of the name object 
System.out.println(name.length());
```
#### !!!
There are some 'things' in Java which are not objects though. Some of the data types we have used like **int**, **char** and **double** are not objects. They contains only a single value. They don't have attributes and methods. You can use the comparison operator == to directly compare the values of these data types. However, you cannot use the == operator to compare objects because objects do not contain a single value. That's why we cannot use == for strings (remember we use **.equals()**) because strings are objects.

```java
/** * This is the definition of the Dog2 class. */
public class Dog2 { 
					int weight = 5; // the weight of the dog 
				   // Ask the dog to bark 
				   void bark() { 
					   System.out.println("Woof!"); 
				   } 
				}
```
 if you have a class in your project, apart from the object bench, you can create an instance of the class using the **new** keyword in code. For example, we can create a new dog of the **Dog** class using the following line of code:
 ```java
 Dog lemon = new Dog();
```
through adding weight attribute:
```java
/** * This is the definition of the Dog3 class. */ 
public class Dog3 { int weight = 5; // the weight of the dog 
				   // Ask the dog to bark 
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
#### [[class constructor]]
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
##### [[the main method]]

Most of the projects that you have downloaded from the first two weeks of the course has a **main** method. We give you the **main** method so that you can use it to start running the project.
```java
	/** * This is the first program in the Java bridging course. */ 
public class HelloWorld { 
	/** * 
		The main method of the program. 
	*/ 
	public static void main(String[] args) { 
		System.out.println("Hey, how are you doing?"); 
	}
}
```
The **main** method is defined inside this class. It takes an input parameter called **args**. The parameter is an array, as shown by the brackets **[]**, which we will discuss in the next lesson. The method does not return anything because it has a data type of **void**. Finally, the method is accessible from every other part of the code, indicated by the word **public**. So what is the meaning of **static**? **static** changes the method to a static method, which means that you can run it without creating an instance of the class containing the method.

Typically when you define a method inside a class you will need to create an instance of the class **first** before running the method. For example, we have to create a dog instance before we use the **bark** method in the previous lesson, as shown below:
```java
Dog2 lemon = new Dog2(); 
lemon.bark();
```
However, sometimes you may want to run some code without using any object. In that situation you will put the code in a static method and then run the code without creating any object.

When you give a program to Java the first thing Java looks for is the **main** method. Once Java finds the **main** method it will start the program by running this method. Therefore, the **main** method is the starting point of a Java program.