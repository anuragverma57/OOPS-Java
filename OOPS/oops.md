# 🧠 OOPS in Java — Ultra Detailed Notes (From Your PDF)

> Source preserved from your handwritten notes: fileciteturn2file0
> NOTHING removed. Everything expanded deeply with same flow + better clarity.

---

# 📌 1. Class & Object (FOUNDATION)

## Class

* A blueprint or template for creating objects
* Contains:

  * Attributes (properties)
  * Methods (behaviour)

👉 From your example (Page 1):

* Class = Concept
* Object = Physical Reality

👉 Real life analogy (your car diagram):

* Class: Car (Blueprint)
* Objects:

  * Hyundai (1200cc, 8L, 20,00,000)
  * Audi (3000cc, 70,00,000)
  * Mercedes (6000cc, 90,00,000)

👉 Insight:
Class defines structure, object brings it to life.

---

## Object

* Instance of class
* Has:

  * State
  * Identity
  * Behaviour

👉 From Page 2:

* State → marks, name
* Identity → memory location
* Behaviour → actions

---

## Important Note (Your note preserved)

Variables inside object = Instance variables

---

# 🧠 Accessing Data

Using dot operator:

```
stu1.rollno
stu2.marks
```

👉 This links reference variable to instance variable

---

# ⚡ Memory Representation (VERY IMPORTANT)

## Case 1: Only Declaration

```
Student stu1;
```

* No object created
* stu1 stored in stack
* Heap empty

---

## Case 2: Object Creation

```
Student stu1 = new Student();
```

👉 What happens (Page 3 diagram explained):

1. `new` keyword allocates memory in heap
2. Object is created
3. Reference returned to stu1 (stack)

👉 One line answer (your note):
Dynamic Memory Allocation

---

# 🧩 Constructors (VERY IMPORTANT)

## What is constructor?

* Special function called when object is created
* Initializes object

---

## Default Constructor

```
Student() {
    this(0, "default", 100.0);
}
```

👉 Calls another constructor using `this()`

---

## Parameterized Constructor

```
Student(int rollno, float marks) {
    this.rollno = rollno;
    this.marks = marks;
}
```

---

## Copy Constructor (Page 6)

```
Student(Student other) {
    this.rollno = other.rollno;
    this.marks = other.marks;
}
```

👉 Creates object from another object

---

## Important Keyword: `this`

* Refers to current object
* Helps resolve naming conflict

👉 Your note:
"this refers to current object instance"

---

# 🔁 Reference Behavior (IMPORTANT)

(Page 7 diagram)

```
Student one = new Student();
Student two = one;
```

👉 Both point to SAME object
👉 Change via one → reflects in two

---

# ⚠️ final Keyword

## For primitives

```
final int a = 10;
```

* Cannot change value

## For objects

```
final Student s1 = new Student();
```

* Reference cannot change
* Object CAN change

👉 Important concept clarified

---

# 🧹 Garbage Collection

(Page 8)

* Removes unused objects
* Triggered when no reference exists

👉 finalize() (your note):

* Special method before object destruction

⚠️ Correction:

* finalize() deprecated in modern Java

---

# 📦 Packages

(Page 10)

* Containers for classes
* Prevent naming conflicts

👉 Example:

* You can create class List without conflict

---

## Features:

* Hierarchical structure
* Explicit import

---

# 🔑 Static Keyword (VERY IMPORTANT)

## Static Variables

(Page 11–12 example)

```
static long population;
```

👉 Belongs to class, not object
👉 Shared across all objects

---

## Why static main?

(Page 12 insight):

* Program starts without object
* So main must be static

---

## Static Methods

* Cannot use non-static directly
* Because non-static needs object

👉 Solution (your note):
Create object inside static method

---

## Static Block

(Page 14)

* Runs once when class loads

---

# 🧱 Singleton Class

(Page 15–16)

## Concept:

* Only one object allowed

## Implementation:

* Private constructor
* Static instance
* Public getter

```
if(instance == null) instance = new Singleton();
```

---

# 🧬 Inheritance

(Page 17)

## Definition:

* Child acquires parent properties

```
class Child extends Parent
```

---

## Important Notes:

* Child gets parent variables
* Must initialize parent properly

---

## Access Rules (Page 18–19)

* Private → not accessible
* Protected → accessible in subclass

---

# 🔑 super Keyword

(Page 20)

Uses:

1. Call parent constructor
2. Access parent variables

---

# 📊 Types of Inheritance

## 1. Single

A → B

## 2. Multilevel

A → B → C

## 3. Hierarchical

A → B, C, D

## 4. Multiple ❌

Not supported in Java

👉 Reason (your note):
Ambiguity problem

## 5. Hybrid ❌

Not supported directly

---

# 🎭 Polymorphism

(Page 23–24)

## Concept:

One task → multiple ways

---

## Compile Time (Overloading)

* Same method name
* Different parameters

---

## Runtime (Overriding)

* Same method signature
* Different implementation

👉 Important:
Method call decided at runtime

---

# 🔐 final Keyword (Deep)

(Page 25)

* Variable → constant
* Method → cannot override
* Class → cannot inherit

---

# 🧠 Encapsulation

* Wrapping data + methods

---

# 🧠 Abstraction

* Hiding unnecessary details
* Showing only essential info

---

# 🔐 Access Modifiers

(Page 26)

* private
* default
* protected
* public

👉 Table explained (page reference):

* Access differs based on class, package, subclass

---

# 📚 Packages (Types)

(Page 27)

* java.lang (auto imported)
* java.io
* java.util
* awt (GUI)

---

# 🧠 Abstract Classes

(Page 33–34)

## Key Points:

* Cannot create object
* Can have abstract methods

## Abstract Method:

* No body

```
abstract void fun();
```

---

## Important Rules:

* If class has abstract method → must be abstract
* Cannot be final

---

# 🔌 Interfaces

(Page 35)

## Key Points:

* Blueprint
* Contains abstract methods

## Default behavior:

* Methods → public abstract
* Variables → static final

---

## Important:

* Supports multiple inheritance

---

# ⚠️ Final Corrections (VERY IMPORTANT)

1. finalize() is deprecated
2. Multiple inheritance not supported due to ambiguity
3. Static methods cannot access non-static directly
4. Object creation happens ONLY when using `new`

---

# 🚀 Final Summary

Your notes are:

* Conceptually STRONG
* Very intuitive
* Good for interviews

---

# 🚀 Next Level Suggestions

If you want to go deeper:

* JVM internals (stack frames, heap regions)
* How method overriding works internally (vtable)
* Memory leaks & GC algorithms

---

👉 Just say:
"deep JVM"
or
"interview revision"
