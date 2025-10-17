🟢 Multiprocessing in Python — Detailed Explanation
🔹 1. What is Multiprocessing?

Multiprocessing is a technique where multiple processes run independently and concurrently, each with its own memory space.

A process is an independent program in execution.

Each process has:

Its own memory space

Program counter, stack, and data

System resources (file descriptors, etc.)

Key Idea: Multiprocessing allows true parallelism, taking full advantage of multiple CPU cores.

🔹 2. Why Multiprocessing?

Overcomes Python’s GIL limitation in CPU-bound tasks.

Useful for parallel computation, data processing, and heavy CPU workloads.

Each process runs independently, so crashes in one process don’t affect others.

🔹 3. Python’s multiprocessing Module

Python provides the multiprocessing module for creating and managing processes.

Creating Processes

Method 1: Using Process with target function

from multiprocessing import Process

def print_numbers():
    for i in range(1, 6):
        print(f"Number: {i}")

if __name__ == "__main__":
    p1 = Process(target=print_numbers)
    p2 = Process(target=print_numbers)

    p1.start()
    p2.start()

    p1.join()
    p2.join()


Method 2: Subclassing Process

from multiprocessing import Process

class MyProcess(Process):
    def run(self):
        for i in range(1, 6):
            print(f"Process {self.name}: {i}")

if __name__ == "__main__":
    p1 = MyProcess()
    p2 = MyProcess()

    p1.start()
    p2.start()

    p1.join()
    p2.join()

🔹 4. Process vs Thread
Feature	Thread	Process
Memory	Shared	Separate
GIL	Present (CPython)	Not affected
Overhead	Low	High
Crash impact	Can affect all threads	Independent
Suitable for	I/O-bound tasks	CPU-bound tasks
🔹 5. Inter-Process Communication (IPC)

Processes do not share memory, so communication requires special mechanisms:

a) Using Queue
from multiprocessing import Process, Queue

def square(n, q):
    q.put(n * n)

if __name__ == "__main__":
    q = Queue()
    p = Process(target=square, args=(5, q))
    p.start()
    p.join()
    print(q.get())  # 25

b) Using Pipe
from multiprocessing import Process, Pipe

def send_data(conn):
    conn.send([1, 2, 3])
    conn.close()

if __name__ == "__main__":
    parent_conn, child_conn = Pipe()
    p = Process(target=send_data, args=(child_conn,))
    p.start()
    print(parent_conn.recv())  # [1, 2, 3]
    p.join()

🔹 6. Shared Memory

Python provides Value and Array to share data between processes:

from multiprocessing import Process, Value, Array

def modify_data(n, arr):
    n.value += 10
    for i in range(len(arr)):
        arr[i] += 1

if __name__ == "__main__":
    num = Value('i', 5)
    arr = Array('i', [1, 2, 3])

    p = Process(target=modify_data, args=(num, arr))
    p.start()
    p.join()

    print(num.value)  # 15
    print(arr[:])     # [2, 3, 4]


'i' → integer type code

'd' → double type code

🔹 7. Process Pools

Pool allows managing multiple worker processes easily:

from multiprocessing import Pool

def square(n):
    return n * n

if __name__ == "__main__":
    with Pool(3) as p:
        results = p.map(square, [1, 2, 3, 4, 5])
    print(results)  # [1, 4, 9, 16, 25]


map → distributes tasks across processes.

Pool is efficient for batch processing.

🔹 8. Daemon Processes

Processes that run in the background and terminate when the main program exits.

p = Process(target=print_numbers, daemon=True)
p.start()

🔹 9. Advantages of Multiprocessing

Achieves true parallelism.

Overcomes GIL limitation.

Each process is isolated, increasing robustness.

Ideal for CPU-intensive tasks.

🔹 10. Disadvantages of Multiprocessing

Higher memory usage than threads.

Inter-process communication is slower.

Process creation overhead can be high.

Debugging is harder due to multiple independent processes.

🔹 11. Summary

Multiprocessing runs multiple processes concurrently with separate memory.

CPU-bound tasks benefit from multiprocessing.

Use Queues, Pipes, Value, and Array for sharing data.

Threading is better for I/O-bound tasks, multiprocessing is better for CPU-bound tasks.