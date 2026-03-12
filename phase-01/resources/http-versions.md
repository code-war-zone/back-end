# HTTP/1.1 vs HTTP/2 vs HTTP/3

HTTP (HyperText Transfer Protocol) has evolved over time to improve **speed, efficiency, and reliability** of web communication.

This document explains the **main differences between HTTP/1.1, HTTP/2, and HTTP/3**.

---

## Overview

| Version  | Released | Transport  | Key Goal                  |
| -------- | -------- | ---------- | ------------------------- |
| HTTP/1.1 | 1997     | TCP        | Reuse connections         |
| HTTP/2   | 2015     | TCP        | Performance & parallelism |
| HTTP/3   | 2022     | QUIC (UDP) | Speed + reliability       |

---

## HTTP/1.1

### Key Characteristics

- Text-based protocol (human readable)
- Uses **one request → one response at a time per connection**
- Introduced **persistent connections (Keep-Alive)**
- Allows **multiple connections per domain**
- Suffers from **Head-of-Line Blocking**

### Example Flow 1.1

TCP connection open
Request → Response
Request → Response
Connection closed

### Problems

- Slow page loading for modern websites
- Many TCP connections required
- Blocking delays when one request is slow

---

## HTTP/2

### Key Improvements

- **Binary protocol** (not text)
- **Multiplexing** → multiple requests at the same time on one connection
- **Header compression (HPACK)**
- **Server Push** (server can send resources without waiting for request)
- Fewer TCP connections needed

### Example Flow 2

One TCP connection
Request 1 ┐
Request 2 ├── parallel
Request 3 ┘
Responses returned independently

### Benefits 2

- Faster page loading
- Reduced latency
- Better network utilization

### Remaining Problem

- Still uses TCP → **Head-of-Line blocking at transport layer**

---

## HTTP/3

### Major Changes

- Uses **QUIC protocol (over UDP)** instead of TCP
- Built-in **TLS encryption (always secure)**
- Eliminates **transport-level Head-of-Line blocking**
- Faster connection setup (0-RTT possible)
- Better performance on **mobile and unstable networks**

### Example Flow 3

QUIC connection
Multiple independent streams
Packet loss affects only one stream

### Benefits 3

- Much faster on high-latency networks
- Better streaming and real-time performance
- Improved reliability

---

## Head-of-Line Blocking Explained

This happens when:

> One slow request blocks all others.

| Version  | Blocking Type                     |
| -------- | --------------------------------- |
| HTTP/1.1 | Application-level blocking        |
| HTTP/2   | TCP transport blocking            |
| HTTP/3   | No blocking (independent streams) |

---

## Connection Behavior Comparison

| Feature               | HTTP/1.1 | HTTP/2 | HTTP/3         |
| --------------------- | -------- | ------ | -------------- |
| Persistent connection | ✅       | ✅     | ✅             |
| Parallel requests     | ❌       | ✅     | ✅             |
| Binary framing        | ❌       | ✅     | ✅             |
| Header compression    | ❌       | ✅     | ✅             |
| Server push           | ❌       | ✅     | ⚠️ (less used) |
| Transport protocol    | TCP      | TCP    | QUIC (UDP)     |
| Built-in encryption   | ❌       | ❌     | ✅             |

---

## Performance Comparison (Simplified)

| Scenario                          | Best Version |
| --------------------------------- | ------------ |
| Old simple websites               | HTTP/1.1     |
| Modern web apps                   | HTTP/2       |
| Mobile / high latency / real-time | HTTP/3       |

---

## Real-World Usage Today

- HTTP/1.1 → still widely supported (fallback)
- HTTP/2 → **default for most websites**
- HTTP/3 → rapidly growing adoption (CDNs, Google, Meta, Cloudflare)

---

## Summary

- **HTTP/1.1** introduced connection reuse but is limited in performance.
- **HTTP/2** improved speed with multiplexing and compression.
- **HTTP/3** is the modern solution using QUIC for faster and more reliable communication.

> Modern backend and frontend systems should be designed with HTTP/2 and HTTP/3 performance characteristics in mind.
