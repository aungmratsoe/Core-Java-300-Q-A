# What are the differences between JDK, JRE, and JVM?

## (JDK, JRE, JVM တို့ရဲ့ ကွာခြားချက်များ) — Core Java Interview

ဒီမေးခွန်းက **Java Interview မှာ အရေးအကြီးဆုံး မေးခွန်းတွေထဲက တစ်ခု** ဖြစ်ပါတယ်။

Beginner Java Developer အများစုက **JDK, JRE, JVM** ကို ရောထွေးတတ်ကြပါတယ်။ Interview မှာ ဒီသုံးခုကို သေချာခွဲပြီး ရှင်းပြနိုင်ရပါမယ်။

---

# 1. Short Answer (အတိုချုပ်)

```
JDK = JRE + Development Tools

JRE = JVM + Java Libraries

JVM = Executes Java Bytecode
```

Diagram:

```
             JDK
   +-----------------------+
   |                       |
   |        JRE            |
   |  +---------------+    |
   |  |               |    |
   |  |     JVM       |    |
   |  |               |    |
   |  +---------------+    |
   |                       |
   | Development Tools     |
   | (javac, javadoc...)   |
   +-----------------------+
```

---

# 2. What is JVM? (Java Virtual Machine)

## Definition

**JVM (Java Virtual Machine)** ဆိုတာ Java Bytecode ကို Execute လုပ်ပေးတဲ့ Virtual Machine ဖြစ်ပါတယ်။

Java Source Code ကို JVM က တိုက်ရိုက် မဖတ်ပါဘူး။

Flow:

```
Hello.java
    |
    | javac
    ↓
Hello.class (Bytecode)
    |
    ↓
JVM
    |
    ↓
Machine Code
    |
    ↓
Output
```

---

## JVM ရဲ့ Responsibilities

JVM က အောက်ပါအလုပ်တွေ လုပ်ပေးပါတယ်။

### 1. Load Class

`.class` file ကို Memory ထဲ Load လုပ်တယ်။

### 2. Verify Bytecode

Bytecode မှာ Security Problem ရှိမရှိ စစ်တယ်။

### 3. Execute Code

Interpreter နဲ့ JIT Compiler အသုံးပြုပြီး Execute လုပ်တယ်။

### 4. Manage Memory

- Heap
- Stack
- Garbage Collection

တွေကို Manage လုပ်တယ်။

---

## Example

Java Program:

```java
public class Hello {

    public static void main(String[] args) {

        System.out.println("Hello Java");

    }
}
```

Compile:

```
Hello.java
     |
     ↓
Hello.class
```

Run:

```
java Hello
```

ဒီအချိန်မှာ JVM က Bytecode ကို Execute လုပ်ပေးပါတယ်။

---

# 3. What is JRE? (Java Runtime Environment)

## Definition

**JRE (Java Runtime Environment)** ဆိုတာ Java Application တွေကို Run ဖို့ လိုအပ်တဲ့ Environment ဖြစ်ပါတယ်။

JRE ထဲမှာ

```
JRE

+----------------+
|      JVM       |
+----------------+

+----------------+
| Java Libraries |
+----------------+
```

ပါဝင်ပါတယ်။

---

## JRE Contains

### 1. JVM

Java Program ကို Run လုပ်ပေးဖို့

### 2. Java Class Libraries

အသုံးများတဲ့ Built-in Classes တွေ

ဥပမာ

```
java.lang
java.util
java.io
java.net
```

---

## JRE ကို ဘယ်သူသုံးလဲ?

Java Application ကို **Run ပဲလုပ်မယ့် User** တွေက JRE လိုပါတယ်။

ဥပမာ:

- Banking Client Software
- Desktop Java Application
- Java-based Tool

သူတို့က Code ရေးစရာမလိုပါဘူး။

---

# 4. What is JDK? (Java Development Kit)

## Definition

**JDK (Java Development Kit)** ဆိုတာ Java Application တွေကို Develop လုပ်ဖို့ အသုံးပြုတဲ့ Complete Package ဖြစ်ပါတယ်။

JDK ထဲမှာ

