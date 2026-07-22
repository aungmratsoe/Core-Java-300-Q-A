# What is Java? (Java ဆိုတာဘာလဲ?) — Core Java Interview

---

# 1. Definition (အဓိပ္ပာယ်)

**Java** ဆိုတာ **high-level, object-oriented, class-based, platform-independent programming language** တစ်ခုဖြစ်ပြီး၊ Sun Microsystems က 1995 ခုနှစ်မှာ ဖန်တီးခဲ့တာဖြစ်ပါတယ်။ နောက်ပိုင်းမှာတော့ Oracle က Sun Microsystems ကို ဝယ်ယူခဲ့တဲ့အတွက် Java ကို Oracle က ဆက်လက်ဖွံ့ဖြိုးတိုးတက်အောင် လုပ်ဆောင်နေပါတယ်။

Java ကို တစ်ခါရေးပြီး (**Write Once**) နေရာအမျိုးမျိုးမှာ (**Run Anywhere**) အလုပ်လုပ်နိုင်အောင် ဒီဇိုင်းထုတ်ထားပါတယ်။

---

# 2. Java ကို ဘာကြောင့် ဖန်တီးခဲ့တာလဲ?

1990 အစောပိုင်းကာလမှာ Programming Language အများစုဟာ Operating System တစ်ခုအတွက် ရေးထားရင် နောက် Operating System မှာ ပြန်ရေးရလေ့ရှိပါတယ်။

ဥပမာ

- Windows အတွက် ရေးထားတဲ့ Program
- Linux မှာ မအလုပ်လုပ်ဘူး။
- Mac မှာလည်း မအလုပ်လုပ်ဘူး။

ဒီပြဿနာကို ဖြေရှင်းဖို့ Java ကို ဖန်တီးခဲ့တာဖြစ်ပါတယ်။

Java က

> **"Write Once, Run Anywhere (WORA)"**

ဆိုတဲ့ အယူအဆကို အသုံးပြုထားပါတယ်။

---

# 3. Java ရဲ့ Features (အဓိကလက္ခဏာများ)

Java မှာ Interview မှာ အမြဲမေးလေ့ရှိတဲ့ Features တွေရှိပါတယ်။

## (1) Platform Independent

Java Program ကို

```java
Hello.java
```

Compile လုပ်လိုက်ရင်

```java
Hello.class
```

ဆိုတဲ့ **Bytecode** ထွက်လာပါတယ်။

ဒီ Bytecode ကို JVM ရှိတဲ့ မည်သည့် Operating System မှာမဆို Run လို့ရပါတယ်။

ဥပမာ

- Windows
- Linux
- macOS

အားလုံးမှာ အလုပ်လုပ်နိုင်ပါတယ်။

---

## (2) Object-Oriented

Java က Object-Oriented Programming Language ဖြစ်ပါတယ်။

OOP Concepts

- Class
- Object
- Inheritance
- Polymorphism
- Encapsulation
- Abstraction

Java Program အများစုကို Object တွေ အသုံးပြုပြီး တည်ဆောက်ပါတယ်။

---

## (3) Simple

Java ရဲ့ Syntax က C++ နဲ့ ဆင်တူပါတယ်။

ဒါပေမယ့်

Java မှာ

- Pointer Arithmetic မရှိ
- Multiple Inheritance (Class) မရှိ
- Operator Overloading မရှိ

အဲဒါကြောင့် C++ ထက် ပိုလွယ်ပါတယ်။

---

## (4) Secure

Java က Security အတွက်

- Bytecode Verification
- Class Loader
- Security Manager (ယခင်ဗားရှင်းများတွင်)
- Garbage Collection

တို့ကို အသုံးပြုပါတယ်။

Virus ရေးဖို့ Java ကို အသုံးပြုရတာ ခက်ခဲပါတယ်။

---

## (5) Robust

Robust ဆိုတာ

Error ဖြစ်နိုင်ခြေ နည်းတယ်။

ဘာကြောင့်လဲ?

- Garbage Collection
- Exception Handling
- Strong Memory Management

တွေရှိလို့ပါ။

---

## (6) Multithreaded

Java က Thread များစွာကို တစ်ချိန်တည်းမှာ Run နိုင်ပါတယ်။

ဥပမာ

Browser

- Download
- Music
- Animation

သုံးခုလုံးကို တစ်ပြိုင်နက် လုပ်နိုင်ပါတယ်။

---

## (7) Distributed

Java က Network Programming ကို Support လုပ်ပါတယ်။

ဥပမာ

- Banking
- Online Shopping
- Client-Server Application

---

## (8) High Performance

