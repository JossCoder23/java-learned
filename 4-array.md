## Creating an Array Explicitly

Imagine that we’re using a program to keep track of the prices of different clothing items we want to buy. We would want a list of the prices and a list of the items they correspond to. To create an array, we provide a name and declare the type of data it holds:

```java
double[] prices;

double[] prices = {13.15, 15.87, 14.22, 16.66};

String[] clothingItems = {"Tank Top", "Beanie", "Funny Socks", "Corduroys"};
```

Example:

```java
public class Newsfeed {
  public Newsfeed(){
      
  }
  // Create getTopics() below:
  public String[] getTopics() {
    String[] topics = {"Opinion", "Tech", "Science", "Health" };
    return topics;
  }
    
}
```

## Importing Arrays

When we printed out the array we created in the last exercise, we saw a memory address that did not help us understand what was contained in the array.

If we want to have a more descriptive printout of the array itself, we need a `toString()` method that is provided by the `Array` package in Java.

```java 
import java.util.Arrays;
```

The `Arrays` package has many useful methods, including `Arrays.toString()`. When we pass an array into Arrays.toString(), we can see the contents of the array printed out:

```java
import java.util.Arrays;

public class Lottery(){
  
  public static void main(String[] args){
    int[] lotteryNumbers = {4, 8, 15, 16, 23, 42};
    String betterPrintout = Arrays.toString(lotteryNumbers);
    System.out.println(betterPrintout);
  }

}

output: [4, 8, 15, 16, 23, 42]
```

Example: 

```java
// import the Arrays package here
import java.util.Arrays;

public class Main {
  public static void main(String[] args) {
    Newsfeed sampleFeed = new Newsfeed();
    String[] topics = sampleFeed.getTopics();
    System.out.println(Arrays.toString(topics));
  }
}

output: [Opinion, Tech, Science, Health]
```

## Get Element By Index

Now that we have an array declared and initialized, we want to be able to get values out of it.

We use square brackets, `[` and `]`, to access data at a certain index:

```java
double[] prices = {13.1, 15.87, 14.22, 16.66};

System.out.println(prices[1]);
output: 15.87
```

Example:

```java
public class Newsfeed {
  String[] topics = {"Opinion", "Tech", "Science", "Health"};
  public int[] views = {0, 0, 0, 0};
  
  public Newsfeed(){

  }
    
  public String[] getTopics(){
    return topics;
  }
  
  // Create getFirstTopic() below
  public String getFirstTopic() {
    return this.topics[0];
  }
  
  public void viewTopic(int topicIndex){
    this.views[topicIndex] = views[topicIndex] + 1;
  }
}

import java.util.Arrays;

public class Main {
  public static void main(String[] args) {
    Newsfeed sampleFeed = new Newsfeed();
        
    System.out.println("The top topic is " + sampleFeed.getFirstTopic());
        
    sampleFeed.viewTopic(1);
    sampleFeed.viewTopic(1);
    sampleFeed.viewTopic(3);
    sampleFeed.viewTopic(2);
    sampleFeed.viewTopic(2);
    sampleFeed.viewTopic(1);
        
    System.out.println("The " + sampleFeed.topics[1] + " topic has been viewed " + sampleFeed.views[1] + " times!");
  }
}

Output:
The top topic is Opinion
The Tech topic has been viewed 3 times!
```

## Creating an Empty Array

We can also create empty arrays and then fill the items one by one. Empty arrays have to be initialized with a fixed size:

```java
String[] menuItems = new String[5];
```

Once you declare this size, it cannot be changed! This array will always be of size `5`.

After declaring and initializing, we can set each index of the array to be a different item:

```java
menuItems[0] = "Veggie hot dog";
menuItems[1] = "Potato salad";
menuItems[2] = "Cornbread";
menuItems[3] = "Roasted broccoli";
menuItems[4] = "Coffee ice cream";
```

This group of commands has the same effect as assigning the entire array at once:

