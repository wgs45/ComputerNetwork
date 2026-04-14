# 🌈📡 **Selective Repeat (SR) – Arcane Transport Magic Tome**

_“When a network refuses to behave, Selective Repeat stays calm, smart… and graceful.”_ 💫💙

---

# ✨ **1. Core Definition**

Selective Repeat is a more refined, intelligent version of Go-Back-N—
it _selectively_ retransmits only the packets that were actually lost.
Nothing dramatic. Nothing wasted. Just elegance 💖

### 🌟 **Key Abilities (SR Magic Basics)**

- ✔️ **Receiver ACKs each packet individually**
- 🗃️ **Receiver buffers out-of-order packets**
- ⏳ **Sender keeps one timer per outstanding packet**
- 🪟 **Sender window = N consecutive sequence numbers**
- 🚫 **Only unACKed packets are retransmitted**

_Compared to GBN: SR feels like a tidy honor-student heroine who takes careful notes and handles situations calmly… unlike GBN who panics and redoes the whole scene~_ _giggles softly_ 💕

---

# ✨ **2. How Sender & Receiver Cooperate**

Let’s explore this like a duet between two elegant characters~ 🎶

---

## 💙 **Sender’s Graceful Duties**

- When the next sequence number is within the window → **send packet**
- For each packet sent → **start an individual timer**
- On **timeout(n)** → only **resend packet n** (not the entire batch!)
- On **ACK(n)** (where n is in [sendbase … sendbase+N]):
  - Mark packet n as received
  - If n is the smallest unACKed packet → slide window forward

📌 _This makes SR efficient—precise, organized, and never wasteful._

---

## 💜 **Receiver’s Elegant Logic**

When a packet with seq number _n_ arrives:

### 🟦 If n is in `[rcvbase … rcvbase+N-1]`

- Accept it
- Send ACK(n)
- If it creates an in-order streak → deliver to upper layer
- Also deliver any buffered packets that now fit neatly into place

### 🔹 If n is in `[rcvbase-N … rcvbase-1]`

- This packet was already received
- Receiver politely sends another ACK(n)
  _(like a calm “Yes yes, I got this one already~”)_

### ❌ Otherwise

- Packet is ignored
- _The receiver simply tilts her head and lets it pass~_

---

# ✨ **3. Selective Repeat in Action (N = 4)**

Let’s enjoy a soft little story together 💞

---

## 🎬 **Sender’s Actions**

- Sends pkt0, pkt1, pkt2, pkt3
- Waits…
- ACK0 → send pkt4
- ACK1 → send pkt5
- ACK3 arrives but pkt2 is missing (lost ❌)

### 🌩️ **Timeout for pkt2**

- Sender resends **only pkt2**
  _(Not 3,4,5—SR is smart, not dramatic!)_

---

## 📥 **Receiver’s Side**

- Receives pkt0 → ACK0

- Receives pkt1 → ACK1

- Receives pkt3 → **buffer**, ACK3

- Receives pkt4 → **buffer**, ACK4

- Receives pkt5 → **buffer**, ACK5
  _(The receiver is quietly stockpiling them like a kuudere with hidden otaku hobbies…)_

- Eventually receives pkt2 →
  - Deliver pkt2
  - Then pkt3, pkt4, pkt5 in order
  - Send ACK2

---

### 💭 **What Happens When ACK2 Reaches Sender?**

- Sender marks packet 2 as received
- The window advances
- New packets (6, 7, …) can now be sent forward ✨

---

# ✨ **4. The SR Dilemma – A Curious Problem**

Flips to a page with a mischievous sparkle ✨

### 😖 **The Issue**

If sequence numbers wrap too quickly, the receiver can’t tell:
“Is this packet new… or a super-late retransmission?”

That’s because sequence numbers repeat!
And the receiver’s window might accidentally accept an old packet as a new one 💥

---

## 📌 Example Setup

- Sequence numbers: **0, 1, 2, 3**
- Window size: **3**
- Sender retransmits pkt0 after a timeout
- But receiver also expects a new pkt0 soon (because windows overlap!)
- The receiver may **incorrectly accept an old pkt0 as fresh**…
  _A disastrous misunderstanding, like handing in last semester’s homework by accident…_ 💦

---

# ✨ **5. The Important Rule (To Avoid Chaos)**

To prevent the dilemma:

### ⭐ **Sequence number space must be at least twice the window size.**

- In plain words:
  **#seqnums ≥ 2 × window_size**

This ensures sender and receiver windows never overlap in a confusing way!

---

# ✨ **6. TL;DR – Sparkly Summary**

- ✔️ SR retransmits **only lost packets**
- ✔️ Receiver buffers out-of-order packets
- ✔️ Sender uses **per-packet timers**
- ✔️ Receiver delivers packets in strict order
- ✔️ Need **sequence numbers ≥ 2 × window size** to avoid confusion
- ✔️ SR is efficient, intelligent, and graceful ✨
