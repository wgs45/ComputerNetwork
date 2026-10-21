# 💠 Transport Layer — Services & Protocols

> [!ABSTRACT]
> **Mission:** Understand how transport protocols enable logical communication between application processes on different hosts.
>
> **Core Protocols:** TCP and UDP
> **Architecture:** Application → Transport → Network → Link

---

## 💠 01. Intuition — Why Transport Exists

The **Transport Layer** provides logical communication between application processes running on different hosts.

Applications need more than host-to-host connectivity: they need a way to deliver data to the correct process on the destination machine.

### 🏠 The Household Analogy

Imagine 12 children in Ann's house sending letters to 12 children in Bill's house.

| Networking Concept   | Household Analogy                     |
| -------------------- | ------------------------------------- |
| Hosts                | Ann's house and Bill's house          |
| Processes            | Individual children                   |
| Application messages | Letters                               |
| Transport layer      | Delivery between the correct children |
| Network layer        | Delivery between the two houses       |

> [!NOTE]
> The network layer gets data to the **destination host**; the transport layer delivers it to the **destination process**.

---

## 🧪 02. Formal Logic — Transport vs. Network

### Layer Responsibilities

| Layer     | Logical Communication | Primary Responsibility          |
| --------- | --------------------- | ------------------------------- |
| Transport | Process-to-process    | Application data delivery       |
| Network   | Host-to-host          | Packet delivery across networks |

The transport layer **relies on and enhances** the services provided by the network layer.

### 🔄 End-to-End Data Flow

```text
SENDER HOST                              RECEIVER HOST

Application Process                      Application Process
        |                                        ^
        v                                        |
Transport Layer                           Transport Layer
  Message → Segment                        Segment → Message
        |                                        ^
        v                                        |
Network Layer                             Network Layer
        |                                        ^
        v                                        |
     Network  -------------------------->  Network
```

> [!IMPORTANT]
> Transport protocols operate at end systems. Routers primarily forward network-layer packets rather than performing application-process delivery.

### ⚙️ Core Transport Actions

**Sender — Segmentation**

1. Receives an application-layer message.
2. Determines the segment header field values.
3. Encapsulates the message into a transport segment.
4. Passes the segment to IP.

**Receiver — Reassembly and Delivery**

1. Receives a segment from IP.
2. Checks the segment's header fields.
3. Extracts the application data.
4. Uses socket-based demultiplexing to deliver data to the appropriate application.

> [!TIP]
> **Encapsulation:** Application message → Transport segment → IP datagram.
> **Decapsulation:** IP datagram → Transport segment → Application message.

---

## ⚡ 03. Protocol Mechanics — TCP vs. UDP

The Internet provides two principal transport protocols: **TCP** and **UDP**.

### 📡 Protocol Comparison Matrix

| Feature              | TCP                                  | UDP                                            |
| -------------------- | ------------------------------------ | ---------------------------------------------- |
| Full name            | Transmission Control Protocol        | User Datagram Protocol                         |
| Delivery reliability | Reliable                             | Best-effort; not guaranteed                    |
| Delivery order       | In order                             | No ordering guarantee                          |
| Congestion control   | Yes                                  | No built-in transport-layer congestion control |
| Flow control         | Yes                                  | No built-in flow control                       |
| Connection setup     | Connection-oriented                  | Connectionless                                 |
| Protocol overhead    | Higher                               | Lower                                          |
| Typical use cases    | Web applications, file transfer, SSH | DNS, real-time media, interactive applications |

> [!IMPORTANT]
> **TCP** provides a reliable, in-order byte stream. **UDP** provides datagram delivery without built-in reliability, ordering, or retransmission guarantees.

### 🔒 TCP — Reliability and Control

TCP provides several important services:

- **Reliable delivery:** Detects loss and retransmits data when necessary.
- **In-order delivery:** Presents received bytes to the application in sequence.
- **Congestion control:** Adjusts sending behavior to respond to network congestion.
- **Flow control:** Prevents a sender from overwhelming the receiving application.
- **Connection setup:** Establishes connection state before normal data transfer.

### ⚡ UDP — Minimal Transport Overhead

UDP is a lightweight extension of IP's best-effort delivery model.

- No connection setup is required before sending datagrams.
- No built-in retransmission or in-order delivery guarantee.
- No built-in transport-layer flow or congestion control.
- Applications can implement additional mechanisms when needed.

