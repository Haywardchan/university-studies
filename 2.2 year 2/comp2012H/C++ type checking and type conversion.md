#### Type Checking and Coercion 

For most languages, data types have to be matched during an operation ⇒ **type checking**. However, sometimes, a type is made compatible with a different type ⇒ **coercion**.

Coercion is the automatic conversion of the data type of operands during an operation. 
	Example: 3 + 2.5 ⇒ int + double.
	The C++ compiler will automatically change it to 3.0 + 2.5 ⇒ double + double 
Thus, the integer 3 is coerced to the double 3.0. 
Example: Convert a Small Character to Capital Letter 
```C++
char small_y, big_y; cin >> small_y; // Character in small case 
big_y = small_y + 'A' - 'a'; // Character in big case
```
 Here big y, small y, ’A’, and ’a’ are “coerced” by “promoting” it to int before addition. 
 The result is converted back (or coerced) to char.
 
##### priority rules for the Usual Arithmetic Conversions for Binary Operations (Simplified Version)
If either operand is of type long double, convert the other operand also to long double. 
If either operand is of type double, convert the other operand also to double.
If either operand is of type float, convert the other operand also to float. 
Otherwise, the integral promotions shall be performed on both operands. 
- Similar rules are used for integral promotion of the operands. 
- Compute using integer arithmetic.

##### Automatic Type Conversion During Assignment 
Examples 
```C++
float x = 3.2; // Initialize x with 3.2 by assignment 
double y = 5.7; // Initialize y with 5.7 by assignment 
short k = x; // k = ? 
int n;
n = y; // n = ? 
```
Since float|double can hold numbers bigger than short | int, the assignment of k and n in the above program will cause the compiler to issue a warning — not an error. 
Compiler Warnings 
```C++
a.cpp:9: warning: converting to ‘short int’ from ‘float’ 
a.cpp:11: warning: converting to ‘int’ from ‘double’
```
- A narrowing conversion changes a value to a data type that might not be able to hold some of the possible values. 
- A widening conversion changes a value to a data type that can accommodate any possible value of the original data.
- C++ uses truncation rather than rounding in converting a float | double to short | int | long
#### Manual Type Conversion (Casting)
$$static\_cast<datatype>(value)$$
No more warning messages on narrowing conversion. 
```C++
int k = 5, n = 2; 
float x = static_cast(n)/k; 
float y = n/static_cast(k);
float z = static_cast(n)/static_cast(k);
```
