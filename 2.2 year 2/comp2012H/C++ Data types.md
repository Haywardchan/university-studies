![[Pasted image 20220801182626.png|500]]
size of data types can be found using **sizeof**:
![[Pasted image 20220801182710.png|600]]
#### Integer
type names: short (int), int, long (int), long long (int)
size is depended on the CPU and compiler
![[Pasted image 20220801182921.png]]
Integral is divided as signed (default) and unsigned version

#### Floating-point
Represent real numbers and very large integers
	**float** is for single-precision numbers
	**double** is for double-precision numbers
[precision] is affected by the number of decimal places, the more the places, the higher the precision.
Under Scientific notation a number consist of: (I.e. 5.16E-02)
- mantissa: 5.16 -->higher precision
- exponent: -2 -->larger real number

#### Integer division (div) Vs floating-point division
10/2 = 5   10.0/2.0 = 5.0 
9/2 = 4      9.0/2.0 = 4.5 
4/8 = 0      4.0/8.0 = 0.5

#### Characters (1 byte)
Examples: ’a’, ’b’, ’4’ 
Represent a single character by delimiting it in single quotes. 
For special characters, use the escape character $\textbackslash$. 
e.g.
```C++
’\t’ = tab 
’\n’ = newline 
’\b’ = backspace 
’\0’ = null character
```

C++ type name: char
![[Pasted image 20220801184921.png|400]]

Char can be interpreted as an integer

#### Character Strings 
Examples: “hkust”, “How are you?”, “500 dollars” 
Character strings are not a basic data type in C++. 
They are sequences of basic char data.

#### Boolean Data Type 
Type name: bool. Used to represent the truth value, true or false of logical (boolean) expressions like:
	a > b        x + y == 0      true && false 
Since C++ evolves from C, C++ follows C’s convention: 
	zero may be interpreted as false. 
	non-zero values may be interpreted as true. 
However, since internally everything is represented by 0’s and 1’s,
	 false is represented as 0. 
	 true is represented as 1. 
 Even if you put other values to a bool variable, 
 its internal value always is changed back to either 1 or 0.
```C++
 #include <iostream> /* File: boolalpha.cpp */ 
 using namespace std;
  int main() { bool x = true; bool y = false; 
  // Default output format of booleans 
  cout << x << " && " << y << " = " << (x && y) << endl << endl; 
  
  cout << boolalpha; // To print booleans in English 
  cout << x << " && " << y << " = " << (x && y) << endl << endl; 
  
  cout << noboolalpha; // To print booleans in 1 or 0 
  cout << x << " && " << y << " = " << (x && y) << endl; 
  return 0; 
  }
```

#### Underflow and Overflow in Integral Data Types 

**Overflow**: 
occurs when a data type is used to represent a number larger than what it can hold. 
e.g. I if you use a short int to store HK’s population. 
when a short int has its max value of 32767, and you want to add 1 to it. 

**Underflow**: 
occurs when a data type is used to represent a number smaller than what it can hold. 
e.g. I use an unsigned int to store a -ve number.

#### Underflow and Overflow in Floating-Point Data Types 

**Underflow**: 
when the -ve exponent becomes too large to fit in the exponent field of the floating-point number. 

**Overflow**: 
when the +ve exponent becomes too large to fit in the exponent field of the floating-point number. 
To prevent these from happening, use double if memory space allows. 
In fact, all floating literals `(e.g., 1.23)` is treated as double 
unless explicitly specified by a suffix `(e.g., 1.23f)`.

##### User-defined enum type
$$enum \space new.datatype\{identifier1[=value1],\space identifier2[=value2]\}$$
i.e.
```C++
enum weekday { MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY }; // 0,1,2,3,4,5,6 
enum primary_color { RED = 1, GREEN, BLUE }; // 1,2,3 
enum bloodtype { A, B, AB = 10, O }; // 0,1,10,11
```
- objects are treated as integer constants
- hold a finite set of symbolic objects.
- By default, the first object is given the value zero, then each subsequent object is assigned a value one greater than the previous object’s value
- It can be used in [[C++ switch]] statements

example of mixing color:
```C++
#include /* File: enum-colors.cpp */ 
using namespace std; int main() 
{ // Declare color variables immediately after the enum definition 
enum color { RED, GREEN, BLUE, YELLOW, CYAN, PURPLE } x, y; 
int xint, yint; // Input variables for the color variables 
cin >> xint >> yint; 
x = static_cast(xint); // Convert an int to a color quantity 
y = static_cast(yint); // Convert an int to a color quantity 
if ( (x == RED && y == GREEN) || (y == RED && x == GREEN) ) 
	cout << YELLOW << endl; 
else if ( (x == RED && y == BLUE) || (y == RED && x == BLUE) ) 
	cout << PURPLE << endl; 
else if ( (x == GREEN && y == BLUE) || (y == GREEN && x == BLUE) ) 
	cout << CYAN << endl; 
else 
	cerr << "Error: only support mixing RED/GREEN/BLUE!" << endl; return 0;
 } // Check what is really printed out
```

##### Void Type 
introduced in [[C++ Function Basics]]
void meaning *nothing, emptyness*
- a function that returns nothing back to caller has a return type od void.
```C++
//leave the <formal-parameter-list> empty
int fcn_example( ) { . . . }
//put the <formal-parameter-list> as void
void print_hkust(void) { cout << ”hkust” << endl; }
```
under void type:
return;//return to the caller
exit;//exit whole program

