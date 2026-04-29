# 🌐 OSI Security Architecture 🔒

---

## 💠 Concept — Security Foundations (Why)

### 🧨 Security Attack

- ⚠️ Any action that **compromises information security**
- 🎯 Targets: confidentiality, integrity, availability

---

### 🌑 Threat vs ⚔️ Attack

| Element   | Meaning                                     | Nature              |
| --------- | ------------------------------------------- | ------------------- |
| 🌑 Threat | Potential danger exploiting a vulnerability | Passive possibility |
| ⚔️ Attack | Actual attempt to breach security           | Active execution    |

> [!NOTE]
> A **threat becomes an attack** when it is actively executed.

---

## 🧪 Theory — Attack Classification (How)

### 👁️ Passive Attacks (Silent Observation)

- 🎧 Snooping → eavesdropping on communication
- 📊 Traffic Analysis → infer patterns without reading content

**Characteristics:**

- 💤 No system alteration
- 🎯 Goal: _steal information quietly_

> [!IMPORTANT]
> Passive attacks are **hard to detect**, but easier to prevent with encryption.

---

### ⚔️ Active Attacks (Direct Interference)

- 🎭 Masquerade → impersonation
- ✏️ Data Modification → alter/reorder messages
- 🔁 Replay → resend captured data
- 🚫 Denial of Service (DoS) → disrupt availability

**Characteristics:**

- 🔧 Modify system/data
- 🎯 Goal: _disrupt or manipulate_

> [!IMPORTANT]
> Active attacks are **harder to prevent**, focus is on detection + recovery.

---

## 🛠️ Tooling — Security Mechanisms (Defense Layer)

### 🔧 Mechanism Definition

- ⚙️ Processes/devices that **detect, prevent, or recover** from attacks

---

### 🧰 Common Mechanisms

- 🔐 Cryptography → protect data confidentiality
- 🧾 Digital Signature → integrity + nonrepudiation
- 🔑 Authentication Exchange → identity verification
- 📦 Traffic Padding → obscure traffic patterns
- 🧭 Routing Control → secure data paths
- 🏛️ Notarization → trusted third-party validation
- 🚪 Access Control → restrict unauthorized access

> [!NOTE]
> Mechanisms are the **tools**, not the end goal.

---

## 🔄 Workflow — Security Services (System Layer)

### 🧩 Service Definition

- 📡 Services that **enhance system security**
- 🔗 Built using one or more mechanisms

---

### 🛡️ Core Security Services

| Service            | Purpose                      |
| ------------------ | ---------------------------- |
| 🔑 Authentication  | Verify identity              |
| 🚪 Access Control  | Restrict unauthorized access |
| 🔐 Confidentiality | Protect data secrecy         |
| 🧬 Integrity       | Ensure data correctness      |
| 🚫 Nonrepudiation  | Prevent denial of actions    |
| ⚡ Availability    | Ensure system accessibility  |

> [!IMPORTANT]
> **Services = What you provide**, **Mechanisms = How you implement it**.

---

## 🧪 Theory — Authentication Deep Dive

### 🔑 Authentication Purpose

- 📩 Verify message origin
- 🔗 Ensure communication is not hijacked

---

### 🤝 Two Types (X.800 Standard)

#### 1. 👥 Peer Entity Authentication

- 🔗 Verifies identity of communicating entities
- ⏱️ Used during connection setup or session

**Prevents:**

- 🎭 Masquerade
- 🔁 Replay attacks

---

#### 2. 📩 Data Origin Authentication

- 🧾 Confirms source of a message
- ❗ Does NOT protect against duplication/modification

**Use Case:**

- 📧 Email systems (no continuous session)

> [!NOTE]
> Peer authentication = _session trust_, Data origin = _message trust_.

---

## ⚡ Optimization — Attack vs Defense Strategy

| Attack Type | Prevention Strategy   | Detection Strategy       |
| ----------- | --------------------- | ------------------------ |
| 👁️ Passive  | 🔐 Encryption         | 🚫 Very difficult        |
| ⚔️ Active   | ⚙️ Limited prevention | 📊 Monitoring + recovery |

> [!IMPORTANT]
> You **prevent passive**, but **manage active** attacks.

---

## 🔄 Workflow — End-to-End Security Flow

```text
Sender → Encrypt → Transmit → Receive → Decrypt → Verify Signature
# Protect data → Send securely → Restore → Validate integrity
```

**System Impact:** Ensures secure communication with confidentiality, integrity, and authenticity.

---

## 🏁 Recap — Strategic Takeaways

- 💠 **Threat ≠ Attack** → potential vs execution
- 👁️ **Passive = silent theft**, ⚔️ **Active = system manipulation**
- 🛠️ **Mechanisms = tools**, 🔄 **Services = protection goals**
- 🔑 **Authentication splits into session vs message trust**
- ⚡ **Security strategy = prevent + detect + recover**
