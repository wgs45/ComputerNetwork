# 💠 Multiplexing & Demultiplexing — Socket Delivery

> [!ABSTRACT]
> **Mission:** Understand how transport-layer segments travel between multiple application processes and reach the correct destination socket.
>
> **Core Mechanism:** Socket-based delivery using transport header fields
> **Key Distinction:** UDP → destination port; TCP → connection 4-tuple

---

## 💠 01. Intuition — Why Multiplexing Exists

A host may run multiple applications simultaneously: a browser, a game, a streaming service, and a background updater.

The transport layer must combine outgoing data from these applications and deliver incoming data to the correct application.

### 🔄 Two Complementary Operations

| Operation      | Direction | Responsibility                                                           |
| -------------- | --------- | ------------------------------------------------------------------------ |
| Multiplexing   | Sender    | Collect data from multiple sockets and add transport headers             |
| Demultiplexing | Receiver  | Inspect transport headers and deliver segments to the appropriate socket |

> [!NOTE]
> Think of multiplexing as **combining outgoing traffic** and demultiplexing as **sorting incoming traffic**.

### 📡 End-to-End Architecture

```text
SENDER HOST                              RECEIVER HOST

Application A                            Application A
Application B                            Application B
Application C                            Application C
     |                                        ^
     v                                        |
  Multiple Sockets                         Sockets
     |                                        ^
     v                                        |
Transport: Multiplexing              Transport: Demultiplexing
     |                                        ^
     v                                        |
Network → Link → Physical  ───────> Network → Link → Physical
```

**System Impact:** Multiplexing allows many application processes to share network resources, while demultiplexing preserves correct application-level delivery.

---

## 🧪 02. Formal Logic — How Socket Delivery Works

### ⚙️ Transport Segment Structure

A TCP or UDP segment contains a header and application data.

```text
  0 bits                                31 bits
  +--------------------+--------------------+
  |    Source Port     |  Destination Port  |
  +--------------------+--------------------+
  |          Other Transport Header Fields  |
  +-----------------------------------------+
  |                                         |
  |          Application Data               |
  |               (Payload)                 |
  |                                         |
  +-----------------------------------------+
```

The complete transport header contains additional fields. TCP and UDP have different header formats.

### 📦 Information Used for Demultiplexing

An IP datagram contains:

- Source IP address
- Destination IP address
- One transport-layer segment

The transport segment contains:

- Source port number
- Destination port number
- Protocol-specific header fields and payload

The receiving host uses the relevant header values to identify the destination socket.

### 🔄 Receiver Workflow

1. 🛰️ Receive an IP datagram from the network layer.
2. 🔍 Identify the transport protocol and inspect the segment header.
3. 🧭 Extract the relevant IP addresses and port numbers.
4. 🎯 Match the segment to the appropriate socket.
5. 📥 Deliver the data to the socket's receiving application.

> [!IMPORTANT]
> A **port number** identifies a transport endpoint on a host; an IP address identifies a network interface/address. Together, they help the operating system deliver traffic to the correct endpoint.

---

## ⚡ 03. UDP — Connectionless Demultiplexing

UDP uses a simple delivery model. For ordinary UDP socket demultiplexing, the receiving host primarily uses the **destination port number**, along with the local addressing and socket configuration.

### 🧪 Socket Initialization

```java
// Create a UDP socket bound to local port 12534.
DatagramSocket mySocket1 = new DatagramSocket(12534);
```

The socket listens on the specified local port, subject to the host's networking configuration.

### 📡 UDP Packet Flow

Suppose a server binds a UDP socket to port `6428`.

```text
CLIENT A                         SERVER
IP: 192.0.2.10                   IP: 192.0.2.20

Source Port: 5775
Destination Port: 6428
       |
       +---------------------------> UDP Socket :6428
                                     |
                                     v
                                  Server App
```

A second client can send a datagram to the same destination port:

