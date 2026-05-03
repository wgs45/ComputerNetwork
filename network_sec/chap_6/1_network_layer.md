# 🌐 Network Layer Security Dashboard 🔒

---

## 💠 Concept — From Connectivity → Security

### 🧠 Intuition (Why)

- 🌍 Designed for **connectivity, not trust**
- 📡 Focus: deliver packets **across any network**
- ⚠️ Security was **never a primary concern**
- 🎭 Attacks exploit **assumptions**, not crypto

> [!IMPORTANT]
> IP’s greatest strength—openness—is also its greatest weakness.

---

### 🧪 Formal Logic (How)

- 📦 IP = **best-effort, connectionless protocol**
- 🔓 No authentication, integrity, or confidentiality
- 🔁 Each packet treated **independently**
- 🧩 Trust is **implicit**, not verified

---

### 🛠️ Applied Example (Metal)

```text
Client → [Packet: src=1.2.3.4, dst=8.8.8.8] → Internet

# Router forwards based ONLY on destination
# Source is blindly trusted
```

**System Impact:** Attackers can forge identity without breaking encryption.

---

### 🏁 Recap

- ⚡ IP prioritizes **reachability over security**
- ⚡ Trust is assumed → **not enforced**
- ⚡ This creates a **massive attack surface**

---

## 🌍 Role of Layer 3 — Global Routing Backbone

---

### 🧠 Intuition (Why)

- 🌐 Connects **multiple networks globally**
- 📡 Enables the **entire Internet**
- ⚖️ Must scale massively → security becomes harder

---

### 🧪 Formal Logic (How)

| Feature        | Description                      |
| -------------- | -------------------------------- |
| 🧭 Routing     | Based on destination IP          |
| 🔄 Forwarding  | Hop-by-hop decisions             |
| 🧠 Knowledge   | Local only (no global awareness) |
| ⚡ Scalability | Extremely high                   |

---

### 🛠️ Applied Example (Metal)

```text
Packet Path:
A → Router1 → Router2 → Router3 → B

# Each router:
# - Sees destination IP
# - Chooses next hop
# - No identity verification
```

**System Impact:** Trust is distributed across routers with no validation layer.

---

### 🏁 Recap

- ⚡ Layer 3 = **Internet backbone**
- ⚡ Local decisions → global behavior
- ⚡ Security is **fragmented and inconsistent**

---

## 📦 IP Protocol — Stateless & Connectionless

---

### 🧠 Intuition (Why)

- ⚡ Fast, lightweight, scalable
- ❌ No session tracking
- 🎯 Designed for **efficiency, not safety**

---

### 🧪 Formal Logic (How)

- 🔁 Stateless: no memory of previous packets
- 📦 Each packet routed independently
- 🎲 Delivery = **best effort only**

---

### 🛠️ Applied Example (Metal)

```text
Packet 1 → delivered
Packet 2 → dropped
Packet 3 → delayed

# No guarantee of order or delivery
```

**System Impact:** Attackers can inject or replay packets freely.

---

### 🏁 Recap

- ⚡ Stateless design = **high performance**
- ⚡ No context = **easy exploitation**

---

## 🧬 IP Packet Structure — Router Perspective

---

### 🧠 Intuition (Why)

- 👁️ Routers only care about **header**
- 📦 Payload is ignored during routing

---

### 🧪 Formal Logic (How)

| Field             | Purpose                |
| ----------------- | ---------------------- |
| 📍 Source IP      | Claimed sender         |
| 🎯 Destination IP | Routing target         |
| ⏳ TTL            | Prevent infinite loops |
| 🔢 Protocol       | Next layer (TCP/UDP)   |
| 🧮 Checksum       | Error detection (weak) |

---

### 🛠️ Applied Example (Metal)

```text
[Header]
src=FakeIP
dst=TargetIP
TTL=64

[Payload]
malicious_data
```

**System Impact:** Routers cannot detect spoofed identities.

---

### 🏁 Recap

- ⚡ Header drives routing decisions
- ⚡ No authenticity checks → **spoofing possible**

---

## ⚠️ Core Weakness — Trust Without Verification

---

### 🧠 Intuition (Why)

- 🤝 Systems trust **source IP blindly**
- 🎭 Identity can be forged easily

---

### 🧪 Formal Logic (How)

- ❌ No mechanism to verify sender
- 🔓 IP assumes **honest participants**
- 🧨 Enables spoofing & redirection

---

### 🛠️ Applied Example (Metal)

```text
Attacker sends:
src=TrustedServer
dst=Victim

# Victim believes it's legitimate
```

**System Impact:** Identity-based security at IP layer is fundamentally broken.

