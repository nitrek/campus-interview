Question Bank: Python
This section contains questions specific to the Python programming language, covering its unique features, data structures, and standard practices.
Easy
Question: What is the difference between a list and a tuple in Python?
Answer:
List: Lists are mutable, meaning their elements can be changed (added, removed, or modified) after they are created. They are defined with square brackets [].
Tuple: Tuples are immutable, meaning once they are created, their elements cannot be changed. They are defined with parentheses ().
Because tuples are immutable, they can be used as keys in dictionaries, while lists cannot. Tuples are also generally more memory-efficient and slightly faster to iterate over than lists.
Hint: Think "list" = a list of groceries you can add to. "Tuple" = a fixed set of coordinates (x, y) that shouldn't change.
Question: What are Python decorators?
Answer: A decorator is a design pattern in Python that allows a user to add new functionality to an existing object (like a function or method) without modifying its structure. Decorators are usually implemented as functions that take another function as an argument, add some functionality, and then return another function. They are syntactically represented with the @ symbol.
Hint: It's a way to "decorate" or wrap a function with extra code. Common uses are for logging, timing, or authentication checks.
Question: What is the difference between .py and .pyc files?
Answer:
.py: These are the source code files containing the Python code you write. They are human-readable text files.
.pyc: These are the compiled bytecode files. When you run a Python script, the interpreter first compiles the source code into a lower-level, platform-independent format called bytecode. This .pyc file is then executed by the Python Virtual Machine (PVM). If you run the same script again and the .py file hasn't changed, the interpreter will skip the compilation step and directly use the .pyc file, making the startup faster.
Hint: .py is what you write. .pyc is what the interpreter creates to run your code faster next time.
Medium
Question: Explain the Global Interpreter Lock (GIL) in Python.
Answer: The Global Interpreter Lock (GIL) is a mutex (or a lock) that allows only one thread to hold the control of the Python interpreter at any given time. This means that in CPython (the standard Python implementation), even on a multi-core processor, only one thread can be executing Python bytecode at once.
The GIL simplifies memory management and makes it easier to integrate non-thread-safe C libraries. However, it effectively prevents true parallelism for CPU-bound tasks in multi-threaded Python programs. For I/O-bound tasks (like network requests or disk reads), the GIL is released while waiting for the I/O operation to complete, allowing other threads to run.
Hint: Think of the GIL as a "talking stick" for threads. Only the thread holding the stick can talk to the Python interpreter. This is a problem for tasks that need a lot of calculation, but not for tasks that involve a lot of waiting.
Follow-up: "How can you achieve true parallelism in Python despite the GIL? (e.g., using the multiprocessing module)."
Question: What are list comprehensions and generators in Python? Give an example.
Answer:
List Comprehension: A concise and readable way to create a list. It consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses. It evaluates the entire expression and returns a new list containing all the generated elements.
Example: squares = [x*x for x in range(10)]
Generator Expression: Similar in syntax to list comprehensions, but they use parentheses () instead of square brackets []. A generator does not create the entire list in memory at once. Instead, it creates a generator object that yields elements one by one as they are needed. This is much more memory-efficient for large sequences.
Example: squares_gen = (x*x for x in range(10))
Hint: List comprehension gives you the whole list right now. A generator gives you a recipe to make the list items one at a time, whenever you ask for the next one.
Follow-up: "What is the yield keyword used for?"
Question: What is the difference between __init__ and __new__ in Python?
Answer:
__new__: This is the first method to be called in object creation. Its main responsibility is to create and return a new, empty instance of the class. It is a static method that takes the class it needs to instantiate as its first argument. You rarely need to override __new__.
__init__: This is the initializer method (often called a constructor). Its job is to initialize the newly created object (returned by __new__). It takes the instance (self) as its first argument and doesn't return anything. It's where you set the initial state of the object's attributes.
In summary, __new__ creates the object, and __init__ initializes it.
Hint: Think of a car factory. __new__ is the assembly line that builds the physical car. __init__ is the part of the process where the car is filled with gas, oil, and set to its default settings before being sold.
Difficult
Question: Explain how memory management works in Python.
Answer: Python uses a combination of reference counting and a cyclic garbage collector.
Reference Counting: Every object in memory has a reference count, which is the number of variables or other objects that refer to it. When a reference to an object is created, its count is incremented. When a reference is deleted (e.g., goes out of scope), its count is decremented. When the reference count reaches zero, the object's memory is immediately deallocated. This is the primary mechanism.
Cyclic Garbage Collector: Reference counting alone cannot handle reference cycles (e.g., object A refers to B, and object B refers back to A). Even if nothing else refers to A and B, their reference counts will never be zero. To solve this, Python has a supplemental garbage collector that periodically runs to detect and break these cycles. It uses a generational algorithm, assuming that most objects die young, to make the process more efficient.
Hint: Python counts how many "names" point to an object. When that count is zero, the object is gone. A special collector cleans up objects that are only pointing to each other in a circle.
Question: What are metaclasses in Python? Why might you use one?
Answer: In Python, everything is an object. Classes are objects too, and they are instances of something. That "something" is a metaclass. A metaclass is the "class of a class." Just as a class defines the behavior of its instances (objects), a metaclass defines the behavior of its instances (classes). The default metaclass is type.
You might use a custom metaclass to automatically modify a class at the time of its creation. For example, you could use a metaclass to:
Enforce coding standards (e.g., all methods must have docstrings).
Automatically register a class in some registry (common in plugin or ORM frameworks).
Inject new methods or attributes into the class.
Metaclasses are an advanced feature and are often not necessary. Decorators or class inheritance can solve many of the same problems in a simpler way.
Hint: If a Class is a blueprint for an Object, a Metaclass is a blueprint for a Class. It's a way to write code that creates classes.
Question: Describe Python's descriptor protocol. How is it used?
Answer: The descriptor protocol is a way of creating objects that have special behavior when they are accessed as attributes of other objects. An object is a descriptor if it implements any of the methods __get__, __set__, or __delete__.
__get__(self, instance, owner): Called to get the attribute from the owner's instance.
__set__(self, instance, value): Called to set the attribute on the owner's instance.
__delete__(self, instance): Called to delete the attribute from the owner's instance.
This protocol is the underlying mechanism behind properties, methods, static methods, and class methods. For example, when you define a property using @property, you are creating a descriptor. When you access a function on an instance (e.g., my_obj.my_method), the __get__ method of the function object is called, which binds the function to the instance, creating a "bound method."
Hint: It's a hook that lets you control what happens when you get, set, or delete an attribute on an object. It's how Python's properties and methods work under the hood.
Follow-up: "What's the difference between a data descriptor and a non-data descriptor?"
