# 🌌 Access Networks & Physical Media

---

## 💠 Concept: Where the Internet Begins (Access Network) 📡

> [!NOTE]
> The **access network** connects end systems (hosts) to the **first router (edge)**—your gateway to the Internet.

---

### 🧠 Intuition (Why)

- Devices cannot directly join the Internet core 🌍
- Need a **bridge from user → ISP**
- Access network = **first hop of connectivity**

---

### 🧪 Formal Logic (How)

| Layer             | Components                                 |
| ----------------- | ------------------------------------------ |
| 💻 Network Edge   | Clients & servers (apps run here)          |
| 📡 Access Network | Wired/wireless links to edge router        |
| 🌐 Network Core   | Interconnected routers (Internet backbone) |

---

### 🔄 Workflow (Connection Path)

```text
[Your Device]
   ↓ Access Network
[Edge Router / ISP]
   ↓ Core Network
[Global Internet]
```

# System Impact: Defines the entry point where performance and latency are first determined

---

### 🏁 Recap (Takeaway)

- Access network = **device → ISP bridge**
- Critical for **latency & bandwidth**
- First step into the Internet

---

## 💠 Concept: Types of Access Networks 🧩

> [!IMPORTANT]
> Different environments require different **access strategies**.

---

### 🧠 Intuition (Why)

- Homes, schools, and mobile users have **different constraints**
- Trade-offs: speed ⚡, mobility 📱, cost 💰

---

### 🧪 Formal Logic (How)

| Type             | Description                        |
| ---------------- | ---------------------------------- |
| 🏠 Residential   | Home broadband (cable, DSL, fiber) |
| 🏫 Institutional | Schools, companies                 |
| 📶 Mobile        | WiFi, 4G/5G cellular               |

---

### 🛠️ Applied Example (Metal)

```bash
# Check your current network interface
ifconfig   # Linux/macOS

# Shows WiFi or Ethernet connection
```

# System Impact: Helps identify the active access method affecting performance

---

### 🏁 Recap (Takeaway)

- Access varies by **environment & mobility**
- Each type balances **speed vs flexibility**

---

## 💠 Concept: Performance Factors ⚡

> [!NOTE]
> Not all access networks are equal—performance depends on key metrics.

---

### 🧠 Intuition (Why)

- Users experience differences in **speed & stability**
- Shared networks can cause **congestion**

---

### 🧪 Formal Logic (How)

| Factor                 | Meaning                                      |
| ---------------------- | -------------------------------------------- |
| ⚡ Bandwidth           | Max data rate (bps)                          |
| 🔄 Shared vs Dedicated | Shared = multiple users, Dedicated = private |
| 📶 Latency             | Delay in transmission                        |

---

### 🛠️ Applied Example (Metal)

```bash
# Measure network speed
speedtest-cli

# Outputs download, upload, latency
```

# System Impact: Quantifies real-world network performance at the edge

---

### 🏁 Recap (Takeaway)

- Bandwidth ≠ actual speed
- Shared networks → variable performance
- Latency impacts real-time apps

---

## 💠 Concept: Cable-Based Access (HFC) 📺

> [!IMPORTANT]
> Cable Internet uses **shared infrastructure with frequency multiplexing**.

---

### 🧠 Intuition (Why)

- Reuse existing TV cable infrastructure 📡
- Efficient but **shared among neighbors**

---

### 🧪 Formal Logic (How)

| Feature          | Description                                 |
| ---------------- | ------------------------------------------- |
| 📡 HFC           | Hybrid Fiber-Coax network                   |
| 🎚️ FDM           | Different signals use different frequencies |
| 👥 Shared Medium | Multiple homes share bandwidth              |
| ⬇️ Downstream    | 40 Mbps – 1.2 Gbps                          |
| ⬆️ Upstream      | 30 – 100 Mbps                               |

---

### 🛠️ Applied Example (Metal)

```text
# Frequency Division Multiplexing (concept)
[TV Signals] | [Data Signals] | [Control Signals]
  freq A        freq B            freq C
```

# System Impact: Enables multiple services over a single physical cable

---

### 🏁 Recap (Takeaway)

- Cable = **high speed but shared**
- Uses **frequency separation (FDM)**
- Performance depends on **neighbor usage**

---

## 💠 Concept: DSL (Digital Subscriber Line) ☎️

> [!NOTE]
> DSL uses **telephone lines with dedicated bandwidth per user**.

