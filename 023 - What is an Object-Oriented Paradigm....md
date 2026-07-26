# What is an Object-Oriented Paradigm?

## (Object-Oriented Paradigm (OOP) ဆိုတာ ဘာလဲ?) — Core Java Interview

ဒီမေးခွန်းက Java Interview တွေမှာ **အရမ်းအမေးများတဲ့ Basic OOP Question** ဖြစ်ပါတယ်။

Java ဟာ **Object-Oriented Programming (OOP)** Language ဖြစ်တာကြောင့် ဒီ Concept ကို နားလည်ထားဖို့ အရေးကြီးပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

**Object-Oriented Paradigm (OOP)** ဆိုတာ Software ကို **Objects** တွေကို အခြေခံပြီး Design နဲ့ Develop လုပ်တဲ့ Programming Approach ဖြစ်ပါတယ်။

မြန်မာလို—

> **Object-Oriented Paradigm ဆိုတာ Program ကို Object တွေကို အခြေခံပြီး တည်ဆောက်တဲ့ Programming နည်းလမ်းတစ်ခု ဖြစ်ပါတယ်။**

---

# 2. What is an Object?

Object ဆိုတာ **Real-world Entity (တကယ့်ဘဝက အရာဝတ္ထု)** ကို ကိုယ်စားပြုတဲ့ အရာတစ်ခု ဖြစ်ပါတယ်။

ဥပမာ—

- 🚗 Car
- 👨 Person
- 🏦 Bank Account
- 📱 Mobile Phone
- 🐶 Dog

Object တစ်ခုမှာ အမြဲတမ်း

- **State (Data/Properties)**
- **Behavior (Methods/Actions)**

ဆိုတဲ့ အချက် ၂ ခု ရှိပါတယ်။

---

### Example: Car

**State (Properties)**

- Color
- Brand
- Speed

**Behavior (Methods)**

- Start()
- Stop()
- Accelerate()

Java Class:

```java
class Car {

    String color;
    String brand;
    int speed;

    void start() {
        System.out.println("Car Started");
    }

    void stop() {
        System.out.println("Car Stopped");
    }
}
```

Object:

```
Car car1 = new Car();
```

---

# 3. What is a Class?

**Class** ဆိုတာ Object တွေဖန်တီးဖို့ **Blueprint (ပုံစံ)** ဖြစ်ပါတယ်။

ဥပမာ—

အိမ်ဆောက်ဖို့ Blueprint လိုသလို

Object ဖန်တီးဖို့ Class လိုပါတယ်။

```
Class
   ↓
Creates
   ↓
Object
```

Example

```java
class Student {

    String name;
    int age;

}
```

Object

```
Student s1 = new Student();
Student s2 = new Student();
```

---

# 4. Why OOP?

OOP မတိုင်ခင် Procedural Programming မှာ—

- Code ကြီးလာရင် ရှုပ်ထွေးလာတယ်။
- Reuse လုပ်ရခက်တယ်။
- Maintain လုပ်ရခက်တယ်။

OOP က—

✅ Code Organization ကောင်းတယ်။

✅ Reusability ရတယ်။

✅ Security ပိုကောင်းတယ်။

✅ Maintain လုပ်ရလွယ်တယ်။

---

# 5. Four Main Pillars of OOP

Java OOP ရဲ့ အခြေခံ Concept (၄) ခု

## 1. Encapsulation

**Data နဲ့ Methods ကို Class တစ်ခုထဲမှာ စုစည်းထားခြင်း။**

Example

```java
class BankAccount {

    private double balance;

    public void deposit(double amount) {
        balance += amount;
    }
}
```

`balance` ကို `private` လုပ်ထားတာက Data ကို ကာကွယ်ထားတာ ဖြစ်ပါတယ်။

---

## 2. Inheritance

**Parent Class ရဲ့ Properties နဲ့ Methods တွေကို Child Class က ပြန်လည်အသုံးပြုခြင်း။**

Example

```java
class Animal {

    void eat() {
        System.out.println("Eating");
    }

}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }

}
```

