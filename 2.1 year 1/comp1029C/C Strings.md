# Lesson 4.1 - Strings

## From Arrays to Strings

Arrays are collections of 'things'. If those 'things' in an array are characters, i.e. with a data type of **char**, we call the array a _string_. In computers a 'string' basically means 'text'. More specifically, a string is any sequence of characters within quotation marks.

Here is an example of using a string in C:

char name1[] = "Ben";
char name2[] = "Jerry";

printf("My name is %s and your name is %s.", name1, name2);

The above code outputs the text **"My name is Ben and your name is Jerry."**

In the first two lines of code two arrays, called **name1** and **name2**, are declared. However, the way that these arrays are initialized is quite different from what we have learned before. Instead of using the curly braces **{}** to enclose the array items, we simply enclose the characters using a pair of double quotes **""**.

Using double quotes is a convenient way of setting up strings. For example, we could have initialized the content of **name1** using curly braces, like this:

char name1[] = { 'B', 'e', 'n', '\0' };

From the point of view of C, this does exactly the same thing. Obviously this is not as intuitive as using the double quotes. Moreover, what is the **'\0'** at the end of the array? This is called the _string terminator_, or the _null terminator_. (You can also write the character using the word **NULL**.) The word _null_ means empty or zero. The terminator tells C where the end of the string is. You need this **'\0'** at the end of every string. We call these strings _null-terminated strings_. When you use double quotes, C automatically adds **'\0'** at the end of the string so you don't need to worry about it.

Note that you can only put the double-quoted string in an array during variable declaration and initialization. You cannot put a double-quoted string in an array anywhere else.

For example, you can do this:

char howareyou[] = "How are you?";

However, you can't do this:

char howareyou[13];
howareyou = "How are you?";

Nevertheless, you can do this:

printf("My name is %s.", "Paul");

The last line of code shown above produces the text **"My name is Paul."**. It is equivalent to this code:

char name[] = "Paul";
printf("My name is %s.", name);

The limitation of using the double-quoted string seems weird but that's the way it is in the C language.

## What Can You Do with Strings?

While there are many things that we can do with strings, here are a few of the most important ones.

For example, we can find the length of a string by using the **strlen()** function from the _string_ library.

Before using the **strlen()** function, let's tell C that we are going to use the string library by including the following line of code at the top of your file:

#include <string.h>

Then we can start to use **strlen()** as well as many other string handling functions. Here is an example:

printf("%d", strlen("Hong Kong"));

This code outputs 9. **"Hong Kong"** contains a space (which is a regular character) so the total length of the string is 9.

Another thing that we can do with strings is to read the character at any given position. Here are some examples:

char name[] = "Ben";

/* Example 1 - putting some characters from a string into char variables */
char first = name[0]; // put 'B' in the variable first
char last = name[2];  // put 'n' in the variable last

/* Example 2 - directly using the characters in a printf function (note the use of %c) */ 
printf("This is how you spell \"%s\": '%c', '%c' and '%c'.", name, name[0], name[1], name[2]);

The above code outputs:

**This is how you spell "Ben": 'B', 'e' and 'n'.**

You may notice that a **"** has been used twice in this part **"%s"** to put a double quote inside a string. Maybe you would think that the obvious way to print a double quote is to put it inside a string, like this:

printf("This is how you spell "%s": '%c', '%c' and '%c'.", name, name[0], name[1], name[2]);

However, it won't work because C would think that the first double quote after the word spell, i.e. at the location **spell "**, means the end of the string. So to make C understand that you actually want to print a double quote you have to use a **"** to represent a double quote **"**.

## Copying String Content

If you want to copy the text content from one variable to another variable, you **CANNOT** do this:

char yourname[10] = "Peter";
char myname[10];

myname = yourname; // wrong!

To copy string content correctly, you have to use the **strcpy()** function. Similar to before, this function comes from the string library so you need to use the following line of code at the start of your source code file:

#include <string.h>

Here is an example of using **strcpy()**:

char yourname[10] = "Peter";
char myname[10];

// copy the content of the variable yourname into the variable myname
strcpy(myname, yourname);

**Important**

Similar to what you have done with **scanf()**. In Visual Studio Community, the IDE will give you an error if you use some of the string functions such as **strcpy()**. To avoid having the error, we will use the same instruction to disable it:

#define _CRT_SECURE_NO_WARNINGS 1

You will not get a similar error if you use other systems or development tool.

The last line of code in the above example copies the content from **yourname** into **myname**. At the start of the code, "Peter" is put in the **yourname** variable and **myname** contains nothing, like this:

![[Pasted image 20220709221857.png]]
The gray boxes in the figures mean the values are not used by the string variables.

After running the code,

// copy the content of the variable yourname into the variable myname
strcpy(myname, yourname);

both the variables **yourname** and **myname** contain the text **"Peter"**, like this:

The content of the **yourname** variable:

![[Pasted image 20220709221921.png]]

The text **"Peter"** has a size of 6, which is the number of characters plus the null terminator. To put the text **"Peter"** in the **myname** variable you need to make sure that **myname** has enough space to store the text. Since the size of **myname** is 10, **myname** has more than enough space to store the text **"Peter"**.

It is important to make sure that your target variable has enough space to store the input string when using **strcpy()**. Otherwise, the program will run into problems.

## Putting Strings Together

You can also put strings together using **strcat()**, which means 'string concatenation'. You probably already know that 'concatenation' means 'putting pieces of text together'.

Here is an example of using **strcat()**:

char message[20] = "";
char name[10] = "Peter";
char greeting[20] = "how are you?";

strcat(message, name);     // message is now "" + "Peter", i.e. "Peter"
strcat(message, ", ");     // message is now "Peter" + ", ", i.e. "Peter, "
strcat(message, greeting); // message is now "Peter, " + "how are you?",
                           // i.e. "Peter, how are you?"

// Print the message
printf("%s", message);

The above code outputs the text **"Peter, how are you?"**. There are three string variables and three lines of code using **strcat()** in the example.

Here is what's happened in the code. First, when the variables are declared, the variable **message** is initialized with the empty string **""**, the variable **name** is initialized with **"Peter"** and the variable **greeting** is initialized with **"how are you?"**.

Let's talk about the empty string first. You may think that the empty string is really empty so that nothing is stored in the **message** variable. However, this is not true. When we say empty string, it means a string with a length of 0. In order to know the end of the string, C needs to see the null terminator somewhere. As **message** is an empty string, the first position of the **message** array stores the null terminator.

Here are the variables after they are declared and initialized:

The content of the **message** variable:
![[Pasted image 20220709221809.png]]
The content of the **name** variable:
![[Pasted image 20220709222020.png]]
The content of the **greeting** variable:
![[Pasted image 20220709222036.png]]
Let's come back to the example. The first **strcat()** function puts the content of **name** at the end of **message**. Since **message** is originally empty, the content of **message** after this line of code becomes **"Peter"**, like this:
![[Pasted image 20220709222057.png]]

What **strcat()** actually does is to look for the null terminator in **message** and then put the content of **name** starting from that position. Similarly, the second **strcat()** puts together the content of **message**, which is **"Peter"** now, and the string **", "**. The resulting string in **message** then becomes **"Peter, "**, like this:
![[Pasted image 20220709222117.png]]

Finally, another piece of text **"how are you?"** is put at the end of the **message** variable in the third **strcat()** function. After running the code, the **message** variable becomes **"Peter, how are you?"**, like this:
![[Pasted image 20220709222140.png]]