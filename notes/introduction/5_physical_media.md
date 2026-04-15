# 🌌 Physical Media & Links 📡

---

## 💠 Intuition — Why Physical Media Matters

> [!NOTE]
> Every network, no matter how abstract, ultimately depends on **how bits physically travel**.

- 💠 A **bit** is the smallest unit of data, moving between devices
- 💠 A **physical link** is the medium that carries those bits
- 💠 Performance depends heavily on the **type of medium used**

> [!IMPORTANT]
> The choice of medium directly impacts **speed, reliability, latency, and scalability**

---

## 🧪 Formal Logic — Media Classification

### 📊 Guided vs Unguided Media

| Type              | Description                           | Examples               | Key Trait             |
| ----------------- | ------------------------------------- | ---------------------- | --------------------- |
| 💠 Guided Media   | Signal travels through solid material | Copper, Fiber, Coax    | Stable & predictable  |
| 💠 Unguided Media | Signal propagates through free space  | Radio, WiFi, Satellite | Flexible but unstable |

---

## 🧪 Guided Media Deep Dive

### 🔌 Twisted Pair (TP)

- 💠 Two insulated copper wires twisted together
- ⚡ Reduces electromagnetic interference
- 📡 Common in Ethernet networks

| Category | Speed Capability  |
| -------- | ----------------- |
| Cat5     | 100 Mbps – 1 Gbps |
| Cat6     | Up to 10 Gbps     |

> [!NOTE]
> Twisting improves signal integrity by canceling noise.

---

### 📺 Coaxial Cable

- 💠 Two concentric copper conductors

- 🔄 Supports bidirectional transmission

- 📡 Enables broadband communication

- ⚡ Multiple frequency channels per cable

- ⚡ Each channel can reach **hundreds of Mbps**

---

### 💡 Fiber Optic Cable

- 💠 Transmits data as **light pulses through glass fiber**

- ⚡ Extremely high-speed communication

- 🔒 Immune to electromagnetic interference

- ⚡ Speed: **10–100+ Gbps**

- ⚡ Low error rate → fewer repeaters needed

> [!IMPORTANT]
> Fiber is the **backbone of the internet** due to its unmatched speed and reliability.

---

## 🧪 Unguided Media Deep Dive

### 📡 Wireless Radio

- 💠 Signals travel via electromagnetic waves
- 🔄 Typically **half-duplex** (one direction at a time)
- 🌍 No physical medium required

#### ⚠️ Environmental Effects

- ⚠️ Reflection (signal bouncing)
- ⚠️ Obstruction (walls, buildings)
- ⚠️ Interference (other signals)

---

### 📊 Radio Link Types

| Type                     | Speed / Property        | Notes                         |
| ------------------------ | ----------------------- | ----------------------------- |
| 📡 Terrestrial Microwave | Up to 45 Mbps           | Line-of-sight required        |
| 📶 WiFi (WLAN)           | 100’s Mbps              | Local area networking         |
| 📱 Cellular (4G)         | ~10’s Mbps              | Wide-area mobility            |
| 🛰️ Satellite             | ~45 Mbps / 270 ms delay | High latency, global coverage |

> [!NOTE]
> Satellite delay comes from long travel distance (especially geosynchronous orbit).

---

## 🛠️ Applied Example — Choosing the Right Medium

```bash
# Scenario: Deploying infrastructure for a cloud data center

if high_speed && low_latency:
    use "Fiber Optic"   # backbone + inter-server links

elif cost_sensitive && short_distance:
    use "Twisted Pair"  # internal office networking

elif wide_area && mobility_required:
    use "Cellular/WiFi" # user access layer

elif remote_area:
    use "Satellite"     # fallback connectivity
```

**System Impact:** Proper medium selection optimizes **performance, cost, and scalability** across network layers.

---

## 🏁 Recap — Takeaways

- 💠 Physical media defines **how bits travel in reality**
- ⚡ **Fiber = fastest & most reliable**
- 📡 **Wireless = flexible but unstable**
- 🛠️ Engineers must balance **speed, cost, and environment**
- 🔄 Network design is a **layered decision of media choices**
