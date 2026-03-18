# 🧱 Backend Engineering — Month 3 (Architecture & Advanced Node.js)

This month is about structure and runtime mastery.
You will stop writing “files that work” and start designing systems that survive change.

⸻

🎯 Month 3 Goals

By the end of this month you must be able to:

- Design backend systems using clear architectural boundaries
- Apply Dependency Inversion to decouple business logic from frameworks
- Understand the Node.js runtime deeply (event loop, memory, concurrency)
- Build a production-grade API with background processing and operational safety

⸻

🧠 THEORY — What You MUST Know

1️⃣ Architectural Styles (Why Structure Matters)

Understand and compare:

- Layered Architecture — presentation / application / domain / infrastructure
- Hexagonal (Ports & Adapters) — isolate domain from IO & frameworks
- Clean Architecture principles — dependency rule, use‑cases first

You must be able to:

- Draw module boundaries
- Explain why business rules should not depend on frameworks
- Swap an adapter (e.g., database or transport) without touching domain logic

⸻

2️⃣ Dependency Inversion in Practice

Learn:

- Interfaces (contracts) for repositories & services
- Inversion via dependency injection
- Testability through mockable boundaries

Understand trade‑offs:

- Indirection cost vs long‑term maintainability
- Over‑engineering vs pragmatic seams

⸻

3️⃣ DDD Lite (Tactical Thinking)

Conceptual depth (not dogma):

- Entities vs Value Objects
- Aggregates & invariants
- Use‑cases / application services
- Ubiquitous language

You must be able to:

- Model a small domain with clear invariants
- Keep business rules centralized

⸻

4️⃣ Node.js Runtime Internals

Master the mental model:

- Event loop phases (timers, pending callbacks, poll, check, close)
- Microtasks vs macrotasks
- libuv threadpool responsibilities
- Non‑blocking IO vs CPU‑bound work

Also learn:

- Worker Threads (when and why)
- Cluster / multi‑process scaling
- Streams & backpressure
- Memory leaks (timers, closures, listeners, caches)

⸻

5️⃣ Operational Safety Basics

You must understand:

- Graceful shutdown (SIGTERM handling)
- Health checks & readiness probes
- Timeouts & cancellation patterns
- Structured logging concepts

⸻

🛠️ PRACTICAL PROJECT — Production‑Grade API

Build a structured backend using a framework that enforces modules (e.g., NestJS),
while keeping the domain independent from the framework.

Core Requirements

- Clear module boundaries (domain / application / infrastructure)
- Repository interfaces with concrete adapters
- Validation at the edges
- Consistent error mapping to HTTP responses

Features to Implement

🔐 Authentication & RBAC

- Login flow with token issuance
- Role‑based access control (at least 2 roles)
- Authorization guards at use‑case boundaries

🧵 Background Jobs

- Offload slow work (e.g., email simulation, report generation)
- Simple in‑process queue or scheduled tasks
- Idempotent job handlers

❤️ Health & Lifecycle

- /health endpoint (liveness)
- /ready endpoint (readiness)
- Graceful shutdown: stop accepting traffic, finish in‑flight work

📊 Observability Basics

- Request logging (method, path, status, duration)
- Correlation/request ID propagation

⸻

🧪 Performance & Runtime Exercises

- Simulate CPU‑bound work → move to Worker Threads
- Stream a large response → observe memory vs latency
- Introduce an event‑listener leak → detect & fix

Document findings with short notes.

⸻

🎯 End‑of‑Month Mastery Test

You are ready for Month 4 if you can:

- Explain your architecture diagram in under 5 minutes
- Swap a database adapter with minimal domain changes
- Describe the event loop without hand‑waving
- Prevent basic memory leaks and handle shutdown safely

⸻

❗ Rule of Month 3

Frameworks are delivery mechanisms.
Architecture is the product.

⸻
