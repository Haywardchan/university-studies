### Lesson 2.1 - Making Decisions

## If and Else

You've probably seen **if...else** statements before (or something similar such as **if...then...else**). Not surprisingly, C has these too! Without **if** and **else**, programs wouldn't be very clever, because they couldn't make decisions about their data.

Let's begin with an example:
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    // Ask for an input number
    printf("Please enter a number: ");

    // Read the input number into a variable
    int x;
    scanf("%d", &x);

    // Test the size of the number
    if (x >= 100)
        printf("That is a big number!\n");
    else
        printf("That is a small number.\n");
}
```

[BigNumber.c](https://canvas.ust.hk/courses/44519/files/6293192/download?wrap=1 "BigNumber.c") 

There are a few things to note here about the program that we've created above. First, the condition of the if statement is put inside a pair of brackets. These brackets are required whereas some other programming languages may not require them.

Both lines of code after **if** and **else** are indented to the right. In fact, C doesn't care about spacing between different lines of code. This indentation is used so that the code is easier to read and understand.

Notice that this program takes an input **x** and then checks if **x** is greater than or equal to 100. If **x >= 100** is True then C does what comes after the **if** statement, namely it prints the text **That is a big number!**. Otherwise, it prints **That is a small number.**.

Here are some examples of using the program.
![[Pasted image 20220625013148.png]]
![[Pasted image 20220625013158.png]]
Let's print a bit more information after reading the number. Here is the example:
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    // Ask for an input number
    printf("Please enter a number: ");

    // Read the input number into a variable
    int x;
    scanf("%d", &x);

    // Test the size of the number
    if (x >= 100) {
        printf("You have entered a number bigger than or equal to 100.\n");
        printf("Wow, that is a big number!\n");
    }
    else {
        printf("You have entered a number smaller than 100.\n");
        printf("Oops! That is a small number.\n");
    }
}
```

[BigNumber2.c](https://canvas.ust.hk/courses/44519/files/6293289/download?wrap=1 "BigNumber2.c") 

As you can see the above example has a pair of curly braces, i.e. **{** and **}**, enclosing the statements after **if** and **else**. These braces are required when you want to put more than one line of code there. If you don't, C has no way to know the lines of code are together for the **if** and **else**.

Here are some examples of running the extended program.
![[Pasted image 20220625013326.png]]
![[Pasted image 20220625013341.png]]
It may be a good practise to always include braces so that you won't forget to add them when you use multiple lines of code in an **if** statement.

### Prime Numbers

You probably know a prime number is any number bigger than 1 which cannot be divided by any positive divisor other than 1 and itself. For the numbers 1 to 10, you know the prime numbers are 2, 3, 5 and 7. Therefore, 1, 4, 6, 8, 9 and 10 are not prime numbers. Our objective is to write a program that takes a number as input and prints whether the input number is a prime number or not.

Here's one way to do it:
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    // Read a number and then tells the user whether the number is a prime or not

    printf("Please enter a number between 1 to 10: ");

    // Read the number to a variable
    int number;
    scanf("%d", &number);

    // Test whether the number is a prime or not
    if (number == 2 || number == 3 || number == 5 || number == 7) {
        printf("Your number is a prime number!\n");
    }
    else {
        printf("Your number is not a prime number!\n");
    }
}
```

[PrimeNumber.c](https://canvas.ust.hk/courses/44519/files/6293300/download?wrap=1 "PrimeNumber.c") 

In the above example, **||** means using a _logical or_ operation to combine the conditions. So the condition in the **if** statement means _2 or 3 or 5 or 7_. To use the _logical and_ operation you put **&&** between the conditions.

Here's some examples of the program being used:
![[Pasted image 20220625013519.png]]
![[Pasted image 20220625013528.png]]
![[Pasted image 20220625013539.png]]
The following program exhibits several new features.
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    // This function takes two numbers as input and
    // does something silly and useless.

    // Read two numbers
    printf("Please enter two numbers: ");
    int x, y;
    scanf("%d %d", &x, &y);

    // Do something silly
    int z;
    if (x < y) {
        z = 2 * y;
        printf("%d\n", z);
    }
    else if (x == y) {
        z = 3 * y;
        printf("%d\n", z);
    }
    else
        printf("0\n");
}
```

