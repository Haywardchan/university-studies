### Lesson 1.4 - Text Input and Output

## Using the printf() Function

We have seen how to use the **printf()** function to print text in C programs. For example, you can do this:

	printf("Very nice!");

The above line of code prints the text **Very nice!**.

It will be much more useful if we can print text content as well as some variable values on the screen. Here is an example:
```C
#include <stdio.h>

int main()
{
    float hours_of_sleep_per_day = 7.5f;

    printf("An average person needs %f hours of sleep each day.\n",
        hours_of_sleep_per_day);
    printf("An average person needs %f hours of sleep each year.\n",
        hours_of_sleep_per_day * 365);
    printf("An average person needs to sleep %f days in a year.\n",
        hours_of_sleep_per_day * 365 / 24);
}
```

[SleepingTime.c](https://canvas.ust.hk/courses/44519/files/6293305/download?wrap=1 "SleepingTime.c")


The first **printf()** prints the content of the variable **hours_of_sleep_per_day**. The **%f** inside the text for the **printf()** function is called the _placeholder_. The placeholder tells the **printf()** function that we are going to print a float value (hence the letter **f** in the placeholder) in that position. Similarly, the second and third **printf()** use the **%f** placeholder to print some calculations which use the variable **hours_of_sleep_per_day**. Let's look at the result:
![[Pasted image 20220625011936.png]]
As you can see, the text output includes the text as well as the content of the float values.

Here are some common placeholders and their examples:

![[Pasted image 20220625012023.png]]

## printf() Formatting Options

You now know how to print variables using placeholders. Let's look at some formatting options so that we can have more flexibility when printing the values.

### Placeholder Width

You can specify the width, i.e. the number of character spaces, that the placeholder occupies. Let's look at the following example:
```C
int dogs = 2;
int cats = 2;
int fish = 12;
printf("I have %3d dogs at home.\n", dogs);
printf("I have %3d cats at home.\n", cats);
printf("I have %3d fish at home.\n", fish);
printf("I have %3d pets at home.\n", dogs + cats + fish);
```

In the code shown above, the placeholders have a **3** between the **%** and **d**. The number means the width of the result.

The above example gives this output:
![[Pasted image 20220625012218.png]]

As you can see, no matter how wide the numbers are, all of them have used up three character spaces in the output. If the number has less than three digits, spaces will be added in front of the number to make sure it uses a width of three. This is called right justification.

In some cases, you may want to have left justification, i.e. spaces will be added after the number. You can slightly modify the placeholder using a **-** before the width number, like this:
```C
int boys = 50, girls = 5;
printf("Students in an Engineering Class\n\n");
printf("%-30s:%3d\n", "Number of male students", boys);
printf("%-30s:%3d\n", "Number of female students", girls);
printf("%-30s:%3d\n", "Total number of students", boys + girls);
```


In the above code the %s placeholders are left justified with a width of 30 characters wide, as indicated by **%-30s** in the code. The output of the code looks like this:

![[Pasted image 20220625012443.png]]

You can see that the width and justification options are very useful in outputting values in a table structure.

## Getting Input

We have seen how to output text using **printf()**. How about getting inputs from users? C provides a function called **scanf()**, also from the stdio library, to get _formatted inputs_ from users.

**Important**

In Visual Studio Community, the IDE will give you an error if you use **scanf()**. To avoid having the error, we will use an instruction to disable it:

	#define _CRT_SECURE_NO_WARNINGS 1

You will not get a similar error if you use other systems or development tool.

The above instruction will get added to all source files that use the **scanf()** function.

**scanf()** is similar to **printf()** in the way that placeholders are used to describe the format of data. For example, the following code reads an integer from the user and put the integer into a variable called **input**.
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    int input;

    // Print the prompting text
    printf("Please enter an integer: ");

    // Read the user input into the variable input
    scanf("%d", &input);

    // Print out the input value
    printf("You have entered %d.\n", input);
}
```
[IntegerInput.c](https://canvas.ust.hk/courses/44519/files/6293291/download?wrap=1 "IntegerInput.c") 

This line of code:

	scanf("%d", &input);

means a number will be read from the user and the number will be stored in a variable called **input**. It is important to note that **scanf()** requires the use of an ampersand **&** before a variable. You don't use **&** for a **printf()** function.

After running the above example, you will be asked to input an integer. For example, we can enter 5. The number will then be output to the screen by the **printf()** function in the last line of **main()**. The display when we enter 5 as the input is shown below:
![[Pasted image 20220625012749.png]]
You can also read a character from the user if you change the placeholder to **%c**, like this:

printf("Please enter 'Y' (yes) or 'N' (no): ");
scanf("%c", &answer);

Certainly the variable **answer** shown in the above code must have a **char** data type. Depending on the type of data you want to get from the user, you will use different placeholders and their corresponding variable with an appropriate data type.

Here are some common placeholders and their examples for **scanf()**:

![[Pasted image 20220625012827.png]]

Almost all of the cases you need to use the ampersand **&** before the variable name provided to **scanf()**. The only exception is when you want to read a piece of text from the user. We will talk about read a piece of text when we discuss _strings_ later in the course.

When using **scanf()** you need to make sure that the actual input matches the placeholder type. For example, if the placeholder is **%d** and the user enters some letters, **scanf()** will produce an error.