# 🌸 SNMP — Simple Network Management Protocol

---

## 🌿 Prologue — Watching Over the Network

_“A healthy network is one that’s quietly observed.”_ 👀🌱

**SNMP** is a **network management protocol** that lets a **managing server** watch, query, and gently control **managed devices** through their **agents**.

Think of SNMP as a system of **crystal sensors** placed inside devices, reporting their status back to the operator 🪄

---

## 🔗 Two Ways SNMP Communicates

SNMP has **two main interaction styles**, like polite conversations vs sudden alerts 💬⚡

### 🔁 1) Request / Response Mode

- 🧠 **Manager → Agent**: asks for data or sets values
- 🤖 **Agent → Manager**: replies with requested info

Used for:

- Monitoring statistics 📊
- Querying device state
- Setting configuration values

---

### 🚨 2) Trap Mode

- 🤖 **Agent → Manager (unsolicited!)**
- Used to report **exceptional events**

Examples:

- 🔥 Interface down
- ❗ Threshold exceeded

> 💡 Traps are _push-based_ — the agent speaks first!

---

## 🧠 SNMP Message Types (Exam Favorites ⭐)

### 📤 Manager → Agent

- 🔍 **GetRequest** → get specific data
- ➡️ **GetNextRequest** → get next item in MIB list
- 📦 **GetBulkRequest** → get block of data (efficient!)
- ✏️ **SetRequest** → set a MIB value

### 📥 Agent → Manager

- 📩 **Response** → reply to requests
- 🚨 **Trap** → notify exceptional event

### 📝 TL;DR

> Managers ask politely. Agents answer—or shout if something’s wrong.

---

## 📦 SNMP Message Format (PDU)

Each SNMP message carries a **Protocol Data Unit (PDU)**.

### 🧩 PDU for Message Types 0–3

(Get, GetNext, GetBulk, Set)

Contains:

- 🔢 **PDU Type (0–3)**
- 🆔 **Request ID**
- ⚠️ **Error Status (0–5)**
- 📍 **Error Index**
- 📜 **Variable bindings** (Name–Value pairs)

---

### 🚨 Trap PDU (Type 4)

Special format for urgent news 💥

Includes:

- 🏢 **Enterprise**
- 🖧 **Agent Address**
- 🚨 **Trap Type (0–7)**
- 🧩 **Specific Code**
- ⏱️ **Timestamp**
- 📜 **Name–Value pairs**

---

## 🗂️ MIB — Management Information Base

### 🌳 What Is a MIB?

- 📚 A **structured database** of device information
- Maintained by the **agent**
- Defines what SNMP can monitor or control

### 📐 Structure of Management Information (SMI)

- A **data definition language**
- Describes:
  - Data types
  - Object names
  - Hierarchical structure

---

## 🧭 Object Identifiers (OIDs)

Each MIB variable has a **unique path**, like a magic address ✨

Example UDP-related MIB variables:

### 📊 UDP MIB Examples

- 🔢 **1.3.6.1.2.1.7.1 — UDPInDatagrams**
  - 32-bit counter
  - Total datagrams delivered

- 🚫 **1.3.6.1.2.1.7.2 — UDPNoPorts**
  - 32-bit counter
  - Datagrams dropped (no app on port)

- ⚠️ **1.3.6.1.2.1.7.3 — UDPInErrors**
  - 32-bit counter
  - Datagrams dropped (other reasons)

- 📤 **1.3.6.1.2.1.7.4 — UDPOutDatagrams**
  - 32-bit counter
  - Datagrams sent

- 📋 **1.3.6.1.2.1.7.5 — udpTable**
  - SEQUENCE
  - One entry per active UDP port

---

## 🌸 Why SNMP Is Still Loved

✔️ Simple & lightweight
✔️ Universally supported
✔️ Excellent for monitoring

⚠️ But remember:

- Limited configuration power
- Being replaced by NETCONF/YANG for automation
