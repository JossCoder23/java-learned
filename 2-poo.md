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

```java
public class Store{
  public String productType;
  public Store(String product){
    productType = product;
  }
}
```

## Classes: Assigning Values to Instance Fields

Since the constructor now accepts a parameter, let’s see how we can use this constructor to create an instance of an object with initial values for its fields.

```java
public class Car { 
  public String color; 

  public Car(String carColor) { 
    // assign parameter value to instance field 
    color = carColor; 
  } 
} 

class Main{ 
  public static void main(String[] args){ 
  Car ferrari = new Car("red"); 
  } 
}  
```

## Classes: Multiple Fields

Objects are not limited to a single instance field. We can declare as many fields as necessary for our program’s requirements. To illustrate this, let’s add two more instance fields to our Car instances.

Remember, it’s important to pass the arguments in the same order as they are listed in the parameters.

```java
public class Car { 
  String color; 

  // new fields! 
  boolean isRunning; 
  int velocity; 

  // new parameters that correspond to the new fields 
  public Car(String carColor, boolean carRunning, int milesPerHour) { 
    color = carColor; 

    // assign new parameters to the new fields 
    isRunning = carRunning; 
    velocity = milesPerHour; 
  } 
} 

Public class Main(){ 

  public static void main(String[] args) { 
    // new values passed into the method call 
    Car ferrari = new Car("red", true, 27); 
    Car renault = new Car("blue", false, 70); 

    System.out.println(renault.isRunning); // false 
    System.out.println(ferrari.velocity); // 27 
  } 
} 

// values match types, no error 
Car honda = new Car("green", false, 0); 

// values do not match types, error! 
Car junker = new Car(true, 42, "brown"); 
```