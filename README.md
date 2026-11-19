# Threads and Multithreading Laboratory

## Student Information
- Name: Michael Cadiz
- Section: B186
- Date: November 19, 2026

## Laboratory Description
This laboratory demonstrates thread creation,
multithreading, thread coordination, and
shared-resource management using Python.

## Completed Tasks
1. Single Thread
2. Multiple Threads
3. Thread Synchronization using join()
4. Shared Resource Management using Lock()

## Learning Outcomes
- Create and execute threads.
- Demonstrate concurrent execution.
- Explain thread coordination.
- Apply locks to protect shared resources.

---

## Lab Guide Questions & Simplified Answers

### Part 2: Task 1 – Single Thread
1. **What is the purpose of `threading.Thread()`?**
   - It initializes a new thread object and designates the target function for that thread to execute.
2. **What happens when `start()` is executed?**
   - It begins the thread's execution in the background by calling its target function.
3. **What is the purpose of `join()`?**
   - It makes the calling thread (main program) wait until the worker thread has completely finished.
4. **What happens if `join()` is removed?**
   - The main program will not wait; it proceeds immediately to print `"Program completed."` while the background thread is still running.

---

### Part 3: Task 2 – Multiple Threads
1. **How many threads are created in the program?**
   - Two worker threads (`t1` and `t2`), plus the default main thread (3 threads total).
2. **Do the two threads execute independently?**
   - Yes, both threads run concurrently and independently of each other.
3. **Why might the output order change when the program is executed again?**
   - Because thread scheduling is controlled by the operating system, which dynamically decides thread execution order and time slicing.
4. **What is the difference between sequential and concurrent execution?**
   - **Sequential:** Tasks execute strictly one after another in order.
   - **Concurrent:** Tasks overlap in their execution period, making progress together.

---

### Part 4: Task 3 – Thread Synchronization Using `join()`
1. **Why does the main program wait when `join()` is used?**
   - `join()` blocks execution of the main thread until the target worker thread completes.
2. **What happens when `join()` is removed?**
   - The main program executes without waiting, printing `"Main program continues."` before `"Download completed."`.
3. **In what situations is thread synchronization necessary?**
   - When subsequent operations require results from a thread, or when coordinating multiple threads accessing common resources.

---

### Part 5: Task 4 – Managing Shared Resources Using Locks
1. **What is a shared resource?**
   - Any data, variable, memory, or file accessed concurrently by more than one thread.
2. **What is a race condition?**
   - A situation where multiple threads read and write shared data at the same time, leading to unexpected, corrupted, or incorrect values.
3. **What is the purpose of `threading.Lock()`?**
   - It provides mutual exclusion (mutex), ensuring only one thread can execute a critical section at any given time.
4. **What is a critical section?**
   - The specific part of the code that accesses or modifies shared resources (e.g., `counter += 1`).
5. **Why is synchronization important when multiple threads access shared data?**
   - It prevents data corruption and lost updates by guaranteeing atomic operations.

---

### Section VII: General Questions
1. **What is the difference between a process and a thread?**
   - A **process** is an independent executing program with its own private memory address space. A **thread** is a lightweight unit of execution within a process that shares memory and resources with other threads in that same process.
2. **What are the advantages of using multithreading?**
   - Improved responsiveness, efficient CPU and I/O utilization, faster handling of I/O-bound tasks, and seamless data sharing.
3. **How does multithreading improve application responsiveness?**
   - Time-consuming tasks (such as downloads or file I/O) run in background threads, keeping the main thread and user interface responsive without freezing.
4. **What is the difference between concurrency and parallelism?**
   - **Concurrency:** Managing and making progress on multiple tasks over overlapping periods (can occur on 1 CPU core via time-slicing).
   - **Parallelism:** Executing multiple tasks simultaneously at the exact same physical instant (requires multiple CPU cores).
5. **Why is a lock necessary when multiple threads access shared data?**
   - Incrementing data involves multiple steps (read, modify, write). A lock makes these steps atomic so threads do not overwrite each other's changes.
6. **What might happen if a thread is not properly synchronized?**
   - Race conditions, data corruption, lost updates, or deadlocks.
7. **Can multiple threads execute simultaneously on a single-core processor? Explain.**
   - No physical simultaneity. On a single core, threads execute concurrently through rapid time-slicing (the CPU switches between threads quickly to simulate simultaneous execution).
8. **How does the operating system manage kernel-level threads?**
   - The OS kernel maintains Thread Control Blocks (TCBs), handles context switches, and schedules threads directly onto available CPU cores.
