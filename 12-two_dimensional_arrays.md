## Introduction to 2D Arrays

As we have learned previously, an array is a group of data consisting of the same type. This means that we can have an array of primitive data types (such as integers):

```java
[1, 2, 3, 4, 5]
```

We can even have an array of Objects. For example, the following example shows an array of String Objects:

```java
["hello", "world", "how", "are", "you"]
```

In Java, arrays are considered Objects; therefore, we can also have an array of arrays:

```java
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

These are called 2D arrays since we can logically view them as a two-dimensional matrix of values containing both rows and columns.

Additionally, we can have 2D arrays which are not rectangular in shape. These are called jagged arrays:

```java
[['a', 'b', 'c', 'd'], ['e', 'f'], ['g', 'h', 'i', 'j'], ['k']]
```

We won’t be covering jagged arrays in this lesson, but be aware that 2D arrays don’t always have to have the same number of subarrays in each array. This would cause the shape of the 2D array to not be rectangular.

Why use 2D arrays?

* It is useful to use 2D arrays for situations where you need to store and organize data by rows and columns. For example, exporting data to be used in a spreadsheet.
* You can condense multiple arrays down to a single variable using 2D arrays. For example, if you have 10 students who each have 10 different quiz grades, you can represent the overall class quiz grades as a 10x10 2D array by having each row represent a student and each column represent one of the quizzes they have taken.
* 2D arrays can be used to `map` out data. For example, if you want to create a game of tic-tac-toe, you can represent the game state by using a 3x3 2D array.

There are many other ways to use 2D arrays depending on the application. The only downside is that once initialized, no new rows or columns can be added or removed without copying the data to a newly initialized 2D array. This is because the length of arrays in Java are immutable (unable to be changed after creation).

## Declaration, Initialization, and Assignment

When declaring 2D arrays, the format is similar to normal, one-dimensional arrays, except that you include an extra set of brackets after the data type. In this example, int represents the data type, the first set of brackets [] represent an array, and the second set of brackets [] represent that we are declaring an array of arrays.

```java
int[][] intTwoDArray;
```

You can think of this as creating an array ([]) of int arrays (int[]). So we end up with int[][].

Now that we’ve declared a 2D array, let’s look at how to initialize it with starting values. When initializing arrays, we define their size. Initializing a 2D array is different because, instead of only including the number of elements in the array, you also indicate how many elements are going to be in the sub-arrays. This can also be thought of as the number of rows and columns in the 2D matrix.

```java
int[][] intArray1;
intArray1 = new int[row][column]; // cajas <- elementos dentro
```

Here is an example of initializing an empty 2D array with 3 rows and 5 columns.
```java
int[][] intArray2;
intArray2 = new int[3][5];
This results in a matrix which looks like this:
//[[0,0,0,0,0],[0,0,0,0,0],[0,0,0,0,0]]
```

If you already know what values are going to be in the 2D array, you can initialize it and write all of the values into it at once. We can accomplish this through initializer lists

* In Java, initializer lists are a way of initializing arrays and assigning values to them at the same time
* We can use this for 2D arrays as well by creating an initializer list of initializer lists

An example of an initializer list for a regular array would be:

```java
char[] charArray = {'a', 'b', 'c', 'd'};
```

Similar to how a regular initializer list defines the size and values of the array, nested initializer lists will define the number of rows, columns, and the values for a 2D array.

There are three situations in which we can use initializer lists for 2D arrays:

1. In the case where the variable has not yet been declared, we can provide an abbreviated form since Java will infer the data type of the values in the initializer lists:
```java
double[][] doubleValues = {{1.5, 2.6, 3.7}, {7.5, 6.4,5.3}, {9.8,  8.7, 7.6}, {3.6, 5.7, 7.8}};
```
2. If the variable has already been declared, you can initialize it by creating a `new` 2D array object with the initializer list values:
```java
String[][] stringValues;
stringValues = new String[][] {{"working", "with"}, {"2D", 
"arrays"}, {"is", "fun"}};
```
3. The previous method also applies to assigning a new 2D array to an existing 2D array stored in a variable.

In the next exercise, we’ll look at how to assign values of individual elements.

## Accessing Elements in a 2D Array

Let’s first review how to access elements in regular `arrays`.

For a normal array, all we need to provide is an index (starting at `0`) which represents the position of the element we want to access. Let’s look at an example!

Given an array of five Strings:

```java
String[] words = {"cat", "dog", "apple", "bear", "eagle"};
```

We can access the first element using index `0`, the last element using the length of the array minus one (in this case, `4`), and any of the elements in between. We provide the index of the element we want to access inside a set of brackets. Let’s see those examples in code:

```java
// Store the first element from the String array
String firstWord = words[0]; 

// Store the last element of the String array
String lastWord = words[words.length-1];

// Store an element from a different position in the array
String middleWord = words[2];
```

Now for 2D arrays, the syntax is slightly different. This is because instead of only providing a single index, we provide two indices. Take a look at this example:

```java
// Given a 2D array of integer data
int[][] data = {{2,4,6}, {8,10,12}, {14,16,18}};

