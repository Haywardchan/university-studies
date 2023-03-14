## C Statements

A C program is written using many _C statements_. Each C statement contains a specific command that you want your program to do.

### Use of Semicolons

A C statement can be put in one line or over multiple lines. To indicate the end of a C statement a semicolon is put at the end of each statement. Here is a couple of example C statements:

1. Adding two numbers and storing the result
```C
sum = 10 + 5;
```

2. Print (display in the console window) a piece of text
```C
printf("Hi, how are you doing?");
```
Some other programming languages such as Visual Basic do not require the use of semicolons at the end of a statement. However, if you do not do that in C, it will result in a syntax error.

### Case Sensitivity

C statements are **case sensitive**. You need to be careful with the big/small letters when writing a C program. For example, the following two statements are not the same:
```C
birthyear = 1980;

BirthYear = 1980;
```
The first statement uses all small letters (**birthyear**) but the second uses big letters for the first letter of each word (**BirthYear**).

### Spacing

The amount of spacing, which can be spaces or tabs, used in a C statement does not affect the meaning of the statement. You can use only a few spaces or add as many spaces as you like. For example, the following statements would do the same thing (i.e. printing the text 'I love spaces!')
```C
printf("I love spaces!");
printf    ("I love spaces!")  ;
printf(  "I love spaces!"    );
```

However, adding spaces within a piece of the text, i.e. text enclosed by a pair of double quotes **"**, will change the content of the text. For example, **"Hello!"** and **"H e l l o !"** are two different pieces of text.

Although you can use any amount of spacing in a statement, the use of spacing is an important aspect in the readability of program code. For example, you can put a C statement in multiple lines, using appropriate spacing at various places, to improve the readability of your code, like this:
```C
savingspermonth = pocketmoney
                + parttime
                - meals
                - tuition
                - transportation
                - otherexpenses;
```
which is equivalent to the code shown below:
```C
savingspermonth = pocketmoney + parttime - meals - tuition - transportation - otherexpenses;
```

Remember that the semicolon is put at the very end to indicate the end of the statement.

## The Starting Point of a C Program

You write a C program by putting together many C statements inside the source file. However, where exactly do we put those C statements?

Every C program must have something called a **main()** function. The **main()** function is the starting point of a program, i.e. the program starts to run from there. The starting C statements are put inside this **main()** function. Later in the course we will also put C statements in some other places such as inside other functions.

The **main()** function is written like this:
```C
int main()
{
    ...Put C statements here...
}
```

It starts with **int main()** and the C statements are put between a pair of 'curly braces', i.e. **{** and **}**. When you run your program the statements are executed from top to bottom, one after another, until it reaches the end of the **main()** function.

## Printing Text

One of the most basic things you do with a C program is to display things. As you have seen in the previous lesson, we can use the **printf()** function to do the printing of text.

There are a lot of C functions you can use to do all sorts of things. Similar functions are usually put together in a library. For instance, all mathematical functions are grouped together in a library called _math_.

The **printf()** function is one of the functions provided by a library called _stdio_ (**st**an**d**ard **i**nput and **o**utput). Before using the **printf()** function you need to tell the C compiler that you are going to use it from the stdio library. To do that, you include this line of code at the top of the source file:
```C
#include <stdio.h>
```

The above line of code says that the program code will use a function from stdio. In our case, we use the **printf()** function. Once this line is added at the top the compiler will then understand the meaning of **printf()** when it sees the function later in the code.

Here is an example of using the **printf()** function:
```C
#include <stdio.h>

int main()
{
    printf("I have $20. I can buy one chocolate bar ($10 each) and two packs of candy ($4 each).\n");
}
```

