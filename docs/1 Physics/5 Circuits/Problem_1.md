# ⚡ Equivalent Resistance Using Graph Theory

## 🧠 Problem Overview

We aim to compute the **equivalent resistance** between two points in a resistor network using **graph theory**. A resistor network can be modeled as an **undirected, weighted graph**, where:

- **Nodes** represent junctions,
- **Edges** represent resistors,
- **Weights** on edges are the resistance values.

---

## 🛠️ Approach

We solve this problem using two main techniques:

### 🔗 1. Graph Simplification

We iteratively reduce the graph using:

- **Series reduction**: Combine resistors in a line.
- **Parallel reduction**: Combine resistors across the same two nodes.

### 🧬 2. Laplacian Matrix Method

When simplification is not enough (e.g. loops or complex topology), we use the Laplacian matrix of the graph and compute resistance via:

$$
R_{eq}(a, b) = (e_a - e_b)^T L^+ (e_a - e_b)
$$

Where:

- **L** is the Laplacian matrix,  
- **L⁺** is its pseudoinverse,  
- **eₐ** and **e_b** are indicator vectors for nodes **a** and **b**.


---

## 🧮 Combined Python Implementation

```python
import networkx as nx
import numpy as np
from numpy.linalg import pinv
from typing import Set

def combine_parallel_edges(G: nx.Graph) -> nx.Graph:
    """
    Combine parallel edges by calculating their equivalent resistance.
    """
    combined = nx.Graph()
    for u, v, data in G.edges(data=True):
        r = data['resistance']
        if combined.has_edge(u, v):
            # Calculate equivalent resistance for parallel resistances
            r_existing = combined[u][v]['resistance']
            r_parallel = 1 / (1 / r_existing + 1 / r)
            combined[u][v]['resistance'] = r_parallel
        else:
            combined.add_edge(u, v, resistance=r)
    return combined

def reduce_series_nodes(G: nx.Graph, terminals: Set) -> nx.Graph:
    """
    Reduce series-connected nodes by calculating their equivalent resistance.
    Nodes in the 'terminals' set are preserved.
    """
    reduced = G.copy()
    while True:
        changed = False
        for node in list(reduced.nodes()):
            # Skip terminal nodes or nodes not part of a series
            if reduced.degree(node) != 2 or node in terminals:
                continue

            # Get the neighbors and resistances
            neighbors = list(reduced.neighbors(node))
            u, v = neighbors
            r1 = reduced[node][u]['resistance']
            r2 = reduced[node][v]['resistance']
            
            # Calculate equivalent resistance for series
            r_eq = r1 + r2
            
            # Remove the intermediate node
            reduced.remove_node(node)
            
            # Add or update the edge between neighbors
            if reduced.has_edge(u, v):
                r_existing = reduced[u][v]['resistance']
                r_parallel = 1 / (1 / r_existing + 1 / r_eq)
                reduced[u][v]['resistance'] = r_parallel
            else:
                reduced.add_edge(u, v, resistance=r_eq)
            
            changed = True
            break  # Restart loop after modifying the graph
        if not changed:
            break
    return reduced

def calculate_equivalent_resistance(G: nx.Graph, start: str, end: str) -> float:
    """
    Calculate the equivalent resistance between two nodes (start and end).
    """
    simplified = combine_parallel_edges(G)
    simplified = reduce_series_nodes(simplified, terminals={start, end})
    
    if simplified.has_edge(start, end):
        return simplified[start][end]['resistance']
    else:
        raise ValueError("No direct connection remains. Use Laplacian method for disconnected graphs.")

def resistance_distance(G: nx.Graph, node_a: str, node_b: str) -> float:
    """
    Compute the resistance distance between two nodes using the pseudoinverse of the Laplacian matrix.
    """
    # Create Laplacian matrix with conductance as weights
    L = nx.laplacian_matrix(G, weight='conductance').toarray()
    L_pinv = pinv(L)  # Compute the pseudoinverse of the Laplacian
    
    # Map nodes to indices
    node_index = {node: i for i, node in enumerate(G.nodes())}
    i, j = node_index[node_a], node_index[node_b]
    
    # Calculate resistance distance
    return L_pinv[i, i] + L_pinv[j, j] - 2 * L_pinv[i, j]

def build_graph_with_conductance() -> nx.Graph:
    """
    Build a sample graph with resistances and calculate conductance for each edge.
    """
    G = nx.Graph()
    G.add_edge('A', 'B', resistance=2)
    G.add_edge('B', 'C', resistance=3)
    G.add_edge('C', 'D', resistance=4)
    G.add_edge('A', 'D', resistance=1)
    
    # Add conductance (inverse of resistance) as edge attributes
    for u, v, data in G.edges(data=True):
        r = data['resistance']
        data['conductance'] = 1 / r
    return G

# Main function for testing
if __name__ == "__main__":
    # Build the graph
    graph = build_graph_with_conductance()
    
    # Test equivalent resistance
    try:
        eq_res = calculate_equivalent_resistance(graph, 'A', 'D')
        print(f"Equivalent Resistance between A and D: {eq_res:.2f} ohms")
    except ValueError as e:
        print(str(e))
    
    # Test resistance distance
    res_dist = resistance_distance(graph, 'A', 'C')
    print(f"Resistance Distance between A and C: {res_dist:.2f}")
```

---

## 🧪 Example Usage

```python
# Graph with multiple edges for simplification
G = nx.MultiGraph()
G.add_edge('A', 'B', resistance=2)
G.add_edge('B', 'C', resistance=3)
G.add_edge('C', 'D', resistance=4)
G.add_edge('A', 'D', resistance=1)

try:
    r_eq = calculate_equivalent_resistance(G, 'A', 'D')
    print(f"Simplified Resistance A–D: {r_eq:.4f} Ω")
except:
    print("Simplification failed, using Laplacian.")

G_conductance = build_graph_with_conductance()
r_eq_lap = resistance_distance(G_conductance, 'A', 'D')
print(f"Laplacian Resistance A–D: {r_eq_lap:.4f} Ω")
```

---
## Visuals
![alt text](image-3.png)
---
![alt text](image-4.png)
---
## ⚙️ Efficiency Analysis

| Method         | Complexity | Best Use Case                        |
| -------------- | ---------- | ------------------------------------ |
| Simplification | $O(E)$   | Tree-like or easily reducible graphs |
| Laplacian      | $O(N^3)$ | Arbitrary/complex graphs with loops  |

- Use simplification first for performance.
- Use Laplacian only if no more reduction is possible.

---

## ✅ Final Notes

- This combined method provides a robust and scalable solution.
- Suitable for use in circuit design software, simulations, and network analysis.
- You can visualize these networks using `networkx.draw()` for better intuition.

