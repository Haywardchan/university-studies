There are different kinds of loop structure in various programming languages. The common ones are for loops and while loops. Java allows you to use three kinds of loops:

1.  For loops
2.  While loops
3.  Do while loops

you can do **for loops** in other programming languages such as:
```python
for i in range(1,11):
	print(i)
```
```excel vba
For Index = 1 To 10 
	MsgBox Index 
Next
```
In java, for loops is like this:
```java
for (i = 1; i < 11; i++) { 
	System.out.println(i); 
}
```
>There are three parts, containing inside a pair of brackets, in the **for** command. The first part is the initialization. In the above example, the initialization of the loop is **i = 1**. That means at the start of the loop, the variable **i** is assigned with the value of 1. The second part of the for loop is the loop condition. In the example, the loop condition is **i < 11**. The loop will keep on running the loop body repeatedly until the loop condition is false. In the example, the for loop keeps on running the loop body when **i** is smaller than 11. The third part in the command is the increment. In the example, the increment is **i++**. The increment is run everytime the loop body finished execution once.

for **while loops**, we only require one input--the loop condition, thus is more flexible than **for loops**:
```java
i = 1; 
while (i < 11) {
	System.out.println(i); i++; 
}
```
While loops are useful when there is no fixed increment for running the loop:
```java
// Show the question 
System.out.println("I am handsome. Do you agree?"); System.out.print("Answer (Y/N): "); 
// Ask for the answer 
String answer;
Scanner scanner = new Scanner(System.in); 
answer = scanner.next(); 
// Ask the question if the answer is not 'Y' 
while (!answer.equals("Y")) { 
	System.out.println("Can't hear you. Please answer again."); 
	System.out.print("Answer (Y/N): ");
	answer = scanner.next(); 
} 
System.out.println("That's right!");
```

for **do while loops**:
the condition is evaluated **after** running the loop content. Therefore, the loop body will be run at least once even if the loop condition is false at the very start. Apart from the timing of evaluating the loop condition, while loops and do while loops are the same.
```java
// Prepare the scanner 
Scanner scanner = new Scanner(System.in); 
// Keep asking the question if the answer is not 'Y' 
String answer; do { 
// Show the question 
		System.out.println("I am handsome. Do you agree?");
		System.out.print("Answer (Y/N): "); 
// Ask for the answer 
		answer = scanner.next(); 
} while (!answer.equals("Y"));
System.out.println("That's right!");
```
