## Introduction Control Flow

Imagine we’re writing a program that enrolls students in courses.

* If a student has completed the prerequisites, then they can enroll in a course.
* Else, they need to take the prerequisite courses.

They can’t take Physics II without finishing Physics I.

We represent this kind of decision-making in our program using conditional or control flow statements. Before this point, our code runs line-by-line from the top down, but conditional statements allow us to be selective in which portions will run.

Conditional statements check a boolean condition and run a block of code depending on the condition. Curly braces mark the scope of a conditional block similar to a method or class.

Here’s a complete conditional statement:

```java
if (true) {
  System.out.println("Hello World!");
}
```

## IF-Then Statement

The *if-then* statement is the most simple control flow we can write. It tests an expression for truth and executes some code based on it.

```java
if (flip == 1) {
  System.out.println("Heads!");
}

boolean isValidPassword = true;
if (isValidPassword) {
  System.out.println("Password accepted!");
}
// Prints "Password accepted!"

int numberOfItemsInCart = 9;
if (numberOfItemsInCart > 12) {
  System.out.println("Express checkout not available");
}
// Nothing is printed.
```

If a conditional is brief we can omit the curly braces entirely:

```java
if (true) System.out.println("Brevity is the soul of wit");
```

## If-Then-Else

We’ve seen how to conditionally execute one block of code, but what if there are two possible blocks of code we’d like to execute?

Let’s say if a student has the required prerequisite, then they enroll in the selected course, else they’re enrolled in the prerequisite course instead.

We create an alternate conditional branch with the `else` keyword:

```java
if (hasPrerequisite) {
  // Enroll in course
} else {
  // Enroll in prerequisite
}
```

## If-Then-Else-If

The conditional structure we’ve learned can be chained together to check as many conditions as are required by our program.

Imagine our program is now selecting the appropriate course for a student. We’ll check their submission to find the correct course enrollment.

The conditional statement now has multiple conditions that are evaluated from the top down:

```java
String course = "Theatre";

if (course.equals("Biology")) {
  // Enroll in Biology course
} else if (course.equals("Algebra")) {
  // Enroll in Algebra course
} else if (course.equals("Theatre")) {
  // Enroll in Theatre course
} else {
  System.out.println("Course not found!");
}
```

## Nested Conditional Statements

We can create more complex conditional structures by creating nested conditional statements, which is created by placing conditional statements inside other conditional statements:

```java
if (outer condition) {
  if (nested condition) {
    Instruction to execute if both conditions are true
  }
}
```

When we implement nested conditional statements, the outer statement is evaluated first. If the outer condition is `true`, then the inner, nested statement is evaluated.

Let’s create a program that helps us decide what to wear based on the weather:

```java
int temp = 45;
boolean raining = true;

if (temp < 60) {
  System.out.println("Wear a jacket!");
  if (raining == true) {
    System.out.println("Bring your umbrella.");
  } else {
    System.out.println("Leave your umbrella home.");
  }
}
```

## Switch Statement

An alternative to chaining if-then-else conditions together is to use the `switch` statement. This conditional will check a given value against any number of conditions and run the code block where there is a match.

Here’s an example of our course selection conditional as a `switch` statement instead:

```java
String course = "History";

switch (course) {
  case "Algebra": 
    // Enroll in Algebra
    break; 
  case "Biology": 
    // Enroll in Biology
    break;
  case "History": 
    // Enroll in History
    break;
  case "Theatre":
    // Enroll in Theatre
    break;
  default:
    System.out.println("Course not found");
}
```

## Introduction to Conditional Operators

Java includes operators that only use boolean values. These conditional operators help simplify expressions containing complex boolean relationships by reducing multiple boolean values to a single value: `true` or `false`

For example, what if we want to run a code block only if multiple conditions are true. We could use the _AND_ operator: `&&`

Or, we want to run a code block if at least one of two conditions are `true`. We could use the OR operator: `||`

AND:
| A             | B             | A && B      |
| ------------- |:-------------:|:-----------:|
| True          | True          | True        |
| True          | False         | False       |
| False         | True          | False       |
| False         | False         | False       |

OR:
| A             | B             | A ll B      |
| ------------- |:-------------:|:-----------:|
| True          | True          | True        |
| True          | False         | True        |
| False         | True          | True        |
| False         | False         | False       |

NOT:
| A             | !A            |
| ------------- |:-------------:|
| True          | False         |
| False         | True          |

## Conditional-And: &&

We’ve nested two `if-then` statements. This does the job but we can be more concise with the AND operator:

```java
if (tuitionPaid && hasPrerequisite) {
  // enroll student
}
```

The AND operator, `&&`, is used between two boolean values and evaluates to a single boolean value. If the values on both sides are `true`, then the resulting value is `true`, otherwise the resulting value is `false`.

This code illustrates every combination:

```java
true && true
// true
false && true
// false
true && false
// false
false && false
// false
```

## Conditional-Or: ||

We’re using two different `if-then` statements with the same code block. We can be more concise with the OR operator:

```java
if (hasAlgebraPrerequisite || hasGeometryPrerequisite) {
  // Enroll in course
}
```

The OR operator, `||`, is used between two boolean values and evaluates to a single boolean value. If either of the two values is `true`, then the resulting value is `true`, otherwise the resulting value is `false`.

This code illustrates every combination:

```java
true || true
// true
false || true
// true
true || false
// true
false || false
// false
```

## Combining Conditional Operators

We have the ability to expand our boolean expressions by using multiple conditional operators in a single expression.

The order of evaluation is: the NOT operator (!) -> the AND operator (&&) -> the OR operator (||)

For example:

```java
boolean foo = true && !(false || !true)
              true && !(false || false)
              true && !false
              true && true

output: true
```