[SimplePrint.c](https://canvas.ust.hk/courses/44519/files/6293301/download?wrap=1 "SimplePrint.c") 


The **printf()** function shown above prints one line of text, like this:
![[Pasted image 20220625003152.png]]

As you can see, text content in a C program is enclosed by a pair of double quotes, i.e. **"**. The line printed by the above example is too long but we will show one way to fix this in the next example. There is a piece of strange looking text, **\n**, at the end of the text content. It is called the newline character, which we will be discussed below.

### Using the Newline Character

You may have used the newline character, which means moving to the start of the next line, in other programming languages. In C, the newline character is represented by **\n**. For example, the program shown above doesn't produce a very nice output because the line of text is too long for the window. Let's break the line at appropriate places using a newline character, as shown below:
```C
#include <stdio.h>

int main()
{
    printf("I have $20.\nI can buy one chocolate bar ($10 each) and two packs of candy ($4 each).\n");
}
```

[Newline.c](https://canvas.ust.hk/courses/44519/files/6293295/download?wrap=1 "Newline.c") 

A \\n has been inserted in the middle of the text (after the text **$20.**) so that the line is broken into two separate lines, like this:
![[Pasted image 20220625003604.png]]
An additional \\n is required at the end of the text so that the **Press any key to continue . . .** text printed by the system will be put on the next line.

### Using the Tab Character

Another useful character that we can use in printing is the tab character. In C, the tab character is represented using **\t**. Typically a tab character aligns text in 4-character or 8-character intervals. In C, the tab character occupies the space of 8 characters. Let's create a tabular structure using tabs. The program is shown below:
```C
#include <stdio.h>

int main()
{
    printf("My Candy Store\n\n");
    printf("Item\t\tPrice\t\tQuantity Left\n");
    printf("----\t\t-----\t\t-------------\n");
    printf("Chocolate\t$10\t\t10\n");
    printf("Candy Pack\t$4\t\t30\n");
    printf("Lollipop\t$8\t\t25\n");
}
```


[TabTable.c](https://canvas.ust.hk/courses/44519/files/6293306/download?wrap=1 "TabTable.c") 

The output is a nicely formatted table, like this:
![[Pasted image 20220625003722.png]]
There are many more ways to control the text using **printf()**. We will discuss some of those later in the course.

## Writing Comments

Comments are extremely useful when writing computer programs. They help people understand the code even though the comments are ignored by the compiler.

You can use two different ways to write comments in C code. First, you can enclose your comments by **/*** and ***/**, for example, like this:

	/* I am a comment and ignored by the compiler */

Using **/*** and ***/** you can write comments with multiple lines too, like this:

	/* I am a comment
	   with two lines */

Another way to write comments is by putting **//** in front of the comments, like this:

	// I am another way of writing a comment

However, you cannot write multiple lines of comments with one **//**. You can only write multiple lines of comments by putting a **//** in front of every line, like this:

	// This is a comment with
	// multiple lines.
	// It is just that every
	// single line will have
	// a '//' at the start.


One good thing is that you can put your comments in almost any place, even in the middle of the code, like this:
```C
// Find out how much money I have got after going to the candy store
mymoney = 20 /* my pocket money */ -
          10 /* chocolate bar */ -
          8; /* candy */
```
## Operators

There are many operators you can use in C. You have already seen a few of them.

### The Assignment Operator

The simplest one is the assignment operator **=**. It puts something into another thing. For example, here is a statement to put the number 5 into something called **a**.

	a = 5

### Arithmetic Operators

There is a set of operators for doing arithmetic operations, as shown below:

**Operator**

**Description**

**+**

Addition

**-**

Subtraction

*****

Multiplication

**/**

Division

**%**

Modulus

Probably you don't know what the modulus operator **%** is. The modulus operator means 'the remainder of a division between two numbers'. For example, the following expression will result in the value 2:

	12 % 5

This is because if you divide 12 by 5, the remainder will be 2. Similarly, the expression **17 % 6** gives you a result of 5.

### Comparison Operators

The following set of operators allows you to compare two numbers and then give you a result of either true or false.

**Operator** **Description**

**>** Greater than

**>=** Greater than or equal to

**<** Smaller than

**<=** Smaller than or equal to

== Equal to

**!=** Not equal to

For instance, you can compare whether two numbers **a** and **b** are equal or not by using the following expression:

	a == b

If **a** and **b** are equal, the above expression will give a value of true. Otherwise, it will give a value of false. Similarly, the expression **a > b** will give a value of true if **a** is bigger than **b** and it will give a value of false otherwise.

### Logical Operators

Sometimes you need to do more than one comparisons. In that case, you have to combine the results of the comparisons using logical operators as shown below:

**Operator** **Description**

**&&** Logical AND

**||** Logical OR

**!** Negation

The operators **&&** and **||** combines two values of true/false using logical AND and logical OR respectively. For example, the following expression gets the result of comparing whether a number **a** is bigger than 5 and smaller than 10.

	a > 5 && a < 10

The operator **!** is called negation. It takes only one value of true or false and returns the opposite value, i.e. true => false and vice versa. The following expression means '**a** is not bigger than 10'.

	!(a > 10)

As you can see, a pair of parentheses has been used to enclose the expression **a > 10** before applying negation. This makes sure that the negation is evaluated on the expression **a > 10** instead of **a**. The order of evaluations of a combination of operators is called _operator precedence_.

The operator precedence in C follows closely of the precedence in mathematics. For example, multiplications and divisions are always evaluated before additions and subtractions. If you are not sure which operator is evaluated before the other, it will be better to enclose the operations you want to perform first using a pair of parentheses.