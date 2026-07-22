# How many types of memory areas are allocated by the JVM?

## (JVM က Memory Area ဘယ်နှစ်မျိုး Allocate လုပ်သလဲ?) — Core Java Interview

ဒီမေးခွန်းက **Core Java Interview** နဲ့ **Senior Java Interview** တွေမှာ အရမ်းမေးလေ့ရှိတဲ့ မေးခွန်းပါ။

Interviewer က JVM Memory ကို နားလည်ထားလား၊ Object တွေ ဘယ်မှာသိမ်းသလဲ၊ Local Variables တွေ ဘယ်မှာရှိလဲဆိုတာကို စစ်ချင်တာ ဖြစ်ပါတယ်။

---

# 1. Answer (အဖြေ)

JVM က **Runtime Data Areas (Memory Areas)** ကို **၅ မျိုး** ခွဲပြီး အသုံးပြုပါတယ်။

1. **Method Area**
2. **Heap Area**
3. **Java Stack Area**
4. **Program Counter (PC) Register**
5. **Native Method Stack**

> **မှတ်ရန်** - Interview မှာ "JVM Memory Areas" ဆိုရင် ဒီ **၅ ခု** ကို ပြောရပါမယ်။

---

# 2. JVM Memory Structure

```
                    JVM Memory

           +-------------------------+
           |      Method Area        |
           +-------------------------+

           +-------------------------+
           |        Heap Area        |
           +-------------------------+

           +-------------------------+
           |      Java Stack         |
           +-------------------------+

           +-------------------------+
           |     PC Register         |
           +-------------------------+

           +-------------------------+
           |   Native Method Stack   |
           +-------------------------+
```

---

# 3. Memory Area တစ်ခုချင်းစီကို အသေးစိတ်ရှင်းပြခြင်း

## (1) Method Area

### Definition

Method Area က **Class-level Information** တွေကို သိမ်းတဲ့ Memory Area ဖြစ်ပါတယ်။

ဒီ Memory ထဲမှာ

- Class Metadata
- Method Information
- Static Variables
- Runtime Constant Pool

တို့ကို သိမ်းထားပါတယ်။

---

### Example

```java
class Student {

    static String school = "ABC";

    public void study() {

    }

}
```

ဒီမှာ

```
static String school
```

က Method Area ထဲမှာ သိမ်းထားပါတယ်။

---

### Characteristics

- JVM တစ်ခုလုံးအတွက် Shared ဖြစ်ပါတယ်။
- Class Load လုပ်တဲ့အချိန်မှာ Allocate လုပ်ပါတယ်။
- Object တစ်ခုချင်းစီအတွက် မဟုတ်ပါဘူး။

---

# (2) Heap Area ⭐ (အရေးကြီးဆုံး)

Heap က Interview မှာ အများဆုံးမေးတဲ့ Memory Area ဖြစ်ပါတယ်။

### Definition

Heap Memory ထဲမှာ **Objects** နဲ့ **Instance Variables** တွေကို သိမ်းပါတယ်။

---

### Example

```java
Student s = new Student();
```

ဒီ

```java
new Student();
```

က Heap ထဲမှာ Object တစ်ခု ဖန်တီးပါတယ်။

`s` ဆိုတဲ့ Reference Variable ကတော့ Stack မှာ ရှိပါတယ်။

---

### Diagram

```
Stack                     Heap

s  -------->        Student Object
```

---

### Characteristics

- Objects အားလုံး Heap ထဲမှာ ရှိတယ်။
- Garbage Collector က Heap ကို Cleanup လုပ်တယ်။
- Threads အားလုံးက Shared အသုံးပြုတယ်။

---

# (3) Java Stack Area

### Definition

Stack Memory က Method Call တွေ၊ Local Variables တွေနဲ့ Method Execution အတွက် အသုံးပြုပါတယ်။

---

### Example

```java
public static void main(String[] args){

    int age = 20;

}
```

ဒီ

```java
age
```

က Stack မှာ သိမ်းထားပါတယ်။

---

### Method Call Example

```
main()

↓

calculate()

↓

print()
```

Method တစ်ခုခေါ်တိုင်း Stack Frame အသစ်တစ်ခု တည်ဆောက်ပါတယ်။

Method ပြီးသွားရင် Stack Frame ကို အလိုအလျောက် ဖယ်ရှားပါတယ်။

---

### Characteristics

- Thread တစ်ခုစီမှာ ကိုယ်ပိုင် Stack ရှိပါတယ်။
- Local Variables တွေကို သိမ်းပါတယ်။
- Method Call ပြီးရင် Memory အလိုအလျောက် Release ဖြစ်ပါတယ်။

---

# (4) Program Counter (PC) Register

### Definition

PC Register က **လက်ရှိ Execute လုပ်နေတဲ့ Instruction ရဲ့ Address** ကို သိမ်းထားပါတယ်။

CPU က Program Counter ရှိသလို JVM မှာလည်း PC Register ရှိပါတယ်။

---

### Example

Program

```java
System.out.println("A");
System.out.println("B");
System.out.println("C");
```

PC Register က

```
Instruction 1

↓

Instruction 2

↓

Instruction 3
```

ဆိုပြီး လက်ရှိ Run နေတဲ့ Bytecode Instruction ကို မှတ်ထားပါတယ်။

