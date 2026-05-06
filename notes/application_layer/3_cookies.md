# 🍪 Cookies

---

## 💠 Concept — Intuition (Why Cookies Exist)

HTTP is **stateless** ⚡
→ Every request is independent
→ Server “forgets” you instantly

> [!NOTE]
> Without cookies, login sessions, carts, and personalization would _not exist_.

### 🧠 The Problem

```text
Request 1 → Server (Who are you?)
Request 2 → Server (Still… who are you?)
```

- 💠 No memory across requests
- ❌ No multi-step transaction tracking

---

## 🧪 Theory — Stateful Illusion via Cookies (How it Works)

Cookies simulate **stateful behavior** on top of stateless HTTP ✨

### 🔄 The 4 Components

| Component          | Role                     |
| ------------------ | ------------------------ |
| 📥 Response Header | Server sets cookie       |
| 📤 Request Header  | Client sends cookie back |
| 💾 Browser Storage | Stores cookie locally    |
| 🗄️ Backend DB      | Maps cookie → user data  |

---

### 🔗 Cookie Lifecycle

```text
1. Client → Request (no cookie)
2. Server → Response + Set-Cookie: ID=1678
3. Browser → Saves cookie
4. Client → Future Requests + Cookie: ID=1678
5. Server → Recognizes user via DB
```

---

## 🔄 Workflow — Real Example (E-commerce)

### 🛍️ First Visit

```text
Client → Request → Server
Server → Set-Cookie: user_id=1678
Server → Store (1678 → user profile)
```

---

### 🔁 Returning Visit

```text
Client → Cookie: user_id=1678 → Server
Server → Lookup DB → Personalized response
```

> [!IMPORTANT]
> Cookie = **Identifier**, not the actual user data.

---

## 🛠️ Tooling — HTTP Cookie Headers

### 📥 Server Response

```http
HTTP/1.1 200 OK
Set-Cookie: user_id=1678   # Assign unique identity
```

---

### 📤 Client Request

```http
GET /cart HTTP/1.1
Cookie: user_id=1678       # Send identity back
```

> System Impact: Enables session continuity without modifying HTTP protocol itself.

---

## ⚡ Optimization — Use Cases

### 🎯 What Cookies Enable

- 🔐 Authentication (login sessions)
- 🛒 Shopping carts
- 🎯 Recommendations
- 📬 Session state (e.g., web email)

---

## 🧪 Theory — State Management Strategies

| Approach             | Description             | Trade-off        |
| -------------------- | ----------------------- | ---------------- |
| 💠 Server-side State | Store session on server | Memory overhead  |
| 🍪 Cookie-based      | Store ID on client      | Privacy concerns |

> [!NOTE]
> Cookies shift _state tracking responsibility_ partially to the client.

---

## 🔒 Security & Privacy — The Dark Side

### ⚠️ Privacy Concerns

- 🍪 Track user behavior across sessions
- 🌐 Third-party cookies track across sites

```text
Site A → Cookie ID 123
Site B → Same Cookie ID 123 → Tracking
```

> [!IMPORTANT]
> Cookies can build detailed behavioral profiles without explicit user awareness.

---

### 🛡️ Key Risks

- ❌ Session hijacking
- ❌ Tracking & profiling
- ❌ Sensitive data exposure (if misused)

---

## 🔄 Workflow — Stateful vs Stateless Thinking

### ⚖️ Comparison

| Feature         | Stateless HTTP | Cookie-Based |
| --------------- | -------------- | ------------ |
| Memory          | ❌ None        | ✅ Simulated |
| Complexity      | ✅ Simple      | ⚡ Moderate  |
| Personalization | ❌ No          | ✅ Yes       |

---

## 🏁 Recap — Takeaways

- 💠 HTTP alone cannot maintain state
- 🍪 Cookies add **memory via identifiers**
- 🔄 Workflow: Set → Store → Send → Identify
- 🛠️ Enables sessions, carts, auth
- 🔒 Trade-off: privacy & security risks