// Access and store a desired element 
int stored = data[0][2];

Print: 6
```

There are two ways of thinking when accessing a specific element in a 2D array.
* The first way of thinking is that the first value represents a row and the second value represents a column in the matrix
* The second way of thinking is that the first value represents which subarray to access from the main array and the second value represents which element of the subarray is accessed

Using this knowledge, we now know that the result of `int stored = data[0][2];` would store the integer `6`. This is because the value `6` is located on the first row (index `0`) and the third column (index `2`). Here is a template which can be used for accessing elements in 2D arrays:

```java
datatype variableName = existing2DArray[row][column];
```

Here is another way to visualize the indexing system for our example integer array seen above. We can see what row and column values are used to access the element at each position.

```java
[data[0][0], data[0][1], data[0][2]]
[data[1][0], data[1][1], data[1][2]]
[data[2][0], data[2][1], data[2][2]]
```

When accessing these elements, if either the row or column value is out of bounds, then an `ArrayIndexOutOfBoundsException` will be thrown by the application.

## Modifying Elements in a 2D Array

Now let’s review how to modify elements in a normal array.

For a one dimensional array, you provide the index of the element which you want to modify within a set of brackets next to the variable name and set it equal to an acceptable value:

```java
storedArray[5] = 10;
```

For 2D arrays, the format is similar, but we will provide the outer array index in the first set of brackets and the subarray index in the second set of brackets. We can also think of it as providing the row in the first set of brackets and the column index in the second set of brackets if we were to visualize the 2D array as a rectangular matrix:

```java
twoDArray[1][3] = 150;
```

To assign a new value to a certain element, make sure that the new value you are using is either of the same type or is castable to the type already in the 2D array.

Let’s say we wanted to replace four values from a new 2D array called intTwoD. Look at this example code to see how to pick individual elements and assign new values to them.

```java
int[][] intTwoD = new int[4][3];

intTwoD[3][2] = 16;
intTwoD[0][0] = 4;
intTwoD[2][1] = 12;
intTwoD[1][1] = 8;
```

Example:
```java
import java.util.Arrays;
public class Main {
	public static void main(String[] args) {
		// Using the provided 2D array
	  int[][] intMatrix = {
				{1, 1, 1, 1, 1},
				{2, 4, 6, 8, 0},
				{9, 8, 7, 6, 5}
		};   
    
		// Declare and initialize a 2D array called subMatrix
		int[][] subMatrix = new int[2][2];
    subMatrix[0][0] = intMatrix[0][0] * 5;
    subMatrix[0][1] = intMatrix[0][1] * 5;
    subMatrix[1][0] = intMatrix[1][0] * 5;
    subMatrix[1][1] = intMatrix[1][1] * 5;
    
    System.out.println(Arrays.deepToString(subMatrix));
  }
}
```

## Review of Nested Loops

We’re about to look at how we can use loops to make our lives easier when working with 2D arrays. But before we do that, let’s take a moment to refresh ourselves on how nested loops work.

Nested loops consist of two or more loops placed within each other. We will be looking at one loop nested within another for 2D traversal.

The way it works is that, for every iteration of the outer loop, the inner loop finishes all of its iterations.

Here is an example using for loops:

```java
for(int outer = 0; outer < 3; outer++){
    System.out.println("The outer index is: " + outer);
    for(int inner = 0; inner < 4; inner++){
        System.out.println("\tThe inner index is: " + inner);
    }
}
```

the output of the above nested loops looks like so:
```terminal
The outer index is: 0
    The inner index is: 0
    The inner index is: 1
    The inner index is: 2
    The inner index is: 3
The outer index is: 1
    The inner index is: 0
    The inner index is: 1
    The inner index is: 2
    The inner index is: 3
The outer index is: 2
    The inner index is: 0
    The inner index is: 1
    The inner index is: 2
    The inner index is: 3
```

From this example we can see how every time the outer loop iterates one time, the inner loop iterates fully.

This is an important concept for 2D array traversal, because for every row in a two dimensional matrix, we want to iterate through every column. We will look more at this in the next exercise.

Nested loops can consist of any type of loop and with any combination of loops. Let’s take a look at a few more interesting examples.

Here is an example of nested while loops:

```java
int outerCounter = 0;
int innerCounter = 0; 
while(outerCounter<5){
    outerCounter++;
    innerCounter = 0;
    while(innerCounter<7){
        innerCounter++;
    }
}
```

We can even have some interesting combinations. Here is an enhanced for loop inside of a while loop:

```java
int outerCounter = 0;
int[] innerArray = {1,2,3,4,5};

