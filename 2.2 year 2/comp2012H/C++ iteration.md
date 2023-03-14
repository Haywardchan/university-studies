#### While loop (Statement)
$$while(<bool>)\{<stms>\}$$
Example: Factorial using while Loop
```C++
#include /* File: while-factorial.cpp */ 
using namespace std; /* To compute x! = x(x-1)(x-2)...1, where x is a non -ve integer */ 
int main() { 
int factorial = 1; 
int number; 
cout << "Enter a non-negative integer: "; cin >> number;
while (number > 0) {
factorial *= number; // Same as: factorial = factorial*number 
--number; // Same as: number = number-1 
} 
cout << factorial << endl; 
return 0; 
}
```

#### Do While loop (Statement)
$$do\space\{<stmts>\}\space while\space(<bool>);$$
- do while loop will be executed at least once

Example: Factorial using do-while Loop
```C++
#include /* File: do-factorial.cpp */ 
using namespace std; // Compute x! = x(x-1)(x-2)...1; x is non -ve 
int main() {
int factorial = 1, number;
cout << "Enter a non-negative integer: "; cin >> number;
if (number > 0) { 
	do { factorial *= number; 
		// Same as: factorial = factorial*number 
		--number; // Same as: number = number-1 
		} while (number > 1); 
	} 
	cout << factorial << endl; 
	return 0; 
}
```

#### For Loop (Statement)
$$for(<for.init.var>;<bool.exp>;
<post-processing>)\{<stmts>\}$$

#### Factorial using for Loop
```C++
#include /* File: for-factorial.cpp */ 
using namespace std; 
/* To compute x! = x(x-1)(x-2)...1, where x is a non -ve integer */ 
int main() { 
int factorial = 1; 
int number; 
cout << "Enter a non-negative integer: "; 
cin >> number; 
for (int j = 1; j <= number; ++j) // Set up a counter to iterate 
factorial *= j; 
cout << number << "! = " << factorial << endl; 
return 0;
}
```

Remarks on For Statement
```C++
for (int j = 1; j <= number; factorial *= j++) ;
//compact coding can be used.
```

### How to choose which Loop to use?
#### for loop : 
- When you know how to specify the required number of iterations. 
- When the counter variable is also needed for computation inside the loop. 
- e.g. To compute sums, products, and to count.
#### while loop : 
- You want to repeat an action but do not know exactly how many times it will be repeated. 
- The number of iterations is determined by a boolean condition.
#### do-while loop : 
- The associated actions have to be executed at least once. 
- Otherwise, do-while and while are used in similar situations.

#### Nested Loops:
```C++
#include /* File: multiplication-table.cpp */ 
#include // a library that helps control input/output formats using namespace std; 
int main() { 
// To print out products of j*k where j, k = 1,...,10 
for (int j = 1; j <= 10; ++j) 
	{
		for (int k = 1; k <= 10; ++k) // Reset k=1 for each j. Why? 
			cout << setw(4) << j*k; 
			// Set the length of output field to 4 
			cout << endl; 
		} 
		return 0; 
	}
```

### Break and Continue
- A **break** causes the **innermost enclosing loop** to exit immediately
![[Pasted image 20220827020349.png]]
- A **continue** causes the **next iteration** of the enclosing loop to begin.
![[Pasted image 20220827020403.png]]

#### Difference between break and continue
![[Pasted image 20220827020455.png]]

