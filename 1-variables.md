datos primitivos:
```int, double, boolean, char``` 

datos objetos (con comportamiento):
```String```

```java
String greeting = "Hello World";
String salutations = new String("Hello World");
```

## Variables
* **int**, which stores whole numbers. 
* **double**, which stores bigger whole numbers and decimal numbers.
* **boolean**, which stores true and false.
* **char**, which stores single characters using single quotes.
* **String**, which stores multiple characters using double quotes.
* Static typing, which is one of the safety features of Java.
* Variable naming conventions.

## Manipulating variables
```java
// declare initial balance
double balance = 20000.99;
// declare deposit amount
double depositAmount = 1000.00;
// store result of calculation in our original variable
balance = balance + depositAmount;
```

## Compound assignment operators
```java
int numCupcakes = 12;
numCupcakes = numCupcakes + 8; //value is now 20
```

Addition (+=)
Subtraction (-=)
Multiplication (*=)
Division (/=)
Modulo (%=)

## Order of Operations

1. Parentheses
2. Exponents
3. Modulo/Multiplication/Division
4. Addition/Subtraction

## Greater Than and Less Than

Java has relational operators for numeric datatypes that make boolean comparisons. These include less than (<) and greater than (>), which help us solve our withdrawal problem.

```java
double balance = 20000.01;
double amountToWithdraw = 5000.01;
System.out.print(amountToWithdraw < balance);
//this will print true, since amountToWithdraw is less than balance
```

## Equals and Not Equals

So how would we validate our paycheck to see if we got paid the right amount?

We can use another relational operator to do this. == will tell us if two variable are equal:

```java
double paycheckAmount = 620;
double calculatedPaycheck = 15.50 * 40;

System.out.print(paycheckAmount == calculatedPaycheck);
// This will print true, since paycheckAmount equals calculatedPaycheck


double balance = 20000.0;
double amountToDeposit = 620;
double updatedBalance = balance + amountToDeposit;

boolean balanceHasChanged = balance != updatedBalance;
// balanceHasChanged holds true, since balance does not equal updatedBalance
```

## Greater/Less Than or Equal To

How could we make sure we got paid at least the amount we expected in our paycheck? We could use greater than or equal to, >=, or less than or equal to, <=.

```java
double paycheckAmount = 620;
double calculatedPaycheck = 15.50 * 40;
System.out.println(paycheckAmount >= calculatedPaycheck);
//this will print true, since paycheckAmount equals calculatedPaycheck
```

## .equals()

For the purposes of this lesson (as well as good practice) remember to use .equals() instead of == when comparing objects.

To use it, we call it on one String, by using ., and pass in the String to compare against in parentheses:

```java
String person1 = "Paul";
String person2 = "John";
String person3 = "Paul";

System.out.println(person1.equals(person2));
// Prints false, since "Paul" is not "John"

System.out.println(person1.equals(person3));
// Prints true, since "Paul" is "Paul"
```

## String Concatenation

With the value of the variable username displayed.

The + operator, which we used for adding numbers together, can be used to concatenate Strings. In other words, we can use it to join two Strings together!

```java
String username = "PrinceNelson";
System.out.println("Your username is: " + username);
```

## final Keyword

To declare a variable with a value that cannot be manipulated, we need to use the final keyword. To use the final keyword, prepend final to a variable declaration like so:

```java
final int yearBorn = 1968;
```