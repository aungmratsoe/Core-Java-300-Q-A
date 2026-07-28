# What is the purpose of a Default Constructor?

## Interview Answer (Short Answer)

**Default Constructor** ရဲ့ အဓိကရည်ရွယ်ချက်က **Object တစ်ခုကို စတင် Initialize လုပ်ပေးဖို့** ဖြစ်ပါတယ်။

Class ထဲမှာ Constructor မရေးထားဘူးဆိုရင် Java Compiler က **No-Argument Constructor** တစ်ခုကို အလိုအလျောက် ဖန်တီးပေးပြီး Object ကို အဆင်ပြေစွာ Create လုပ်နိုင်အောင် ဆောင်ရွက်ပေးပါတယ်။

---

# Default Constructor ဆိုတာ ဘာလဲ?

Default Constructor ဆိုတာ **Parameter မပါတဲ့ Constructor** ဖြစ်ပါတယ်။

```java
class Student {

    Student() {
        System.out.println("Student Object Created");
    }

}
```

Object ဖန်တီးလိုက်တဲ့အချိန်

```java
Student s = new Student();
```

Output

```text
Student Object Created
```

Constructor က အလိုအလျောက် Run သွားပါတယ်။

---

# Default Constructor ရဲ့ Purpose (ရည်ရွယ်ချက်)

## 1. Object Initialization

Object အသစ်တစ်ခု ဖန်တီးတဲ့အချိန်မှာ Instance Variables တွေကို Initial Value သတ်မှတ်ပေးဖို့ အသုံးပြုပါတယ်။

ဥပမာ

```java
class Student {

    String name;
    int age;

    Student() {
        name = "Unknown";
        age = 18;
    }

    void display() {
        System.out.println(name);
        System.out.println(age);
    }

}
```

Main

```java
Student s = new Student();
s.display();
```

Output

```text
Unknown
18
```

ဒီမှာ Object စဖန်တီးလိုက်တာနဲ့ Default Values တွေ သတ်မှတ်ပြီးသား ဖြစ်ပါတယ်။

---

## 2. Compiler Automatically Creates It

Class ထဲမှာ Constructor တစ်ခုမှ မရေးထားရင် Java Compiler က Empty Constructor ကို အလိုအလျောက် ထည့်ပေးပါတယ်။

ဥပမာ

```java
class Student{

}
```

Compiler က နောက်ကွယ်မှာ

```java
Student(){

}
```

ဆိုပြီး Generate လုပ်ပေးပါတယ်။

ဒါကြောင့်

```java
Student s = new Student();
```

ဆိုတာ Error မဖြစ်ပါဘူး။

---

## 3. Default Values ပေးနိုင်တယ်

Object အသစ်တိုင်းမှာ တူညီတဲ့ Default Data တွေ သတ်မှတ်ချင်ရင် Default Constructor ကို အသုံးပြုပါတယ်။

ဥပမာ

```java
class Employee {

    String department;

    Employee() {
        department = "IT";
    }

}
```

Employee အသစ်တိုင်းရဲ့ Department က `"IT"` ဖြစ်နေပါမယ်။

---

## 4. Required Setup လုပ်နိုင်တယ်

Object ဖန်တီးချိန်မှာ လိုအပ်တဲ့ Setup တွေကိုလည်း Default Constructor ထဲမှာ ပြုလုပ်နိုင်ပါတယ်။

ဥပမာ

- Configuration Load လုပ်ခြင်း
    
- Log Message ထုတ်ခြင်း
    
- Resource Initialize လုပ်ခြင်း
    

```java
class Logger {

    Logger() {
        System.out.println("Logger Initialized");
    }

}
```

---

## 5. Object Creation ကို လွယ်ကူစေတယ်

Parameter မလိုတဲ့အတွက်

```java
Student s = new Student();
```

ဆိုပြီး လွယ်လွယ်ကူကူ Object Create လုပ်နိုင်ပါတယ်။

