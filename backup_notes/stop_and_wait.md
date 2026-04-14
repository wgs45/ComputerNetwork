# ⏳✨ Stop-and-Wait Protocol ✨⏳

> _“Like a polite conversation where one speaks and waits for the other to reply, Stop-and-Wait ensures no one talks over the other~”_ 💬💞

---

## 💡 Definition

- **Stop-and-Wait** is a **data link layer protocol** used for transmitting frames over **noiseless channels** 🌐.
- Provides **flow control** ✅ but **no error control** ❌.
- Simple idea:
  1. Sender transmits **one frame at a time** 📨
  2. Waits for an **ACK** before sending the next one.

🎀 Think of it as passing love letters 💌—you send one, wait for a reply, then send the next. No rushing, no overlapping~

---

## ⚙️ Primitives (Rules)

### ✨ Sender Side

- Rule 1: Send **one packet at a time** 📦
- Rule 2: Only send the **next packet after receiving ACK** ✅

### ✨ Receiver Side

- Rule 1: Receive + consume data packet 🍪
- Rule 2: Send **ACK** after consuming 📩

---

## 📜 Visual Flow

```
Sender  ->  Data Packet  ->  Receiver
Sender  <-       ACK      <-  Receiver
Sender  ->  Data Packet  ->  Receiver
Sender  <-       ACK      <-  Receiver
(repeats…)
```

💭 It’s like a rhythm 🎶: _send, wait, reply… send, wait, reply…_

---

## ⚠️ Problems with Stop-and-Wait

1. **Lost Data** ❌
   - Sender waits forever for ACK ⏳
   - Receiver waits forever for data 😵

2. **Lost ACK** 💨
   - Sender keeps waiting infinitely for ACK that never arrives 🥲

3. **Delayed ACK/Data** 🐢
   - If ACK is delayed, sender might mistake it for ACK of a _different_ frame → causing confusion ❗

---

## 🧠 TL;DR Charm

- Simple but limited: send one frame ➡️ wait ➡️ ACK ➡️ repeat 🔁
- Elegant for noiseless channels, but fragile when errors occur 🌪️
- Problems: lost data, lost ACK, delayed signals 🚨
