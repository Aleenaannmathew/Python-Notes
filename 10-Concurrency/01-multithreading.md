🟢 Multithreading in Python — Detailed Explanation
🔹 1. What is Multithreading?

Multithreading is a concurrent execution technique where multiple threads run in the same process, sharing the same memory space.

A thread is the smallest unit of execution within a process.

All threads within a process share:

Memory

File descriptors

Global variables

Threads have their own program counter, stack, and local variables.

Key Idea: Multithreading allows tasks to run seemingly simultaneously, improving I/O-bound program performance.

🔹 2. Why Multithreading?

Efficient I/O operations:

File reading/writing, network requests, database queries.

Resource sharing:

Threads share data easily within a process.

Lightweight:

Threads consume less memory than processes.

🔹 3. Python’s threading Module

Python provides the threading module to work with threads.

Creating Threads

Method 1: Using Thread with target function

import threading

def print_numbers():
    for i in range(1, 6):
        print(f"Number: {i}")

t1 = threading.Thread(target=print_numbers)
t2 = threading.Thread(target=print_numbers)

t1.start()
t2.start()

t1.join()
t2.join()


Method 2: Subclassing Thread

import threading

class MyThread(threading.Thread):
    def run(self):
        for i in range(1, 6):
            print(f"Thread {self.name}: {i}")

t1 = MyThread()
t2 = MyThread()

t1.start()
t2.start()

t1.join()
t2.join()


start() → begins thread execution.

join() → waits for thread to finish.

🔹 4. Thread Lifecycle

New → Thread is created.

Runnable → Ready to run.

Running → Executing instructions.

Waiting/Blocked → Waiting for resources or I/O.

Terminated → Thread finishes execution.

🔹 5. Thread Synchronization

Since threads share memory, race conditions can occur.

Example of Race Condition
import threading

counter = 0

def increment():
    global counter
    for _ in range(1000000):
        counter += 1

t1 = threading.Thread(target=increment)
t2 = threading.Thread(target=increment)

t1.start()
t2.start()
t1.join()
t2.join()

print("Counter:", counter)  # May not be 2000000 due to race condition

Solution: Using Lock
import threading

counter = 0
lock = threading.Lock()

def increment():
    global counter
    for _ in range(1000000):
        with lock:
            counter += 1

t1 = threading.Thread(target=increment)
t2 = threading.Thread(target=increment)

t1.start()
t2.start()
t1.join()
t2.join()

print("Counter:", counter)  # Always 2000000


Lock ensures mutual exclusion for critical sections.

Other synchronization tools:

RLock → Reentrant lock

Semaphore → Limit concurrent access

Event → Communication between threads

Condition → Advanced thread coordination

🔹 6. GIL and Multithreading

Python’s GIL allows only one thread to execute Python bytecode at a time.

Impact:

CPU-bound tasks → no real parallelism.

I/O-bound tasks → threads can release GIL, improving performance.

Tip: Use multiprocessing for CPU-bound parallelism.

🔹 7. Daemon Threads

Threads that run in the background and terminate when main program exits.

t = threading.Thread(target=print_numbers, daemon=True)
t.start()


Useful for background tasks like logging, monitoring.

🔹 8. Thread Pools (concurrent.futures)

Python provides ThreadPoolExecutor for managing multiple threads easily:

from concurrent.futures import ThreadPoolExecutor

def square(n):
    return n * n

with ThreadPoolExecutor(max_workers=3) as executor:
    results = executor.map(square, [1, 2, 3, 4, 5])

print(list(results))  # [1, 4, 9, 16, 25]


Advantages: Simple thread management, better resource handling.

🔹 9. Advantages of Multithreading

Efficient for I/O-bound tasks.

Less memory overhead than processes.

Faster context switching than processes.

🔹 10. Disadvantages of Multithreading

GIL limits CPU-bound performance in CPython.

Race conditions if shared resources are not synchronized.

Debugging is harder due to concurrency issues.

🔹 11. Summary

Multithreading: Multiple threads in a single process sharing memory.

Ideal for I/O-bound applications.

Requires synchronization mechanisms for shared resources.

GIL restricts CPU-bound concurrency; use multiprocessing if needed.