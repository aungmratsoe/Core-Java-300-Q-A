# What is the difference between an Object-Oriented Programming Language and an Object-Based Programming Language?

## (Object-Oriented Programming Language နဲ့ Object-Based Programming Language တို့ရဲ့ ကွာခြားချက်) — Core Java Interview

ဒီမေးခွန်းက Interview မှာ **OOP Concepts** ကို နက်နက်ရှိုင်းရှိုင်း နားလည်ထားလားဆိုတာ စစ်တဲ့ မေးခွန်းဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

### Object-Oriented Programming Language (OOP)

> **Object-Oriented Programming Language** ဆိုတာ **Objects** ကို အခြေခံပြီး Program ရေးတဲ့ Language ဖြစ်ပြီး OOP ရဲ့ **4 Pillars** ကို Support လုပ်ပါတယ်။

- ✅ Encapsulation
- ✅ Inheritance
- ✅ Polymorphism
- ✅ Abstraction

**Examples:**

- Java
- C++
- C#
- Python

---

### Object-Based Programming Language

> **Object-Based Programming Language** ဆိုတာလည်း Objects ကို အသုံးပြုပါတယ်။ ဒါပေမယ့် **Inheritance** နဲ့ **Polymorphism** ကို မပံ့ပိုးပါဘူး။

**Examples:**

- JavaScript (Traditional View)
- VBScript
- Adobe ActionScript

> **မှတ်ချက်:** ယနေ့ခေတ် JavaScript (ES6+) မှာ `class` နဲ့ inheritance ရှိလာတဲ့အတွက် JavaScript ကို OOP Style နဲ့လည်း ရေးနိုင်ပါတယ်။ ဒါပေမယ့် Interview တွေမှာတော့ Traditional Definition အရ Object-Based Language အဖြစ် မေးလေ့ရှိပါတယ်။

---

# 2. What is Object-Oriented Programming?

Object-Oriented Programming မှာ—

- Objects
- Classes
- Inheritance
- Polymorphism
- Abstraction
- Encapsulation

အားလုံး ပါဝင်ပါတယ်။

Java က **Complete Object-Oriented Features** အများစုကို Support လုပ်ပါတယ်။

Example

```java
class Animal {

    void sound() {
        System.out.println("Animal Sound");
    }

}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }

}
```

ဒီမှာ

- `extends` → Inheritance
- `@Override` → Polymorphism

---

# 3. What is Object-Based Programming?

Object-Based Language မှာ—

- Objects ရှိတယ်။
- Encapsulation ရှိတယ်။
- Classes (သို့) Objects ရှိနိုင်တယ်။

ဒါပေမယ့်

❌ Inheritance မရှိ

❌ Runtime Polymorphism မရှိ

---

ဥပမာ

```
Calculator Object

+
-
*
/
```

Object ကို အသုံးပြုနိုင်ပေမယ့် Class Inheritance မရှိဘူး။

---

# 4. Main Difference

## Object-Oriented Language

Supports

```
Object
Class
Encapsulation
Inheritance
Polymorphism
Abstraction
```

---

## Object-Based Language

Supports

```
Object
Encapsulation
```

Does NOT support

```
Inheritance
Runtime Polymorphism
```

---

# 5. Comparison Table

|Feature|Object-Oriented|Object-Based|
|---|---|---|
|Object|✅ Yes|✅ Yes|
|Class|✅ Yes|✅ Usually Yes|
|Encapsulation|✅ Yes|✅ Yes|
|Inheritance|✅ Yes|❌ No (traditional definition)|
|Polymorphism|✅ Yes|❌ No|
|Abstraction|✅ Yes|Limited / ❌|
|Code Reusability|✅ High|❌ Limited|

---

# 6. Real-World Example

## Object-Oriented

```
Animal
   │
   ├── Dog
   ├── Cat
   └── Lion
```

Child Classes က Parent Class ကို Inherit လုပ်နိုင်ပါတယ်။

---

## Object-Based

```
Dog Object

Cat Object

Lion Object
```

Object တွေ ရှိပေမယ့် Parent-Child Relationship မရှိပါဘူး။

---

# 7. Why Java is Object-Oriented?

Java မှာ

✅ Class

```java
class Student {

}
```

✅ Object

```java
Student s = new Student();
```

✅ Inheritance

```java
class Dog extends Animal {

}
```

✅ Polymorphism

```java
@Override
```

✅ Encapsulation

```java
private int age;
```

✅ Abstraction

```java
abstract class Shape {

}
```

အားလုံး ရှိတဲ့အတွက် Java ကို **Object-Oriented Programming Language** လို့ ခေါ်ပါတယ်။

---

# 8. Interview Answer (1 Minute)

> **"An Object-Oriented Programming language supports all four core OOP principles: Encapsulation, Inheritance, Polymorphism, and Abstraction. Examples include Java, C++, and C#. An Object-Based Programming language also uses objects and supports encapsulation, but traditionally does not support inheritance and runtime polymorphism. Therefore, object-oriented languages provide greater code reuse and flexibility than object-based languages."**

---

# 9. Common Follow-up Interview Questions

1. Is Java 100% Object-Oriented?
2. Why is Java called an Object-Oriented language?
3. What are the four pillars of OOP?
4. What is Inheritance?
5. What is Polymorphism?
6. Is JavaScript Object-Oriented or Object-Based?
7. Difference between OOP and Procedural Programming?

---

# 10. Interview Key Points ⭐

```
Object-Oriented Programming

✔ Object
✔ Class
✔ Encapsulation
✔ Inheritance
✔ Polymorphism
✔ Abstraction
```

```
Object-Based Programming

✔ Object
✔ Encapsulation

✘ Inheritance
✘ Runtime Polymorphism
```

---

## Memory Trick ⭐

**Object-Oriented = OOP 4 Pillars**

```
E → Encapsulation
I → Inheritance
P → Polymorphism
A → Abstraction
```

**Object-Based = Objects Only (Traditional Definition)**

```
Object
+
Encapsulation

(No Inheritance, No Runtime Polymorphism)
```

---

## Final Answer

> **An Object-Oriented Programming language supports all four OOP principles—Encapsulation, Inheritance, Polymorphism, and Abstraction. An Object-Based Programming language supports objects and encapsulation but traditionally does not support inheritance and runtime polymorphism. Therefore, Object-Oriented languages provide better code reuse, extensibility, and flexibility than Object-Based languages.** ✅