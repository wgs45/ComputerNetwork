# 🌊✨ Flow Control ✨🌊

_“Like a graceful dance, flow control keeps communication smooth—neither too fast nor too slow~”_ 💃📡

---

## 💡 What is Flow Control?

⭐ **Definition:**
Flow control is a **speed-matching mechanism** between **sender** and **receiver**.

- 📨 **Sender**: Wants to send data quickly.
- 💾 **Receiver**: Has limited memory + processing speed.
- 🎶 **Flow Control**: Coordinates how much data can be sent **before waiting for an ACK**.

💬 Imagine pouring tea 🍵—too fast and the cup overflows, too slow and it feels endless… flow control makes sure the pour is **just right** 💖.

---

## 🔑 Core Ideas

- 🔸 Sender must **wait for ACK** before sending too much.
- 🔸 Receiver notifies sender when it’s nearing its limit.
- 🔸 Sender may be asked to:
  - Send fewer frames 🚦
  - Or even stop temporarily ⏸️

✨ This ensures no data is lost, and the receiver isn’t overwhelmed~

---

## 📜 Flow Control Protocols

### 🟢 Noiseless Channels

(safe, simple, like two best friends chatting without interruption~ 💕)

- **Stop-and-Wait** ⏳
  → Sender sends one frame, waits for ACK before sending the next.

---

### 🔴 Noisy Channels

(like talking in a crowded festival 🎆—errors can happen!)

1. **Stop-and-Wait ARQ**
   - Sender resends if ACK isn’t received (like politely repeating yourself 🌸).

2. **Go-Back-N ARQ**
   - If an error is detected, the sender goes back and retransmits **N frames** starting from the error point.
   - (Like saying: “Oops, let me start that part again~” 🎤)

3. **Selective Repeat ARQ**
   - Only the **incorrect frames** are resent, not the whole bunch.
   - (Efficient, elegant—like fixing just one note in a song instead of replaying the whole piece 🎶✨).

---

## 🧠 TL;DR Charm

- Flow Control = **balance between sender & receiver speed** ⚖️
- Prevents overflow, data loss, and chaos 🚫
- Protocols:
  - Noiseless 🌸 → Stop & Wait
  - Noisy 🔊 → Stop & Wait ARQ, Go-Back-N, Selective Repeat
