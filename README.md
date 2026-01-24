# Adaptive Thread Pool Scheduler

A lightweight and efficient **C++ thread pool** designed to execute asynchronous tasks using a fixed or adaptive number of worker threads.  
This project focuses on clarity, correctness, and practical concurrency patterns used in real systems.

---

## ✨ Features

- **Thread Pool Abstraction** – Reuses worker threads to avoid repeated thread creation overhead  
- **Asynchronous Task Execution** – Submit callable tasks and retrieve results via futures  
- **Static & Dynamic Worker Management** – Supports fixed-size pools and pools that adapt to workload  
- **Graceful Shutdown** – Ensures all queued tasks are completed before termination  
- **Header-only Design** – Easy to integrate into existing C++ projects  

---

## 🛠️ Design Overview

The system follows a classic **producer–consumer** model:

- Producers submit tasks to a shared task queue  
- Worker threads continuously fetch and execute tasks  
- Synchronization ensures thread safety while minimizing contention  

Two execution strategies are supported:
- **Static Pool**: Fixed number of workers, ideal for predictable workloads  
- **Dynamic Pool**: Adjusts worker count based on task pressure  

---

## 🚀 Example Usage

```cpp
#include "thread_pool.hpp"

int main() {
    ThreadPool pool(4);

    auto result = pool.enqueue([] {
        return 42;
    });

    std::cout << result.get() << std::endl;
}
```

---

## 📊 Performance Notes

- Designed to scale with available CPU cores  
- Throughput improves with parallelizable workloads  
- Performance plateaus once CPU saturation or synchronization overhead dominates  

Benchmarks can be extended to evaluate performance across different task sizes and thread counts.

---

## 🔍 Future Improvements

- Task prioritization  
- Work-stealing between worker threads  
- Bounded queues with backpressure  
- Better instrumentation and profiling hooks  

---

## 📚 Learning Goals

This project was built to strengthen understanding of:
- Thread pools and task scheduling  
- C++ concurrency primitives  
- Performance trade-offs in multithreaded systems  

---

## 📄 License

This project is intended for learning and demonstration purposes.
