### What is the output of the following Java program?

```java
class Main {
    public static void main(String args[]) {
        System.out.println(10 * 20 + "Tpointtech");
        System.out.println("Tpointtech" + 10 * 20);
    }
}
```

## According to the Java Language

The second line:

```
"Tpointtech" + 10 * 20
```

is parsed according to **operator precedence**.

The `*` operator has **higher precedence** than `+`.

So the compiler interprets it as:

```java
"Tpointtech" + (10 * 20)
```

First:

```
10 * 20
```

becomes

```
200
```

Then:

```
"Tpointtech" + 200
```

becomes

```
Tpointtech200
```

## Therefore the output is:

```
200Tpointtech
Tpointtech200
```

---

### Why did I previously say it was a compilation error?

That was **my mistake**. I incorrectly analyzed the expression as if the `+` operation happened before the multiplication. In Java, **`*` has higher precedence than `+`**, so the multiplication is completed first, and only then does string concatenation occur.

---

## Think of it like this

### Example 1

```java
System.out.println("Java" + 5 * 2);
```

Compiler sees:

```java
System.out.println("Java" + (5 * 2));
```

Output:

```
Java10
```

---

### Example 2

```java
System.out.println(5 + 2 * 3);
```

Compiler sees:

```
5 + (2 * 3)
```

Output:

```
11
```

---

### Example 3

```java
System.out.println((5 + 2) * 3);
```

Output:

```
21
```

---

## Interview Answer

**Output:**

```
200Tpointtech
Tpointtech200
```

**Explanation:**

- In the first statement, `10 * 20` is evaluated first because `*` has higher precedence than `+`. The result `200` is then concatenated with `"Tpointtech"` to produce `200Tpointtech`.
- In the second statement, multiplication still happens first (`10 * 20 = 200`), and then `"Tpointtech"` is concatenated with `200`, producing `Tpointtech200`.