# Is the constructor inherited?

## Interview Answer (Short Answer)

**No. Constructors are not inherited in Java.**

ဆိုလိုတာက **Parent Class ရဲ့ Constructor ကို Child Class က အမွေဆက်ခံ (inherit) မလုပ်နိုင်ပါဘူး။**

သို့သော် **Child Class ရဲ့ Constructor က Parent Class ရဲ့ Constructor ကို `super()` keyword နဲ့ ခေါ်နိုင်ပါတယ်။**

---

# Constructor ကို ဘာကြောင့် Inherit မလုပ်တာလဲ?

Constructor ရဲ့ အဓိကတာဝန်က **Object တစ်ခုကို Initialize လုပ်ပေးဖို့** ဖြစ်ပါတယ်။

Constructor ဟာ **Class တစ်ခုအတွက်ပဲ သီးသန့်** ဖြစ်ပြီး Class Name နဲ့ တူရပါတယ်။

ဥပမာ

```java
class Animal {

    Animal() {
        System.out.println("Animal Constructor");
    }

}
```

ဒီ Constructor က `Animal` Class အတွက်ပဲ ဖြစ်ပါတယ်။

`Dog` Class က ဒီ Constructor ကို Inherit မလုပ်နိုင်ပါဘူး။

---

# Example

### Parent Class

```java
class Animal {

    Animal() {
        System.out.println("Animal Constructor");
    }

}
```

### Child Class

```java
class Dog extends Animal {

    Dog() {
        System.out.println("Dog Constructor");
    }

}
```

Main

```java
public class Main {

    public static void main(String[] args) {

        Dog d = new Dog();

    }

}
```

Output

```text
Animal Constructor
Dog Constructor
```

ဒီ Output ကိုကြည့်ရင် Parent Constructor အရင် Run တာကို တွေ့ရပါတယ်။

ဒါပေမယ့် **ဒါဟာ Constructor ကို Inherit လုပ်တာ မဟုတ်ပါဘူး။**

Java က Child Constructor ထဲမှာ

```java
super();
```

ကို အလိုအလျောက် ထည့်ပေးလို့ ဖြစ်ပါတယ်။

---

# `super()` ဘာလုပ်ပေးတာလဲ?

Child Class Constructor က Parent Class Constructor ကို ခေါ်ချင်ရင်

```java
super();
```

ကို အသုံးပြုပါတယ်။

```java
class Animal {

    Animal() {
        System.out.println("Animal Constructor");
    }

}

class Dog extends Animal {

    Dog() {
        super();
        System.out.println("Dog Constructor");
    }

}
```

Output

```text
Animal Constructor
Dog Constructor
```

> **မှတ်ချက်**: `super()` ကို Constructor ထဲမှာ **ပထမဆုံး Statement** အဖြစ်သာ ရေးနိုင်ပါတယ်။

---

# `super()` မရေးရင် ဘာဖြစ်မလဲ?

Parent Class မှာ **No-Argument Constructor** ရှိရင် Java Compiler က

```java
super();
```

ကို အလိုအလျောက် ထည့်ပေးပါတယ်။

```java
class Dog extends Animal {

    Dog() {
        System.out.println("Dog Constructor");
    }

}
```

Compiler က နောက်ကွယ်မှာ

```java
class Dog extends Animal {

    Dog() {
        super();
        System.out.println("Dog Constructor");
    }

}
```

လိုမျိုး ပြောင်းပေးပါတယ်။

---

# Parent မှာ Parameterized Constructor ပဲရှိရင်?

```java
class Animal {

    Animal(String name) {
        System.out.println(name);
    }

}
```

Child Class

```java
class Dog extends Animal {

    Dog() {

    }

}
```

ဒီ Code က **Compile Error** ဖြစ်ပါတယ်။

ဘာကြောင့်လဲ?

Compiler က

```java
super();
```

ကို ထည့်ပေးပေမယ့် Parent မှာ `Animal()` (No-Argument Constructor) မရှိလို့ ဖြစ်ပါတယ်။

မှန်အောင်ရေးရင်

```java
class Dog extends Animal {

    Dog() {
        super("Dog");
    }

}
```

---

# Constructor vs Method Inheritance

|Constructor|Method|
|---|---|
|❌ Inherit မလုပ်နိုင်|✅ Inherit လုပ်နိုင်|
|Override မလုပ်နိုင်|Override လုပ်နိုင်|
|Object Initialize လုပ်ဖို့ သုံး|Behavior သတ်မှတ်ဖို့ သုံး|
|Class Name နဲ့ တူ|မည်သည့် Name မဆို ရ|

---

# Real-world Example

**Person → Student**

```java
class Person {

    Person() {
        System.out.println("Person Created");
    }

}

class Student extends Person {

    Student() {
        System.out.println("Student Created");
    }

}
```

Output

```text
Person Created
Student Created
```

ဒီမှာ `Student` က `Person` Constructor ကို Inherit လုပ်တာ မဟုတ်ပါဘူး။

`Student()` Constructor က `Person()` Constructor ကို `super()` နဲ့ ခေါ်ထားတာ ဖြစ်ပါတယ်။

---

# Interview မှာ အတိုချုပ် ဘယ်လိုဖြေရမလဲ?

> **"No, constructors are not inherited in Java because they belong to the class itself and are used to initialize objects of that class. However, a child class constructor can invoke the parent class constructor using the `super()` keyword."**

---

# Interview Follow-up Questions

ဒီမေးခွန်းနောက်မှာ Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းတွေကတော့ -

1. `super()` ဆိုတာ ဘာလဲ?
    
2. `super()` ကို မရေးရင် ဘာဖြစ်မလဲ?
    
3. Parent Class မှာ Parameterized Constructor ပဲရှိရင် Child Class မှာ ဘာလုပ်ရမလဲ?
    
4. Constructor ကို Override လုပ်လို့ရလား?
    
5. Constructor Overloading လုပ်လို့ရလား?
    
6. `this()` နဲ့ `super()` က ဘာကွာလဲ?
    

---

## Interview Tip (အရေးကြီး)

Interviewer တွေက အောက်ပါမေးခွန်းနှစ်ခုကို ဆက်တိုက်မေးလေ့ရှိပါတယ်။

> **Q:** Constructors are not inherited. Then why is the parent constructor executed when we create a child object?

**အဖြေ**

> **Parent Constructor Run တာဟာ Inheritance ကြောင့် မဟုတ်ပါဘူး။ Child Constructor က `super()` ကို (ရေးထားသည်ဖြစ်စေ၊ Compiler က အလိုအလျောက်ထည့်ပေးသည်ဖြစ်စေ) ခေါ်တဲ့အတွက် Parent Constructor အရင် Execute ဖြစ်တာပါ။**

ဒီအချက်ကို ရှင်းပြနိုင်ရင် Java Inheritance နဲ့ Constructor အလုပ်လုပ်ပုံကို သေချာနားလည်ထားကြောင်း ပြသနိုင်ပါတယ်။