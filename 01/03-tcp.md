# 🔌 TCP Connection Basics

Backend engineers don’t need to implement TCP.
But they must understand how it behaves, because HTTP performance and failures depend on it.

This guide explains TCP at the level required for backend engineering.

⸻

🧠 What Is TCP?

TCP (Transmission Control Protocol) is a transport layer protocol.

It provides:

- Reliable communication
- Ordered delivery of data
- Error detection and retransmission

HTTP (except HTTP/3) runs on top of TCP.

This means:

👉 Every HTTP request usually depends on a TCP connection.

⸻

🎯 Why Backend Engineers Must Understand TCP

Because TCP affects:

- Request latency
- Connection timeouts
- Throughput
- Server load
- Failure behavior

Many production issues are actually:

👉 TCP issues, not application bugs.

⸻

🔄 TCP Connection Lifecycle

A TCP connection has three main stages:

- 1️⃣ Connection establishment
- 2️⃣ Data transfer
- 3️⃣ Connection termination

⸻

1️⃣ Connection Establishment — The Three‑Way Handshake

Before sending data, client and server must establish trust.

```txt
This happens via the TCP handshake:

Step 1 — SYN

Client → Server:

“I want to start a connection”

Step 2 — SYN‑ACK

Server → Client:

“I accept, let’s communicate”

Step 3 — ACK

Client → Server:

“Connection confirmed”
```

Now:

👉 A reliable communication channel is created.

This process introduces initial latency.

⸻

2️⃣ Data Transfer Phase

During communication:

- Data is split into packets
- Packets are numbered
- Lost packets are retransmitted
- Delivery order is guaranteed

TCP ensures:

- No missing data
- No duplicated data
- Correct ordering

This reliability is why HTTP can assume:

👉 “If request arrives, it arrived intact.”

⸻

3️⃣ Connection Termination

When communication finishes:

- Either side can close the connection
- TCP performs a closing handshake

Frequent connection open/close cycles can:

- Increase latency
- Increase server CPU usage

⸻

⚡ Persistent Connections (Keep‑Alive)

Modern HTTP reuses TCP connections.

Instead of:

- Open → send → close

It does:

- Open → send many requests → close later

Benefits:

- Lower latency
- Better performance
- Reduced handshake overhead

⸻

🚧 Head‑of‑Line Blocking (Important Concept)

In HTTP/1.1 over TCP:

- Only one request is processed at a time per connection
- If one response is slow → others wait

This is called:

👉 Head‑of‑line blocking.

HTTP/2 improves this using multiplexing.

⸻

🌐 TCP and Network Failures

TCP must handle real network problems:

- Packet loss
- Congestion
- Variable latency

It uses:

- Retransmission
- Flow control
- Congestion control

Backend impact:

- Slow responses
- Timeouts
- Partial failures

⸻

📊 Throughput vs Latency

TCP behavior influences:

- How fast large responses transfer
- How quickly small requests complete

Examples:

- Many small requests → handshake cost matters
- Large streaming responses → congestion control matters

⸻

🧠 Senior Backend Mental Model

HTTP request is not just an API call.

It is:

- TCP handshake
- Packet scheduling
- Congestion management
- Application processing

Understanding TCP helps you:

- Diagnose performance issues
- Design better timeout strategies
- Optimize connection usage

⸻

🏁 Final Insight

You do not need to become a network engineer.

But you must understand:

👉 HTTP performance and reliability are strongly influenced by TCP behavior.
