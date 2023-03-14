Output:
```java
System.out.println();//this will produce a empty line
System.out.print();//this is different from the println function
```
we can adjust the output using the $\t$ operator
```java
System.out.print("Lab average\t");
System.out.print(labs);
System.out.println("\t(20%)");
System.out.print("Midterm exam\t"); 
System.out.print(midtermexam); 
System.out.println("\t(20%)"); 
System.out.print("Final exam\t");
System.out.print(finalexam);
System.out.println("\t(50%)");
System.out.print("Attendance\t"); 
System.out.print(attendance);
System.out.println("\t(10%)");
System.out.println(); 
System.out.print("Final grade\t"); 
System.out.println(finalgrade);
```
Input:
You have learned that **System.out** represents the screen output. And you use **System.out** to print things on the screen. A similar name, **System.in**, represents the keyboard input from the user. That means we get keyboard input from the user by using **System.in**. However, getting input through **System.in** is not as trivial as using a **print** or **println** command on **System.out**.
```java
import java.util.Scanner;
Scanner scanner = new Scanner(System.in);
String inputstring = scanner.next();//read a string from this code
System.out.println("Hello, " + inputstring + "!");//print read subject
```
**the .next function can only pick up until an space or an Enter key in the text
