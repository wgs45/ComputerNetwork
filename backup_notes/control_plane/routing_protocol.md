# 🧭 Routing Protocols

### ✨ _How Packets Find Their Way Home_ ✨

> _“A network without routing is like an adventure with no map.”_ 🗺️💫

---

## 🎯 The Sacred Goal of Routing

💡 **Routing protocols exist to find _good paths_**

🔹 From **sending host** ➡️ **receiving host**
🔹 Through a **network of routers**

### 🛤️ What Is a Path?

✔️ A **path** is a _sequence of routers_ that a packet travels through:

```
Host → Router → Router → … → Destination
```

---

## ⭐ What Does “Good” Mean?

✨ A _good path_ can be defined in different ways:

- ⚡ **Fastest** (low delay)
- 💰 **Least cost**
- 🚦 **Least congested**

📌 _The definition depends on what the network operator cares about._

❗ Routing is so hard that it’s often called:

> 🏆 **One of the “Top-10” challenges in networking**

---

## 🧠 Graph Abstraction — Turning Networks into Maps

🗺️ To reason clearly, we **abstract the network as a graph**.

### 🧩 Graph Basics

- 🔵 **Nodes (N)** → Routers
- 🔗 **Edges (E)** → Links between routers
- 🔢 **Link cost** → Weight of each edge

```
G = (N, E)
```

---

## 🧙‍♀️ Routers as Nodes

🟢 **Set of routers:**

```
N = { u, v, w, x, y, z }
```

Each letter is a router living in our little network village 🌱

---

## 🔗 Links as Edges

🟣 **Set of links:**

```
E = {
 (u,v), (u,x), (v,x), (v,w),
 (x,w), (x,y), (w,y), (w,z), (y,z)
}
```

✨ Each pair means _a direct physical or logical connection_.

---

## 💰 Link Costs — The Price of Travel

📌 **Notation:**

- `c(a,b)` = cost of the direct link between router **a** and **b**

🔍 Examples:

- ✔️ `c(w,z) = 5` → direct but expensive
- ❌ `c(u,z) = ∞` → no direct link at all

---

## ⚖️ Who Decides the Cost?

🧑‍💻 **Network operator defines link costs**, such as:

- ⭐ Always `1` (hop count)
- 📶 Inversely related to **bandwidth**
- 🚦 Inversely related to **congestion**

💬 _Same network, different philosophy, different routes._

---

## 🧩 Routing Algorithm Classification

Routing algorithms differ along **two main dimensions** 👇

---

## 🌍 Global vs 🤝 Decentralized

### 🌍 Global Algorithms

✔️ Every router knows:

- Full network topology
- All link costs

🧠 Routers compute routes **independently but with full knowledge**.

✨ Known as:

> 🔵 **Link-State Algorithms**

---

### 🤝 Decentralized Algorithms

✔️ Routers initially know only:

- Costs to **direct neighbors**

🔁 They:

- Exchange information
- Iteratively compute routes

✨ Known as:

> 🟠 **Distance-Vector Algorithms**

---

## ⏳ Static vs 🔄 Dynamic Routing

### 🐢 Static Routing

- Routes change **slowly**
- Often fixed or manually adjusted

---

### ⚡ Dynamic Routing

- Routes change **quickly**
- React to:
  - 🔗 Link cost changes
  - ❌ Failures

📡 Updates happen:

- ⏰ Periodically
- ⚠️ Or when changes occur

---

## 🗂️ Mental Summary Table (In Your Head 💭)

```
Link-State     → Global knowledge
Distance-Vector→ Neighbor knowledge
Static         → Rare changes
Dynamic        → Fast adaptation
```

---

## 🧁 TL;DR — Gentle Recap

✔️ Routing finds **good paths** through routers
✔️ Networks are modeled as **graphs** 🗺️
✔️ **Link costs** guide decisions
✔️ Algorithms can be:

- 🌍 Global (Link-State)
- 🤝 Decentralized (Distance-Vector)
  ✔️ Routes may be **static** or **dynamic**
