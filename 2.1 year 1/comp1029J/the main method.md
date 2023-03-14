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