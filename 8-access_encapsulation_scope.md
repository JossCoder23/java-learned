## The public Keyword

After running the code in the last exercise, you should be developing an intuition on what the `public` and `private` keywords are doing. These keywords are defining what parts of your code have access to other parts of your code.

We can define the access of many different parts of our code including instance `variables`, `methods`, `constructors`, and even a class itself. If we choose to declare these as `public` this means that any part of our code can interact with them - even if that code is in a different class!

The way we declare something to be `public` is to use the `public` keyword in the declaration statement. In the code block below, we have a public class, constructor, instance variables, and method. Notice the five different uses of `public`.

```java
public class Dog{
  public String name;
  public int age;

  public Dog(String input_name, int input_age){
    name = input_name;
    age = input_age;
  }
    
  public void speak() {
    System.out.println("Arf Arf! My name is " + name + " and I am a good dog!");
  }
}
```

Since everything about a `Dog` is public, any other class can access anything about a `Dog`. For example, let’s say there was a `DogSchool` class. Any method of the `DogSchool` class could make a new `Dog` using the `public Dog` constructor, directly access that `Dog’s` instance variables, and directly use that `Dog’s` methods:

```java
public class DogSchool{
  public void makeADog(){
    Dog cujo = new Dog("Cujo", 7);
    System.out.println(cujo.age);
    cujo.speak();
  }
}
```

Notice that the `DogSchool` class and the `makeADog()` method are also public. This means that if some other class created a `DogSchool`, they would have access to these methods as well! We have public methods calling public methods!

One final thing to note is that for the purposes of this lesson, we’ll almost always make our `classes` and constructors `public`. While you can set them to `private`, it’s fairly uncommon to do so. Instead, we’ll focus on why you might make your instance variables and methods `private`. We’ll start looking into the `private` keyword in the next exercise.

## The private Keyword and Encapsulation

By now you’re probably catching onto what the `private` keyword does. When a Class’ instance variable or method is marked as `private`, that means that you can only access those structures from elsewhere inside that same class. Let’s look back at our `DogSchool` example:

```java
public class DogSchool{

  public void makeADog(){
    Dog cujo = new Dog("Cujo", 7);
    System.out.println(cujo.age);
    cujo.speak();
  }
}
```

`makeADog` is trying to directly access `Dog`‘s `.age` variable. It’s also trying to use the `.speak()` method. If those are marked as `private` in the `Dog` class, the `DogSchool` class won’t be able to do that. Other `methods` within the `Dog` class would be able to use `.age` or `.speak()` (for example, we could use `cujo.age` within the `Dog` class), but other classes won’t have access.

__Keep Reading: AP Computer Science A Students__

At this point, you might be thinking to yourself “Why even bother with any of this? In the last exercise, my code was broken until I flipped some `variables` and methods to `public`. Why don’t I just make everything `public`?”

While those are valid points, sometimes restricting our code is actually useful from a design perspective. This is one of the core ideas behind encapsulation. By making our instance variables (and some methods) `private`, we encapsulate our code into nice little bundles of logic.

For example, a `Bank` object doesn’t necessarily need to know the inner workings of a `CheckingAccount` object. It doesn’t need to know that the money is stored in a field named `money`, or that interest is added to an account by using a method named `.addInterest()`. In fact, if it had access to those fields or methods, it’s possible that someone using a `Bank` object could change things in a `CheckingAccount` without realizing it. By limiting access by using the `private` keyword, we are able to segment, or encapsulate, our code into individual units.

Note that we don’t necessarily want to completely block everything from other classes. In the next exercise, we’ll get into when you might want to make methods public — we’ll take a look at getter and setter methods.