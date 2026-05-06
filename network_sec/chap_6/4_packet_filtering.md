# 🌌 Packet Filtering

---

## 💠 First Line of Defense (Why it matters)

> [!IMPORTANT]
> Packet filtering is your **fastest gatekeeper** — simple, scalable, and always on duty.

- 🚫 Inspects packets and decides **allow / deny**
- 📡 Operates on header fields (IP, ports, protocol)
- 🛠️ Deployed on routers & basic firewalls
- ⚡ Handles massive traffic with minimal latency
- 🎯 Blocks clearly invalid or unauthorized traffic

---

## 🧪 Core Mechanism — The 5-Tuple (How it works)

> [!NOTE]
> Every decision is made using a compact identity: the **5-tuple**.

| Field               | Purpose                        |
| ------------------- | ------------------------------ |
| 🌐 Source IP        | Where the packet comes from    |
| 🎯 Destination IP   | Where the packet is going      |
| 🔢 Source Port      | Sender application identifier  |
| 📥 Destination Port | Target service (e.g., 80, 443) |
| 📡 Protocol         | TCP / UDP / ICMP               |

---

### 🔄 Rule Evaluation Workflow

- 📜 Rules define **conditions → actions (ALLOW / DENY)**
- ⏭️ Processed **top-down (first match wins)**
- 🚫 Ends with **default deny** (best practice)
- ⚡ Rule order directly impacts performance & security

```bash
# Example: Allow HTTP traffic, deny everything else
iptables -A INPUT -p tcp --dport 80 -j ACCEPT   # allow web traffic
iptables -A INPUT -j DROP                       # default deny
```

**System Impact:** Ensures only explicitly permitted traffic enters, minimizing attack surface.

---

## 🛠️ Ingress & Egress Filtering (BCP 38)

> [!IMPORTANT]
> Stop spoofing at the **network boundary** — before it spreads.

### 🔄 Ingress Filtering (Incoming)

- 🚫 Blocks packets with **invalid/spoofed source IPs**
- 🎯 Protects internal network from fake origins

### 🔄 Egress Filtering (Outgoing)

- 🚫 Prevents internal hosts from sending spoofed packets
- 🌐 Reduces participation in global attacks

---

### 📜 Best Practice Standard

- 📡 **BCP 38** → Industry guideline for anti-spoofing
- ⚡ Highly effective against IP spoofing
- ⚠️ Limited global adoption → weakens overall Internet security

```bash
# Example: Drop packets claiming internal IP from external interface
iptables -A INPUT -s 192.168.0.0/16 -i eth0 -j DROP
```

**System Impact:** Prevents spoofed traffic from entering or leaving the network boundary.

---

## ⚡ Strengths vs Limitations (Reality Check)

> [!NOTE]
> Packet filtering is powerful—but not intelligent.

| Aspect         | Strength 💪                  | Limitation ⚠️                |
| -------------- | ---------------------------- | ---------------------------- |
| ⚡ Speed       | Extremely fast (header-only) | No deep inspection           |
| 📈 Scalability | Works in high-speed networks | Limited decision complexity  |
| 🧠 Awareness   | Simple rule matching         | Stateless (no context)       |
| 🔍 Visibility  | Sees headers only            | Cannot inspect payload       |
| 🐍 Resilience  | Blocks obvious threats       | Bypass via spoofing/fragment |

---

## ⚡ Applied Scenario (Metal — Real Flow)

> [!NOTE]
> Example: Blocking Unauthorized SSH Access

1. 🐍 Attacker scans for open port 22 (SSH)
2. 📡 Sends connection attempts to server
3. 🚫 Filter blocks all except trusted IP

```bash
# Allow SSH only from trusted IP
iptables -A INPUT -p tcp --dport 22 -s 203.0.113.10 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP
```

**System Impact:** Restricts sensitive access to trusted sources only.

---

## 🏁 Recap (Takeaways)

- 💠 Packet filtering = **fast, stateless gatekeeper**
- 🧪 Decisions based on **5-tuple identity**
- 🔄 Rule order = **critical for correctness & performance**
- 🛠️ Ingress/Egress filtering = **key anti-spoofing defense**
- ⚠️ Limitation = **no context, no payload awareness**
