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
 (and how we've not)

---
# What are we going to talk about
- Language improvements and its benefits
- API changes to adopt some improvements
<br>
- ~~Internal optimizations~~
- ~~Garbage collection estrategies~~
- ~~External libraries~~

---

![bg](assets/historyOfJava.png)

### At a glance
---
###### Java 5: It's 2004
- Generics
- Annotations
- Autoboxing/unboxing
- Enhanced for loops
---
###### Java 5: Generics
```java
// Java 1.4
private ArrayList cart = new ArrayList();
list.add(new Product(1, 6));
list.add(new Product(8, 1));

Product p = (Product) cart.get(0);
```
```java
// Java 5
private ArrayList<Product> cart = new ArrayList<Product>();
list.add(new Product(1, 6));
list.add(new Product(8, 1));

Product p = cart.get(0);
```
---
###### Java 5: Annotations
```java
// Java 5
@SuppressWarnings(value = "unchecked")
void myMethod() { ... }
```

```java
// Java 5
@Entity
@Table(name = "PRODUCT")
public class Product { ... }
```
---
###### Java 5: Autoboxing/unboxing
```java
// Java 1.4
List li = new ArrayList();
for (int i = 1; i < 50; i += 2) {}
    li.add(Integer.valueOf(i));
}
```

```java
// Java 5
List<Integer> li = new ArrayList<Integer>();
for (int i = 1; i < 50; i += 2) {}
    li.add(i);
}
```
---
###### Java 5: Enhanced For loop
```java
// Java 1.4
int arr[]={2,11,45,9};

for(int i=0; i<arr.length; i++){
    System.out.println(arr[i]);
}
```
```java
// Java 5
int arr[]={2,11,45,9};

for (int num : arr) {
    System.out.println(num);
}
```
---
###### Java 6: It's 2006
- Improvements on many areas :
  - monitoring and instrumentation
  - networking
  - performance
  - reflection
  - RMI
  - security
  - serialization
- But no language improvements

---
###### Java 7: It's 2011
- Strings in switch Statements
- The try-with-resources Statement
- Type Inference for Generic Instance Creation
- Catching Multiple Exception Types
---
###### Java 7: Strings in switch Statements
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
###### Java 7: The try-with-resources Statement

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
###### Java 7: Type Inference for Generic Instance Creation


```java
// Java 6
Map<String, List<String>> myMap = new HashMap<String, List<String>>();
```
```java
// Java 7
Map<String, List<String>> myMap = new HashMap<>();
```


---

###### Java 7: Catching Multiple Exception Types


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
###### Java 8: It's 2014
- Lambda expressions
- Streams 
- Functional API
- Optional class


---

###### Java 8: lambda expressions
```java
@FunctionalInterface
interface MyFunctionalInterface {
  public String sayHello(String name);
}
```
[//]: # (Java 8 adds functional programming through what are called lambda  xpressions, which is a simple way of describing a function as some operation on an arbitrary set of supplied variables. All of the variables of the expression must be explicitly supplied; you don't access or store data that's not represented as a parameter. This makes lambda expressions more self-documenting, and the code is immune to hidden variables or states called side-effects. You can describe the transformation from input to output in lambda terms, and the details of transformations and recursions are hidden, which reduces complexity and errors. Lambda or functional language expressions can also facilitate parallelism because every variable is always represented as a parameter, so it follows you can run an expression anywhere and it will return the correct result if you give it the correct parameters. You can also split the lambda expression across several platforms and again get the same result. Lambda expressions add functional programming to Java 8, but the traditional imperative model is still available.)

---
###### Java 8: lambda expressions: functional interfaces
```java 
// Java 7
MyFunctionalInterface msg = new MyFunctionalInterface() {
  @Override
  public String sayHello(String name) {
    return "Hello " + name;
  }
};
System.out.println(msg.sayHello("Lambda!"));
```

```java 
// Java 8: lambda expression
MyFunctionalInterface msg = (name) -> {
  return "Hello " + name;
};
System.out.println(msg.sayHello("Lambda!"));
```
---
###### Java 8: lambda expressions: functional interfaces
```java 
// Java 7
Arrays.sort(dogArray, new Comparator<Dog>() {
  @Override
  public int compare(Dog o1, Dog o2) {
    return o1.getWeight() - o2.getWeight();
  }
});
```
```java 
// Java 8
Arrays.sort(dogArray, (m, n) -> m.getWeight() - n.getWeight());
```
---
###### Java 8: lambda expressions: iterate list
```java 
// Java 7
public void iterateList(List<String> names) {
  for (String name : names) {
    System.out.println(iterator.next());
  }
}
```

```java 
// Java 8: lambda expression
public void iterateList(List<String> names) {
  // Iterable.forEach is added in JDK8 to take profit of lambda expressions
  names.forEach(name->System.out.println(name));
}
```
---
###### Java 8: lambda expressions: method references
```java 
// Java 8: lambda expression
public void iterateList(List<String> names) {
  // Iterable.forEach is added in JDK8 to take profit of lambda expressions
  names.forEach(name->System.out.println(name));
}
```
```java 
// Java 8: lambda expression
public void iterateList(List<String> names) {
  // Instead of implement a lambda for an existing method, we can use method reference
  names.forEach(System.out::println);
}
```
---
###### Java 8: Streams & Functional API
```java 
// Java 7
List<Transaction> groceryTransactions = new Arraylist<>(); 
for(Transaction t: transactions){  
  if(t.getType() == Transaction.GROCERY){   
    groceryTransactions.add(t);  
  } 
} 
Collections.sort(groceryTransactions, new Comparator(){  
  public int compare(Transaction t1, Transaction t2){   
    return t2.getValue().compareTo(t1.getValue());  
  } 
}); 
List<Integer> transactionIds = new ArrayList<>(); 
for(Transaction t: groceryTransactions){  
  transactionsIds.add(t.getId()); 
}
```
---
###### Java 8: Streams & Functional API
```java 
// Java 8
List<Integer> transactionsIds = transactions.stream()   
  .filter(t -> t.getType() == Transaction.GROCERY)   
  .sorted(comparing(Transaction::getValue).reversed())   
  .map(Transaction::getId)   
  .collect(toList());
```
<style>
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
</style>
![saturate center](assets/streams.png)

---
###### Java 8: But also Parallel Streams
```java 
// Java 8
List<Integer> transactionsIds = transactions.parallelStream()   
  .filter(t -> t.getType() == Transaction.GROCERY)   
  .sorted(comparing(Transaction::getValue).reversed())   
  .map(Transaction::getId)   
  .collect(toList());
```
Just using *parallelStream()*  instead of *stream()*  we obtain the same result but taking profit of multiple CPU cores! (*)

<br>
<br>
<br>
(*) multithreading benefits are not granted on all conditions!


---
###### Java 8: Optional class
```java 
// Java 7
String result = this.buildResult();
if (result == null) {
    return "n/a";
}

return result.toUpperCase();
```

```java 
// Java 8
return Optional.ofNullable(buildResult())
               .map(String::toUpperCase)
               .orElse("n/a");
```
---
###### Java 8: Optional class
```java 
// Java 7
String version = "UNKNOWN";
if(computer != null){
  Soundcard soundcard = computer.getSoundcard();
  if(soundcard != null){
    USB usb = soundcard.getUSB();
    if(usb != null){
      version = usb.getVersion();
    }
  }
}
// Java 8
String version = computer.flatMap(Computer::getSoundcard)
                        .flatMap(Soundcard::getUSB)
                        .map(USB::getVersion)
                        .orElse("UNKNOWN");
```
---
###### Java 9: It's 2017
- No remarkable language improvements
<br>
- Reactive Streams 
- HTTP 2.0 (Google SPDY) Support
- Modular system (jigsaw)
- Java + REPL (Read-Eval-Print-Loop) = jshell

- Removes support for 1.5 and earlier source and target options




---
###### Java 10: It's 2018
- Local Variable Type Inference
<br>
- GC improvements
- Bytecode generation improvement
- Security improvements
- Lots of deprecations



---
###### Java 10: Local Variable Type Inference
```java 
// Java 9
public void method() {
  Map<String, String> map = new HashMap<>();
  map.put("APL", "Apple");
  map.put("SMG", "Samsung");
  map.forEach((k,v)-> System.out.println(k + " " + v));
}
```
```java 
// Java 10
public void method() {
  var map = new HashMap<>();
  map.put("APL", "Apple");
  map.put("SMG", "Samsung");
  map.forEach((k,v)-> System.out.println(k + " " + v));
}
```
---
###### Java 11: It's still 2018
- Local-Variable Syntax for Lambda Parameters
 (Allowing 'var' for the formal parameters of an implicitly typed lambda expression)
<br>
- LTS version
- Oracle JDK is no longer free for commercial use

- JEP 321: HTTP Client

---
###### Java 12: It's  2019
- Switch Expressions
  
<br>

---
###### Java 12: Switch Expressions
```java
// Java 7
int numberOfLetters;
switch (fruit) {
case PEAR:
    numberOfLetters = 4;
    break;
case APPLE:
case MANGO:
    numberOfLetters = 5;
    break;
case ORANGE:
case PAPAYA:
    numberOfLetters = 6;
    break;
default:
    numberOfLetters = 0;
}
```
---
###### Java 12: Switch Expressions
```java
// Java 12
int numberOfLetters = switch (fruit) {
    case PEAR -> 4;
    case APPLE, MANGO -> 5;
    case ORANGE, PAPAYA -> 6;
    default      -> {
        // We can also write blocks of code and return with yield
        int result = 0
        yield result;
    }
}

```

---

###### Java 13: It's still 2019
- No remarkable language improvements
<br>
- Improvements on NIO and networking
- Improvements in memory management
- Improvements in cryptography


---
###### Java 14: It's  2020
- Pattern Matching of instanceof
<br>



---
###### Java 14: Pattern Matching of instanceof
```java
// Java 13
if (obj instanceof Integer) {
    int intValue = (Integer) obj;
    // ... use intValue ...
}
```
```java
// Java 14
if (x instanceof Integer i) {
    // ... use i as an Integer directly ...
}
```
---
###### Java 15: September 2020

- Text Blocks
- Sealed Classes (Preview)
- Records (Second Preview)
<br>
- Hidden Classes
 
---
###### Java 15: Text Blocks

```java
String query = "SELECT `EMP_ID`, `LAST_NAME` FROM `EMPLOYEE_TB`\n" +
               "WHERE `CITY` = 'INDIANAPOLIS'\n" +
               "ORDER BY `EMP_ID`, `LAST_NAME`;\n";
```

```java
String query = """
               SELECT `EMP_ID`, `LAST_NAME` FROM `EMPLOYEE_TB`
               WHERE `CITY` = 'INDIANAPOLIS'
               ORDER BY `EMP_ID`, `LAST_NAME`;
               """;
```
---
###### Java 15: Sealed Classes 

```java
package com.example.geometry;

public sealed class Shape
    permits Circle, Rectangle, Square {...}
```

```java
package com.example.geometry;

sealed class Shape {...}
... class Circle    extends Shape {...}
... class Rectangle extends Shape {...}
... class Square    extends Shape {...}
```
---
###### Java 15: Records (Second Preview)

```java
public record FXOrder(int units,
                      CurrencyPair pair,
                      Side side,
                      double price,
                      LocalDateTime sentAt,
                      int ttl) {}
```

```java
var order = new FXOrder(1, 
                    CurrencyPair.GBPUSD, 
                    Side.Bid, 
                    1.25, 
                    LocalDateTime.now(), 
                    1000);

```



---
![bg](assets/historyOfJava.png)
#### Thoughts
