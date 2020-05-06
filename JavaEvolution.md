---
theme: gaia
_class: lead
paginate: true
_paginate: false
backgroundColor: #fff
marp: true
backgroundImage: url('assets/hero-background.jpg')
---

![bg left:40% 80%](assets/java.svg)

# **How Java has evolved through time**
 (and how we not)


[//]: # (What are we going to talk about / Who am I)


---

![bg](assets/historyofJava.png)

## At a glance



---
## Java 7: Strings in switch Statements

- The comparison of String objects in switch statements is case sensitive. 
- The Java compiler generates generally more efficient bytecode from switch statements that use String objects than from chained if-then-else statements

---
```java
public String getTypeOfDayWithSwitchStatement(String dayOfWeekArg) {
     String typeOfDay;
     switch (dayOfWeekArg) {
         case "Monday":
             typeOfDay = "Start of work week";
             break;
         case "Tuesday":
         case "Wednesday":
         case "Thursday":
             typeOfDay = "Midweek";
             break;
         case "Friday":
             typeOfDay = "End of work week";
             break;
         case "Saturday":
         case "Sunday":
             typeOfDay = "Weekend";
             break;
         default:
             throw new IllegalArgumentException("Invalid day of the week: " + dayOfWeekArg);
     }

     return typeOfDay;
}
```

---
## Java 7: The try-with-resources Statement
- The try-with-resources statement ensures that each resource is closed at the end of the statement. 
- Any object that implements java.lang.AutoCloseable, which includes all objects which implement java.io.Closeable, can be used as a resource.

---
```java
// Java 6
static String readFirstLineFromFileWithFinallyBlock(String path) throws IOException {
  BufferedReader br = new BufferedReader(new FileReader(path));
  try {
    return br.readLine();
  } finally {
    if (br != null) br.close();
  }
}
```
```java
// Java 7
static String readFirstLineFromFile(String path) throws IOException {
  try (BufferedReader br = new BufferedReader(new FileReader(path))) {
    return br.readLine();
  }
}
```

---
## Java 7: The diamond 
Type Inference for Generic Instance Creation

```java
// Java 6
Map<String, List<String>> myMap = new HashMap<String, List<String>>();
```
```java
// Java 7
Map<String, List<String>> myMap = new HashMap<>();
```


---

## Java 7: Catching Multiple Exception Types


```java
// Java 6
catch (IOException ex) {
     logger.log(ex);
     throw ex;
catch (SQLException ex) {
     logger.log(ex);
     throw ex;
}
```
```java
// Java 7
catch (IOException|SQLException ex) {
     logger.log(ex);
     throw ex;
}
```

---

## Java 8: lambda expressions

Java 8 adds functional programming through what are called lambda expressions, which is a simple way of describing a function as some operation on an arbitrary set of supplied variables. All of the variables of the expression must be explicitly supplied; you don't access or store data that's not represented as a parameter. This makes lambda expressions more self-documenting, and the code is immune to hidden variables or states called side-effects. You can describe the transformation from input to output in lambda terms, and the details of transformations and recursions are hidden, which reduces complexity and errors. Lambda or functional language expressions can also facilitate parallelism because every variable is always represented as a parameter, so it follows you can run an expression anywhere and it will return the correct result if you give it the correct parameters. You can also split the lambda expression across several platforms and again get the same result. Lambda expressions add functional programming to Java 8, but the traditional imperative model is still available.

---

