
```java
System.out.println("Hello!");
```
>Notice that both the above examples have a **;** (semi-colon) at the end of the statement. The semi-colon is a placeholder to indicate that is the end of the statement.

>When you write Java statements small and big letters do not mean the same thing. For example, the small letter **a** and the big letter **A** are not treated as the same letter in Java.

the spacing in java is flexible in most of the cases:
```java
System.out.println("Hello!"); 
System.out.println( "Hello!"); 
System.out.println("Hello!" );
System.out.println("Hello!") ;

\\the statements above are all identical
```
however, these 2 are not appropriate:
```jave
System.out. println("Hello!");
System.out.println("H e l l o!") ; \\this is different from "Hello!"
```
multiple lines could be used for better visualization:
```java
finalgrade=(lab1 + 
			lab2 + 
			lab3 + 
			lab4 + 
			lab5 + 
			lab6) / 6.0 * 0.2 + 
			midtermexam * 0.2 + 
			finalexam * 0.5 + 
			attendance * 0.1;
```
First program 'Hello world':
```java
/** * This is the first program in the Java bridging course. */ 
public class HelloWorld { 
/** * The main method of the program. */ 
	public static void main(String[] args)
	 { System.out.println("Hey, how are you doing?"); 
	 } 
}
```
Identation should be used for readability and manageability of the code
```java
if (hour < 12) { 
	System.out.println("Good morning!");
} 
else { 
	System.out.println("Good afternoon!"); 
}
```

[[java comments]] can be written in 2 forms:
$/*comment*/$ or //comment
```java
/*I am a comment*/
//I amd a comment
```