```text
CLIENT B                         SERVER
IP: 192.0.2.30                   IP: 192.0.2.20

Source Port: 9157
Destination Port: 6428
       |
       +---------------------------> UDP Socket :6428
                                     |
                                     v
                                  Server App
```

Both clients can reach the same server socket even though their source IP addresses and source ports differ.

### 🛠️ Multi-Socket Example

```java
// Create a UDP server socket.
DatagramSocket serverSocket = new DatagramSocket(6428);

// Create two UDP client sockets with different local ports.
DatagramSocket mySocket1 = new DatagramSocket(5775);
DatagramSocket mySocket2 = new DatagramSocket(9157);
```

| Socket         | Local Port | Typical Role              |
| -------------- | ---------: | ------------------------- |
| `serverSocket` |       6428 | Receives client datagrams |
| `mySocket1`    |       5775 | Client endpoint 1         |
| `mySocket2`    |       9157 | Client endpoint 2         |

> [!IMPORTANT]
> For UDP, datagrams addressed to the same local destination port can be delivered to the same socket despite having different source endpoints. Actual selection also depends on socket binding, address configuration, and operating-system behavior.

**System Impact:** UDP's simple demultiplexing model enables one server socket to communicate with multiple remote endpoints without establishing a separate transport connection for each client.

---

## 🔒 04. TCP — Connection-Oriented Demultiplexing

TCP identifies an established connection using a **4-tuple**.

### 💠 The TCP 4-Tuple

| Field            | Purpose                                    | Example      |
| ---------------- | ------------------------------------------ | ------------ |
| Source IP        | Identifies the sender's IP endpoint        | `192.0.2.10` |
| Source port      | Identifies the sender's transport endpoint | `9157`       |
| Destination IP   | Identifies the receiving host endpoint     | `192.0.2.20` |
| Destination port | Identifies the receiving transport service | `80`         |

The connection is distinguished by the complete combination of these four values.

### 📡 Why One TCP Server Can Serve Many Clients

Imagine a web server listening on port `80`.

```text
CLIENT A                                SERVER B
192.0.2.10:9157  -------------------->  192.0.2.20:80
                                         TCP Socket A

CLIENT C                                SERVER B
192.0.2.30:5775  -------------------->  192.0.2.20:80
                                         TCP Socket C

CLIENT C                                SERVER B
192.0.2.30:9157  -------------------->  192.0.2.20:80
                                         TCP Socket D
```

Although all three segments have the same destination IP address and destination port, their complete 4-tuples differ.

The server can therefore associate each established connection with a different TCP socket.

### 🧪 Connection Identity Matrix

| Connection | Source IP    | Source Port | Destination IP | Destination Port |
| ---------- | ------------ | ----------: | -------------- | ---------------: |
| A → B      | `192.0.2.10` |        9157 | `192.0.2.20`   |               80 |
| C → B      | `192.0.2.30` |        5775 | `192.0.2.20`   |               80 |
| C → B      | `192.0.2.30` |        9157 | `192.0.2.20`   |               80 |

**Result:** Three distinct TCP connections can terminate at the same server IP and port.

> [!TIP]
> A TCP server's listening socket accepts connection requests. Established connections are handled through connection-specific sockets, allowing the server to communicate with many clients concurrently.

**System Impact:** TCP's 4-tuple-based connection identification supports concurrent sessions without requiring a unique server port for every client.

---

## ⚔️ 05. Metal — UDP vs. TCP Demultiplexing

### Comparison Matrix

| Property                                   | UDP                                               | TCP                                                      |
| ------------------------------------------ | ------------------------------------------------- | -------------------------------------------------------- |
| Transport model                            | Connectionless                                    | Connection-oriented                                      |
| Primary demultiplexing information         | Destination port, with local socket configuration | Source IP, source port, destination IP, destination port |
| Separate established socket per connection | Not inherently required                           | Yes, for each established connection                     |
| Multiple remote clients                    | Can share a UDP socket                            | Can have distinct TCP connection sockets                 |
| Connection setup                           | Not required                                      | Required before normal connection data transfer          |