while(outerCounter<7){
    System.out.println();
    for(int number : innerArray){
        System.out.print(number * outerCounter + " ");
    }
    outerCounter++;
}
```

The output of the above example creates a multiplication table:

```terminal
0 0 0 0 0 
1 2 3 4 5 
2 4 6 8 10 
3 6 9 12 15 
4 8 12 16 20 
5 10 15 20 25 
6 12 18 24 30 
```

This is an interesting example, because for every iteration of the while loop, we iterate through every element of an array using an enhanced for loop. This is similar to the iteration pattern we use for 2D array traversal. We will be going over that in the next exercise.

Let’s practice using nested loops!

You are in charge of controlling the amount of people who reserve seats for the world famous programming contest. You have two long arrays of integers which represent the contestant’s IDs for two days of the competition. The index of the array represents their seat number. You need to use nested for loops to find if a contestant tried to register for both days. Print out the ID of the contestants who tried to register twice as well as their seat numbers for both days.

Example:

```java
public class Main {
	public static void main(String[] args) {
		int tableSize = 10;
		for(int i = 1; i <= 10; i++){
			for(int j = 1; j <= 10; j++){
				System.out.print(i * j);
				System.out.print(" ");
			}
			System.out.println();
		}
	}
}
```

Output:
```terminal
1 2 3 4 5 6 7 8 9 10 
2 4 6 8 10 12 14 16 18 20 
3 6 9 12 15 18 21 24 27 30 
4 8 12 16 20 24 28 32 36 40 
5 10 15 20 25 30 35 40 45 50 
6 12 18 24 30 36 42 48 54 60 
7 14 21 28 35 42 49 56 63 70 
8 16 24 32 40 48 56 64 72 80 
9 18 27 36 45 54 63 72 81 90 
10 20 30 40 50 60 70 80 90 100 
```

## Traversing 2D Arrays: Introduction

In the last exercise, we reviewed how to use nested `loops` as well as how to iterate through regular `arrays` using loops. In this exercise, we will apply that knowledge in order to learn how to traverse 2D arrays.

Traversing 2D arrays using loops is important because it allows us to access many elements quickly, access elements in very large 2D arrays, and even access elements in 2D arrays of unknown sizes.

Let’s remember the structure of 2D arrays in Java:

```java
char[][] letterBlock = {{'a','b','c'},{'d','e','f'},{'g','h','i'},{'j', 'k', 'l'}};
```

In Java, 2D arrays are like normal arrays, but each element is another array. This is shown by the initialized 2D array above. The outer array consists of four elements, where each element consists of a three element subarray.

Let’s see what happens when we access elements of the outer array

```java
System.out.println(Arrays.toString(letterBlock[0]) + "\n");
System.out.println(Arrays.toString(letterBlock[1]) + "\n");
System.out.println(Arrays.toString(letterBlock[2]) + "\n");
System.out.println(Arrays.toString(letterBlock[3]) + "\n");
```

Here is the `output` of the above code:
```terminal
[a, b, c]
[d, e, f]
[g, h, i]
[j, k, l]
```

As you can see, we can retrieve the entire subarray from each of the outer array elements. If you look at how we are accessing these subarrays, we are just increasing the index. This means we can access each sub-array in the 2D array using a loop!

Let’s take a look at an example which produces the same output, but can handle any sized 2D array.

```java
for(int index = 0; index < letterBlock.length; index++){
    System.out.println(Arrays.toString(letterBlock[index]) + "\n");
}
```

Here is the result:

```terminal
[a, b, c]
[d, e, f]
[g, h, i]
[j, k, l]
```

Now let’s remember how to access a value from the subarray. Previously, we learned that we can use the double brackets `[][]`, where the first set of brackets contains the index of the element of the outer array and the second set of brackets contains the index of the element in the subarray. If we wanted to retrieve the letter `'f'` we would use:

`char storedLetter = letterBlock[1][2];`

Since we know we can use a loop to retrieve each of the subarrays stored in the outer array, we can then use a nested loop to access each of the elements from the sub-array.

You might be wondering how we can figure out the number of iterations needed in order to fully traverse the 2D array.

* In order to find the number of elements in the outer array, we just need to get the length of the 2D array.
	* `int lengthOfOuterArray = letterBlock.length;`
	* When thinking about the 2D array in matrix form, this is the height of the matrix (the number of rows)
* In order to find the number of elements in the subarray, we can get the length of the subarray after it has been retrieved from the outer array.
	* Remember that we retrieved the sub array earlier using this format:
		* `char[] subArray = letterBlock[0];`
	* Therefore, we can use this to get the length of the first subarray in the 2D array
		* `int lengthOfSubArray = letterBlock[0].length;`
		* When thinking about the 2D array in matrix form, this is the width of the matrix (the number of columns)
	* In most cases, getting the length of the first subarray in the 2D array will apply to the rest of the subarrays (if it is rectangular in shape), but there are rare occasions where the length of the subarrays could be different. This occurs if the 2D array is a jagged array. We won’t be working with any jagged 2D arrays in this lesson, but it’s something to keep in mind.

Let’s look at an example!

```java
for(int a = 0; a < letterBlock.length; a++) {
    for(int b = 0; b < letterBlock[a].length; b++) {
        System.out.print("Accessed: " + letterBlock[a][b] + "\t");
    }
    System.out.println();
}
```

You can think of the variable `a` as being the outer loop index, and the variable `b` as being the inner loop index.

Here is the output:

```terminal
Accessed: a	Accessed: b	Accessed: c	
Accessed: d	Accessed: e	Accessed: f	
Accessed: g	Accessed: h	Accessed: i	
```

Within the nested for loop, we can see that each of the subarray elements are being accessed by using the outer loop index for the outer array, and the inner loop index for the subarray.

Here is a diagram to help visualize how the 2D array is traversed using nested loops:

We don’t have to only use regular for loops for traversing 2D arrays. We can use enhanced for loops if we do not need to keep track of the indices. Since enhanced for loops only use the element of the arrays, it is a bit more cumbersome to keep track of which index we are at. This same idea applies to while and do-while loops as well. This is why we usually use regular for loops except for when we want to do something simple like printing.

We have gone over how to think about 2D array traversal in terms of arrays of arrays, but there are two main ways of thinking about traversal in terms of rows and columns. These are called row-major order and column-major order.

Example:

```java
public class Main {
	public static void main(String[] args) {
		//Given the provided 2d array
		int[][] intMatrix = {
				{ 4,  6,  8, 10, 12, 14, 16},
				{18, 20, 22, 24, 26, 28, 30},
				{32, 34, 36, 38, 40, 42, 44},
				{46, 48, 50, 52, 54, 56, 58},
				{60, 62, 64, 66, 68, 70, 79}
		};
		
		
		int sum = 0;
    	int rows = intMatrix.length;
    	int columns = intMatrix[0].length;
		for(int i = 0; i < rows; i++) {
			for(int j = 0; j < columns; j++) {
				// Add a line to calculate sum of all elements
				sum += intMatrix[i][j];
			}
		}
		System.out.println(sum);
	}
}

