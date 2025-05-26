# 📘 Phase 1: Understanding the Concepts



## 🔌 Equivalent Resistance Rules

Understanding how resistors combine is fundamental before translating circuits into graph models.

### ➕ Series Connection

- Resistors are in **series** if they are connected end-to-end with no branching.
- The **equivalent resistance** is the **sum** of the individual resistances:

$$
R_{\text{eq(series)}} = R_1 + R_2 + R_3 + \dots + R_n
$$

- **Current** through each resistor is the same.
- **Voltage** divides across resistors.

---

### 🔁 Parallel Connection

- Resistors are in **parallel** if both ends are connected to the same two nodes.
- The reciprocal of the **equivalent resistance** is the **sum** of reciprocals:

$$
\frac{1}{R_{\text{eq(parallel)}}} = \frac{1}{R_1} + \frac{1}{R_2} + \frac{1}{R_3} + \dots + \frac{1}{R_n}
$$

- **Voltage** across each resistor is the same.

- **Current** divides among the resistors.

---

## 📈 Circuit-to-Graph Mapping


To apply graph theory, we convert the electrical circuit into a mathematical graph:

- **Nodes** represent **junctions** in the circuit.

- **Edges** represent **resistors**, with the edge **weight** equal to the resistor’s resistance (in ohms, $\Omega$).

### 🧠 Key Concepts

- A resistor between two junctions is modeled as an **undirected weighted edge** between two nodes.
- The full circuit becomes a **weighted undirected graph** $G = (V, E)$, where:

- $V$ is the set of junctions (vertices),

- $E$ is the set of resistors (edges with weights).

---

### ✅ Benefits of Graph Representation

- **Structured and algorithmic** simplification.
- Supports complex topologies and nested resistor configurations.
- Enables usage of algorithms from **graph theory**, such as traversal, cycle detection, and graph reduction.

---

## 🧭 Summary

By understanding how resistors combine and how to represent circuits as graphs, we lay the groundwork for designing an **algorithm** that can automate the process of finding equivalent resistance—even in complex, nested networks.

---

# ✅ Phase 2: Develop the Algorithm (Conceptual Level)


## 🔍 Objective

We aim to design an algorithm that calculates the **equivalent resistance** of a complex circuit represented as a **graph**. The method must iteratively **detect**, **simplify**, and **combine** resistors until the graph reduces to a single equivalent resistance between two terminals.

---

## 🧠 Key Concepts

### ➕ Series Connection Detection

![alt text](image-1.png)

---

- A **series** configuration occurs when:
  - Two resistors share a **common node** of **degree 2**.
  - No branching occurs at this node.
- The equivalent resistance for series:
  
  $$
  R_{\text{eq}} = R_1 + R_2
  $$

---

### 🔁 Parallel Connection Detection

![alt text](image-2.png)

---

- A **parallel** configuration exists when:
  - **Multiple edges** connect the **same pair of nodes**.
- The equivalent resistance for parallel:

$$
\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
$$

---

## 🔁 Iterative Graph Simplification

We apply the following logic **iteratively** until the entire graph reduces to a **single edge** representing the total equivalent resistance:

1. Detect **series** resistor pairs and combine.
2. Detect **parallel** resistor groups and combine.
3. Replace each group with its **equivalent resistance**.
4. Repeat until no more simplifications are possible.

---

## 🧾 Pseudocode: Resistance Reduction Algorithm

```pseudo
function compute_equivalent_resistance(graph G):
    while G has more than two nodes:
        for each node v in G:
            if degree(v) == 2:
                u, w = neighbors of v
                if edge(u, v) and edge(v, w) exist:
                    R1 = weight of edge(u, v)
                    R2 = weight of edge(v, w)
                    replace with edge(u, w) with weight R1 + R2
                    remove node v and its incident edges
        for each pair of nodes (u, v):
            if multiple edges exist between u and v:
                Let R1, R2, ..., Rn be the weights of all edges(u, v)
                compute R_eq using:
                    1 / R_eq = 1 / R1 + 1 / R2 + ... + 1 / Rn
                replace all edges(u, v) with a single edge of weight R_eq
    return weight of final edge between terminals
```

---

## 🔄 Handling Nested Combinations

