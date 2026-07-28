# What is a Static Method?

## Interview Answer (Short Answer)

**Static Method** ဆိုတာ **`static` keyword နဲ့ Declare လုပ်ထားတဲ့ Method** ဖြစ်ပြီး **Class ကိုပိုင်ဆိုင်တဲ့ Method** ဖြစ်ပါတယ်။

Static Method ကို **Object Create မလုပ်ဘဲ Class Name နဲ့ တိုက်ရိုက် ခေါ်နိုင်ပါတယ်။**

---

# Static Method ဆိုတာ ဘာလဲ?

Static Method က **Class Level Method** ဖြစ်ပါတယ်။

Instance Method လို Object တစ်ခုချင်းစီနဲ့ မသက်ဆိုင်ဘဲ **Class တစ်ခုလုံးနဲ့ သက်ဆိုင်ပါတယ်။**

ဥပမာ

```java
class Student {

    static void showMessage() {
        System.out.println("Welcome");
    }

}
```

ဒီမှာ

```java
showMessage()
```

က Static Method ဖြစ်ပါတယ်။

---

# Static Method ကို ဘယ်လိုခေါ်မလဲ?

### ✔ Class Name နဲ့ ခေါ်ခြင်း (Recommended)

```java
Student.showMessage();
```

Output

```text
Welcome
```

---

### ✔ Object နဲ့လည်း ခေါ်လို့ရတယ်

```java
Student s = new Student();

s.showMessage();
```

Output

```text
Welcome
```

ဒါပေမယ့် **Best Practice မဟုတ်ပါဘူး**။

Interview မှာ

> **Static Method ကို Class Name နဲ့ ခေါ်သင့်တယ်။**

လို့ ဖြေရပါတယ်။

---

# Example 1

```java
class Calculator {

    static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {

        int result = Calculator.add(10, 20);

        System.out.println(result);

    }

}
```

Output

```text
30
```

ဒီမှာ Object တစ်ခုမှ Create မလုပ်ဘဲ Method ကို ခေါ်ထားပါတယ်။

---

# Static Method ရဲ့ အလုပ်လုပ်ပုံ

```java
class Test {

    static void display() {
        System.out.println("Hello");
    }

}
```

Memory

```text
Class Test
----------------------
display()   ← Static Method
----------------------

Object 1
Object 2
Object 3
```

Object ဘယ်လောက်ပဲ Create လုပ်လုပ်

Static Method က **တစ်ခုတည်း** ရှိပါတယ်။

---

# Static Method က ဘာတွေကို Access လုပ်နိုင်သလဲ?

### ✔ Static Variable ကို တိုက်ရိုက် Access လုပ်နိုင်တယ်။

```java
class Student {

    static String school = "ABC";

    static void display() {
        System.out.println(school);
    }

}
```

Output

```text
ABC
```

---

### ✔ Static Method ကိုလည်း တိုက်ရိုက် ခေါ်နိုင်တယ်။

```java
class Test {

    static void first() {
        second();
    }

    static void second() {
        System.out.println("Hello");
    }

}
```

Output

```text
Hello
```

---

### ❌ Instance Variable ကို တိုက်ရိုက် Access မလုပ်နိုင်ဘူး။

```java
class Student {

    String name = "Aung";

    static void display() {
        System.out.println(name);
    }

}
```

Compile Error

```text
non-static variable name cannot be referenced from a static context
```

**ဘာကြောင့်လဲ?**

Static Method က Class နဲ့ သက်ဆိုင်ပြီး Object မလိုပါဘူး။

ဒါပေမယ့် Instance Variable က Object ရှိမှပဲ ရှိတာဖြစ်လို့ Static Method က တိုက်ရိုက် Access မလုပ်နိုင်ပါဘူး။

---

# Instance Variable ကို Access လုပ်ချင်ရင်?

Object Create လုပ်ရပါမယ်။

```java
class Student {

    String name = "Aung";

    static void display() {

        Student s = new Student();

        System.out.println(s.name);

    }

}
```

Output

```text
Aung
```

---

# Static Method vs Instance Method

