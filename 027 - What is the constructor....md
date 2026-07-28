## Java Constructor ဆိုတာဘာလဲ?

**Constructor** ဆိုတာ **Object တစ်ခုကို စတင်ဖန်တီး (Initialize) လုပ်တဲ့အချိန်မှာ အလိုအလျောက်ခေါ်သွားတဲ့ Special Method** ဖြစ်ပါတယ်။

Object အသစ်တစ်ခု (`new` keyword နဲ့) ဖန်တီးလိုက်တဲ့အချိန်မှာ Constructor က အလုပ်လုပ်ပြီး Object ရဲ့ Instance Variables တွေကို Initial Value သတ်မှတ်ပေးခြင်း၊ လိုအပ်တဲ့ Setup တွေပြုလုပ်ပေးခြင်းကို လုပ်ဆောင်ပါတယ်။

---

# Constructor ရဲ့ အဓိကလက္ခဏာများ (Characteristics)

### 1. Constructor Name က Class Name နဲ့ တူရမယ်

ဥပမာ

```java
class Student {

    Student() {
        System.out.println("Constructor Called");
    }

}
```

Class Name က `Student` ဖြစ်ရင် Constructor Name လည်း `Student` ဖြစ်ရပါမယ်။

---

### 2. Return Type မရှိဘူး

Constructor မှာ

- `void`
    
- `int`
    
- `String`
    

စတဲ့ Return Type တွေ မပါဘူး။

❌ မှား

```java
void Student() {

}
```

✔ မှန်

```java
Student() {

}
```

---

### 3. Object Create လုပ်တဲ့အချိန်မှာ Automatically Call ဖြစ်တယ်

```java
Student s = new Student();
```

ဒီလို Object ဆောက်လိုက်တာနဲ့

```
Student()
```

Constructor က အလိုအလျောက် Run သွားပါတယ်။

---

# Constructor ဘာကြောင့်သုံးတာလဲ?

Object တစ်ခုဖန်တီးတဲ့အချိန်မှာ

- Default Value ထည့်ချင်တယ်
    
- User ပေးတဲ့ Data ကို Initialize လုပ်ချင်တယ်
    
- Database Connection ဖွင့်ချင်တယ်
    
- File Open လုပ်ချင်တယ်
    

ဆိုရင် Constructor ကို အသုံးပြုပါတယ်။

ဥပမာ

Employee Object အသစ်တစ်ခုဖန်တီးတဲ့အချိန်မှာ

```
Name
Salary
Department
```

တွေကို Constructor ကနေ Initialize လုပ်ပေးနိုင်ပါတယ်။

---

# Constructor Types

Java မှာ Constructor နှစ်မျိုးရှိပါတယ်။

## 1. Default Constructor (No-Argument Constructor)

Parameter မပါတဲ့ Constructor ဖြစ်ပါတယ်။

```java
class Student {

    Student() {
        System.out.println("Student Created");
    }

}

public class Main {

    public static void main(String[] args) {

        Student s = new Student();

    }

}
```

Output

```
Student Created
```

---

## Java Compiler ပေးတဲ့ Default Constructor

Class ထဲမှာ Constructor လုံးဝမရေးထားရင်

Java Compiler က

```java
Student(){

}
```

ဆိုတဲ့ Empty Constructor ကို Auto ထည့်ပေးပါတယ်။

ဥပမာ

```java
class Student{

}
```

အောက်က Code က Error မဖြစ်ဘူး

```java
Student s = new Student();
```

ဘာကြောင့်လဲ?

Compiler က

```java
Student(){

}
```

ကို Auto Generate လုပ်ပေးထားလို့ပါ။

> **မှတ်ချက်**: ကိုယ်တိုင် Constructor တစ်ခုရေးလိုက်တာနဲ့ Compiler က Default Constructor ကို မထည့်ပေးတော့ပါဘူး။

---

# 2. Parameterized Constructor

Parameter ပါတဲ့ Constructor ဖြစ်ပါတယ်။

```java
class Student {

    String name;
    int age;

    Student(String n, int a) {
        name = n;
        age = a;
    }

    void display() {
        System.out.println(name);
        System.out.println(age);
    }
}
```

Main

```java
public class Main {

    public static void main(String[] args) {

        Student s = new Student("Aung Aung",20);

        s.display();

    }

}
```

Output

```
Aung Aung
20
```

ဒီမှာ Constructor က Data ကို Initialize လုပ်ပေးထားပါတယ်။

---

# Constructor Overloading

Method Overloading လိုပဲ

Constructor ကိုလည်း Multiple Constructor ရေးလို့ရပါတယ်။

```java
class Student {

    Student() {
        System.out.println("No Parameter");
    }

    Student(String name) {
        System.out.println(name);
    }

    Student(String name,int age) {
        System.out.println(name+" "+age);
    }

}
```

