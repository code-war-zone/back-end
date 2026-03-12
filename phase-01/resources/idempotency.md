# Idempotency in APIs

Idempotency is a **fundamental concept in HTTP and distributed systems**.

It ensures that **performing the same operation multiple times produces the same result as performing it once**.

This property is critical for:

- reliability
- retry mechanisms
- network failure handling
- safe API design

---

## 1. Simple Definition

> An operation is **idempotent** if repeating it does NOT change the final state of the system after the first successful execution.

Example:

- Setting a user’s status to `active` multiple times → still `active`
- Deleting the same resource multiple times → resource remains deleted

---

## 2. Why Idempotency Matters

In real networks:

- requests can time out
- connections can drop
- responses may be lost
- clients may retry automatically

Without idempotency, retries may cause:

- duplicate payments
- duplicate orders
- inconsistent database state

Idempotent APIs make systems **safe to retry**.

---

## 3. Idempotent vs Non-Idempotent Operations

### Idempotent Operations

These can be repeated safely.

Examples:

- GET user
- PUT update profile
- DELETE resource

Final state remains the same after multiple calls.

### Non-Idempotent Operations

These change system state every time.

Examples:

- POST create order
- POST charge credit card
- POST send email

Calling them multiple times may produce **duplicate effects**.

---

## 4. HTTP Methods and Idempotency

| Method | Idempotent | Explanation                   |
| ------ | ---------- | ----------------------------- |
| GET    | Yes        | Read-only                     |
| PUT    | Yes        | Replaces resource state       |
| DELETE | Yes        | Resource remains deleted      |
| POST   | No         | Usually creates new data      |
| PATCH  | Usually No | Partial update may accumulate |

Example:

PUT /users/10

Setting:

{ “name”: “Sam” }

Calling this 10 times → user name still "Sam".

---

## 5. Real-World Example

### Non-Idempotent Payment

POST /payments

Retry may cause:

- double charge

### Idempotent Payment Design

Client sends:

POST /payments
Idempotency-Key: abc123

Server logic:

- first request → process payment
- repeated request with same key → return stored result

This guarantees **exactly-once behavior**.

---

## 6. Idempotency Key Pattern

Used in:

- payment systems
- booking systems
- financial transactions

Flow:

1. Client generates unique key
2. Server stores request result
3. Duplicate request → server returns cached response

Benefits:

- prevents duplicate operations
- improves reliability
- supports safe retries

---

## 7. Idempotency in Distributed Systems

Important for:

- message queues
- microservices
- event-driven architectures

Strategies:

- unique transaction IDs
- database constraints
- deduplication tables
- optimistic locking

---

## 8. Common Misunderstandings

### Idempotent ≠ No Side Effects

Example:

- Server may log each request
- Metrics may increase

But **business state remains unchanged**.

### DELETE Still Idempotent

Even if:

- first call → deletes resource
- second call → returns 404

Final system state is the same.

---

## 9. Best Practices

- Design **critical operations to be idempotent**
- Use **PUT for updates instead of POST**
- Implement **Idempotency-Key for financial actions**
- Make retries safe at infrastructure level
- Document idempotency behavior in API specs

---

## 10. Summary

Idempotency ensures:

- predictable system behavior
- safe retry mechanisms
- resilience in unreliable networks

It is a **core principle of robust API and microservice design**.
