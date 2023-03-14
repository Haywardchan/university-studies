$$<variable>=<value>;$$
"=" sign is used to assign a value to a variable and its called as the **assignment operator**

##### Arithmetic operators
![[Pasted image 20220826005515.png]]

##### modulus arithmetics
mod is used to get the remainder in an integer division. 
mod(17, 5) = 17 mod 5 = 17%5 = 2
- -ve divisor is supported in C++

if quotient a/b is representable in the type of the result, then the following holds:
$$a=(a/b)*b+a\%b$$
$$\therefore a\%b=a-(a/b)*b$$

##### Pre- and Post- Increment and decrement
unary increment operator   x++ Vs ++x
unary decrement operator   x-- Vs --x
For ++x, --x:
add/ minus 1 to x and further operate the value
For x++, x--:
use current value for operation and further changing the value of x
I.e
```C++
cout << ++x; /* same as */ x = x + 1; cout << x;
cout << x++; /* same as */ cout << x; x = x + 1;
```
++++++x add 3 to x and return x value afterwards
```C++
#include /* File: inc-mod.cpp */ 
using namespace std; 
int main() 
{ 
int x = 100, y = 100; // Variable definitions and initialization 
int a = 10, b = 10, c = 10, d = 10; 
cout << ++x << "\t"; cout << "x = " << x << endl; // Pre-increment 
cout << y++ << "\t"; cout << "y = " << y << endl; // Post-increment 
a = ++b; cout << "a = " << a << "\t" << "b = " << b << endl; 
c = d++; cout << "c = " << c << "\t" << "d = " << d << endl; 
cout<< 17%5 << endl; // Trickiness of the mod function 
cout << (-17)%5 << endl; 
cout << 17%(-5) << endl; 
cout << (-17)%(-5) << endl;
return 0; 
}
```

##### Shorthand assignment operators
![[Pasted image 20220826011726.png]]

##### Precedence and Associativity
![[Pasted image 20220826011801.png]]
![[Pasted image 20220826022942.png]]
- Precedence rules decide which operators run first.
- Associativity decides the grouping of operands with operators of the same level of precedence.
- extra parentheses to enforce the order of operations.

##### Casading assignment
assign multiple values at once
```C++
int w, x, y, z;
y = w = 5; // Same as y = (z = 5);
w = x = y + z; // Same as w = (x = (y+z));
```

##### Expression Vs Statement
expression has a value which is the result of some operation(s) on its(theirs) operands.
- value exist
I.e 4 \ x-y \ 2-a-(b$*$c)
statement is a sentence that acts as a command.
- no value
- ends with ;
I.e input output statements cin>>x; cout>>x;
assignment and variable definition x = 5; int x;

##### Relational Operators
![[Pasted image 20220826022423.png]]

##### logical operators
![[Pasted image 20220826022821.png]]