# 🌟 Link Layer Services

---

| 🔢 Physical | 🔢 Data Link | 🔢 Network | 🔢 Transport | 🔢 Session | 🔢 Presentation | 🔢 Application |
| ----------- | ------------ | ---------- | ------------ | ---------- | --------------- | -------------- |

## 🎯 Data Link Layer

It is responsible for moving data (frames) from one node to another node.

✨ Services provided by Data Link Layer:

- Framing
- Physical Addressing
- Flow Control
- Error Control (Error Detection & Correction)
- Access Control (Media Access Control)

## 🖼️ Framing

- The data link layer needs to pack bits into frames, so each frame is distinguishable from another.
- Our postal system practices a type of framing.
- The simple act of inserting a letter into an envelope separates one piece of information from another (The envelope serves as the delimiter).

## 🏠 Physical Addressing

- A frame is the encapsulation of the header and trailer information with the packet.
- In the header, the source and the destination MAC address are dealt.

## 🚰 Flow Control

- Flow control is one of the duties of data link control sub layer.
- The flow control in data link layer is end to end flow control.
- Speed matching mechanism.
- Flow control coordinates the amount of data that can be sent before receiving an acknowledgment.
