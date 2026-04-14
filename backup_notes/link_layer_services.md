# 🌟 Link Layer Services

---

| 🔢 Physical | 🔢 Data Link | 🔢 Network | 🔢 Transport | 🔢 Session | 🔢 Presentation | 🔢 Application |
| ----------- | ------------ | ---------- | ------------ | ---------- | --------------- | -------------- |

## 🎯 Data Link Layer - The Bridge Between Nodes 🌉

The **Data Link Layer** is responsible for **moving data (frames) from one node to another** efficiently and accurately.

### 🚀 Key Services Provided

- 🏷 **Framing** – Organizes data into manageable units (frames).
- 🏠 **Physical Addressing** – Uses MAC addresses to identify sender and receiver.
- ⚖ **Flow Control** – Ensures smooth data transfer between sender & receiver.
- 🚨 **Error Control** – Detects & corrects transmission errors.
- 🚦 **Access Control** – Regulates access to the shared communication medium.

---

## 🖼️ Framing – Packing Data into Frames 📦

- The **Data Link Layer** packs bits into **frames**, making each unit of data distinguishable.
- Think of it like sending a letter 📩 – inserting a message into an envelope ✉ acts as a **delimiter** between different pieces of data.
- It ensures proper structure, making communication smooth & organized. 🏗

---

## 🏠 Physical Addressing – Identifying Senders & Receivers 🔍

- **A frame = Header + Data + Trailer**
- The **header** contains the **source** & **destination MAC addresses**.
- This ensures the frame reaches the right device in a local network. 🖥➡📡➡🖥

---

## 🚰 Flow Control – Avoiding Data Overload ⚖

- **Prevents a fast sender from overwhelming a slow receiver**. 🚦
- Ensures smooth data flow using a **speed-matching mechanism**. ⏳
- Uses **acknowledgments (ACKs)** to confirm receipt before sending more data. ✅

---

# 🔹 Data Link Sublayers – The Two Pillars 🏛

## 🔗 Logical Link Control (LLC) – Managing Data Flow 🔄

- Bridges communication between **upper (Network Layer) & lower (MAC Layer) layers**. 🔀
- Adds **control info** to network data, ensuring smooth delivery. 📡
- Responsible for **flow control & error detection**. 🛠

## 📡 Media Access Control (MAC) – The Hardware Layer ⚙

- **Implemented in hardware** (like **NICs** – Network Interface Cards). 💾
- Handles **data encapsulation** & **Media Access Control**.
- **Two main roles:**
  - 🛠 **Data Encapsulation** – Assembling frames before transmission & disassembling upon reception.
  - 📡 **MAC Addressing** – Unique physical address for each device.

---

## 📦 Data Encapsulation – Wrapping Data for Safe Transmission 🎁

- **Before transmission:** Frames are **assembled** with headers & trailers. 🔄
- **Upon reception:** Frames are **disassembled** & passed to upper layers. 📩
- **Key functions:**
  - 🏷 **Framing** – Organizes data into frames.
  - 🏠 **MAC Addressing** – Identifies devices.
  - 🚨 **Error Control** – Ensures data integrity.

🔹 The **MAC layer** directly interacts with the **Physical Layer**, ensuring data is placed & removed from the communication medium correctly. 📡
