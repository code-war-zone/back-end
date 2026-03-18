# 🚀 Backend Engineering — Month 1 (Protocols & Raw Backend Thinking)

This month rewires how you think about backend engineering.
You will stop thinking in frameworks and start thinking in protocols, requests, failures, and system behavior.

⸻

🎯 Month 1 Goals

By the end of this month you must be able to:

- Build a backend without any framework
- Understand the full HTTP request lifecycle
- Explain authentication flows clearly
- Debug CORS issues confidently
- Design clean API semantics
- Implement core backend mechanisms manually

⸻

🧠 THEORY — What You MUST Know

1️⃣ HTTP Fundamentals

You must deeply understand:

- Stateless nature of HTTP
- Request → Response lifecycle
- TCP connection basics (high level)
- Headers as protocol control surface
- Payload vs metadata

You must be able to explain:

- What happens from browser click → server response
- Why servers don’t remember previous requests
- Why stateless systems scale better

⸻

2️⃣ HTTP Request Anatomy

You must know:

- Request line (method + path + version)
- Headers (Authorization, Content-Type, Accept)
- Body (JSON / form / binary)

Understand:

- Parsing request data
- Handling malformed input
- Content negotiation basics

⸻

3️⃣ HTTP Methods Semantics

You must clearly understand:

- GET → safe + idempotent
- POST → create / side effects
- PUT → full replacement
- PATCH → partial update
- DELETE → idempotent removal

Also understand:

- Why GET must not change state
- Why GET body is unreliable
- Why POST retries can be dangerous

⸻

4️⃣ Status Codes — Semantic Truth

You must know categories:

- 2xx success
- 3xx redirects
- 4xx client errors
- 5xx server errors

You must understand:

- Transport success vs business success
- When NOT to use 200
- Difference between 401 and 403

⸻

5️⃣ API Styles

Conceptual understanding only:

- REST (resource modeling)
- RPC (action-based design)
- GraphQL (client-driven queries)

You must explain:

- Over-fetching vs under-fetching
- Versioning challenges
- Caching trade-offs

⸻

6️⃣ Authentication over HTTP

You must understand:

- Authentication vs Authorization
- Cookies
- Sessions
- Token-based auth
- Header-based auth flows

Also know:

- Where trust is stored
- Stateless vs stateful auth

⸻

7️⃣ CORS (Browser Security Model)

You must deeply understand:

- Same-origin policy
- Preflight requests
- Allowed origins
- Allowed headers
- Credentials handling

You must be able to debug CORS without copying configs from the internet.

⸻

8️⃣ Idempotency (Conceptual)

Understand:

- Safe retries
- Duplicate submissions
- Payment-like scenarios

⸻

9️⃣ Basic HTTP Performance Awareness

Conceptual only:

- Keep-alive connections
- Request size impact
- Latency vs throughput

⸻

🛠️ PRACTICAL PROJECTS — Month 1

Project 1 — Raw HTTP Server (Core)

Build using Node built-in http module.

Must implement:

- Manual routing
- Request parsing
- JSON body parsing
- Proper response formatting
- Error handling

Constraints:

- ❌ No Express
- ❌ No Fastify
- ❌ No validation libraries

⸻

Project 2 — Authentication System

Implement:

- /login endpoint
- Random token generation
- In-memory token store
- Protected routes

Compare:

- Authorization header vs cookies

⸻

Project 3 — Logging & Middleware Concept

Implement manually:

- Request logger
- Response time measurement
- Error logger

Learn:

- Middleware flow concept without framework

⸻

Project 4 — Rate Limiter

Build simple rate limiter:

- IP-based
- In-memory counter
- Time window reset

Understand:

- Abuse protection basics

⸻

Project 5 — Request Validation

Implement manual validation:

- Required fields
- Type checking
- Proper status codes

⸻

Project 6 — CORS Break & Fix Exercise

You must:

- Build small frontend request
- Trigger CORS failure
- Fix headers manually
- Document why it failed

⸻

🎯 End-of-Month Mastery Test

You are ready for Month 2 if you can:

- Build backend without framework
- Explain full request lifecycle
- Implement auth manually
- Debug CORS confidently
- Choose correct HTTP methods and codes

⸻

❗ Rule of Month 1

If you don’t understand HTTP deeply,
everything else in backend becomes accidental.

⸻
