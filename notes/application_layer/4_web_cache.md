# 🧊 Web Caches (Proxy Servers)

---

## 💠 Concept — Intuition (Why Caching Exists)

A **Web Cache (Proxy)** sits between client and server to **serve content faster** ⚡

```text id="qv9x3s"
Client → Cache → Origin Server
        ↑
     (Serve if cached)
```

> [!NOTE]
> Goal: **avoid contacting origin server whenever possible**

---

### 🎯 Core Behavior

- 💠 Browser sends all requests to cache
- 📦 If object exists → return immediately
- 🌐 Else → fetch from origin → store → return

---

## 🧪 Theory — Dual Role Architecture

A cache acts as both:

| Role      | Behavior                    |
| --------- | --------------------------- |
| 🖥️ Server | Responds to client          |
| 🌐 Client | Requests from origin server |

> [!IMPORTANT]
> This duality enables transparent acceleration without changing clients or servers.

---

## ⚡ Optimization — Why Web Caching Matters

### 🚀 Performance Benefits

1. ⚡ Faster response time
   - Cache is **closer to client**

2. 📉 Reduced bandwidth usage
   - Less traffic on access link

3. 🌍 Scalable Internet
   - Helps small providers deliver content efficiently

---

## 🧪 Theory — Performance Scenario (Without Cache)

### 📊 Given System

| Metric          | Value     |
| --------------- | --------- |
| 📶 Access Link  | 1.54 Mbps |
| ⏱️ RTT          | 2 sec     |
| 📦 Object Size  | 100 Kbits |
| 🔄 Request Rate | 15/sec    |

---

### ⚠️ Problem

- Access link utilization ≈ **0.97 (almost saturated)**
- Result: **Huge delays (minutes!)**

```text id="6m2qlf"
Delay = Internet Delay + Access Delay + LAN Delay
     ≈ 2s + minutes + microseconds
```

> System Impact: Network congestion destroys user experience.

---

## ⚡ Optimization — Solution Strategies

### 🅰️ Upgrade Link (Expensive 💸)

- Increase bandwidth (1.54 → 154 Mbps)
- Reduces congestion

> ❌ High cost

---

### 🅱️ Install Cache (Smart 💡)

- Serve requests locally
- Reduce external traffic

> ✅ Low cost + high impact

---

## 🧪 Theory — With Cache (Quantitative Insight)

### 📊 Given

- Cache hit rate = **0.4 (40%)**

---

### 📉 Access Link Utilization

```text id="3pgl6u"
Data Rate = 0.6 × 1.50 Mbps = 0.9 Mbps
Utilization = 0.9 / 1.54 ≈ 0.58
```

---

### ⏱️ Average Delay

```text id="t6kq2o"
Delay ≈ 0.6 × (2.01 sec) + 0.4 × (~milliseconds)
      ≈ ~1.2 sec
```

> [!IMPORTANT]
> Cache beats even a **100× faster link** in cost-efficiency.

---

## 🔄 Workflow — Conditional GET (Smart Caching)

### 🎯 Goal

Avoid sending data if cache is already **up-to-date**

---

### 🔁 Mechanism

```http id="dknq4g"
GET /file HTTP/1.1
If-Modified-Since: <date>   # Cache validation
```

---

### 📥 Server Responses

| Status              | Meaning                  |
| ------------------- | ------------------------ |
| ✅ 200 OK           | File updated → send data |
| ⚡ 304 Not Modified | Use cached copy          |

```http id="2vpk9l"
HTTP/1.1 304 Not Modified   # No data sent
```

> System Impact: Saves bandwidth and reduces latency significantly.

---

## ⚡ Optimization — HTTP/1.1 Limitations

### 🧱 Head-of-Line (HOL) Blocking

```text id="cxb1fa"
Large Object → Small Objects stuck behind
```

- 💠 Requests processed in order (FCFS)
- ⚠️ Small objects wait behind large ones

---

## 🚀 Evolution — HTTP/2 Improvements

### ⚡ Key Innovations

- 📦 Split objects into **frames**
- 🔄 Interleave transmission
- 🎯 Prioritize important resources

```text id="1g9txk"
Frame(O1) → Frame(O2) → Frame(O3) → ...
```

> [!IMPORTANT]
> Eliminates HOL blocking at application layer.

---

### 🎯 Additional Features

- Push unrequested objects (server push)
- Maintain single TCP connection
- Same semantics as HTTP/1.1

---

## 🌌 Evolution — HTTP/3 Leap

### ⚡ Core Shift

- Moves from TCP → **UDP-based transport**

---

### 🚀 Advantages

- ⚡ Independent streams (no global blocking)
- 🔒 Built-in security
- 📈 Better performance under packet loss

> [!NOTE]
> Each object has its own delivery control → no cross-impact.

---

## ⚖️ Comparison — HTTP Evolution

| Feature      | HTTP/1.1              | HTTP/2     | HTTP/3        |
| ------------ | --------------------- | ---------- | ------------- |
| Connection   | Multiple / Persistent | Single     | Single        |
| HOL Blocking | ❌ Yes                | ⚡ Reduced | ✅ Eliminated |
| Transport    | TCP                   | TCP        | UDP           |
| Security     | Optional              | Optional   | Built-in      |

---

## 🏁 Recap — Takeaways

- 💠 Web cache = **performance amplifier**
- ⚡ Reduces latency & bandwidth usage
- 🧠 Conditional GET avoids redundant transfers
- 🚀 HTTP/2 improves multiplexing
- 🌌 HTTP/3 eliminates transport-level blocking
