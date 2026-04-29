# 🔐 Security Mechanisms & Cryptography 🛠️

---

## 💠 Concept — Mechanisms as the Engine (Why)

**Security Mechanisms** are the _execution layer_ of security:

- ⚙️ Detect attacks
- 🛡️ Prevent breaches
- 🔄 Recover from failures

> [!IMPORTANT]
> If **services define goals**, mechanisms are the **actual machinery** that enforces them.

---

## 🧪 Theory — Cryptographic Foundations (How)

### 🔑 Cryptographic Mechanisms

#### 🔄 Reversible (Encryption-Based)

- 🔐 Data can be encrypted **and decrypted**
- 🎯 Goal: confidentiality

---

#### ♾️ Irreversible (One-Way)

- 🧬 Hash functions
- 🧾 Message Authentication Codes (MAC)

**Properties:**

- 🚫 Cannot recover original data
- 🎯 Used for integrity + authentication

> [!NOTE]
> Irreversible ≠ useless—it’s the **foundation of trust verification**.

---

## 🛠️ Tooling — Core Security Mechanisms

- 🧾 Digital Signature → verify origin + integrity
- 🔑 Authentication Exchange → identity verification
- 📦 Traffic Padding → hide traffic patterns
- 🧭 Routing Control → secure transmission paths
- 🏛️ Notarization → trusted third-party validation
- 🚪 Access Control → enforce permissions

---

## 🧪 Theory — Cryptographic Algorithm Types

### 🧩 Classification Overview

| Type          | Key Usage        | Examples                          | Purpose                     |
| ------------- | ---------------- | --------------------------------- | --------------------------- |
| ♾️ Keyless    | No key           | Hash, PRNG                        | Integrity, randomness       |
| 🔑 Single-Key | Shared secret    | Symmetric encryption, MAC         | Fast encryption + integrity |
| 🔐 Two-Key    | Public + private | Asymmetric encryption, signatures | Secure exchange + identity  |

---

## 🧬 Keyless Algorithms

### 🧾 Hash Function

- 🔄 Converts variable input → fixed-size digest
- 🧬 Used in signatures, MACs

**Properties:**

- ⚡ Fast computation
- 🚫 One-way (irreversible)

---

### 🎲 Pseudorandom Number Generator (PRNG)

- 🎯 Produces _deterministic but random-like_ sequences
- 🔑 Used in key generation, cryptographic protocols

> [!NOTE]
> Weak randomness = broken security.

---

## 🔑 Single-Key Algorithms (Symmetric)

### 🔐 Core Principle

```text
Plaintext + Secret Key → Ciphertext → Decryption (same key)
# One shared key for both operations
```

**System Impact:** Enables fast, efficient encryption for large-scale data.

---

### 🧱 Block Cipher

- 📦 Operates on fixed-size blocks
- 🔗 Depends on previous blocks (mode of operation)

---

### 🌊 Stream Cipher

- 🧵 Operates bit-by-bit
- ⚡ Suitable for real-time data streams

---

### 🧾 Message Authentication Code (MAC)

- 🔑 Combines:
  - 🧬 Hash function
  - 🔐 Secret key

**Workflow:**

```text
Message + Secret Key → MAC → Verify MAC
# Compare computed MAC with received MAC
```

**System Impact:** Ensures message integrity and authenticity efficiently.

---

## 🔐 Two-Key Algorithms (Asymmetric)

### 🔑 Core Principle

```text
Public Key (Encrypt) ↔ Private Key (Decrypt)
# Separate keys for security separation
```

**System Impact:** Enables secure communication without pre-shared secrets.

---

### 🧾 Digital Signature

- ✍️ Generated using private key
- 🔍 Verified using public key

**Guarantees:**

- 🪪 Authenticity
- 🧬 Integrity
- 🚫 Nonrepudiation

---

### 🔄 Key Exchange

- 🔑 Securely share symmetric keys
- ⚡ Used before fast symmetric encryption

---

### 👤 User Authentication

- 🪪 Verifies:
  - User identity
  - System authenticity

> [!IMPORTANT]
> Authentication is the **entry point of all security layers**.

---

## 🔄 Workflow — Secure Communication Stack

```text id="3nv0yx"
User → Authenticate → Key Exchange → Encrypt Data → Verify Integrity
# Identity → Shared secret → Protect → Validate
```

**System Impact:** Establishes trust, confidentiality, and integrity in one continuous flow.

---

## ⚡ Optimization — Choosing the Right Mechanism

### ⚖️ Tradeoff Matrix

| Mechanism     | Strength                 | Weakness                 |
| ------------- | ------------------------ | ------------------------ |
| 🔐 Symmetric  | Fast, efficient          | Key distribution problem |
| 🔐 Asymmetric | Secure key exchange      | Slower performance       |
| 🧬 Hash       | Fast integrity check     | No confidentiality       |
| 🧾 MAC        | Efficient authentication | Requires shared key      |

---

### 🧠 Design Insight

- 🔄 Use **asymmetric → establish trust**
- ⚡ Then **symmetric → scale performance**

> [!IMPORTANT]
> Real systems combine mechanisms—not choose one.

---

## 🏁 Recap — Strategic Takeaways

- 💠 Mechanisms = **execution layer of security**
- 🔄 Reversible → encryption, ♾️ irreversible → hashing
- 🔑 Symmetric = fast, 🔐 asymmetric = secure exchange
- 🧾 MAC + signature = integrity + authenticity
- ⚡ Real-world security = **hybrid cryptography**