---

### 🏁 Recap

- ⚡ Source IP ≠ identity
- ⚡ Trust model is flawed by design

---

## 🔄 Routing Model — Hop-by-Hop Trust

---

### 🧠 Intuition (Why)

- 🧩 No central authority
- 🌐 Each router acts independently

---

### 🧪 Formal Logic (How)

- 📡 Forward based on routing tables
- 🔄 Dynamic path selection
- ❌ No sender verification

---

### 🛠️ Applied Example (Metal)

```text
Router Decision:
if dst in table:
    forward to next hop

# No validation of sender authenticity
```

**System Impact:** Attackers exploit trust between routing nodes.

---

### 🏁 Recap

- ⚡ Distributed trust model
- ⚡ No identity enforcement

---

## ⚖️ Design Trade-off — Scalability vs Security

---

### 🧠 Intuition (Why)

- 🌍 Internet must scale globally
- ⚡ Security mechanisms slow things down

---

### 🧪 Formal Logic (How)

| Feature      | Benefit  | Risk            |
| ------------ | -------- | --------------- |
| Stateless    | Fast     | No validation   |
| No auth      | Simple   | Spoofing        |
| Open routing | Scalable | Attack exposure |

---

### 🛠️ Applied Example (Metal)

```text
Design Choice:
Skip verification → faster routing

# Trade-off:
Speed ↑, Security ↓
```

**System Impact:** Fundamental vulnerabilities are unavoidable without redesign.

---

### 🏁 Recap

- ⚡ Performance prioritized over trust
- ⚡ Security must be added externally

---

## 🎭 Attacker Model — Thinking Like the Enemy

---

### 🧠 Intuition (Why)

- 🧠 Security depends on **who attacks**
- 🎯 Different attackers → different risks

---

### 🧪 Formal Logic (How)

| Type        | Capability                    |
| ----------- | ----------------------------- |
| 🧷 On-path  | Observe, modify, drop traffic |
| 🕵️ Off-path | Guess, spoof, inject blindly  |

---

### 🛠️ Applied Example (Metal)

```text
On-path:
Attacker sits between A and B → full visibility

Off-path:
Attacker sends fake packets → no visibility
```

**System Impact:** Attack feasibility depends on attacker position.

---

### 🏁 Recap

- ⚡ On-path = powerful, realistic
- ⚡ Off-path = limited, probabilistic

---

## 🎯 Attack Goals — Strategy Patterns

---

### 🧠 Intuition (Why)

- 🎯 Attacks follow **predictable goals**

---

### 🧪 Formal Logic (How)

- 🚪 Bypass → impersonate trusted source
- 📢 Amplify → small input → large impact
- 🎭 Obfuscate → hide identity

---

### 🛠️ Applied Example (Metal)

```text
DDoS Attack:
spoofed requests → amplify → overwhelm server
```

**System Impact:** Most attacks combine multiple strategies.

---

### 🏁 Recap

- ⚡ Think in goals, not just techniques
- ⚡ Predict attacks by intention

---

## 🧨 IP Spoofing — The Art of Deception

---

### 🧠 Intuition (Why)

- 🎭 Fake identity = bypass trust
- 🔓 Exploits lack of verification

---

### 🧪 Formal Logic (How)

- ✏️ Modify source IP in packet header
- 🎯 Keep destination valid
- 📡 Network cannot detect forgery

---

### 🛠️ Applied Example (Metal)

```text
Spoofed Packet:
src=BankServer
dst=User

# User trusts packet → attack succeeds
```

**System Impact:** Spoofing is a foundational primitive for many attacks.

---

### 🏁 Recap

- ⚡ Identity can be forged trivially
- ⚡ Enables larger attack chains

---

## 🎲 Off-Path Spoofing — Blind Injection

---

### 🧠 Intuition (Why)

- 👀 Cannot see responses
- 🎲 Relies on guessing

---

### 🧪 Formal Logic (How)

- 🔢 Guess sequence numbers / IDs
- 🔁 Retry many times
- 🎯 Success depends on randomness weakness

---

### 🛠️ Applied Example (Metal)

```text
for i in range(100000):
    send_packet(seq=random_guess)

# Hope one matches
```

**System Impact:** Weak randomness = dramatically higher attack success.

---

### 🏁 Recap

- ⚡ Probabilistic attack model
- ⚡ Defense = strong randomness + validation

---

# 🏁 Final System Insight

> [!IMPORTANT]
> Layer 3 is a **trustless delivery system pretending to be trustworthy**.

- 💠 Built for **scale**, not identity
- 🔓 Assumes honesty → enables deception
- ⚡ Security must be enforced **above or around IP**