### 🧠 Practical Mental Model

```python
# UDP mental model:
# Which local socket should receive this datagram?
udp_key = destination_port

# TCP mental model:
# Which established connection does this segment belong to?
tcp_key = (
    source_ip,
    source_port,
    destination_ip,
    destination_port,
)
```

> [!NOTE]
> This Python snippet is a conceptual model, not a literal implementation of the operating system's socket-demultiplexing algorithm.

---

## 🛠️ 06. Important Technical Nuances

### Multiplexing and Demultiplexing Exist Beyond Transport

The same general idea appears at multiple networking layers, although each layer uses its own identifiers and rules.

| Layer       | Example of Identification or Multiplexing   |
| ----------- | ------------------------------------------- |
| Application | Application protocols and message types     |
| Transport   | Port numbers and TCP connection identifiers |
| Network     | IP addresses and protocol identifiers       |
| Link        | Ethernet MAC addresses and EtherType        |

### ⚠️ Common Exam Traps

- **Trap 1:** TCP and UDP use identical demultiplexing rules.
  **Correction:** UDP commonly uses the local destination port and socket configuration; TCP uses the full connection 4-tuple for established connections.

- **Trap 2:** Every TCP client requires a different server port.
  **Correction:** Multiple TCP connections can share the same server IP and port.

- **Trap 3:** Source ports are irrelevant to UDP.
  **Correction:** The source port identifies the sender's endpoint and is useful for replies, even though ordinary UDP receiving demultiplexing primarily relies on the destination port and local socket configuration.

- **Trap 4:** Multiplexing means combining application payloads into one message.
  **Correction:** It means handling data from multiple sockets and adding transport headers; it does not necessarily merge their payloads into one segment.

---

## 🏁 07. Recap — Rapid Interview Revision

### Five Core Takeaways

1. 💠 **Multiplexing:** Collects outgoing data from multiple sockets and adds transport headers.
2. 📡 **Demultiplexing:** Uses header information to direct incoming segments to the correct socket.
3. 🧪 **UDP:** Commonly demultiplexes using the destination port and local socket configuration.
4. 🔒 **TCP:** Identifies established connections using source IP, source port, destination IP, and destination port.
5. ⚡ **Concurrency:** Many TCP connections can share one server IP and listening port while maintaining distinct connection identities.

### Interview Flashcards

| Question                                          | Answer                                                                          |
| ------------------------------------------------- | ------------------------------------------------------------------------------- |
| What is multiplexing?                             | Handling data from multiple sockets and adding transport headers at the sender. |
| What is demultiplexing?                           | Directing received transport data to the appropriate socket.                    |
| What identifies a TCP connection?                 | The source IP, source port, destination IP, and destination port.               |
| Can two UDP clients use the same server port?     | Yes, they can send datagrams to the same destination port.                      |
| Can two TCP connections share a destination port? | Yes, if their complete connection identities differ.                            |
| Why are port numbers necessary?                   | They help identify transport endpoints and deliver data to applications.        |

### 🔄 Final Mental Model

```text
MULTIPLE APPLICATIONS
         |
         v
MULTIPLEXING — SENDER
         |
         v
TRANSPORT HEADER + PAYLOAD
         |
         v
       NETWORK
         |
         v
DEMULTIPLEXING — RECEIVER
         |
         +---- UDP: Destination Port + Socket Configuration
         |
         +---- TCP: Full Connection 4-Tuple
         |
         v
CORRECT APPLICATION SOCKET
```

> [!SUCCESS]
> **Final takeaway:** Multiplexing gathers data from application sockets; demultiplexing directs incoming data to the correct socket. UDP uses a simpler connectionless model, while TCP distinguishes established connections using a four-field identity.
