# What are the differences between Constructors and Methods?

## Interview Answer (Short Answer)

**Constructor** နဲ့ **Method** တို့က Java မှာ Member တွေဖြစ်ပေမယ့် **ရည်ရွယ်ချက် (Purpose)** နဲ့ **အလုပ်လုပ်ပုံ (Behavior)** က မတူပါဘူး။

- **Constructor** ကို **Object အသစ်တစ်ခု Create လုပ်တဲ့အချိန်မှာ Initialize လုပ်ဖို့** အသုံးပြုပါတယ်။
    
- **Method** ကို **Object ရဲ့ လုပ်ဆောင်ချက် (Behavior/Functionality)** တွေကို ဆောင်ရွက်ဖို့ အသုံးပြုပါတယ်။
    

---

# Constructor vs Method (Comparison Table)

|Constructor|Method|
|---|---|
|Object ကို Initialize လုပ်ဖို့ သုံးသည်|Object ရဲ့ Functionality ကို လုပ်ဆောင်ဖို့ သုံးသည်|
|Class Name နဲ့ အမည်တူရသည်|မည်သည့်အမည်မဆို ပေးနိုင်သည်|
|Return Type မရှိ (Not even `void`)|Return Type ရှိနိုင်သည် (`void`, `int`, `String`...)|
|Object Create လုပ်ချိန်မှာ အလိုအလျောက် ခေါ်သည်|Programmer က Explicitly Call လုပ်မှ Run သည်|
|Constructor ကို Override မလုပ်နိုင်|Method ကို Override လုပ်နိုင်သည်|
|Constructor ကို Inherit မလုပ်နိုင်|Method ကို Inherit လုပ်နိုင်သည်|
|Constructor ကို Overload လုပ်နိုင်သည်|Method ကို Overload လုပ်နိုင်သည်|
|`super()`၊ `this()` ဖြင့် Constructor Chaining လုပ်နိုင်သည်|Method Call ဖြင့် အခြား Method များကို ခေါ်နိုင်သည်|
|`final`, `static`, `abstract` မဖြစ်နိုင်|`final`, `static`, `abstract` စသည်ဖြင့် သတ်မှတ်နိုင်သည်|

---

# 1. Purpose (ရည်ရွယ်ချက်)

## Constructor

Object ကို စတင်ဖန်တီးပြီး Initial Values သတ်မှတ်ပေးဖို့ အသုံးပြုပါတယ်။

```java
class Student {

    String name;

    Student() {
        name = "Unknown";
    }

}
```

ဒီမှာ Object အသစ်ဖန်တီးတိုင်း `name` ကို `"Unknown"` လို့ သတ်မှတ်ပေးပါတယ်။

---

## Method

Object ရဲ့ အလုပ် (Behavior) ကို လုပ်ဆောင်ဖို့ အသုံးပြုပါတယ်။

```java
class Student {

    void study() {
        System.out.println("Student is studying");
    }

}
```

ဒီ Method က Student ရဲ့ Behavior ကို ကိုယ်စားပြုပါတယ်။

---

# 2. Name

## Constructor

Class Name နဲ့ တူရပါတယ်။

```java
class Student {

    Student() {

    }

}
```

---

## Method

နာမည်ကို လွတ်လပ်စွာ ပေးနိုင်ပါတယ်။

```java
void display() {

}

void calculate() {

}
```

---

# 3. Return Type

## Constructor

Return Type မရှိပါဘူး။

```java
Student() {

}
```

---

## Method

Return Type ရှိနိုင်ပါတယ်။

```java
int getAge() {
    return 20;
}
```

ဒါမှမဟုတ်

```java
void display() {

}
```

---

# 4. Calling

## Constructor

Object Create လုပ်တဲ့အချိန်မှာ Automatically Call ဖြစ်ပါတယ်။

```java
Student s = new Student();
```

---

## Method

Method ကို ကိုယ်တိုင် Call လုပ်ရပါတယ်။

```java
s.display();
```

---

# 5. Inheritance

## Constructor

Constructor ကို Inherit မလုပ်နိုင်ပါဘူး။

```java
class Animal {

    Animal() {

    }

}
```

Child Class က ဒီ Constructor ကို အမွေဆက်ခံလို့ မရပါဘူး။

---

## Method

Method ကို Inherit လုပ်နိုင်ပါတယ်။