---

# Java ရဲ့ Default Values

Default Constructor မရေးထားဘဲ Variable တွေကို Initialize မလုပ်ထားရင် Java က Data Type အလိုက် Default Value တွေ သတ်မှတ်ပေးပါတယ်။

|Data Type|Default Value|
|---|---|
|int|0|
|double|0.0|
|boolean|false|
|char|'\u0000'|
|Object|null|

ဥပမာ

```java
class Test {

    int age;
    boolean active;
    String name;

    Test() {

    }

    void display() {

        System.out.println(age);
        System.out.println(active);
        System.out.println(name);

    }

}
```

Output

```text
0
false
null
```

---

# Compiler-generated Default Constructor

**Case 1 - Constructor မရေးထားဘူး**

```java
class Student{

}
```

Compiler က

```java
Student(){

}
```

ကို Auto Generate လုပ်ပေးပါတယ်။

---

**Case 2 - Parameterized Constructor ရေးထားတယ်**

```java
class Student{

    Student(String name){

    }

}
```

အခု

```java
Student s = new Student();
```

ဆိုရင်

```text
Compile Error
```

ဖြစ်ပါတယ်။

**ဘာကြောင့်လဲ?**

ကိုယ်တိုင် Constructor ရေးလိုက်တာနဲ့ Compiler က Default Constructor ကို မထည့်ပေးတော့လို့ ဖြစ်ပါတယ်။

---

# Real-world Example

**Mobile Phone** တစ်လုံးကို စဉ်းစားကြည့်ပါ။

အသစ်ဖွင့်လိုက်တာနဲ့

- Language = English
    
- Brightness = 50%
    
- Wi-Fi = Off
    

စတဲ့ Default Settings တွေ ရှိပြီးသား ဖြစ်ပါတယ်။

Java မှာလည်း Object အသစ်တစ်ခု ဖန်တီးတဲ့အချိန် Default Constructor က အလားတူ Initial Settings တွေ သတ်မှတ်ပေးနိုင်ပါတယ်။

---

# Interview Tips

Interview မှာ ဒီလိုအတိုချုပ် ဖြေနိုင်ပါတယ်။

> **"The purpose of a default constructor is to initialize an object when it is created. If no constructor is explicitly defined in a class, the Java compiler automatically provides a default no-argument constructor, allowing objects to be created with default initialization."**

---

# Interview Follow-up Questions

ဒီမေးခွန်းနောက်မှာ Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းတွေကတော့ -

1. Default Constructor နဲ့ Parameterized Constructor ဘာကွာလဲ?
    
2. Java Compiler က Default Constructor ကို ဘယ်အချိန် Generate လုပ်ပေးသလဲ?
    
3. Constructor မရှိရင် Object Create လုပ်လို့ရသလား?
    
4. Default Constructor ကို Override လုပ်လို့ရသလား?
    
5. Constructor Overloading ဆိုတာ ဘာလဲ?
    
6. `this()` နဲ့ `super()` ကို Constructor ထဲမှာ ဘယ်လို အသုံးပြုသလဲ?
    

> **Interview မှာ သတိထားရမယ့်အချက်**  
> "Default Constructor" ဆိုတဲ့ အသုံးအနှုန်းကို တချို့ Interviewer တွေက **Compiler-generated constructor** ကို ရည်ညွှန်းပြီး မေးနိုင်သလို၊ တချို့က **No-Argument Constructor** ကို ရည်ညွှန်းပြီး မေးနိုင်ပါတယ်။ အဲဒါကြောင့် "**A default (no-argument) constructor...**" လို့ စတင်ဖြေပြီး၊ **"If no constructor is defined, the compiler automatically generates one."** လို့ ဆက်ရှင်းပြပေးရင် ပိုပြည့်စုံတဲ့အဖြေ ဖြစ်ပါတယ်။