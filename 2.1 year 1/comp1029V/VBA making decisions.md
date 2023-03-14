# Lesson 2.4 - Making Decisions in VBA

## The VBA If Statement

Like most programming languages, the VBA **If** statement is used to control the flow of the program based upon a condition.

Let's use the BMI program in the previous section as an example. At the end of the BMI program, we can add some code to display a message saying "you should start to think about weight management because your BMI is over 30." _**if**_ the calculated BMI value is over 30. In this situation the condition is "the calculated BMI value is over 30". If this condition is true, the message will be shown.

Let's see how we can achieve this using VBA code:

' This function is executed when the workbook is opened
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

    ' Check if BMI is bigger than 30
    If BMI > 30 Then
        MsgBox "You should start to think about " & _
               "weight management because your " & _
               "BMI is over 30.", vbExclamation, "Warning"
    End If
End Sub

You can download the example [here](https://canvas.ust.hk/courses/44418/files/6294043/download?wrap=1 "01_BMI_with_warning.xlsm") . If you run the program using 100 as the weight and 180 as the height, you will see a result like this:
![[Pasted image 20220714020129.png]]
Looking at the VBA code shown above you can see that we have added this code:

' Check if BMI is bigger than 30
If BMI > 30 Then
    MsgBox "You should start to think about " & _
           "weight management because your " & _
           "BMI is over 30.", vbExclamation, "Warning"
End If

Obviously a VBA **If** statement uses the following general structure:

If ...condition... Then
    ...some code...
End If

You can run as many lines of code as you like inside the **If**...End If block.

What about if the condition is false? In that case the code inside the **If**...End If block will not be executed, and the VBA program will move on to the next line of code after End If, if there is any.

## The VBA If...Else Statement

In the previous page we made a BMI program that gives a warning message for a person whose BMI value is over 30. How about people who have a BMI value of 30 or less? Let's congratulate them and tell them that they are healthy! (People are officially categorised as underweight if their BMI is under 18.5, but let's ignore that for now.)

So we want our program to do something like this:

-   If the BMI value is over 30 the program will show a 'warning' message
-   If the BMI value is less then or equal to 30 the program will show a 'healthy' message

Let's see how we can do this with **If** statements:

' Check if BMI is bigger than 30
If BMI > 30 Then
    MsgBox "You should start to think about " & _
           "weight management because your " & _
           "BMI is over 30.", vbExclamation, "Warning"
End If

' Check if BMI is less than or equal to 30
If BMI <= 30 Then
    MsgBox "You are a healthy person. Keep it up!", _
           vbInformation, "Congratulations"
End If

To do this, we just add another **If** statement at the end which handles the second case, when the BMI is less than or equal to 30. If we enter 65 for the weight and 170 for the height we will see a message like this:
![[Pasted image 20220714020148.png]]
You can download the example [here](https://canvas.ust.hk/courses/44418/files/6294254/download?wrap=1 "02_BMI_with_two_messages_using_if.xlsm")  

Let's look at the conditions of the **If** statements again. BMI > 30 and BMI <= 30 are the exact opposite of each other. That means, if one is true, the other must be false, and vice versa. In this situation, we can write the **If** statements in a more efficient way using a **If**...**Else** statement, like this:

' Check if BMI is bigger than 30 show a warning
' Otherwise, show a congratulations message 
If BMI > 30 Then
    MsgBox "You should start to think about " & _
           "weight management because your " & _
           "BMI is over 30.", vbExclamation, "Warning"
Else
    MsgBox "You are a healthy person. Keep it up!", _
           vbInformation, "Congratulations"
End If

You can download the example [here](https://canvas.ust.hk/courses/44418/files/6294072/download?wrap=1 "03_BMI_with_two_messages_using_if_else.xlsm")  . So the **If**...**Else** statement is an efficient way to express "If a condition is true, do this; otherwise, do that". The general structure of the **If**...**Else** statement is this:

If ...condition... Then
    ...some code to do if the condition is true...
Else
    ...some code to do if the condition is false...
End If

Based on the condition either one of the blocks of code is executed, but not both.

## The VBA If...ElseIf...Else Statement

In the previous page we made a BMI program which shows two different messages based on whether the BMI value is over 30 or not. However, the program did not properly reflect a person's health because we ignored cases where the BMI values are under 18.5 (meaning that the person is underweight). To make the program complete let's add the underweight case too!

To do that we need to consider these conditions in the code:

1.  If the BMI value is over 30 the program will show an overweight warning
2.  If the BMI value is under 18.5 the program will show an underweight warning
3.  If the BMI value is within the range of 18.5 and 30 the program will show a 'healthy' message

Following this logic, the program will satisfy only one of the conditions; a person can only be overweight, underweight or healthy. Instead of writing three separate **If** statements we can use the **If**...**ElseIf**...**Else** statement to express these conditions. The example can be downloaded [here](https://canvas.ust.hk/courses/44418/files/6294129/download?wrap=1 "04_BMI_with_three_messages_using_if_elseif_else.xlsm") . The revised VBA code at the end of the code is shown below:

' If BMI is bigger than 30 show an overweight warning
' If BMI is less than 18.5 show an underweight warning
' Otherwise, show a congratulations message 
If BMI > 30 Then
    MsgBox "You should start to think about " & _
           "weight management because your " & _
           "BMI is over 30.", vbExclamation, "Warning"
ElseIf BMI < 18.5 Then
    MsgBox "You should try to gain weight " & _
           "because your BMI is under 18.5.", _
           vbExclamation, "Warning"
Else
    MsgBox "You are a healthy person. Keep it up!", _
           vbInformation, "Congratulations"
End If

What is going on here? After the calculation of the BMI value (not shown in the above code), the program starts by looking at the condition where the BMI value is bigger than 30:

If BMI > 30 Then

If the condition (BMI > 30) is true, an overweight warning will be shown and the program will continue at the next line of code **after** End If (i.e., not the next condition). If the condition (BMI > 30) is false, the program will further test whether the BMI value is under 18.5:

ElseIf BMI < 18.5 Then

This is the second condition in this **If**...**ElseIf**...**Else** statement. The keyword **ElseIf** means the program will only check this condition if every condition before this **ElseIf** is false (there is only one such condition in this example). If the condition (BMI < 18.5) is true an underweight warning will be shown and the program will continue at the next line of code after End If. Finally, if the condition (BMI < 18.5) is false, which means the person is neither overweight nor underweight, a congratulations message will be shown.

To try the example you can enter 50 for the weight and 170 for the height. You will see this message box:
![[Pasted image 20220714020205.png]]
The basic structure of an **If**...**ElseIf**...**Else** statement is like this:

If ...condition 1... Then
    ...some code to do if condition 1 is true...
ElseIf ...condition 2...Then
    ...some code to do if condition 2 is true...

...you can put as many ElseIf statements here as you want...

Else
    ...some code to do if none of the above conditions is true...
End If

Can you tell the difference between using separate **If** statements and a single **If**...**ElseIf**...**Else** statement? When you use separate **If** statements all three conditions have to be evaluated. This happens even though ultimately only one of the conditions is true. However, when you use an **If**...**ElseIf**...**Else** statement the program will stop evaluating the conditions if one of them is true. Therefore, what you gain by using the **If**...**ElseIf**...**Else** statement is a saving of processing time for evaluating the conditions, which you know are not going to be true anymore. For example, if you know the BMI value is over 30 (satisfying the first condition), it is pointless to further test whether the BMI value is under 18.5 (the second condition).