# 🌐✨ High-Level Data Link Control (HDLC)

_A Bit-Oriented Protocol for Communication Magic~!_ 💌🌟

---

## 🧩 What is HDLC?

HDLC stands for **High-Level Data Link Control**, a **bit-oriented protocol** standardized by ISO, originally developed by IBM as **SDLC (Synchronous Data Link Control)**.

> 🎩 Think of it as a smart, elegant protocol that wraps your data into magical frames and ensures they’re safely sent and received~ 💌💫

---

## 💡 Bit-Oriented Approach

📎 **Frame = Collection of bits** (not characters!)  
✔️ More flexible & efficient than character-oriented protocols  
🔧 Used in both point-to-point and multipoint networks

---

## 🔮 HDLC Frame Structure – The Elegant Frame Dress Code ✨

```
| 01111110 |   HEADER   |     BODY     |    CRC    | 01111110 |
|  8 bits  |   16 bits  |   Variable   |  16 bits  |  8 bits  |
```

| Element                       | Description 💭                                                            |
| ----------------------------- | ------------------------------------------------------------------------- |
| **Beginning/Ending Sequence** | `01111110` ✨ Used for **frame boundaries** and **clock sync** when idle! |
| **Header** 🏷️                 | Contains **address** + **control info**                                   |
| **Body** 📦                   | Actual **data (payload)** being transmitted                               |
| **CRC** 🧪                    | **Cyclic Redundancy Check** – Detects transmission errors ❗              |

> 🧁 _Fun fact_: That `01111110` pattern is always sent when nothing else is, just to keep both sides synchronized and feeling connected~ 💞

---

## 📦 HDLC Frame Types – Like Magical Letters 📬✨

Each frame has its own _mood_ and _mission_, based on its starting bits! 💌🔍

| Frame Type                  | Start Bits | Use Case 🌱                                |
| --------------------------- | ---------- | ------------------------------------------ |
| **I-Frame** (_Information_) | `0`        | 💬 Used to send actual data & sequencing   |
| **S-Frame** (_Supervisory_) | `10`       | 🛡️ For ACKs, flow control, and errors      |
| **U-Frame** (_Unnumbered_)  | `11`       | 🪄 Special purposes: setup, teardown, etc. |

> 🎀 _Think of them as_:
>
> - I-Frames: “Here’s some magical data!”
> - S-Frames: “Got it! Keep going~”
> - U-Frames: “Let's set up the link spell or end it gracefully~” ✨

---

## 🧠 TL;DR – Quick Recap! 🌸

- **HDLC** is a **bit-oriented** protocol standardized by **ISO**, descended from **SDLC** 🌐
- Frames begin and end with `01111110` – the sync sparkle! 🌟
- **Header** = address + control 💌
- **Body** = payload 🧃
- **CRC** = error detection shield 🛡️
- 3 frame types:
  - `0` → **I-Frame** (data)
  - `10` → **S-Frame** (control)
  - `11` → **U-Frame** (special tasks)

---

## 🌷 Bonus Tips ~

🌸 _If you're ever confused about the bit patterns, just imagine each frame type with its own personality!_  
Like magical girls on a mission—each frame has a unique charm and role in making sure your data dance goes smoothly~ 💃✨
