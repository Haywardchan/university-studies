### Basic Function Syntax
Function definition
$<return.type><func.name>(<formal.parameter.list>)\{<func.body>\}$
Function Call
$<function.name>(<actual.parameter.list>)$

The function name “main” is reserved; you must define it, and define it exactly once. 
- Recall that each program can only have one “main( )” function. 
- When a program is run, the shell — command interpreter of the operating system — looks for the “main( )”function and starts execution from there.

### Formal Parameter List & Actual Parameter List
```C++
/* max function definition */ 
int max(int a, int b) { return (a > b) ? a : b; } 
/* max function call */ 
cout << max(5, 8) << endl;
```

$<formal.parameter.list>$appears in the **function definition**, and is basically a list of **variable declarations** separated by **commas**.

$<type_1 variable_1>, <type_2 variable_2>, ..., <type_N variable_N>$

$<actual.parameter.list>$ appears in a **function call**, and is a list of **objects** separated by **commas** that are passed to the called function.

$<object_1>, <object_2>, ..., <object_N>$

one-to-one correspondence between **actual parameters** and the **formal parameters**

the following **initializations** are performed during the function call:
$< type_1\space variable_1 >= object_1,$ 
$< type_2\space variable_2 >= object_2,$ 
. . . 
$< type_N\space variable_N >= object_N$

- strongly typed programming language
- the data types of an actual parameter and its corresponding formal parameters must be the same or “matched”.
- type checking will be performed by C++ compiler
- Exception: unless an automatic type conversion — coercion — can be done, just like normal initialization or assignment of an object to a variable of a different type. (More about that later.)

$<return.type><func.name>(<formal.parameter.list>)$
is called as the function header, the rest is the function body:
which consists of
- constant declaration
- variable declarations and definitions
- other C++ statements
- return statement
- ( could be empty )
- { } must exist

### Return Type

the **returned obect** of function may be:
- signal to tell caller the status
- result of the computation
- a new object crearted by the function e.g. a new window

the **return-type** specified the data type od the single returned object
the return-type can be any of the C++ built-in data type, except the array type.

the return statement generally returns 2 things to the caller:
- program control (stop running function and take back the control)
- an object/ value

The value of < expression > in the return statement should have the same type as the <$return.type$>. Or, if it can be converted to the <$return.type$> by coercion, otherwise it will be a compilation error.

Example: max
```C++
#include /* File: max.cpp */ 
using namespace std; /* To find the greater value between x and y */ 
int max(int a, int b) { 
if (a > b) 
	return a; 
else 
	return b; 
} // Question: can you write with only 1 return statement? 
int main() { 
int x, y; 
cout << "Enter 2 numbers: "; 
cin >> x >> y; 
cout << "The bigger number is " << max(x, y) << endl; 
return 0; 
}
```

Void: a New Type in [[C++ Data types]]

##### Remark: Why Function?
- When you have several segments of codes doing similar things, then they are good candidates for a function. 
- A function allows “write-once-call-many”: you only write it once they can be called many times in the same program with the same or different arguments.
- Functions make programs easier to understand.
- Functions make programs easier to modify.
- Functions allow reusable code. (e.g. log, sqrt, sin, etc.) 
- Functions separate the concept (what is done) from the implementation (how it is done).
- The last two remarks lead to the creation of binary libraries which are a set of compiled functions. These libraries can be shared, yet the users do not know their implementation.