Output:
1337
```

## Traversing 2D Arrays: Practice with Loops

We have seen how to traverse 2D arrays using standard for loops, but in this exercise, we will practice traversing them using some other loop types. For example, you may want to only retrieve elements without keeping track of the indices using enhanced for loops, or you could continuously update the 2D array until a condition is met using while loops.

In enhanced for loops, each element is iterated through until the end of the array. When we think about the structure of 2D arrays in Java (arrays of array objects) then we know that the outer enhanced for loop elements are going to be arrays.

Let’s take a look at an example:

Given this 2D array of character data:

```java
char[][] charData = {{'a', 'b', 'c', 'd', 'e', 'f'},{'g', 'h', 'i', 'j', 'k', 'l'}};
```

Print out every character using enhanced for loops:

```java
for(char[] charRow : charData) {
    for(char c : charRow) {
        System.out.print(c + " ");
    }
    System.out.println();
}
```

Remember that the syntax for enhanced for loops looks like so: for( datatype elementName : arrayName){. Since 2D arrays in Java are arrays of arrays, each element in the outer enhanced for loop is an entire row of the 2D array. The nested enhanced for loop is then used to iterate through each element in the extracted row. Here is the output of the above code:

```terminal
a b c d e f 
g h i j k l
```

Here is an example which accomplishes the same thing, but using while loops:

```java
int i = 0, j=0;
while(i<charData.length) {
    j = 0;
    while(j<charData[i].length) {
        System.out.print(charData[i][j] + " ");
        j++;
    }
    System.out.println();
    i++;
}
```

Here is the output of the above code:

```terminal
a b c d e f 
g h i j k l
```

Notice how we can use different loop types for traversal, but still receive the same result.

Let’s work some example problems using different loop types!

```java
public class Main {
	public static void main(String[] args) {
	  int[][] binary = {
      {0, 1, 0, 1},
      {1, 1, 1, 0},
      {1, 0, 0, 1},
      {1, 0, 1, 0}
    };
	
	int onesCount = 0;
		
    for(int[] row : binary ) {
      for(int i : row) {
        onesCount += i;
      }
    }

    System.out.println(onesCount);

    String[][] wordData = {{"study", "consider", "examine", "learn"}, {"ponder", "read", "think", "cogitate"}};	
    
	int i = 0, j = 0;

    while (i < wordData.length) {

      j = 0;
      while (j < wordData[i].length) {
        System.out.println(wordData[i][j] + ": [" + i + "]" + "[" + j + "]");
        j++;
      }
      i++;
    
    }

	}
}
```

Output:

```terminal
9
study: [0][0]
consider: [0][1]
examine: [0][2]
learn: [0][3]
ponder: [1][0]
read: [1][1]
think: [1][2]
cogitate: [1][3]
```

## Traversing 2D Arrays: Row-Major Order

Row-major order for 2D arrays refers to a traversal path which moves horizontally through each row starting at the first row and ending with the last.

Although we have already looked at how 2D array objects are stored in Java, this ordering system conceptualizes the 2D array into a rectangular matrix and starts the traversal at the top left element and ends at the bottom right element.

Here is a diagram which shows the path through the 2D array:

This path is created by the way we set up our nested loops. In the previous exercise, we looked at how we can traverse the 2D array by having nested loops in a variety of formats, but if we want to control the indices, we typically use standard for loops.

Let’s take a closer look at the structure of the nested for loops when traversing a 2D array:

Given this 2D array of strings describing the element positions:

```java
String[][] matrix = {{"[0][0]", "[0][1]", "[0][2]"}, 
                     {"[1][0]", "[1][1]", "[1][2]"},
                     {"[2][0]", "[2][1]", "[2][2]"},
                     {"[3][0]", "[3][1]", "[3][2]"}};
