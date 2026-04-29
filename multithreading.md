# Multithreading in Java — Deep Dive (OS + JVM + Practical)

---

## 1. What is a Thread?

A **thread** is the smallest unit of execution within a process.

- A **process** = independent program (own memory space)
- A **thread** = lightweight unit inside a process (shares memory with other threads)

### Key Idea:

```
Process → Resource container
Thread  → Execution unit
```

---

## 2. Why Multithreading?

### Benefits:

- Parallelism (true on multi-core CPUs)
- Concurrency (efficient use of CPU)
- Better responsiveness (UI apps)
- Throughput improvement (servers, APIs)

---

## 3. OS-Level Understanding

### 3.1 Threads at OS Level

Threads are managed by the OS scheduler.

Each thread has:

- Program Counter (PC)
- Stack
- Registers

Shared between threads:

- Heap memory
- Code segment
- Open files

---

### 3.2 Context Switching

When CPU switches between threads:

Steps:

1. Save current thread state (registers, PC)
2. Load next thread state
3. Resume execution

⚠️ Costly operation → too many threads = performance drop

---

### 3.3 Scheduling

OS uses scheduling algorithms:

- Round Robin
- Priority-based
- Preemptive scheduling

Java threads map to native OS threads → JVM relies on OS scheduler.

---

## 4. Java Thread Model

Java uses **1:1 thread model**:

```
1 Java Thread → 1 OS Thread
```

So:

- Real parallelism possible
- OS handles scheduling

---

## 5. Creating Threads in Java

### 5.1 Extending Thread Class

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running");
    }
}

MyThread t = new MyThread();
t.start();  // NOT run()
```

---

### 5.2 Implementing Runnable (Preferred)

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable thread");
    }
}

Thread t = new Thread(new MyRunnable());
t.start();
```

---

### 5.3 Using Lambda

```java
Thread t = new Thread(() -> {
    System.out.println("Lambda thread");
});
t.start();
```

---

## 6. Thread Lifecycle

```
NEW → RUNNABLE → RUNNING → BLOCKED/WAITING → TERMINATED
```

### States:

- **NEW**: created, not started
- **RUNNABLE**: ready to run
- **RUNNING**: executing
- **BLOCKED**: waiting for lock
- **WAITING**: waiting indefinitely
- **TIMED_WAITING**: waiting for time
- **TERMINATED**: finished execution

---

## 7. Thread Methods

```java
t.start();        // starts thread
t.run();          // just method call (no new thread)
t.sleep(ms);      // pause thread
t.join();         // wait for thread to finish
t.yield();        // hint scheduler
t.interrupt();    // signal interruption
```

---

## 8. Concurrency vs Parallelism

| Concept     | Meaning                      |
| ----------- | ---------------------------- |
| Concurrency | Multiple tasks interleaved   |
| Parallelism | Tasks running simultaneously |

---

## 9. Shared Memory Problem

Threads share heap → leads to:

- Race conditions
- Data inconsistency

---

## 10. Race Condition

```java
int counter = 0;

Thread t1 = new Thread(() -> counter++);
Thread t2 = new Thread(() -> counter++);
```

Expected: 2
Actual: 1 (due to overlap)

---

## 11. Synchronization

### 11.1 Synchronized Method

```java
synchronized void increment() {
    counter++;
}
```

### 11.2 Synchronized Block

```java
synchronized(this) {
    counter++;
}
```

### Internal Mechanism:

- Uses **monitor lock (intrinsic lock)**
- Only one thread enters at a time

---

## 12. Locks in Depth (OS + JVM)

Each object has a **monitor lock**:

```
Thread tries → acquire lock → execute → release lock
```

If lock is held:

- Thread goes to BLOCKED state

---

## 13. Volatile Keyword

```java
volatile boolean flag = true;
```

### Guarantees:

- Visibility (latest value seen by all threads)
- No caching

### Does NOT guarantee:

- Atomicity

---

## 14. Atomic Operations

Use `AtomicInteger`:

```java
AtomicInteger count = new AtomicInteger(0);
count.incrementAndGet();
```

Internally uses:

- CAS (Compare And Swap)
- Lock-free programming

---

## 15. Inter-Thread Communication

### wait() / notify()

```java
synchronized(obj) {
    obj.wait();
}

synchronized(obj) {
    obj.notify();
}
```

### Flow:

- Thread releases lock and waits
- Another thread notifies
- Waiting thread resumes

---

## 16. Deadlock

### Condition:

1. Mutual exclusion
2. Hold and wait
3. No preemption
4. Circular wait

### Example:

```java
Thread 1 → lock A → wait for B
Thread 2 → lock B → wait for A
```

💥 System stuck forever

---

## 17. Thread Pools (Executor Framework)

Instead of creating threads manually:

```java
ExecutorService executor = Executors.newFixedThreadPool(5);

executor.submit(() -> {
    System.out.println("Task");
});

executor.shutdown();
```

### Benefits:

- Reuse threads
- Avoid overhead
- Controlled concurrency

---

## 18. Callable vs Runnable

| Feature   | Runnable | Callable |
| --------- | -------- | -------- |
| Return    | No       | Yes      |
| Exception | No       | Yes      |

```java
Callable<Integer> task = () -> 10;

Future<Integer> result = executor.submit(task);
System.out.println(result.get());
```

---

## 19. Future & Async

```java
Future<Integer> f = executor.submit(() -> 5);
int result = f.get(); // blocking
```

---

## 20. Modern Concurrency (Java 8+)

### CompletableFuture

```java
CompletableFuture.supplyAsync(() -> 10)
    .thenApply(x -> x * 2)
    .thenAccept(System.out::println);
```

---

## 21. Memory Model (JMM)

Defines:

- How threads interact with memory
- Visibility rules
- Happens-before relationship

### Key Concept:

```
Thread A writes → Main Memory → Thread B reads
```

---

## 22. Happens-Before Rules

Ensures order & visibility:

- Lock release → lock acquire
- Thread start → thread execution
- Write to volatile → read volatile

---

## 23. CPU-Level Reality (Very Important)

### Problem:

CPU caches values → threads may not see updates

### Solution:

- `volatile`
- `synchronized`
- Memory barriers

---

## 24. Performance Considerations

### Avoid:

- Too many threads
- Excessive synchronization

### Prefer:

- Thread pools
- Lock-free structures
- Async programming

---

## 25. When NOT to Use Multithreading

- CPU-bound with limited cores
- Simple sequential tasks
- Heavy locking scenarios

---

## 26. Summary

- Threads = execution units
- Java uses OS threads
- Synchronization prevents race conditions
- JMM ensures visibility
- Executors improve scalability

---

## 27. Interview-Level Understanding (What You Should Be Able to Explain)

- Difference between process & thread
- How synchronization works internally
- What is JMM
- Difference between volatile & synchronized
- How thread pools work
- What is deadlock & how to prevent it
- CAS vs locking

---

If you want, next I can:

- Give **real-world backend examples (like your Firebase/login rewards system) using multithreading**
- Or **deep dive into JVM internals (locks, biased locking, spin locks, etc.)**
- Or **DSA + multithreading interview questions**

Just tell me 👍
