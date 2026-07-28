# Question

**What is the output of the following Java program?**

```java
class Test
{
    int i;
}

public class Main
{
    public static void main(String args[])
    {
        Test test = new Test();
        System.out.println(test.i);
    }
}
```

---

# Answer (Output)

```text
0
```

---

# Explanation (မြန်မာလို)

ဒီ Program မှာ `Test` class ထဲမှာ

```java
int i;
```

ဆိုတဲ့ **Instance Variable** တစ်ခုကို Declare လုပ်ထားပါတယ်။

ဒါပေမယ့် Value မသတ်မှတ်ထားပါဘူး။

---

## Step 1: Object Creation

```java
Test test = new Test();
```

ဒီအချိန်မှာ

- `new` keyword က `Test` Object အသစ်တစ်ခုကို Memory ထဲမှာ Create လုပ်တယ်။
    
- Instance Variable `i` ကို Java က **Default Value** ပေးပါတယ်။
    

---

## Step 2: Default Value

Java မှာ **Instance Variables** နဲ့ **Static Variables** တွေကို Initialize မလုပ်ထားရင် JVM က Default Value တွေ အလိုအလျောက် သတ်မှတ်ပေးပါတယ်။

`int` ရဲ့ Default Value က

```text
0
```

ဖြစ်ပါတယ်။

ဒါကြောင့်

```java
System.out.println(test.i);
```

က

```text
0
```

ကို Print ထုတ်ပါတယ်။

---

# Memory Representation

Object Create လုပ်ပြီးနောက် Memory ကို အကြမ်းဖျင်း ဒီလိုမြင်နိုင်ပါတယ်။

```text
test
  │
  ▼
+----------------+
| Test Object    |
|----------------|
| i = 0          |
+----------------+
```

---

# Java Default Values

|Data Type|Default Value|
|---|---|
|`byte`|0|
|`short`|0|
|`int`|0|
|`long`|0L|
|`float`|0.0f|
|`double`|0.0|
|`char`|`'\u0000'` (null character)|
|`boolean`|`false`|
|Reference Types (`String`, Objects, Arrays)|`null`|

---

# အရေးကြီးတဲ့ Interview Point

ဒီမေးခွန်းမှာ Interviewer က **Instance Variable** နဲ့ **Local Variable** ကွာခြားချက်ကို စမ်းတာ ဖြစ်ပါတယ်။

### Instance Variable

```java
class Test {
    int i;
}
```

✔ Default Value ရှိတယ်။

Output

```text
0
```

---

### Local Variable

```java
public static void main(String[] args) {

    int i;

    System.out.println(i);
}
```

ဒီ Code က

**Compile Error** ဖြစ်ပါတယ်။

```text
variable i might not have been initialized
```

**ဘာကြောင့်လဲ?**

Local Variable ကို Java က Default Value မပေးပါဘူး။

Programmer ကိုယ်တိုင် Initialize လုပ်ရပါတယ်။

---

# Instance Variable vs Local Variable

|Instance Variable|Local Variable|
|---|---|
|Class အတွင်း၊ Method အပြင်မှာ Declare လုပ်သည်|Method / Constructor / Block အတွင်းမှာ Declare လုပ်သည်|
|JVM က Default Value ပေးသည်|Default Value မရှိ|
|Object နဲ့အတူ Create ဖြစ်သည်|Method ခေါ်တဲ့အချိန်မှ Create ဖြစ်သည်|
|Object မရှိမချင်း အသက်ရှင်သည်|Method ပြီးတာနဲ့ ပျက်သွားသည်|

---

# Interview Answer (Short)

> **Output:**
> 
> ```text
> 0
> ```
> 
> **Reason:** `i` is an **instance variable** of type `int`. Since it is not explicitly initialized, Java automatically assigns it the default value `0` when the object is created.

---

## ⭐ Interview Follow-up Question

Interviewer က ဒီမေးခွန်းပြီးရင် မကြာခဏ ဆက်မေးတာက—

> **Q:** _What if `i` were declared inside the `main()` method instead of inside the class?_

**Answer:**

```java
public static void main(String[] args) {
    int i;
    System.out.println(i);
}
```

**Result:**

```text
Compile-time Error:
variable i might not have been initialized
```

အကြောင်းကတော့ **Local Variables** ကို Java က Default Value မသတ်မှတ်ပေးဘဲ၊ အသုံးမပြုခင် Programmer ကိုယ်တိုင် Initialize လုပ်ရတာကြောင့် ဖြစ်ပါတယ်။