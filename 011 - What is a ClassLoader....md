# What is a ClassLoader?

## (ClassLoader ဆိုတာ ဘာလဲ?) — Core Java Interview

ဒီမေးခွန်းက **JVM Architecture** နဲ့ **Java Class Loading Mechanism** ကို နားလည်ထားလား စစ်တဲ့ အရေးကြီးတဲ့ Interview Question ဖြစ်ပါတယ်။

---

# 1. Definition (အဓိပ္ပာယ်)

**ClassLoader** ဆိုတာ JVM ရဲ့ အစိတ်အပိုင်းတစ်ခုဖြစ်ပြီး **Java Class (.class file) တွေကို JVM Memory ထဲသို့ Load လုပ်ပေးတဲ့ Component** ဖြစ်ပါတယ်။

အလွယ်ပြောရရင်—

> **ClassLoader = JVM ထဲကို Class တွေ သွင်းပေးတဲ့ Mechanism**

ဖြစ်ပါတယ်။

---

# 2. Why do we need ClassLoader?

Java Program Run လုပ်တဲ့အခါ `.class` file တွေကို တစ်ခါတည်း Memory ထဲ အကုန်မတင်ပါဘူး။

လိုအပ်တဲ့ Class ကိုပဲ **Runtime မှာ Dynamic Loading** လုပ်ပါတယ်။

ဥပမာ—

```java
public class Main {

    public static void main(String[] args) {

        Student s = new Student();

    }

}
```

Run လုပ်တဲ့အခါ JVM က—

1. `Main.class` ကို Load လုပ်မယ်။
2. `Student.class` လိုအပ်တဲ့အခါ Load လုပ်မယ်။

ဒီအလုပ်ကို ClassLoader က လုပ်ပေးပါတယ်။

---

# 3. Class Loading Process

Java Class Loading မှာ အဓိက အဆင့် ၃ ခု ရှိပါတယ်။

```
.class File

     |
     ↓

Loading

     |
     ↓

Linking

     |
     ↓

Initialization

     |
     ↓

Class Ready to Use
```

---

# 4. ClassLoader Responsibilities

ClassLoader ရဲ့ အဓိက တာဝန် ၃ ခုရှိပါတယ်။

---

# (1) Loading

### အလုပ်

`.class` file ကို ရှာပြီး JVM Memory ထဲ Load လုပ်ပါတယ်။

Example:

```
Student.class
        |
        ↓
JVM Memory
```

---

# (2) Linking

Loading ပြီးရင် Linking လုပ်ပါတယ်။

Linking မှာ အဆင့် ၃ ခုရှိပါတယ်။

---

## a. Verification

Bytecode မှန်ကန်မှု စစ်ဆေးပါတယ်။

စစ်ဆေးတာတွေ—

- Invalid bytecode
- Security issues
- Type errors

---

## b. Preparation

Static variables အတွက် Memory Allocate လုပ်ပါတယ်။

Example:

```java
class Student {

    static int count = 0;

}
```

`count` အတွက် Memory ပြင်ဆင်ပေးပါတယ်။

---

## c. Resolution

Symbolic References တွေကို Direct References အဖြစ် ပြောင်းပေးပါတယ်။

---

# (3) Initialization

Class ရဲ့ Static Variables နဲ့ Static Blocks တွေကို Execute လုပ်ပါတယ်။

Example:

```java
class Test {

    static int value = 100;

    static {

        System.out.println("Class Loaded");

    }

}
```

Initialization အချိန်မှာ Static Block Run ပါတယ်။

---

# 5. Types of ClassLoader

JVM မှာ အဓိက ClassLoader ၃ မျိုးရှိပါတယ်။

---

# (1) Bootstrap ClassLoader

### အမြင့်ဆုံး Level ClassLoader ဖြစ်ပါတယ်။

တာဝန်:

Java ရဲ့ Core Classes တွေကို Load လုပ်ပေးပါတယ်။

ဥပမာ:

```java
java.lang.String
java.lang.Object
java.util.ArrayList
```

---

Location:

Java Runtime Library ထဲက Class တွေကို Load လုပ်ပါတယ်။

---

Example:

```java
String s = "Hello";
```

`String.class` ကို Bootstrap ClassLoader က Load လုပ်ပါတယ်။

---

# (2) Platform ClassLoader

