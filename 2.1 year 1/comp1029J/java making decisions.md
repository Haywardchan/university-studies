the if statement:
```java
// Get the total score 
String inputscore; 
System.out.print("What is the total score of your course? "); 
Scanner scanner = new Scanner(System.in); 
inputscore = scanner.next(); 
// Convert the score to a number 
int score = Integer.parseInt(inputscore); 
// Print a message if the score is excellent 
if (score > 80) { System.out.println("Excellent! You have done a great job!"); }
```
the if-else statement:
```java
// Print a message based on the score value 
if (score > 80) { 
	System.out.println("Excellent! You have done a great job!"); 
} 
else { 
	System.out.println("Good job! You can do better next time!");
}
```
The code becomes tighter when the braces are not used. However, if a block of code contains more than one line of code, you must use braces to enclose the code.
more than 1 conditions:
```java
// Handle the A grade 
if (score >= 80) { System.out.println("A"); } 
// Handle the B grade 
else if (score >= 60) { System.out.println("B"); } 
// Handle the C grade 
else if (score >= 40) { System.out.println("C"); } 
// Handle the D grade 
else { System.out.println("D"); }
```
the [[switch statement]] can be used in this situation as an alternative multiple if statement:
```java
// Get the route number 
System.out.println("HKUST routes: 91, 91M, 792"); System.out.println(); 
System.out.print("Please enter the route you want to know: ");
String number; 
Scanner scanner = new Scanner(System.in);
number = scanner.next(); 
// Show the information of route 91 
if (number.equals("91")) { 
	System.out.println("Clear Water Bay <> HKUST <> Diamond Hill"); 
	} 
	// Show the information of route 91M 
	else if (number.equals("91M")) { System.out.println("Po Lam <> HKUST <> Diamond Hill"); } 
	// Show the information of route 792 
	else if (number.equals("792")) { System.out.println("Sai Kung <> HKUST <> Tseung Kwan O"); } 
	// No such route 
	else { System.out.println("Bus route does not exist"); }
```
turning it into:
```java
switch (number) { 
		case "91": // Show the information of route 91
			System.out.println("Clear Water Bay 
								<> HKUST <> Diamond Hill"); 
			break; 
		case "91M": // Show the information of route 91M 
			System.out.println("Po Lam <> HKUST <> Diamond Hill"); 
			break; 
		case "792": // Show the information of route 792 
			System.out.println("Sai Kung <> HKUST <> Tseung Kwan O"); 
			break; 
		default: // No such route 
			System.out.println("Bus route does not exist"); }
```