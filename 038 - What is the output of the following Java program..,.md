# Question

**What is the output of the following Java program?**

```java
class Test
{
    int test_a, test_b;

    Test(int a, int b)
    {
        test_a = a;
        test_b = b;
    }

    public static void main(String args[])
    {
        Test test = new Test();
        System.out.println(test.test_a + " " + test.test_b);
    }
}
```

---

# Answer

**ဒီ Program က Output မထုတ်ပါဘူး။**

**Compile-time Error** ဖြစ်ပါတယ်။

---

# Error

```text
constructor Test in class Test cannot be applied to given types;
required: int, int
found: no arguments
reason: actual and formal argument lists differ in length
```

(IDE အလိုက် Error Message အနည်းငယ် ကွာနိုင်ပါတယ်။)

---

# Explanation (မြန်မာလို)

ဒီ Class မှာ Constructor တစ်ခုတည်း ရှိပါတယ်။

```java
Test(int a, int b)
{
    test_a = a;
    test_b = b;
}
```

ဒီ Constructor က

- Parameter (၂) ခု လိုအပ်ပါတယ်။
    
    - `int a`
        
    - `int b`
        

---

## ဒါပေမယ့် Main Method မှာ

```java
Test test = new Test();
```

လို့ ရေးထားပါတယ်။

ဒီမှာ

```java
new Test();
```

ဆိုတာ **No-Argument Constructor** ကို ခေါ်နေတာ ဖြစ်ပါတယ်။

---

## Problem ဘာလဲ?

Class ထဲမှာ

```java
Test()
```

ဆိုတဲ့ No-Argument Constructor မရှိပါဘူး။

ရှိတာက

```java
Test(int a, int b)
```

တစ်ခုတည်းပါ။

ဒါကြောင့် Compiler က

> **ဘယ် Constructor ကို ခေါ်ရမလဲ?**

ဆိုတာ မသိတဲ့အတွက် Compile-time Error ဖြစ်ပါတယ်။

---

# Java Rule

Java Compiler က **Default Constructor** ကို **Class ထဲမှာ Constructor တစ်ခုမှ မရှိတဲ့အခါ** မှသာ Auto Generate လုပ်ပေးပါတယ်။

ဒီ Program မှာ

```java
Test(int a, int b)
```

ကို ကိုယ်တိုင်ရေးထားပြီးသား ဖြစ်တဲ့အတွက်

Compiler က

```java
Test()
{
}
```

ကို Auto Generate **မလုပ်တော့ပါဘူး။**

---

# Memory Flow

```
Test(int,int)   ✔ Exists

Test()          ✘ Doesn't Exist

        │
        ▼

new Test()

        │
        ▼

Compile Error
```

---

# ဘယ်လိုပြင်ရမလဲ?

## Method 1: Parameter ထည့်ပေးပါ

```java
Test test = new Test(10, 20);

System.out.println(test.test_a + " " + test.test_b);
```

Output

```text
10 20
```

---

## Method 2: No-Argument Constructor ထပ်ရေးပါ

```java
class Test {

    int test_a, test_b;

    Test() {
        test_a = 0;
        test_b = 0;
    }

    Test(int a, int b) {
        test_a = a;
        test_b = b;
    }

    public static void main(String[] args) {

        Test test = new Test();

        System.out.println(test.test_a + " " + test.test_b);

    }
}
```

Output

```text
0 0
```

---

# Interview Trick ⭐

ဒီမေးခွန်းက Interview မှာ **Default Constructor** ကို နားလည်မလားဆိုတာ စမ်းတာဖြစ်ပါတယ်။

Interviewer က သိချင်တာက

> **"Parameterized Constructor ရေးလိုက်ရင် Compiler က Default Constructor ကို Auto Generate လုပ်ပေးသေးလား?"**

**အဖြေက**

> **မလုပ်ပေးတော့ပါဘူး။**

---

# Interview Answer (Short)

> **Output:** ❌ **Compile-time Error**
> 
> **Reason:** The class defines only a parameterized constructor `Test(int, int)`. Since no no-argument constructor exists, the statement `new Test()` is invalid. Also, once a constructor is explicitly defined, Java does not automatically generate a default constructor.