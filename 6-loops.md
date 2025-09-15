## While We're Here

A `while` loop looks a bit like an `if` statement:

```java
while (silliness > 10) {

  // code to run

}
```

Like an `if` statement, the code inside a `while` loop will only run if the condition is `true`. However, a `while` loop will continue running the code over and over until the condition evaluates to `false`. So the code block will repeat until `silliness` is less than or equal to 10.

```java
// set attempts to 0
int attempts = 0;

// enter loop if condition is true
while (passcode != 0524 && attempts < 4) {

  System.out.println("Try again.");
  passcode = getNewPasscode();
  attempts += 1;

  // is condition still true?
  // if so, repeat code block
}
// exit when condition is not true
```

`While loops` are extremely useful when you want to run some code until a specific change happens. However, if you aren´t certain that change will occur, beware the infinite loop!

Infinite loops occur when the condition will never evalute to `false`. This can cause your entire program to crash.

```java
int hedgehogs = 5;

// This will cause an infinite loop:
while (hedgehogs < 6) {

  System.out.println("Not enough hedgehogs!");

}
```

In the example above, `hedgehogs` remains equal to `5`, which is less than `6`. So we would get an infinite loop.


## Incrementing While Loops

When looping through code, it’s common to use a counter variable. A counter (also known as an iterator) is a variable used in the conditional logic of the loop and (usually) incremented in value during each iteration through the code. For example:

```java
// counter is initialized
int wishes = 0;

// conditional logic uses counter
while (wishes < 3) {

  System.out.println("Wish granted.");
  // counter is incremented
  wishes++;

}
```

In the above example, the counter `wishes` gets initialized before the loop with a value of `0`, then the program will keep printing `"Wish granted."` and adding `1` to `wishes` as long as `wishes` has a value of less than `3`. Once `wishes` reaches a value of 3 or more, the program will exit the loop.

So the `output` would look likes:

```terminal
Wish granted.
Wish granted.
Wish granted.
```

We can also decrement counters like this:

```java
int pushupsToDo = 10;

while (pushupsToDo > 0) {

  doPushup();
  pushupsToDo--;

}
```

In the code above, the counter, `pushupsToDo`, starts at 10, and increments down one at a time. When it hits 0, the loop exits.

## For Loops

```java
for( int i = 0;  i < 3 ; i++ ) {
  System.out.println("i is now" + i);
}

Output:
i is now 0
i is now 1
i is now 2
```

Example:
```java
class Coffee {
  
  public static void main(String[] args) {
    
    for( int cupsOfCoffee = 1; cupsOfCoffee <= 100; cupsOfCoffee++ ) {
      System.out.println("Fry drinks cup of coffee #" + cupsOfCoffee);
    }
    
  }
  
}
```

## Iterating Over Arrays and ArrayLists

One common pattern we’ll encounter as a programmer is traversing, or looping, through a list of data and doing something with each item. In Java, that list would be an `array` or `ArrayList` and the loop could be a `for` loop. But wait, how does this work?

In order to traverse an array or `ArrayList` using a loop, we must find a way to access each element via its index. We may recall that `for loops` are created with a counter variable. We can use that counter to track the index of the current element as we iterate over the list of data.

Because the first index in an array or `ArrayList` is `0`, the counter would begin with a value of `0` and increment until the end of the list. So we can increment through the array or `ArrayLis` using its indices.

For example, if we wanted to add `1` to every `int` item in an array `secretCode`, we could do this:

```java
for (int i = 0; i < secretCode.length; i++) {
  // Increase value of element value by 1
  secretCode[i] += 1;
}
```

Notice that our condition in this example is `i < secretCode.length`. Because array indices start at 0, the length of `secretCode` is 1 larger than its final index. A loop should stop its traversal before its counter variable is equal to the length of the list.

To give a concrete example, if the length of an array is `5`, the last index we want to access is `4`. If we were to try to access index `5`, we would get an `ArrayIndexOutOfBoundsException` error! This is a very common mistake when first starting to traverse arrays.

Traversing an `ArrayList` looks very similar:

