##### Variables
putting a value into a variable, is called an _assignment_. Thus, we call the **=** operator, the _assignment operator_.

we can separate this code:
```java
/* The following code calculates the final grade which includes: - the 6 labs - the midterm exam - the final exam, and - the attendance record */ finalgrade = (lab1 + lab2 + lab3 + lab4 + lab5 + lab6) / 6.0 * 0.2 + 
// the labs contribute 20% of the final grade 
			midtermexam * 0.2 + // the midterm exam contributes 20% of the final grade 
			finalexam * 0.5 + // the final exam contributes 50% of the final grade 
			attendance * 0.1; // the attendance record contributes 10% of the final grade
```
into
```java
/* This statement calculates the lab average */ 
labs = (lab1 + lab2 + lab3 + lab4 + lab5 + lab6) / 6.0; 
/* This statement calculates the final grade */ 
finalgrade = labs * 0.2 + // the labs contribute 20% of the final grade 
			
			midtermexam * 0.2 + // the midterm exam contributes 20% of the final grade 
			finalexam * 0.5 + // the final exam contributes 50% of the final grade 
			attendance * 0.1; // the attendance record contributes 10% of the final grade
```

we can store things into variables in the following forms:
```java
luckynumber=5;//number
name="Lucky"//text
```
However, u have to declare the datatype before assigning variable values:
```java
int luckynumber;
String name;
```
![[Pasted image 20220418173614.png]]
this would happen if variables are not declared before using it.

>A variable name must start with a letter, a dollar sign or an underscore (i.e., **_** ), followed by any combination of letters, digits, dollar signs or underscores. You cannot use a space inside a variable name. Moreover, you cannot use a word that Java uses for other purposes. For example, you cannot call a variable 'int' because 'int' has been used by Java already.

common [[data types]] is introduced here.
![[Pasted image 20220418173950.png]]
this would happen if the data type is incompatible.

we sometimes have to convert the data types using codes:
```java
double length; 
int area; 
length = 10.5; 
area = length * length;
area = (int) (length * length); //this line of code
```
What the above line of code does is to, first, compute the result of **length * length**. This gives you **110.25**. The number **110.25** is then converted to an integer by the type casting operator **(int)**. The **int** inside the brackets means you want to convert whatever comes after **(int)** to an integer. Converting **110.25** to an integer gives you **110** (throwing away the fractional part). Finally, the number **110** is stored in the **area** variable. Since **110** is an integer, there is no incompatible types error in this situation.
##### Operators
**=** is the assignment operator, **+** and * are the arithmetic operators for addition and multiplication.
![[Pasted image 20220418174442.png]] (Arithmetic operators)
```java
greeting = "Good" + " " + "morning" + "!";
luckynumber++;
luckynumber--;
```
 you know that mathematically 5 divided by 2 is 2.5. And you may expect that the expression **5 / 2** in Java will also give you 2.5. However, **5 / 2** in Java is not 2.5! Instead, It gives you a result of 2. What's happening here? This type of division is called _integer division_. Integer division means that the result of a division between two integers is also an integer. So the result of 5 divided by 2 is 2.5. Changing 2.5 to an integer gives you 2.
 
 you will have to change at least one of the operands to a floating number. To do that you add a decimal point after the number. For example, both **5.0 / 2** and **5 / 2.0** give you a result of 2.5. If you use integer variables as the operands you will need to use **(double)** to convert the value to a double before the division.
 ![[Pasted image 20220418174756.png]]![[Pasted image 20220418174840.png]]
 (Comparison Operators & conditional operators)
 ```java
 a==b
 number > 5 && number < 10
 !(number > 10)
```
As you can see, a pair of parentheses has been used to enclose the expression **number > 10** before applying negation. This makes sure that the comparison **number > 10** is evaluated first before the negation operator. The order of evaluations of a combination of operators is called _operator precedence_.