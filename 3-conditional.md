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