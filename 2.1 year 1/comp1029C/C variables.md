# Lesson 1.3 - Variables

## Giving Names to Values

We have looked at this C statement in the previous lesson:

	sum = 10 + 5;

This statement adds two numbers and then gives the result to a name called **sum**. As you probably know, we call something like **sum** a _variable_ because we can assign it any value that we like - its value can "vary".

Giving names to values is very useful. For example, it allows you to compute a value, give the result a name, and then use it by referring to that name in the future. Here is another example:

	radius = 10;
	area = radius * radius * 3.141592;

In the first line, we define **radius** to be 10. In the second line, we use that value to compute the area of a circle with radius 10.

Notice that the "=" sign is used to make an assignment, just like in other programming languages. On the left of the equal sign is the name of the variable. On the right of the equal sign is an expression that C evaluates. The result is then assigned to the variable.

However, before you use a variable, C would like to know what type of thing the variable is going to store. Why does C want to know that? First, different types of thing use different amount of memory. If the type is known, C will be able to prepare the memory space according to the type. Second, you may make a mistake later in the code so that you try to put an invalid value into a variable. For example, it is a mistake to assign a piece of text to a variable storing numerical value. Knowing the type of a variable, C can check whether you are doing the right thing with the variable when it inspects the code later.

## Declaring a Variable

Let's say you want to do this:

	answer = 1 + 1;

This line adds two 1s and then puts the result 2 in a variable called **answer**. As we have said in the previous lesson, C would like to know what you are going to do with the variable **answer** before you use it. Let's add a line of code before using the variable:

	int answer;
	answer = 1 + 1;

The new line of code tells C that you are going to use a variable called **answer** later in the code. The **int** before the name is the _data type_. In this example, we say that the variable is going to store an **int**eger, i.e. a number without the decimal place. This code is called _variable declaration_ in C.

You have to declare a variable before you use it. For example, if you don't declare the variable **answer** before using it, C will give you an error like this:

	error C2065: 'answer' : undeclared identifier

You can use a variable to store different types of things. Integer is just one type of them.

Here is another example:

	int weekdays, weekend, daysinweek;
	weekdays = 5;
	weekend = 2;
	daysinweek = weekdays + weekend;

The first line declares all variables at the same time. If you have many variables having the same data type you can just list them together, separated by commas. After this line, C understands that you have three variables which are integers and they have the names **weekdays**, **weekend** and **daysinweek**. The next two lines assign a value to each of **weekdays** and **weekend**. Finally, **daysinweek** stores the sum of the previous two numbers.

We can make the above code shorter by putting the values in the variables in the very first line, like this:

	int weekdays = 5, weekend = 2, daysinweek;
	daysinweek = weekdays + weekend;

The first line declares the variables and then puts initial values into a couple of them.

## What's in a Name?

C uses a set of rules, that you're probably already used to from other programming languages, when assigning names to variables. Those rules are that variable names must begin with a letter, and there are certain symbols that aren't permitted in a variable name. For example, naming a variable "Joe" or "Joe42" is fine, but naming it "Joe+Sally" is not permitted. You can probably imagine why. If C sees "Joe+Sally" it will think that you are trying to add the values of two variables "Joe" and "Sally".

Similarly, there are special C words that can't be used as variable names. If you try to use them, C will give you an error message. For example, the word **if** is used by C for conditional statements (just like most other programming languages), so you can't have a variable named **if**.

Rather than listing here all of the words that cannot be used as C variable names, just keep in mind that if you get a C error when you declare a variable, it's probably because the variable name is not permitted. In this case, you can adjust the variable name that you have used.

_Reserved words_ are words that have been used by C as a command or an operator. You are not allowed to name your variables using reserved words. Here are two examples of someone trying to use a C reserved word as a variable name:
![[Pasted image 20220625005225.png]]

You can see in the above picture, which is from Visual Studio, the two variable names are underlined with red colour. These underlines indicate there are problems at those two places, where reserved words have been used as variable names. You can ignore the gray lines in the above picture. Those are the way Visual Studio used to highlight the current line of code in the code editor.

Finally, just a reminder of something you've probably heard before: try to use descriptive variable names to help the reader understand your program. For example, if a variable is going to store the area of a circle, calling that variable **area** is a much better choice than calling it something like **z** or **x42b** or **monkey**.

## Data Types

You have seen examples using the integer data type, i.e. numbers without a decimal place, when declaring variables. What if you want to use real numbers, i.e. numbers with a fractional part or a decimal place, in C? Rather than using the integer data type, you can use another data type called _float_.