Java ဟာ C/C++ လောက် မမြန်ပေမယ့်

JIT Compiler (Just-In-Time Compiler) ကြောင့် Performance က ကောင်းပါတယ်။

---

# 4. Java Program ဘယ်လိုအလုပ်လုပ်သလဲ?

```
Hello.java
      │
      ▼
javac
      │
      ▼
Hello.class (Bytecode)
      │
      ▼
JVM
      │
      ▼
Machine Code
      │
      ▼
Output
```

ဒီ Process က Java ရဲ့ အရေးကြီးဆုံး Concept တစ်ခုပါ။

---

# 5. Simple Example

```
public class Hello {
    public static void main(String[] args) {

        System.out.println("Hello Java");

    }
}
```

Output

```
Hello Java
```

---

# 6. Real-World Applications

Java ကို နေရာအများကြီးမှာ အသုံးပြုပါတယ်။

### Android Development

- Android Apps (ယခင်က Java ကို အဓိက အသုံးပြုခဲ့ပြီး ယနေ့ Kotlin နှင့် တွဲဖက်အသုံးပြုကြသည်)

### Banking Systems

- Online Banking
- ATM Software
- Payment Systems

### Enterprise Applications

- ERP
- CRM
- HR Management

### Web Applications

- Spring Boot
- Jakarta EE

### Desktop Applications

- Swing
- JavaFX

### Big Data

- Apache Hadoop

### Cloud Applications

- Microservices
- REST APIs

---

# 7. Advantages of Java

- Platform Independent
- Secure
- Robust
- Object-Oriented
- Automatic Garbage Collection
- Huge Community
- Rich Libraries
- Multithreading Support

---

# 8. Disadvantages of Java

- C/C++ ထက် Memory ပိုသုံးတတ်တယ်။
- Native Languages ထက် Performance အနည်းငယ်နိမ့်နိုင်တယ်။
- Startup Time က အချို့ Application တွေမှာ ပိုကြာနိုင်တယ်။

---

# 9. Interview Answer (1 Minute)

> **"Java is a high-level, object-oriented, class-based, platform-independent programming language developed by Sun Microsystems in 1995 and now maintained by Oracle. Its biggest advantage is 'Write Once, Run Anywhere,' which is possible because Java code is compiled into bytecode and executed by the JVM. Java is widely used for enterprise applications, web development, Android development, desktop applications, and cloud services. Its key features include platform independence, security, robustness, multithreading, automatic garbage collection, and strong object-oriented support."**

---

# 10. Common Follow-up Interview Questions

Interviewer က ဆက်မေးနိုင်တဲ့ မေးခွန်းတွေကတော့ -

1. Java က Platform Independent ဖြစ်တာ ဘာကြောင့်လဲ?
2. JVM ဆိုတာ ဘာလဲ?
3. JDK, JRE, JVM ကွာခြားချက်က ဘာလဲ?
4. Bytecode ဆိုတာ ဘာလဲ?
5. JIT Compiler ဆိုတာ ဘာလဲ?
6. Java က Compiled Language လား၊ Interpreted Language လား?
7. Java ကို ဘယ်လို Application တွေမှာ အသုံးပြုကြသလဲ?
8. Java က C++ နဲ့ ဘာကွာလဲ?
9. Garbage Collection ဆိုတာ ဘာလဲ?
10. Java ရဲ့ OOP Principles တွေက ဘာတွေလဲ?

---

# 11. Interview Tips ⭐

- **"Java is platform independent because of the JVM."** ဆိုတဲ့အချက်ကို ရှင်းပြနိုင်ရင် အမှတ်ရပါတယ်။
- **Bytecode → JVM → Machine Code** ဆိုတဲ့ Flow ကို Diagram နဲ့ ရှင်းပြနိုင်ရင် ပိုကောင်းပါတယ်။
- **Java သည် Compiled + Interpreted Language** လို့လည်း ပြောနိုင်ပါတယ်။
    - `javac` က Source Code ကို **Bytecode** အဖြစ် Compile လုပ်ပါတယ်။
    - JVM က Bytecode ကို ဖတ်ပြီး Execute လုပ်ရာမှာ Interpreter နဲ့ JIT Compiler ကို ပေါင်းစပ်အသုံးပြုပါတယ်။
- Interview မှာ "Java is just an object-oriented language." လို့ပဲ မဖြေဘဲ **Platform Independence, JVM, Bytecode, OOP, Garbage Collection** စတဲ့ အချက်တွေကို ထည့်ပြောနိုင်ရင် Beginner အဆင့်ထက် ပိုပြီး Professional ဖြစ်ပါတယ်။