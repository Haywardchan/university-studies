# Lesson 3.2 - Variable Scope

## Local and Global Variables

Up to now our C statements, including variable declarations, have been put inside the **main()** function and other functions that we have created. Here is an example:
```C
// A function for adding two numbers together
int addition(int a, int b)
{
    return a + b;
}

int main()
{
    int x, y;

    // Put the result of adding 2 and 1 in the variable x
    x = addition(2, 1);

    // Put the result of adding 10 and 12 in the variable y
    y = addition(10, 12);
}
```

In the above example, two variables **x** and **y** are declared and used in the **main()** function. Another two variables **a** and **b** are declared in the parameter list of the **addition()** function and used inside the function. These variables are called _local variables_. The word 'local' means these variables are locally bound to the functions they have been declared in. For example, you cannot use the variable **x** and **y** in the **addition()** function because **x** and **y** are local to **main()**. Similarly, you cannot use the variables **a** and **b** in **main()**.

Let's look at another example.
```C
int x, y, a, b;

// A function for adding two numbers together
int addition()
{
    return a + b;
}

int main()
{
    // Put the result of adding 2 and 1 in the variable x
    a = 2;
    b = 1;
    x = addition();

    // Put the result of adding 10 and 12 in the variable y
    a = 10;
    b = 12;
    y = addition();
}
```

You might think we have done something wrong with the variable declarations but this program works perfectly well. Compared to the previous program, the variables are not declared in their corresponding functions anymore. They are declared outside any function. When a variable is declared out of any function, it is called a _global variable_. Global variables are 'visible' to every function and that means every function can use them. For example, both the **main()** function and the **addition()** function can use all of **a**, **b**, **x** and **y** even though they are not declared inside those functions.

## Local Variables in Functions

Let's look at this example.
```C
#include <stdio.h>

void change(int a, int b)
{
    int temp;

    // Swap the value of a and b
    temp = a;
    a = b;
    b = temp;
}

int main()
{
    int x = 1, y = 2;

    // Print values before change()
    printf("x = %d, y = %d\n", x, y);

    change(x, y);

    // Print values after change()
    printf("x = %d, y = %d\n", x, y);
}
```

[ChangeLocalVariables.c](https://canvas.ust.hk/courses/44519/files/6293329/download?wrap=1 "ChangeLocalVariables.c") 

What's happening is, first, two local variables **x** and **y** in **main()** are initialized to the values 1 and 2. The values of these two variables are then passed to the **change()** function. Inside the **change()** function, the parameters **a** and **b** then store the values of **x** and **y** respectively. At this moment, **a** is equal to 1 and **b** is equal to 2. The content of **a** and **b** are then swapped so that at the end of **change()**, **a** becomes 2 and **b** becomes 1. Then after finishing the **change()** function the program finishes by printing the value of **x** and **y** using **printf()**.

A common misunderstanding in this example is that one would think the values of **x** and **y** are swapped after calling **change()**. This is because intuitively one would think **a** corresponds to **x** and **b** corresponds to **y**. Therefore, swapping **a** and **b** implies **x** and **y** are swapped as well. However, it doesn't work like that. Let's first look at the output of the program.
![[Pasted image 20220705210612.png]]
Surprised? The values of **x** and **y** are not changed at all after calling **change()**. When a program passes a variable from one function to another as a parameter, only the _value_ is passed but not the actual variable. Using the above example, let's think of the variables as boxes. In **main()**, two boxes are created, one holding a value of 1 and the other holding a value of 2, like this:

**In main()**

**x:** 1
**y:** 2

Then when calling **change()**, the values of x and y, i.e. 1 and 2 respectively, are passed to the function. These two values are stored in two new boxes **a** and **b**, like this:

**In main()**

**x:** 1
**y:** 2

**In change()**

**a:** 1
**b:** 2

As you can see only the values are passed, i.e. copied, to the parameters of the **change()** function. The program proceeds to run the content of **change()**, the values of the variables are then swapped at the end of the function, like this:

**In main()**

**x:** 1
**y:** 2

**In change()**

**a:** 2
**b:** 1

In **main()**, **x** and **y** are still having their original values after calling **change()**. Therefore, you will see the same values of the variables **x** and **y** when they are printed before and after calling the **change()** function.