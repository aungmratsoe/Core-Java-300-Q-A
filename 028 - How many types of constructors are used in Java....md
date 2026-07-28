# Java မှာ Constructor အမျိုးအစား ဘယ်နှစ်မျိုးရှိသလဲ?

**Interview Answer (Short Answer):**

Java မှာ Constructor ကို **အဓိကအားဖြင့် ၂ မျိုး** ခွဲခြားနိုင်ပါတယ်။

1. **Default Constructor (No-Argument Constructor)**
    
2. **Parameterized Constructor**
    

> **မှတ်ချက်**: တချို့စာအုပ်တွေမှာ **User-defined Constructor** နဲ့ **Compiler-generated Default Constructor** ကို ခွဲပြီး ရှင်းပြတတ်ပါတယ်။ ဒါပေမယ့် Interview မှာတော့ အများအားဖြင့် **Default Constructor** နဲ့ **Parameterized Constructor** ဆိုပြီး ၂ မျိုးဖြေလိုက်ရင် လုံလောက်ပါတယ်။

---

# 1. Default Constructor (No-Argument Constructor)

Parameter မပါတဲ့ Constructor ကို Default Constructor (သို့) No-Argument Constructor လို့ခေါ်ပါတယ်။

ဥပမာ

```java
class Student {

    Student() {
        System.out.println("Default Constructor Called");
    }

}
```

Main Method

```java
public class Main {

    public static void main(String[] args) {

        Student s = new Student();

    }

}
```

Output

```
Default Constructor Called
```

### အသုံးဝင်ပုံ

Object တစ်ခု စဖန်တီးတဲ့အချိန်မှာ

- Default Values ထည့်ပေးချင်တယ်။
    
- Initialization လုပ်ချင်တယ်။
    

ဆိုရင် အသုံးပြုပါတယ်။

---

## Compiler-generated Default Constructor

Class ထဲမှာ Constructor **လုံးဝမရေးထားဘူး** ဆိုရင် Java Compiler က Empty Constructor တစ်ခုကို အလိုအလျောက် ထည့်ပေးပါတယ်။

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

ဆိုပြီး Auto Generate လုပ်ပေးပါတယ်။

ဒါကြောင့်

```java
Student s = new Student();
```

ဆိုတာ Error မဖြစ်ပါဘူး။

> **သတိထားရန်**: ကိုယ်တိုင် Constructor တစ်ခုရေးလိုက်တာနဲ့ Compiler က Default Constructor ကို Auto Generate မလုပ်တော့ပါဘူး။

ဥပမာ

```java
class Student {

    Student(String name){

    }

}
```

အခု

```java
Student s = new Student();
```

ဆိုရင် **Compile Error** ဖြစ်ပါမယ်။ ဘာကြောင့်လဲဆိုတော့ No-Argument Constructor မရှိတော့လို့ပါ။

---

# 2. Parameterized Constructor

Parameter ပါတဲ့ Constructor ကို Parameterized Constructor လို့ခေါ်ပါတယ်။

ဥပမာ

```java
class Student {

    String name;
    int age;

    Student(String name, int age) {

        this.name = name;
        this.age = age;

    }

    void display(){

        System.out.println(name);
        System.out.println(age);

    }

}
```

Main Method

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

### အသုံးဝင်ပုံ

Object ဖန်တီးတဲ့အချိန်မှာ User ပေးတဲ့ Data ကို တစ်ခါတည်း Initialize လုပ်ပေးနိုင်ပါတယ်။

---

# Constructor Types အကျဉ်းချုပ်

|Constructor Type|Parameter|အသုံးပြုပုံ|
|---|---|---|
|Default (No-Argument)|❌ မပါ|Default Initialization|
|Parameterized|✅ ပါ|User ပေးတဲ့ Data ဖြင့် Initialization|

---

# Real-world Example

**Bank Account System** ကို စဉ်းစားကြည့်ပါ။

### Default Constructor

```java
BankAccount account = new BankAccount();
```

Account အသစ်ဖွင့်ပြီး

- Balance = 0
    
- Status = Active
    

စတဲ့ Default Values တွေ သတ်မှတ်ပေးနိုင်ပါတယ်။

---

### Parameterized Constructor

```java
BankAccount account = new BankAccount("John", 1000);
```

Account Owner = John

Opening Balance = 1000

ဆိုပြီး တစ်ခါတည်း သတ်မှတ်နိုင်ပါတယ်။

---

# Constructor Overloading

Java မှာ Constructor အမျိုးအစား ၂ မျိုးပဲ ရှိပေမယ့် **Constructor Overloading** ကြောင့် Constructor အများကြီး ရေးနိုင်ပါတယ်။

```java
class Student {

    Student(){

    }

    Student(String name){

    }

    Student(String name,int age){

    }

}
```

ဒီမှာ Constructor သုံးခုရှိပေမယ့် Type ကတော့

- Default Constructor
    
- Parameterized Constructor
    

ဆိုတဲ့ အမျိုးအစား ၂ မျိုးပဲ ဖြစ်ပါတယ်။

---

# Interview Tips

Interview မှာ ဒီလိုအတိုချုပ် ဖြေလို့ရပါတယ်။

> **"Java has two main types of constructors: Default (or No-Argument) Constructor and Parameterized Constructor. If no constructor is defined, the Java compiler automatically provides a default constructor. Parameterized constructors are used to initialize objects with specific values at the time of object creation."**

---

# Interview Follow-up Questions

ဒီမေးခွန်းနောက်မှာ Interviewer က ဆက်မေးနိုင်တာတွေကတော့ -

1. Default Constructor ကို Compiler က ဘယ်အချိန် Auto Generate လုပ်ပေးသလဲ?
    
2. Constructor Overloading ဆိုတာ ဘာလဲ?
    
3. Constructor နဲ့ Method ဘာကွာလဲ?
    
4. `this()` နဲ့ `super()` ကို Constructor ထဲမှာ ဘယ်လိုသုံးလဲ?
    
5. Constructor ကို `private` လုပ်လို့ရလား? ဘာအတွက် အသုံးပြုသလဲ?
    
6. Constructor ကို `static` သို့မဟုတ် `final` လုပ်လို့ရလား? ဘာကြောင့် မရတာလဲ?
    

ဒီလို Follow-up Questions တွေအတွက်လည်း ပြင်ဆင်ထားရင် Java Interview မှာ အခက်အခဲမရှိ ဖြေနိုင်ပါလိမ့်မယ်။