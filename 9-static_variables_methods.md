## Static Methods Refresher

In this lesson, we’re going to dive into how to create `classes` with your own static `methods` and static `variables`. To begin, let’s take a quick refresher on static methods.

Static methods are methods that belong to an entire class, not a specific object of the class. Static methods are called using the class name and the `.` operator. We’ve seen a couple of static methods already!

```java
double randomNumber = Math.random();
// Stores a random decimal between 0.0 and 1.0 in randomNumber

double number = Double.valueOf("2.5");
// Transforms the String "2.5" into a double
```

In the first example, `random()` is a static method that belongs to the `Math` class. We didn’t need to create a `Math` object (like `Math myMathObject = new Math()`) in order to use that method. We could just call it using the class name.

Similarly, `valueOf()` is a static method of the `Double` class. Given a `String` as an input, this method will turn that `String` into a `double`. Again, we don’t need to create a `Double` object in order to call this method — we use the class itself to call it.

Finally, notice that our `main()` methods have been `static` this whole time. When Java runs your program, it calls that the main method of your class — `YourClassName.main()`.

## Static Variables

We’ll begin writing our own static `methods` soon, but before we do, let’s take a look at static `variables`. Much like static methods, you can think of static variables as belonging to the class itself instead of belonging to a particular object of the class.

Just like with static methods, we can access static variables by using the name of the class and the `.` operator. Finally, we declare static variables by using the `static` keyword during declaration. This keyword usually comes after the variable’s access modifier (`public` or `private`).

When we put this all together, we might end up with a class that looks something like this:

```java
public class Dog{

  // Static variables
  public static String genus = "Canis";

  //Instance variables
  public int age;
  public String name;

  public Dog(int inputAge, String inputName){
    this.age = inputAge;
    this.name = inputName;
  }
}
```

Since all dogs share the same genus, we could use a static variable to store that information for the entire class. However, we want each dog to have its own unique `name` and `age`, so those aren’t `static`. We could now access this static variable in a `main()` function like so:

```java
public class Dog{
  //Variables, constructors and methods defined here

  public static void main(String[] args){
    System.out.println(Dog.genus); // Prints Canis
  }
}
```

Unlike static methods, you can still access static variables from a specific object of the class. However, no matter what object you use to access the variable, the value will always be the same. You can think of it as all objects of the class sharing the same variable

```java
public static void main(String[] args){
  Dog snoopy = new Dog(3, "Snoopy");
  Dog ringo = new Dog(5, "Ringo");

  System.out.println(Dog.genus); // Prints Canis
  System.out.println(snoopy.genus); // Prints Canis
  System.out.println(ringo.genus); // Prints Canis
}
```

Finally, you might have seen a few static variables before. If you want easy access to the largest possible integer, you can get it by using `Integer.MAX_VALUE`. If you look at the official documentation you’ll see that this variable is `public`, `static`, and `final`. (`final` means that you can’t change the variable’s value after creating it.) We’re starting to know a lot of Java keywords!

Example:

```java
public class ATM{

  // Step 2: Create your static variables here
  public static int totalMoney = 0;
  public static int numATMs = 0;

  // Instance variables
  public int money;

  public ATM(int inputMoney){
    this.money = inputMoney;
  }

  public void withdrawMoney(int amountToWithdraw){
    if(amountToWithdraw <= this.money){
      this.money -= amountToWithdraw;
    }
  }

  public static void main(String[] args){
    // Step 1: Create your two ATMs here
    ATM firstATM = new ATM(1000);
    ATM secondATM = new ATM(500);

    System.out.println(firstATM.money);
    System.out.println(secondATM.money);
    
    // Step 3: Print your static variable in three different ways here
    System.out.println(ATM.totalMoney);
    System.out.println(firstATM.totalMoney);
    System.out.println(secondATM.totalMoney);

  }

}
```

## Modifying Static Variables

Now that we’ve created a couple of static `variables`, let’s start to edit them. The good news is that editing static variables is similar to editing any other variable. Whether you’re writing code in a constructor, a non-static method, or a static method, you have access to static variables.

Before we jump into the checkpoints, let’s think about times when you might want to edit static variables. Often times, you’ll see static variables used to keep track of information about all objects of a class. For example, our variable `numATMs` is keeping track of the total number of `ATM`s in the system. Therefore, every time an `ATM` is created (using the constructor), we should increase that variable by `1`. If we could somehow destroy an `ATM`, the method that destroys it should decrease `numATMs` static variable by `1`.

Similarly, we have a variable named `totalMoney`. This variable is keeping track of all money across all ATMs. Whenever we remove money from an ATM using the non-static `withdrawMoney()` method, we should modify the `money` instance variable for that particular ATM as well as the `totalMoney` variable. In doing so, all ATMs will know how much money is in the system.

Example:

