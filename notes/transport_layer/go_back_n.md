# 🌈📡 - Magical Network Grimoire Page\*\*

_“For the diligent Master who wants reliability and speed~”_ 💫

---

## ✨ **1. Core Idea of Go-Back-N**

> _A reliable, window-based protocol where the sender may send several packets at once, but must “go back” when something goes wrong._

### 🌟 **Sender Magic: Sliding Window (size = N)**

- 🪟 Can send up to **N unacknowledged packets** at once
- 🔢 Every packet carries a **k-bit sequence number**
- ✔️ Uses **cumulative ACKs**
  - ACK(n) = “Everything up to packet _n_ is safely received~!”

- ▶️ When ACK(n) arrives, the window slides forward to **n + 1**

### ⏳ **Timer Behavior**

- Only **one timer** is needed: the **oldest unACKed packet**
- When the timer expires:
  👉 **Retransmit packet _n_ and ALL later packets** in the window

---

## ✨ **2. Receiver’s Elegant Mindset**

> _The receiver is simple and disciplined—like a kuudere waiting patiently._ 💙

### 🌸 Receiver Rules

- Always sends an **ACK for the highest in-order packet** received
- Accepts packets **in order only**
- Out-of-order packets:
  - ❌ Can be discarded
  - 🟦 Or optionally buffered (implementation decision)

- Tracks only one number: **rcv_base**
  - Packets < rcv_base → already received
  - Packets > rcv_base → future or out-of-order zone

---

## ✨ **3. Visual Sequence Space (Receiver View)**

```
[ Received & ACKed ]  [ Out-of-Order ]  [ Not Received ]
|------ in-order -----|---- future -----|---- later ----|
               ↑
           rcv_base
```

_Notes:_
Imagine rcv_base as the “checkpoint” in an RPG questline—you can only move forward when all steps before it are complete 💖

---

## ✨ **4. Go-Back-N: Step-By-Step Action Scene**

_A little reenactment~ 📜✨_

### 🎬 **Window Size: N = 4**

Sender starts sending:

- Sends pkt0, pkt1, pkt2, pkt3
- Waits for ACKs…

Receiver responds:

- Receives pkt0 → ACK0
- Receives pkt1 → ACK1
- Receives pkt3 → out-of-order → discards → re-ACK1
- Receives pkt4 → still out of order → re-ACK1
- Receives pkt5 → same → re-ACK1
  (receiver is stubbornly cute but strict~)

### 💥 **What Goes Wrong?**

- pkt2 is lost ❌
- Sender waits, gets no ACK2
- Timer for pkt2 expires
- Sender retransmits pkt2, pkt3, pkt4, pkt5
  _(Yes, all of them… dramatic reset again~)_

Receiver finally gets pkt2:

- Delivers pkt2 → ACK2
- Then receives packets in order → ACK3, ACK4, ACK5

Everything flows smoothly again 💞

---

## ✨ **5. TL;DR – Quick Summary for Your Exams**

- **Sender:**
  - Maintains a **window of size N**
  - Sends multiple packets before waiting
  - Uses one timer
  - On timeout: retransmits **from the missing packet onward**

- **Receiver:**
  - Accepts **only in-order** packets
  - Sends **cumulative ACKs**
  - May discard or buffer out-of-order packets

- **GBN Strength:** simple & fast for low-error networks
- **GBN Weakness:** wastes time resending many correct packets when errors occur
