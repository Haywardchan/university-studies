##### Switch statement
switch statement is a variant of the if-else-if statement, that allows multiple choices based on the value of an integral expression.
```C++
switch (integral expression) {
case constant-1: 
	statement-sequence-1; 
	break; 
case constant-2:
	statement-sequence-2; 
	break; ...
case constant-N: 
	statement-sequence-N; 
	break; 
default: // optional 
	statement-sequence-(N+1); 
}
```
Integer switch:
```C++
#include /* File: switch-find-comp2012h-instructor.cpp */ 
using namespace std; int main() // To determine your instructor 
{ 
cout << "Enter the COMP2012H section number to find its instructor: "; 
 int section; // COMP2012H section number: should be 1, 2, 3, or 4 
 cin >> section; // Input COMP2012H section number 
 switch (section) { 
 case 1: cout << "Sergey Brin" << endl; break; 
 case 2: cout << "Bill Gates" << endl; break;
  case 3: cout << "Steve Jobs" << endl; break;
   case 4: cout << "Jeff Bezos" << endl; break;
    default: cerr << "Error: Invalid lecture section " << section
    << endl; 
    break; 
    } 
    return 0;
}
```
Character switch:
```C++
#include /* File: switch-char-bloodtype.cpp */
using namespace std; int main() // To find out who may give you blood 
{ 
cout << "Enter your blood type (put 'C' for blood type AB): "; 
char bloodtype; 
cin >> bloodtype; 
switch (bloodtype) { 
case 'A': cout << "Your donor must be of blood type: O or A\n"; break; 
case 'B': cout << "Your donor must be of blood type: O or B\n"; break; 
case 'C': cout << "Your donor must be of blood type: O, A, B, or AB\n"; 
break; 
case 'O': cout << "Your donor must be of blood type: O"; break; default: // To catch errors 
cerr << "Error: " << bloodtype << " is not a valid blood type!\n"; break;
} 
return 0; 
}
```
Sharing cases switch:
```C++
#include /* File: switch-int-grade.cpp */ 
using namespace std; 
int main() // To determine your grade (fictitious) 
{ 
char grade; // Letter grade 
int mark; // Numerical mark between 0 and 100 
cin >> mark; 
switch (mark/10) { 
case 10: // Several cases may share the same action 
case 9: 
grade = 'A'; break; // If mark >= 90 
case 8: case 7: case 6: // May write several cases on 1 line 
grade = 'B'; break; // If 90 > mark >= 60 
case 5: case 4: case 3: case 2: 
grade = 'C'; break; // If 60 > mark >= 20 
case 1: grade = 'D'; break; // If 20 > mark >= 10 
default: grade = 'F'; break; 
} 
cout << "Your letter grade is " << grade << endl; 
return 0; 
}

```

Switch Vs if-else-if statement in [[C++ selection]]
- switch statement can only test for equality of the value of one quantity. 
- each expression of the if-else-if statement may test the truth value of different quantities or concepts

When a case constant is matched, the statements associated with the case are executed until either 
- a break statement. 
- a return statement. 
- the end of the switch statement.

enum<[[C++ Data types]]>with switch
```C++
#include /* File: enum-shapes.cpp */ 
using namespace std;
int main() { 
enum shapes { TEXT, LINE, RECT, CIRCLE }; 
cout << "supported shapes: " << " TEXT = " << TEXT << " LINE = " << LINE << " RECT = " << RECT << " CIRCLE = " << CIRCLE << endl; int myshape; // Why the type of myshape is not shape? cin >> myshape; 
switch (myshape) { 
case TEXT: 
	cout << "Call a function to print text" << endl; break; 
case LINE: 
	cout << "Call a function to draw a line" << endl; break; 
case RECT: 
	cout << "Call a function to draw a rectangle" << endl; break; 
case CIRCLE: 
	cout << "Call a function to draw a circle" << endl; break; 
default: 
	cerr << "Error: Unsupported shape" << endl; break; 
} 
return 0; 
}
```

