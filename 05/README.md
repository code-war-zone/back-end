# 🧵 Backend Engineering — Month 5 (Concurrency & High‑Performance Services with Go)

This month is about true parallel thinking.
You move beyond event loops into threads, scheduling, races, and throughput engineering.

Study Mode: Full-time (6–8 hours daily)

⸻

🎯 Month 5 Goals

By the end of this month you must be able to:

- Explain concurrency vs parallelism and choose the right model
- Build high‑throughput services using Go primitives
- Detect and fix race conditions
- Reason about latency vs throughput vs memory trade‑offs
- Design idempotent, cancellation‑aware handlers

⸻

🧠 THEORY — What You MUST Know

1️⃣ Concurrency Mental Models

Understand deeply:

- Concurrency vs Parallelism
- CPU‑bound vs IO‑bound workloads
- Cooperative vs preemptive scheduling (high level)
- Work queues & fan‑out / fan‑in patterns

Be able to explain:

- Why async IO (Node) differs from multi‑threaded execution
- When adding workers improves throughput — and when it hurts

⸻

2️⃣ Go Runtime & Goroutines

Learn:

- Goroutine lifecycle & lightweight stacks
- M:N scheduling (goroutines over OS threads)
- Blocking vs non‑blocking operations
- Garbage collection impact on latency (conceptual)

⸻

3️⃣ Channels & Synchronization

Master patterns:

- Unbuffered vs buffered channels
- Select statements for multiplexing
- Worker pools
- Pipelines & backpressure

Also understand alternatives:

- Mutexes & RWMutex
- Atomic operations (conceptual)

⸻

4️⃣ Context & Cancellation

You must understand:

- Request‑scoped cancellation
- Deadlines & timeouts
- Propagating context across goroutines

Design handlers that:

- Stop work when clients disconnect
- Avoid resource leaks

⸻

5️⃣ Race Conditions & Safety

Learn to:

- Identify shared mutable state
- Use the race detector
- Design for immutability where possible

Understand consequences:

- Data corruption
- Heisenbugs under load

⸻

6️⃣ Performance Engineering Basics

Conceptual depth:

- Throughput vs latency trade‑offs
- Batching & connection pooling
- Memory allocation patterns & GC pressure
- Streaming large responses

⸻

🛠️ PRACTICAL PROJECTS — Month 5

Project 1 — High‑Performance HTTP Microservice (Go)

Build a simple but fast service.

Requirements:

- JSON endpoints with validation
- Worker‑pool for CPU‑bound tasks
- Context‑aware handlers (timeouts / cancellation)
- Structured logging

Measure:

- Requests per second
- P95 latency

⸻

Project 2 — Concurrent Pipeline

Implement a pipeline that:

- Ingests jobs (HTTP or CLI)
- Processes stages via goroutines
- Uses channels for fan‑out / fan‑in

Demonstrate:

- Backpressure when downstream is slow
- Graceful shutdown of workers

⸻

Project 3 — Race Condition Lab

Create a shared‑state bug intentionally, then:

- Reproduce under load
- Detect using -race
- Fix with channels / mutex / redesign

Document the lesson learned.

⸻

Project 4 — Load Testing & Profiling

Use a simple load generator to:

- Compare single‑thread vs worker‑pool performance
- Observe memory & CPU trends
- Profile hot paths (high level)

Write a short report:

- What limited throughput?
- What improved latency?

⸻

🎯 End‑of‑Month Mastery Test

You are ready for Month 6 if you can:

- Explain how goroutines are scheduled
- Design a safe worker pool
- Prevent basic race conditions
- Tune concurrency to balance latency and throughput

⸻

❗ Rule of Month 5

Concurrency multiplies both performance and bugs.

⸻