```

Lets keep track of the total number of iterations as we traverse the 2D array:

```java
int stepCount = 0;
        
for(int a = 0; a < matrix.length; a++) {
    for(int b = 0; b < matrix[a].length; b++) {
        System.out.print("Step: " + stepCount);
        System.out.print(", Element: " + matrix[a][b]);
        System.out.println();
        stepCount++;
    }
}
```

Here is the output of the above code:
```terminal
Step: 0, Element: [0][0]
Step: 1, Element: [0][1]
Step: 2, Element: [0][2]
Step: 3, Element: [1][0]
Step: 4, Element: [1][1]
Step: 5, Element: [1][2]
Step: 6, Element: [2][0]
Step: 7, Element: [2][1]
Step: 8, Element: [2][2]
Step: 9, Element: [3][0]
Step: 10, Element: [3][1]
Step: 11, Element: [3][2]
```

The step value increases with every iteration within the inner for loop. Because of this, we can see the order in which each element is accessed. If we follow the step value in the output shows us that the elements are accessed in the same order as the row-major diagram above. Now why is that?

This is because in our for loop, we are using the number of rows as the termination condition within the outer for loop header a < matrix.length; Additionally, we are using the number of columns b < matrix[a].length as the termination condition for our inner loop. Logically we are saying: “For every row in our matrix, iterate through every single column before moving to the next row”. This is why our above example is traversing the 2D array using row-major order.

Here is a diagram showing which loop accesses which part of the 2D array for row-major order:

__Why Use Row-Major Order?__

Row-major order is important when we need to process data in our 2D array by row. You can be provided data in a variety of formats and you may need to perform calculations of rows of data at a time instead of individual elements. Let’s take one of our previous checkpoint exercises as an example. You were asked to calculate the sum of the entire 2D array of integers by traversing and accessing each element. Now, if we wanted to calculate the sum of each row, or take the average of each row, we can use row-major order to access the data in the order that we need. Let’s look at an example!

Given a 6X3 2D array of doubles:

```java
double[][] data = {{0.51,0.99,0.12},
                   {0.28,0.99,0.89},
                   {0.05,0.94,0.05},
                   {0.32,0.22,0.61},
                   {1.00,0.95,0.09},
                   {0.67,0.22,0.17}};
```

Calculate the sum of each row using row-major order:

```java
double rowSum = 0.0;
for(int o = 0; o < data.length; o++) {
    rowSum = 0.0;
    for(int i = 0; i < data[o].length; i++) {
        rowSum += data[o][i];
    }
    System.out.println("Row: " + o +", Sum: " + rowSum);
}
```

The output of the above code is:

Output:
```terminal
Row: 0, Sum: 1.62
Row: 1, Sum: 2.16
Row: 2, Sum: 1.04
Row: 3, Sum: 1.15
Row: 4, Sum: 2.04
Row: 5, Sum: 1.06
```

An interesting thing to note is that, due to the way 2D arrays are structured in Java, enhanced for loops are always in row-major order. This is because an enhanced for loop iterates through the elements of the outer array which causes the terminating condition to be the length of the 2D array which is the number of rows.

```java
public class Main {
	public static void main(String[] args) {
		// Given runner lap data
		double[][] times = {
      {64.791, 75.972, 68.950, 79.039, 73.006, 74.157}, 
      {67.768, 69.334, 70.450, 67.667, 75.686, 76.298}, 
      {72.653, 77.649, 74.245, 62.121, 63.379, 79.354}
    };
		
		double runnerTime = 0.0;
      for(int outer = 0; outer < times.length; outer++) {
        runnerTime = 0.0;
        for(int inner = 0; inner < times[outer].length; inner++) {
          System.out.println("Runner index: " + outer + ", Time index: " + inner);
          // Add a line to sum up the values in each row.
          runnerTime += times[outer][inner];
			  }
        double averageVal = 0;
        averageVal = runnerTime / times[outer].length;
        System.out.println("Sum of runner " + outer + " times: " + runnerTime);
        System.out.println("Average of runner " + outer + ": " + averageVal);
		}
	}
}
```

## Traversing 2D Arrays: Column-Major Order

Column-major order for 2D arrays refers to a traversal path which moves vertically down each column starting at the first column and ending with the last.

This ordering system also conceptualizes the 2D array into a rectangular matrix and starts the traversal at the top left element and ends at the bottom right element. Column-major order has the same starting and finishing point as row-major order, but it’s traversal is completely different

Here is a diagram which shows the path through the 2D array:

In order to perform column-major traversal, we need to set up our nested loops in a different way. We need to change the outer loop from depending on the number of rows, to depending on the number of columns. Likewise we need the inner loop to depend on the number of rows in its termination condition.

Let’s look at our example 2D array from the last exercise and see what needs to be changed.

Given this 2D array of strings describing the element positions:

```java
String[][] matrix = {{"[0][0]", "[0][1]", "[0][2]"}, 
                     {"[1][0]", "[1][1]", "[1][2]"},
                     {"[2][0]", "[2][1]", "[2][2]"},
                     {"[3][0]", "[3][1]", "[3][2]"}};