![alt text](image-3.png)
---

- **Nested structures** (e.g. series within parallel) are simplified **recursively** or by **repeated iteration**.
- The graph is dynamically updated:
  - Merging two resistors may enable a new parallel pattern.
  - Re-check after each merge.

---


## ✅ Summary

This algorithm provides a robust and scalable method for calculating the **equivalent resistance** in arbitrary networks by:

- Modeling the circuit as a graph.
- Identifying structural patterns (series, parallel).
- Reducing them iteratively using physics-based rules.

The approach is suitable for both **manual analysis** and **automated implementations** in tools like Python with `networkx`.

---

# ✅ Phase 3: Work on Examples


## 🔍 Goal

To demonstrate how the algorithm simplifies real-world circuit cases, we analyze **three examples**:

1. Pure Series Resistors  
2. Pure Parallel Resistors  
3. Nested Configuration (Series and Parallel combined)

Each example includes a description, circuit logic, and a step-by-step simplification.

---

## 🔸 Example 1: Series Resistors

### 🧩 Description

Three resistors connected **in series** between two nodes A and D.

- **Components**:

- $R_1 = 5\ \Omega$

- $R_2 = 10\ \Omega$

 - $R_3 = 15\ \Omega$

- **Connection**: A — R₁ — B — R₂ — C — R₃ — D

### ⚙️ Simplification Logic

- Series resistors are **linearly connected**:
  
$$
R_{\text{eq}} = R_1 + R_2 + R_3 = 5 + 10 + 15 = 30\ \Omega
$$

- Algorithm detects each degree-2 node and collapses them iteratively:
  - Combine A–B and B–C into A–C
  - Then combine A–C and C–D into A–D

---

## 🔸 Example 2: Parallel Resistors

### 🧩 Description

Two resistors connected **in parallel** between nodes A and B.

- **Components**:

- $R_1 = 10\ \Omega$

- $R_2 = 20\ \Omega$

- **Connection**:
- Path 1: A → R₁ → B  

- Path 2: A → R₂ → B

### ⚙️ Simplification Logic

- Parallel resistors are connected across the **same two nodes**:

$$
\frac{1}{R_{\text{eq}}} = \frac{1}{10} + \frac{1}{20} = \frac{3}{20}
\Rightarrow R_{\text{eq}} = \frac{20}{3} \approx 6.67\ \Omega
$$

- Algorithm groups all edges between A and B, replaces them with the calculated equivalent resistance.

---

## 🔸 Example 3: Nested Configuration (Series + Parallel)

### 🧩 Description

- $R_1 = 5\ \Omega$ (A → B)  

- $R_2 = 10\ \Omega$ (B → C)  

- $R_3 = 20\ \Omega$ (B → C) — **parallel to R₂**  

- $R_4 = 5\ \Omega$ (C → D)

### 🛠 Structure:

- A — R₁ — B  
- B → R₂ → C  
- B → R₃ → C (in parallel with R₂)  
- C → R₄ → D

### ⚙️ Simplification Logic

1. **Parallel between B–C**:
$$
\frac{1}{R_{BC}} = \frac{1}{10} + \frac{1}{20} = \frac{3}{20}
\Rightarrow R_{BC} = \frac{20}{3} \approx 6.67\ \Omega
$$

2. **New path** becomes:

- A — R₁ — B — $R_{BC}$ — C — R₄ — D

3. **Series total**:

$$
R_{\text{eq}} = R_1 + R_{BC} + R_4 = 5 + \frac{20}{3} + 5 = \frac{50}{3} \approx 16.67\ \Omega
$$

- The algorithm reduces:

- Parallel group → replaces with $R_{BC}$

- Remaining series → collapsed step-by-step

## Visual

![alt text](image-4.png)

---

![alt text](image-6.png)

---

![alt text](image-11.png)

---

![alt text](image-12.png)

---

![alt text](image-13.png)



## ✅ Summary

| Type          | Formula Used                                 | Result             |
|---------------|-----------------------------------------------|--------------------|
| Series        | $R_{\text{eq}} = R_1 + R_2 + \dots + R_n$     | $30\ \Omega$       |
| Parallel      | $\frac{1}{R_{\text{eq}}} = \sum \frac{1}{R_i}$| $6.67\ \Omega$     |
| Nested        | Series + Parallel combination                 | $16.67\ \Omega$    |

