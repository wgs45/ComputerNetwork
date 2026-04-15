# 🌌 Throughput ⚡📡

---

## 💠 Intuition — What Throughput Really Means

> [!NOTE]
> Throughput is the **actual delivery speed**, not the theoretical maximum.

- 💠 Defined as **bits transferred per unit time**
- 🔄 Represents **real system performance**
- ⚡ Always constrained by the **slowest part of the path**

---

### 🧠 Two Perspectives

| Type             | Meaning                    |
| ---------------- | -------------------------- |
| 💠 Instantaneous | Speed at a specific moment |
| 💠 Average       | Speed over a time interval |

> [!IMPORTANT]
> Engineers care most about **average throughput** for system evaluation

---

## 🧪 Formal Logic — End-to-End Throughput

### 🔗 Single Path Model

- 💠 Data flows through multiple links (like pipes)
- ⚠️ The slowest link determines total throughput

```bash id="th1"
# End-to-end throughput rule

throughput = min(Rs, Rc)
# Rs = sender rate
# Rc = receiver link capacity
```

**System Impact:** System speed is **bounded by the weakest link**, not the strongest.

---

## 🧪 Bottleneck Concept

> [!IMPORTANT]
> The **bottleneck link** is the limiting factor in performance.

- 💠 Defined as the link with **lowest capacity**
- ⚠️ All data must pass through it → limits entire flow

---

### 📊 Cases

| Condition | Throughput Result  |
| --------- | ------------------ |
| Rs < Rc   | ⚡ Throughput = Rs |
| Rs > Rc   | ⚡ Throughput = Rc |

> [!NOTE]
> Increasing capacity elsewhere has **zero effect** if bottleneck remains unchanged

---

## 🛠️ Applied Example — Pipe Analogy

```bash id="pipe1"
# Scenario:
Rs = 50 Mbps   # sender rate
Rc = 100 Mbps  # receiver capacity

throughput = min(50, 100)
# = 50 Mbps
```

**System Impact:** Faster receiver **does not improve performance** if sender is slower.

---

## 🧪 Multi-Connection Network Scenario

> [!NOTE]
> Real networks involve **shared resources**

- 💠 Multiple connections share a **backbone link**
- 🔄 Fair sharing divides capacity

---

### ⚖️ Throughput per Connection

```bash id="th2"
# Given:
R  = backbone capacity
Rs = sender rate
Rc = receiver rate
N  = number of connections

per_connection_throughput = min(Rs, Rc, R / N)
```

**System Impact:** More users → **lower per-user throughput** due to sharing.

---

### 📊 Example (10 Connections)

| Parameter       | Value    |
| --------------- | -------- |
| Backbone (R)    | 100 Mbps |
| Connections (N) | 10       |
| Share per user  | 10 Mbps  |

> [!IMPORTANT]
> Even if Rs and Rc are high, **shared bottleneck dominates**

---

## 🧠 Key Insight — Throughput Hierarchy

- 💠 Local limits → Rs, Rc
- 🌐 Global limits → shared backbone (R/N)
- ⚠️ Final throughput = **minimum of all constraints**

---

## 🧪 Real-World Behavior

- ⚡ High bandwidth ≠ high throughput
- 🔄 Congestion reduces effective throughput
- 📉 Packet loss → retransmissions → lower throughput

> [!NOTE]
> Throughput reflects **both capacity and network conditions**

---

## 🏁 Recap — Takeaways

- 💠 Throughput = **actual data delivery rate**
- ⚡ Determined by **bottleneck link**
- 🔄 Multi-user systems → **shared throughput**
- ⚠️ Increasing one component ≠ improving system
- 🧠 Always analyze **end-to-end path**
