# What will be the initial value of an object reference that is defined as an instance variable?

## (Instance Variable အဖြစ် ကြေညာထားသော Object Reference ရဲ့ Initial Value က ဘာလဲ?) — Core Java Interview

ဒီမေးခွန်းက Java ရဲ့ **Default Values** နဲ့ **Memory Management** ကို နားလည်ထားလားဆိုတာ စစ်တဲ့ Interview Question ဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

**The default value of an object reference instance variable is `null`.**

မြန်မာလိုဆိုရရင်—

> **Class ထဲမှာ Instance Variable အဖြစ် ကြေညာထားတဲ့ Object Reference ရဲ့ Default Value က `null` ဖြစ်ပါတယ်။**

---

# 2. What is an Object Reference?

Object Reference ဆိုတာ Object ကို တိုက်ရိုက်မသိမ်းဘဲ **Object ရှိတဲ့ Memory Address (Reference)** ကို သိမ်းထားတဲ့ Variable ဖြစ်ပါတယ်။

ဥပမာ—

```
Student s;
```

ဒီမှာ

- `Student` → Class
- `s` → Object Reference Variable

---

# 3. Example

```
class Student {

}
```

```
class Test {

    Student s;

    public static void main(String[] args) {

        Test t = new Test();

        System.out.println(t.s);

    }

}
```

### Output

```
null
```

---

# Explanation

```
Student s;
```

ကို Value မပေးထားပေမယ့်

Java က Default အနေနဲ့

```
Student s = null;
```

လို သတ်မှတ်ပေးပါတယ်။

---

# 4. Memory Diagram

```
Heap Memory

Test Object
-----------------
s  -------> null
```

`null` ဆိုတာ

> **"ဒီ Reference Variable က ဘယ် Object ကိုမှ မညွှန်သေးဘူး"**

လို့ အဓိပ္ပာယ်ရပါတယ်။

---

# 5. After Creating an Object

```
class Student {

}
```

```
class Test {

    Student s = new Student();

}
```

Memory

```
Heap

Test Object
-----------------
s ---------+

Student Object
--------------
```

အခု `s` က `null` မဟုတ်တော့ဘဲ Student Object ကို Reference လုပ်နေပါတယ်။

---

# 6. What is `null`?

`null` ဆိုတာ

> **Object မရှိသေးတဲ့ Reference** ကို ကိုယ်စားပြုတဲ့ Special Literal ဖြစ်ပါတယ်။

Example

```
String name = null;
```

ဆိုလိုတာက

```
name

↓

No Object
```

---

# 7. Instance Variable vs Local Variable

ဒီနေရာက Interview မှာ မေးတတ်ပါတယ်။

## Instance Variable

```
class Test {

    Student s;

}
```

Default Value

```
null
```

---

## Local Variable

```
public static void main(String[] args){

    Student s;

    System.out.println(s);

}
```

Output

```
Compilation Error
```

Error:

```
variable s might not have been initialized
```

**Local Variables** ကို Java က Default Value မပေးပါဘူး။

---

# 8. Default Values of Instance Variables

|Data Type|Default Value|
|---|---|
|byte|0|
|short|0|
|int|0|
|long|0L|
|float|0.0f|
|double|0.0|
|char|'\u0000'|
|boolean|false|
|Object Reference|**null**|

---

# 9. Example

```
class Employee {

}

class Company {

    Employee emp;

    void display() {
        System.out.println(emp);
    }

    public static void main(String[] args) {

        Company c = new Company();

        c.display();

    }

}
```

Output

```
null
```

---

# 10. Interview Trick ⭐

### Example 1

```
class Test {

    String name;

}
```

Output

```
null
```

---

### Example 2

```
class Test {

    int age;

}
```

Output

```
0
```

---

### Example 3

```
class Test {

    boolean flag;

}
```

Output

```
false
```

---

### Example 4

```
class Test {

    Test t;

}
```

Output

```
null
```

---

# 11. Interview Answer (30 Seconds)

> **"The default value of an object reference instance variable in Java is `null`. When an object reference is declared as an instance variable and not explicitly initialized, the JVM automatically assigns it the value `null`, indicating that it does not refer to any object. However, local reference variables do not receive default values and must be initialized before use."**

---

# 12. Common Follow-up Interview Questions

1. What is `null` in Java?
2. What is the default value of an instance variable?
3. What is the default value of a String variable?
4. What happens if you use a local variable without initialization?
5. What is the difference between instance variables and local variables?
6. Where are instance variables stored?
7. Why does the JVM assign default values only to instance variables?

---

# Interview Key Points ⭐

```
Instance Variable
        │
        ▼
Default Value Assigned by JVM
        │
        ▼
Object Reference = null
```

### Remember

```
class Test {

    Student s;   // default = null

}
```

```
public static void main(String[] args){

    Student s;   // ❌ No default value

}
```

---

# Final Answer

> **The initial (default) value of an object reference that is defined as an instance variable is `null`. The JVM automatically assigns `null` to all uninitialized object reference instance variables, indicating that they do not reference any object.** ✅