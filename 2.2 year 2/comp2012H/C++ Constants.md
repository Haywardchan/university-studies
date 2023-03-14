#### Literal Constants
- fixed value/ permanent values that cannot be modified

char constants:      ‘a’, ‘5’, ‘\n’ 
string constants:   “hello world”, “don’t worry, be happy” 
int constants:        123, 456, -89 
double constants: 123.456, -2.90E+11

#### Symbolic Constants
- A named constant with an identifier name
- by convention, constant identifiers are written in **capital letters**
- declared before it can be used
$$const<\text datatype><\text identifier>=<\text value>$$

I.e. 
```C++
const char BACKSPACE = '\b'; 
const float US2HK = 7.80; 
const float HK2RMB = 0.86; 
const float US2RMB = US2HK * HK2RMB;
```

```C++
#include /* File: symbolic-constant.cpp */ 
#include // For calling the ceil() function 
using namespace std; 
int main() { 
const int COMP2012H_QUOTA = 67; 
const float STUDENT_2_PROF_RATIO = 100.0; 
const float STUDENT_2_TA_RATIO = 40.0; 
const float STUDENT_2_ROOM_RATIO = 100.0;
cout << "COMP2012H requires " 
	<< ceil(COMP2012H_QUOTA/STUDENT_2_PROF_RATIO) 
	<< " instructors, " 
	<< ceil(COMP2012H_QUOTA/STUDENT_2_TA_RATIO) 
	<< " TAs, and " 
	<< ceil(COMP2012H_QUOTA/STUDENT_2_ROOM_RATIO) 
	<< " classrooms" << endl; 
return 0; }
```

