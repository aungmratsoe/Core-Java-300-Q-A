# What do you understand by Copy Constructor in Java?

## Interview Answer (Short Answer)

**Java မှာ C++ လို Built-in Copy Constructor မရှိပါဘူး။**

Java မှာ **Copy Constructor** ဆိုတာ **တူညီတဲ့ Class ရဲ့ Object တစ်ခုကို Parameter အဖြစ်လက်ခံပြီး Object အသစ်တစ်ခုကို မူရင်း Object ရဲ့ Data တွေနဲ့ Copy လုပ်ပေးတဲ့ User-defined Constructor** ကို ဆိုလိုပါတယ်။

---

# Copy Constructor ဆိုတာ ဘာလဲ?

Copy Constructor ဆိုတာ

**Object တစ်ခုရဲ့ Data ကို နောက် Object အသစ်တစ်ခုထဲကို Copy လုပ်ပေးတဲ့ Constructor** ဖြစ်ပါတယ်။

Java က အလိုအလျောက် Copy Constructor မပေးပါဘူး။

Programmer ကိုယ်တိုင် ရေးရပါတယ်။

---

# Syntax

```java
ClassName(ClassName obj) {

}
```

ဥပမာ

```java
Student(Student s) {

}
```

ဒီ Constructor က

Student Object တစ်ခုကို လက်ခံပြီး

Student အသစ်တစ်ခုကို Copy လုပ်ပေးတာ ဖြစ်ပါတယ်။

---

# Example

```java
class Student {

    String name;
    int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Copy Constructor
    Student(Student s) {
        this.name = s.name;
        this.age = s.age;
    }

    void display() {
        System.out.println(name + " " + age);
    }

}
```

Main

```java
public class Main {

    public static void main(String[] args) {

        Student s1 = new Student("Aung Aung",20);

        Student s2 = new Student(s1);

        s2.display();

    }

}
```

Output

```text
Aung Aung 20
```

ဒီမှာ

```java
Student s2 = new Student(s1);
```

ဆိုတာ Copy Constructor ကို ခေါ်လိုက်တာ ဖြစ်ပါတယ်။

---

# Copy Constructor ဘယ်လိုအလုပ်လုပ်သလဲ?

ပထမ Object

```java
Student s1 = new Student("Aung Aung",20);
```

Memory

```text
s1
 ├── name = "Aung Aung"
 └── age = 20
```

Copy Constructor

```java
Student s2 = new Student(s1);
```

Memory

```text
s1                    s2
 ├─ name=Aung Aung     ├─ name=Aung Aung
 └─ age=20             └─ age=20
```

Object နှစ်ခုက **မတူတဲ့ Object** ဖြစ်ပေမယ့် Data တူပါတယ်။

---

# Java မှာ Copy Constructor Built-in ရှိလား?

**မရှိပါဘူး။**

C++ မှာ

```cpp
Student s2 = s1;
```

ဆိုရင် Compiler က Copy Constructor ကို အလိုအလျောက် ခေါ်ပေးပါတယ်။

ဒါပေမယ့် Java မှာတော့

Programmer က

```java
Student(Student s)
```

ကို ကိုယ်တိုင်ရေးရပါတယ်။

---

# Copy Constructor နဲ့ Assignment (`=`) ကွာခြားချက်

### Assignment

```java
Student s1 = new Student("Aung",20);

Student s2 = s1;
```

Memory

```text
s1 ───────┐
          ▼
      Student Object
```

ဒီမှာ

**Object အသစ် မဖန်တီးပါဘူး။**

`s1` နဲ့ `s2` က Object တစ်ခုတည်းကို Reference လုပ်ထားတာ ဖြစ်ပါတယ်။

ဥပမာ

```java
s2.name = "Kyaw";
```

Output

```text
s1.name = Kyaw
```

Original Object ပါ ပြောင်းသွားပါတယ်။

---

### Copy Constructor

```java
Student s2 = new Student(s1);
```

Memory