```java
for (int i = 0; i < secretCode.size(); i++) {
  // Increase value of element value by 1
  int num = secretCode.get(i);
  secretCode.set(i, num + 1);
}
```

We can also use `while` loops to traverse through arrays and `ArrayLists`. If we use a `while` loop, we need to create our own counter variable to access individual elements. We’ll also set our condition to continue looping until our counter variable equals the list length.

For example, let’s use a `while` loop to traverse through an array:

```java
int i = 0; // initialize counter

while (i < secretCode.length) {
  secretCode[i] += 1;
  i++; // increment the while loop
}
```

Traversing through an `ArrayList` with a `while` loop would look like this:

```java
int i = 0; // initialize counter

while (i < secretCode.size()) {
  int num = secretCode.get(i);
  secretCode.set(i, num + 1);
  i++; // increment the while loop
}
```

Example:
```java
import java.util.ArrayList;

class CalculateTotal {
  
  public static void main(String[] args) {
    
    ArrayList<Double> expenses = new ArrayList<Double>();
    expenses.add(74.46);
    expenses.add(63.99);
    expenses.add(10.57);
    expenses.add(81.37);
    
    double total = 0;
    
    // Iterate over expenses
    for( int i = 0; i < expenses.size(); i++ ) {
      total += expenses.get(i);
    }
    
    System.out.println(total);
    
  }
  
}

Output:
230.39
```

## break and continue

If we ever want to exit a loop before it finishes all its iterations or want to skip one of the iterations, we can use the `break` and `continue` keywords.

The `break` keyword is used to exit, or `break`, a loop. Once break is executed, the loop will stop iterating. For example:

```java
for (int i = 0; i < 10; i++) {
  System.out.println(i);
  if (i == 4) {
    break;
  }
}
```

Even though the loop was set to iterate until the condition `i < 10` is `false`, the above code will `output` the following because we used `break`:

```terminal
0
1
2
3
4
```

The `continue` keyword can be placed inside of a loop if we want to skip an iteration. If `continue` is executed, the current loop iteration will immediately end, and the next iteration will begin. We can use the `continue` keyword to skip any even valued iteration:

```java
int[] numbers = {1, 2, 3, 4, 5};
    
for (int i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 == 0) {
    continue;
  }
  System.out.println(numbers[i]);
}
```

This program would output the following:
```terminal
1
3
5
```

In this case, if a number is even, we hit a `continue` statement, which skips the rest of that iteration, so the print statement is skipped. As a result, we only see odd numbers print.

__Keep Reading: AP Computer Science A Students__

Loops can exist all throughout our code - including inside a method. If the `return` keyword was executed inside a loop contained in a method, then the loop iteration would be stopped and the method/constructor would be exited.

For example, we have a method called `checkForJacket()` that takes in an array of `Strings`. If any of the elements are equivalent to the `String` value `"jacket"`, the method will return `true`:

```java
public static boolean checkForJacket(String[] lst) {
  for (int i = 0; i < lst.length; i++) {
    System.out.println(lst[i]);
    if (lst[i] == "jacket") {
      return true;
    }
  }
  return false;
} 

public static void main(String[] args) {
  String[] suitcase = {"shirt", "jacket", "pants", "socks"};   
  System.out.println(checkForJacket(suitcase));
}
```

As soon as an element equals `"jacket", return true;` is executed. This causes the loop to stop and the `compiler` to exit `checkForJacket()`. Running this code would output the following:

```terminal
shirt
jacket
true
```

Example:
```java
class Numbers {
  public static void main(String[] args) {
    for (int i = 0; i < 100; i++) {
      // Add your code below
      if( i % 5 != 0 ) {
        continue;
      }
      System.out.println(i);
      
    }
  }
}
Output: printed are those that are divisible by 5!
```

## For-Each Loops

Sometimes we need access to the elements’ indices or we only want to iterate through a portion of a list. If that’s the case, a regular `for` loop or `while` loop is a great choice.

For example, we can use a `for` loop to print out each element in an array called `inventoryItems`:

