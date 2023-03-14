#### Identifiers
$$f(x)=x^2+c$$
- name of **function**, **variable**, **constant**

#### rule of making up identifier names
- first character cannot be a **digit (0–9)**
- [[Reserved words]] are not allowed
- C++ **case-sensitive**
- **meaningful** names
- use '$\_$' to separate **several words**

#### Variables
- memory location for a value that we can write to, retrieve from, and manipulate
- must be declared and/or defined before it can be used
- compiler allocates memory with corresponding datatype size for it 
$$<datatype><identifier>;$$
I.e
```C++
int radius = 10, sum = 0;
int radius, num_of_words; 
char choice, gender, pass_or_fail;
```
- does not require compilers to initialize variables
- initial contents may be garbage before defining

An example of 2 number addition using variables:
```C++
#include /* File: add-var.cpp */ 
using namespace std; 
int main() // Program's entry point { 
int x, y; // Define 2 variables to hold the int values to add 
cin >> x; // You may also shorten the 2 statements into one: 
cin >> y; // cin >> x >> y; 
cout << x << " + " << y << " = " << x+y << endl; 
return 0; // A nice ending 
}
```