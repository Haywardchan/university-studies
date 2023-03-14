If statements:
$$if (boolean)<statement> $$$$if (boolean)\{<sequence \space of \space statements> \}$$
Sorting 2 numbers:
```C++
#include /* File: swap.cpp */ 
using namespace std; 
int main() /* To sort 2 numbers so that the 2nd one is larger */ 
{ int x, y; // The input numbers 
 int temp; // A dummy variable for manipulation 
 cout << "Enter two integers (separated by whitespaces): "; 
 cin >> x >> y; 
 if (x > y) { 
 temp = x; // Save the original value of x 
 x = y; // Replace x by y 
 y = temp; // Put the original value of x to y 
 }
  cout << x << '\t' << y << endl; 
  return 0; }
```

If else statements:
$$if (boolean)<stms> else<stms> $$$$if (boolean) \{<stms>\}\space else\space \{<stms> \}$$
If else if statment
```C++
if (bool) <stms>
else if (bool)<stms> ... else if (bool)
else<stms>
```

Grade conversion:
```C++
#include /* File: if-elseif-grade.cpp */
using namespace std; 
int main() /* To determine your grade (fictitious) */ 
{ 
char grade; // Letter grade 
int mark; // Numerical mark between 0 and 100 
cin >> mark; if (mark >= 90) grade = 'A'; // mark >= 90 
else if (mark >= 60) grade = 'B'; // 90 > mark >= 60 
else if (mark >= 20) grade = 'C'; // 60 > mark >= 20 
else if (mark >= 10) grade = 'D'; // 20 > mark >= 10 
else grade = 'F'; // 10 > mark 
cout << "Your letter grade is " << grade << endl; 
return 0; 
}
```

Relational Operators is one of [[C++ operator]] used for comparing 2 values
![[Pasted image 20220826022423.png]]

Logical Operators is one of [[C++ operator]] used to modify or combine boolean values.
![[Pasted image 20220826022815.png]]

If-else operator:?
$$(<bool.exp>)?<then.exp>:<else.exp>;$$
ternary if-else operator ?: is used
I.e
```C++
/* Example: get the larger of two numbers */ 
larger = (x > y) ? x : y; /* Example: get the letter grade from the percentile */ 
grade = (percentile >= 85) ? 'A' 
	: ((percentile >= 60) ? 'B' 
   : ((percentile >= 15) ? 'C' 
   : ((percentile >= 5) ? 'D': 'F' 
	   ) 
   ) 
);
```

Nested if 
![[Pasted image 20220826030047.png]]
- C++ groups a dangling else with the most recent if.

