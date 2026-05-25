# Network Security Assignment 6 🔐

---

# Multiple Choice Questions

---

## 1. Why are stateful inspection firewalls generally more secure than traditional packet-filtering firewalls?

**Type:** Multiple-Choice (10 Points)

- A. They only inspect packets using MAC addresses.
- B. They replace VPN tunnels with DNS filtering.
- C. They automatically encrypt all network traffic.
- D. They track active sessions and connection states.

✅ **Right Answer:** D

---

## 2. What abnormal TCP handshake behavior may indicate a SYN Flood attack?

**Type:** Multiple-Choice (10 Points)

- A. Frequent DNS resolution failures during browsing sessions
- B. Repeated TLS certificate renewals from trusted servers
- C. Large numbers of incomplete TCP connection requests
- D. Continuous ICMP echo replies between internal hosts

✅ **Right Answer:** C

---

## 3. What is the main characteristic of an amplification attack?

**Type:** Multiple-Choice (10 Points)

- A. Attackers physically disconnect servers from the network.
- B. DNS traffic is completely blocked.
- C. TLS certificates are forged automatically.
- D. Small requests generate much larger responses.

✅ **Right Answer:** D

---

## 4. What security advantage does Perfect Forward Secrecy (PFS) provide?

**Type:** Multiple-Choice (10 Points)

- A. It removes the need for certificates in TLS communication
- B. It blocks all denial-of-service attacks automatically.
- C. It renews expired certificates without administrator action.
- D. It protects past encrypted sessions if private keys are compromised.

✅ **Right Answer:** D

---

## 5. What is the primary purpose of the TLS Handshake process?

**Type:** Multiple-Choice (10 Points)

- A. To compress web traffic before secure transmission
- B. To dynamically assign hardware MAC addresses
- C. To resolve domain names before HTTPS connections
- D. To negotiate encryption settings and session keys

✅ **Right Answer:** D

---

## 6. Which protocol combination is most commonly used to provide secure web browsing over HTTPS?

**Type:** Multiple-Choice (10 Points)

- A. ICMP + ARP
- B. UDP + FTP
- C. UDP + DNS
- D. TCP + TLS

✅ **Right Answer:** D

---

## 7. In a SYN Flood attack, which TCP packet does the attacker intentionally avoid sending in order to keep connections in a half-open state?

**Type:** Multiple-Choice (10 Points)

- A. ACK
- B. SYN
- C. SYN-ACK
- D. FIN

✅ **Right Answer:** A

---

## 8. Which statement best describes a TCP Session Hijacking attack?

**Type:** Multiple-Choice (10 Points)

- A. An attacker gains unauthorized control of an active TCP communication session.
- B. An attacker physically disconnects network devices from the infrastructure.
- C. An attacker remotely modifies DNS records to redirect traffic.
- D. An attacker encrypts traffic using TLS to bypass firewalls.

✅ **Right Answer:** A

---

## 9. Why do analysts inspect TCP flags such as SYN, ACK, FIN, and RST in Wireshark?

**Type:** Multiple-Choice (10 Points)

- A. To identify connection states and abnormal communication behavior
- B. To increase packet transmission speeds automatically
- C. To disable encrypted traffic during packet analysis sessions
- D. To dynamically assign MAC addresses across enterprise networks

✅ **Right Answer:** A

---

## 10. What is the primary difference between an IDS and an IPS?

**Type:** Multiple-Choice (10 Points)

- A. IDS replaces firewalls, while IPS replaces VPN technologies.
- B. IDS analyzes encrypted traffic, while IPS blocks DNS queries.
- C. IDS blocks attacks automatically, while IPS only logs traffic.
- D. IDS generates alerts, while IPS can actively block malicious traffic.

✅ **Right Answer:** D

---

# Quick Review Summary ✨

| Topic                 | Key Concept                                  |
| --------------------- | -------------------------------------------- |
| Stateful Firewall     | Tracks active connections and session states |
| SYN Flood             | Many incomplete TCP handshakes               |
| Amplification Attack  | Small request → huge response                |
| PFS                   | Protects old sessions even if keys leak      |
| TLS Handshake         | Negotiates encryption and session keys       |
| HTTPS                 | Uses TCP + TLS                               |
| TCP Session Hijacking | Unauthorized takeover of active session      |
| TCP Flags             | Help analyze connection behavior             |
| IDS                   | Detects and alerts                           |
| IPS                   | Detects and blocks                           |

---

# Important Security Concepts 🔐

## TCP Three-Way Handshake

Normal TCP connection process:

1. Client sends **SYN**
2. Server replies **SYN-ACK**
3. Client sends **ACK**

Connection becomes established afterward.

### SYN Flood Attack

In a SYN Flood attack:

- Attacker sends many SYN packets
- Server replies with SYN-ACK
- Attacker never sends final ACK
- Connections remain half-open
- Server resources become exhausted

---

## IDS vs IPS

| System                            | Function                     |
| --------------------------------- | ---------------------------- |
| IDS (Intrusion Detection System)  | Monitors and alerts          |
| IPS (Intrusion Prevention System) | Monitors and actively blocks |

---

## Perfect Forward Secrecy (PFS)

PFS ensures:

- Even if a private key is stolen later,
- Previous encrypted sessions remain secure.

Very important in modern TLS security ✨

---

## TCP Flags

| Flag | Meaning                     |
| ---- | --------------------------- |
| SYN  | Start connection            |
| ACK  | Acknowledge packet          |
| FIN  | Gracefully close connection |
| RST  | Forcefully reset connection |

Analysts inspect these flags in tools like Wireshark to detect suspicious traffic patterns and attacks.
