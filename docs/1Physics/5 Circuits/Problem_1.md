# Problem 1

# 🔌 Equivalent Resistance Using Graph Theory

## 🎯 Motivation

Traditional methods for calculating equivalent resistance—applying series and parallel rules—become impractical for large or complex circuits. **Graph theory** provides a powerful and flexible alternative. In this method:

- **Nodes** represent junctions in the circuit.
- **Edges** represent resistors with weights corresponding to resistance values.

By applying graph simplification techniques, we can reduce even complex resistor networks into a single equivalent resistance. This method is particularly useful for:

- Circuit analysis software
- Complex network design
- Automating circuit reduction

---

## 🧠 Option 1: Algorithm Description

### 🔁 Core Idea

We use graph reduction techniques:

1. **Series Reduction:** If two resistors are connected end-to-end with a common node and no other branches, combine them into one.
2. **Parallel Reduction:** If two or more resistors connect the same two nodes, combine them using parallel rules.

---

### 📋 Pseudocode

```plaintext
function simplify_graph(G):
    while changes can be made:
        for each node in G:
            if node has degree 2:
                check if connected resistors are in series:
                    combine and replace with equivalent resistor
            for each pair of nodes (u, v):
                if multiple edges (resistors) exist between u and v:
                    replace with one equivalent resistor in parallel

    return total resistance between source and target nodes

```
