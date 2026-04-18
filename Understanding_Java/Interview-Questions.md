# Java Interviewer Favorite Questions (With Answers & Explanations)

---

## 1. What is the difference between JDK, JRE, and JVM?

### Answer:

* **JDK (Java Development Kit)**: Full package used for development (includes JRE + tools like compiler).
* **JRE (Java Runtime Environment)**: Provides libraries and environment to run Java programs.
* **JVM (Java Virtual Machine)**: Executes Java bytecode and provides platform independence.

### Explanation:

Think of it like:

* JVM → Engine
* JRE → Engine + Fuel
* JDK → Full Car (for building + running)

---

## 2. What is OOP? Explain its principles.

### Answer:

OOP (Object-Oriented Programming) is a paradigm based on objects.

#### 4 Principles:

1. **Encapsulation** – Wrapping data + methods together
2. **Abstraction** – Hiding implementation details
3. **Inheritance** – Reusing code from parent class
4. **Polymorphism** – Many forms (method overloading/overriding)

### Explanation:

OOP helps in writing modular, reusable, and maintainable code.

---

## 3. Difference between == and equals()?

### Answer:

* `==` → compares references (memory address)
* `equals()` → compares actual content

### Example:

```java
String a = new String("hello");
String b = new String("hello");

System.out.println(a == b);       // false
System.out.println(a.equals(b));  // true
```

### Explanation:

Always use `.equals()` for object value comparison.

---

## 4. What is String immutability?

### Answer:

Strings in Java are immutable, meaning once created, they cannot be changed.

### Example:

```java
String s = "hello";
s.concat(" world"); // new object created
```

### Explanation:

Benefits:

* Thread-safe
* Secure
* Efficient (String pool optimization)

---

## 5. What is method overloading vs overriding?

### Answer:

| Feature         | Overloading  | Overriding        |
| --------------- | ------------ | ----------------- |
| Same class      | Yes          | No (parent-child) |
| Parameters      | Different    | Same              |
| Runtime/Compile | Compile-time | Runtime           |

### Explanation:

* Overloading → same method name, different args
* Overriding → redefining parent method

---

## 6. What is the difference between ArrayList and LinkedList?

### Answer:

| Feature   | ArrayList     | LinkedList         |
| --------- | ------------- | ------------------ |
| Structure | Dynamic array | Doubly linked list |
| Access    | Fast (O(1))   | Slow (O(n))        |
| Insertion | Slow          | Fast               |

### Explanation:

Use:

* ArrayList → frequent reads
* LinkedList → frequent inserts/deletes

---

## 7. What is HashMap? How does it work?

### Answer:

HashMap stores key-value pairs and allows fast access using hashing.

### Internal Working:

1. Key's `hashCode()` is calculated
2. Hash is converted to index
3. Value is stored in bucket
4. Collisions handled using LinkedList / Tree

### Example:

```java
HashMap<Integer, String> map = new HashMap<>();
map.put(1, "Anurag");
map.get(1);
```

### Explanation:

Average complexity → **O(1)** for get/put

---

## 8. What is multithreading?

### Answer:

Multithreading allows multiple threads to run concurrently.

