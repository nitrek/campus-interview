# Question Bank: Object-Oriented Programming (OOPs)

This section covers fundamental concepts of Object-Oriented Programming. These questions are common in interviews to test your core computer science knowledge.

---

## **Easy**

### **Question:** What are the four main pillars of OOPs?

**Answer:**  
The four main pillars are:

- **Encapsulation:** The bundling of data (attributes) and methods (functions) that operate on the data into a single unit or class. It restricts direct access to some of an object's components.
- **Abstraction:** Hiding complex implementation details and showing only the essential features of the object. It's about simplifying a complex system by modeling classes appropriate to the problem.
- **Inheritance:** A mechanism where a new class (subclass or derived class) inherits properties and behaviors (methods) from an existing class (superclass or base class). It promotes code reusability.
- **Polymorphism:** The ability of an object to take on many forms. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object. It allows a single action to be performed in different ways (e.g., method overriding).

**Hint:**  
- Encapsulation is like a capsule with medicine inside.  
- Abstraction is like a TV remote—you know what the buttons do but not how they work internally.  
- Inheritance is like a child inheriting traits from a parent.  
- Polymorphism means "many forms."  

---

### **Question:** What is the difference between a class and an object?

**Answer:**  
- **Class:** A class is a blueprint or a template for creating objects. It defines a set of attributes and methods that the created objects will have.  
  *Example:* A `Car` class can define properties like `color` and `maxSpeed`.  

- **Object:** An object is an instance of a class. It is a concrete entity created from the class blueprint that has actual values for the attributes.  
  *Example:* `myBlueCar` could be an object of the `Car` class with `color = "blue"`.  

**Hint:**  
Think of a cookie cutter (class) and the cookies it makes (objects).

---

## **Medium**

### **Question:** Explain the difference between method overloading and method overriding.

**Answer:**  
- **Method Overloading (Compile-time Polymorphism):** Occurs when two or more methods in the same class have the same name but different parameters (either different number of arguments, or different types of arguments, or both). The correct method to call is decided at compile time.  
- **Method Overriding (Run-time Polymorphism):** Occurs when a subclass has a method with the same name, parameters, and return type as a method in its superclass. The version of the method that gets executed is determined at runtime based on the object type. It's used to provide a specific implementation of a method that is already provided by its parent class.  

**Hint:**  
- Overloading is about "loading" a method with different parameters in the same class.  
- Overriding is about a child class "riding over" or replacing a parent's method.  

**Follow-up:**  
- Can you override a private method?  
- Can you overload a static method?  

---

### **Question:** What is an abstract class? Why would you use one?

**Answer:**  
An abstract class is a class that cannot be instantiated on its own and is meant to be subclassed. It can contain both abstract methods (methods without a body) and concrete methods (methods with implementation). If a class contains at least one abstract method, the class itself must be declared abstract. Subclasses are forced to provide implementations for the abstract methods.

**Use case:**  
To create a base class template that defines a common interface and shared functionality for a group of related subclasses, while leaving some specific implementation details to the subclasses.

**Hint:**  
It's a contract. It says, "Any class that inherits from me must provide these specific methods."

**Follow-up:**  
What is the difference between an abstract class and an interface?

---

### **Question:** What is the static keyword used for in classes?

**Answer:**  
The `static` keyword means a variable or method belongs to the class itself, rather than to any specific instance (object) of the class.

- **Static Variable:** A single copy of the variable is shared among all objects of the class. If one object changes its value, the change is reflected for all other objects.  
- **Static Method:** A method that can be called on the class itself, without creating an object. Static methods can only access static variables and other static methods directly. They cannot use `this` or `super`.

**Hint:**  
Think of `studentCount` in a `Student` class. You want one count for the whole class, not one count for each student object.

**Follow-up:**  
Why can't a static method access a non-static instance variable?

---

## **Difficult**

### **Question:** Explain the concept of coupling and cohesion in OOP.

**Answer:**  
- **Coupling:** Refers to the degree of dependency between two or more classes. Low coupling is desirable, as it means a change in one class will have a minimal impact on other classes. This makes the system easier to maintain, test, and understand.  
- **Cohesion:** Refers to how closely related and focused the responsibilities of a single class or module are. High cohesion is desirable, as it means a class is designed to do one specific job well. A class with low cohesion does many unrelated tasks, making it difficult to understand and maintain.  

**Hint:**  
Aim for **High Cohesion** and **Low Coupling**.  
- High cohesion: All baking supplies in one drawer (related purpose).  
- Low coupling: Replace your toaster without rewiring the entire kitchen (independence).  

**Follow-up:**  
Can you give an example of code that has high coupling and how you would refactor it?

---

### **Question:** What are SOLID principles? Can you name and briefly explain one of them?

**Answer:**  
SOLID is an acronym for five design principles intended to make software designs more understandable, flexible, and maintainable.

- **S - Single Responsibility Principle:** A class should have only one reason to change, meaning it should have only one job.  
- **O - Open/Closed Principle:** Software entities (classes, modules, functions) should be open for extension, but closed for modification.  
- **L - Liskov Substitution Principle:** Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.  
- **I - Interface Segregation Principle:** No client should be forced to depend on methods it does not use. It's better to have many smaller, specific interfaces than one large, general-purpose interface.  
- **D - Dependency Inversion Principle:** High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details.  

**Hint:**  
Pick one you understand well, like the **Single Responsibility Principle**, and be ready to give a simple code example.

**Follow-up:**  
How does the Open/Closed principle promote better software design?

---

### **Question:** What is a virtual function and how does it enable polymorphism?

**Answer:**  
A **virtual function** (or virtual method) is a member function in a base class that you expect to be redefined (overridden) in derived classes. When you refer to a derived class object using a pointer or a reference to the base class, you can call a virtual function for that object and execute the derived class's version of the function.

This enables **runtime polymorphism**. The decision on which function to call is not made at compile time but is deferred until runtime, based on the actual type of the object being pointed to. This is typically implemented using a **virtual table (v-table)**, which is a lookup table of functions used to resolve function calls in a dynamic/late binding manner.

**Hint:**  
It's the mechanism that makes method overriding work when using base class pointers. The `virtual` keyword tells the compiler **"Wait until runtime to decide which version of this function to call."**

**Follow-up:**  
What is a pure virtual function? What is its purpose?

---