```java
String[] menuItems = {"Veggie hot dog", "Potato salad", "Cornbread", "Roasted broccoli", "Coffee ice cream"};
```

We can also change an item after it has been assigned! Let’s say this restaurant is changing its broccoli dish to a cauliflower one:

```java
menuItems[3] = "Baked cauliflower";
Output:
["Veggie hot dog", "Potato salad", "Cornbread", "Baked cauliflower", "Coffee ice cream"]
```

Example:

```java
public class Newsfeed {
  String[] topics = {"Opinion", "Tech", "Science", "Health"};
  int[] views = {0, 0, 0, 0};
  String[] favoriteArticles;
  
  public Newsfeed(){
    // Initialize favoriteArticles here:
    favoriteArticles = new String[10];
  }
  
  public void setFavoriteArticle(int favoriteIndex, String newArticle){
    // Add newArticle to favoriteArticles:
    favoriteArticles[favoriteIndex] = newArticle;
  }
}

import java.util.Arrays;

public class Main {

  public static void main(String[] args) {

    Newsfeed sampleFeed = new Newsfeed();
    
    sampleFeed.setFavoriteArticle(2, "Humans: Exterminate Or Not?");
    sampleFeed.setFavoriteArticle(3, "Organic Eye Implants");
    sampleFeed.setFavoriteArticle(0, "Oil News");
      
    System.out.println(Arrays.toString(sampleFeed.favoriteArticles));

  }

}

Output:
[Oil News, null, Humans: Exterminate Or Not?, Organic Eye Implants, null, null, null, null, null, null]
```

## Length

What if we have an array storing all the usernames for our program, and we want to quickly see how many users we have? To get the length of an array, we can access the length field of the array object:

```java
String[] menuItems = new String[5];
System.out.println(menuItems.length);
Output: 5
```

Example:

```java
public class Newsfeed {
  String[] topics = {"Opinion", "Tech", "Science", "Health"};
  int[] views = {0, 0, 0, 0};
  
  public Newsfeed(){
  }
    
  public String[] getTopics(){
    return topics;
  }
  
  public int getNumTopics(){
    return topics.length;
  }
  
}

import java.util.Arrays;
public class Main {
  public static void main(String[] args){
    Newsfeed sampleFeed = new Newsfeed();
    System.out.println("The number of topics is "+ sampleFeed.getNumTopics());
  }
}

Output:
The number of topics is 4
```

## String[] args

When we write `main()` methods for our programs, we use the parameter `String[] args`. Now that we know about array syntax, we can start to parse what this means.

A `String[]` is an array made up of `String`. Examples of `String` arrays:

```java
String[] humans = {"Talesha", "Gareth", "Cassie", "Alex"};
String[] robots = {"R2D2", "Marvin", "Bender", "Ava"};
```

The `args` parameter is another example of a `String` array. In this case, the array `args` contains the arguments that we pass in from the terminal when we run the class file. (So far, `args` has been empty.)

So how can you pass arguments to `main()`? Let’s say we have this class `HelloYou`:

```java
public class HelloYou {
  public static void main(String[] args) {
    System.out.println("Hello " + args[0]);  
  }
}
```

When we run the file `HelloYou` in the terminal with an argument of "Laura":

```terminal
java HelloYou Laura
```

We get the output:

```terminal
Hello Laura
```

The `String[] args` would be interpreted as an array with one element, "Laura".

When we use `args[0]` in the main method, we can access that element like we did in `HelloYou`.

```java
import java.util.Arrays;

public class Main {
  public static void main(String[] args) {
    String[] students = {"Sade", "Alexus", "Sam", "Koma"};
    int[] mathScores = new int[4];
    mathScores[0] = 64;
    mathScores[1] = 57;
    mathScores[2] = 76;
    mathScores[3] = 98;
    for(int i = 0; i < students.length; i++){
      System.out.println(students[i] + ": " + mathScores[i]);
    }
  }
}
```