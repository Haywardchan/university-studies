### Lesson 2.3 - While Loops

## While Loops

Sometimes, we don't know how many times we need to loop. In such cases, **while** loops are very useful. Let's start with an example.

The program below takes a number as the amount of money we have. It then uses the money to buy big chocolate bars for $5 and small chocolate bars for $2. The program tries to buy as many big chocolate bars as possible. For example, if we have $8, we will be able to buy one big chocolate bar and one small chocolate bar.
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    // Takes the amount of money the user has and then buy as many chocolate
    // bars as possible.

    // Ask for the amount of money
    printf("Please enter the amount of money you have: ");
    int amount;
    scanf("%d", &amount);

    int bigbars = 0, smallbars = 0;

    // While there is enough money to buy at least one small chocolate bar...
    while (amount >= 2) {
        // Buy a big chocolate bar if there is at least $5 left
        if (amount >= 5) {
            bigbars++;
            amount = amount - 5;
        }
        // Buy a small chocolate bar if there is not enough money for a big bar
        else {
            smallbars++;
            amount = amount - 2;
        }
    }

    printf("You can buy %d big chocolate bar(s) and %d small chocolate bar(s).\n",
        bigbars, smallbars);
}
```

[ChocoBar.c](https://canvas.ust.hk/courses/44519/files/6293298/download?wrap=1 "ChocoBar.c") 

Here are some examples of running the above program:
![[Pasted image 20220625014956.png]]
![[Pasted image 20220625015006.png]]
![[Pasted image 20220625015014.png]]
Let's look at the **while** loop in the example.

The plan is to find out how many big chocolate bars (the variable **bigbars**) and small chocolate bars (the variable **smallbars**) we can buy using the amount of money we have. The initial amount of money is stored in the variable **amount**.

As you can see, the **while** statement is testing if the amount is bigger than or equal to 2. We use this condition because we can buy more chocolate bars if we have at least $2 left (i.e. **amount >= 2**). If so, we enter the body of the **while** loop - the line or lines that are inside a pair of braces after it. Those lines of code help us buy a big chocolate bar or a small chocolate bar. The type of chocolate bar we buy depends on the amount of money left. After buying a chocolate bar, the amount is adjusted according to the price of the bar. This process is repeated until the Boolean test in the **while** loop, namely **amount >= 2**, becomes False. At that point, we do not have any more money to buy chocolate bars. Therefore, we continue past the **while** loop to the next statement after the **while** statement. In our code, that's the statement containing the **printf()** function.

## Do While Loops

A **do while** loop works very similarly to a **while** loop. A **while** loop evaluates the loop condition at the start whereas a **do while** loop evaluates the loop condition at the end.

A **while** loop:
```C
while (loop condition) {
    ...loop content...
}
```

A **do while** loop:
```C
do {
    ...loop content...
} while (loop condition);
```

That means a **while** loop may not run the loop content at all, e.g. when the loop condition is False at the very beginning. A **do while** loop always runs the loop content at least once because the loop condition is evaluated after running the loop content.

Let's show a program using a **do while** loop.
```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>

int main()
{
    // This program shows a smiley the user has selected from a menu

    int smiley;
    do {
        // Ask the user to select a smiley
        printf("Which smiley do you want to see (or select 6 to quit)?\n\n");
        printf("1) Happy\n");
        printf("2) Sad\n");
        printf("3) Winking\n");
        printf("4) Surprised\n");
        printf("5) Tongue Out\n");
        printf("6) Quit the program.\n");
        printf("\nSelect: ");

        // Get the selection
        scanf("%d", &smiley);

        // Print the smiley
        printf("\n");
        switch (smiley) {
        case 1:
            printf(":)");
            break;
        case 2:
            printf(":(");
            break;
        case 3:
            printf(";)");
            break;
        case 4:
            printf(":o");
            break;
        case 5:
            printf(":p");
            break;
        case 6:
            printf("Bye bye!");
            break;
        default:
            printf("What? (@_@)");
        }
        printf("\n\n");
    } while (smiley != 6); // Stop only if the user selects 6
}
```

[Smilies.c](https://canvas.ust.hk/courses/44519/files/6293234/download?wrap=1 "Smilies.c") 

The program shown above asks you to select a smiley and then it will show you the selected one. By using a **do while** loop the program makes sure that the question is asked at least once before you can stop it.

Here is an example of running the program.
![[Pasted image 20220625015301.png]]
### For Loop Or While Loop?

Let's do one more example that uses **for** loops and **while** loops.

The value of π (Pi) can be estimated using the following formula:
$$\sum_{k=1}^{\infty}\frac{4(-1)^{k+1}}{2k-1}$$
Suppose we need to write a program to calculate the value of Pi. We cannot exactly use the above formula in the program because the formula sums an infinite number of terms. What we can do is to calculate the first n terms of the formula, where n is a finite number, like this:

$$\sum_{k=1}^{n}\frac{4(-1)^{k+1}}{2k-1}$$

We have two ways to do that.

First, you can write a program to calculate the value of Pi up to the first n terms in the formula. Should we use a **for** loop or **while** loop? Remember that a **for** loop is preferable when we know in advance how many times to loop whereas a **while** loop is ideal when we don't know that in advance. In this situation, we know the value of n beforehand so we will use a **for** loop to do that.

Let's assume that a variable **n** has been declared and the number of terms is stored in this variable. The following code estimates the value of Pi using the first n terms.
```C
double pi = 0.0;
int k;

for (k = 1; k <= n; k++) {
    pi += (4 * pow(-1.0, k + 1)) / (2 * k - 1);
}
```

In the above code, the **pow(x, y)** function is used to calculate **x** to the power of **y**. To use the **pow()** function, we need to use the math library by including the following line of code at the top of the source file:
```C
#include <math.h>
```

Back to the **for** loop, if the value of **n** is 5, then the value of **pi** will be 3.339683 at the end of the **for** loop. If the value of **n** is 20, then the value of **pi** will be 3.091624. If the value of **n** is 40, then the value of **pi** will be 3.116597. You may find it strange that the value of **pi** fluctuates as **n** increases. The way the formula works is to converge to the correct value of **pi** by swinging around it.

You can see that after the first 40 terms are calculated, the value of **pi** is still some way off the more accurate value, which is supposed to be 3.1415.... Even if **n** is 1000, the value of **pi** will still only be 3.140593. We could have improved the accuracy by increasing the number of terms. However, is there a better way to do it?

An alternative way is to use a **do while** loop, like this:

double pi = 0.0, term;
int k = 1;

do {
    term = (4 * pow(-1.0, k + 1)) / (2 * k - 1);
    pi += term;
    k++;
} while (fabs(term) > pow(0.1, places));

The above code continuously sums the terms in the formula until the value of the term is smaller than some number. Since the value of the variable **term** can either be positive or negative, the **fabs()** function (i.e. the absolute value) is used to change the value to positive.

The final value of the **term** variable is restricted by the value of **pow(0.1, places)**. We assume that the **places** variable has been declared and filled with the number of desired accuracy in terms of the number of decimal places. If **places** is 2 the loop will stop when the value of **term** is smaller than or equal to 0.01.

You do not know the number of iterations the **do while** loop will run but you will be able to get a number in your desired accuracy. For example, if **places** is 6, the value of **pi** will be 3.141593. This is a fairly accurate number. However, you may find the loop takes at least a few seconds to compute that value.