# What are the various access specifiers in Java?

## (Java မှာ Access Specifier / Access Modifier ဘယ်နှစ်မျိုးရှိသလဲ?) — Core Java Interview

ဒီမေးခွန်းက Java ရဲ့ **Encapsulation, Data Hiding, Class Accessibility** Concept ကို နားလည်ထားလား စစ်တဲ့ မေးခွန်းဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

Java မှာ **Access Specifiers (Access Modifiers) ၄ မျိုး** ရှိပါတယ်။

1. **private**
2. **default (package-private)**
3. **protected**
4. **public**

---

# 2. What is Access Specifier?

**Access Specifier** ဆိုတာ Class, Method, Variable, Constructor တွေကို ဘယ်နေရာကနေ Access လုပ်ခွင့်ရှိမရှိ သတ်မှတ်ပေးတဲ့ keyword ဖြစ်ပါတယ်။

Example:

```java
public class Student {

    private String name;

    public void display() {

    }

}
```

ဒီမှာ—

```java
private
public
```

တွေက Access Specifiers ဖြစ်ပါတယ်။

---

# 3. Types of Access Specifiers

---

# (1) private Access Modifier

## Definition

`private` က **အနည်းဆုံး access level** ဖြစ်ပါတယ်။

Private member ကို **အဲဒီ Class အတွင်းမှာပဲ** အသုံးပြုနိုင်ပါတယ်။

---

## Example

```java
class Student {

    private int age;

    private void display() {

        System.out.println(age);

    }

}
```

Access:

```
Same Class        ✅ Allowed
Same Package      ❌ Not Allowed
Subclass          ❌ Not Allowed
Other Package     ❌ Not Allowed
```

---

## Usage

Data Hiding အတွက် အသုံးများပါတယ်။

Example:

```java
class BankAccount {

    private double balance;

    public void deposit(double amount){

        balance += amount;

    }

}
```

`balance` ကို တိုက်ရိုက် မပြောင်းနိုင်အောင် private လုပ်ထားပါတယ်။

---

# (2) Default Access Modifier (Package-Private)

## Definition

Access modifier မရေးထားရင် default access ဖြစ်ပါတယ်။

Example:

```java
class Student {

    int age;

}
```

ဒီမှာ—

```java
int age;
```

က default access ဖြစ်ပါတယ်။

---

## Access Level

```
Same Class        ✅ Allowed
Same Package      ✅ Allowed
Subclass          ❌ Not Allowed (different package)
Other Package     ❌ Not Allowed
```

---

# (3) protected Access Modifier

## Definition

`protected` က Same Package နဲ့ Subclass တွေအတွက် access ပေးပါတယ်။

Example:

```java
class Animal {

    protected String name;

}
```

---

## Access Level

```
Same Class        ✅ Allowed
Same Package      ✅ Allowed
Subclass          ✅ Allowed
Other Package     ❌ (unless inherited)
```

---

## Example

Parent Class:

```java
class Animal {

    protected void eat(){

        System.out.println("Eating");

    }

}
```

Child Class:

```java
class Dog extends Animal {

    void bark(){

        eat();

    }

}
```

Access လုပ်နိုင်ပါတယ်။

---

# (4) public Access Modifier

## Definition

`public` က အမြင့်ဆုံး access level ဖြစ်ပါတယ်။

Public member ကို နေရာမရွေး Access လုပ်နိုင်ပါတယ်။

Example:

```java
public class Student {

    public String name;

}
```

---

## Access Level

```
Same Class        ✅ Allowed
Same Package      ✅ Allowed
Subclass          ✅ Allowed
Other Package     ✅ Allowed
```

---

# 4. Access Modifier Table ⭐

|Modifier|Same Class|Same Package|Subclass|Other Package|
|---|---|---|---|---|
|private|✅ Yes|❌ No|❌ No|❌ No|
|default|✅ Yes|✅ Yes|❌ No|❌ No|
|protected|✅ Yes|✅ Yes|✅ Yes|⚠️ Yes (through inheritance)|
|public|✅ Yes|✅ Yes|✅ Yes|✅ Yes|

---

# 5. Access Level Order

အနည်းဆုံးကနေ အများဆုံးသို့—

```
private
   ↓
default
   ↓
protected
   ↓
public
```

---

# 6. Access Modifier on Class

## Top-Level Class

Top-level class အတွက်—

✅ public  
✅ default

ပဲ သုံးနိုင်ပါတယ်။

Example:

```java
public class Student {

}
```

or

```java
class Student {

}
```

---

❌ Invalid:

```java
private class Student {

}
```

```java
protected class Student {

}
```

---

# 7. Access Modifier on Members

Class Members (Variable, Method, Constructor) တွေမှာ—

```
private
default
protected
public
```

အားလုံး သုံးနိုင်ပါတယ်။

Example:

```java
class Employee {

    private int id;

    String name;

    protected double salary;

    public void display(){

    }

}
```

---

# 8. Real World Example

Bank Account Class ကို စဉ်းစားပါ။

```java
class BankAccount {

    private double balance;

    public void deposit(double amount){

        balance += amount;

    }

    protected void calculateInterest(){

    }

}
```

- `balance` → private (Data Protection)
- `deposit()` → public (User Access)
- `calculateInterest()` → protected (Inheritance)

---

# 9. Interview Answer (1 Minute)

> **"Java provides four access specifiers: private, default, protected, and public. They control the visibility and accessibility of classes, methods, variables, and constructors. Private members are accessible only within the same class. Default members are accessible within the same package. Protected members are accessible within the same package and through inheritance. Public members are accessible from anywhere. Access modifiers are mainly used to implement encapsulation and data hiding."**

---

# 10. Common Follow-up Interview Questions

1. Difference between private and protected?
2. Can we make a class private in Java?
3. What is the default access modifier?
4. Can we override a private method?
5. Can a constructor be private?
6. Difference between protected and default?
7. Why do we use private variables with public getters/setters?

---

# Interview Key Points ⭐

မှတ်ထားရန်—

```
private
→ Only same class

default
→ Same package

protected
→ Same package + child class

public
→ Everywhere
```

အရေးကြီးဆုံး Concept:

> **Access modifiers in Java control visibility and provide security by restricting direct access to class members.** ✅