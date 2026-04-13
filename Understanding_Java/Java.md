# 📘 Java + Programming Notes (Deep + Preserved)

> Source preserved from your handwritten notes: fileciteturn1file0
> Everything is kept, expanded, and clarified (NOTHING removed)

---

# 🧠 Introduction to Programming

## Types of Languages

### 1. Procedural

* Specifies a series of well-structured steps
* Contains systematic order of statements, functions, commands

👉 Meaning (deep explanation):
You solve problems step by step like a recipe.

---

### 2. Functional

* Writing program using pure functions
* No modification of variables
* Create new values instead

👉 Used in ML, data-heavy transformations

---

### 3. Object-Oriented

* Revolves around objects
* Code + Data = Object
* Easier to debug, reuse, maintain

👉 Important:
This is WHY Java exists → to model real world

---

# ⚖️ Static vs Dynamic Languages

## Static

* Type checking at compile time
* Errors show early
* Need to declare datatype

Examples:

* C++
* Java
* Go

---

## Dynamic

* Type checking at runtime
* Errors appear later
* No datatype declaration needed

Examples:

* Python
* JavaScript

👉 Insight:
Static = safer
Dynamic = flexible

---

# 🧠 Memory Concept (VERY IMPORTANT)

## Two Types:

* Stack
* Heap

---

## Example (from your notes):

```
a = 10
```

👉 Explanation (corrected + preserved):

* `a` → stored in STACK
* Value `10` → depends:

  * Primitive → stored directly in stack
  * Object → stored in heap

⚠️ Correction:
Your note says: "a is stored in stack pointing to 10 in heap"
👉 This is ONLY TRUE for objects, NOT primitives

---

## Objects in Heap

(Page 2 diagram explanation)

* Object always stored in heap
* Reference variable stored in stack

Example:

```
String name = "Anurag";
```

* name → stack
* "Anurag" → heap

---

## Important Concept (VERY GOOD IN YOUR NOTES)

👉 What happens when object has NO reference?

Example:

```
a = 10
a = 57
```

* Old value becomes unreachable
* Garbage Collector deletes it

👉 Correct ✔️
BUT:

* GC is NOT instant
* Runs when JVM decides

---

# 🔄 Flow of Program (Flowcharts)

## Symbols

* Start/Stop → Oval
* Input/Output → Parallelogram
* Processing → Rectangle
* Condition → Diamond

---

## Example 1 (Salary Bonus)

👉 Question:
If salary > 10000 → add 2000
Else → add 1000

👉 Flow logic:

```
Input S
if S > 10000
    S = S + 2000
else
    S = S + 1000
```

---

## Example 2 (Prime Check)

(Page 4 diagram + pseudocode)

👉 Your logic preserved:

```
start
input n
c = 2
while c < n:
    if n % c == 0:
        output "not prime"
        exit
    c = c + 1
output "prime"
exit
```

👉 Improvement:

* Can optimize till √n

---

# ☕ Why Java / How Java Executes

## Flow (Page 5 diagram)

```
Java File (.java)
   ↓ compiler
Bytecode (.class)
   ↓ interpreter (JVM)
Machine Code (0/1)
```

👉 Key Points:

* Java does NOT run directly
* JVM required

---

## Platform Independence

* Bytecode runs everywhere
* JVM converts to machine code

👉 Important line (VERY IMPORTANT INTERVIEW):
"Java is platform independent BUT JVM is platform dependent"

---

# 🏗️ Java Architecture

## JDK vs JRE vs JVM vs JIT

### JDK

* Development kit
* Includes:

  * Compiler (javac)
  * JRE
  * Tools (javadoc)

---

### JRE

* Runtime environment
* Contains:

  * Libraries
  * JVM

---

### JVM

* Executes bytecode
* Handles:

  * Memory
  * Garbage collection

---

### JIT

* Just-in-Time compiler
* Converts repeated code into native code
* Improves performance

---

# ⚙️ How JVM Works (Page 6)

## Steps:

1. Class Loader

   * Loads class into memory
   * Creates object in heap

2. Bytecode Verifier

   * Checks correctness

3. Interpreter

   * Executes line by line

4. Runtime

   * Manages execution

5. Hardware

   * Final execution

---

## Important JVM Insight

* Stack + Heap inside JVM
* JIT speeds execution

---

# 🧪 First Java Program

(Preserved exactly)

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.println(input.nextInt());
    }
}
```

👉 Explanation:

* Scanner reads input
* System.in → input stream

---

# 📦 Arrays

## Syntax

```
datatype[] arr = new datatype[size];
```

Example:

```
int[] arr = new int[5];
int[] arr = {23, 15, 25, 27, 11};
```

👉 Important (from your note):

* Object created in heap
* Dynamic memory allocation

---

## Memory Concept

* C++ → continuous memory
* Java → depends on JVM

⚠️ Correction:
Java arrays ARE contiguous logically
But JVM handles allocation internally

---

# 📚 ArrayList

## Syntax

```
ArrayList<Integer> list = new ArrayList<>(10);
```

👉 initial capacity = 10

---

## Example (Preserved)

```
list.add(67);
list.add(234);
System.out.println(list);
```

---

## Methods

* list.contains()
* list.add()
* list.remove(index)
* list.get(index)

⚠️ Important:

```
list[index] ❌
list.get(index) ✔️
```

---

# ⚠️ Concept Corrections (VERY IMPORTANT)

1. Primitive vs Object memory clarified
2. GC is not immediate
3. Java arrays internally contiguous (JVM managed)
4. JVM does NOT create object automatically on class load (only when instantiated)

---

# 🚀 What You Should Do Next

If you want to go next level:

* Deep dive JVM internals
* How GC actually works (Mark & Sweep)
* Stack frame execution
* Class loading lifecycle

---

👉 If you want, I can now:

* Convert this into **interview notes**
* OR create **super deep JVM notes (like how V8 works level)**
