### Lesson 3.1 - Functions

## Functions in C

In C, a function must have a data type. The data type defines the type of data returned by the function. For example, the following code creates a function using the **double** data type, which means the function returns a floating point number. Then comes the name of the function, in our case **square**. Then comes the inputs to the function in parentheses. In our case there was just one input, which we called **x**. The input has its own data type too, which is a **double**. The content of the function is enclosed by a pair of braces. In this example, the function computes x*x and then returns it.

We can put the function near the top of our source code file and then use it later. For example, we can use the **square()** function to calculate the square of any number entered into the program.
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

// This function calculates the square of the input x
double square(double x)
{
    // Compute the square and return it
    return x * x;
}

int main()
{
    // Ask for a number
    printf("Please enter a number: ");
    double number;
    scanf("%lf", &number);

    // Take a square of the number and print it
    printf("The square of your number is: %g\n", square(number));
}
```
[Square.c](https://canvas.ust.hk/courses/44519/files/6293312/download?wrap=1 "Square.c") 

Notice that the above example uses the **square()** function to take the square of a number and then directly prints the returned value. If we wanted to, we could have put the returned value in a variable like this:

double result; 
result = square(number);

and then printed the variable using a **printf()** function:

printf("The square of your number is: %g\n", result);

Using a variable or not, the outcome is the same.

## Functions Without Output

Sometimes a function does not need to return anything. For example, a function could be used simply to perform a specific action, and not to return anything.

Let's see an example.
```C
#include <stdio.h>

void printcurrency(double amount)
{
    printf("$%9.2f", amount);
}

int main()
{
    // Print the monthly spending with a formatted amount
    // using a function.

    printf("My Monthly Spending\n\n");

    printf("%-20s", "Food");
    printcurrency(70 * 30);
    printf("\n");

    printf("%-20s", "Transportation");
    printcurrency(20 * 25);
    printf("\n");

    printf("%-20s", "Leisure");
    printcurrency(100 * 20);
    printf("\n");

    for (int i = 0; i < 30; i++) {
        printf("=");
    }
    printf("\n");

    printf("%-20s", "Total");
    printcurrency(70 * 30 + 20 * 25 + 100 * 20);
    printf("\n");
}
```

[PrintCurrency.c](https://canvas.ust.hk/courses/44519/files/6293313/download?wrap=1 "PrintCurrency.c")

Here is the output of running the above example.

![[Pasted image 20220703165244.png]]
As you can see, the values are nicely printed using the **printcurrency()** function. The job of this function is to print the values using the nicely formatted currency. So there is no point in returning anything from the function.

Looking at the data type of the function (the word before the function name), it is something called **void**. You haven't seen the **void** data type so far. It is a special 'data type' which means _no type_. Yes, it is confusing and contradictory when you can specify a data type as no type! When **void** is used to define the data type of a function, it actually means the function does not return any value, i.e. the function has no data type at all.

We can make use of **void** in functions without input parameters. Here is an example.
```C
void sayhello(void)
{ 
    printf("Hi there!\n"); 
}
```

The above function prints a message **Hi there!** on the screen. Notice that the data type **void** is used in the parameter list (the content of the brackets after the function name) without any parameter name. The meaning is that the function does not require any input parameters and hence there is no data type at all for the input.

It is very common that the first line of the above code is written like this:
```C
void sayhello()
```

As you can see, the data type **void** can be omitted altogether when no parameter is needed in a function.

## The main() Function

You know that **main()** is the starting point of a program.
```C
int main()
{ 
    ...Put C statements here... 
}
```

It is just a normal function that the system, i.e. the operating system, calls when you start to run your program. The **main()** function does not behave any differently to other functions that you make.

The return value of **main()** indicates whether the execution of your program is a success or a failure. Typically a return value of 0 means a success and a non-zero return value means something bad has happened.

However, you may notice that we do not have a **return** statement in **main()** although it has a data type of **int**. If we don't write a **return** statement at the end of the function, the C compiler will assume we have no problem and add the following line automatically at the end of the function, which you won't actually see.

	return 0;