These examples validate how graph-based simplification can be used to iteratively reduce circuits of arbitrary complexity using consistent rules and clear patterns.

--- 

# ✅ Phase 4: Analyze the Algorithm

---

## 📊 Efficiency Evaluation

Understanding the computational efficiency of the graph-based resistance simplification algorithm is key for scaling to large networks.

### 🔄 Number of Steps

- Let $n$ be the number of **nodes**, and $m$ be the number of **edges** (resistors).

- In the **worst case**, the algorithm performs:

- $O(n)$ passes for series simplifications.

- $O(m)$ checks for parallel edge reductions.

### 📉 Complexity of Series/Parallel Detection

#### ➕ Series Detection:

- For each node $v$:

- Check if $\text{deg}(v) = 2$

- Cost: $O(n)$ per pass

- If two neighbors $u$ and $w$ are connected to $v$:

- Combine $R_{uv}$ and $R_{vw}$ into $R_{uw}$

- Time per operation: $O(1)$

- **Total complexity** (series-only): $O(n^2)$ in worst case due to repeated passes.

#### 🔁 Parallel Detection:

- For each unordered pair of nodes $(u, v)$:
  - Collect all edges between them: $O(m)$
  - Reduce them using:

$$
\frac{1}{R_{\text{eq}}} = \sum_{i=1}^{k} \frac{1}{R_i}
$$

- **Total complexity** (parallel-only): $O(m^2)$ worst case for densely connected graphs.

---

## ⚠️ Limitations

### 🧩 Edge Cases & Complex Cycles

- The current algorithm assumes:
  - Graph is **connected**.
  - No **dependent sources** or **nonlinear elements** (e.g., capacitors, inductors).
- **Bridging nodes** (nodes that are part of multiple paths) may delay detection of simplification patterns.
- Circuits with **cycles that are not purely parallel** can be harder to simplify without advanced techniques (e.g., mesh analysis).

---



### 📈 Visualization 

![alt text](<circuit_simplification (1).gif>)
---

## ✅ Summary

| Aspect              | Summary                                                                 |
|---------------------|-------------------------------------------------------------------------|
| Series Detection    | Fast per step, repeated passes required ($O(n^2)$ worst case)           |
| Parallel Detection  | Simple but costly in dense graphs ($O(m^2)$ worst case)                 |
| Limitations         | Cannot directly solve meshes, bridges, or nonlinear elements            |
| Improvements        | DFS, union-find, real-time animation, and better data structures        |

This phase ensures the algorithm isn't just **correct**, but also **efficient**, **scalable**, and **educationally valuable** in practice.

## Python Codes