---

### Characteristics

- Thread တစ်ခုစီမှာ PC Register တစ်ခု ရှိပါတယ်။
- Bytecode ဘယ်နေရာ Execute လုပ်နေတယ်ဆိုတာ Track လုပ်ပါတယ်။

---

# (5) Native Method Stack

### Definition

Java မဟုတ်တဲ့ Native Code (C/C++) ကို Execute လုပ်တဲ့အခါ အသုံးပြုတဲ့ Stack ဖြစ်ပါတယ်။

---

### Example

Java က Operating System API ကို Native Method နဲ့ ခေါ်တဲ့အခါ Native Method Stack ကို အသုံးပြုပါတယ်။

ဥပမာ

```
System.loadLibrary("xyz");
```

JNI (Java Native Interface) ကတစ်ဆင့် Native Code ကို ခေါ်နိုင်ပါတယ်။

---

### Characteristics

- Native Methods အတွက် အသုံးပြုပါတယ်။
- Java Code သာရေးတဲ့ Application အများစုမှာ တိုက်ရိုက် မမြင်ရပေမယ့် JVM အတွက် အရေးကြီးပါတယ်။

---

# 4. Summary Table

|Memory Area|Stores|Shared?|
|---|---|---|
|Method Area|Class Metadata, Static Variables, Runtime Constant Pool|✅ Yes|
|Heap|Objects, Instance Variables|✅ Yes|
|Java Stack|Local Variables, Method Calls|❌ No (Per Thread)|
|PC Register|Current Instruction Address|❌ No (Per Thread)|
|Native Method Stack|Native Method Execution|❌ No (Per Thread)|

---

# 5. Real-World Example

```java
class Student {

    static String school = "ABC";

    String name;

    public void study() {

        int hour = 5;

    }

}
```

Memory Allocation

```
Method Area
--------------------
Student Class
school

Heap
--------------------
Student Object
name

Stack
--------------------
hour
Reference Variable

PC Register
--------------------
Current Executing Instruction

Native Stack
--------------------
Native Method Calls
```

---

# 6. Interview Answer (1 Minute)

> **"The JVM divides its runtime memory into five main areas: Method Area, Heap Area, Java Stack, Program Counter Register, and Native Method Stack. The Method Area stores class-level information such as metadata and static variables. The Heap stores objects and instance variables, and it is managed by the Garbage Collector. The Java Stack stores local variables and method call frames for each thread. The PC Register keeps track of the currently executing bytecode instruction, while the Native Method Stack supports the execution of native methods written in languages such as C or C++."**

---

# 7. Common Follow-up Interview Questions

Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းများ—

1. Heap နဲ့ Stack က ဘာကွာလဲ?
2. Object တွေ ဘယ် Memory မှာ သိမ်းလဲ?
3. Local Variables တွေ ဘယ် Memory မှာ ရှိလဲ?
4. Static Variables တွေ ဘယ်မှာ သိမ်းလဲ?
5. Garbage Collector က ဘယ် Memory ကို Cleanup လုပ်သလဲ?
6. StackOverflowError ဘာကြောင့် ဖြစ်တာလဲ?
7. OutOfMemoryError ဘာကြောင့် ဖြစ်တာလဲ?
8. Runtime Constant Pool ဆိုတာ ဘာလဲ?
9. Program Counter Register က ဘာလုပ်တာလဲ?
10. Native Method Stack ကို ဘယ်အချိန်မှာ အသုံးပြုလဲ?

---

# 8. Interview Tips ⭐

## ⭐ Tip 1: Heap vs Stack ကို မရောထွေးပါနဲ့

- **Heap** → Objects, Instance Variables
- **Stack** → Local Variables, Method Calls

ဒါက Interview မှာ အမေးအများဆုံး ဖြစ်ပါတယ်။

---

## ⭐ Tip 2: Static Variables ဘယ်မှာလဲ?

လူအများစုက Static Variables ကို Heap ထဲမှာလို့ မှားဖြေတတ်ပါတယ်။

မှန်တဲ့အဖြေက

**Method Area** ဖြစ်ပါတယ်။

---

## ⭐ Tip 3: Garbage Collector

Garbage Collector က

**Heap Memory** ထဲက အသုံးမလိုတော့တဲ့ Object တွေကိုပဲ Cleanup လုပ်ပါတယ်။

Stack Memory ကို Garbage Collector က မစီမံပါဘူး။ Method ပြီးသွားတာနဲ့ Stack Frame တွေ အလိုအလျောက် ဖယ်ရှားသွားပါတယ်။

---

## ⭐ Tip 4: Senior Interview မှာ ပြောသင့်တဲ့ အချက်

JDK 8 နောက်ပိုင်းမှာ **Permanent Generation (PermGen)** ကို **Metaspace** နဲ့ အစားထိုးခဲ့ပါတယ်။

- **JDK 7 နှင့် အစောပိုင်း** → PermGen
- **JDK 8 နှင့် နောက်ပိုင်း** → Metaspace

ဒါဟာ JVM Implementation Detail ဖြစ်ပြီး Runtime Data Areas ရဲ့ အခြေခံ **၅ ခု** မပြောင်းပါဘူး။ ဒီအချက်ကို သိထားရင် Senior Java Interview မှာ အမှတ်ပိုရနိုင်ပါတယ်။