```

Let’s keep track of the total number of iterations as we traverse the 2D array. We also need to change the termination condition (middle section) within the outer and inner for loop.

```java
int stepCount = 0;
                
for(int a = 0; a < matrix[0].length; a++) {
    for(int b = 0; b < matrix.length; b++) {
        System.out.print("Step: " + stepCount);
        System.out.print(", Element: " + matrix[b][a]);
        System.out.println();
        stepCount++;
    }
}	
```

Here is the output of the above code:

```terminal
Step: 0, Element: [0][0]
Step: 1, Element: [1][0]
Step: 2, Element: [2][0]
Step: 3, Element: [3][0]
Step: 4, Element: [0][1]
Step: 5, Element: [1][1]
Step: 6, Element: [2][1]
Step: 7, Element: [3][1]
Step: 8, Element: [0][2]
Step: 9, Element: [1][2]
Step: 10, Element: [2][2]
Step: 11, Element: [3][2]
```

As you can see in the code above, the way we accessed the elements from our 2D array of strings called matrix is different from the way we accessed them when using row-major order. Let’s remember that the way we get the number of columns is by using matrix[0].length and the way we get the number of rows is by using matrix.length. Because of these changes to our for loops, our iterator a now iterates through every column while our iterator b iterates through every row. Since our iterators now represent the opposite values, whenever we access an element from our 2D array, we need to keep in mind what indices we are passing to our accessor. Remember the format we use for accessing the elements matrix[row][column]? Since a now iterates through our column indices, we place it in the right set of brackets, and the b is now placed in the left set of brackets.

Here is a diagram showing which loop accesses which part of the 2D array for column-major order:

__Why Use Column-Major Order?__

Column major order is important because there are a lot of cases when you need to process data vertically. Let’s say that we have a chart of information which includes temperature data about each day. The top of each column is labeled with a day, and each row represents an hour. In order to find the average temperature per day, we would need to traverse the data vertically since each column represents a day. As mentioned in the last exercise, data can be provided in many different formats and shapes and you will need to know how to traverse it accordingly.

Let’s look at our sum example from the last exercise, but now using column-major order.

Given a 6X3 2D array of doubles:

```java
double[][] data = {{0.51,0.99,0.12},
                   {0.28,0.99,0.89},
                   {0.05,0.94,0.05},
                   {0.32,0.22,0.61},
                   {1.00,0.95,0.09},
                   {0.67,0.22,0.17}};
```

Calculate the sum of each column using column-major order:

```java
double colSum = 0.0;
for(int o = 0; o < data[0].length; o++) {
    colSum = 0.0;
    for(int i = 0; i < data.length; i++) {
        colSum += data[i][o];
    }
    System.out.println("Column: " + o +", Sum: " + colSum);
}
```

The output of the above code is:

```terminal
Column: 0, Sum: 2.83
Column: 1, Sum: 4.31
Column: 2, Sum: 1.93
```

Let’s try an example!

We will be using the same runner data from the last exercise, but this time we are going to take the average times per lap rather than per runner. This requires that we use column-major traversal.

Example:

```java
public class Main {
	public static void main(String[] args) {
    // Given runner lap data
		double[][] times = {
      {64.791, 75.972, 68.950, 79.039, 73.006, 74.157}, 
      {67.768, 69.334, 70.450, 67.667, 75.686, 76.298}, 
      {72.653, 77.649, 74.245, 62.121, 63.379, 79.354}
    };
		
		double lapTime = 0.0;
		for(int outer = 0; outer < times[0].length; outer++){
			lapTime = 0.0;
			for(int inner = 0; inner < times.length; inner++){
				System.out.println("Lap index: " + outer + ", Time index: " + inner);
				// Add a line to sum up the values
        lapTime += times[inner][outer];
			}
			double averageVal = 0;
      averageVal = lapTime / times.length;

			System.out.println("Sum of lap " + outer + " times: " + lapTime);
			System.out.println("Average time for lap " + outer + ": " + averageVal);
		}
	}
}
```

## Combining Traversal and Conditional Logic

When working with 2D `arrays`, it is important to be able to combine traversal logic with conditional logic in order to effectively navigate and process the data. Here are a few ways in how conditional logic can affect 2D array traversal:

* Skipping or selecting certain rows and columns
* Modifying elements only if they meet certain conditions
* Complex calculations using the 2D array data
* Formatting the 2D array
* Avoiding exceptions / smart processing

Let’s go over a few examples which use these ideas:

First, let’s think about a situation where you have some string data inside a 2D array. We have an application which allows users to input events on a `calendar`. This is represented by a 5x7 2D array of `strings`. Due to the fact that the number of days in each month is slightly different and that there are less than 35 days in a month, we know that some of our elements are going to be empty. We want our application to do a few things:

* Detect which days of which weeks have something planned and alert us about the event.
* Count the number of events for each week
* Count the number of events for each day

Here is a visualization of what our calendar data looks like after a user has entered in some event information:

Here’s what our calendar data looks like in our application

```java
String[][] calendar = {
	{"volunteer", "delivery", null, null, "doctor", null, "soccer"}, 
	{null, "exam 1", null, "mechanic", null, null, "soccer"}, 
	{"volunteer", "off work", null, "birthday", null, "concert", null}, 
	{null, "exam 2", null, null, "doctor", null, "soccer"}, {"visit family", null, null, null, null, null, null}
};
```

Let’s look at some code which accomplishes the requirements above. Carefully look through each line of code and read all of the `comments`.

There are a few things to note:

* Row-major or column-major order can be used to access the individual events
* Row-major order must be used to count the number of events per week since each row represents a week

Let’s take care of the first 2 requirements in one set of nested row-major loops

```java
for(int i = 0; i < calendar.length; i++) {
    numberOfEventsPerWeek = 0;
    for(int j = 0; j < calendar[i].length; j++) {
        // We need conditional logic to ensure that we do not count the empty days
        String event = calendar[i][j];
        if(event!=null && !event.equals("")) {
            // If the day does not have a null value and an empty string for an event, then we print it and count it
            System.out.println("Week: " + (i+1) + ", Day: " + (j+1) + ", Event: " + event);
            numberOfEventsPerWeek++;
        }
    }
    System.out.println("Total number of events for week "+ (i+1) +": " + numberOfEventsPerWeek + "\n");
}
```

The above code produces this output:

```terminal
Week: 1, Day: 1, Event: volunteer
Week: 1, Day: 2, Event: delivery
Week: 1, Day: 5, Event: doctor
Week: 1, Day: 7, Event: soccer
Total number of events for week 1: 4

