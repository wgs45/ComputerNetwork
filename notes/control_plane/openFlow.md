# 🌸 OpenFlow Protocol

---

## 🌊 Prologue — The Language of Control

_"If SDN is the brain… OpenFlow is the voice."_ 🗣️✨

OpenFlow is the **protocol** that allows an SDN **controller** and **switches** to communicate.
It tells switches **what to do**, **when to do it**, and **how packets should flow** 🌈

---

## 🔗 Where OpenFlow Lives

### 📡 Communication Basics

- 🔄 Operates **between controller and switches**
- 🔐 Uses **TCP** for message exchange
  - Optional **encryption** for security

❗ Important distinction:

> 🧩 **OpenFlow Protocol** ≠ **OpenFlow API**

- 📜 **Protocol** → defines message exchange
- 🎮 **API** → defines _what actions_ can be programmed (match, forward, drop, modify)

---

## 🧠 Three Classes of OpenFlow Messages

Think of them as different kinds of magical letters 💌

### 1️⃣ Controller ➜ Switch (Commands)

> _"Do this for me, dear switch~"_ 🌸

### 2️⃣ Switch ➜ Controller (Events)

> _"Something happened!"_ ⚠️

### 3️⃣ Symmetric (Miscellaneous)

> _"We both agree on this."_ 🤝

---

## 🧙 Controller-to-Switch Messages

### ⭐ Key Message Types

- 🔍 **Features**
  - Controller asks: _"What can you do?"_
  - Switch replies with capabilities

- ⚙️ **Configure**
  - Get or set switch parameters

- 🧩 **Modify-State**
  - Add ✨ / Delete ❌ / Modify 🔄 flow entries

- 📤 **Packet-Out**
  - Controller sends a packet
  - Chooses **exact output port**

### 📝 TL;DR

> Controller directly programs the switch’s behavior.

---

## 📢 Switch-to-Controller Messages

### ⭐ Key Message Types

- 📥 **Packet-In**
  - Switch sends packet to controller
  - Happens when no flow rule matches

- 🗑️ **Flow-Removed**
  - A flow entry expires or is deleted

- 🔌 **Port Status**
  - Link up/down
  - Port configuration changes

💡 Relief for humans:

> Network operators **do not** manually craft OpenFlow messages ❌✋
> They use **high-level abstractions** at the controller 🌈

---

## 🔄 Control/Data Plane Interaction — A Little Story

### 📘 Scenario: Link Failure Detected

1️⃣ 🔌 **Switch S1 detects link failure**

- Sends **Port Status** message to controller

2️⃣ 🧠 **Controller updates network state**

- Link-state info refreshed

3️⃣ 📣 **Routing app is notified**

- Dijkstra app registered for link changes

4️⃣ 🧮 **New routes computed**

- Uses network graph + link-state data

5️⃣ 🧩 **Flow tables recomputed**

- Controller prepares new rules

6️⃣ ✨ **OpenFlow installs new rules**

- Updated switches receive new tables

### 📝 TL;DR

> One link fails → the whole network adapts gracefully 💞

---

## 🏯 Real-World SDN Controllers

---

## 🌐 OpenDaylight (ODL)

### 🧱 Architecture Highlights

- 🧠 **Service Abstraction Layer (SAL)**
  - Connects apps & services

- 🌈 **Northbound APIs**
  - REST / RESTCONF / NETCONF

- 🔌 **Southbound APIs**
  - OpenFlow, NETCONF, SNMP, OVSDB

### 🛠️ Core Services

- Topology processing
- Switch manager
- Stats manager
- Forwarding rules manager
- Host tracking

### 📝 TL;DR

> ODL is modular, extensible, and enterprise-friendly.

---

## 🌟 ONOS Controller

### 💎 Design Philosophy

- 🧠 **Distributed core**
  - Reliability
  - Replication
  - Scalability

- 🎯 **Intent Framework**
  - Specify _what_ you want
  - ONOS decides _how_

### 🌈 APIs

- 🔼 Northbound: REST, Intent
- 🔽 Southbound: OpenFlow, NETCONF, OVSDB

### 📝 TL;DR

> ONOS is built for carrier-grade, always-on networks ⚡

---

## ⚠️ SDN — Selected Challenges

### 🧱 Control Plane Hardening

- Fault tolerance
- Security baked in 🔐
- Performance at scale

### 🎯 Mission-Specific Networks

- Real-time ⏱️
- Ultra-reliable 💎
- Ultra-secure 🛡️

### 🌍 Internet-Scale SDN

- Beyond a single AS

### 📡 5G & Beyond

- SDN is **critical** in 5G networks

---

## 🔮 SDN & The Future of Protocols

### 🌱 A New Way of Thinking

- Traditional:
  - Routers compute tables themselves

- SDN:
  - Controller computes tables centrally

### 🌊 Beyond Routing

- Possible **SDN-based congestion control**
  - Routers report congestion
  - Controller adjusts sender rates

💭 Final question:

> _Which network functions should be protocols… and which should be SDN-controlled?_