```java
for (int inventoryItem = 0; inventoryItem < inventoryItems.length; inventoryItem++) {
  // Print element at current index
  System.out.println(inventoryItems[inventoryItem]);
}
```

But sometimes we couldn’t care less about the indices; we only care about the element itself.

At times like this, for-each `loops` come in handy.

For-each loops, which are also referred to as enhanced loops, allow us to directly loop through each item in a list of items (like an array or `ArrayList`) and perform some action with each item. 

If we want to use a for-each loop to rewrite our program above, the syntax looks like this:

```java
for (String inventoryItem : inventoryItems) {
  // Print element value
  System.out.println(inventoryItem);

}
```

Our enhanced loop contains two items: an enhanced `for` loop variable (`inventoryItem`) and a list to traverse through (`inventoryItems`).

We can read the `:` as “in” like this: for each `inventoryItem` (which should be a `String`) in `inventoryItems`, print `inventoryItem`.

If we try to assign a new value to the enhanced `for` loop variable, the value stored in the array or `ArrayList` will not change. This is because, for every iteration in the enhanced loop, the loop variable is assigned a copy of the list element.

Note: We can name the enhanced `for` loop variable whatever we want; using the singular of a plural is just a convention. We may also encounter conventions like `String word : sentence`.

Example:
```java
import java.util.ArrayList;

class MostExpensive {
  
  public static void main(String[] args) {
    
    ArrayList<Double> expenses = new ArrayList<Double>();
    expenses.add(74.46);
    expenses.add(63.99);
    expenses.add(10.57);
    expenses.add(81.37);
    
    double mostExpensive = 0;
    
    // Iterate over expenses
    for( double expense : expenses ) {
      if( expense > mostExpensive ) {
        mostExpensive = expense;
      }
    }
    
    System.out.println(mostExpensive);
    
  }
  
}
```

## Removing Elements During Traversal

If we want to remove elements from an `ArrayList` while traversing through one, we can easily run into an error if we aren’t careful.

When an element is removed from an `ArrayList`, all the items that appear after the removed element will have their index value shift by negative one — it’s like all elements shifted to the left! We’ll have to be very careful with how we use our counter variable to avoid skipping elements.

__Removing An Element Using `while`__

When using a `while` loop and removing elements from an `ArrayList`, we should not increment the `while` loop’s counter whenever we remove an element. We don’t need to increase the counter because all of the other elements have now shifted to the left.

For example, if we removed the element at index `3`, then the element that was at index `4` will be moved to index `3`. If we increase our counter to `4`, we’ll skip that element!

Take a look at this block of code that will remove all odd numbers from an `ArrayList`. Think about what the value of `i` is, when we’re increasing the value of `i`, and when `i < lst.size()` becomes `False`.

```java
int i = 0; // initialize counter

while (i < lst.size()) {
  // if value is odd, remove value
  if (lst.get(i) % 2 != 0){
    lst.remove(i);
  } else {
    // if value is even, increment counter
    i++;
  }
}
```

__Removing An Element Using `for`__

We can use a similar strategy when removing elements using a `for` loop. When using a `while` loop, we decided to not increase our loop control variable whenever we removed an element. This ensured that we would not skip an element when all of the other elements shifted to the left.

When using a `for` loop, we, unfortunately, must increase our loop control variable — the loop control variable will always change when we reach the end of the loop (and it will usually change by `1` because we often use something like `i++`.) Since we can’t avoid increasing our loop control variable, we can take matters into our own hands and decrease the loop control variable whenever we remove an item.

For example:
```java
for (int i = 0; i < lst.size(); i++) {
  if (lst.get(i) == "value to remove"){
    // remove value from ArrayList
    lst.remove(lst.get(i));
    // Decrease loop control variable by 1
    i--;    
  }
}
```

Now whenever we remove an item, we’ll decrease `i` by `1`. Then when we reach the end of the loop, `i` will increase by `1`. It will be like `i` never changed!

__Note:__ Avoid manipulating the size of an ArrayList when using an enhanced for loop. Actions like adding or removing elements from an ArrayList when using a for each loop can cause a `ConcurrentModificationException` error.