# What is a Static Variable?

## Interview Answer (Short Answer)

**Static Variable** ဆိုတာ **`static` keyword နဲ့ Declare လုပ်ထားတဲ့ Class Variable** ဖြစ်ပါတယ်။

Static Variable က **Object တစ်ခုချင်းစီအတွက် မဟုတ်ဘဲ Class တစ်ခုလုံးအတွက် တစ်ခုပဲ ရှိပါတယ်။** အဲဒါကြောင့် Object အားလုံးက **တူညီတဲ့ Static Variable ကို Share လုပ်ကြပါတယ်။**

---

# Static Variable ဆိုတာ ဘာလဲ?

Static Variable ကို **Class Variable** လို့လည်း ခေါ်ပါတယ်။

ဥပမာ

```java
class Student {

    String name;          // Instance Variable
    static String school; // Static Variable

}
```

ဒီမှာ

- `name` → Object တစ်ခုချင်းစီမှာ သီးသန့်ရှိတယ်။
    
- `school` → Student Class အတွက် **တစ်ခုတည်း** ရှိတယ်။
    

---

# Static Variable ဘယ်မှာ သိမ်းထားသလဲ?

- **Instance Variable** → Object နဲ့အတူ Memory ထဲမှာ သိမ်းတယ်။
    
- **Static Variable** → **Class Area (Method Area)** မှာ Class Load လုပ်တဲ့အချိန်ကတည်းက Create ဖြစ်ပါတယ်။
    

ဆိုလိုတာက

```java
Student s1 = new Student();
Student s2 = new Student();
Student s3 = new Student();
```

ဆိုရင်

Instance Variable က **၃ ခု** ရှိပေမယ့်

Static Variable က **၁ ခုတည်း** ရှိပါတယ်။

---

# Example 1

```java
class Student {

    String name;
    static String school = "ABC University";

    Student(String name) {
        this.name = name;
    }

    void display() {
        System.out.println(name + " - " + school);
    }

    public static void main(String[] args) {

        Student s1 = new Student("Aung");
        Student s2 = new Student("Kyaw");

        s1.display();
        s2.display();

    }
}
```

### Output

```text
Aung - ABC University
Kyaw - ABC University
```

**ရှင်းလင်းချက်**

Student နှစ်ယောက်လုံးက `school` Variable တစ်ခုတည်းကို Share လုပ်ထားတာ ဖြစ်ပါတယ်။

---

# Example 2 (Shared Variable)

```java
class Counter {

    static int count = 0;

    Counter() {
        count++;
    }

    public static void main(String[] args) {

        new Counter();
        new Counter();
        new Counter();

        System.out.println(count);

    }

}
```

### Output

```text
3
```

### ဘာကြောင့် 3 ထွက်တာလဲ?

Object အသစ် Create လုပ်တိုင်း

```java
count++;
```

လုပ်ပါတယ်။

ဒါပေမယ့် `count` က Static Variable ဖြစ်လို့ Object အားလုံးက Variable တစ်ခုတည်းကို အသုံးပြုပါတယ်။

Memory

```text
Counter Class
------------------
count = 3
------------------

Object1
Object2
Object3
```

---

# Static Variable ကို ဘယ်လို Access လုပ်မလဲ?

### ✔ Class Name နဲ့ Access လုပ်တာ (Recommended)

```java
Student.school = "XYZ University";
```

---

### ✔ Object နဲ့လည်း Access လုပ်လို့ရတယ်

```java
Student s = new Student("Aung");

s.school = "XYZ University";
```

ဒါပေမယ့် **Best Practice မဟုတ်ပါဘူး**။

Interview မှာ

> **Static Variable ကို Class Name နဲ့ Access လုပ်သင့်တယ်။**

လို့ ဖြေရပါတယ်။

---

# Static Variable vs Instance Variable

