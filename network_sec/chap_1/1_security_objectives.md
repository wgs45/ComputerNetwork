# 🌌 Security Objectives & Challenges 🔒

---

## 💠 Concept — Information & Network Security (Why)

**Information Security** protects the _essence of data existence_:

- 🔐 Confidentiality → prevent unauthorized access
- 🧬 Integrity → ensure correctness & trustworthiness
- ⚡ Availability → ensure timely access

> [!NOTE]
> These three form the **CIA Triad**, the core of all security design.

**Extended Properties** (beyond CIA):

- 🪪 Authenticity → verify identity
- 🧾 Accountability → trace actions to entities
- 🚫 Nonrepudiation → no denial of actions
- 🔁 Reliability → consistent system behavior

---

**Network Security** protects the _infrastructure layer_:

- 🌐 Prevent unauthorized modification, destruction, disclosure
- 📡 Ensure services operate correctly
- ⚙️ Avoid harmful side effects

> [!IMPORTANT]
> Security is not just protection—it’s also **assurance of correct behavior**.

---

## 🧪 Theory — Core Security Objectives (How)

### 🔐 CIA Triad Breakdown

| Objective          | Purpose                      | Key Risk if Broken        |
| ------------------ | ---------------------------- | ------------------------- |
| 🔐 Confidentiality | Hide sensitive data          | Data leaks / privacy loss |
| 🧬 Integrity       | Prevent unauthorized changes | Corruption / tampering    |
| ⚡ Availability    | Ensure system accessibility  | Downtime / denial         |

---

### 🧬 Integrity Deep Dive

**1. Data Integrity**

- 🧾 Data changed only in authorized ways
- 🪪 Authenticity → data is genuine
- 🚫 Nonrepudiation → proof of origin & delivery

**2. System Integrity**

- ⚙️ System performs intended function correctly
- 🛡️ Protected from unauthorized manipulation

> [!NOTE]
> Integrity is both **data correctness** and **system trustworthiness**.

---

### ⚡ Availability

- ⏱️ Systems respond promptly
- 🚪 Access is granted to authorized users

> [!IMPORTANT]
> Even a perfectly secure system is useless if it’s unavailable.

---

## 🔄 Workflow — Security Objectives in Practice

```text
User Request → Authentication → Authorization → Resource Access → Logging
# Verify identity → Check permissions → Allow/deny → Record action
```

**System Impact:** Ensures every access is controlled, traceable, and secure.

---

## 🛠️ Tooling — Security Mechanisms

- 🔑 Encryption → confidentiality
- 🧾 Digital signatures → integrity + nonrepudiation
- 🔐 Access control systems → authorization
- 📊 Monitoring systems → accountability

> [!NOTE]
> Security is **multi-layered**, not a single tool or algorithm.

---

## ⚡ Optimization — Computer Security Challenges

### 🧠 Core Realities

1. 🎭 **Deceptive Simplicity**
   - Easy to define, hard to implement

2. 🕵️ **Adversarial Thinking**
   - Attackers exploit _unexpected angles_

3. 🔄 **Counterintuitive Design**
   - Secure solutions may feel unnatural

---

### ⚙️ System Design Challenges

1. 📍 **Placement Problem**
   - Where to apply security controls?

2. 🔑 **Key Management Problem**
   - Create, distribute, protect secrets

3. ⚔️ **Asymmetric Battle**
   - Attacker: 1 weakness needed
   - Defender: must secure everything

---

### 🧑‍💻 Human & Organizational Factors

1. 💸 **Delayed Value Perception**
   - Security seen as useless until failure

2. 📡 **Continuous Monitoring Need**
   - Hard in overloaded environments

3. 🏗️ **Late Integration Mistake**
   - Security added _after_ system design

4. ⚡ **Usability vs Security Tradeoff**

- Strong security can reduce convenience

> [!IMPORTANT]
> The strongest systems integrate security **from day zero**, not as a patch.

---

## 🏁 Recap — Strategic Takeaways

- 💠 **CIA Triad = Foundation** of all security systems
- 🧬 **Integrity = Data + System correctness**
- ⚡ **Availability defines usability**
- 🔄 **Security = layered + continuous process**
- ⚔️ **Security is a mindset battle, not just technology**