|Static Method|Instance Method|
|---|---|
|`static` keyword ပါသည်|`static` မပါ|
|Class ကိုပိုင်ဆိုင်သည်|Object ကိုပိုင်ဆိုင်သည်|
|Object မလိုဘဲ ခေါ်နိုင်သည်|Object Create လုပ်ပြီးမှ ခေါ်နိုင်သည်|
|Static Members ကို တိုက်ရိုက် Access လုပ်နိုင်သည်|Static နှင့် Instance Members နှစ်မျိုးလုံးကို Access လုပ်နိုင်သည်|
|`this` နှင့် `super` ကို အသုံးမပြုနိုင်|`this` နှင့် `super` ကို အသုံးပြုနိုင်သည်|

---

# `main()` Method က ဘာကြောင့် `static` ဖြစ်တာလဲ?

```java
public static void main(String[] args)
```

`main()` က Program စတဲ့ Entry Point ဖြစ်ပါတယ်။

Program စတဲ့အချိန်မှာ Object တစ်ခုမှ မရှိသေးပါဘူး။

ဒါကြောင့် JVM က Object Create မလုပ်ဘဲ `main()` ကို တိုက်ရိုက် ခေါ်နိုင်ဖို့ `static` ဖြစ်ရပါတယ်။

---

# Real-world Example

Calculator Class

```java
class Calculator {

    static int square(int number) {
        return number * number;
    }

}
```

အသုံးပြုပုံ

```java
int result = Calculator.square(5);

System.out.println(result);
```

Output

```text
25
```

Calculator Object Create လုပ်စရာ မလိုပါဘူး။

---

# Static Method ကို ဘယ်အချိန်သုံးသလဲ?

အောက်ပါအခြေအနေတွေမှာ Static Method ကို အသုံးများပါတယ်။

- Utility Methods (`Math.sqrt()`, `Math.max()`)
    
- Helper Functions
    
- Factory Methods
    
- `main()` Method
    
- Validation Methods
    
- Common Calculation Methods
    

ဥပမာ

```java
Math.max(10, 20);
Math.sqrt(25);
Integer.parseInt("100");
```

ဒီ Methods တွေအားလုံးက Static Methods ဖြစ်ပါတယ်။

---

# Interview မှာ အတိုချုပ် ဘယ်လိုဖြေရမလဲ?

> **"A static method is a method declared with the `static` keyword. It belongs to the class rather than individual objects, so it can be called using the class name without creating an object. A static method can directly access only static members of the class."**

---

# Interview Follow-up Questions

ဒီမေးခွန်းနောက်မှာ Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းတွေကတော့ -

1. Static Method နဲ့ Instance Method ဘာကွာလဲ?
    
2. Static Method က Instance Variable ကို ဘာကြောင့် တိုက်ရိုက် Access မလုပ်နိုင်တာလဲ?
    
3. `main()` Method က ဘာကြောင့် `static` ဖြစ်တာလဲ?
    
4. Static Method ကို Override လုပ်လို့ရလား?
    
5. Static Method မှာ `this` ကို သုံးလို့ရလား?
    
6. Static Block ဆိုတာ ဘာလဲ?
    

---

# Interview Tip ⭐

Java Interview တွေမှာ မကြာခဏ မေးတဲ့ Follow-up Question က—

> **Q:** _Can a static method access a non-static method directly?_

**Answer:**

> **No.** Static Method က Object မရှိဘဲ Run ဖြစ်တာကြောင့် Non-static (Instance) Method ကို တိုက်ရိုက် မခေါ်နိုင်ပါဘူး။ ခေါ်ချင်ရင် အရင် Object Create လုပ်ပြီး အဲဒီ Object ကနေ ခေါ်ရပါတယ်။

ဥပမာ

```java
class Demo {

    void display() {
        System.out.println("Instance Method");
    }

    static void test() {
        Demo d = new Demo();
        d.display();
    }
}
```

ဒီအချက်ကို နားလည်ထားရင် Static Method နဲ့ ပတ်သက်တဲ့ Interview Questions အများစုကို အလွယ်တကူ ဖြေနိုင်ပါလိမ့်မယ်။