You can use a lot of different data types in C. Here are some of the commonly used data types:

![[Pasted image 20220625005358.png]]

Here are some things you need to know about them:

-   When putting a character to a variable of the **char** data type, the character is enclosed by a pair of single quotes **'**. This is different from the double quotes **"** used by a piece of text with more than one characters, i.e. **"How are you?"**, as you have seen earlier.
-   A variable of the **float** data type can store a real number with up to roughly 7 significant digits, i.e. **3.141592**. If you want to have more digits you will need to use the **double** data type that can hold a real number of up to roughly 15 significant digits, i.e. **3.14159265358979**.

Let's make an example using these data types. The example uses some weight and height values to calculate the body mass index (BMI). BMI is a reference to determine whether a person is too thin, normal or too fat). The program code is shown below:
```C
#include <stdio.h>

int main()
{
    char   name_initial = 'D';
    int    weight_in_lb = 200;
    double lb_to_kg     = 0.45359237;
    double weight_in_kg = weight_in_lb * lb_to_kg;
    int    height_in_cm = 170;
    float  height_in_m  = height_in_cm / 100.0;
    double bmi          = weight_in_kg / (height_in_m * height_in_m);

    printf("Hello! I am %c.\n", name_initial);
    printf("\n");
    printf("My weight (kg) is: %f\n", weight_in_kg);
    printf("My height (cm) is: %d\n", height_in_cm);
    printf("My BMI is: %f\n", bmi);
}
```

[CalculateBmi.c](https://canvas.ust.hk/courses/44519/files/6293272/download?wrap=1 "CalculateBmi.c") 

The above C program declares the variables, puts in the values and then prints the content of some of these variables. At this stage, you don't need to worry about how to write all these **printf** functions. We will talk about it in detail in the next lesson.

## Mixing the Data Types

You can create many variables with different data types. As we have said before, declaring a variable tells C what we are going to store in the variable.

Then what happens if we store something else in the variable?

Let's look at the following example:

	int total_lab_computers;
	total_lab_computers = 40.5;

The first line declares a variable called **total_lab_computers**, which is created to store the total number of computers in a lab. We use the integer data type because we know we won't have half a computer in the lab. Then, the second line tries to set the number to **40.5** even though the number means forty and a half of computers in the lab. What will happen to the value of the variable then? If we use the following line to print the output:

	printf("Number of computers = %d", total_lab_computers);
	
the output will show 40.

This is what happens: C automatically changes **40.5** into an integer before the number is stored in **total_lab_computers**. When C does this conversion it does not do rounding on the number. It simply throws away the fractional part, i.e. 3.2 becomes 3 and 5.89 becomes 5. To warn you about the loss of data (the fractional part) C will give you a warning if you build a program which has this issue. The warning looks like this:

	warning C4244: '=' : conversion from 'double' to 'int', possible loss of data

Why does the above message say from **double** to **int**? This is because C treats any number with a decimal component as a 'double' value. For example, if you have the following line of code:

	float weight = 70.8;

and you build the program containing this code, C will give you this warning:

	warning C4305: 'initializing' : truncation from 'double' to 'float'

To tell C that you are using a 'float' value you can put an **f** at the end of the number, like this:

	float weight = 70.8f;

Integer Division

As we are talking about data types, you have to be aware of an important behaviour called _integer division._

Integer division means using the **/** operator to calculate the result of a division between two integers. For example, **5 / 2** is an integer division because both 5 and 2 are integers.

Intuitively, you would think that the result of **5 / 2** is 2.5. However, programming languages may not think it that way.

For instance, C does not think in the way we intuitively think of the division of numbers. The logic of C is like this:

If both operands are integers, the result must also be an integer.

Using this logic, if the division is **5 / 2**, the result will be equal to 2. Why 2? It is because 2 is the truncation (throwing away the decimal places) of 2.5, which makes the number an integer.

Let's look at the following example:

	float number;
	number = 5 / 2;

You would think that after running the above two lines of code, the variable **number** contains the value of 2.5. You may be surprised to know that the actual value of **number** is 2. Why? Because the expression **5 / 2** is an integer division, the result of the expression is 2. The result of 2 is then stored in the variable **number**, even though **number** is a **float**.

If you want to obtain the result of 2.5, you will have to explicitly set one of the operands to a floating point value, like this:

	float number;
	number = 5.0 / 2;

After running the above code the variable **number** stores the value of 2.5. You could have use the expression **5 / 2.0** or **5.0 / 2.0** to obtain the same result.