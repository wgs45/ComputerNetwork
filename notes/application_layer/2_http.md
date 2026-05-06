# 🌐 Web & HTTP

---

## 💠 Concept — Intuition (Why the Web Works)

A **web page** is not a single entity… it’s a **collection of objects** ✨

- 💠 Base HTML file (structure)
- 🖼️ Embedded objects (images, audio, scripts)
- 📍 Each object has its own **URL**

```text
www.someschool.edu/someDept/pic.gif
└── Host ───────────────┘ └─ Path ─┘
```

> [!NOTE]
> One page = **multiple network requests** (not just one!)

---

## 🧪 Theory — HTTP Overview (How Communication Happens)

### 📡 HTTP Basics

- 💠 HTTP = Web’s application-layer protocol
- 🖥️ Follows **Client-Server model**

| Role                | Function                     |
| ------------------- | ---------------------------- |
| 🌐 Client (Browser) | Requests & displays objects  |
| 🖥️ Server           | Responds with requested data |

```text
Client → HTTP Request → Server
Client ← HTTP Response ← Server
```

---

### 🔗 HTTP + TCP Relationship

- 💠 HTTP runs on **TCP (port 80)**
- 🔄 Lifecycle:

```text
1. Client opens TCP connection
2. Server accepts connection
3. HTTP messages exchanged
4. Connection closed
```

> [!IMPORTANT]
> HTTP is **stateless** — no memory of past requests.

---

## 🔄 Workflow — HTTP Connections

### ⚡ Non-Persistent HTTP

- 💠 One object per connection
- ❌ Multiple connections needed

```text
Open → Request → Response → Close
(repeat per object)
```

> Drawback: High latency due to repeated setup

---

### ⚡ Persistent HTTP (HTTP/1.1)

- 💠 One connection, multiple objects
- ⚡ Reduced delay

```text
Open → Request → Response → Request → Response → Close
```

> [!IMPORTANT]
> Can reduce total delay to ~**1 RTT for multiple objects**

---

## 🧪 Theory — Performance Analysis

### ⏱️ RTT (Round Trip Time)

- Time for request → server → response back

---

### 📊 Non-Persistent Response Time

- 💠 1 RTT → TCP setup
- 💠 1 RTT → Request + first response bytes

> System Impact: High latency makes non-persistent HTTP inefficient for modern web apps.

---

## 🛠️ Tooling — HTTP Messages

### 📤 Request Message Structure

```http
GET /index.html HTTP/1.1          # Request line
Host: www.example.com            # Header
User-Agent: Firefox              # Header
Accept: text/html                # Header

# Empty line = end of headers
```

> 💠 ASCII-based → human-readable

---

### 📥 Response Message Structure

```http
HTTP/1.1 200 OK                  # Status line
Date: Sun, 26 Sep 2010           # Header
Content-Type: text/html          # Header
Content-Length: 2652             # Header

<html>...</html>                 # Body (data)
```

> System Impact: Standardized format ensures interoperability across all web systems.

---

## 🔄 Workflow — HTTP Methods

| Method  | Purpose                 |
| ------- | ----------------------- |
| 📥 GET  | Retrieve data           |
| 📤 POST | Send data (form input)  |
| 🧾 HEAD | Retrieve headers only   |
| 📦 PUT  | Upload/replace resource |

```text
GET /search?q=anime&food=ramen
```

> [!NOTE]
> GET sends data via URL, POST via message body.

---

## 🧪 Theory — Status Codes

### 📊 Common HTTP Status Codes

| Code   | Meaning               |
| ------ | --------------------- |
| ✅ 200 | Success               |
| 🔀 301 | Moved Permanently     |
| ❌ 400 | Bad Request           |
| 🔍 404 | Not Found             |
| ⚠️ 505 | Version Not Supported |

---

## 🛠️ Tooling — Testing HTTP Manually

### 💻 Using Telnet

```bash
telnet gaia.cs.umass.edu 80   # Connect to HTTP server

GET /index.html HTTP/1.1      # Request
Host: gaia.cs.umass.edu

# Press Enter twice to send
```

> System Impact: Direct testing helps debug low-level protocol behavior.

---

## ⚡ Optimization — Persistent vs Non-Persistent

| Feature     | Non-Persistent | Persistent |
| ----------- | -------------- | ---------- |
| Connections | Many           | One        |
| RTT Cost    | High           | Low        |
| Efficiency  | ❌ Poor        | ✅ Better  |

> [!IMPORTANT]
> Modern web relies heavily on **persistent connections** for performance.

---

## 🏁 Recap — Takeaways

- 💠 Web pages = **multiple objects** across servers
- 📡 HTTP = stateless request-response protocol
- 🔗 Runs on TCP (port 80)
- ⚡ Persistent HTTP improves performance drastically
- 🛠️ Messages = structured (request/response)
- 📊 Status codes define outcomes