```java
public class ATM{
  // Static variables
  public static int totalMoney = 0;
  public static int numATMs = 0;

  // Instance variables
  public int money;

  public ATM(int inputMoney){
    this.money = inputMoney;

    // Steps 1 and 2: Edit numATMs and total money here
    numATMs += 1;
    totalMoney += inputMoney;
  }

  public void withdrawMoney(int amountToWithdraw){
    if(amountToWithdraw <= this.money){
      this.money -= amountToWithdraw;
      // Step 3: Edit totalMoney here
      totalMoney -= amountToWithdraw;
    }
  }

  public static void main(String[] args){

    System.out.println("Total number of ATMs: " + ATM.numATMs); 
    ATM firstATM = new ATM(1000);
    ATM secondATM = new ATM(500);
    System.out.println("Total number of ATMs: " + ATM.numATMs); 

    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);  
    firstATM.withdrawMoney(500);
    secondATM.withdrawMoney(200);
    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);    

  }

}

Output:
Total number of ATMs: 0
Total number of ATMs: 2
Total amount of money in all ATMs: 1500
Total amount of money in all ATMs: 800
```

## Writing Your Own Static Methods

Nice work! Now that we’ve seen how static `variables` work, let’s look into how to write our own static `methods`.

Let’s get the syntax out of the way first — just like with variables, to create a static method, use the `static` keyword in the method’s definition. Just like with variables, this keyword usually comes after `public` or `private`.

```java
public static void myFirstStaticMethod(){
  // Some code here
}
```

Often times, you’ll see static methods that are accessors or mutators for static variables.

```java
public static int getMyStaticVariable(){
  return myStaticVariable;
}

public static void setMyStaticVariable(int newValue){
  myStaticVariable = newValue;
}
```

One important rule to note is that static methods can’t interact with non-static instance variables.

To wrap your mind around this, consider why we use `this` when working with non-static instance variables. Let’s say we have a `Dog` class with a non-static instance variable named `age`. If we have a line of code like `this.age = 5;`, that means we’re setting the `age` of a specific `Dog` equal to `5`. However, if `age` were static, that would mean that the variable belongs to the entire class, not a specific object.

The `this` keyword can’t be used by a static method since static methods are associated with an entire class, not a specific object of that class. If you try to mix `this` with a static method, you’ll see the error message `non-static variable this cannot be referenced from a static context`.

Example:
```java
public class ATM{
  // Static variables
  public static int totalMoney = 0;
  public static int numATMs = 0;

  // Instance variables
  public int money;

  public ATM(int inputMoney){
    this.money = inputMoney;
    numATMs += 1;
    totalMoney += inputMoney;
  }

  public void withdrawMoney(int amountToWithdraw){
    if(amountToWithdraw <= this.money){
      this.money -= amountToWithdraw;
      totalMoney -= amountToWithdraw;
    }
  }

  // Write your averageMoney() method here
  public static void averageMoney() {
    System.out.println(totalMoney/numATMs);
    // System.out.println(this.money);
  }

  public static void main(String[] args){

    System.out.println("Total number of ATMs: " + ATM.numATMs); 
    ATM firstATM = new ATM(1000);
    ATM secondATM = new ATM(500);
    System.out.println("Total number of ATMs: " + ATM.numATMs); 

    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);  
    firstATM.withdrawMoney(500);
    secondATM.withdrawMoney(200);
    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);    

    // Call averageMoney() here
    firstATM.averageMoney();
    secondATM.averageMoney();
  }

}
Output:
Total number of ATMs: 0
Total number of ATMs: 2
Total amount of money in all ATMs: 1500
Total amount of money in all ATMs: 800
400
400

//Example wrong
public class ATM{
  // Static variables
  public static int totalMoney = 0;
  public static int numATMs = 0;

  // Instance variables
  public int money;

  public ATM(int inputMoney){
    this.money = inputMoney;
    numATMs += 1;
    totalMoney += inputMoney;
  }

  public void withdrawMoney(int amountToWithdraw){
    if(amountToWithdraw <= this.money){
      this.money -= amountToWithdraw;
      totalMoney -= amountToWithdraw;
    }
  }

  // Write your averageMoney() method here
  public static void averageMoney() {
    System.out.println(totalMoney/numATMs);
    System.out.println(this.money); //USAMOS UNA VARIABLE NO ESTATICA
  }

  public static void main(String[] args){

    System.out.println("Total number of ATMs: " + ATM.numATMs); 
    ATM firstATM = new ATM(1000);
    ATM secondATM = new ATM(500);
    System.out.println("Total number of ATMs: " + ATM.numATMs); 

    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);  
    firstATM.withdrawMoney(500);
    secondATM.withdrawMoney(200);
    System.out.println("Total amount of money in all ATMs: " + ATM.totalMoney);    

    // Call averageMoney() here
    firstATM.averageMoney();
    secondATM.averageMoney();
  }

}

Output:
ATM.java:25: error: non-static variable this cannot be referenced from a static context
    System.out.println(this.money); //USAMOS UNA VARIABLE NO ESTATICA
                       ^
1 error
```