Question Bank: Java
This section contains questions specific to the Java programming language, covering core concepts, the JVM, and common libraries.
Easy
Question: What is the difference between JDK, JRE, and JVM?
Answer:
JVM (Java Virtual Machine): An abstract machine that provides a runtime environment in which Java bytecode can be executed. It's what makes Java "write once, run anywhere." It interprets the compiled .class file (bytecode).
JRE (Java Runtime Environment): The JRE is an implementation of the JVM. It is a software package that contains what is required to run Java programs, including the JVM, Java class libraries, and other supporting files.
JDK (Java Development Kit): The JDK is a superset of the JRE. It contains everything in the JRE, plus development tools necessary for compiling, debugging, and running Java applications, such as the compiler (javac) and debugger. You need the JDK to write Java programs, but only the JRE to run them.
Hint: JVM is the core concept. JRE = JVM + Libraries (for running). JDK = JRE + Tools (for developing).
Question: What is the difference between String, StringBuilder, and StringBuffer?
Answer:
String: An immutable class. Once a String object is created, its value cannot be changed. Every modification (like concatenation) creates a new String object.
StringBuilder: A mutable class. It allows for modification of the string's content without creating a new object. It is not thread-safe, making it faster. Use it for string manipulation in a single-threaded environment.
StringBuffer: Also a mutable class, similar to StringBuilder. However, StringBuffer is thread-safe (its methods are synchronized). This makes it slightly slower than StringBuilder. Use it when you need to modify strings in a multi-threaded environment.
Hint: String is unchangeable. StringBuilder is changeable and fast (for one thread). StringBuffer is changeable and safe (for multiple threads).
Question: What is the difference between an interface and an abstract class?
Answer:
| Feature | Abstract Class | Interface |
| :--- | :--- | :--- |
| Methods | Can have both abstract and concrete (implemented) methods. | Can only have abstract methods (before Java 8). Java 8+ allows default and static methods with implementation. |
| Variables | Can have final, non-final, static, and non-static variables. | Can only have public static final (constant) variables. |
| Inheritance | A class can extend only one abstract class. | A class can implement multiple interfaces. |
| Constructor| Can have a constructor. | Cannot have a constructor. |
| Purpose | To provide a common base with some shared implementation for a group of related classes. | To define a contract that unrelated classes can implement. |
Hint: Use an abstract class for an "is-a" relationship when you want to share code. Use an interface for a "can-do" or "has-a" capability that can be applied to many different classes.
Medium
Question: Explain the Java memory model (Heap vs. Stack).
Answer:
Stack Memory: Used for static memory allocation and thread execution. It contains primitive values that are specific to a method and references to objects that are stored in the Heap. Memory is allocated and deallocated in a Last-In-First-Out (LIFO) manner. Each thread has its own stack. It's fast but has a limited size.
Heap Memory: Used for dynamic memory allocation for all Java objects and JRE classes. Objects in the Heap are accessible by all threads. Memory management is more complex and is handled by the Garbage Collector. It's slower than the stack but much larger.
Hint: Stack is for method calls and local variables (short-lived). Heap is for objects (can be long-lived). int x = 10; - x is on the stack. Person p = new Person(); - p (the reference) is on the stack, but the Person object itself is on the heap.
Question: What are checked and unchecked exceptions in Java?
Answer:
Checked Exceptions: These are exceptions that are checked at compile time. The compiler forces you to handle them, either by catching them with a try-catch block or by declaring that your method throws the exception. They typically represent recoverable error conditions that a well-written application should anticipate and handle (e.g., IOException, SQLException). They inherit from the Exception class.
Unchecked Exceptions (Runtime Exceptions): These are exceptions that are not checked at compile time. You are not required to handle or declare them. They usually indicate programming errors or logic flaws, such as NullPointerException, ArrayIndexOutOfBoundsException, or IllegalArgumentException. They inherit from the RuntimeException class.
Hint: Checked = Compiler "checks" that you've handled it. Unchecked = Programmer's fault, happens at runtime.
Follow-up: "What is the finally block and when is it executed?"
Question: Explain the equals() and hashCode() contract.
Answer: This contract is crucial for the correct functioning of hash-based collections like HashMap and HashSet.
The contract is:
If two objects are equal according to the equals(Object) method, then calling the hashCode() method on each of the two objects must produce the same integer result.
If two objects are unequal according to the equals(Object) method, it is not required that hashCode() produce distinct results. However, producing distinct results for unequal objects may improve the performance of hash tables.
In short: Equal objects must have equal hash codes. If you override equals(), you MUST override hashCode(). If you fail to do so, when you put an object in a HashMap, you may not be able to retrieve it, because the hash code used to store the object might be different from the hash code used to look for it.
Hint: Think of hashCode as the bucket number in a hash map where an object should go. equals is used to check if the object is actually the one you're looking for within that bucket.
Follow-up: "What happens if you only override equals() but not hashCode() and try to use your object in a HashSet?"
Difficult
Question: What is garbage collection in Java? How does it work?
Answer: Garbage Collection (GC) is the process by which the Java Virtual Machine (JVM) automatically manages memory. It identifies and discards objects that are no longer in use by the program, freeing up their memory.
The basic process is often called "Mark and Sweep":
Marking: The garbage collector identifies all objects that are still reachable by the application. It starts from "GC Roots" (like active threads, static variables) and traverses the object graph, marking every object it visits as "alive".
Sweeping: After marking, all the heap memory that is not occupied by marked (alive) objects is considered garbage. The GC sweeps through the heap and reclaims the memory used by these unreachable objects.
Compacting (Optional): To reduce fragmentation, the GC can move all the live objects together, which makes new memory allocation faster.
Modern GCs like G1 and ZGC use more sophisticated algorithms, but they are all based on this principle of reachability.
Hint: GC's job is to find and delete objects that you can no longer get to from your running code.
Follow-up: "Can you name different types of Garbage Collectors in Java? (e.g., Serial, Parallel, G1GC)"
Question: What is the difference between fail-safe and fail-fast iterators?
Answer: This relates to how iterators handle concurrent modification of a collection.
Fail-fast Iterators: These iterators throw a ConcurrentModificationException if the underlying collection is structurally modified (items added or removed) in any way except through the iterator's own remove() method while iterating. They work on a copy of the collection or use an internal modification counter. Iterators for ArrayList and HashMap are fail-fast.
Fail-safe Iterators: These iterators do not throw any exception if the collection is modified while iterating. They work on a clone of the collection, so they are iterating over the state of the collection as it was when the iterator was created. They are generally slower and use more memory. Iterators for concurrent collections like CopyOnWriteArrayList and ConcurrentHashMap are fail-safe.
Hint: Fail-fast fails immediately and loudly. Fail-safe plays it safe by working on a copy, so it won't see the concurrent changes.
Follow-up: "Why would you choose a CopyOnWriteArrayList over a synchronized ArrayList?"
Question: Explain how a HashMap works internally in Java.
Answer: A HashMap in Java stores key-value pairs. Internally, it uses an array of "buckets," where each bucket can be a linked list or, after a certain threshold (8 in Java 8+), a balanced tree (Red-Black tree).
put(key, value):
The hashCode() of the key is calculated. This hash is then used to compute an index into the underlying array (e.g., index = hashCode % array_size).
The map goes to the bucket at that index.
If the bucket is empty, a new Node(key, value) is placed there.
If the bucket is not empty (a "collision"), it iterates through the nodes in the linked list (or tree). For each node, it checks if the key is the same using the equals() method.
If a node with the same key is found, its value is updated.
If no matching key is found, the new key-value pair is added to the end of the list (or to the tree).
get(key):
It calculates the hashCode() of the key and finds the bucket index, just like in put.
It then searches the linked list or tree in that bucket, using equals() to find the exact match for the key, and returns the corresponding value.
Hint: It's a combination of an array and linked lists/trees. hashCode() tells you which list to look in, and equals() finds the right item in that list.
Follow-up: "What happens when the HashMap becomes too full? (It gets resized)."