---

### 🧠 Intuition (Why)

- Leverages existing phone infrastructure 📞
- Separates voice and data → simultaneous use

---

### 🧪 Formal Logic (How)

| Feature            | Description               |
| ------------------ | ------------------------- |
| 📞 Medium          | Telephone line            |
| 🎚️ Frequency Split | Voice vs Data separation  |
| 🔒 Dedicated Line  | Not shared with neighbors |
| ⬇️ Downstream      | 24–52 Mbps                |
| ⬆️ Upstream        | 3.5–16 Mbps               |

---

### 🛠️ Applied Example (Metal)

```text
# DSL frequency usage
[Voice] --- low freq
[Data ] --- high freq
```

# System Impact: Provides stable, predictable performance per household

---

### 🏁 Recap (Takeaway)

- DSL = **dedicated but slower than cable**
- Stable performance
- Uses **frequency separation**

---

## 💠 Concept: Home Network Architecture 🏠

> [!NOTE]
> A home network combines multiple technologies into a **single unified system**.

---

### 🧠 Intuition (Why)

- Multiple devices need connectivity simultaneously 📱💻
- Requires routing, security, and wireless access

---

### 🧪 Formal Logic (How)

| Component       | Role                        |
| --------------- | --------------------------- |
| 📡 Modem        | Connects to ISP             |
| 📶 WiFi AP      | Wireless access             |
| 🧭 Router       | Traffic routing             |
| 🔒 Firewall/NAT | Security & IP management    |
| 🔌 Ethernet     | High-speed wired connection |

---

### 🛠️ Applied Example (Metal)

```bash
# Check local IP (assigned by router/NAT)
ipconfig   # Windows
```

# System Impact: Shows internal network structure managed by the router

---

### 🏁 Recap (Takeaway)

- Home network = **mini Internet system**
- Combines wired + wireless
- Router is the **control center**

---

## 💠 Concept: Wireless Access Networks 📶

> [!IMPORTANT]
> Wireless access prioritizes **mobility over stability**.

---

### 🧠 Intuition (Why)

- Users need connectivity anywhere 🌍
- Trade-off: convenience vs performance

---

### 🧪 Formal Logic (How)

| Type                | Range    | Speed       |
| ------------------- | -------- | ----------- |
| 📡 WiFi (WLAN)      | ~30 m    | 11–450 Mbps |
| 📶 Cellular (4G/5G) | 10–50 km | 10s Mbps+   |

---

### 🛠️ Applied Example (Metal)

```bash
# Scan WiFi networks
nmcli dev wifi list   # Linux
```

# System Impact: Reveals shared wireless spectrum and network congestion

---

### 🏁 Recap (Takeaway)

- WiFi = **local, high speed**
- Cellular = **wide coverage, lower speed**
- Both are **shared mediums**

---

## 💠 Concept: Enterprise Networks 🏢

> [!NOTE]
> Enterprise networks are **high-performance, mixed environments**.

---

### 🧠 Intuition (Why)

- Organizations need **scalability, reliability, security**
- Must support many users and services simultaneously

---

### 🧪 Formal Logic (How)

| Component   | Description                   |
| ----------- | ----------------------------- |
| 🔀 Switches | Internal data forwarding      |
| 🧭 Routers  | Connect to ISP                |
| 🌐 Ethernet | 100 Mbps → 10 Gbps wired      |
| 📶 WiFi     | Wireless access               |
| 🖥️ Servers  | Internal services (mail, web) |

---

### 🛠️ Applied Example (Metal)

```bash
# Ping internal server
ping 192.168.1.10

# Tests connectivity inside enterprise network
```

# System Impact: Validates internal network communication reliability

---

### 🏁 Recap (Takeaway)

- Enterprise = **hybrid wired + wireless**
- High-speed infrastructure
- Designed for **scale and control**

---

# 🌠 Final Synthesis

> [!IMPORTANT]
> Access networks define how devices **enter the Internet**, shaping performance, reliability, and user experience.

---

## 🏁 Recap

- 📡 Access network = **first hop to Internet**
- 🧩 Types: residential, mobile, enterprise
- ⚡ Performance = bandwidth + sharing + latency
- 📺 Cable = fast but shared
- ☎️ DSL = stable but slower
- 📶 Wireless = flexible but variable
- 🏠 Home & 🏢 enterprise = **integrated systems**
