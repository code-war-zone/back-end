# 🗄️ Backend Engineering — Month 2 (Databases & Performance Thinking)

This month transforms how you think about data.
You will stop writing CRUD blindly and start reasoning about consistency, latency, locks, and access patterns.

⸻

🎯 Month 2 Goals

By the end of this month you must be able to:

- Design relational schemas based on query patterns
- Explain and apply ACID and transactions in practice
- Diagnose slow queries using indexes and query plans
- Recognize and fix N+1 and join inefficiencies
- Compare PostgreSQL vs MongoDB with real benchmarks
- Choose normalization vs denormalization intentionally

⸻

🧠 THEORY — What You MUST Know

1️⃣ ACID in Practice

Understand deeply:

- Atomicity — all-or-nothing writes
- Consistency — constraints & invariants
- Isolation — concurrent transaction visibility
- Durability — persistence after commit

Be able to explain:

- Why transactions exist
- When long transactions are harmful
- How partial failures corrupt systems

⸻

2️⃣ Isolation Levels & Concurrency

Know the spectrum:

- Read Uncommitted (rare)
- Read Committed (common default)
- Repeatable Read
- Serializable (strongest)

Understand anomalies:

- Dirty reads
- Non‑repeatable reads
- Phantom reads

Also understand:

- Row locks vs table locks
- Deadlocks and detection
- Retry strategies for transient failures

⸻

3️⃣ Indexes — How Databases Find Data

Learn:

- B‑Tree indexes (range scans, ordering)
- Hash indexes (exact lookups)
- Composite indexes (prefix rules)
- Covering indexes

Understand trade‑offs:

- Faster reads vs slower writes
- Storage overhead
- When indexes are ignored

⸻

4️⃣ Query Planners & Execution

Understand conceptually:

- Cost‑based planning
- Sequential scan vs index scan
- Join strategies (nested loop, hash join)
- Why SELECT \* hurts performance

Be able to:

- Read an execution plan
- Predict when a query will degrade

⸻

5️⃣ Data Modeling Trade‑offs

You must reason about:

- Normalization (data integrity, flexibility)
- Denormalization (read performance, simplicity)
- Write amplification vs read amplification
- Schema evolution risks

⸻

6️⃣ Common Backend Data Problems

Recognize and fix:

- N+1 queries in relational access
- Missing indexes on hot paths
- Inefficient joins and large result sets
- Unbounded pagination and memory pressure

⸻

7️⃣ SQL vs NoSQL Thinking

Conceptual comparison:

- Strong consistency vs flexible schema
- Joins vs document embedding
- Transactions scope
- Horizontal scaling approaches

You must be able to justify:

- When PostgreSQL is the right tool
- When MongoDB simplifies the model

⸻

🛠️ PRACTICAL PROJECTS — Month 2

Project 1 — PostgreSQL API (Relational First)

Design and build a REST‑style API backed by PostgreSQL.

Requirements:

- Normalized schema (3–5 related tables)
- Foreign keys & constraints
- Transactions for multi‑step writes
- Proper indexes for hot queries
- Pagination & filtering

Must implement:

- Create / update flows using transactions
- At least one reporting query (aggregation)
- EXPLAIN plan analysis for slow endpoints

⸻

Project 2 — Performance Tuning Exercise

Intentionally create slow paths, then fix them.

Tasks:

- Add missing indexes → measure improvement
- Replace N+1 with joins / batching
- Limit result sets & add pagination
- Compare SELECT \* vs column selection

Document:

- Before / after latency
- Query plan differences

⸻

Project 3 — MongoDB API (Document Model)

Re‑implement the same API using MongoDB.

Requirements:

- Thoughtful document design
- Embedded vs referenced relations
- Appropriate secondary indexes
- Aggregation pipeline for reporting

Compare with PostgreSQL:

- Code complexity
- Query simplicity
- Read/write performance
- Schema change friction

⸻

Project 4 — Benchmark & Analysis

Create a small load script to simulate traffic.

Measure:

- Throughput (req/sec)
- P95 latency
- CPU / memory trends (rough)

Produce a short report:

- Which model performed better for which endpoints
- Why the database behaved that way

⸻

🎯 End‑of‑Month Mastery Test

You are ready for Month 3 if you can:

- Design a schema from access patterns, not intuition
- Explain an execution plan at a high level
- Fix an N+1 without guidance
- Add the right index for a given query
- Defend SQL vs NoSQL choices with trade‑offs

⸻

❗ Rule of Month 2

If you don’t understand how data is stored and accessed,
your backend performance will always be accidental.

⸻