Week: 2, Day: 2, Event: exam 1
Week: 2, Day: 4, Event: mechanic
Week: 2, Day: 7, Event: soccer
Total number of events for week 2: 3

Week: 3, Day: 1, Event: volunteer
Week: 3, Day: 2, Event: off work
Week: 3, Day: 4, Event: birthday
Week: 3, Day: 6, Event: concert
Total number of events for week 3: 4

Week: 4, Day: 2, Event: exam 2
Week: 4, Day: 5, Event: doctor
Week: 4, Day: 7, Event: soccer
Total number of events for week 4: 3

Week: 5, Day: 1, Event: visit family
Total number of events for week 5: 1
```

Now let’s complete the third requirement. Since we need to count all of the events for each of the weekdays, we will need to traverse the calendar vertically.

```java
int numberOfEventsPerWeekday = 0;
// We will use this array of day strings for our output later on so we don't have (day: 1)
String[] days = {"Sundays", "Mondays", "Tuesdays", "Wednesdays", "Thursdays", "Fridays", "Saturdays"};
for(int i = 0; i < calendar[0].length; i++) {
    numberOfEventsPerWeekday = 0;
    for(int j = 0; j < calendar.length; j++) {
        // Don't forget to flip the iterators in the accessor since we are flipping the direction we are navigating.
        // Remember, i now controls columns and j now controls rows
        String event = calendar[j][i];
        if(event!=null && !event.equals("")) {
            // Make sure we have an event for the day before counting it
            numberOfEventsPerWeekday++;
        }
    }
    // Use the days string array from earlier to convert the day index to a real weekday string
    System.out.println("Number of events on " + days[i] + ": " + numberOfEventsPerWeekday);
}
```

The `output` is:

```terminal
Number of events on Sundays: 3
Number of events on Mondays: 4
Number of events on Tuesdays: 0
Number of events on Wednesdays: 2
Number of events on Thursdays: 2
Number of events on Fridays: 1
Number of events on Saturdays: 3
```

This example uses many of the concepts we have learned before. We use row-major order, column-major order, as well as including conditional logic to ensure that we have data for the elements we are accessing.

Additionally, we can use conditional logic to skip portions of the 2D array. For example, let’s say we wanted to print the events for weekdays only and skip the weekends.

We could use a conditional statement such as `if(j!=0 && j!=6)` in order to skip Sunday (`0`) and Saturday (`6`).

These modifications to our 2D array traversal are very common when processing data in applications. We need to know which cells to look at (skipping column titles for example), which cells to ignore (empty data, invalid data, outliers, etc.), and which cells to convert (converting string input from a file to numbers).

Let’s try an example!

We are making a simple grayscale image editor program and we want to apply some modifications to the image. We have a 4x8 pixel image that is stored as a 2D array of integers. The integer value represents the brightness of the pixel, where the acceptable values are between `0` and `255`, inclusive.

```java
import java.util.Arrays;
public class Main {

