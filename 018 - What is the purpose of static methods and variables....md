# What is the purpose of static methods and variables?

## (`static` Methods နဲ့ Variables တွေရဲ့ ရည်ရွယ်ချက်က ဘာလဲ?) — Core Java Interview

ဒီမေးခွန်းက Java ရဲ့ **Class-level Members, Memory Management, Object-Oriented Programming** Concept ကို နားလည်ထားလား စစ်တဲ့ အရေးကြီးတဲ့ Interview Question ဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

**`static` keyword is used to create class-level variables and methods that belong to the class itself rather than individual objects.**

မြန်မာလိုဆိုရရင်—

> **static variable နဲ့ static method တွေက Object တစ်ခုချင်းစီအတွက် မဟုတ်ဘဲ Class တစ်ခုလုံးအတွက် သက်ဆိုင်တဲ့ Members တွေ ဖြစ်ပါတယ်။**

---

# 2. What is static variable?

## Definition

`static variable` ဆိုတာ Class ထဲမှာ `static` keyword သုံးပြီး Declare လုပ်ထားတဲ့ Variable ဖြစ်ပါတယ်။

ဒါကို—

- Class Variable
- Static Variable

လို့ခေါ်ပါတယ်။

---

## Example

```java
class Student {

    int id;
    String name;

    static String school = "ABC School";

}
```

ဒီမှာ—

```java
static String school;
```

က Static Variable ဖြစ်ပါတယ်။

---

# 3. Why do we use static variables?

အဓိက ရည်ရွယ်ချက်က—

> **To share common data among all objects of a class.**

ဖြစ်ပါတယ်။

---

## Without static

```java
class Student {

    String school;

}
```

Object တစ်ခုချင်းစီမှာ Copy တစ်ခုစီ ရှိပါတယ်။

```
Student Object 1
school = ABC

Student Object 2
school = ABC

Student Object 3
school = ABC
```

Memory ပိုသုံးပါတယ်။

---

## With static

```java
class Student {

    static String school = "ABC";

}
```

Memory မှာ တစ်ခုတည်းရှိပါတယ်။

```
        Student Class

        school
          |
          |
-----------------
|       |        |
Obj1   Obj2     Obj3
```

အားလုံး Share လုပ်ပါတယ်။

---

# 4. Example of Static Variable

```java
class Student {

    int id;
    String name;

    static String school = "MIT";

    Student(int id, String name){

        this.id = id;
        this.name = name;

    }

    void display(){

        System.out.println(id + " " + name + " " + school);

    }

}
```

Main:

```java
public class Main {

    public static void main(String[] args){

        Student s1 = new Student(1, "Aung");
        Student s2 = new Student(2, "Mg Mg");

        s1.display();
        s2.display();

    }

}
```

Output:

```
1 Aung MIT
2 Mg Mg MIT
```

`school` ကို Object နှစ်ခုလုံး Share လုပ်ပါတယ်။

---

# 5. What is static method?

## Definition

`static method` ဆိုတာ Class နဲ့ သက်ဆိုင်တဲ့ Method ဖြစ်ပြီး Object မဖန်တီးဘဲ ခေါ်နိုင်တဲ့ Method ဖြစ်ပါတယ်။

---

## Example

```java
class Calculator {

    static int add(int a, int b){

        return a + b;

    }

}
```

Call:

```java
public class Main {

    public static void main(String[] args){

        int result = Calculator.add(10,20);

        System.out.println(result);

    }

}
```

Object မလိုပါဘူး။

---

# 6. Why do we use static methods?

## 1. Utility Methods

Object State မလိုတဲ့ Methods တွေအတွက် သုံးပါတယ်။

Examples:

```java
Math.max(10,20);

Math.sqrt(25);
```

`Math` Class မှာ Static Methods တွေ အများကြီးရှိပါတယ်။

---

## 2. Common Operations

Example:

```java
class Calculator {

    static double calculateTax(double amount){

        return amount * 0.05;

    }

}
```

Tax Calculation က Object တစ်ခုချင်းစီနဲ့ မသက်ဆိုင်လို့ static သုံးနိုင်ပါတယ်။

---

## 3. Main Method

Java Program စတင်တဲ့ Method:

```java
public static void main(String[] args)
```

ဘာကြောင့် static လဲ?

JVM က Object မဖန်တီးဘဲ `main()` ကို ခေါ်ဖို့ လိုလို့ ဖြစ်ပါတယ်။

---

# 7. Static Method Rules

## Rule 1: Static Method can access only static members directly

Example:

```java
class Test {

    int x = 10;

    static void display(){

        System.out.println(x);

    }

}
```

❌ Error

ဘာကြောင့်လဲ?

`x` က Instance Variable ဖြစ်ပြီး Object လိုအပ်ပါတယ်။

---

Correct:

```java
class Test {

    static int x = 10;

    static void display(){

        System.out.println(x);

    }

}
```

✅ Valid

---

# 8. Static vs Instance Members

|Feature|Static|Instance|
|---|---|---|
|Belongs to|Class|Object|
|Memory|Method Area|Heap|
|Object Required|No|Yes|
|Created|Class Loading|Object Creation|
|Access|Class Name|Object Reference|

---

# 9. Static Memory Concept

Example:

```java
class Employee {

    static String company = "ABC";

    int salary;

}
```

Memory:

```
Method Area
----------------
Employee Class
company = ABC


Heap
----------------
Employee Object 1
salary = 5000

Employee Object 2
salary = 7000
```

---

# 10. Real World Examples

## Static Variables

### Company Name

```java
static String companyName;
```

Employee အားလုံး Company တူလို့ Share လုပ်နိုင်ပါတယ်။

---

## Static Methods

### Utility Classes

Examples:

```java
Arrays.sort();

Collections.sort();

Math.random();
```

အားလုံး Static Methods ဖြစ်ပါတယ်။

---

# 11. Interview Answer (1 Minute)

> **"The purpose of the static keyword in Java is to create members that belong to the class rather than individual objects. Static variables are used to store common data shared by all objects of a class, which saves memory. Static methods are used for operations that do not require object-specific data and can be called using the class name without creating an object. The main method is static because the JVM calls it without creating an object."**

---

# 12. Common Follow-up Interview Questions

1. Why is main method static?
2. Can static methods access non-static variables?
3. Can we override static methods?
4. Where are static variables stored?
5. Difference between static and final?
6. Can a constructor be static?
7. Why do we use static blocks?

---

# Interview Key Points ⭐

မှတ်ထားရန်—

```
static variable
        ↓
One copy per class
        ↓
Shared by all objects


static method
        ↓
Belongs to class
        ↓
Call without object
```

အရေးကြီးဆုံး Sentence:

> **"Static members are class-level members. They are created once when the class is loaded and shared among all objects of that class."** ✅