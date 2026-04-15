# 🌌 Network Core & Switching ⚙️📡

---

## 💠 Intuition — Why the Network Core Exists

> [!NOTE]
> The network core is the **intelligence + transport engine** of the Internet.

- 💠 A **mesh of interconnected routers** forms the backbone
- 📡 Data travels as **packets**, not continuous streams
- 🔄 Core responsibility: **move data efficiently from source → destination**

> [!IMPORTANT]
> The core decides **how fast, how reliably, and through which path data flows**

---

## 🧪 Formal Logic — Packet Switching

### 📦 Core Mechanism

- 💠 Messages are split into **packets**
- 🔄 Packets travel **router → router**
- ⚡ Each packet uses **full link capacity**

---

### 🔄 Store-and-Forward Model

> [!NOTE]
> A router must receive the **entire packet before forwarding**

- 💠 Transmission delay = time to push packet into link

Transmission Delay = L / R

- 💠 End-to-end (2 hops, no propagation delay):

End-to-End Delay = 2 \* (L / R)

---

### 🧮 Applied Example — One-Hop Delay

```bash id="6k9p2x"
# Given:
L = 10_000 bits     # packet size (10 Kbits)
R = 100_000_000 bps # link rate (100 Mbps)

delay = L / R       # transmission delay
# = 0.0001 seconds = 0.1 ms
```

**System Impact:** Even small packets introduce **non-zero latency**, which compounds across hops.

---

## 🧪 Queueing Delay & Packet Loss

> [!IMPORTANT]
> When input traffic > output capacity → congestion emerges

- 🔄 Packets **queue in router buffers**
- ⚠️ If buffer is full → **packet loss occurs**

---

### ⚠️ Congestion Behavior

| Condition                | Result                 |
| ------------------------ | ---------------------- |
| Arrival rate < Link rate | ⚡ Smooth transmission |
| Arrival rate ≈ Link rate | 🔄 Queue buildup       |
| Arrival rate > Link rate | ⚠️ Delay + packet loss |

---

## 🧪 Core Functions — Forwarding vs Routing

### 🔀 Forwarding (Local Decision)

- 💠 Moves packet **input → correct output link**
- ⚡ Uses **forwarding table**

```bash id="fwd1"
# Example forwarding table
# header_value -> output_link

0100 -> 3
0101 -> 2
0111 -> 2
1001 -> 1
```

**System Impact:** Enables **fast, real-time packet movement** at each router.

---

### 🧭 Routing (Global Decision)

- 💠 Determines **end-to-end path**
- 🛠️ Uses routing algorithms
- 🔄 Updates forwarding tables dynamically

> [!NOTE]
> Routing = “thinking”, Forwarding = “acting”

---

## 🧪 Alternative Model — Circuit Switching

### 🔌 Core Idea

- 💠 Dedicated path reserved **before transmission**
- 🔒 Resources are **not shared**

---

### ⚖️ Characteristics

- ⚡ Guaranteed performance (no congestion)
- ⚠️ Inefficient if idle (wasted capacity)
- 📞 Used in traditional telephone systems

---

## 🧪 Multiplexing Techniques

### 🌈 Frequency Division Multiplexing (FDM)

- 💠 Spectrum split into **frequency bands**
- 📡 Each user gets a **continuous slice**

---

### ⏱️ Time Division Multiplexing (TDM)

- 💠 Time split into **slots**
- 🔄 Users transmit in **turns**

---

## ⚖️ Packet vs Circuit Switching

### 📊 Comparison

| Feature        | Packet Switching         | Circuit Switching   |
| -------------- | ------------------------ | ------------------- |
| Resource Usage | ⚡ Shared dynamically    | 🔒 Reserved         |
| Efficiency     | ⚡ High (bursty traffic) | ⚠️ Low (idle waste) |
| Delay          | ⚠️ Variable (congestion) | ⚡ Predictable      |
| Setup          | ⚡ No setup needed       | ⚠️ Requires setup   |

---

## 🧪 Applied Example — Network Utilization

> [!NOTE]
> Scenario: 1 Gbps link, each user needs 100 Mbps, active 10% of time

- 🔒 Circuit Switching → max **10 users**
- ⚡ Packet Switching → supports **~35 users**

---

### 🎯 Key Insight

- 💠 Packet switching leverages **probability of inactivity**
- ⚡ Not all users transmit simultaneously

> [!IMPORTANT]
> Probability (>10 active users) ≈ **0.0004 → very low congestion risk**

---

## ⚠️ Is Packet Switching Always Better?

### 🌊 Strengths

- ⚡ Efficient for **bursty data**
- 🔄 Dynamic resource sharing
- 🛠️ No connection setup required

---

### 🌩️ Weaknesses

- ⚠️ Congestion → delay & packet loss
- 🛠️ Requires:
  - Reliable transport protocols
  - Congestion control mechanisms

---

## 🧠 Conceptual Insight — Human Analogy

- 🔒 Circuit Switching → **Reserved highway lane** (always yours, even if empty)
- ⚡ Packet Switching → **Public road** (shared, efficient, but can jam)

---

## 🏁 Recap — Takeaways

- 💠 Network core = **router mesh enabling global communication**
- 📦 Packet switching = **efficient, flexible, dominant model**
- 🔄 Store-and-forward introduces **fundamental delay**
- ⚠️ Congestion leads to **queueing + packet loss**
- 🔀 Forwarding (local) ≠ Routing (global)
- 🔒 Circuit switching = **predictable but inefficient**
