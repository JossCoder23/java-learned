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