	public static void main(String[] args) {

		int[][] imageData={
      {100,90,255,80,70,255,60,50},
			{255,10,5,255,10,5,255,255},
			{255,255,255,0,255,255,255,75},
			{255,60,30,0,30,60,255,255}
    };

		// Declare and initialize the 2D array newImage
		int[][] newImage = new int[4][6];

		// Add a nested `for` loop and copy the data of `imagedata` to `newImage`
    for(int i = 0; i < newImage.length; i++) {
      for(int j = 0; j < newImage[i].length; j++) {
        newImage[i][j] = imageData[i][j];
      }
    }

		System.out.println(Arrays.deepToString(newImage));
			
		for(int i=0; i< newImage.length; i++){
      for(int j=0; j< newImage[i].length; j++){
        // Add the if-else statement here
         if(newImage[i][j]-50<0){
          newImage[i][j] = 0;
        }
        else{
          newImage[i][j]-=50;
        }
      }
    }
		System.out.println(Arrays.deepToString(newImage));
    
	}

}
```

Output:
```terminal
[[100, 90, 255, 80, 70, 255], [255, 10, 5, 255, 10, 5], [255, 255, 255, 0, 255, 255], [255, 60, 30, 0, 30, 60]]
[[50, 40, 205, 30, 20, 205], [205, 0, 0, 205, 0, 0], [205, 205, 205, 0, 205, 205], [205, 10, 0, 0, 0, 10]]
```

## 2D Array Review

Let’s review the concepts we have learned throughout this lesson.

Arrays are objects in Java, we can have `arrays` of objects, therefore we can also have arrays of arrays. This is the way 2D arrays are structured in Java.

We can declare and initialize 2D arrays in a few different ways depending on the situation:

```java
// Declaring without initializing
int[][] intTwoD;

// Initializing an empty 2D array which has already been declared
intTwoD = new int[5][5];

// Declaring and initializing an empty 2D array at once
String[][] stringData = new String[3][6];

// Declaring and initializing a 2D array using initializer lists
double[][] doubleValues = {{1.5, 2.6, 3.7}, {7.5, 6.4, 5.3}, {9.8,  8.7, 7.6}, {3.6, 5.7, 7.8}};

// Initializing a 2D array using initializer lists after it has already been declared, or already contains data;
char[][] letters = new char[100][250];
letters = new char[][]{{'a', 'b', 'c'}, {'d', 'e', 'f'}};
```

We retrieve elements in a 2D array by providing a row and column index char `c = letters[0][1];`

* We can also think of them as the index of the outer array and the index of the subarray
* We can modify elements the same way `letters[1][2] = 'z';`

We traverse 2D arrays using nested `loops`.

* We can use loops of any type, but we typically use nested for loops to keep track of the indices
* Row-major order traverses through each row moving horizontally to the right through each row
* Column-major order traverses through each column moving vertically down through each column
* Row-major order and column-major order start and end on the same elements, but the paths are different.
* In order to convert row-major to column-major, we need to make the outer loop terminating condition depend on the number of columns, make the inner loop terminating condition depend on the number of rows, and flip the `variables` in our accessor within the inner loop to ensure that we don’t try to access outside of the 2D array since we flipped the direction of traversal. 

Here are examples of row-major and column-major order:

```java
// Row-major order
for(int o = 0; o < letters.length; o++) {
    for(int i = 0; i < letters[o].length; i++) {
        char c = letters[o][i];
    }
}

// Column-major order
for(int o = 0; o < letters[0].length; o++) {
    for(int i = 0; i < letters.length; i++) {
        char c = letters[i][o];
    }
}
```

Conditional logic in our 2D array traversal allows us to use the data in a meaningful way. We can control which rows and columns we look at, ensure that the data we are looking at is what we want, perform calculations on specific elements, avoid throwing exceptions, and more.

Here is an example of traversal with conditional logic.

Given this 2D array of Strings:

```java
String[][] words = {{"championship", "QUANTITY", "month"},{"EMPLOYEE", "queen", "understanding"},{"method", "writer", "MOVIE"}};
```

We are going to flip the capitalization of the words:

```java
System.out.println("Before...");
System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");

for(int i=0; i<words.length; i++) {
  for(int j = 0; j<words[i].length; j++) {
    if(words[i][j]!=null) {

      // Check the capitalization
      boolean allCaps = true;
      for(char c : words[i][j].toCharArray()) 
          if(!Character.isUpperCase(c)) 
              allCaps = false;
          
      // Flip the capitalization
      if(allCaps)
          words[i][j] = words[i][j].toLowerCase();
      else
          words[i][j] = words[i][j].toUpperCase();
    }
  }
}

System.out.println("After...");
System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");
```

Here is the `output` of the above code:

```terminal
Before...
[[championship, QUANTITY, month],
 [EMPLOYEE, queen, understanding],
 [method, writer, MOVIE]]

After...
[[CHAMPIONSHIP, quantity, MONTH],
 [employee, QUEEN, UNDERSTANDING],
 [METHOD, WRITER, movie]]
```

Time to work some review problems!

After learning about 2D arrays, you have decided to become a CS professor and you are now teaching your class about 2D arrays. You are making an application which will keep track of their exam grades and show you statistics about their performance. You will be using 2D arrays to keep track of their exam grades

