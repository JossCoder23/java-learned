## Introduction to String Methods

As you may recall, a `String`, which is widely used in Java, is an object that represents a sequence of characters. It is a great way to store information.

Because character strings are so vital to programming, Java dedicated an entire class to them. This is great news for us because the `String` class has a lot of useful `methods` to help us perform operations on `Strings` and data manipulation. We don’t have to import anything to use the `String` class because it’s part of the `java.lang` package which is available by default.

In this lesson, we will go over several `String` methods:

* length()
* concat()
* equals()
* indexOf()
* charAt()
* substring()
* toUpperCase() / toLowerCase()


```java
public class HelloWorld {
  
	public static void main(String[] args) {
    
    String str = "Hello, World!";
    
    // Examples:

    System.out.println(str.length());
    
    System.out.println(str.substring(4));
    
    System.out.println(str.toUpperCase());
    
  }
  
}

Output:
13
o, World!
HELLO, WORLD!
```

## length()

In Java, the `length()` string method returns the length ⁠— total number of characters ⁠— of a `String`.

Suppose we have a `String` called `str`, `str.length()` would return its length.

Take a look at this code for example:

```java
String str = "Hello World!";  

System.out.println(str.length());
```

`12` would be printed because `str` has 12 characters:

`H e l l o _ W o r l d !`

In theory, the length of a `String` is the same as the `Unicode` units of the `String`. For example, escape sequences such as `\n` count as only one character.

## concat()

The `concat()` method concatenates one string to the end of another string. Concatenation is the operation of joining two strings together.

Suppose we have a `String` called `str1` and another `String` called `str2`, using `str1.concat(str2)` would return `str1` with `str2` appended to the end of it.

For example:

```java
String name = new String("Code");

name = name.concat("cademy");

System.out.println(name);
```

`Codecademy` would be printed.

`Strings` are immutable objects which means that `String methods`, like `concat()` do not actually change a `String` object.

Our variable, `name` holds a reference to the `String` object, `"Code"`. When we use `concat()` on `name`, we changed its value so that it references a new object — `"Code"`, combined with the String literal, `"cademy"`.

Suppose we do something slightly different. We’ll use `concat()` on `name` without reassigning its value:

```java
String name = "Code";

name.concat("cademy");

System.out.println(name);
```

`Code` would be printed instead. The value of the `String` can’t change! Instead, we create a new object and need to assign that new object to some variable.

__Keep Reading: AP Computer Science A Students__

When we first discussed Objects we learned that if we tried printing an Object, we’d get an `output` of the class name and the Object’s memory address. If we wanted to get a more useful printout, we’d have to call the Object’s `toString()` method.

This `toString()` method comes into play with `concat()`. If we concatenate a String with another Object, we’re really adding the result of that Object’s `toString()` method to our original String. We can even see this when we concatenate two Strings together (remember a String is an Object). When we use `concat()` on another String, we don’t concatenate its memory address to the original String. Instead, we combine the result of its `toString()` method to the original String.

Example:
 
```java
public class CombineNames {
  
	public static void main(String[] args) {
    
    // Add your first names:
    String firstName = "Jose";  
    String lastName = " Pardo";

    // What's the full name?
    System.out.println(firstName.concat(lastName));
    
  }
  
}

Output:
Jose Pardo
```

## equals()

With objects, such as `Strings`, we can’t use the primitive equality operator `==` to check for equality between two strings. To test equality with strings, we use a built-in method called `equals()`

For example:

```java
String flavor1 = "Mango";
String flavor2 = "Peach";

System.out.println(flavor1.equals("Mango"));
// prints true

System.out.println(flavor2.equals("Mango"));
// prints false
```

Side note, there’s also an `equalsIgnoreCase()` method that compares two strings without considering upper/lower cases.

__Keep Reading: AP Computer Science A Students__

We can also compare String values lexicographically (think dictionary order) using the `.compareTo()` method. When we call the `.compareTo()` method, each character in the `String` is converted to Unicode; then the Unicode character from each `String` is compared.

The method will return an `int` that represents the difference between the two Strings.

For Example:

```java
String flavor1 = "Mango";
String flavor2 = "Peach";

System.out.println(flavor1.compareTo(flavor2)); 
```

Our program above will output `-3`.

When we use `.compareTo()`, we must pay attention to the return value:

* If the method returns `0`, the two `Strings` are equal.
* If the value is less than `0`, then the `String` object is lexicographically less than the `String` object argument.
* If the value is greater than `0`, then the `String` object is lexicographically greater than the `String` object argument.

