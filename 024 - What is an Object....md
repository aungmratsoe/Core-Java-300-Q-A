# What is an Object?

## (Object ဆိုတာ ဘာလဲ?) — Core Java Interview

ဒီမေးခွန်းက Java Interview တွေမှာ **အမေးအများဆုံး OOP Basic Question** ဖြစ်ပါတယ်။

Java ဟာ **Object-Oriented Programming (OOP)** Language ဖြစ်တဲ့အတွက် **Object** ဆိုတာ ဘာလဲဆိုတာ နားလည်ထားဖို့ အရမ်းအရေးကြီးပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

**An object is an instance of a class.**

မြန်မာလိုဆိုရရင်—

> **Object ဆိုတာ Class တစ်ခုကနေ ဖန်တီးထားတဲ့ Instance (အမှန်တကယ် တည်ရှိတဲ့ အရာ) ဖြစ်ပါတယ်။**

Class က **Blueprint (ပုံစံ)** ဖြစ်ပြီး Object က **Blueprint အတိုင်း ဆောက်ထားတဲ့ အရာ** ဖြစ်ပါတယ်။

---

# 2. Real-World Example

ဥပမာ **Car** ကို စဉ်းစားကြည့်ပါ။

### Blueprint

ကားဆောက်ဖို့ Design Drawing (Blueprint)

↓

### Actual Car

လမ်းပေါ်မှာ မောင်းနေတဲ့ ကား

ဒီလိုပဲ Java မှာ

```
Class
   ↓
Object
```

---

### Another Example

Class

```
Student
```

Objects

```
Student 1 (Aung)
Student 2 (Su Su)
Student 3 (Mg Mg)
```

Student Class တစ်ခုကနေ Student Object အများကြီး ဖန်တီးနိုင်ပါတယ်။

---

# 3. Definition

Object တစ်ခုမှာ အဓိက အချက် (၃) ခု ရှိပါတယ်။

### 1. State (Properties)

Object ရဲ့ Data တွေ

ဥပမာ Car

- Color
- Brand
- Speed

---

### 2. Behavior (Methods)

Object လုပ်နိုင်တဲ့ အလုပ်တွေ

ဥပမာ

- Start()
- Stop()
- Accelerate()

---

### 3. Identity

Object တစ်ခုချင်းစီကို ခွဲခြားပေးတဲ့ Unique Identity ဖြစ်ပါတယ်။

ဥပမာ—

ကားနှစ်စီးလုံး Toyota ဖြစ်နိုင်ပေမယ့် Registration Number မတူသလို၊ Java မှာလည်း Object တစ်ခုချင်းစီမှာ Memory Reference မတူပါဘူး။

---

# 4. Java Example

### Class

```java
class Student {

    String name;
    int age;

    void study() {
        System.out.println(name + " is studying.");
    }

}
```

---

### Creating Objects

```java
public class Main {

    public static void main(String[] args) {

        Student s1 = new Student();

        s1.name = "Aung";
        s1.age = 22;

        s1.study();

    }

}
```

Output

```
Aung is studying.
```

---

# 5. Memory Representation

```
Class
----------------
Student

Fields
name
age

Methods
study()

        │
        │ new
        ▼

Heap Memory
----------------
Student Object

name = Aung
age = 22
```

`new` keyword က Object ကို Heap Memory ထဲမှာ ဖန်တီးပေးပါတယ်။

---

# 6. Multiple Objects

```java
class Student {

    String name;

}
```

```
Student s1 = new Student();
Student s2 = new Student();
Student s3 = new Student();
```

Memory

```
Heap

Object 1
name = Aung

Object 2
name = Su Su

Object 3
name = Mg Mg
```

Object တစ်ခုချင်းစီမှာ ကိုယ်ပိုင် Data ရှိပါတယ်။

---

# 7. How is an Object Created?

Java မှာ Object ကို `new` keyword နဲ့ ဖန်တီးပါတယ်။

Syntax

```java
ClassName objectName = new ClassName();
```

Example

```java
Car car = new Car();
```

ဒီမှာ

- `Car` → Class
- `car` → Reference Variable
- `new Car()` → Object Creation

---

# 8. Class vs Object

|Class|Object|
|---|---|
|Blueprint|Actual Instance|
|Logical Entity|Physical Entity (Memory ထဲမှာ တည်ရှိ)|
|Memory မယူသေး|Memory ယူထားတယ်|
|Template|Real Object|
|One Class|Many Objects|

---

# 9. Real-Life Example

### Mobile Phone

Class

```
Mobile
```

Properties

- Brand
- Model
- Color

Methods

- Call()
- Message()
- Camera()

Objects

```
Phone 1
Samsung

Phone 2
iPhone

Phone 3
Xiaomi
```

အားလုံး Mobile Class ကနေ ဖန်တီးထားတာ ဖြစ်ပါတယ်။

---

# 10. Advantages of Objects

- ✅ Real-world modeling လုပ်ရလွယ်တယ်။
- ✅ Code ကို ပြန်အသုံးပြုနိုင်တယ်။
- ✅ Data နဲ့ Methods ကို တစ်နေရာတည်းမှာ စုစည်းထားနိုင်တယ်။
- ✅ Maintenance လုပ်ရလွယ်တယ်။
- ✅ OOP Concepts (Encapsulation, Inheritance, Polymorphism) ကို အသုံးချနိုင်တယ်။

---

# 11. Interview Answer (1 Minute)

> **"An object is an instance of a class. It is a real entity that occupies memory and contains state (data), behavior (methods), and identity. Objects are created using the `new` keyword in Java. A class acts as a blueprint, while objects are the actual instances created from that blueprint. One class can be used to create many objects, each having its own state but sharing the same behavior defined in the class."**

---

# 12. Common Follow-up Interview Questions

1. What is the difference between a Class and an Object?
2. How do you create an object in Java?
3. Where are objects stored in memory?
4. What is the `new` keyword?
5. Can one class create multiple objects?
6. What are the characteristics of an object?
7. What is the difference between an object and a reference variable?

---

# 13. Interview Key Points ⭐

```
Class
   │
   │ new
   ▼
Object
```

### Object = 3 Characteristics

```
Object

├── State (Data)
├── Behavior (Methods)
└── Identity (Unique Reference)
```

---

## Final Answer

> **An object is an instance of a class. It represents a real-world entity, occupies memory, and contains state (fields), behavior (methods), and identity. In Java, objects are created using the `new` keyword, and multiple objects can be created from the same class.** ✅