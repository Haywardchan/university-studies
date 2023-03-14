# Lesson 2.3 - Basic VBA Programming

## Showing a Message Box

In this section we will introduce some useful skills in VBA programming. The first is the use of the **MsgBox** command. Later we will talk about **InputBox** and the use of variables.

Let's start with **MsgBox**. The **MsgBox** command is used to show a few words in a small window, which we call a 'message box'. Here's an example:

![[Pasted image 20220714015548.png]]
The VBA code used to show the box is this:

MsgBox "Welcome to the Excel VBA course!"

This line of code asks VBA to show a box, i.e. a window, containing the message "Welcome to the Excel VBA course!". You can try it out by downloading the example [here](https://canvas.ust.hk/courses/44418/files/6294045/download?wrap=1 "01_msgbox_welcome.xlsm")  . If you want to you can change the title and icon by using a second and third parameter. Here is some example VBA code which does that.

MsgBox "Welcome to the Excel VBA course!", vbExclamation, "Welcome"

Looking at the above code you can see there are now second and third parameters for the **MsgBox** command. The second parameter asks VBA to show an exclamation alongside the message text. The third parameter gives the box a title of "Welcome" instead of the default "Microsoft Excel" that you can see in the first message box example. Running the above line of code will give you this window:

![[Pasted image 20220714015543.png]]
You can download the example [here](https://canvas.ust.hk/courses/44418/files/6294451/download?wrap=1 "02_msgbox_with_title.xlsm") 

There are several common icons that you can choose from. The table below shows four of them.

![[Pasted image 20220714015620.png]]

There are some other icons you can use but they are not very useful. Let's see two more examples of the **MsgBox** command.

MsgBox "I lost my mobile phone! :(", vbCritical, "Oh no!"
![[Pasted image 20220714015632.png]]
MsgBox "Did you know I just stole all your money?", vbQuestion, "Hahaha"
![[Pasted image 20220714015642.png]]
You may ask what should you do if you want to change the title of the window but you don't want to use an icon? The answer is that you can simply leave the second parameter empty. For example, this line of code:

MsgBox "Do I have an icon?", , "No icon"

will show this message box:
![[Pasted image 20220714015652.png]]
with no icon shown. You can see the above three example message boxes in the example [here](https://canvas.ust.hk/courses/44418/files/6294298/download?wrap=1 "03_msgbox_different_icons.xlsm")  .

## Getting Input From the User

We have seen the **MsgBox** command is used to show 'output'. Let's see how we can get 'input' using the **InputBox** command. Here is an example window after running the **InputBox** command:
![[Pasted image 20220714015711.png]]
Similar to a message box, the **InputBox** command gives you a small window, i.e. an input box, which contains a text message. The major difference is that in an input box the user can enter text in a text field. The user simply types something in the input box and then presses _OK_.

After the user has entered something, you need to store it before you can do something with it. You use a _variable_ to store the response. As you know from your previous programming experience, you can think of a variable as a box. There are different types of box which can hold different things. For example, you can use a _String_ variable to store text (in computers a 'string' means 'text'). We can store the text the user enters like this:

Dim Name As String
Name = InputBox("What is your name?")

In the first line:

Dim Name As String

we make the text variable, which is called _Name_. You could have used any variable name. However, keep in mind that, just like other programming languages, you cannot use some special words such as _If_, _Dim_ and _For_ as variable names. This is because they are keywords of the VBA language, and so cannot be used as variable names.

When this line of code:

Name = InputBox("What is your name?")

is executed an input box will be shown (like the one shown at the start of this page). You can then enter any text in the box and press _OK_. After pressing _OK,_ the text you enter will be stored in the variable _Name_. To use the variable, for example, you can run this line of code:

MsgBox "Hello, " & Name & "!", , "Greeting"

This code, as you can see from the example [here](https://canvas.ust.hk/courses/44418/files/6294390/download?wrap=1 "04_inputbox_greeting.xlsm")  , will show a greeting with the name entered by the user, like this:
![[Pasted image 20220714015726.png]]
Remember that you can tell VBA to change the title and icon of a message box. You can do something similar for an input box. For example, if you run this line of code:

Dim Name As String
Name = InputBox("What is your name?", "Input your name", "David")

an input box like this will be shown:
![[Pasted image 20220714015735.png]]
You can guess what those parameters are used for after looking at the above InputBox. The first parameter, "What is your name?", is the message displayed inside the window. The second parameter, "Input your name", is the title of the input box window. Finally, the last parameter, "David", is the default text shown when the input box appears, before the user does anything. You can try the example [here](https://canvas.ust.hk/courses/44418/files/6294387/download?wrap=1 "05_inputbox_default_answer.xlsm") .

## VBA Variables

You have seen how to use _String_ variables in the previous example. In addition to _String_ variables which store text, there are many other types of variable for storing other things. We will briefly look at the following types of variables.

-   _Integer_ for storing (small) integer numbers
-   _Long_ for storing (large) integer numbers
-   _Single_ for (less accurate) storing of decimal numbers
-   _Double_ for (more accurate) storing of decimal numbers

These are not the only types of variables, you will encounter some other types later.

If you want to store an integer number (i.e., a number without a fractional part) in VBA you can use an _Integer_ variable. Here's an example, which you can download [here](https://canvas.ust.hk/courses/44418/files/6294081/download?wrap=1 "06_integer_variable.xlsm") .

Dim Money As Integer
Money = InputBox("How much do you have?")
MsgBox "You have $" & Money
![[Pasted image 20220714015806.png]]
An _Integer_ variable can only handle a number in the range of -32,768 to 32,767. If you try to put a number that is outside the range of an _Integer_ variable, the code will show an error, as shown in the example below.
![[Pasted image 20220714015817.png]]
If you want to store a number larger than 32,767 or smaller than -32,768, you can use a _Long_ variable. A _Long_ variable can store a number in the range -2,147,483,648 to 2,147,483,647. The same example using a _Long_ variable looks like this (you can download this example [here](https://canvas.ust.hk/courses/44418/files/6294067/download?wrap=1 "07_long_variable.xlsm")  .

Dim Money As Long
Money = InputBox("How much do you have?")
MsgBox "You have $" & Money

In the above two examples, if you try to enter a number which has a decimal point (such as 13.4), the decimal place is dumped. The number is automatically rounded up or rounded down, like this:
![[Pasted image 20220714015832.png]]
If you want to keep the decimal place, you need to use a variable type which can handle it.

_Single_ and _Double_ are variable types which can handle numbers with decimal places. The difference between them is that _Double_ is more precise than _Single_. This can be shown in the following examples.

The first example uses a _Single_ variable to store the PI value. The resulting value has only 6 digits left after the decimal place. You can download the example [here](https://canvas.ust.hk/courses/44418/files/6294491/download?wrap=1 "08_single_variable.xlsm")  

Dim Pi As Single
Pi = InputBox("What is the value of Pi?")
MsgBox "The value of Pi is " & Pi
![[Pasted image 20220714015851.png]]
The second example uses a _Double_ variable. As you will see, the stored value has more precision than the example which uses a _Single_ variable. You can download this example [here](https://canvas.ust.hk/courses/44418/files/6294249/download?wrap=1 "09_double_variable.xlsm")  

Dim Pi As Double
Pi = InputBox("What is the value of Pi?")
MsgBox "The value of Pi is " & Pi
![[Pasted image 20220714015901.png]]
## An Example - Calculating the Body Mass Index

Let's look at an example, _Body Mass Index_, using the three topics we have covered in this section. You can download the example [here](https://canvas.ust.hk/courses/44418/files/6294026/download?wrap=1 "10_BMI.xlsm")  . The Body Mass Index (BMI) is an indicator of healthiness. It is calculated from the weight (kg) and height (m) of a person like this:

BMI = Weight / Height2

The meaning of the BMI value depends upon which BMI range it is in, as shown in this table.

![[Pasted image 20220714015916.png]]

So how do we calculate the BMI value using a VBA program? In this example we use two input boxes. The first input box asks for the weight (kg) and the second input box asks for the height (cm). After receiving the values the program calculates the BMI and shows it in a message box.

Here is the VBA code of the program:

' This function is executed when the worksheet is opened
Sub Workbook_Open()
    Dim Weight As Double, Height As Double, BMI As Double

    Weight = InputBox("Please enter your weight (kg):", _
             "Weight")
    Height = InputBox("Please enter your height (cm):", _
             "Height")

    ' Change from centimeter to meter
    Height = Height / 100

    ' Calculate the BMI
    BMI = Weight / (Height * Height)

    MsgBox "Your BMI is " & BMI & ".", , "BMI"
End Sub

Note that the underscore ('_') cuts any line of VBA code into two lines. We did this in our example code simply to improve the readibility of the code. You can put the two lines of code back into one single line without the underscore, if you wish. Using the underscore can be very useful when you want to improve the readibility of your code.

Let's see an example execution of the VBA program. We will enter 65 for the weight and 170 for the height, like this:
![[Pasted image 20220714015956.png]]
For the data we entered, the BMI is about 22.5. According to the table shown above, this is a BMI value of a normal person.