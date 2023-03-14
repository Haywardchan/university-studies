```java
'' is for char
"" is for String
```
```java
instruction = "Press the \"Compile\" button to compile your source code";
quote = '\'';
```
by adding \, double quotes or single quotes can be included in the string / char.
```java
// Convert the string to an integer 
int integer_number; 
integer_number = Integer.parseInt(number); 
// Calculate the square of the number 
int square; square = integer_number * integer_number; 
// Show the number 
System.out.print("The square of the number is: "); System.out.println(square);
```
the parseint function convert number to an integer variable
**Float.parseFloat** or **Double.parseDouble** to convert the string to a **float** variable or a **double** variable respectively.

the .length() function can be used to fetch the length of a String.
```java
// Ask for the name 
System.out.print("What is your name? "); 
// Get the name input 
String name; 
Scanner scanner = new Scanner(System.in); name = scanner.next();
// Show the length of the name 
System.out.println("Your name is " + name.length() + " characters long.");
```

the .charAt() function can fetch a particular position in a String.
![[Pasted image 20220418180819.png]]
```java
// Use a char variable 
char letterU; 
// Store the second character into the variable 
letterU = name.charAt(1);
```
the last character is at the position of String.length()-1