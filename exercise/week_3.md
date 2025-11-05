# 🌐 Week 3 – The Tale of Switching Networks ✨

_(A gentle journey through circuits, packets, and the magic of connections 💫)_

---

## 💎 R12 — Circuit Switching vs Packet Switching

### 🌸 Circuit-Switched Network (電路交換網路)

🔹 **Connection:** Must establish a dedicated circuit before communication (connection-oriented).
🔹 **Resource Allocation:** Each link reserves a fixed bandwidth exclusively for the call until it ends.
🔹 **Efficiency:** Lower when idle — bandwidth is still occupied even during silence.
🔹 **Delay:** Initial setup delay, but transmission after that is steady and predictable.
🔹 **Reliability:** Once connected, transmission is highly reliable and ordered.
🔹 **Examples:** Traditional telephone networks (PSTN), early voice calls 📞

### 💫 Packet-Switched Network (封包交換網路)

🔸 **Connection:** No need for a dedicated path — data is divided into packets and sent independently.
🔸 **Resource Allocation:** No fixed bandwidth; links dynamically share resources.
🔸 **Efficiency:** Very high — uses bandwidth as needed.
🔸 **Delay:** No setup delay, but packet paths may vary, causing variable latency.
🔸 **Reliability:** May experience packet loss or disorder; needs protocols like TCP to manage it.
🔸 **Examples:** Internet, email, web browsing, YouTube, video streaming 🌍🎥

---

### ⚔️ R12 Key Advantage Battle

| Aspect                  | Circuit Switching                                  | Packet Switching                               |
| ----------------------- | -------------------------------------------------- | ---------------------------------------------- |
| **Bandwidth Guarantee** | ✔️ Guarantees constant bandwidth                   | ❌ No end-to-end guarantee                     |
| **Hardware Complexity** | Simpler digital design                             | Requires routing & queuing                     |
| **TDM vs FDM**          | TDM (digital & flexible) needs simpler hardware 💡 | FDM needs complex analog frequency shifting ⚙️ |

🩵 **Summary:**
Circuit-switched networks shine when **steady, guaranteed transmission** is needed 🌟.
Packet-switched networks win in **efficiency and flexibility** for varied data traffic 🌈.

---

## ⚙️ Application Scenario — Choosing the Right Network

> 💭 _Imagine an app that sends small, steady data units at a constant rate and runs for a long time._

### 💎 a. Which Network Fits Best?

🧭 **Answer:** A **Circuit-Switched Network**

💬 **Why:**
Because it ensures a **fixed, stable bandwidth** and **predictable delay**, perfect for steady, continuous data flow (like voice or video calls).

📜 **TL;DR:**

> Choose **Circuit Switching** when data is steady, long-term, and delay-sensitive 🕰️✨

---

## 🚦 Congestion Control — When the Traffic Is Calm 🌤️

### 💭 Suppose

All applications are constant-rate senders,
and the total data rate is **less than the link capacities**.

### 💎 b. Is Congestion Control Needed?

💬 **Answer:** No 🌼

**Reason:**
Even if all applications send data simultaneously,
the network has enough bandwidth to carry all traffic smoothly.
So, **no congestion**, and **no queue buildup** occurs.

📜 **TL;DR:**

> If total traffic < link capacity → no congestion control required 💚

---

## 🧩 Circuit-Switched Network Example

### 💠 Given

A simple circuit-switched network with **four switches (A, B, C, D)** connected in a ring.
Each link can carry **4 circuits**.

🔸 Between each pair of adjacent switches = 4 circuits
🔸 Total links = 4

⭐ **Maximum simultaneous connections:**
`4 links × 4 circuits = 16 connections`

📜 **TL;DR:**

> Up to **16 calls** can happen at the same time 🌟

---

## 🔄 Routing Challenge

> Make **4 connections** between A–C
> and another **4 connections** between B–D.

⚡ **Can the network handle it?**

💬 It depends on how paths are routed.
Each pair (A–C and B–D) must share intermediate links carefully.
If both sets of calls try to use the **same links**, the 4-circuit limit will cause blocking 🚧.

📜 **TL;DR:**

> The network **can’t handle all 8** if routes overlap on the same 4-circuit links ❗
> Smart routing or additional capacity would be required.

---

## 🌷 Summary of Key Insights

| Concept            | Essence                              | Memory Charm ✨                             |
| ------------------ | ------------------------------------ | ------------------------------------------- |
| Circuit Switching  | Dedicated path, guaranteed bandwidth | 🕊️ "Steady as a melody"                     |
| Packet Switching   | Shared, dynamic path                 | 💫 "Flexible as the wind"                   |
| TDM > FDM          | Digital, efficient, simpler          | 🔮 "Time is easier to shape than frequency" |
| Congestion Control | Not needed if link capacity > demand | 🌤️ "Calm roads, no traffic"                 |
| Max Connections    | 4 links × 4 circuits = 16            | 🔢 "4×4, easy as magic"                     |