|Static Variable|Instance Variable|
|---|---|
|`static` keyword ပါသည်|`static` မပါ|
|Class အတွက် တစ်ခုပဲ ရှိသည်|Object တစ်ခုချင်းစီအတွက် သီးသန့်ရှိသည်|
|Class Load လုပ်ချိန်မှာ Create ဖြစ်သည်|Object Create လုပ်ချိန်မှာ Create ဖြစ်သည်|
|Memory သက်သာသည်|Object များလာရင် Memory ပိုသုံးသည်|
|Class Name နဲ့ Access လုပ်နိုင်သည်|Object Reference နဲ့ Access လုပ်ရသည်|

---

# Static Variable ကို ဘယ်အချိန်သုံးသလဲ?

Object အားလုံးမှာ **တူညီတဲ့ Data** ကို သိမ်းချင်တဲ့အခါ သုံးပါတယ်။

ဥပမာ

- Company Name
    
- School Name
    
- Country
    
- Currency
    
- Counter
    
- Tax Rate
    
- Configuration Value
    

---

# Real-world Example

Employee Class ကို စဉ်းစားကြည့်ပါ။

```java
class Employee {

    int id;
    String name;
    static String company = "OpenAI";

}
```

Employees

```text
Employee 1
Name = Aung
Company = OpenAI

Employee 2
Name = Kyaw
Company = OpenAI

Employee 3
Name = Su
Company = OpenAI
```

Employee တိုင်းမှာ Company Name တူပါတယ်။

ဒါကြောင့်

```java
static String company;
```

ကို သုံးတာက Memory ပိုသက်သာပါတယ်။

---

# Static Variable ရဲ့ အားသာချက်များ

- Memory ကို သက်သာစေတယ် (တစ်ခုပဲ သိမ်းထားလို့)
    
- Object အားလုံးက Data တစ်ခုတည်းကို Share လုပ်နိုင်တယ်။
    
- Class Name နဲ့ တိုက်ရိုက် Access လုပ်နိုင်တယ်။
    
- Counter, Configuration, Constants စတာတွေမှာ အသုံးများတယ်။
    

---

# Static Variable ရဲ့ အားနည်းချက်

Static Variable ကို ပြောင်းလိုက်ရင်

Object အားလုံးအပေါ် သက်ရောက်မှုရှိပါတယ်။

ဥပမာ

```java
Student.school = "XYZ";
```

ဆိုရင်

Student အားလုံးရဲ့ School Name က `"XYZ"` ဖြစ်သွားပါမယ်။

---

# Interview မှာ အတိုချုပ် ဘယ်လိုဖြေရမလဲ?

> **"A static variable is a class-level variable declared using the `static` keyword. It belongs to the class rather than individual objects, so only one copy exists regardless of how many objects are created. All objects of the class share the same static variable."**

---

# Interview Follow-up Questions

ဒီမေးခွန်းနောက်မှာ Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းတွေကတော့ -

1. Static Variable နဲ့ Instance Variable ဘာကွာလဲ?
    
2. Static Variable ကို ဘယ် Memory Area မှာ သိမ်းသလဲ?
    
3. Static Variable ကို Object နဲ့ Access လုပ်လို့ရလား?
    
4. Static Method က Static Variable ကို ဘယ်လို Access လုပ်လဲ?
    
5. `static final` ဆိုတာ ဘာလဲ?
    
6. Static Block ဆိုတာ ဘာလဲ?
    

---

# Interview Tip ⭐

Java Interview တွေမှာ အရမ်းမေးလေ့ရှိတဲ့ မေးခွန်းက—

> **Q:** _How many copies of a static variable are created if 100 objects are created?_

**Answer:**

> **Only one copy.** Static variables belong to the class, not to individual objects, so all 100 objects share the same variable.

ဒီအချက်ကို မှတ်ထားရင် Static Variable နဲ့ ပတ်သက်တဲ့ Interview Questions အများစုကို ယုံကြည်စွာ ဖြေနိုင်ပါလိမ့်မယ်။