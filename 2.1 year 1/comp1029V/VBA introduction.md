# Lesson 2.1 - Starting to Program with VBA

## A First Look at Excel VBA

VBA is a programming language. VBA stands for _Visual Basic for Application_s (VBA). The name reflects the nature of VBA code:

-   VBA is based upon an older language called _Visual Basic_.
-   VBA works inside some specific programs (i.e. applications), including most of the Microsoft Office programs such as PowerPoint and Word.

![VBA Logo](https://canvas.ust.hk/courses/44418/files/6294394/preview)

We will learn VBA in the context of the Microsoft Excel program. Note that VBA code is quite different to the Excel cell formula style of 'programming' that we have looked at.

### Starting VBA Code

When you work on other programming languages you usually have to write code for the starting point of a program. For example, the main() routine in a C program is the starting point of a program written in the C language. Excel VBA does not work that way. Instead, the VBA code has to be started by some kind of 'signal'.

There are two types of 'signals' that can make Excel run VBA code. The first one is a _Macro_ and the second one is an _Event_.

### Macros

Macros are useful pieces of VBA code which you can use as many times as you like. There are several ways to make a macro in Excel.

-   You can write it - if you know how to write VBA code
-   You can record it - then there's no need to write any VBA code

Sometimes you do a mixture of both of these. For example, first, you could record the macro. Then you could look at the macro VBA code to see what it is doing. Then you could adjust or extend it so it behaves differently, to make it do what you want.

### Events

There are many different possible events. For example, when someone presses _Ctrl-Z_ on the keyboard a keyboard event occurs. Or when someone clicks on something, such as a cell on a worksheet, a mouse event occurs. What can you do with events then? You can say, for example, that if a particular event occurs some code will be executed. The way that VBA works is like this:

1.  The user does something in the Excel file. For instance, he/she clicks on a cell.
2.  An event occurs (or in Computer Science language we say 'an event is triggered')
3.  Some relevant VBA code is executed

The VBA code that is used by an event is called an _event handler_.

We will look at both these methods of using VBA code.

## Using the VBA Editor

Where is the VBA code in an Excel file? To access the VBA code you need to use the _VBA editor_. To show the VBA editor, go to the _Developer_ tab near the top of the Excel window and then click on the _Visual Basic_ button, as shown on the left side of the image below:

![[Pasted image 20220714014528.png]]

However, you may not find the _Developer_ tab there. This is because the _Developer_ tab is not shown by default. You have to enable it in order to see it. To do this select _File_, _Options_ and then _Customize Ribbon_. In the _Customize Ribbon_ window tick the _Developer_ checkbox, i.e. ![Developer checkbox](https://canvas.ust.hk/courses/44418/files/6294471/preview) and then click _OK_. After that you will be able to see the _Developer_ tab near the top of your Excel window.

Let's return to look at the _Developer_ tab. If you click on the _Visual Basic_ button the VBA editor will be shown. It will look something like this:
![[Pasted image 20220714014609.png]]
You can see there is an orange box in the top-left area of the above image. Obviously, the orange box is not there when you open your VBA editor! It has been added simply to highlight the area we are now going to discuss. In this area the name of each worksheet in the Excel file is shown. In an Excel file each worksheet can have its own individual VBA code. If you double-click on one of the worksheets you will be able to see the VBA code for that worksheet (if there is any). It will be shown in the large right side area.

In the example shown above, there are one worksheet in the Excel file. You can see from reading the names that it is _Sheet1_. However, there is a second item listed as well. This item, 'ThisWorkbook', is not a worksheet. Remember that in Excel a workbook means an Excel file. 'ThisWorkbook', as the name suggests, means the Excel file as a whole. Any VBA code associated with this part, 'ThisWorkbook', applies to the whole file instead of a single worksheet.

Although everything may not be perfectly clear at this stage, don't worry! We will show examples and do some exercises which will help you understand.

## Adding Code to the Workbook

You can add code to the workbook (i.e. the Excel file) easily in the VBA editor. We will show you how to do that for the workbook open event. The open event occurs when you open an Excel file.

To add VBA code to the open event, first, you open the VBA code window for the workbook by double-clicking on 'ThisWorkbook', as shown below, inside the VBA editor.

![[Pasted image 20220714014625.png]]

After doing this you can see the VBA code window of the workbook, which is empty at this moment. In the code window you need to select the event you want to write your program in. In this example, the workbook open event will be selected by choosing 'Workbook' in the first selection box, like this:
![[Pasted image 20220714014635.png]]
Once 'Workbook' is selected,the VBA editor automatically assumes you want to write code for the open event. Therefore, you will see the event handler, Workbook_Open(), for the workbook open event showing up in the editor, like this:

![[Pasted image 20220714014650.png]]

Inside there you can start to write your VBA code for the open event. If you want to write code for other events you can select another event from the selection box on the right hand side.

In the next part we will show our first VBA example, which uses the workbook open event.

## Our First VBA Code

Let's look at our first VBA code example, which can be downloaded [here](https://canvas.ust.hk/courses/44418/files/6294045/download?wrap=1 "01_msgbox_welcome.xlsm")  .

Probably, when you load the example file into Excel you will see a security warning (the orange bar shown in the middle of the picture below). This appears whenever you load an Excel file which has some VBA code.
![[Pasted image 20220714014709.png]]
This security warning gives you a chance to refuse to run any VBA code, which can be potentially dangerous. Obviously the examples in this course are not dangerous, but Excel doesn't know that. To run the code you need to click on the 'Enable Content' button before it can work.

As soon as you give permission, the VBA code can be executed. Our first example shows a message immediately after you permit the code to run. The message looks like this:
![[Pasted image 20220714014720.png]]
The event that started running the VBA code in this case is _the workbook was opened_ (in other words, the Excel file was opened, which triggered an event).

The VBA code used in this example is shown in the image below:

![[Pasted image 20220714014743.png]]
The VBA code is stored in the 'ThisWorkbook' object and therefore the code applies to the whole Excel file. This line of code:

MsgBox "Welcome to the Excel VBA course!"

tells Excel to show a message box with the text "Welcome to the Excel VBA course!".

## Using Macros

What is a macro? It is a way for you to record the 'actions' (such as moving around a worksheet, sorting a table and so on) that you do in Excel. Once a macro is recorded you can play it back. In other words you can tell Excel to perform the recorded 'actions' all over again. You can do this as many times as you want. This is very useful if you want to perform some tedious tasks many times or if you want to do the same thing in many different places. For example, you can record a macro once and then use it many times, in different worksheets.

You don't need to know how to do VBA programming to make and use a macro. However, the recorded 'actions' in a macro are stored by Excel as a sequence of VBA code. This means that you can record a macro by, for example, clicking on a few buttons in the GUI, and then you can look at the VBA code which was created by Excel. This is very helpful for learning how to do things with VBA code!

Just to be extra clear, this is what happens when you make a macro inside Excel:

1.  _Start recording the macro_
2.  Everything you do is converted into a sequence of VBA code by Excel
3.  _Stop recording the macro_

We will look at an example shortly.

There are two types of macros:

-   _A macro which uses absolute references_  
    
    Because it uses absolute references, this type of macro will work only at one particular place in the worksheet.
    
-   _A macro which uses relative references_  
    
    Because it uses relative references, this type of macro will work anywhere in the worksheet.
    

In the next part of this course, we will make a macro which uses relative references.