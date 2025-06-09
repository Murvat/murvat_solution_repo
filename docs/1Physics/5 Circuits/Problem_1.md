# 🔌 Problem 1: Equivalent Resistance Using Graph Theory

---

## 🎯 Motivation

Computing the **equivalent resistance** of an electrical circuit is a fundamental problem in electronics. While basic circuits with few resistors can be simplified using series and parallel rules, **large or complex networks** quickly become intractable without a systematic approach. This is where **graph theory** comes in.

By modeling a circuit as a **graph**, we can automate and simplify the process of finding equivalent resistance between any two points.

- **🔹 Nodes (Vertices)** represent junctions or connection points.
- **🔸 Edges** represent resistors with weights corresponding to resistance values (in ohms, Ω).

This graph-based model is used in:

- Circuit analysis software (e.g., SPICE)
- Electrical design automation (EDA)
- Network analysis and optimization
- Physics simulations

---

## ⚙️ Conceptual Overview

### 🔁 Two Key Simplifications

![Resistor network](https://www.researchgate.net/publication/225263504/figure/fig5/AS:668205852925960@1536324098926/Graph-representation-of-a-realistic-resistor-network-The-squares-are-external-nodes-and.png)

#### 1. **Series Reduction**

Two resistors connected **end-to-end** between three nodes (A-B-C), where the middle node has only two connections (degree 2), can be replaced with a single resistor.

**Formula**: $R_{eq} = R_1 + R_2$

**Illustration:**

```
 A —[5Ω]— B —[3Ω]— C     ➞     A —[8Ω]— C
```

#### 2. **Parallel Reduction**

Resistors connecting the **same two nodes** (e.g., A and B) can be replaced with a single resistor using the parallel formula:

**Formula**: $\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2} + \cdots + \frac{1}{R_n}$

**Illustration:**

```
 A —[6Ω]— B
 A —[3Ω]— B       ➞      A —[2Ω]— B
```

---

## 🔍 Problem Example

### 🎯 Goal: Find the equivalent resistance between nodes A and D

**Initial Circuit Diagram:**

```
    A
    |
   [2Ω]
    |
    B
   / \
[4Ω] [6Ω]
 /       \
C ——[3Ω]—— D
```

**Graph View:**

- Nodes: A, B, C, D
- Edges:

  - A—B: 2Ω
  - B—C: 4Ω
  - B—D: 6Ω
  - C—D: 3Ω

### 🔧 Step-by-Step Simplification

1. **B—C—D** forms a triangle with B—D
2. First reduce C—D: no simplification yet
3. Use Delta-to-Wye transformation if necessary
4. Apply parallel reduction between paths to D
5. Then, compute the total resistance from A to D

> Note: For complex networks, advanced transformations like Delta-Wye (Δ-Y) may be needed.

---

## 🧠 Algorithm: Graph-Based Simplification

We can automate the reduction using a loop that simplifies until no further changes are possible.

### 🧾 Pseudocode

```plaintext
function simplify_graph(G):
    repeat
        for each node in G:
            if node has degree 2:
                check for series configuration:
                    replace with single resistor (R1 + R2)

        for each pair of nodes (u, v):
            if multiple resistors exist:
                replace with equivalent parallel resistor

    until no more simplifications

    return resistance between source and target
```

---

## 📊 Illustration: Example Before and After

**Before Simplification:**

```
Graph: (weighted undirected)

A —(2Ω)— B
B —(4Ω)— C
B —(6Ω)— D
C —(3Ω)— D
```

**After Simplification:**

```
Equivalent graph (conceptual):
A —[R_eq]— D
```

---

## 🧰 Use Cases and Extensions

- 🔌 Electrical Engineering Design Tools
- 🖥️ Circuit Simulation and Visualization Software
- 📐 Symbolic Circuit Analysis (algebraic manipulation)
- 🧮 Support for AC circuits and impedance (Z = R + jX)
- 🔁 Integration with Kirchhoff's laws and mesh analysis
- ⚡ Advanced: Delta-Wye Transformations and matrix-based reductions

---

## 🧩 Advanced Concepts

- **Kirchhoff's Laws**: Model using linear algebra
- **Laplacian Matrix**: Resistance as function of inverse Laplacian
- **Delta-Wye Transformations**: For reducing triangular subgraphs

> Interested in implementation? Ask for Python/NumPy code or an interactive visualization!

---

## 📌 Summary

Graph theory offers a structured, repeatable, and automatable method to calculate equivalent resistance in electrical networks. It scales better than manual series-parallel techniques and provides the foundation for modern circuit analysis software.

Use it to:

- Simplify large resistor networks
- Automate design verification
- Teach concepts interactively

Let me know if you'd like this as a visual Markdown file with embedded diagrams or code samples!
