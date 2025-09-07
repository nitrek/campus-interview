Here’s your **Java Question Bank reformatted as Markdown** with a **Table of Contents**:

---

# **Java Question Bank**

This section contains questions specific to the **Java programming language**, covering **core concepts**, **the JVM**, and **common libraries**.

---

## **Table of Contents**

- [**Java Question Bank**](#java-question-bank)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**What is the difference between JDK, JRE, and JVM?**](#what-is-the-difference-between-jdk-jre-and-jvm)
    - [**What is the difference between String, StringBuilder, and StringBuffer?**](#what-is-the-difference-between-string-stringbuilder-and-stringbuffer)
    - [**What is the difference between an interface and an abstract class?**](#what-is-the-difference-between-an-interface-and-an-abstract-class)
  - [**Medium**](#medium)
    - [**Explain the Java memory model (Heap vs. Stack).**](#explain-the-java-memory-model-heap-vs-stack)
    - [**What are checked and unchecked exceptions in Java?**](#what-are-checked-and-unchecked-exceptions-in-java)
    - [**Explain the equals() and hashCode() contract.**](#explain-the-equals-and-hashcode-contract)
  - [**Difficult**](#difficult)
    - [**What is garbage collection in Java? How does it work?**](#what-is-garbage-collection-in-java-how-does-it-work)
    - [**What is the difference between fail-safe and fail-fast iterators?**](#what-is-the-difference-between-fail-safe-and-fail-fast-iterators)
    - [**Explain how a HashMap works internally in Java.**](#explain-how-a-hashmap-works-internally-in-java)

---

## **Easy**

### **What is the difference between JDK, JRE, and JVM?**

**Answer:**

* **JVM (Java Virtual Machine):**

  * An abstract machine that provides a **runtime environment** for executing Java bytecode.
  * Enables **write once, run anywhere**.
  * Interprets the compiled `.class` file (bytecode).

* **JRE (Java Runtime Environment):**

  * Implementation of the JVM.
  * Contains **JVM + Java class libraries + supporting files**.
  * Required to **run Java programs**.

* **JDK (Java Development Kit):**

  * Superset of the JRE.
  * Contains **JRE + development tools** (e.g., `javac`, debugger).
  * Required to **write Java programs**.

**Hint:**

* JVM = core execution environment
* JRE = JVM + libraries (**run**)
* JDK = JRE + tools (**develop**)

---

### **What is the difference between String, StringBuilder, and StringBuffer?**

**Answer:**

* **String:**

  * Immutable class.
  * Every modification creates a **new String object**.

* **StringBuilder:**

  * Mutable class.
  * Allows modification **without creating new objects**.
  * **Not thread-safe**, so faster (for single-threaded environments).

* **StringBuffer:**

  * Mutable class, similar to StringBuilder.
  * **Thread-safe** (methods are synchronized).
  * Slower than StringBuilder.

**Hint:**

* String = **unchangeable**
* StringBuilder = **changeable, fast, single-thread**
* StringBuffer = **changeable, safe, multi-thread**

---

### **What is the difference between an interface and an abstract class?**

**Answer:**

| Feature         | Abstract Class                                  | Interface                                                  |
| --------------- | ----------------------------------------------- | ---------------------------------------------------------- |
| **Methods**     | Can have both abstract and concrete methods.    | Only abstract methods (Java 8+ allows default and static). |
| **Variables**   | Can have final, non-final, static, non-static.  | Only `public static final` constants.                      |
| **Inheritance** | A class can extend only **one** abstract class. | A class can implement **multiple** interfaces.             |
| **Constructor** | Can have a constructor.                         | Cannot have a constructor.                                 |
| **Purpose**     | Common base with shared implementation.         | Defines a contract for unrelated classes.                  |

**Hint:**

* Abstract class = **"is-a" relationship** (share code).
* Interface = **"can-do" capability** (contract).

---

## **Medium**

### **Explain the Java memory model (Heap vs. Stack).**

**Answer:**

* **Stack Memory:**

  * Stores **method calls, local variables, and references**.
  * Allocated per thread (LIFO order).
  * Fast but limited in size.

* **Heap Memory:**

  * Stores **objects and class instances**.
  * Shared across threads.
  * Managed by **Garbage Collector**.
  * Slower but much larger.

**Hint:**

* **Stack:** for short-lived data (method calls).
* **Heap:** for objects (long-lived).
* Example:

  ```java
  int x = 10;  // x in stack
  Person p = new Person(); // reference in stack, object in heap
  ```

---

### **What are checked and unchecked exceptions in Java?**

**Answer:**

* **Checked Exceptions:**

  * Checked at **compile-time**.
  * Must be handled or declared with `throws`.
  * Represent **recoverable conditions**.
  * Examples: `IOException`, `SQLException`.

* **Unchecked Exceptions:**

  * Checked at **runtime**.
  * Represent **programming errors**.
  * Examples: `NullPointerException`, `ArrayIndexOutOfBoundsException`.

**Hint:**

* Checked = compiler **forces handling**.
* Unchecked = happens at **runtime**.

**Follow-up:**
*What is the `finally` block and when is it executed?*

---

### **Explain the equals() and hashCode() contract.**

**Answer:**

* If two objects are equal by `equals()`, their `hashCode()` **must be the same**.
* If two objects are **not equal**, `hashCode()` can be same (but distinct is better).
* If you **override equals()**, you **must override hashCode()**.
* Failure leads to issues in **HashMap, HashSet**.

**Hint:**

* `hashCode()` = bucket index.
* `equals()` = verifies exact object match.

**Follow-up:**
*What happens if you override equals() but not hashCode()?*

---

## **Difficult**

### **What is garbage collection in Java? How does it work?**

**Answer:**

* **Garbage Collection (GC):**

  * JVM automatically **reclaims memory of unreachable objects**.
  * **Mark and Sweep process:**

    * **Mark:** Identify reachable objects from GC roots.
    * **Sweep:** Remove unmarked objects.
    * **Compact (optional):** Reduce fragmentation.

* Modern GCs: **G1, ZGC, Parallel GC**.

**Hint:**

* GC = delete objects that **no longer have references**.

**Follow-up:**
*Name types of Garbage Collectors (Serial, Parallel, G1GC).*

---

### **What is the difference between fail-safe and fail-fast iterators?**

**Answer:**

* **Fail-fast Iterators:**

  * Throw `ConcurrentModificationException` if collection is modified during iteration.
  * Example: **ArrayList, HashMap**.

* **Fail-safe Iterators:**

  * Work on a **copy** of the collection.
  * No exception if modified.
  * Example: **CopyOnWriteArrayList, ConcurrentHashMap**.

**Hint:**

* Fail-fast = **fails immediately**.
* Fail-safe = **safe copy, slower**.

**Follow-up:**
*Why use CopyOnWriteArrayList instead of synchronized ArrayList?*

---

### **Explain how a HashMap works internally in Java.**

**Answer:**

* **Stores key-value pairs** in **buckets**.
* `hashCode()` → determines bucket index.
* Handles collisions via:

  * **Linked List** (Java < 8).
  * **Tree (Red-Black)** if chain > 8 (Java 8+).
* **put():**

  * Compute hash → find bucket → add/update node.
* **get():**

  * Compute hash → find bucket → compare keys via `equals()`.

**Hint:**

* **Array + Linked List + Tree** for collisions.
* **Resize when load factor > threshold**.

**Follow-up:**
*What happens when HashMap gets too full? (Resizes).*