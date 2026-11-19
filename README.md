# Threads and Multithreading Laboratory

## Student Information
- Name: Michael Cadiz
- Section: 
- Date: November 19, 2026

## Laboratory Description
This laboratory demonstrates thread creation, multithreading, thread coordination, and shared-resource management using Python.

## Completed Tasks
1. Single Thread (`task1_single_thread.py`)
2. Multiple Threads (`task2_multiple_threads.py`)
3. Thread Synchronization using join() (`task3_thread_synchronization.py`)
4. Shared Resource Management using Lock() (`task4_thread_lock.py`)

## Learning Outcomes
- Create and execute threads.
- Demonstrate concurrent execution.
- Explain thread coordination.
- Apply locks to protect shared resources.

---

## Lab Guide Questions & Simplified Answers

### Part 2: Task 1 – Single Thread
1. **What is the purpose of `threading.Thread()`?**
   - It creates a new thread object and defines what target function the thread will run.
2. **What happens when `start()` is executed?**
   - It begins the thread's execution by calling its target function in a separate thread of control.
3. **What is the purpose of `join()`?**
   - It blocks the calling thread (main program) until the target thread finishes executing.
4. **What happens if `join()` is removed?**
   - The main program will not wait; it continues running and may finish before the thread finishes its work.

---

### Part 3: Task 2 – Multiple Threads
1. **How many threads are created in the program?**
   - Two worker threads (`t1` and `t2`), in addition to the main thread (total of 3 threads).
2. **Do the two threads execute independently?**
   - Yes, both threads run concurrently and independently of each other.
3. **Why might the output order change when the program is executed again?**
   - Because thread scheduling is controlled by the operating system, which can switch between threads at unpredictable times.
4. **What is the difference between sequential and concurrent execution?**
   - **Sequential:** Tasks run one after another in order.
   - **Concurrent:** Tasks overlap in their execution time and make progress together.

---

### Part 4: Task 3 – Thread Synchronization Using `join()`
1. **Why does the main program wait when `join()` is used?**
   - `join()` pauses the main program's flow until the target thread completely terminates.
2. **What happens when `join()` is removed?**
   - The main program continues executing immediately, causing "Main program continues" to print before the download finishes.
3. **In what situations is thread synchronization necessary?**
   - When a program depends on data or results from a thread before moving to the next step, or when multiple threads access shared resources.

---

### Part 5: Task 4 – Managing Shared Resources Using Locks
1. **What is a shared resource?**
   - Any data, variable, memory, or device accessed and used by more than one thread simultaneously.
2. **What is a race condition?**
   - A bug where two or more threads access and modify shared data concurrently, causing unpredictable or corrupted results depending on execution order.
3. **What is the purpose of `threading.Lock()`?**
   - It provides mutual exclusion (mutex), ensuring only one thread can access a critical section at a time.
4. **What is a critical section?**
   - The part of a program where shared resources are accessed or modified.
5. **Why is synchronization important when multiple threads access shared data?**
   - It prevents data corruption and lost updates by ensuring coordinated, atomic access to shared variables.

---

### Section VII: General Questions
1. **What is the difference between a process and a thread?**
   - A **process** is an independent executing program with its own dedicated memory space. A **thread** is a lightweight sub-unit of execution within a process that shares memory and resources with other threads in that process.
2. **What are the advantages of using multithreading?**
   - Improved responsiveness, efficient CPU and I/O utilization, faster execution of I/O-bound tasks, and easy sharing of memory/data within a process.
3. **How does multithreading improve application responsiveness?**
   - Heavy or blocking tasks (like downloads or computations) can run in background threads, keeping the main thread (or UI) free to respond to user input.
4. **What is the difference between concurrency and parallelism?**
   - **Concurrency:** Handling and making progress on multiple tasks over overlapping periods (interleaving on 1 or more cores).
   - **Parallelism:** Executing multiple tasks at the exact same physical instant (requires multiple CPU cores).
5. **Why is a lock necessary when multiple threads access shared data?**
   - Because operations (like `counter += 1`) involve multiple steps (read, modify, write). A lock makes these steps atomic so threads don't overwrite each other's changes.
6. **What might happen if a thread is not properly synchronized?**
   - Race conditions, data corruption, lost updates, deadlocks, or inconsistent program states.
7. **Can multiple threads execute simultaneously on a single-core processor? Explain.**
   - No, not in true physical simultaneity. On a single core, threads execute *concurrently* through rapid time-slicing (the CPU switches between threads so fast it creates the illusion of simultaneous execution).
8. **How does the operating system manage kernel-level threads?**
   - The OS kernel maintains thread control blocks (TCBs), schedules threads directly onto available CPU cores, handles context switching, and manages thread synchronization primitives.