`Dog` က `eat()` ကို ပြန်သုံးနိုင်ပါတယ်။

---

## 3. Polymorphism

**တူညီတဲ့ Method Name ကို အခြေအနေအလိုက် အမျိုးမျိုး အလုပ်လုပ်စေခြင်း။**

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

တူညီတဲ့ `sound()` Method ဖြစ်ပေမယ့် အလုပ်လုပ်ပုံ ကွာပါတယ်။

---

## 4. Abstraction

**မလိုအပ်တဲ့ အသေးစိတ်အချက်တွေကို ဖုံးကွယ်ပြီး လိုအပ်တဲ့ Function တွေကိုပဲ ပြသခြင်း။**

Example

```java
abstract class Shape {

    abstract void draw();

}
```

User က `draw()` ကိုပဲ အသုံးပြုနိုင်ပြီး အတွင်းပိုင်း Implementation ကို မသိလည်း ရပါတယ်။

---

# 6. Real-World Example

### Banking System

```
Customer
    |
    | owns
    ↓
BankAccount
    |
    ├── deposit()
    ├── withdraw()
    └── checkBalance()
```

- **Encapsulation** → Balance ကို private လုပ်ထားတယ်။
- **Inheritance** → SavingsAccount, CurrentAccount က BankAccount ကို extends လုပ်တယ်။
- **Polymorphism** → `calculateInterest()` ကို Account အမျိုးအစားအလိုက် Override လုပ်တယ်။
- **Abstraction** → User က deposit(), withdraw() ကိုပဲ အသုံးပြုတယ်။

---

# 7. Advantages of OOP

|Advantage|Explanation|
|---|---|
|Code Reusability|Inheritance ကြောင့် Code ပြန်သုံးနိုင်တယ်။|
|Easy Maintenance|Code ကို ပြင်ဆင်ထိန်းသိမ်းရ လွယ်တယ်။|
|Security|Encapsulation ကြောင့် Data ကို ကာကွယ်နိုင်တယ်။|
|Modularity|Class အလိုက် ခွဲရေးနိုင်တယ်။|
|Flexibility|Polymorphism ကြောင့် Code ကို လွယ်ကူစွာ ချဲ့ထွင်နိုင်တယ်။|

---

# 8. OOP vs Procedural Programming

|Procedural Programming|Object-Oriented Programming|
|---|---|
|Functions အခြေခံ|Objects အခြေခံ|
|Data နဲ့ Function သီးခြား|Data နဲ့ Method ကို Class ထဲမှာ စုထား|
|Reusability နည်း|Reusability ကောင်း|
|Security နည်း|Encapsulation ကြောင့် Security ပိုကောင်း|

---

# 9. Interview Answer (1 Minute)

> **"Object-Oriented Paradigm, or Object-Oriented Programming (OOP), is a programming approach that organizes software around objects rather than functions. An object contains both data (state) and methods (behavior). Java follows the OOP paradigm and is based on four main principles: Encapsulation, Inheritance, Polymorphism, and Abstraction. OOP improves code reusability, maintainability, security, and scalability, making it suitable for building large and complex applications."**

---

# 10. Common Follow-up Interview Questions

1. What is the difference between a Class and an Object?
2. What are the four pillars of OOP?
3. Why is Java called an Object-Oriented language?
4. Can Java be considered a 100% Object-Oriented language?
5. What are the advantages of OOP over Procedural Programming?
6. What is Encapsulation?
7. What is Inheritance?
8. What is Polymorphism?
9. What is Abstraction?

---

# Interview Key Points ⭐

```
Object-Oriented Programming (OOP)

        Object
           │
   ┌───────┴────────┐
   │                │
State            Behavior
(Data)          (Methods)

          ↓

Four Pillars

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction
```

## Final Answer

> **Object-Oriented Paradigm (OOP)** is a programming approach that models software using **objects**, where each object contains **data (state)** and **methods (behavior)**. Java follows the OOP paradigm to build software that is **modular, reusable, secure, maintainable, and scalable**. The four fundamental principles of OOP are **Encapsulation, Inheritance, Polymorphism, and Abstraction**.