[SillyProgram.c](https://canvas.ust.hk/courses/44519/files/6293258/download?wrap=1 "SillyProgram.c") 

This is a rather useless program. We are using it simply to learn about a particular piece of code. Notice that the program uses **scanf()** take two inputs, not just one. In general, **scanf()** can take any number of inputs.

Here are two examples of using the program.
![[Pasted image 20220625013708.png]]
![[Pasted image 20220625013717.png]]
Note that the program uses multiple the **if** statements. If x < y, the indented block of code underneath it is executed. Notice that a pair of curly braces is used here because there are two lines of code under **if**. Everything indented after the if line is executed if the condition is True. Otherwise, C says "_OK, x was not less than y so now I will check if x equals y, if so, there is another block of two lines that I should execute. If x is not equal to y, I'll continue down and do what's under the else statement._" What's under the else statement is just a single line, so you can omit using braces if you like to.

## The Switch Statement

Let's say you want to create a program to convert digits from 0 to 9 into English words. For example, 1 is converted to 'one', 2 is converted to 'two', 3 is converted to 'three' and so on.

You can write the program this way:
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    // Ask for a number
    printf("Please enter a number between 0 to 9: ");
    int digit;
    scanf("%d", &digit);

    // Convert the number to an English word
    if (digit == 0) {
        printf("Zero\n");
    }
    else if (digit == 1) {
        printf("One\n");
    }
    else if (digit == 2) {
        printf("Two\n");
    }
    else if (digit == 3) {
        printf("Three\n");
    }
    else if (digit == 4) {
        printf("Four\n");
    }
    else if (digit == 5) {
        printf("Five\n");
    }
    else if (digit == 6) {
        printf("Six\n");
    }
    else if (digit == 7) {
        printf("Seven\n");
    }
    else if (digit == 8) {
        printf("Eight\n");
    }
    else if (digit == 9) {
        printf("Nine\n");
    }
    else {
        printf("Hey, the number is not in the range 0 to 9!\n");
    }
}
```


[ConvertDigitUsingIf.c](https://canvas.ust.hk/courses/44519/files/6293292/download?wrap=1 "ConvertDigitUsingIf.c") 

The above program uses many **if** statements to check for each digit and print the corresponding word.

Here are some examples of running the program.
![[Pasted image 20220625013808.png]]
![[Pasted image 20220625013816.png]]
![[Pasted image 20220625013825.png]]

This program can also be written in another way:
```C
int main()
{
    // Ask for a number
    printf("Please enter a number between 0 to 9: ");
    int digit;
    scanf("%d", &digit);

    // Convert the number to an English word
    switch (digit) {
    case 0:
        printf("Zero\n");
        break;
    case 1:
        printf("One\n");
        break;
    case 2:
        printf("Two\n");
        break;
    case 3:
        printf("Three\n");
        break;
    case 4:
        printf("Four\n");
        break;
    case 5:
        printf("Five\n");
        break;
    case 6:
        printf("Six\n");
        break;
    case 7:
        printf("Seven\n");
        break;
    case 8:
        printf("Eight\n");
        break;
    case 9:
        printf("Nine\n");
        break;
    default:
        printf("Hey, the number is not in the range 0 to 9!\n");
    }
}
```

[ConvertDigitUsingSwitch.c](https://canvas.ust.hk/courses/44519/files/6293307/download?wrap=1 "ConvertDigitUsingSwitch.c") 

This example replaces the multiple **if** statements with a **switch** statement. A **switch** statement works like this. Based on the value of a variable, do the code associated with some particular values (the **case** statements). If the value of the variable does not match any of those values, a _default_ code is executed (the **default** statement).

Using the multiple **if** statements or a **switch** statement doesn't change the program execution in any way. It is not faster or slower using either type of statement. Nevertheless, some people believe using a single **switch** statement is clearer than using a cluster of **if** statements.

When you use a **switch** statement, you have to be careful to use the **break** statement. The **break** statement stops the execution of the code within a particular case. If you don't stop it, the program will continue to run the content for the rest of the cases. For instance, the following code will print **123** instead of **1**:
```C
int x = 1;
switch (x) {
case 1:
    printf("1");
case 2:
    printf("2");
case 3:
    printf("3");
}
```


Using Booleans to Store Logical Results

You've probably used or heard of the _boolean_ data types in other programming languages. A Boolean is either a value of true or false, which represents the result of a logical comparison.

However, by default, C **does not** have the Boolean data type. If you want to store a logical result in a variable, you will need to use an integer instead. The way to represent true or false is simply this: an integer value of 0 means _false_ whereas any other value means _true_. Therefore, an integer can be directly used in an **if** statement like this.
```C
#include <stdio.h>

int main()
{
    int age = 18;
    if (age) {
        printf("You are a big boy!\n");
    }
}

```

[YouAreABigBoy.c](https://canvas.ust.hk/courses/44519/files/6293245/download?wrap=1 "YouAreABigBoy.c")


If you run the above program, you will see the program outputting "You are a big boy!". That means the condition in the **if** statement, i.e. **age**, is evaluated to true. This is because the value inside the variable is 18, which is not zero.

It will be interesting to see what happens if the variable is initialized with a different value like this.

	int age = 0;

If we change the value of the variable as shown above, running the program will give you no output because the **if** statement evaluates the condition as false.