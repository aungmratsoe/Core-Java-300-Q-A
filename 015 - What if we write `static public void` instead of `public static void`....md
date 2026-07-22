# What if we write `static public void` instead of `public static void`?

## (`public static void` နေရာမှာ `static public void` ရေးရင် ဘာဖြစ်မလဲ?) — Core Java Interview

ဒီမေးခွန်းက Java ရဲ့ **Access Modifier နဲ့ Non-access Modifier order** ကို နားလည်ထားလား စစ်တဲ့ မေးခွန်းဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

**`static public void` and `public static void` are both valid in Java.**

Java Compiler အတွက် Modifier တွေရဲ့ Order က အရေးမကြီးပါဘူး။

နှစ်ခုလုံး Compile လုပ်နိုင်ပါတယ်။

---

# 2. Example

Normal way:

```java
public class Main {

    public static void main(String[] args) {

        System.out.println("Hello Java");

    }

}
```

ဒါက အများဆုံးအသုံးပြုတဲ့ Style ဖြစ်ပါတယ်။

---

Alternative way:

```java
public class Main {

    static public void main(String[] args) {

        System.out.println("Hello Java");

    }

}
```

ဒါလည်း Valid ဖြစ်ပါတယ်။

Output:

```
Hello Java
```

---

# 3. Why does it work?

Java မှာ Method Declaration Syntax က—

```
[Access Modifier] [Non-access Modifier] ReturnType MethodName()
```

လို ရေးလေ့ရှိပေမယ့် Compiler က Modifier တွေရဲ့ Order ကို တိတိကျကျ မတောင်းဆိုပါဘူး။

---

ဥပမာ—

```java
public static final int VALUE = 10;
```

ကို

```java
static final public int VALUE = 10;
```

လို့လည်း ရေးနိုင်ပါတယ်။

နှစ်ခုလုံး အဓိပ္ပာယ်တူပါတယ်။

---

# 4. What does each keyword mean?

## `public`

ဒါက **Access Modifier** ဖြစ်ပါတယ်။

```java
public
```

ဆိုတာ—

- ဘယ် Class ကမဆို Access လုပ်နိုင်တယ်။

---

## `static`

ဒါက **Non-access Modifier** ဖြစ်ပါတယ်။

```java
static
```

ဆိုတာ—

- Object မဖန်တီးဘဲ Class Name နဲ့ ခေါ်နိုင်တယ်။
- JVM က `main()` method ကို Object မဖန်တီးဘဲ ခေါ်နိုင်အောင် လုပ်ပေးတယ်။

---

## `void`

ဒါက Return Type ဖြစ်ပါတယ်။

```java
void
```

ဆိုတာ—

- Method က ဘာ Value မှ Return မပြန်ဘူး။

---

# 5. How JVM Finds main Method?

JVM က `main()` method ကို ဒီ Signature နဲ့ ရှာပါတယ်—

```java
public static void main(String[] args)
```

ဒါပေမယ့် Modifier Order ကို မစစ်ပါဘူး။

ဒီနှစ်ခုကို JVM အတွက် တူတူပဲ ဖြစ်ပါတယ်။

```java
public static void main(String[] args)
```

and

```java
static public void main(String[] args)
```

---

# 6. What About Other Orders?

ဒီလိုတွေကလည်း Valid ဖြစ်နိုင်ပါတယ်။

```java
final public static int x = 10;
```

```java
static final public int x = 10;
```

```java
public final static int x = 10;
```

အားလုံး အဓိပ္ပာယ်တူပါတယ်။

---

# 7. Recommended Style

Technically အားလုံး Valid ဖြစ်ပေမယ့် Java Coding Convention အရ—

✅ Recommended:

```java
public static void main(String[] args)
```

ဘာကြောင့်လဲ?

- Java Developer အများစု ဒီ Style ကို သုံးတယ်။
- Readability ကောင်းတယ်။
- Code Review လုပ်ရလွယ်တယ်။
- Standard ဖြစ်တယ်။

---

# 8. Interview Answer (30 Seconds)

> **"In Java, the order of modifiers does not matter. Both `public static void main(String[] args)` and `static public void main(String[] args)` are valid and compile successfully. The JVM can recognize the main method regardless of the modifier order. However, according to Java coding conventions, we normally write `public static void main()` because it is more readable and commonly used."**

---

# 9. Common Follow-up Questions

1. Can we write `private static void main()`?
2. Why is main method static?
3. Can we overload main method?
4. Can we change the return type of main method?
5. Can we remove `public` from main method?
6. Why does JVM require public access?

---

# Interview Key Point ⭐

မှတ်ထားရန်—

```java
public static void main()
```

and

```java
static public void main()
```

are **exactly the same**.

အရေးကြီးဆုံးက Modifier order မဟုတ်ပါဘူး။

JVM အတွက် လိုအပ်တာက—

```java
public + static + void + main + String[]
```

ရှိနေဖို့ ဖြစ်ပါတယ်။