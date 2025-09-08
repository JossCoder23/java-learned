## Classes: Constructor Parameters

Since the constructor is a method, we can include parameters to assign values to instance fields.

Here the Car constructor has a parameter: String carColor:

```java
public class Car { 
  public String color; 

  // constructor method with a parameter 
  public Car(String carColor) { 
    // parameter value assigned to the field 
    color = carColor; 
  } 
} 
```

Keep Reading: AP Computer Science A Students

A class can have multiple constructors. We can differentiate them based on their parameters. The signature helps the compiler to differentiate between different methods in classes. The difference between a method and a function is that methods are always related to a class or an object.
.

For example, here we have defined two constructors:

```java
public class Car { 
  public String color; 
  public int mpg; 
  public boolean isElectric; 

  // constructor 1 
  public Car(String carColor, int milesPerGallon) { 
    color = carColor; 
    mpg = milesPerGallon; 
  } 

  // constructor 2 
  public Car(boolean electricCar, int milesPerGallon) { 
    isElectric = electricCar; 
    mpg = milesPerGallon; 
  } 
} 
```

When we don’t define the constructor, the Java compiler creates a default constructor that assigns default values to an instance. Default values can be created by assigning values to the instance fields during their declaration:

```java
public class Car { 
 public String color = "red"; 
 public boolean isElectric = false; 
 public int cupHolders = 4; 

 public static void main(String[] args) { 
   Car myCar = new Car(); 
   System.out.println(myCar.color); // Prints: red 
 } 
} 
```

## Methods

In the last lesson, we learned that objects have state and behavior. We have seen how to give objects state through instance fields. Now, we’re going to learn how to create object behavior using methods. Remember our example of a Savings Account.

## Defining Methods

If we were to define a checkBalance() method for the Savings Account example we talked about earlier, it would look like the following:

```java 
public void checkBalance(){
  System.out.println("Hello!");
  System.out.println("Your balance is " + balance);
}
```

The first line, public void checkBalance(), is the method declaration. It gives the program some information about the method:

* **public** means that other classes can access this method. We will learn more about that later in the course.

* The **void** keyword means that there is no specific output from the method. We will see methods that are not **void** later in this lesson, but for now, all of our methods will be **void**.

* **checkBalance()** is the name of the method.

```java
public class Store {
  // instance fields
  String productType;
    
  // constructor method
  public Store(String product) {
    productType = product;
  }
    
  // Add advertise method below
  public void advertise() {
    System.out.println("Come spend some money!");
    System.out.println("Selling "+this.productType+"!");
  }
}
```

## Calling Methods

When we add a non-static method to a class, it becomes available to use on an object of that class. In order to have our methods get executed, we must call the method on the object we created.

Let’s add a non-static startEngine() method to our Car class from the previous lesson. Inside the main() method, we’ll call startEngine() on the myFastCar object:

```java
class Car {

  String color;

  public Car(String carColor) {
    color = carColor;
  }

  public void startEngine() {
    System.out.println("Starting the car!");
    System.out.println("Vroom!");
  }

  public static void main(String[] args){
    Car myFastCar = new Car("red");
    // Call a method on an object 
    myFastCar.startEngine();
    System.out.println("That was one fast car!");
  }
}

output:
Starting the car!
Vroom!
That was one fast car!
```

## Adding Parameters

We saw how a method’s scope prevents us from using variables declared in one method in another method. What if we had some information in one method that we needed to pass into another method?

Similar to how we added parameters to constructors, we can customize all other methods to accept parameters. For example, in the following code, we create a startRadio() method that accepts a double parameter, stationNum, and a String parameter called stationName:

```java
class Car {

  String color;

  public Car(String carColor) {
    color = carColor;		 
  }

  public void startRadio(double stationNum, String stationName) {
    System.out.println("Turning on the radio to " + stationNum + ", " + stationName + "!");
    System.out.println("Enjoy!");
  }

  public static void main(String[] args){
    Car myCar = new Car("red");
    myCar.startRadio(103.7, "Meditation Station");
  }
}

output:
Turning on the radio to 103.7, Meditation Station!
Enjoy!
```

## Reassigning Instance Fields

Earlier, we thought about a Savings Account as a type of object we could represent in Java.

Two of the methods we need are depositing and withdrawing:

```java
public void deposit(double amountToDeposit){
  double updatedBalance = balance + amountToDeposit;
  balance = updatedBalance;
}

public static void main(String[] args){
  SavingsAccount myAccount = new SavingsAccount(2000);
  System.out.println(myAccount.balance);
  myAccount.deposit(100);
  System.out.println(myAccount.balance);
}
```

## Returns 

Remember, variables can only exist in the scope that they were declared in. We can use a value outside of the method it was created in if we return it from the method.

We return a value by using the keyword return:

```java
public int numberOfTires() {
  int tires = 4;
  // return statement
  return tires;
}
```

Example:

```java
public class Store {
  // instance fields
  String productType;
  double price;
  double tax = 0.08;
    
  // constructor method
  public Store(String product, double initialPrice) {
    productType = product;
    price = initialPrice;
  }
    
  // increase price method
  public void increasePrice(double priceToAdd){
    double newPrice = price + priceToAdd;
    price = newPrice;
  }
    
  // get price with tax method
  public double getPriceWithTax() {
    double totalPrice = price + price * tax;
    return totalPrice;
  }

}

public class Main {
  public static void main(String[] args) {
    Store lemonadeStand = new Store("Lemonade", 3.75);
    double lemonadePrice = lemonadeStand.getPriceWithTax();
    System.out.println(lemonadePrice);
  }
}
```

## The toString() Method

When we print out Objects, we often see a String that is not very helpful in determining what the Object represents. In the last lesson, we saw that when we printed our Store objetcs, we would see output like: Store@6bc7c054

When we define a toString() method for a class, we can return a String that will print when we print the object:

```java
class Car {

    String color;

    public Car(String carColor) {
        color = carColor;
    }

    public static void main(String[] args){
        Car myCar = new Car("red");
        System.out.println(myCar);
    }

   public String toString(){
       return "This is a " + color + " car!";
   }
}
```
