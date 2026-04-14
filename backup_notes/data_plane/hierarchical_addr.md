# 🌐✨ **Hierarchical Addressing — Elegant Routing Grimoire** ✨🌐

_“Routing becomes simpler when the world is grouped into meaningful realms.”_ 💞

---

# 🧭 **1. What Is Hierarchical Addressing?**

Hierarchical addressing is like organizing the world into **regions → cities → neighborhoods** so messages don’t get lost~ 🗺️✨

It allows:

- ✔️ **Efficient routing**
- ✔️ **Smaller routing tables**
- ✔️ **Route aggregation** (bundling many routes into one)
- ✔️ **Easy provider-level announcements**

---

# 🏛️ **2. Route Aggregation — Bundling Many into One**

_Imagine an ISP acting like a queen sending a single royal decree for many villages at once._ 👑💌

### 🌟 Scenario

Multiple organizations have nearby address blocks:

- Org 0 → **200.23.16.0/23**
- Org 1 → **200.23.18.0/23**
- Org 2 → **200.23.20.0/23**
- …
- Org 7 → **200.23.30.0/23**

These are all handled by **Fly-By-Night-ISP**.

Instead of announcing each /23 individually, the ISP proudly declares:

> **“Send me anything beginning with 200.23.16.0/20!”** ✨

💡 Because `/20` covers ALL of these ranges at once — it’s a _super-block_.

### 🧙 Why This Matters

- Fewer routes → routers run faster
- Simpler updates → fewer mistakes
- Cleaner Internet routing tables 🌸

---

## ✨ **TL;DR — Route Aggregation**

⭐ ISPs combine multiple smaller networks into one bigger announcement
⭐ Saves space, reduces clutter, improves routing
⭐ `/20` can represent many `/23` blocks at once

---

# 🔍 **3. More Specific Routes — When a Village Moves**

### 💔📦 Organization 1 moves away!

Org 1 (200.23.18.0/23) switches from **Fly-By-Night-ISP** → **ISPs-R-Us**.

### 🪄 What happens?

ISPs-R-Us announces two things:

1. Their normal big range:

   > “Send me anything beginning with **199.31.0.0/16**.”

2. PLUS a new, precise route:

   > “Also send me **200.23.18.0/23** specifically.”

This is called a **more specific route**.

### 🌈 Why routers care

Routers always prefer:
✔️ **More specific** (longer prefix) routes
over
✖️ More general (shorter prefix) ones

So even though Fly-By-Night-ISP still announces the big `/20`,
ISPs-R-Us’s `/23` wins because it's more specific.

This ensures all traffic for **Org 1** reaches the correct new home 💞

---

## 🗂️ Updated Routing Logic

- “200.23.16.0/20” → still goes to Fly-By-Night-ISP
- **“200.23.18.0/23” → goes to ISPs-R-Us** (highest priority)

Routers: _“Aha! The `/23` is more exact!”_ 😤✨

---

## ✨ **TL;DR — More Specific Routing**

⭐ When a network moves, the new ISP advertises a narrower prefix
⭐ Routers choose the **longest prefix match**
⭐ Specific beats general — like finding a precise apartment number instead of a whole street 🌸