(Java 9 နောက်ပိုင်း)

### တာဝန်

Platform-specific Java modules တွေကို Load လုပ်ပါတယ်။

ဥပမာ:

- java.sql
- java.xml

---

# (3) Application ClassLoader

System ClassLoader လို့လည်း ခေါ်ပါတယ်။

### တာဝန်

Developer ရေးထားတဲ့ Application Classes တွေကို Load လုပ်ပါတယ်။

ဥပမာ:

```
MyApplication.class
Student.class
Employee.class
```

---

# 6. ClassLoader Hierarchy

```
        Bootstrap ClassLoader
                |
                ↓
        Platform ClassLoader
                |
                ↓
        Application ClassLoader
                |
                ↓
        User Defined ClassLoader
```

---

# 7. Parent Delegation Model ⭐

Java ClassLoader ရဲ့ အရေးကြီးတဲ့ Concept တစ်ခုက **Parent Delegation Model** ဖြစ်ပါတယ်။

အဓိကအယူအဆ—

> Class တစ်ခု Load လုပ်တဲ့အခါ Child ClassLoader က အရင်မလုပ်ဘဲ Parent ClassLoader ကို အရင်တောင်းပါတယ်။

Flow:

```
Application ClassLoader

        |
        ↓

Platform ClassLoader

        |
        ↓

Bootstrap ClassLoader
```

---

## Why Parent Delegation?

Security အတွက် ဖြစ်ပါတယ်။

ဥပမာ—

User တစ်ယောက်က

```
java.lang.String
```

ဆိုတဲ့ Class အတုရေးထားရင်

JVM က User Class ကို မသုံးဘဲ Bootstrap ClassLoader က Load လုပ်ထားတဲ့ Original String Class ကိုပဲ သုံးပါတယ်။

ဒါကြောင့် Java Security ပိုကောင်းပါတယ်။

---

# 8. Custom ClassLoader

Developer က ကိုယ်ပိုင် ClassLoader ရေးနိုင်ပါတယ်။

အသုံးများတဲ့နေရာများ—

- Application Servers
- Plugin Systems
- Frameworks

ဥပမာ:

- Tomcat
- Spring Boot
- Hibernate

တွေမှာ ClassLoader ကို အသုံးပြုပါတယ်။

---

# 9. Real World Example

Spring Boot Application တစ်ခု Run လုပ်တဲ့အခါ—

```
Application Start

       |
       ↓

JVM Starts

       |
       ↓

ClassLoader Loads

       |
       ↓

Controller.class
Service.class
Repository.class

       |
       ↓

Application Runs
```

ဒီ Class တွေကို Memory ထဲ ထည့်ပေးတာ ClassLoader ဖြစ်ပါတယ်။

---

# 10. Interview Answer (1 Minute)

> **"A ClassLoader is a part of the JVM that loads Java class files into memory at runtime. It performs three main tasks: loading, linking, and initialization. The loading phase brings the class into memory, linking verifies and prepares the class, and initialization executes static blocks and initializes static variables. JVM provides three main class loaders: Bootstrap ClassLoader, Platform ClassLoader, and Application ClassLoader. ClassLoader also follows the parent delegation model to improve security and avoid duplicate class loading."**

---

# 11. Common Follow-up Interview Questions

Interviewer ဆက်မေးနိုင်တာများ—

1. What are the different types of ClassLoaders?
2. How does ClassLoader work internally?
3. What is Parent Delegation Model?
4. Why do we need Custom ClassLoader?
5. Difference between Loading, Linking, and Initialization?
6. When does ClassLoader load a class?
7. Where are loaded classes stored?
8. What happens if two ClassLoaders load the same class?

---

# 12. Interview Key Points ⭐

မှတ်ထားရန်—

```
ClassLoader
     |
     ↓
Loads .class files
     |
     ↓
JVM Memory
     |
     ↓
Execution
```

အရေးကြီးဆုံး Sentence:

> **"ClassLoader is responsible for dynamically loading classes into JVM memory during runtime and is an essential part of Java's dynamic and secure execution environment."**

ဒီ Concept ကို နားလည်ထားရင် နောက်လာမယ့် **JVM Architecture, Garbage Collection, Reflection, Spring Framework Class Loading** မေးခွန်းတွေကို ပိုလွယ်ကူစွာ နားလည်နိုင်ပါတယ်။