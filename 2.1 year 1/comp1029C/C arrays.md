# Lesson 3.3 - Arrays

## Arrays

Sometimes it's convenient to 'package' a bunch of things together in a single data structure. You've probably encountered similar structures such as lists or arrays before, in another programming language. In C you put things together in a collection using arrays.

Here is an example.

int odds[6] = { 1, 3, 5, 7, 9, 11 };

In the above code, **odds** is a variable and we've assigned that variable to be an array of six odd numbers. We have declared the array as **int** which means the items of the array must be integers. In this example, we explicitly set the size of the array, i.e. the number of items it has, to be 6. You could have also left the size value empty like this:

int odds[] = { 1, 3, 5, 7, 9, 11 };

In this case, the C compiler automatically determines the size of the array by looking at the number of items in the initialization.

We can read the value of an item from an array using indexing, i.e. getting back items based on the order which they appear inside the array. Intuitively, you may think the index of the first item is 1. However, the index of the first item in C is 0, the index of the second item is 1 and so on. Here are some examples:

char alphabets[7] = { 'A', 'B', 'C', 'D', 'E', 'F', 'G' };

// read the value 'A' and store it in the variable 'myfavorite'
char myfavorite = alphabets[0];

// read the value 'F' and store it in the variable 'idontlike'
char idontlike = alphabets[5];

In this example, **myfavorite** stores the first item of the array, which is **'A'**. When the index is 5, as shown in the last line of the above code, the 6th item is read into the variable **idontlike**, which is **'F'**.

From the declaration of the array, we know that there are 7 items in the array so the last item can be read using **alphabets[6]**, which is **'G'**.

What happens if we use **alphabets[7]**? Surprisingly, C won't give you any error, even though **alphabets[7]** does not exist! There is no way to know exactly what the value of **alphabets[7]** is. Using an out-of-range index would cause big problems in your program. Therefore, when working with arrays, you have to be very careful with the indexing. Don't mix up the numbering used by the brackets when you declare an array and read an array, i.e.:

// the size of the array is 7
char alphabets[7];

// the last item with an index 6 of the array is assigned 'F'
alphabets[6] = 'F';

As you can see in the above two lines of code, we don't need to always initialize an array. We can declare it first and then assign values to it later.

## Two Dimensional Arrays

We have looked at using an array as a collection of items. When happens if each item itself is an array? In that case, we have an array of arrays. This is called a _two dimensional array_, or simply as a _2D array_.

Let's look at this example.

char board[3][3] = { { 'o', 'x', 'o' }, { 'o', 'x', 'x' }, { 'o', 'o', 'x' } };

Similar to what we have done before we declare and initialize an array with a data type and its initial values. In this code, the first size determines the number of array items we have in the array. The second size determines the size of each array items. Combining both gives us a 3x3 array. The data type tells us that the items in second level arrays are characters.

If we layout the items in a tabular structure, typically the first index refers to the rows and the second index refers to the columns. So the example above gives a data structure like this:

o x o 
o x x
o o x

To read a value from a 2D array we use two indexes, one for the row and another for the column. Here are some examples.

// give the 'x' at the center of the board
char center = board[1][1];

// give the 'o' at the bottom-left corner of the board
char bottomleft = board[2][0];

We can use a 2D array with different number of items in each dimension. Here is an example.

int seatingplan[2][5] = {
    { 10, 5, 4, 6, 7 },
    { 2, 9, 3, 8, 1 }
}

The initial values are arranged in different lines so that we can clearly see the structure. Similar to an array with a single dimension we can leave out the size of the array, like this:

int seatingplan[][5] = {
    { 10, 5, 4, 6, 7 },
    { 2, 9, 3, 8, 1 }
}

However, only the first index can be omitted. We have to provide the correct size for the second dimension.

## Using Arrays as Function Parameters

We have learned that when we pass a variable to a function as a parameter, only the value is passed and copied to the variable inside the function. Even if we change the variable inside the function, the original variable containing the value will not be changed.

Here is an example.

void changeit(int x, int y)
{
    x = y;
}

int main()
{
    int x = 1, y = 2;
    changeit(x, y);
}

In the above example, at the end of **main()**, the variable **x** and **y** remain as 1 and 2 respectively. They have not been changed even though the **changeit()** function changes the value of the parameter **x**, which happens to have the same name of the variable in **main()**. However, keep in mind that both variables **x** are different variables local to their respective functions.

What happens if we pass an array as a function parameter? Let's see an example.

#include <stdio.h>

// Fill a 5x5 board with checker pattern
void fill(int board[5][5])
{
    int row, col;

    for (row = 0; row < 5; row++) {
        for (col = 0; col < 5; col++) {
            if (row % 2 == col % 2)
                board[row][col] = 1;
            else
                board[row][col] = 0;
        }
    }
}

// Print the content of a 5x5 board
void print(int board[5][5])
{
    int row, col;

    for (row = 0; row < 5; row++) {
        for (col = 0; col < 5; col++) {
            printf("%2d", board[row][col]);
        }
        printf("\n");
    }
}

int main()
{
    // Initialize a 2D array with zeros
    int checkerboard[5][5] = {
        { 0, 0, 0, 0, 0 },
        { 0, 0, 0, 0, 0 },
        { 0, 0, 0, 0, 0 },
        { 0, 0, 0, 0, 0 },
        { 0, 0, 0, 0, 0 }
    };

    // Print the board before filling
    printf("Initial values:\n\n");
    print(checkerboard);

    // Fill the array with checker pattern
    fill(checkerboard);

    // Print the board after filling
    printf("\nAfter filling:\n\n");
    print(checkerboard);
}

[ArrayParameter.c](https://canvas.ust.hk/courses/44519/files/6293288/download?wrap=1 "ArrayParameter.c") 

Here is the output after running the above example.
![[Pasted image 20220705210946.png]]

As you can see from the code, the array has been used as a parameter both the **fill()** and **print()** function. Only the **fill()** function changes the content of the **board** parameter. From what we have learned before the **fill()** function cannot change the content of **checkerboard** in **main()** because the variable is local to **main()** only. However, array is a special parameter type so that when an array is passed as a parameter, the actual array variable is passed onto the function.

Looking at the above code, the variable **checkerboard** is passed to the **fill()** function as a parameter called **board**. Because the parameter is an array, in effect, the **board** variable and the **checkerboard** variable are refering to the same content. Therefore, after **board** has been changed in **fill()**, you would see the same changes made in the **checkerboard** variable in **main()**. That means you need to be careful when you handle arrays as function parameters.