```
JDK

+----------------+
|      JRE       |
|  +---------+   |
|  |   JVM   |   |
|  +---------+   |
+----------------+

+----------------+
| Development    |
| Tools          |
+----------------+
```

ပါဝင်ပါတယ်။

---

## JDK Contains

### 1. JRE

Application Run ဖို့

### 2. Development Tools

ဥပမာ

|Tool|Purpose|
|---|---|
|javac|Java Compiler|
|java|Run Java Program|
|javadoc|Generate Documentation|
|jar|Create Java Archive|
|jdb|Java Debugger|

---

## Example

Java Developer တစ်ယောက်က

```java
class Student {

}
```

ရေးတဲ့အခါ

Compile လုပ်ဖို့

```
javac Student.java
```

လိုပါတယ်။

ဒီ `javac` က JDK ထဲမှာ ပါပါတယ်။

---

# 5. Comparison Table

|Feature|JVM|JRE|JDK|
|---|---|---|---|
|Full Name|Java Virtual Machine|Java Runtime Environment|Java Development Kit|
|Purpose|Execute Bytecode|Run Java Applications|Develop Java Applications|
|Contains|-|JVM + Libraries|JRE + Development Tools|
|Used By|JVM internally|End Users|Java Developers|
|Compile Code|❌ No|❌ No|✅ Yes|
|Run Code|✅ Yes|✅ Yes|✅ Yes|

---

# 6. Real World Example

Imagine Java ကို ကားတစ်စီးနဲ့ နှိုင်းမယ်ဆိုရင်

## JVM = Engine

ကားကို အလုပ်လုပ်စေတဲ့ အဓိကအစိတ်အပိုင်း

---

## JRE = Complete Car

Engine + အခြားလိုအပ်တဲ့ အစိတ်အပိုင်းတွေ

ကားကို မောင်းနိုင်ပြီ။

---

## JDK = Car Factory

ကားတည်ဆောက်ဖို့ လိုအပ်တဲ့ Tools အားလုံး ပါတယ်။

---

# 7. When Do We Need Them?

## Java Developer

လိုအပ်တာ:

```
JDK
```

ဘာကြောင့်လဲ?

- Write Code
- Compile Code
- Debug Code
- Run Code

အားလုံးလုပ်ရလို့ပါ။

---

## Normal User

လိုအပ်တာ:

```
JRE
```

Java Application Run ပဲ လုပ်မယ်ဆိုရင် လုံလောက်ပါတယ်။

---

## JVM

User က သီးခြား Install လုပ်တာမဟုတ်ပါဘူး။

JRE/JDK ထဲမှာ ပါပြီးသား ဖြစ်ပါတယ်။

---

# 8. Interview Answer (1 Minute)

> **"JDK, JRE, and JVM are three important components of Java. JVM is the core component that executes Java bytecode and provides platform independence. JRE contains JVM and Java libraries required to run Java applications. JDK is a complete development kit that contains JRE along with development tools such as javac, javadoc, and debugger tools. In simple terms, JVM runs Java code, JRE provides the runtime environment, and JDK is used by developers to create Java applications."**

---

# 9. Common Follow-up Interview Questions

Interviewer က ဆက်မေးနိုင်တာများ—

1. Why is Java platform independent?
2. What happens when we run a Java program?
3. What is the role of javac?
4. Is JVM platform dependent or independent?
5. Can we run Java program without JDK?
6. Can we develop Java application using only JRE?
7. What are the components of JVM?
8. Difference between JDK 8 and JDK 17?
9. What is JIT Compiler?
10. Why do we need JVM?

---

# 10. Interview Memory Trick ⭐

မှတ်ရလွယ်အောင်—

```
JVM → Run Java Bytecode

JRE → Run Java Application

JDK → Develop Java Application
```

ဒါကို မှတ်ထားရင် Interview မှာ အလွယ်တကူ ဖြေနိုင်ပါတယ်။

**Java Developer တစ်ယောက်အတွက် အရေးကြီးဆုံးက JDK ဖြစ်ပြီး၊ Java ရဲ့ Platform Independence ရဲ့ အခြေခံက JVM ဖြစ်ပါတယ်။**