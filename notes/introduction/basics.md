# 🌌 Basics of Computer Networking 🌐⚙️

---

## 💠 Intuition — What a Network Truly Is

> [!NOTE]
> A computer network is a **system of interconnected nodes** designed to exchange data efficiently and reliably.

- 💠 Connects devices for **communication + resource sharing**
- 🔄 Governed by **protocols (rules of interaction)**
- ⚡ Designed to balance **performance, reliability, and security**

> [!IMPORTANT]
> Networking is about managing **trade-offs under constraints**

---

## 🧪 Formal Logic — Core Characteristics

### 🏗️ System Properties

| Property           | Meaning                      | System Impact          |
| ------------------ | ---------------------------- | ---------------------- |
| 💠 Fault Tolerance | Survives failures            | ⚡ High availability   |
| 📈 Scalability     | Grows without degradation    | ⚡ Future-proof design |
| 🚀 QoS             | Prioritizes critical traffic | ⚡ Stable performance  |
| 🔒 Security        | Protects system              | ⚡ Trust & integrity   |

---

### 🔐 Security Model (CIA Triad)

- 🔒 **Confidentiality** → Prevent unauthorized access
- 🧪 **Integrity** → Prevent data tampering
- ⚡ **Availability** → Ensure system uptime

> [!IMPORTANT]
> Security is not optional—it is **foundational architecture**

---

## 🧪 Network Protocols & Communication

> [!NOTE]
> Protocols define **how data behaves in transit**

---

### 📦 Protocol Elements

- 📝 **Encoding** → Format of bits
- 📦 **Encapsulation** → Wrapping data with headers
- ⏳ **Timing** → When data is sent
- 📏 **Size** → Packet/message limits
- 📡 **Delivery** → Unicast / Multicast

---

### 🛠️ Applied Example — Protocol Flow

```bash id="proto1"
# Sending a message

data = "Hello"
encoded = encode(data)        # format bits
packet = encapsulate(encoded) # add headers
send(packet)                  # transmit via network
```

**System Impact:** Protocol structure ensures **interoperability across heterogeneous systems**.

---

## 🧪 Network Architecture Models

### 🔄 Peer-to-Peer (P2P)

- 💠 All nodes are **equal participants**
- ⚡ Simple, decentralized

| Pros                  | Cons                |
| --------------------- | ------------------- |
| ⚡ Easy setup         | 🚫 Poor scalability |
| 🔄 No central failure | 🚫 Hard to manage   |

---

### 🖥️ Client-Server

- 💠 Central server handles requests
- 🔄 Request → Response model

| Pros               | Cons                       |
| ------------------ | -------------------------- |
| ⚡ Scalable        | 🚫 Server bottleneck       |
| 🛠️ Central control | 🚫 Single point of failure |

> [!IMPORTANT]
> Most modern systems use **hybrid architectures**

---

## 🧪 Network Classification (Scale-Based)

| Type   | Scope       | Example Use Case     |
| ------ | ----------- | -------------------- |
| 🏠 LAN | Small/local | Home, office         |
| 🏙️ MAN | City-scale  | Urban infrastructure |
| 🌍 WAN | Global      | Internet             |

> [!NOTE]
> Scale directly affects **latency, complexity, and cost**

---

## 🧪 Network Topology — Structure vs Flow

- 💠 **Physical Topology** → Device layout
- 🔄 **Logical Topology** → Data flow pattern

---

## 🛠️ Applied Topologies — Design Trade-offs

### 🚋 Bus Topology

| Pros        | Cons                                  |
| ----------- | ------------------------------------- |
| ⚡ Low cost | 🚫 Single cable failure kills network |
| 🛠️ Simple   | 🚫 Poor scalability & security        |

---

### 🔄 Ring Topology

| Pros                | Cons                               |
| ------------------- | ---------------------------------- |
| ⚡ Equal access     | 🚫 Single node failure breaks loop |
| 🔄 Predictable flow | 🚫 Traffic bottlenecks             |

---

### ⭐ Star Topology

| Pros               | Cons                    |
| ------------------ | ----------------------- |
| ⚡ Easy management | 🚫 Central failure risk |
| 📈 Scalable        | 🚫 Hardware cost        |

> [!NOTE]
> Extended Star = scalable enterprise structure

---

### 🕸️ Mesh Topology

| Pros                    | Cons                      |
| ----------------------- | ------------------------- |
| 🔒 High fault tolerance | 🚫 Expensive (many links) |
| ⚡ Reliable paths       | 🚫 Complex routing        |

---

### 🔗 Hybrid Topology

- 💠 Combination of multiple topologies
- ⚡ Flexible + scalable

> [!IMPORTANT]
> Real-world networks are **almost always hybrid**

---

## 🧠 Design Insight — Choosing the Right Topology

```bash id="topo1"
# Network design decision

if reliability_critical:
    use "Mesh"

elif cost_sensitive:
    use "Bus or Star"

elif scalable_enterprise:
    use "Extended Star / Hybrid"
```

**System Impact:** Topology determines **fault tolerance, cost, and scalability envelope**.

---

## 🏁 Recap — Takeaways

- 💠 Networks balance **performance, security, and scalability**
- 🔄 Protocols define **communication rules**
- 🖥️ Architecture = **P2P vs Client-Server (or hybrid)**
- 🌍 Scale → LAN, MAN, WAN
- 🕸️ Topology defines **structure + resilience**
- ⚡ Real systems = **hybrid, layered, optimized designs**
