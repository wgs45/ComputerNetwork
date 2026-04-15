# 🌌 Performance — Delay & Loss ⏱️📦

---

## 💠 Intuition — Why Delay & Loss Occur

> [!NOTE]
> Networks don’t fail randomly—**they degrade under pressure**.

- 💠 Packets travel through **routers with limited buffers**
- 🔄 When traffic spikes → packets must **wait (delay)**
- ⚠️ When buffers overflow → packets are **dropped (loss)**

> [!IMPORTANT]
> Performance issues are not bugs—they are **natural consequences of finite resources**

---

## 🧪 Formal Logic — Four Sources of Packet Delay

> [!NOTE]
> Total delay is the sum of four independent components:

d{nodal} = d{proc} + d{queue} + d{trans} + d{prop}

---

### 🔍 Breakdown

| Component             | Meaning                        | Key Insight                    |
| --------------------- | ------------------------------ | ------------------------------ |
| 💠 Processing Delay   | Error check + routing decision | ⚡ Very small (< ms)           |
| 🔄 Queueing Delay     | Waiting in buffer              | ⚠️ Depends on congestion       |
| 📤 Transmission Delay | Push bits into link            | ⚡ Depends on packet size/rate |
| 🌍 Propagation Delay  | Travel across physical medium  | ⚡ Depends on distance         |

---

## 🧪 Transmission vs Propagation (Core Distinction)

### 📤 Transmission Delay

d{trans} = L / R

- 💠 Time to **send bits into the link**
- ⚡ Controlled by **bandwidth**

---

### 🌍 Propagation Delay

d{prop} = d / s

- 💠 Time for signal to **travel through medium**
- ⚡ Controlled by **distance & signal speed (~2×10⁸ m/s)**

> [!IMPORTANT]
> Increasing bandwidth **does NOT reduce propagation delay**

---

## 🧪 Queueing Delay — The Real Bottleneck

> [!NOTE]
> Queueing delay is the **most unpredictable** component.

- 🔄 Packets wait in buffer before transmission
- ⚠️ Highly sensitive to traffic load

---

### 📊 Traffic Intensity Model

Traffic Intensity = La / R

- 💠 L = packet length
- 💠 a = arrival rate
- 💠 R = link bandwidth

---

### ⚠️ Behavior

| Traffic Intensity (La/R) | Network State        |
| ------------------------ | -------------------- |
| ~0                       | ⚡ Smooth flow       |
| → 1                      | 🔄 Heavy delay       |
| > 1                      | ⚠️ Congestion + loss |

> [!IMPORTANT]
> As La/R → 1, delay grows **non-linearly (explodes)**

---

## 🛠️ Applied Example — Caravan Analogy

```bash id="caravan1"
# Scenario:
cars = 10                  # bits in packet
service_time = 12 sec      # per car (transmission)
distance = 100 km
speed = 100 km/hr          # propagation

push_time = cars * service_time  # 120 sec
propagation_time = 1 hour

total_time ≈ 62 minutes
```

**System Impact:** Transmission and propagation delays **accumulate differently**, shaping total latency.

---

### ⚡ Insight Variation

- Faster propagation (1000 km/hr) → first packet arrives early
- But transmission still ongoing → **pipeline effect appears**

> [!NOTE]
> This is the foundation of **network pipelining efficiency**

---

## 🧪 Packet Loss — When Things Break

- 💠 Buffers have **finite capacity**
- ⚠️ If full → incoming packets are **dropped**

---

### 🔄 Loss Handling

| Strategy             | Description             |
| -------------------- | ----------------------- |
| 🔄 Retransmission    | Sender resends packet   |
| 💠 Upstream recovery | Previous router retries |
| ⚠️ No recovery       | Packet permanently lost |

> [!IMPORTANT]
> Loss triggers **higher-layer protocols (e.g., reliability mechanisms)**

---

## 🛠️ Tooling — Traceroute Analysis

> [!NOTE]
> Traceroute reveals **real-world delay per hop**

### 🔄 How It Works

```bash id="trace1"
# For hop i:
send 3 packets with TTL = i
router i replies
measure round-trip time (RTT)
```

**System Impact:** Enables visibility into **network path + latency bottlenecks**.

---

### 📊 Real Insight Patterns

- 💠 Increasing delay → longer distance or congestion
- ⚠️ "\*" → packet lost or router not responding
- 🔄 Variability → unstable network conditions

---

## 🧠 Mental Model — System Behavior

- 💠 Light traffic → predictable performance
- 🔄 Moderate traffic → queueing dominates
- ⚠️ Heavy traffic → loss + exponential delay

> [!IMPORTANT]
> Network performance is **non-linear under load**

---

## 🏁 Recap — Takeaways

- 💠 Total delay = **processing + queueing + transmission + propagation**
- ⚡ Transmission ≠ Propagation (very different causes)
- 🔄 Queueing delay = **main source of unpredictability**
- ⚠️ Packet loss occurs when **buffers overflow**
- 🛠️ Tools like traceroute reveal **real-world behavior**
