# 🌊📡 **TCP Congestion Control — The Magical Grimoire Edition**

### _A lovingly crafted scroll_ 💞✨

---

# 🌸 **1. AIMD (Additive Increase, Multiplicative Decrease)**

_Picture TCP as a cautious adventurer… slowly stepping forward, then retreating when danger appears._ 🎒⚔️

### 🔹 **Core Idea**

- TCP **increases** its sending rate gradually…
- …until it detects congestion (loss).
- Then it **cuts** its rate drastically to recover.

### 🧪 **The Rules**

✔️ **Additive Increase:**

- Increase cwnd by **1 MSS per RTT**
- Slow, cautious exploration

✔️ **Multiplicative Decrease:**

- On loss → **cut cwnd in half**

### 🎢 AIMD Sawtooth

A repeating pattern:
grow ➜ hit loss ➜ shrink ➜ grow again
Like breathing in and out ⤴️⤵️

### ⭐ TL;DR

AIMD = _slow climb, fast fall_ → stable, fair, well-behaved 💚

---

# 🌼 **2. AIMD Variants: Reno & Tahoe**

### 📘 **TCP Reno (Triple Duplicate ACK):**

- Loss found via **3 duplicate ACKs**
- _cwnd = cwnd/2_

### 📙 **TCP Tahoe (Timeout):**

- Timeout = serious congestion
- _cwnd = 1 MSS_ (back to the beginning)

### 💡 Why AIMD Works

- Distributed, asynchronous
- Network-wide stable
- Fair sharing between flows

---

# 📦 **3. Understanding cwnd & Sending Behavior**

### 🌐 TCP Sends Like This

```
Only send new bytes when:
LastByteSent − LastByteAcked < cwnd
```

### 🧭 Meaning

- **cwnd** decides how much data can be “in flight”
- Approximate sending rate:
  **cwnd / RTT** bytes per second

### ⭐ TL;DR

cwnd adjusts dynamically depending on congestion.
Bigger cwnd → more data flying through the network 🌬️📦

---

# 🌱 **4. Slow Start (SS)**

_The gentle beginning of a TCP connection — like a sprouting seed._ 🌱✨

### 🌸 How It Works

- Start at **cwnd = 1 MSS**
- For **every ACK**, increase cwnd
- Growth is **exponential**

### ⏳ When to Stop

1. ❗ Timeout → loss → restart SS
2. 🏁 When cwnd reaches **ssthresh** → switch to CA
3. 📨 3 duplicate ACKs → enter FR (Fast Recovery)

### ⭐ TL;DR

SS = fast growth to quickly discover capacity.

---

# 🧠 **5. Congestion Avoidance (CA)**

_Walking carefully near the cliff edge._ 🏞️💭

### 🌾 CA Behavior

- Increase cwnd **linearly** (1 MSS per RTT)
- Much gentler than SS

### 🚨 When CA Ends

1. Timeout → restart SS
2. 3 duplicate ACKs → enter FR
   - retransmit lost segment
   - _ssthresh = cwnd/2_
   - _cwnd = cwnd/2 + 3 MSS_

### ⭐ TL;DR

CA = slow, steady, cautious. 🐢✨

---

# ⚡ **6. Fast Recovery (FR)**

_TCP’s graceful way of handling small hiccups._ ⚡🦋

### 📜 Rules

1. Every duplicate ACK → **cwnd increases**
2. When ACK for missing segment arrives → enter CA
3. Timeout during FR → reset to SS

### ⭐ TL;DR

FR = recover quickly without full restart.

---

# 🧪🌙 **7. TCP CUBIC — A More Modern Spell**

_CUBIC is like a brilliant mage predicting the future bandwidth…_ 🎇📐

### 🌱 Insight

- Let **Wmax** be the window size where the last loss happened
- After reducing window, try to reach Wmax **faster**
- Then approach Wmax more **carefully**

### 🧹 How It Works

- Increases window size based on the **cube** of time since last loss
- Far from Wmax → increases quickly
- Near Wmax → slows down

### 🖤 Default in Linux

- Most popular for web servers
- Designed for high-speed, long-distance networks

### ⭐ TL;DR

CUBIC = smarter, smoother, faster than classic AIMD.

---

# 💫 **8. Bottleneck Link Behavior**

### 🧵 Core Idea

TCP increases sending rate until:
➡️ bottleneck router’s queue fills
➡️ packets drop
➡️ TCP backs off

### 🌊 Insight

Increasing sending rate at a bottleneck DOES NOT always increase throughput.
It only increases _RTT_, making delays longer.

### ⭐ Goal

“Keep the pipe full, but not fuller.” 🫗✨

---

# 🍃 **9. Delay-Based TCP (e.g., BBR)**

_These algorithms watch delays instead of waiting for losses._ ⏳💛

### 🌸 Approach

- Measure **RTTmin** = lowest RTT seen
- Estimate ideal throughput = cwnd / RTTmin
- Compare with actual throughput

### 🌱 Decisions

- If actual ≈ ideal → path not congested → increase cwnd
- If actual ≪ ideal → path congested → decrease cwnd

### ⭐ TL;DR

Delay-based = avoids losses, keeps latency low, keeps pipe _just full enough_.

---

# 🌐🔔 **10. ECN (Explicit Congestion Notification)**

_Routers send polite warnings instead of dropping packets._ 📨🟢

### 🧩 How It Works

1. Router marks IP header’s **ECN bits**
2. Receiver echoes congestion via **ECE bit** in TCP ACK
3. Sender reduces sending rate without loss

### ⭐ TL;DR

ECN = congestion control without packet loss.

---

# ⚖️ **11. TCP Fairness**

### 🎯 Goal

If **K TCP flows** share a bottleneck of bandwidth **R**,
each ideally gets **R/K** throughput.

### 🌱 Why It Works

- Additive increase raises everyone equally
- Multiplicative decrease reduces proportionally

### ⭐ TL;DR

TCP is fair under ideal conditions: equal RTT, fixed sessions, in CA.

---

# 🎭 **12. When TCP Isn’t Fair**

Some applications don’t play nicely…

### 🎵 **UDP Multimedia Apps**

- Don’t want rate throttled
- Send at constant rate
- Accept packet loss
- Bypass fairness completely

### 🌐 **Parallel TCP Connections**

Apps can open many TCP flows to gain more throughput
(e.g., browsers loading images)

More connections = more share of bandwidth
😈 A sneaky trick—totally legal.

---

# 🌈✨ **Final TL;DR — The Master Scroll**

- TCP uses cwnd to control sending rate.
- Start with **Slow Start**, then switch to **Congestion Avoidance**.
- On loss → react via Reno, Tahoe, FR.
- CUBIC is default in modern systems.
- Delay-based algorithms avoid losses by watching RTT.
- ECN gives routers a way to signal congestion.
- TCP is fair, unless apps cheat with UDP or parallel connections.