In the example above, `"Mango"` comes before `"Peach"`, so we get a negative number (we specifically get `-3` because the Unicode values of `"M"` and `"P"` differ by 3). If we did `flavor2.compareTo(flavor1)`, we would get 3, signifying that `"Peach"` is greater than `"Mango"`.

__Note:__ Make sure to pay attention to capitalization when using `.compareTo()`. Upper case and lower case letters have different Unicode values. For example, when comparing `"Mango"` and `"Peach"`, we got `-3`, meaning that `"Mango"` was smaller. But if we compare `"mango"` and `"Peach"` we get `29`. The Unicode value for lower case `"m"` is actually larger than upper case `"P"`. Using `.compareToIgnoreCase()` will perform the same task, but will not consider upper/lower case.

```java
public class Password {
  
  public static void main(String[] args) {
    
    String password = "correcthorsebatterystaple";
    
    // Write the code:
    System.out.println(password.equals("pruebasiestees"));
    
  }
  
}

Output:
false
```

## indexOf()

If we want to know the index of the first occurrence of a character in a string, we can use the `indexOf()` method on a string.

Remember that the indices in Java start with 0:

```java
String letters = "ABCDEFGHIJKLMN";

System.out.println(letters.indexOf("C"));
```

This would `output 2`

Although `C` is the third letter in the English alphabet, it is located in the second index of the string.

Suppose we want to know the index of the first occurrence of an entire substring. The `indexOf()` instance method can also return where the substring begins (the index of the first character in the substring):

```java
String letters = "ABCDEFGHIJKLMN";

System.out.println(letters.indexOf("EFG"));
```

This would output `4`, because `EFG` starts at index 4.

If the `indexOf()` doesn’t find what it’s looking for, it’ll return a `-1`.

## charAt()

The `charAt()` method returns the character located at a `String‘s` specified index.

For Example: 

```java
String str = "qwer";

System.out.println(str.charAt(2));
```

It would output `e` because that’s what’s at index 2. (Once again, indices start with 0.)

Suppose we try to return the character located at index 4. It would produce an `IndexOutOfBoundsException` error because index 4 is out of `str`‘s range:

```terminal
java.lang.StringIndexOutOfBoundsException: String index out of range: 4
```

Example:

```java
public class Initials {
  
	public static void main(String[] args) {
    
    // Add a first name and a last name:
    String firstName = "Jose";  
    String lastName = "Pardo";
    
    // What are the initials?
    System.out.println(firstName.charAt(0));
    System.out.println(lastName.charAt(0));
    
  }
  
}

Output:
J
P
```

## substring()

There may be times when we only want a part of a string. In such cases, we may want to extract a substring from a string.

The `substring()` method does exactly that. For example:

```java
String line = "The Heav'ns and all the Constellations rung";

System.out.println(line.substring(24));
```

It would output `Constellations rung` because that’s what begins at index 24 and ends at the end of `line`. The substring begins with the character at the specified index and extends to the end of the string.

Suppose we want a substring from the middle of the string. We can instead include two arguments in this method. For example:

```java
String line = "The Heav'ns and all the Constellations rung";

System.out.println(line.substring(27, 33));
```

When `substring()` is called with two arguments, the first argument is inclusive and the second is exclusive. This means the resulting substring will begin at index 27 and extend up to, but not including, index 33. Therefore, the example above would output `stella` because that’s the substring that begins at index 27 and ends at index 32, one index before 33.

We can use this method to return a single-element substring at a specific index. We do this by calling `substring()` with the desired index value as the first argument and then the index value plus one as the second argument.

For example, we can use this method to output just `C`:

```java
String line = "The Heav'ns and all the Constellations rung";

System.out.println(line.substring(24, 25));
// Prints: C
```

## toUpperCase() / toLowerCase()

There will be times when we have a word in a case other than what we need it in. Luckily, Java has a couple `String methods` to help us out:

* __toUpperCase()__: returns the string value converted to uppercase
* __toLowerCase()__: returns the string value converted to lowercase

For example:
```java
String input = "Cricket!";

String upper = input.toUpperCase();
// stores "CRICKET!"

String lower = input.toLowerCase();
// stores "cricket!"
```

A good use of this functionality is to ensure consistency of the data you store in a database. Making sure all of the data you get from a user is lowercase before you store it in your database will make your database easier to search through later.