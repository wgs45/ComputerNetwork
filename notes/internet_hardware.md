# **Internet Hardware** 🖥️🔌

---

## **List of Various Network Devices** 🌐

- **Repeater** 🔄
- **Hub** 🕹️
- **Switch** 🔀
- **Bridge** 🌉
- **Router** 🚦
- **Multi-layer Switch (Layer 3 Switch)** 🧑‍💻🔄
- **Bridge Router** 🌉🌐
- **Modem** 📶
- **Firewall** 🔥🛡️ (Security Device)

---

## **Hub & Switch** 🔄🖧

### **Difference between Hub and Switch**

| **Hub** 🚪                               | **Switch** 🔄                                                     |
| ---------------------------------------- | ----------------------------------------------------------------- |
| **Layer 1 Device**                       | **Layer 2 Device**                                                |
| Works at the **Physical Layer**          | Works at the **Data Link Layer**                                  |
| **No memory**                            | **Has memory** (Stores MAC address table)                         |
| **Not intelligent**                      | **Intelligent** (Can manage traffic)                              |
| Floods the network with **Broadcasting** | Can handle **Unicasting**, **Multicasting**, and **Broadcasting** |
| **High security risk**                   | **Low security risk**                                             |
| **Less efficient**                       | **More efficient**                                                |
| **Half Duplex**                          | **Full Duplex**                                                   |

---

## **Repeater** 🔄

### **What is a Repeater?**

- When data signals travel too far, they weaken or get corrupted.
- **Repeater** regenerates and **boosts** the signal over the same network.
- Operates at the **Physical Layer**.
- **Does not amplify** signals, it simply **regenerates** them.
- **2 port device**.

---

## **Bridge** 🌉

### **What is a Bridge?**

- **Bridge** = **Repeater** + **MAC Address Reading Functionality**
- Operates at the **Data Link Layer**.
- Connects two **LANs** using the same protocol.
- Also a **2 port device**.

### **Types of Bridges**

- **Transparent Bridges**:

  - The stations don’t even know the bridge exists.
  - No need to reconfigure stations when a bridge is added/removed.

- **Source Routing Bridges**:
  - **Routing is performed by the source station**.
  - The **frame** specifies which route to follow.
