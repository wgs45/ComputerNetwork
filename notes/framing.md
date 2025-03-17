# 🖼️ **Framing in Data Link Layer**

---

## 📌 **What is Framing?**

Framing is a technique used in the **Data Link Layer** to separate one **frame** from another, ensuring data is properly structured for transmission.

🔹 A **Frame** consists of:  
✅ **Header** – Contains control information (e.g., addresses).  
✅ **Network Layer PDU** – The actual data being transmitted.  
✅ **Trailer** – Used for error detection.

🔹 Instead of sending **continuous bit streams**, data is sent in structured **frames** in packet-switched networks.

### 🔹 **How Framing Works?**

1️⃣ **Node A** prepares a frame and sends it via its network adaptor.  
2️⃣ **The frame is transmitted as a sequence of bits over the link.**  
3️⃣ **Node B**'s adaptor **reassembles** the bits into a frame and stores it in memory.

---

## 🔄 **Types of Framing**

### 🏛️ **1. Fixed-Size Framing**

✔️ Frames have a **constant** size.  
✔️ The **frame length** acts as the boundary marker.  
✔️ No need for additional markers to identify **start/end** of a frame.  
✔️ Simple but **less flexible** for varying data sizes.

### 🔧 **2. Variable-Size Framing**

✔️ Frame sizes **vary**, depending on the data being transmitted.  
✔️ Requires **additional markers** (special bits or characters) to indicate the **start** and **end** of a frame.  
✔️ More **flexible** but requires **extra processing** to handle frame boundaries.

---

### 💡 **Why is Framing Important?**

🔹 Prevents **data corruption** by ensuring proper boundaries.  
🔹 Helps with **error detection** and efficient transmission.  
🔹 Improves **network performance** by structuring data properly.