### Example:

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running");
    }
}
```

### Explanation:

Used for:

* Parallel execution
* Better CPU utilization

---

## 9. What is synchronization?

### Answer:

Synchronization is used to control access to shared resources.

### Example:

```java
synchronized void print() {
    // critical section
}
```

### Explanation:

Prevents race conditions in multithreading.

---

## 10. What is Exception Handling?

### Answer:

Mechanism to handle runtime errors.

### Keywords:

* try
* catch
* finally
* throw
* throws

### Example:

```java
try {
    int a = 10 / 0;
} catch (Exception e) {
    System.out.println(e);
}
```

### Explanation:

Helps in maintaining program flow even after errors.

---

## Pro Tips (Interview Perspective)

* Always give **real-world analogy**
* Write **small code snippets**
* Mention **time complexity where possible**
* Speak clearly and structured

---

---

# 🔥 FAANG-Level Tricky Java Questions

## 11. Why is String immutable but StringBuilder is mutable?

### Answer:

* String → Immutable (cannot change)
* StringBuilder → Mutable (can change without new object)

### Explanation:

* String is used in security-sensitive areas (e.g., class loading, networking)
* Immutability ensures thread safety and caching (String pool)
* StringBuilder is optimized for performance in frequent modifications

---

## 12. What happens internally when you use "String s = "abc";"?

### Answer:

* Stored in **String Constant Pool**
* If already exists → reference reused
* Else → new object created

### Explanation:

This saves memory and improves performance.

---

## 13. Difference between HashMap and ConcurrentHashMap?

### Answer:

* HashMap → Not thread-safe
* ConcurrentHashMap → Thread-safe

### Explanation:

* HashMap can cause race conditions
* ConcurrentHashMap uses segment locking / CAS for better performance

---

## 14. What is the difference between fail-fast and fail-safe iterators?

### Answer:

* Fail-fast → Throws exception if collection modified (e.g., ArrayList)
* Fail-safe → Works on clone (e.g., ConcurrentHashMap)

### Explanation:

Fail-fast detects bugs early, fail-safe avoids crashes.

---

## 15. What is memory leak in Java?

### Answer:

Memory leak occurs when objects are no longer needed but still referenced.

### Explanation:

Even though Java has GC, leaks happen due to:

* Static collections
* Unclosed resources

---

## 16. Why HashMap is not thread-safe?

### Answer:

Because multiple threads can modify structure simultaneously.

### Explanation:

This can lead to:

* Infinite loops (older versions)
* Data inconsistency

---

## 17. What is the difference between final, finally, and finalize?

### Answer:

* final → keyword (constant / restriction)
* finally → block (always executes)
* finalize → method (called by GC)

---

## 18. Explain Java Memory Model (JMM)

### Answer:

Defines how threads interact with memory.

### Explanation:

* Stack → Thread specific
* Heap → Shared
* Ensures visibility + ordering

---

## 19. What is volatile keyword?

### Answer:

Ensures visibility of variable across threads.

### Explanation:

* Prevents caching
* Does NOT guarantee atomicity

---

## 20. What is difference between Comparable and Comparator?

### Answer:

* Comparable → natural ordering (inside class)
* Comparator → custom ordering (external)

### Example:

```java
Collections.sort(list, (a, b) -> a.age - b.age);
```

---

## 🔥 Interview Insight (Very Important)

In FAANG interviews, they expect:

* "Why" more than "What"
* Internal working (HashMap, JVM, Threads)
* Trade-offs discussion

If you only give definition → ❌ Reject
If you explain internal working → ✅ Strong hire signal

---


# Java Interviewer Favorite Questions (Deep Explanation Version)

---

## 21. How does HashMap handle collisions internally?

### Answer:

When two keys generate the same hash index, HashMap stores them in the same bucket.

### Deep Explanation:

* Initially, each bucket is a LinkedList
* When multiple elements collide, they are chained together
* After Java 8, if the number of elements in a bucket exceeds 8, it converts into a Balanced Tree (Red-Black Tree)

### Why this matters:

* LinkedList → O(n)
* Tree → O(log n)

So worst-case performance improves significantly.

---

## 22. What is load factor and rehashing in HashMap?

### Answer:

Load factor defines when HashMap should resize.

### Deep Explanation:

* Default load factor = 0.75
* When size > capacity * loadFactor → resizing happens

Example:
If capacity = 16
Threshold = 16 × 0.75 = 12

After 12 elements → resize to 32

### Rehashing:

* New array is created
* All elements are reinserted
* Index recalculated

### Why important:

Too small → waste memory
Too large → slow performance

---

## 23. Why capacity is always power of 2 in HashMap?

### Answer:

To optimize index calculation.

### Deep Explanation:

HashMap uses:
index = hash & (capacity - 1)

Example:
capacity = 16 (10000)

This is much faster than modulo (%) operation.

### Why power of 2:

Ensures uniform distribution of keys.

---

## 24. What happens when two keys have same hashCode?

### Answer:

They go into the same bucket.

### Deep Explanation:

* First, hashCode() determines bucket
* Then equals() is used to compare keys

### Important:

If equals() is not overridden properly → duplicates or wrong behavior

---

## 25. Can HashMap have null key?

### Answer:

Yes, only one null key is allowed.

### Deep Explanation:

* null key always goes to bucket index 0
* Multiple null keys overwrite previous value

---

## 26. What is JVM architecture?

### Answer:

JVM consists of:

* ClassLoader
* Runtime Memory Areas
* Execution Engine

### Deep Explanation:

1. ClassLoader → loads .class files
2. Memory Areas → stores data
3. Execution Engine → executes bytecode

---

## 27. What are different memory areas in JVM?

### Answer:

* Heap
* Stack
* Method Area
* PC Register
* Native Stack

### Deep Explanation:

* Heap → Objects (shared)
* Stack → Method calls (per thread)
* Method Area → class metadata
* PC Register → current instruction

---

## 28. What is Garbage Collection?

### Answer:

Automatic memory cleanup process.

### Deep Explanation:

GC removes objects that are no longer reachable.

Example:
Object has no reference → eligible for GC

---

## 29. What are types of Garbage Collectors?

### Answer:

* Serial GC
* Parallel GC
* CMS
* G1 GC

### Deep Explanation:

* Serial → single thread
* Parallel → multiple threads
* CMS → low pause time
* G1 → best for large apps

---

## 30. What is mark-and-sweep algorithm?

### Answer:

Basic GC algorithm.

### Deep Explanation:

1. Mark phase → mark reachable objects
2. Sweep phase → delete unreachable

Problem:
Leaves memory fragmentation

---

## 31. What is memory leak in Java?

### Answer:

When unused objects are still referenced.

### Deep Explanation:

GC cannot remove them because references still exist.

Example:
Static list storing unused objects

---

## 32. What are reference types?

### Answer:

* Strong
* Weak
* Soft
* Phantom

### Deep Explanation:

* Strong → never GC
* Weak → removed quickly
* Soft → removed when memory low

---

## 33. What is Stop-The-World?

### Answer:

GC pauses all threads.

### Deep Explanation:

During GC, application stops completely.

Impact:
High latency systems suffer

---

## 34. What is JIT compiler?

### Answer:

Converts bytecode to machine code at runtime.

### Deep Explanation:

* Improves performance
* Frequently used code is optimized

---

## 35. What is classloader?

### Answer:

Loads classes into JVM.

### Deep Explanation:

Follows delegation:

* Bootstrap
* Extension
* Application

---

## 36. Heap vs Stack?

### Answer:

* Heap → objects
* Stack → execution

### Deep Explanation:

Stack is faster, heap is shared.

---

## 37. What is escape analysis?

### Answer:

Optimization technique.

### Deep Explanation:

If object does not escape method → allocate on stack

---

## 38. What is GC root?

### Answer:

Starting point of GC.

### Deep Explanation:

Includes:

* Static variables
* Thread references

---

## 39. What is generational GC?

### Answer:

Heap divided into generations.

### Deep Explanation:

* Young → short-lived objects
* Old → long-lived

Optimization:
Most objects die young

---

## 40. Minor vs Major GC?

### Answer:

* Minor → young gen
* Major → old gen

### Deep Explanation:

Minor is fast, Major is slow and expensive

---

## 🚀 Final Insight

If you truly understand THIS document:

* You can answer 90% Java interviews
* Focus on explaining WHY and INTERNALS

---


**End of Document**
