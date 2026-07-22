# If I do not provide any arguments on the command line, then what will be the value stored in the String array passed into the `main()` method: empty or NULL

## (Command Line Arguments မပေးရင် `main()` method ထဲက String array က empty လား NULL လား?) — Core Java Interview

ဒီမေးခွန်းက Java ရဲ့ **Command Line Arguments** နဲ့ **Array Initialization** concept ကို စစ်တဲ့ Interview Question ဖြစ်ပါတယ်။

---

# 1. Short Answer (အတိုချုပ်)

**The value will be an empty String array, not NULL.**

ဆိုလိုတာက—

```java
public static void main(String[] args)
```

မှာ `args` က

```java
[]
```

ဖြစ်ပါတယ်။

`null` မဖြစ်ပါဘူး။

---

# 2. Example

Java Program:

```java
public class Test {

    public static void main(String[] args) {

        System.out.println(args.length);

    }

}
```

---

## Case 1: No command line arguments

Run:

```
java Test
```

Output:

```
0
```

ဘာကြောင့်လဲ?

`args` array ရှိပေမယ့် element မရှိလို့ ဖြစ်ပါတယ်။

Memory Concept:

```
args
 |
 ↓
+---------+
| empty   |
+---------+

length = 0
```

---

# 3. Case 2: With Arguments

Run:

```
java Test Hello Java
```

`args` ထဲမှာ—

```java
args[0] = "Hello"
args[1] = "Java"
```

ဖြစ်ပါတယ်။

Array:

```
args
 |
 ↓
+---------+---------+
| Hello   | Java    |
+---------+---------+

length = 2
```

---

# 4. Difference Between Empty Array and Null

## Empty Array

```java
String[] args = new String[0];
```

ဆိုလိုတာ—

- Array Object ရှိတယ်။
- Element မရှိဘူး။
- `length = 0`

Example:

```java
System.out.println(args.length);
```

Output:

```
0
```

---

## Null Array

```java
String[] args = null;
```

ဆိုလိုတာ—

- Array Object မရှိဘူး။
- Reference က ဘာမှမညွှန်ဘူး။

Example:

```java
System.out.println(args.length);
```

Output:

```java
NullPointerException
```

---

# 5. Why JVM Provides Empty Array?

JVM က `main()` method ကို Call လုပ်တဲ့အခါ—

```java
public static void main(String[] args)
```

အတွက် String Array တစ်ခု ဖန်တီးပေးပါတယ်။

Arguments မရှိရင်—

```java
new String[0]
```

ပေးပါတယ်။

ဒါကြောင့် Developer က—

```java
args.length
```

ကို Safe အသုံးပြုနိုင်ပါတယ်။

---

# 6. Important Example

```java
public class Demo {

    public static void main(String[] args) {

        if(args.length == 0) {

            System.out.println("No arguments provided");

        }
        else {

            System.out.println(args[0]);

        }

    }
}
```

Run:

```
java Demo
```

Output:

```java
No arguments provided
```

Error မဖြစ်ပါဘူး။

---

# 7. Interview Answer (30 Seconds)

> **"If no command-line arguments are provided, the JVM passes an empty String array to the main() method, not null. The array object exists, but it contains zero elements, so its length is 0. If the array were null, accessing its length would cause a NullPointerException."**

---

# 8. Common Follow-up Questions

Interviewer ဆက်မေးနိုင်တာများ—

1. Can we change the name of `args` in main method?
2. Why is main method parameter an array?
3. Can we overload the main method?
4. Can we run Java program without main method?
5. What is the difference between `String[] args` and `String args[]`?

---

# Interview Key Point ⭐

မှတ်ထားရန်—

```
No command line arguments

args = []

NOT

args = null
```

အရေးကြီးဆုံး Sentence:

> **"The JVM always creates a String array for the main method. If there are no command-line arguments, the array is empty with length 0."**