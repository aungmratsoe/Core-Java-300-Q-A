# Is `delete`, `next`, `main`, `exit`, or `null` a keyword in Java?

## (Java မှာ `delete`, `next`, `main`, `exit`, `null` တွေ Keyword ဟုတ်ပါသလား?) — Core Java Interview

ဒီမေးခွန်းက Java ရဲ့ **Keywords, Identifiers, and Literals** ကို ခွဲခြားနားလည်ထားလား စစ်တဲ့ မေးခွန်းဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

|Word|Is it a Java Keyword?|Explanation|
|---|---|---|
|`delete`|❌ No|Java မှာ keyword မဟုတ်ပါ|
|`next`|❌ No|Keyword မဟုတ်ပါ (method name အဖြစ်သုံးနိုင်)|
|`main`|❌ No|Keyword မဟုတ်ပါ (special method name)|
|`exit`|❌ No|Keyword မဟုတ်ပါ (method name အဖြစ်သုံးနိုင်)|
|`null`|❌ Not a keyword|Null literal ဖြစ်ပါတယ်|

**အဖြေမှန်: None of these are Java keywords.**

---

# 2. What are Java Keywords?

**Keyword** ဆိုတာ Java Language က သတ်မှတ်ထားပြီး အထူးအဓိပ္ပာယ်ရှိတဲ့ Reserved Words တွေဖြစ်ပါတယ်။

Keyword တွေကို Variable, Class, Method name အဖြစ် အသုံးပြုလို့ မရပါဘူး။

Examples:

```java
class
public
private
static
void
int
if
else
while
for
return
new
```

---

# 3. `delete` Keyword ဟုတ်ပါသလား?

## Answer:

❌ No

Java မှာ `delete` keyword မရှိပါဘူး။

C++ မှာတော့ memory release လုပ်ဖို့—

```c++
delete pointer;
```

အသုံးပြုပါတယ်။

ဒါပေမယ့် Java မှာ—

```
delete;
```

မရှိပါဘူး။

Java က Garbage Collector အသုံးပြုပါတယ်။

Example:

```java
Student s = new Student();

s = null;
```

Object ကို Garbage Collector က နောက်ပိုင်းမှာ ရှင်းပေးနိုင်ပါတယ်။

---

# 4. `next` Keyword ဟုတ်ပါသလား?

## Answer:

❌ No

`next` က Java keyword မဟုတ်ပါဘူး။

ဒါပေမယ့် Method Name အဖြစ် အသုံးများပါတယ်။

Example:

```java
Scanner scanner = new Scanner(System.in);

int number = scanner.nextInt();
```

ဒီမှာ—

```
nextInt()
```

က Scanner Class ရဲ့ method ဖြစ်ပါတယ်။

---

# 5. `main` Keyword ဟုတ်ပါသလား?

## Answer:

❌ No

`main` က keyword မဟုတ်ပါဘူး။

ဒါက Java Program စတင် Run ဖို့ JVM ရှာတဲ့ **special method name** ဖြစ်ပါတယ်။

Example:

```java
public static void main(String[] args) {

    System.out.println("Hello");

}
```

ဒီမှာ—

- `public` → keyword
- `static` → keyword
- `void` → keyword
- `main` → method name

ဖြစ်ပါတယ်။

---

# 6. `exit` Keyword ဟုတ်ပါသလား?

## Answer:

❌ No

`exit` က keyword မဟုတ်ပါဘူး။

ဒါက Method Name ဖြစ်ပါတယ်။

Example:

```java
System.exit(0);
```

ဒီမှာ—

```
exit()
```

က `System` Class ထဲက method ဖြစ်ပါတယ်။

---

# 7. `null` Keyword ဟုတ်ပါသလား?

## Answer:

❌ Technically, `null` is NOT a keyword.

Java မှာ `null` ကို **null literal** လို့ ခေါ်ပါတယ်။

---

Example:

```java
String name = null;
```

အဓိပ္ပာယ်က—

`name` Reference Variable က ဘယ် Object ကိုမှ မညွှန်ဘူးလို့ ဆိုလိုပါတယ်။

---

## Important Difference

Java Keywords:

```
null
```

မပါပါဘူး။

ဒါပေမယ့် Java Language Specification မှာ special literal အဖြစ် သတ်မှတ်ထားပါတယ်။

---

# 8. Java Keywords vs Literals vs Method Names

|Type|Examples|
|---|---|
|Keyword|`class`, `public`, `static`, `void`, `new`|
|Literal|`true`, `false`, `null`|
|Method Name|`main()`, `nextInt()`, `exit()`|

---

# 9. Interview Answer (30 Seconds)

> **"Among delete, next, main, exit, and null, none of them are Java keywords. `delete` is not used in Java because memory is managed by Garbage Collection. `next` and `exit` are method names, and `main` is a special method name used as the entry point of a Java application. `null` is a null literal, not a keyword."**

---

# 10. Common Follow-up Interview Questions

1. How many keywords are there in Java?
2. Is `goto` a keyword in Java?
3. Is `const` a keyword in Java?
4. Difference between keyword and identifier?
5. Is `true` a keyword?
6. Is `String` a keyword?
7. Why is `main` not a keyword?

---

# Interview Tip ⭐

ဒီလို မေးခွန်းတွေမှာ အများဆုံးမှားတာက—

❌ `main` is a keyword  
❌ `null` is a keyword

လို့ ဖြေတာပါ။

မှန်ကန်တဲ့အချက်:

```
main  → Method name
exit  → Method name
next  → Method name
null  → Literal
delete → Not available in Java
```

**Answer: None of them are Java keywords.** ✅