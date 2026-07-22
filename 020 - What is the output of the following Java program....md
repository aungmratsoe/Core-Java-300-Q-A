# What is the output of the following Java program?

## (Java String Concatenation and Addition Operator) — Core Java Interview

Given program:

```java
class Main  
{  
    public static void main (String args[])   
    {  
        System.out.println(10 + 20 + "Tpointtech");   
        System.out.println("Tpointtech" + 10 + 20);  
    }  
}
```

---

# Step 1: Understand `+` Operator in Java

Java မှာ `+` operator ကို အလုပ် ၂ မျိုးအတွက် အသုံးပြုပါတယ်။

### 1. Arithmetic Addition

Numbers နှစ်ခုလုံးဖြစ်ရင် ပေါင်းပေးပါတယ်။

Example:

```java
10 + 20
```

Result:

```java
30
```

---

### 2. String Concatenation

String တစ်ခု ပါလာရင် နောက်က Values တွေကို String အဖြစ် ဆက်ပေးပါတယ်။

Example:

```java
"Hello" + 10
```

Result:

```
Hello10
```

---

# First Statement

```java
System.out.println(10 + 20 + "Tpointtech");
```

Evaluation order က **left to right** ဖြစ်ပါတယ်။

---

First:

```java
10 + 20
```

Both are integers, so addition happens.

Result:

```java
30
```

---

Then:

```java
30 + "Tpointtech"
```

String ပါလာပြီဖြစ်လို့ concatenation ဖြစ်သွားပါတယ်။

Result:

```
30Tpointtech
```

---

# Second Statement

```java
System.out.println("Tpointtech" + 10 + 20);
```

Evaluation order က left to right ဖြစ်ပါတယ်။

---

First:

```java
"Tpointtech" + 10
```

String ပါနေတဲ့အတွက် concatenation ဖြစ်ပါတယ်။

Result:

```
Tpointtech10
```

---

Then:

```java
"Tpointtech10" + 20
```

ထပ်ပြီး String concatenation ဖြစ်ပါတယ်။

Result:

```
Tpointtech1020
```

---

# Final Output

```
30Tpointtech
Tpointtech1020
```

---

# Detailed Execution Flow

## Line 1

```java
10 + 20 + "Tpointtech"
```

Flow:

```
10 + 20
   |
   ↓
30
   |
   ↓
30 + "Tpointtech"
   |
   ↓
"30Tpointtech"
```

---

## Line 2

```java
"Tpointtech" + 10 + 20
```

Flow:

```
"Tpointtech" + 10
        |
        ↓
"Tpointtech10"
        |
        ↓
"Tpointtech10" + 20
        |
        ↓
"Tpointtech1020"
```

---

# Interview Key Point ⭐

Java မှာ မှတ်ထားရမယ့် Rule:

> **If `+` operator encounters a String, all remaining operands are treated as String concatenation (evaluated from left to right).**

Examples:

```java
System.out.println(1 + 2 + "Java");
```

Output:

```
3Java
```

---

```java
System.out.println("Java" + 1 + 2);
```

Output:

```
Java12
```

---

```java
System.out.println(1 + "Java" + 2 + 3);
```

Output:

```
1Java23
```

---

**Final Answer:**

```
30Tpointtech
Tpointtech1020
```