```python
import matplotlib.pyplot as plt
import matplotlib.patches as patches
import matplotlib.animation as animation

# Resistor values (Ohms)
resistor_values = {
    "R1": 10,
    "R2": 20,
    "R3": 30,
    "R4": 40,
    "R5": 50,
    "R23": 1 / (1 / 20 + 1 / 30),
    "R45": 40 + 50,
    "R123": 10 + (1 / (1 / 20 + 1 / 30)),
    "R12345": 10 + (1 / (1 / 20 + 1 / 30)) + 40 + 50
}

positions = {
    "B+": (0, 2),
    "R1": (2, 0.5),
    "R2": (2, 3.5),
    "R3": (4, 3.5),
    "R4": (6, 2),
    "R5": (8, 2),
    "R23": (3, 3.5),
    "R45": (7, 2),
    "R123": (3, 2),
    "R12345": (4.5, 2),
    "B-": (10, 2)
}

steps = [
    {
        "title": "🔰 Step 0: Initial Circuit",
        "boxes": ["B+", "R1", "R2", "R3", "R4", "R5", "B-"],
        "lines": [("B+", "R2"), ("R2", "R3"), ("R3", "R4"),
                  ("B+", "R1"), ("R1", "R4"), ("R4", "R5"), ("R5", "B-")],
        "highlight": [],
        "label_lines": {
            ("B+", "R2"): "R2", ("R2", "R3"): "R3", ("R3", "R4"): "R4",
            ("B+", "R1"): "R1", ("R1", "R4"): "R4", ("R4", "R5"): "R5", ("R5", "B-"): "R5"
        },
        "formula": "R23 = (R2 || R3) = 12.00Ω"
    },
    {
        "title": "🔁 Step 1: Combine R2 || R3 → R23",
        "boxes": ["B+", "R1", "R23", "R4", "R5", "B-"],
        "lines": [("B+", "R23"), ("R23", "R4"),
                  ("B+", "R1"), ("R1", "R4"), ("R4", "R5"), ("R5", "B-")],
        "highlight": ["R23"],
        "label_lines": {
            ("B+", "R23"): "R23", ("R23", "R4"): "R23",
            ("B+", "R1"): "R1", ("R1", "R4"): "R4", ("R4", "R5"): "R5", ("R5", "B-"): "R5"
        },
        "formula": "R45 = R4 + R5 = 90.00Ω"
    },
    {
        "title": "🔁 Step 2: Combine R4 + R5 → R45",
        "boxes": ["B+", "R1", "R23", "R45", "B-"],
        "lines": [("B+", "R23"), ("R23", "R45"),
                  ("B+", "R1"), ("R1", "R45"), ("R45", "B-")],
        "highlight": ["R45"],
        "label_lines": {
            ("B+", "R23"): "R23", ("R23", "R45"): "R23",
            ("B+", "R1"): "R1", ("R1", "R45"): "R4", ("R45", "B-"): "R45"
        },
        "formula": "R123 = R1 + R23 = 22.00Ω"
    },
    {
        "title": "🔁 Step 3: Combine R1 + R23 → R123",
        "boxes": ["B+", "R123", "R45", "B-"],
        "lines": [("B+", "R123"), ("R123", "R45"), ("R45", "B-")],
        "highlight": ["R123"],
        "label_lines": {
            ("B+", "R123"): "R123", ("R123", "R45"): "R123", ("R45", "B-"): "R45"
        },
        "formula": "R12345 = R123 + R45 = 112.00Ω"
    },
    {
        "title": "✅ Final Result: R12345",
        "boxes": ["B+", "R12345", "B-"],
        "lines": [("B+", "R12345"), ("R12345", "B-")],
        "highlight": ["R12345"],
        "label_lines": {
            ("B+", "R12345"): "R12345", ("R12345", "B-"): "R12345"
        },
        "formula": "R_eq = 112.00Ω"
    }
]

highlight_colors = {
    "R23": "#FF6F61",
    "R45": "#76D7C4",
    "R123": "#85C1E9",
    "R12345": "#DDA0DD"
}

# Draw frame for animation
def draw_frame(i):
    step = steps[i]
    ax.clear()
    ax.set_xlim(-1, 11)
    ax.set_ylim(-1, 5)
    ax.axis("off")
    ax.set_title(step["title"], fontsize=13, pad=10, weight='bold', color="#2C3E50")

    for box in step["boxes"]:
        x, y = positions[box]
        color = highlight_colors.get(box, "#D6DBDF") if box in step["highlight"] else "#F2F4F4"
        rect = patches.FancyBboxPatch((x - 0.3, y - 0.3), 0.6, 0.6,
                                      boxstyle="round,pad=0.1", edgecolor="#2C3E50",
                                      facecolor=color, linewidth=2)
        ax.add_patch(rect)
        ax.text(x, y, box, ha="center", va="center", fontsize=9, weight="bold", color="#34495E")

    for u, v in step["lines"]:
        x1, y1 = positions[u]
        x2, y2 = positions[v]
        mx, my = (x1 + x2) / 2, (y1 + y2) / 2
        ax.annotate("",
                    xy=(x2, y2), xytext=(x1, y1),
                    arrowprops=dict(arrowstyle="->", lw=2, color="#566573"))

        if "label_lines" in step:
            key = (u, v) if (u, v) in step["label_lines"] else (v, u)
            rname = step["label_lines"].get(key)
            if rname and rname in resistor_values:
                rlabel = f"R = {resistor_values[rname]:.2f}Ω"
                ax.text(mx, my + 0.25, rlabel, ha="center", va="center",
                        fontsize=9, color="#7D3C98", weight='bold')

    ax.text(0, -0.5, step["formula"], fontsize=10, weight='bold', color='#1F618D')

# Create the animation
fig, ax = plt.subplots(figsize=(11, 4.5))
ani = animation.FuncAnimation(fig, draw_frame, frames=len(steps), interval=1500, repeat=True)

# Save to GIF
gif_path = "/content/circuit_simplification.gif"
ani.save(gif_path, writer="pillow", fps=1)

from IPython.display import Image
Image(filename=gif_path)
```
---

