# Lesson 4.2 - Structures

## C Structures

We have learned how to arrange a group of things into an array in C. Using an array, you can group together the same type of things, i.e. things with the same data type.

In real life, we can group many things together. For example, a movie can have information such as title, released year, language and so on. Intuitively, when we write a program about movies, we should group all this information together to form one movie. Obviously, we cannot use an array to do that because the data types of the information are different to each other.

In this situation, we can use a C _structure_ to group different things together. Here is an example:

struct movieinfo {
    char title[50];
    int year;
    char language;
};

The above code uses the **struct** statement to create a structure called **movieinfo**. As you can see, there are three things inside this structure, i.e. the three 'variables' declared inside the brackets. They are the 'members' of the structure with certain data types.

After using the **struct** statement, the structure **movieinfo** becomes a new data type that you can use to create variables in the rest of the code. We cannot use the variables inside **movieinfo** at this stage because **movieinfo** is only a data type.

To use the structure we need to declare a variable using the structure data type, like this:

struct movieinfo hobbit;

The variable **hobbit** is then a variable of the data type **movieinfo**, which is a structure containing three different values. To use one of the member values, you can put the name of the member after the structure variable separated by a dot (**.**).

Here is an example of setting up the values inside the structure:

// Put the title in the structure
strcpy(hobbit.title, "The Hobbit - An Unexpected Journey");

// Set the year to the value 2012
hobbit.year = 2012;

// Set the language to 'E', representing English in the example
hobbit.language = 'E';

As you can see, to set the value of the member **year** in the **movieinfo** structure, you use **hobbit.year**. Then, to read a value from the structure, you use the same way to specify the structure members. Here is an example:

printf("Current movie is '%s' (%d [%c]).", hobbit.title, hobbit.year, hobbit.language);

The above line of code outputs:

**Current movie is 'The Hobbit - An Unexpected Journey' (2012 [E]).**

The code is shown in [MovieInfoStructure.c](https://canvas.ust.hk/courses/44519/files/6293317/download?wrap=1 "MovieInfoStructure.c") 

## Nested Structures

You have seen how useful a C structure is when you need to group different things together.

Let's say we need to write a program to store an iPhone's information. We can use the following C structure to store it:

struct iphoneinfo {
    char colour;  // 'B' means black and 'W' means white
    int capacity; // capacity in GB
    int price;    // price in HKD
};

We can then store some actual values into it.

// Define the information of a phone using the structure
struct iphoneinfo myphone;

myphone.colour = 'B';
myphone.capacity = 64;
myphone.price = 6799;

The above code creates a structure called **iphoneinfo** and declares a variable **myphone** using the newly created structure. The variable is then assigned the information of a black iPhone with 64GB of memory that costs HKD6,799.

Let's assume that we now want to add the dimension of the iPhone, i.e. height, width and depth, to the data structure. To do that, we can extend the structure like this:

struct iphoneinfo {
    char colour;  // 'B' means black and 'W' means white
    int capacity; // capacity in GB
    int price;    // price in HKD

    // Dimension in cm
    float height;
    float width;
    float depth;
};

The above structure works fine. An alternative way to do that is to use a _nested structure_ like this:

struct dimensioninfo {
    // Dimension in cm
    float height;
    float width;
    float depth;
};

struct iphoneinfo {
    char colour;  // 'B' means black and 'W' means white
    int capacity; // capacity in GB
    int price;    // price in HKD

    struct dimensioninfo dimension; // dimension of the phone, which uses the other structure
};

As you can see, we have used another newly created structure **dimensioninfo** inside the **iphoneinfo** structure. Using a structure inside another structure is called a nested structure.

Here is an example of how to use the values inside a nested structure:

struct iphoneinfo myphone;

myphone.dimension.height = 146.7;
myphone.dimension.width = 71.5;
myphone.dimension.depth = 7.4;

What are the advantages of using a nested structure?

First, a nested structure gives you a better organization of information inside a structure. Second, you can reuse structures which are common to different things. For example, we could use the **dimensioninfo** structure again if we want to store an Android phone's information, like this:

struct dimensioninfo {
    // Dimension in cm
    float height;
    float width;
    float depth;
};

struct androidinfo {
    char model[100]; // model of the phone
    char OS[20];     // current Android OS

    struct dimensioninfo dimension; // dimension of the phone, which uses the other structure
};

We can start to fill some information into the structure.

// Define the information of an Android phone using the structure
struct androidinfo galaxy;

strcpy(galaxy.model, "Samsung Galaxy Note20");
strcpy(galaxy.OS, "Android 10");
galaxy.dimension.height = 161.6;
galaxy.dimension.width = 75.2;
galaxy.dimension.depth = 8.3;

Certainly, if the **dimensioninfo** structure has been created before you do not need to define it again.

The use of both structures can be found in [PhoneInfoStructure.c](https://canvas.ust.hk/courses/44519/files/6293315/download?wrap=1 "PhoneInfoStructure.c") 

## Arrays of Structures

After creating a structure, it becomes a data type which can be used in the rest of the code. We can then create an array using that structure, just like what we usually do with the normal data types.

For example, let's say we have defined a **movieinfo** structure like this:

struct movieinfo {
    char title[50];
    int year;
};

After creating the structure we can use it to create an array of **movieinfo**, as shown in the following example:

// Create a variable to store the information of the six Starwars movies
struct movieinfo starwars[6];

strcpy(starwars[0].title, "Star Wars Episode IV: A New Hope");
starwars[0].year = 1977;

...more movies here...

strcpy(starwars[5].title, "Star Wars Episode III: Revenge of the Sith");
starwars[5].year = 2005;

The above example creates an array with six items using the **movieinfo** structure. The data type of each item is **movieinfo** and therefore we can use each item to store information of a movie.

Using the array, we can easily print them out from a for loop, like this:

for (i = 0; i < 6; i++) {
    printf("%s (%d)\n", starwars[i].title, starwars[i].year);
}

The code can be found in [MovieInfoArray.c](https://canvas.ust.hk/courses/44519/files/6293316/download?wrap=1 "MovieInfoArray.c") 

## Using **typedef**

You may find it a bit tedious to write **struct movieinfo** every time you need to create a variable from the **movieinfo** structure. The **typedef** command allows you to shorten the type name by using an 'alternative name'. The alternative name is also called the alias.

For example, we can use **MovieInfo** to be the alias of the structure using **typedef**:

typedef struct movieinfo MovieInfo;

From the above code onwards, the structure can be declared like this:

MovieInfo starwars[6];