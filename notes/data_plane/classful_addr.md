# 🌐✨ **Classful Addressing — Magical Networking Grimoire** ✨🌐

---

## 🏰 **1. The Five Great Address Classes**

Think of IP classes like kingdoms—each one with its own territory, citizens, and purpose 🌟

### 🔵 **Class A — The Grand Kingdom**

- **Starts with:** `0`
- **Range:** **1.0.0.0 → 127.255.255.255**
- **Structure:**
  - Network: **8 bits**
  - Host: **24 bits**

- **# Networks:** 128
- **# Hosts per network:** ~16 million 😮✨
- **Vibe:** Huge population, few big kingdoms.

---

### 🟣 **Class B — The Balanced Dominion**

- **Starts with:** `10`
- **Range:** **128.0.0.0 → 191.255.255.255**
- **Structure:**
  - Network: **16 bits**
  - Host: **16 bits**

- **# Networks:** 16,384
- **# Hosts:** 65,536
- **Vibe:** Balanced and versatile, like a middle realm.

---

### 🟢 **Class C — The Small Villages**

- **Starts with:** `110`
- **Range:** **192.0.0.0 → 223.255.255.255**
- **Structure:**
  - Network: **24 bits**
  - Host: **8 bits**

- **# Networks:** ~2 million
- **# Hosts:** 256
- **Vibe:** Many tiny villages — perfect for small groups 💚

---

### 🔥 **Class D — The Multicast Guild**

- **Starts with:** `1110`
- **Range:** **224.0.0.0 → 239.255.255.255**
- **Purpose:** Multicast ✨
- **Vibe:** A guild broadcasting to many listeners.

---

### 🌌 **Class E — The Forbidden Zone**

- **Starts with:** `1111`
- **Range:** **240.0.0.0 → 255.255.255.255**
- **Purpose:** Reserved for future experiments… mysterious~ 👀✨

---

## ✨ TL;DR — Address Classes

- **Class A:** Big hosts, few networks
- **Class B:** Balanced
- **Class C:** Lots of networks, few hosts
- **Class D:** Multicast
- **Class E:** Reserved

---

# 🛡️💫 **2. Subnet Masks — Your Magical Filtering Runes**

Subnet masks reveal the “Network Part” of an address, like wiping fog from a window 🔍✨

### ⭐ Examples

- **/24** → `255.255.255.0`
  - Network bits: 24
  - Host bits: 8

- **/22** → `255.255.252.0`
  - Network bits: 22
  - Host bits: 10

- **/28** → `255.255.255.240`
  - Network bits: 28
  - Host bits: 4

Each `/` number is how many bits (from left) are “locked” for the network.

---

# 🚦✨ **3. Forwarding with Subnet Masks**

_Imagine a router as a very diligent librarian sorting letters into the right delivery boxes~_ 📬💗

### 📮 **Local Forwarding Table**

| Destination | Output Link |
| ----------- | ----------- |
| 10.1.1.0/24 | 1           |
| 10.1.2.0/24 | 2           |
| 10.1.3.0/24 | 3           |

---

### 🌟 **Example: Received Packet → 10.1.2.6**

**Step 1: Represent as bits**
`00001010 00000001 00000010 00000110`

**Step 2: Apply Mask**
Mask for `/24`:
`11111111 11111111 11111111 00000000`

**AND Operation:**

```
00001010 00000001 00000010 00000110
AND
11111111 11111111 11111111 00000000
=
00001010 00000001 00000010 00000000
```

**Result:** `10.1.2.0` 🎯

### 🧭 **Step 3: Compare with Table**

Matches → **10.1.2.0/24**
So the packet goes to **Output Link 2** 🚀✨

---

## ✨ TL;DR — How Routing Works

✔️ Router uses subnet mask to extract the network part
✔️ Compares that result with table entries
✔️ Sends the packet to the matching output link
✔️ Simple and magical~ 💞
