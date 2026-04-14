# 🧠 Link-State Routing

### ✨ _Dijkstra’s Algorithm — Finding the Purest Path_ ✨

> _“When every node knows the whole world, the shortest path reveals itself.”_ 🌟

---

## 🎯 What Is Link-State Routing?

💡 **Core Idea:** Every router has a **complete map of the network** 🗺️

✔️ Achieved by:

- 📡 **Link-state broadcast**
- All routers share:
  - Full topology
  - All link costs

✨ Result:

> 🌍 **All nodes have the same global information**

---

## 🧙‍♂️ Dijkstra’s Link-State Algorithm

🌸 Think of Dijkstra as a **gentle strategist**, expanding known safe paths step by step.

### ⭐ What It Computes

- 🧮 **Least-cost paths** from one source node (u)
- 🎁 Produces:
  - 🌳 Least-cost-path tree
  - 📋 Forwarding table for the source router

---

## 🔤 Notation (Spellbook Symbols 📜)

🔹 `c(x,y)` → direct link cost from x to y

- ❌ = ∞ if not direct neighbors

🔹 `D(v)` → current estimate of least-cost path from source to v

🔹 `p(v)` → predecessor of v on the current best path

🔹 `N'` → set of nodes whose **least-cost path is finalized** ⭐

---

## 🔁 Algorithm Intuition (Before Steps)

💭 Start small.
💭 Lock in the _closest_ node.
💭 Expand outward, carefully.

✨ One node at a time, the shortest-path tree grows.

---

## 🧩 Dijkstra’s Algorithm — Step by Step

### 🟢 1️⃣ Initialization

- Start at **source node u**
- Initialize:

```
N' = {u}
```

For every other node `v`:

- ✔️ If `v` is adjacent to `u` → `D(v) = c(u,v)`
- ❌ Else → `D(v) = ∞`

📌 _At this stage, u only knows its neighbors._

---

### 🔄 2️⃣ Main Loop (The Heartbeat 💓)

Repeat until **all nodes are in N'**:

1️⃣ Find node `w` **not in N'** with smallest `D(w)`
2️⃣ Add `w` to `N'` ⭐
3️⃣ Update neighbors of `w`:

```
D(v) = min( D(v), D(w) + c(w,v) )
```

💡 Meaning:

- Either keep the old best path
- Or go through `w` if it’s cheaper ✨

---

## 🧪 Example — Watching the Magic Happen

### 🪄 Step 0 — Initialization

- `N' = {u}`
- Set `D(a) = c(u,a)` for neighbors
- Others are ∞

---

### 🪄 Each Iteration

✔️ Pick closest node not yet finalized
✔️ Lock it into `N'`
✔️ Relax edges to its neighbors

📈 Gradually, the table fills with real distances and predecessors.

---

## 🌳 Result: Least-Cost-Path Tree

✨ By tracing `p(v)` for each node:

- You get a **tree rooted at u** 🌳
- Every branch is the cheapest known route

💬 _Ties can happen — break them arbitrarily._

---

## 📋 Forwarding Table (From the Tree)

📌 **Router u only needs to know the next hop!**

Example intuition:

- Destination `v` → send directly `(u,v)`
- Destination `x, y, w, z` → forward via `x`

🧡 _Simple table, powerful routing._

---

## ⚙️ Algorithm Cost (Reality Check)

### ⏱️ Time Complexity

- n nodes
- n iterations × n checks

⭐ Complexity:

- 🐢 Basic: `O(n²)`
- ⚡ Optimized (heaps): `O(n log n)`

---

### 📡 Message Complexity

- Each router broadcasts link-state info
- Broadcast cost: `O(n)` link crossings
- Total message cost:

⭐ **Overall: `O(n²)`**

---

## ⚠️ A Subtle Danger: Route Oscillations

😵 When **link costs depend on traffic volume**, strange things happen…

### 🌊 What Goes Wrong?

- Traffic changes → link costs change
- New shortest paths chosen
- Traffic shifts again
- 🔁 Costs change again

💥 Result:

> ❗ **Routing oscillations** (never settles!)

---

## 🌀 Oscillation Scenario (Intuition Only)

✨ Routers repeatedly recompute routes:

- Given costs → compute routes
- Routes → change traffic
- Traffic → changes costs
- Costs → trigger recomputation

🧠 _A feedback loop emerges._

---

## 🧁 TL;DR — Gentle Recap

✔️ Link-State routing uses **global knowledge** 🌍
✔️ Dijkstra computes **least-cost paths** from one source
✔️ Builds a **shortest-path tree** 🌳
✔️ Time complexity: `O(n²)` (or `O(n log n)` optimized)
✔️ Beware of **traffic-dependent cost oscillations** ⚠️