```text
s1 -----------> Object 1

s2 -----------> Object 2
```

Object အသစ် ဖန်တီးပြီး Data ကို Copy လုပ်တာ ဖြစ်ပါတယ်။

ဒါကြောင့်

```java
s2.name = "Kyaw";
```

ဆိုရင်

```text
s1.name = Aung
```

မပြောင်းပါဘူး။

---

# Copy Constructor vs `clone()`

Java မှာ Object Copy လုပ်တဲ့ နည်းလမ်းနှစ်ခု ရှိပါတယ်။

|Copy Constructor|`clone()` Method|
|---|---|
|User-defined|`Object` Class က ပေးထားသည်|
|ရေးရလွယ်|အသုံးပြုရ ပိုရှုပ်ထွေး (`Cloneable` Interface လိုအပ်)|
|လိုချင်တဲ့ Fields ကို ရွေးပြီး Copy လုပ်နိုင်|Default အားဖြင့် Field များကို Copy လုပ်ပေးသည်|
|Interview မှာ ပိုအသုံးများ|အသုံးနည်းလာပြီး အကြံပြုမှုလည်း နည်းလာ|

---

# Shallow Copy vs Deep Copy

Copy Constructor နဲ့

**Shallow Copy** လည်း လုပ်နိုင်သလို

**Deep Copy** လည်း လုပ်နိုင်ပါတယ်။

### Shallow Copy

Reference Object ကိုပဲ Copy လုပ်တာ။

```java
this.address = s.address;
```

Object နှစ်ခုလုံးက Address Object တစ်ခုတည်းကို Share လုပ်ပါတယ်။

---

### Deep Copy

Object အသစ် ထပ်ဆောက်ပြီး Copy လုပ်တာ။

```java
this.address = new Address(s.address);
```

Object နှစ်ခုက သီးခြား ဖြစ်သွားပါတယ်။

---

# Real-world Example

ဥပမာ Employee Record တစ်ခုရှိတယ်။

```text
Name = Aung Aung

Age = 30
```

ဒီ Employee ကို အခြေခံပြီး အသစ်တစ်ခု ဖန်တီးချင်တယ်။

```text
Name = Aung Aung

Age = 30
```

ဒါပေမယ့် Object အသစ် ဖြစ်ရမယ်။

အဲဒီလိုအခါ Copy Constructor ကို သုံးပါတယ်။

---

# Interview မှာ အတိုချုပ် ဘယ်လိုဖြေရမလဲ?

> **"Java does not provide a built-in copy constructor like C++. A copy constructor is a user-defined constructor that accepts an object of the same class and creates a new object by copying its fields. It is commonly used to create independent copies of objects."**

---

# Interview Follow-up Questions

ဒီမေးခွန်းနောက်မှာ Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းတွေကတော့ -

1. Java မှာ Copy Constructor Built-in ရှိလား?
    
2. Copy Constructor နဲ့ `clone()` ဘာကွာလဲ?
    
3. Assignment (`=`) နဲ့ Copy Constructor ဘာကွာလဲ?
    
4. Shallow Copy နဲ့ Deep Copy ဘာကွာလဲ?
    
5. `Cloneable` Interface ဆိုတာ ဘာလဲ?
    
6. Mutable Object တွေကို Copy လုပ်တဲ့အခါ ဘာတွေ သတိထားရမလဲ?
    

---

# Interview Tip ⭐

ဒီမေးခွန်းမှာ Interviewer တွေ စမ်းချင်တာက **Java နဲ့ C++ ကွာခြားချက်** ကို သိမသိ ဖြစ်ပါတယ်။

အကောင်းဆုံးအဖြေကတော့—

> **"Unlike C++, Java does not have a built-in copy constructor. We can implement our own copy constructor by creating a constructor that accepts an object of the same class and copies its fields."**

ဒီလိုဖြေလိုက်ရင် Java Language Features ကို နားလည်ထားကြောင်း ကောင်းကောင်းပြသနိုင်ပါတယ်။