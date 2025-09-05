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