```python
# ✅ Final Clean Circuit Diagrams with Small Fonts and Beautiful Layout
import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Resistor values (Ohms)
resistor_values = {
    "R1": 10,
    "R2": 20,
    "R3": 30,
    "Req_series": 10 + 20 + 30,
    "Req_parallel": 1 / (1 / 10 + 1 / 20)
}

# Layouts with wider spacing
positions_series = {
    "A": (0, 2),
    "R1": (2, 2),
    "R2": (4, 2),
    "R3": (6, 2),
    "Req": (4, 2),
    "B": (8, 2)
}

positions_parallel = {
    "A": (0, 2),
    "R1": (2, 3.2),
    "R2": (2, 0.8),
    "Req": (2, 2),
    "B": (4, 2)
}

highlight_colors = {"Req": "#BB8FCE"}

line_labels_series = {
    ("A", "R1"): "R1",
    ("R1", "R2"): "R2",
    ("R2", "R3"): "R3",
    ("R3", "B"): "R3"
}

line_labels_parallel = {
    ("A", "R1"): "R1",
    ("R1", "B"): "R1",
    ("A", "R2"): "R2",
    ("R2", "B"): "R2"
}

# Drawing function
def draw_valued_circuit(title, boxes, lines, highlight=[], positions=None, line_labels=None, note="", formula=""):
    fig, ax = plt.subplots(figsize=(11, 5))
    ax.set_xlim(-1, 9)
    ax.set_ylim(-0.5, 5.5)
    ax.axis("off")
    ax.set_title(title, fontsize=13, pad=10, weight='bold', color="#2C3E50")

    # Boxes
    for box in boxes:
        x, y = positions[box]
        color = highlight_colors.get(box, "#D6DBDF") if box in highlight else "#F2F4F4"
        rect = patches.FancyBboxPatch(
            (x - 0.3, y - 0.3), 0.6, 0.6,
            boxstyle="round,pad=0.1",
            edgecolor="#2C3E50",
            facecolor=color,
            linewidth=1.8
        )
        ax.add_patch(rect)
        ax.text(x, y, box, ha="center", va="center", fontsize=9, weight='bold', color="#34495E")

    # Arrows + edge labels
    for u, v in lines:
        x1, y1 = positions[u]
        x2, y2 = positions[v]
        mx, my = (x1 + x2) / 2, (y1 + y2) / 2

        ax.annotate("",
            xy=(x2, y2), xytext=(x1, y1),
            arrowprops=dict(arrowstyle="->", lw=2, color="#566573"))

        if line_labels:
            key = (u, v) if (u, v) in line_labels else (v, u)
            if key in line_labels:
                rname = line_labels[key]
                if rname in resistor_values:
                    rlabel = f"R = {resistor_values[rname]:.2f}Ω"
                    offset = 0.25 if abs(y2 - y1) < 0.1 else 0.15
                    ax.text(mx, my + offset, rlabel, ha="center", va="center",
                            fontsize=9, color="#7D3C98", weight='bold')

    ax.text(0, -0.2, note, fontsize=9, style='italic', color='gray')
    ax.text(0, -0.45, formula, fontsize=10, weight='bold', color='#1F618D')
    plt.tight_layout()
    plt.show()

# Values
R1, R2, R3 = resistor_values["R1"], resistor_values["R2"], resistor_values["R3"]
R_eq_series = resistor_values["Req_series"]
R_eq_parallel = resistor_values["Req_parallel"]

# Series Step 1
draw_valued_circuit(
    "🔰 Series Connection – Step 1",
    ["A", "R1", "R2", "R3", "B"],
    [("A", "R1"), ("R1", "R2"), ("R2", "R3"), ("R3", "B")],
    positions=positions_series,
    line_labels=line_labels_series,
    note="Three resistors connected in series.",
    formula=f"R_eq = {R1}Ω + {R2}Ω + {R3}Ω = {R_eq_series:.2f}Ω"
)

# Series Step 2
draw_valued_circuit(
    "✅ Series Connection – Step 2: Simplified Req",
    ["A", "Req", "B"],
    [("A", "Req"), ("Req", "B")],
    highlight=["Req"],
    positions=positions_series,
    note="Replaced with equivalent Req.",
    formula=f"R_eq = {R_eq_series:.2f}Ω"
)

# Parallel Step 1
draw_valued_circuit(
    "🔰 Parallel Connection – Step 1",
    ["A", "R1", "R2", "B"],
    [("A", "R1"), ("R1", "B"), ("A", "R2"), ("R2", "B")],
    positions=positions_parallel,
    line_labels=line_labels_parallel,
    note="Two resistors connected in parallel.",
    formula=f"1/R_eq = 1/{R1} + 1/{R2} → R_eq = {R_eq_parallel:.2f}Ω"
)

# Parallel Step 2
draw_valued_circuit(
    "✅ Parallel Connection – Step 2: Simplified Req",
    ["A", "Req", "B"],
    [("A", "Req"), ("Req", "B")],
    highlight=["Req"],
    positions=positions_parallel,
    note="Replaced with equivalent Req.",
    formula=f"R_eq = {R_eq_parallel:.2f}Ω"
)
```
---

