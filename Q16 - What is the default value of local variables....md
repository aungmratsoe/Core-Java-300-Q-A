# What is the default value of local variables?

## (Local Variables တွေရဲ့ Default Value က ဘာလဲ?) — Core Java Interview

ဒီမေးခွန်းက Java ရဲ့ **Variable Initialization Rules** ကို စစ်တဲ့ မေးခွန်းဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

**Local variables do not have any default values in Java.**

ဆိုလိုတာက—

> **Local Variable တွေကို အသုံးမပြုခင် ကိုယ်တိုင် Initialize လုပ်ပေးရပါတယ်။**

မလုပ်ဘဲ အသုံးပြုရင် **Compilation Error** ဖြစ်ပါတယ်။

---

# 2. Example

```java
public class Test {

    public static void main(String[] args) {

        int age;

        System.out.println(age);

    }

}
```

Output:

```
Compilation Error:
variable age might not have been initialized
```

ဘာကြောင့်လဲ?

`age` က Local Variable ဖြစ်လို့ Java Compiler က Default Value မပေးပါဘူး။

---

# 3. Local Variable ဆိုတာဘာလဲ?

Method အတွင်းမှာ Declare လုပ်ထားတဲ့ Variable ကို Local Variable လို့ခေါ်ပါတယ်။

Example:

```java
public class Student {

    public void display() {

        int marks = 90;   // Local Variable

        System.out.println(marks);

    }

}
```

ဒီမှာ—

```java
int marks = 90;
```

က Local Variable ဖြစ်ပါတယ်။

---

# 4. Why Local Variables Have No Default Value?

အကြောင်းရင်းက **Memory Safety** ဖြစ်ပါတယ်။

Example:

```java
public void calculate() {

    int result;

    // Some complex logic

    System.out.println(result);

}
```

Compiler က မသေချာနိုင်ပါဘူး—

- Developer က Value ထည့်ဖို့ မေ့သွားတာလား?
- တကယ်မလိုတာလား?

ဒါကြောင့် Java က အလိုအလျောက် Value မပေးဘဲ Compile Error ပေးပါတယ်။

---

# 5. Instance Variables vs Local Variables

ဒီနှစ်ခုကို Interview မှာ မေးလေ့ရှိပါတယ်။

## Instance Variable

Class အတွင်း Method အပြင်မှာ Declare လုပ်ထားတဲ့ Variable

Example:

```java
class Student {

    int age;

}
```

Java က Default Value ပေးပါတယ်။

|Data Type|Default Value|
|---|---|
|int|0|
|long|0L|
|float|0.0f|
|double|0.0d|
|boolean|false|
|char|'\u0000'|
|Object Reference|null|

---

## Local Variable

Method အတွင်း Declare လုပ်ထားတာ

Example:

```java
void test(){

    int age;

}
```

Default Value:

```
No default value
```

---

# 6. Example Comparison

## Instance Variable

```java
class Person {

    int age;

    public static void main(String[] args) {

        Person p = new Person();

        System.out.println(p.age);

    }

}
```

Output:

```
0
```

ဘာကြောင့်လဲ?

`age` က Instance Variable ဖြစ်လို့ Default Value = 0 ရပါတယ်။

---

## Local Variable

```java
class Person {

    public static void main(String[] args) {

        int age;

        System.out.println(age);

    }

}
```

Output:

```
Compilation Error
```

---

# 7. What About Reference Local Variables?

Example:

```java
public class Test {

    public static void main(String[] args) {

        String name;

        System.out.println(name);

    }

}
```

Output:

```
Compilation Error
```

မဟုတ်ပါဘူး—

```
null
```

မထွက်ပါဘူး။

Local Reference Variable တွေလည်း Default Value မရှိပါဘူး။

---

# 8. Important Rule ⭐

Java မှာ—

```
Instance Variables
        ↓
Have Default Values

Local Variables
        ↓
No Default Values
```

---

# 9. Interview Answer (30 Seconds)

> **"Local variables in Java do not have any default values. They must be explicitly initialized before use; otherwise, the compiler will generate an error saying that the variable might not have been initialized. Unlike instance variables, local variables are stored in the stack and Java does not automatically initialize them."**

---

# 10. Common Follow-up Questions

1. What is the default value of instance variables?
2. Why local variables don't get default values?
3. Where are local variables stored?
4. Where are instance variables stored?
5. What happens if we access an uninitialized local variable?
6. Difference between local and instance variables?

---

# Interview Key Points ⭐

မှတ်ထားရန်—

```
Local Variable
      |
      ↓
No Default Value
      |
      ↓
Must Initialize Before Use
```

Example:

```
int x;        // ❌ Not initialized

int x = 10;   // ✅ Correct
```

**Final Answer:**

> **Local variables do not have any default values in Java. They must be initialized explicitly before use.** ✅