Main

```java
Student s1 = new Student();

Student s2 = new Student("Mg Mg");

Student s3 = new Student("Kyaw",22);
```

Output

```
No Parameter

Mg Mg

Kyaw 22
```

---

# `this()` Constructor Chaining

Constructor တစ်ခုကနေ အခြား Constructor တစ်ခုကို ခေါ်ချင်ရင် `this()` ကို သုံးပါတယ်။

```java
class Student {

    Student() {
        this("Unknown");
        System.out.println("Default");
    }

    Student(String name) {
        System.out.println(name);
    }

}
```

Output

```
Unknown
Default
```

**မှတ်ရန်**: `this()` ကို Constructor ထဲက **ပထမဆုံး Statement** အဖြစ်သာ ရေးနိုင်ပါတယ်။

---

# `super()` နှင့် Constructor

Child Class ရဲ့ Constructor က Parent Class ရဲ့ Constructor ကို `super()` နဲ့ ခေါ်နိုင်ပါတယ်။

```java
class Animal {

    Animal() {
        System.out.println("Animal Constructor");
    }

}

class Dog extends Animal {

    Dog() {
        super();
        System.out.println("Dog Constructor");
    }

}
```

Output

```
Animal Constructor

Dog Constructor
```

Java က `super()` မရေးထားရင်လည်း Parent ရဲ့ No-Argument Constructor ကို အလိုအလျောက် ခေါ်ပေးပါတယ် (ရှိခဲ့လျှင်)။

---

# Constructor နှင့် Method ကွာခြားချက်

|Constructor|Method|
|---|---|
|Object ဖန်တီးချိန်တွင် အလိုအလျောက် ခေါ်သည်|လိုအပ်မှ Call လုပ်ရသည်|
|Class Name နဲ့ အမည်တူရသည်|နာမည်လွတ်လပ်စွာ ပေးနိုင်သည်|
|Return Type မရှိ|Return Type ရှိနိုင်သည် (`void`, `int`, `String`...)|
|Object Initialization အတွက် သုံးသည်|အလုပ်အမျိုးမျိုး လုပ်ဆောင်ရန် သုံးသည်|
|Inheritance မရ|Method ကို Override/Overload လုပ်နိုင်သည်|

---

# Real-world Example

ကားတစ်စီး ဝယ်လိုက်တယ်ဆိုပါစို့။

ကားစက်ရုံက ထုတ်လိုက်ချိန်မှာ

- Engine
    
- Color
    
- Model
    
- Fuel Type
    

စတာတွေကို စတင်သတ်မှတ်ပေးထားပြီးသား ဖြစ်ပါတယ်။

ဒီ "စတင်သတ်မှတ်ပေးတဲ့ လုပ်ငန်းစဉ်" ကို Java မှာ Constructor နဲ့ နှိုင်းယှဉ်နိုင်ပါတယ်။

```java
class Car {

    String model;
    String color;

    Car(String model, String color) {
        this.model = model;
        this.color = color;
    }

    void display() {
        System.out.println("Model : " + model);
        System.out.println("Color : " + color);
    }

    public static void main(String[] args) {
        Car car = new Car("Toyota Corolla", "White");
        car.display();
    }
}
```

Output

```
Model : Toyota Corolla
Color : White
```

---

# Interview မှာ အတိုချုပ် ဘယ်လိုဖြေရမလဲ?

> **"Constructor is a special member of a class that is automatically invoked when an object is created. It has the same name as the class, does not have any return type, and is mainly used to initialize object state. Java supports default constructors, parameterized constructors, and constructor overloading."**

---

# Interview Follow-up Questions

အင်တာဗျူးမှာ ဆက်မေးနိုင်တဲ့ မေးခွန်းများ -

1. Constructor နဲ့ Method က ဘာကွာလဲ?
    
2. Java မှာ Constructor Overloading ဆိုတာ ဘာလဲ?
    
3. Default Constructor ကို Compiler က ဘယ်အချိန် Generate လုပ်ပေးလဲ?
    
4. `this()` နဲ့ `super()` က ဘာကွာလဲ?
    
5. Constructor ကို `private` လုပ်လို့ရလား? ဘာအတွက် သုံးတာလဲ?
    
6. Constructor ကို `static` သို့မဟုတ် `final` လုပ်လို့ရလား? ဘာကြောင့် မရတာလဲ?
    
7. Constructor Chaining ဆိုတာ ဘာလဲ?
    

ဒီမေးခွန်းတွေဟာ Java အင်တာဗျူးတွေမှာ Constructor အကြောင်းမေးပြီးနောက် ဆက်တိုက်မေးလေ့ရှိတဲ့ မေးခွန်းတွေဖြစ်ပါတယ်။