```python
# ✅ Final Nested Circuit Simplification with R = xxΩ Labels (Colab-ready)
import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Resistor values (Ohms)
resistor_values = {
    "R1": 10,
    "R2": 20,
    "R3": 30,
    "R4": 40,
    "R23": 1 / (1 / 20 + 1 / 30),
    "R123": 10 + (1 / (1 / 20 + 1 / 30)),
    "R1234": 10 + (1 / (1 / 20 + 1 / 30)) + 40
}

# Node positions
positions = {
    "A": (0, 2),
    "R1": (1.5, 2),
    "R2": (3, 3.5),
    "R3": (3, 0.5),
    "R23": (3, 2),
    "R4": (4.5, 2),
    "R123": (2.25, 2),
    "R1234": (3.75, 2),
    "B": (6, 2)
}

# Drawing steps
steps = [
    {
        "title": "🔰 Step 0: Initial Nested Circuit",
        "boxes": ["A", "R1", "R2", "R3", "R4", "B"],
        "lines": [("A", "R1"), ("R1", "R2"), ("R1", "R3"),
                  ("R2", "R4"), ("R3", "R4"), ("R4", "B")],
        "highlight": [],
        "label_lines": {
            ("A", "R1"): "R1", ("R1", "R2"): "R2", ("R1", "R3"): "R3", ("R4", "B"): "R4"
        },
        "formula": "1/R23 = 1/R2 + 1/R3 → R23 = 12.00Ω"
    },
    {
        "title": "🔁 Step 1: R2 || R3 → R23",
        "boxes": ["A", "R1", "R23", "R4", "B"],
        "lines": [("A", "R1"), ("R1", "R23"), ("R23", "R4"), ("R4", "B")],
        "highlight": ["R23"],
        "label_lines": {
            ("A", "R1"): "R1", ("R1", "R23"): "R23", ("R23", "R4"): "R23", ("R4", "B"): "R4"
        },
        "formula": "R123 = R1 + R23 = 10Ω + 12Ω = 22.00Ω"
    },
    {
        "title": "🔁 Step 2: R1 + R23 → R123",
        "boxes": ["A", "R123", "R4", "B"],
        "lines": [("A", "R123"), ("R123", "R4"), ("R4", "B")],
        "highlight": ["R123"],
        "label_lines": {
            ("A", "R123"): "R123", ("R123", "R4"): "R123", ("R4", "B"): "R4"
        },
        "formula": "R1234 = R123 + R4 = 22Ω + 40Ω = 62.00Ω"
    },
    {
        "title": "✅ Step 3: R123 + R4 → R1234",
        "boxes": ["A", "R1234", "B"],
        "lines": [("A", "R1234"), ("R1234", "B")],
        "highlight": ["R1234"],
        "label_lines": {
            ("A", "R1234"): "R1234"
        },
        "formula": "R_eq = 62.00Ω"
    }
]

# Highlight colors
highlight_colors = {
    "R23": "#F1948A",
    "R123": "#5DADE2",
    "R1234": "#BB8FCE"
}

# Drawing function
def draw_nested_step(step):
    fig, ax = plt.subplots(figsize=(10, 4.5))
    ax.set_xlim(-1, 7)
    ax.set_ylim(-1, 5)
    ax.axis("off")
    ax.set_title(step["title"], fontsize=13, pad=10, weight='bold', color="#2C3E50")

    for box in step["boxes"]:
        x, y = positions[box]
        color = highlight_colors.get(box, "#D6DBDF") if box in step["highlight"] else "#F2F4F4"
        rect = patches.FancyBboxPatch((x - 0.3, y - 0.3), 0.6, 0.6,
                                      boxstyle="round,pad=0.1", edgecolor="#2C3E50",
                                      facecolor=color, linewidth=2)
        ax.add_patch(rect)
        ax.text(x, y, box, ha="center", va="center", fontsize=9, weight="bold", color="#34495E")

    for u, v in step["lines"]:
        x1, y1 = positions[u]
        x2, y2 = positions[v]
        mx, my = (x1 + x2) / 2, (y1 + y2) / 2
        ax.annotate("", xy=(x2, y2), xytext=(x1, y1),
                    arrowprops=dict(arrowstyle="->", lw=2, color="#566573"))

        # Label resistors
        if "label_lines" in step and ((u, v) in step["label_lines"] or (v, u) in step["label_lines"]):
            key = (u, v) if (u, v) in step["label_lines"] else (v, u)
            rname = step["label_lines"][key]
            if rname in resistor_values:
                rlabel = f"R = {resistor_values[rname]:.2f}Ω"
                ax.text(mx, my + 0.25, rlabel, ha="center", va="center",
                        fontsize=9, color="#7D3C98", weight='bold')

    ax.text(0, -0.4, step["formula"], fontsize=10, weight='bold', color='#1F618D')
    plt.tight_layout()
    plt.show()

# 🔁 Draw all steps
for step in steps:
    draw_nested_step(step)
```
---

