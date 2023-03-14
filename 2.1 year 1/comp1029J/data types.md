![[Pasted image 20220418173855.png]]
As you can see, the **char** data type, i.e. a character, is enclosed by a pair of single quotes **'** and a string is enclosed by a pair of double quotes **"**. Although some programming languages such as Python allow the two types of quotes to be used interchangeably Java uses single quotes only for characters and double quotes only for strings.

Looking at the table you can find three data types for numbers: **int**, **float** and **double**. What are the differences between these data types?

Integer variables, i.e. **int**, store numbers without a decimal place. They don't work with real numbers. If you have a real number and you want to store it in an integer variable, you will have to throw away the decimal place first before you do that.

**float** and **double** are both used to store floating point numbers, i.e. real numbers. **float** has a lower precision and **double** has a higher precision. The tradeoff is a **double** variable occupies more memory than a **float** variable. So which one should you choose when you want to store a real number in a variable? You should almost always choose **double** because of its precision. You use **float** only in the situation where you know you have to use **a lot of** them in your program.