# 🖧 **Switching Techniques in Computer Networking**

---

## 🔍 **What is Switching?**

Switching helps determine the **best route** for data when multiple paths exist in a network. 🌐  
It’s like choosing the **fastest road** for your data to travel. 🚗💨  
👉 It establishes a **one-to-one connection** for communication between devices.

---

## ⚡ **Types of Switching Techniques**

1. **Circuit Switching**
2. **Message Switching**
3. **Packet Switching**:
   - **Datagram Approach**
   - **Virtual Circuit Approach**

---

## 🛣️ **Circuit Switching**

- A **dedicated path** is created between the **sender** and **receiver**.
- Before sending data, the **connection is established**.
- **Example**: Traditional **telephone networks** 📞

### 🔄 **3 Phases of Circuit Switching**

1. **Connection Establishment**: The path is set up.
2. **Data Transfer**: The actual data is sent.
3. **Connection Disconnection**: The path is cleared after data transfer.

---

## 📨 **Message Switching**

- **Store and Forward Mechanism**: Messages are stored temporarily at intermediate nodes and then forwarded.
- Messages are transferred **in complete units**.
- **Not ideal for real-time or streaming** media. ⏳
  - Think of it as sending a letter via post: You **send it in one piece**, and it travels from station to station until it reaches the recipient.

---

## 💥 **Packet Switching**

The **internet** works using **packet switching**. 🌍

### 🚚 **How Packet Switching Works**

1. The message is **broken into packets**.
2. Each packet is sent **individually** to the destination.
3. Each packet carries the **source and destination IP address**, along with a **sequence number**.

#### 🛠️ **Why Sequence Number is Important**

- Helps the receiver **reorder the packets** correctly.
- Detects **missing packets** and requests for them.
- Allows the receiver to send an **acknowledgment (ACK)** back to the sender.

---

### 🛤️ **Packet Switching (Datagram Approach)**

- Known as **Connectionless Switching**.
- Each message is an **independent datagram**.
- The datagram has **destination info**.
- Intermediate devices **decide the route** at each step.
  - **No fixed path**. Each packet might take a different route!

---

### 🛣️ **Packet Switching (Virtual Circuit Approach)**

- Known as **Connection-Oriented Switching**.
- A **pre-planned route** is set up before sending data.
- **Call request** and **call accept** packets establish the path.
- The path remains **fixed** during the entire communication.
