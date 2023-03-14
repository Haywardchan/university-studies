#### Lesson 2.2 - For Loops

## Loop

In your programming experience before taking this course you must have learned how to write a loop. For example, you may have used constructs such as **For**, **Do-While**, and **Do-Until** in VBA or **for**, **while**, and **range** in Python. C has the same kind of looping control code.

Let's start with **for** loops. In most programming languages you specify what kind of things (typically numbers) you want to loop over with. For example, in Python, you could do something like this:

```python
for i in range(1, 11):
    # some code here
```


And in VBA you could do something like this:
```vb
Dim i As Integer
For i = 1 To 10
    ' some code here
```

The **for** loop in C is very similar. It usually iterates through a variable. For example, the program below adds up the numbers from 1 to 10 and prints the sum.
```C
#include <stdio.h>

int main()
{
    // This program reads no input. It simply returns the sum of the integers
    // between 1 and 10.

    int sum = 0; // Initialize the sum to 0
    int i; // The loop variable

    for (i = 1; i <= 10; i++) {
        sum = sum + i; // update the sum
    }

    printf("%d\n", sum); // print the sum
}
```


[Loopy.c](https://canvas.ust.hk/courses/44519/files/6293233/download?wrap=1 "Loopy.c") 

As you can see, there are three parts in a C **for** loop:

for (initialization; loop condition; increment)
    ...some code here...

In this example,

1.  the initialization is **i = 0**  
2.  the loop condition is **i <= 10**
3.  the increment is **i++**

The structure of the **for** loop works like this:

-   The variable **i** is initialized to 1 before entering the **for** loop
-   Before entering the body of the loop (the indented part inside a pair of curly braces) the loop condition is evaluated
-   If the loop condition is True, the loop will run; otherwise the loop will stop
-   In this case, **i** (=1) is smaller than or equal to 10, so we enter the body of the loop and **sum** becomes 1
-   After the body is finished **i** is added by 1, i.e. the increment, so that the value becomes 2
-   Before entering the next iteration, the loop condition is again evaluated  
    
-   In this case, **i** (=2) is smaller than or equal to 10, so we again enter the body of the loop and **sum** takes the value 1 + 2 = 3
-   This process continues until **i** has finally become 11. At this point, **sum** has been added 10 times, i.e. 1 + 2 + ... + 10 = 55
-   Before entering the next iteration, the loop condition is evaluated to False and therefore the loop stops
-   The program then continues to the next line after the **for** statement - namely the **printf()** statement in this example. So, the **sum** (which is 55 now) is printed

Notice that the name of the variable that we are using in the loop can be anything that we want - here we called it **i**, but any name is fine.

By the way, C allows you to write this:

	sum = sum + i;

using the following method, which is much quicker to type:

	sum += i;

This is used in other languages as well, such as Python and Java. Using this notation, you could increment the variable **sum** by 1 like this:

	sum += 1;

Or you could use this form, which is an even simpler:

	sum++;

## Nested Loops

Let's look at prime numbers again. A prime number is a number without any positive divisor excluding 1 and itself. If we can find out the number of divisors for a particular number, we will know whether that number is a prime number or not.

To do that for a number **x** the following code can be used:
```C
// Find out how many divisors for a number x
int divisors = 0;
for (int i = 1; i < x; i++) {
    if (x % i == 0) {
        divisors++;
    }
}

// The number is a prime number if there is only one divisor
if (divisors == 1) {
    printf("%d is a prime number.\n", x);
}
```


The **%** operator used inside the **for** loop is called modulus. It finds the remainder of the division of the first number by the second number. For example, **20 % 4** is 0 and **20 % 3** is 2. If the remainder of dividing **x** by **i** is 0, it means that **i** is a divisor of **x**.

The above code works out the number of divisors for a number **x** using the **for** loop. If the total number of divisors is 1 (i.e. only the number 1 is the divisor), the number will be a prime number.

Let's say we want to find out all prime numbers between 1 to 20. What we can do is to use the above code 20 times, each time setting **x** to a different number. This is shown in the following program.
```C
#include <stdio.h>

int main()
{
    // This program finds all prime numbers from 1 to 20
    int divisors;
    int x, i;

    // Loop through the value of x from 1 to 20
    for (x = 1; x <= 20; x++) {
        // Find out how many divisors for the number x
        divisors = 0;
        for (i = 1; i < x; i++) {
            if (x % i == 0) {
                divisors++;
            }
        }

        // The number is a prime number if there is only one divisor
        if (divisors == 1) {
            printf("%2d is a prime number.\n", x);
        }
    }
}
```


[PrimeNumbers.c](https://canvas.ust.hk/courses/44519/files/6293252/download?wrap=1 "PrimeNumbers.c") 

Here is the output of the program.
![[Pasted image 20220625014725.png]]
As you can see from the code, a **for** loop is used inside another **for** loop. You may remember from your previous programming experience before beginning this course that this is called a _nested loop_, because there is one loop nested inside another.