> [!NOTE]
> UDP does not automatically mean faster communication in every situation. Its main advantage is minimal protocol overhead and the absence of built-in connection establishment and reliability mechanisms.

---

## 🛠️ 04. Applied Example — Metal

### Example A: Sending Data Through TCP

```text
Application: "Hello, Server!"
        |
        v
TCP: Add header and manage reliable delivery
        |
        v
IP: Route the datagram toward the destination
        |
        v
Receiver TCP: Validate, reorder, and recover data as needed
        |
        v
Server application: Receives the ordered byte stream
```

### Example B: Sending Data Through UDP

```text
Application: "Hello, Server!"
        |
        v
UDP: Add a lightweight datagram header
        |
        v
IP: Route the datagram toward the destination
        |
        v
Receiver UDP: Deliver the datagram if received
        |
        v
Server application: Receives the datagram
```

### 🧪 Python Demonstration — UDP Socket

```python
import socket

# Create an IPv4 UDP socket.
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

# Send one datagram to the destination host and port.
sock.sendto(b"Hello, Server!", ("127.0.0.1", 9999))

# Release the socket resource.
sock.close()
```

**System Impact:** UDP allows the application to send a datagram without establishing a TCP connection, making it useful when low overhead is important.

### 📡 Application-Level Examples

| Scenario              | Common Choice | Reason                                                     |
| --------------------- | ------------- | ---------------------------------------------------------- |
| File downloads        | TCP           | Reliable, ordered transfer                                 |
| SSH sessions          | TCP           | Reliable interactive communication                         |
| DNS queries           | UDP commonly  | Small request-response messages with low overhead          |
| Real-time voice/video | UDP commonly  | Avoids transport-level retransmission delays               |
| Multiplayer games     | UDP commonly  | Supports application-specific handling of latency and loss |

_Note: Application protocols can use other transports or add their own reliability mechanisms._

---

## ⚠️ 05. Transport Service Limitations

TCP and UDP do not inherently provide guaranteed end-to-end delay or bandwidth.

| Service                      | TCP | UDP |
| ---------------------------- | --- | --- |
| Guaranteed maximum delay     | No  | No  |
| Guaranteed minimum bandwidth | No  | No  |
| Reliable delivery            | Yes | No  |
| In-order delivery            | Yes | No  |

> [!WARNING]
> TCP reliability does not imply predictable latency. Retransmissions, congestion, routing, and receiver behavior can all affect performance.

**System Impact:** Applications requiring strict latency or bandwidth guarantees need additional mechanisms beyond ordinary TCP or UDP service.

---

## 🏁 06. Recap — Interview-Ready Knowledge

### The Five Core Principles

1. **Transport layer:** Provides logical process-to-process communication.
2. **Network layer:** Provides logical host-to-host communication.
3. **Segmentation:** The sender encapsulates application data into transport segments.
4. **Demultiplexing:** The receiver directs incoming data to the appropriate socket and application.
5. **TCP vs. UDP:** TCP prioritizes reliable, ordered delivery; UDP offers lightweight datagram delivery without those guarantees.

### 🧠 Rapid Recall

| Interview Question                      | One-Line Answer                                                                     |
| --------------------------------------- | ----------------------------------------------------------------------------------- |
| What does the transport layer do?       | Enables logical communication between application processes on different hosts.     |
| How does transport differ from network? | Transport is process-to-process; network is host-to-host.                           |
| What is segmentation?                   | Encapsulating application data into transport-layer segments.                       |
| What is demultiplexing?                 | Delivering received transport data to the appropriate socket.                       |
| What makes TCP reliable?                | Mechanisms such as acknowledgments, sequence numbers, and retransmissions.          |
| Why use UDP?                            | To send datagrams with minimal transport overhead and no built-in connection setup. |
| Does TCP guarantee low latency?         | No. It provides reliable, ordered delivery, not a strict delay guarantee.           |
| Do TCP or UDP guarantee bandwidth?      | Neither provides a general guaranteed-bandwidth service.                            |

### 🔄 Mental Model

```text
HOST-TO-HOST
     |
     v
Network Layer — IP
     |
     v
PROCESS-TO-PROCESS
     |
     +---- TCP: Reliability + Ordering + Control
     |
     +---- UDP: Minimal Overhead + Datagram Delivery
```

> [!SUCCESS]
> **Final takeaway:** IP moves data between hosts; TCP or UDP provides transport services to applications, with different trade-offs in reliability, ordering, control, and overhead.
