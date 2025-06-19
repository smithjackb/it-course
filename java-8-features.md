---
layout: default
title: Java 8 Features Deep Dive
permalink: /it-course/java-8-features/
---

# Java 8 Features Deep Dive

Java 8 introduced several powerful features that significantly changed how we write Java code. This guide provides a clear explanation of the most important additions, including functional programming, the Stream API, the Optional class, and enhancements to interfaces and date/time handling.

---

## 1. Functional Programming in Java

Java 8 brought functional programming concepts to the language with lambda expressions and functional interfaces.

### Lambda Expressions

Lambda expressions allow you to write anonymous methods concisely.

```java
// Traditional approach
Runnable r = new Runnable() {
  public void run() {
    System.out.println("Running...");
  }
};

// Java 8 lambda
Runnable r = () -> System.out.println("Running...");
````

### Functional Interfaces

A functional interface has only one abstract method. Common examples include:

* `Runnable`
* `Comparator<T>`
* `Function<T, R>`
* `Predicate<T>`

These are often used with lambda expressions and method references.

---

## 2. Stream API

The Stream API makes it easy to process collections using a functional approach.

### Key Stream Methods

* `map()` – transform elements
* `filter()` – exclude items based on conditions
* `reduce()` – combine values into one result
* `collect()` – collect results into a list, set, or map

### Example

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

List<String> result = names.stream()
  .filter(name -> name.startsWith("A"))
  .map(String::toUpperCase)
  .collect(Collectors.toList());

System.out.println(result); // Output: [ALICE]
```

---

## 3. Optional Class

`Optional<T>` is a container object that may or may not contain a non-null value, helping to avoid `NullPointerException`.

### Example

```java
Optional<String> name = Optional.ofNullable(getName());

name.ifPresent(n -> System.out.println(n)); // Prints name if present
```

Other methods:

* `orElse("default")`
* `isPresent()`
* `orElseThrow()`

---

## 4. New Date and Time API

Java 8 introduced a new date and time package `java.time` which replaces the older `java.util.Date` and `Calendar`.

### Common Classes

* `LocalDate` – for dates
* `LocalTime` – for times
* `LocalDateTime` – for both
* `Period` – for date-based time amounts
* `Duration` – for time-based durations

### Example

```java
LocalDate start = LocalDate.of(2000, 1, 1);
LocalDate end = LocalDate.now();

Period age = Period.between(start, end);
System.out.println("Years: " + age.getYears());
```

---

## 5. Default and Static Methods in Interfaces

Java 8 allows interfaces to contain method implementations using `default` and `static` keywords.

### Default Method Example

```java
interface MyInterface {
  default void greet() {
    System.out.println("Hello from default method!");
  }
}
```

### Static Method Example

```java
interface MyInterface {
  static void sayHello() {
    System.out.println("Hello from static method!");
  }
}
```

These features allow interfaces to evolve without breaking existing implementations.

---

## Summary of Java 8 Features

| Feature                | Description                                         |
| ---------------------- | --------------------------------------------------- |
| Lambda Expressions     | Write concise code using anonymous functions        |
| Functional Interfaces  | Enable functional-style programming                 |
| Stream API             | Process collections in a declarative manner         |
| Optional Class         | Avoid `NullPointerException` safely                 |
| Date/Time API          | Improved handling of dates and times                |
| Default/Static Methods | Add methods to interfaces without breaking old code |

---

## Learn More

* [Best Java Certification Training - igmGuru](https://www.igmguru.com/digital-marketing-programming/java-certification-training)
* [Java Tutorial for Beginners - igmGuru](https://www.igmguru.com/blog/java-tutorial)
* [Try Java Tool](https://www.w3schools.com/java/tryjava.asp?filename=demo_helloworld)

---
