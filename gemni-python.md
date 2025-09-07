

# **Python Question Bank**

This section contains questions specific to the Python programming language, covering its unique features, data structures, and standard practices.

---

## **Table of Contents**

- [**Python Question Bank**](#python-question-bank)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**What is the difference between a list and a tuple in Python?**](#what-is-the-difference-between-a-list-and-a-tuple-in-python)
    - [**What are Python decorators?**](#what-are-python-decorators)
    - [**What is the difference between .py and .pyc files?**](#what-is-the-difference-between-py-and-pyc-files)
  - [**Medium**](#medium)
    - [**Explain the Global Interpreter Lock (GIL) in Python.**](#explain-the-global-interpreter-lock-gil-in-python)
    - [**What are list comprehensions and generators in Python? Give an example.**](#what-are-list-comprehensions-and-generators-in-python-give-an-example)
    - [**What is the difference between `__init__` and `__new__` in Python?**](#what-is-the-difference-between-__init__-and-__new__-in-python)
  - [**Difficult**](#difficult)
    - [**Explain how memory management works in Python.**](#explain-how-memory-management-works-in-python)
    - [**What are metaclasses in Python? Why might you use one?**](#what-are-metaclasses-in-python-why-might-you-use-one)
    - [**Describe Python's descriptor protocol. How is it used?**](#describe-pythons-descriptor-protocol-how-is-it-used)

---

## **Easy**

### **What is the difference between a list and a tuple in Python?**

**Answer:**

* **List:** Mutable (can be changed), defined with square brackets `[]`.
* **Tuple:** Immutable (cannot be changed), defined with parentheses `()`.
* Tuples can be used as dictionary keys; lists cannot.
* Tuples are more memory-efficient and slightly faster.

**Hint:** List = grocery list you can add to; Tuple = fixed coordinates (x, y).

---

### **What are Python decorators?**

**Answer:**
A **decorator** is a design pattern that adds functionality to an existing function or method without modifying its structure. It usually:

* Takes a function as an argument.
* Adds functionality.
* Returns another function.

Represented by `@` symbol.

**Hint:** Think of it as "wrapping" a function for extra behavior (e.g., logging, timing).

---

### **What is the difference between .py and .pyc files?**

**Answer:**

* **.py:** Source code file (human-readable).
* **.pyc:** Compiled bytecode file. Created by the Python interpreter to speed up execution.

**Hint:** `.py` = you write it; `.pyc` = Python creates it for faster execution.

---

## **Medium**

### **Explain the Global Interpreter Lock (GIL) in Python.**

**Answer:**

* **GIL** is a mutex that allows only one thread to execute Python bytecode at a time.
* Exists in **CPython** (standard implementation).
* Simplifies memory management but prevents true parallelism for CPU-bound tasks.
* Released during I/O operations (good for I/O-bound tasks).

**Hint:** Think of GIL as a "talking stick" for threads.

**Follow-up:** *How can you achieve true parallelism despite GIL? (Hint: `multiprocessing`)*

---

### **What are list comprehensions and generators in Python? Give an example.**

**Answer:**

* **List Comprehension:** Creates an entire list in memory.

  ```python
  squares = [x*x for x in range(10)]
  ```
* **Generator Expression:** Uses `()` instead of `[]`, creates values on demand (memory-efficient).

  ```python
  squares_gen = (x*x for x in range(10))
  ```

**Hint:** List comprehension = full list now; Generator = items one at a time.

**Follow-up:** *What is the `yield` keyword used for?*

---

### **What is the difference between `__init__` and `__new__` in Python?**

**Answer:**

* **`__new__`:** Creates and returns a new instance (static method).
* **`__init__`:** Initializes the instance created by `__new__`.

**Hint:** `__new__` = factory builds car; `__init__` = fill car with fuel & settings.

---

## **Difficult**

### **Explain how memory management works in Python.**

**Answer:**

* **Reference Counting:** Each object tracks how many references point to it.
* **Cyclic Garbage Collector:** Handles reference cycles using a generational algorithm.

**Hint:** Python counts references; when zero → delete. Garbage collector cleans cycles.

---

### **What are metaclasses in Python? Why might you use one?**

**Answer:**

* **Metaclass:** The "class of a class."
* Defines behavior of classes (just like classes define behavior of objects).
* Use cases:

  * Enforce coding standards.
  * Auto-register classes (plugins, ORMs).
  * Inject attributes or methods.

**Hint:** If Class = blueprint for Object, Metaclass = blueprint for Class.

---

### **Describe Python's descriptor protocol. How is it used?**

**Answer:**
A **descriptor** is an object that defines behavior for attribute access by implementing:

* `__get__(self, instance, owner)`
* `__set__(self, instance, value)`
* `__delete__(self, instance)`

Used in:

* `@property`
* `staticmethod`
* `classmethod`

**Hint:** It's how properties and methods work internally.

**Follow-up:** *What's the difference between a data descriptor and a non-data descriptor?*