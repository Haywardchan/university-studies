As you know from other programming languages, instead of a single value, you can also store a collection of things as a data structure in a single variable. For example, in Python, you can use a list to store many things. In C, you can use arrays. Similar to C, in Java, we store a collection of things using arrays.

Let's look at a simple Java array:
```java
String[] greeting = { "how", "are", "you", "?" };
```
The data type **String** indicates that you want to store strings and the **[]** following the data type means the variable is a collection, i.e. an array. The strings that you want to store are the four strings given between the pair of braces. The size of an array, i.e. the number of things you are going to store in the array, is automatically determined by the number of items you put inside the pair of braces. In the above case, the size of the array is 4.

Alternatively, you can create an empty array first, before putting any value inside the array. Here is an example:
```java
String[] greeting = new String[4]; 
greeting[0] = "how"; 
greeting[1] = "are";
greeting[2] = "you";
greeting[3] = "?";
```
When you create an array you need to give exactly how many items you are going to store in the array, by putting the number between a pair of brackets. In this example, **new String[4]** means creating an empty array with four items.
```java
String[] names = new String[5]; 
names[5] = "Nobody";
```
as the index array is out of range, error ('array index out of bounds' error) occurs:
![[Pasted image 20220418211703.png]]

##### two dimensional arrays
It is two dimensional because we use one index to get an array out of the 'outer' array and another index to get the items out of the 'inner' array.

Here is an example:
```java
int[][] magicsquare = { { 4, 9, 2 }, { 3, 5, 7 }, { 8, 1, 6 } };
```
Since there are three things inside the outer pair of braces. The first dimension of the array is 3. And there are three items inside each inner pair of braces. Therefore the second dimension is also 3. Combining both gives us a 3x3 array.

To read a value from a 2D array we use two indices, one for the row and another for the column. Here are some examples.
```java
System.out.println(magicsquare[1][1]); // print 5 at the center of the square
System.out.println(magicsquare[2][1]); // print 1 at the bottom of the square
```
we can generate empty 2 dimensional arrays:
```java
int[][] bigarray = new int[4][5];
```
we can verify whether our code is correctly placed or not:
```java
// Print the sum of the numbers in the rows 
for (i = 0; i < 3; i++) { 
	System.out.print("The sum in row " + i + " is: "); 
	System.out.println(magicsquare[i][0] + magicsquare[i][1] +
	magicsquare[i][2]); 
}
// Print the sum of the numbers in the columns 
for (i = 0; i < 3; i++) { 
	System.out.print("The sum in column " + i + " is: ");
	System.out.println(magicsquare[0][i] + magicsquare[1][i] + 
	magicsquare[2][i]);
}
// Print the sum of the numbers in the diagonals 
	System.out.print("The sum in the downward diagonal is: "); 
	System.out.println(magicsquare[0][0] + magicsquare[1][1] + 
	magicsquare[2][2]); 
	System.out.print("The sum in the upward diagonal is: "); 
	System.out.println(magicsquare[2][0] + magicsquare[1][1] + 
	magicsquare[0][2]);
```