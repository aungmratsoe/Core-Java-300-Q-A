# Question

**What is the output of the following Java program?**

```java
public class Main
{
    Main(int a, int b)
    {
        System.out.println("a = " + a + " b = " + b);
    }

    Main(int a, float b)
    {
        System.out.println("a = " + a + " b = " + b);
    }

    public static void main(String args[])
    {
        byte a = 10;
        byte b = 15;

        Main obj = new Main(a, b);
    }
}
```

---

# Answer (Output)

```text
a = 10 b = 15
```

---

# Explanation (မြန်မာလို)

ဒီ Program မှာ Constructor နှစ်ခုရှိပါတယ်။

```java
Main(int a, int b)
```

နဲ့

```java
Main(int a, float b)
```

---

## Step 1: Variables

```java
byte a = 10;
byte b = 15;
```

Variable နှစ်ခုလုံးက **byte** type ဖြစ်ပါတယ်။

---

## Step 2: Constructor Call

```java
Main obj = new Main(a, b);
```

ဒီနေရာမှာ

Argument နှစ်ခုလုံးက

```text
byte, byte
```

ဖြစ်ပါတယ်။

Java Compiler က Constructor ရှာတဲ့အခါ

### Constructor 1

```java
Main(int a, int b)
```

လိုအပ်တဲ့ Parameter

```text
int, int
```

byte → int

✔ Widening Conversion ဖြစ်လို့ ရပါတယ်။

---

### Constructor 2

```java
Main(int a, float b)
```

လိုအပ်တာက

```text
int, float
```

byte → int ✔

byte → float ✔

ဒါလည်း ရပါတယ်။

---

## Step 3: ဘယ် Constructor ကိုရွေးမလဲ?

ဒီနေရာမှာ Java က **Method/Constructor Overloading Resolution Rules** ကို အသုံးပြုပါတယ်။

Comparison

|Constructor|Conversion|
|---|---|
|`Main(int, int)`|byte → int, byte → int|
|`Main(int, float)`|byte → int, byte → float|

Java က **ပို Specific ဖြစ်တဲ့ Match** ကို ရွေးပါတယ်။

`int` က `float` ထက် ပို Specific ဖြစ်တဲ့အတွက်

```java
Main(int, int)
```

ကို ခေါ်ပါတယ်။

---

## ဒါကြောင့် Output က

```text
a = 10 b = 15
```

ဖြစ်ပါတယ်။

---

# Memory Flow

```
byte a = 10
byte b = 15

        │
        ▼

new Main(a,b)

        │
        ▼

Constructor Matching

Main(int,int)   ✔ Selected

Main(int,float) ✘ Not Selected
```

---

# Interview Point (အရေးကြီး)

ဒီမေးခွန်းက Interview မှာ **Constructor Overloading Resolution** နဲ့ **Type Promotion (Widening Conversion)** ကို နားလည်မလားဆိုတာ စမ်းတာဖြစ်ပါတယ်။

Java မှာ Constructor သို့မဟုတ် Method Overloading ဖြစ်တဲ့အခါ Compiler က

1. **Exact Match** ရှာတယ်။
    
2. Exact Match မရှိရင် **Widening Conversion** ကို အသုံးပြုတယ်။
    
3. **ပို Specific ဖြစ်တဲ့ Constructor/Method** ကို ရွေးတယ်။
    
4. မရွေးနိုင်ရင် **Compile-time Error (Ambiguous Method Call)** ဖြစ်တယ်။
    

---

# Interview Answer (Short)

> **Output:**
> 
> ```text
> a = 10 b = 15
> ```
> 
> **Reason:** Both constructors are applicable because `byte` can be widened to both `int` and `float`. However, Java selects the more specific overloaded constructor, which is `Main(int, int)`.