```python
# ✅ Final Mixed Circuit Visualization with Edge Labels and Formulas
import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Ohm values
resistor_values = {
    "R1": 10,
    "R2": 20,
    "R3": 30,
    "R4": 40,
    "R5": 50,
    "R23": 1 / (1 / 20 + 1 / 30),           # ≈12
    "R45": 40 + 50,                         # 90
    "R123": 10 + (1 / (1 / 20 + 1 / 30)),   # ≈22
    "R12345": 10 + (1 / (1 / 20 + 1 / 30)) + 40 + 50  # ≈112
}

# Positions of nodes
positions = {
    "B+": (0, 2),
    "R1": (2, 0.5),
    "R2": (2, 3.5),
    "R3": (4, 3.5),
    "R4": (6, 2),
    "R5": (8, 2),
    "R23": (3, 3.5),
    "R45": (7, 2),
    "R123": (3, 2),
    "R12345": (4.5, 2),
    "B-": (10, 2)
}

# Simplification steps
steps = [
    {
        "title": "🔰 Step 0: Initial Circuit",
        "boxes": ["B+", "R1", "R2", "R3", "R4", "R5", "B-"],
        "lines": [("B+", "R2"), ("R2", "R3"), ("R3", "R4"),
                  ("B+", "R1"), ("R1", "R4"), ("R4", "R5"), ("R5", "B-")],
        "highlight": [],
        "label_lines": {
            ("B+", "R2"): "R2", ("R2", "R3"): "R3", ("R3", "R4"): "R4",
            ("B+", "R1"): "R1", ("R1", "R4"): "R4", ("R4", "R5"): "R5", ("R5", "B-"): "R5"
        },
        "formula": "R23 = (R2 || R3) = 12.00Ω"
    },
    {
        "title": "🔁 Step 1: Combine R2 || R3 → R23",
        "boxes": ["B+", "R1", "R23", "R4", "R5", "B-"],
        "lines": [("B+", "R23"), ("R23", "R4"),
                  ("B+", "R1"), ("R1", "R4"), ("R4", "R5"), ("R5", "B-")],
        "highlight": ["R23"],
        "label_lines": {
            ("B+", "R23"): "R23", ("R23", "R4"): "R23",
            ("B+", "R1"): "R1", ("R1", "R4"): "R4", ("R4", "R5"): "R5", ("R5", "B-"): "R5"
        },
        "formula": "R45 = R4 + R5 = 40Ω + 50Ω = 90.00Ω"
    },
    {
        "title": "🔁 Step 2: Combine R4 + R5 → R45",
        "boxes": ["B+", "R1", "R23", "R45", "B-"],
        "lines": [("B+", "R23"), ("R23", "R45"),
                  ("B+", "R1"), ("R1", "R45"), ("R45", "B-")],
        "highlight": ["R45"],
        "label_lines": {
            ("B+", "R23"): "R23", ("R23", "R45"): "R23",
            ("B+", "R1"): "R1", ("R1", "R45"): "R4", ("R45", "B-"): "R45"
        },
        "formula": "R123 = R1 + R23 = 10Ω + 12Ω = 22.00Ω"
    },
    {
        "title": "🔁 Step 3: Combine R1 + R23 → R123",
        "boxes": ["B+", "R123", "R45", "B-"],
        "lines": [("B+", "R123"), ("R123", "R45"), ("R45", "B-")],
        "highlight": ["R123"],
        "label_lines": {
            ("B+", "R123"): "R123", ("R123", "R45"): "R123", ("R45", "B-"): "R45"
        },
        "formula": "R12345 = R123 + R45 = 22Ω + 90Ω = 112.00Ω"
    },
    {
        "title": "✅ Step 4: Final Equivalent Resistance",
        "boxes": ["B+", "R12345", "B-"],
        "lines": [("B+", "R12345"), ("R12345", "B-")],
        "highlight": ["R12345"],
        "label_lines": {
            ("B+", "R12345"): "R12345", ("R12345", "B-"): "R12345"
        },
        "formula": "R_eq = 112.00Ω"
    }
]

highlight_colors = {
    "R23": "#FF6F61",
    "R45": "#76D7C4",
    "R123": "#85C1E9",
    "R12345": "#DDA0DD"
}

# Drawing function
def draw_step(step):
    fig, ax = plt.subplots(figsize=(11, 4.5))
    ax.set_xlim(-1, 11)
    ax.set_ylim(-1, 5)
    ax.axis("off")
    ax.set_title(step["title"], fontsize=13, pad=10, weight='bold', color="#2C3E50")

    # Draw boxes
    for box in step["boxes"]:
        x, y = positions[box]
        color = highlight_colors.get(box, "#D6DBDF") if box in step["highlight"] else "#F2F4F4"
        rect = patches.FancyBboxPatch((x - 0.3, y - 0.3), 0.6, 0.6,
                                      boxstyle="round,pad=0.1", edgecolor="#2C3E50",
                                      facecolor=color, linewidth=2)
        ax.add_patch(rect)
        ax.text(x, y, box, ha="center", va="center", fontsize=9, weight="bold", color="#34495E")

    # Draw connections
    for u, v in step["lines"]:
        x1, y1 = positions[u]
        x2, y2 = positions[v]
        mx, my = (x1 + x2) / 2, (y1 + y2) / 2
        ax.annotate("",
                    xy=(x2, y2), xytext=(x1, y1),
                    arrowprops=dict(arrowstyle="->", lw=2, color="#566573"))

        if "label_lines" in step:
            key = (u, v) if (u, v) in step["label_lines"] else (v, u)
            rname = step["label_lines"].get(key)
            if rname and rname in resistor_values:
                rlabel = f"R = {resistor_values[rname]:.2f}Ω"
                ax.text(mx, my + 0.25, rlabel, ha="center", va="center",
                        fontsize=9, color="#7D3C98", weight='bold')

    ax.text(0, -0.5, step["formula"], fontsize=10, weight='bold', color='#1F618D')
    plt.tight_layout()
    plt.show()

# 🖼️ Draw all simplification steps
for step in steps:
    draw_step(step)
```