```java
class Animal {

    void eat() {
        System.out.println("Eating");
    }

}

class Dog extends Animal {

}
```

```java
Dog d = new Dog();

d.eat();
```

Output

```text
Eating
```

---

# 6. Overriding

## Constructor

Override မလုပ်နိုင်ပါဘူး။

---

## Method

Override လုပ်နိုင်ပါတယ်။

```java
class Animal {

    void sound() {
        System.out.println("Animal");
    }

}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog");
    }

}
```

Output

```text
Dog
```

---

# 7. Overloading

Constructor လည်း Overload လုပ်နိုင်သလို Method လည်း Overload လုပ်နိုင်ပါတယ်။

## Constructor Overloading

```java
Student() {

}

Student(String name) {

}
```

---

## Method Overloading

```java
void display() {

}

void display(String name) {

}
```

---

# 8. Memory Allocation

```java
Student s = new Student();
```

ဒီ Process မှာ

1. `new` keyword က Memory Allocate လုပ်တယ်။
    
2. Constructor က Object ကို Initialize လုပ်တယ်။
    
3. Reference ကို Variable `s` ထဲမှာ သိမ်းတယ်။
    

Method ကတော့ Memory Allocate မလုပ်ပါဘူး။

---

# Real-world Example

**Car** ကို ဥပမာယူကြည့်ပါ။

### Constructor

ကားအသစ် စက်ရုံက ထွက်လာတဲ့အချိန်

- Engine တပ်ပြီး
    
- Color သတ်မှတ်ပြီး
    
- Fuel ထည့်ပေးထားတယ်။
    

ဒါဟာ **Constructor** နဲ့တူပါတယ်။

```java
Car car = new Car();
```

---

### Method

ကားဝယ်ပြီးနောက်

- Start
    
- Stop
    
- Brake
    
- Accelerate
    

လုပ်တာက **Method** ဖြစ်ပါတယ်။

```java
car.start();

car.stop();
```

---

# Complete Example

```java
class Car {

    String model;

    // Constructor
    Car(String model) {
        this.model = model;
    }

    // Method
    void display() {
        System.out.println("Model: " + model);
    }

    public static void main(String[] args) {

        Car car = new Car("Toyota");

        car.display();

    }

}
```

Output

```text
Model: Toyota
```

ဒီမှာ

- `Car(String model)` → Constructor
    
- `display()` → Method
    

ဖြစ်ပါတယ်။

---

# Interview မှာ အတိုချုပ် ဘယ်လိုဖြေရမလဲ?

> **"A constructor is a special member of a class used to initialize objects. It has the same name as the class, has no return type, and is called automatically when an object is created. A method, on the other hand, defines the behavior of an object, can have any valid name, has a return type (or `void`), and must be called explicitly."**

---

# Interview Follow-up Questions

ဒီမေးခွန်းနောက်မှာ Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းတွေကတော့ -

1. Constructor ကို Override လုပ်လို့ ဘာကြောင့် မရတာလဲ?
    
2. Constructor ကို Inherit လုပ်လို့ရလား?
    
3. Constructor နဲ့ Static Method ဘာကွာလဲ?
    
4. Constructor မှာ `return` ရေးလို့ရလား?
    
5. Constructor Overloading ဆိုတာ ဘာလဲ?
    
6. `this()` နဲ့ `super()` ကို Constructor ထဲမှာ ဘယ်လိုအသုံးပြုသလဲ?
    

---

# Interview Tip ⭐

Java Interview တွေမှာ မကြာခဏ မေးတတ်တဲ့ မေးခွန်းတစ်ခုကတော့—

> **"Can a constructor call a method?"**

**အဖြေ**

**Yes.** Constructor ထဲကနေ Method ကို ခေါ်နိုင်ပါတယ်။

```java
class Student {

    Student() {
        display();   // Constructor က Method ကို ခေါ်နေသည်
    }

    void display() {
        System.out.println("Welcome");
    }

}
```

ဒါပေမယ့် **Method က Constructor ကို တိုက်ရိုက် မခေါ်နိုင်ပါဘူး**။ Constructor က Object ဖန်တီးချိန်မှာသာ အလိုအလျောက် Execute ဖြစ်တာဖြစ်လို့၊ Method ကနေ Constructor ကို သီးခြားခေါ်ဖို့ မဖြစ်နိုင်ပါဘူး။