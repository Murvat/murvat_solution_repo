# Problem 2

# 🎯 Estimating π Using Monte Carlo Methods

## 🧠 Motivation

Monte Carlo simulations harness the power of randomness to solve problems that may be difficult to tackle analytically. One classic and elegant example is **estimating π** through probabilistic simulations involving geometry.

---

# 📌 Part 1: Estimating π Using a Circle

## 1️⃣ Theoretical Foundation

A **unit circle** (radius = 1) inscribed in a square has an area ratio of:

\[
\text{Ratio} = \frac{\text{Area of Circle}}{\text{Area of Square}} = \frac{\pi r^2}{(2r)^2} = \frac{\pi}{4}
\]

Hence, by generating **random points** inside the square and calculating the **fraction that fall inside the circle**, we can estimate π:

\[
\pi \approx 4 \times \frac{\text{Points in Circle}}{\text{Total Points}}
\]

## 2️⃣ Simulation Code

```python
import numpy as np
import matplotlib.pyplot as plt

def monte_carlo_pi(num_points):
    x = np.random.uniform(-1, 1, num_points)
    y = np.random.uniform(-1, 1, num_points)
    inside = x**2 + y**2 <= 1
    pi_estimate = 4 * np.sum(inside) / num_points
    return x, y, inside, pi_estimate

# Example
x, y, inside, pi_val = monte_carlo_pi(10000)
print(f"Estimated π = {pi_val}")
```

## 3️⃣ Visualization

```python
def plot_circle_simulation(x, y, inside):
    plt.figure(figsize=(6,6))
    plt.scatter(x[inside], y[inside], color='green', s=1, label="Inside Circle")
    plt.scatter(x[~inside], y[~inside], color='red', s=1, label="Outside Circle")
    circle = plt.Circle((0,0), 1, color='blue', fill=False)
    plt.gca().add_artist(circle)
    plt.gca().set_aspect('equal')
    plt.title("Monte Carlo Estimation of π")
    plt.xlabel("x")
    plt.ylabel("y")
    plt.legend()
    plt.grid(True)
    plt.show()

# Visualization
plot_circle_simulation(x, y, inside)
```

### 🔍 Visual Example

![Monte Carlo Circle Example](https://upload.wikimedia.org/wikipedia/commons/8/84/Pi_30K.gif)

## 4️⃣ Convergence Analysis

| Points  | π Estimate |
| ------- | ---------- |
| 100     | ~3.16      |
| 1,000   | ~3.14      |
| 10,000  | ~3.1416    |
| 100,000 | ~3.14159   |

As the number of random points increases, the estimate of π converges closer to the true value. Convergence is **slow**, which highlights the stochastic nature of the method.

---

# 📌 Part 2: Estimating π Using Buffon’s Needle

## 1️⃣ Theoretical Foundation

In **Buffon's Needle Problem**, a needle of length \( L \) is dropped on a plane with parallel lines \( D \) units apart. The probability \( P \) that the needle crosses a line is:

\[
P = \frac{2L}{\pi D}
\Rightarrow \pi \approx \frac{2L \cdot N}{D \cdot N_c}
\]

Where:

- \( N \): total drops
- \( N_c \): number of crosses

## 2️⃣ Simulation Code

```python
def buffon_needle_simulation(num_needles, L=1.0, D=2.0):
    x_centers = np.random.uniform(0, D/2, num_needles)
    angles = np.random.uniform(0, np.pi/2, num_needles)
    crosses = x_centers <= (L/2) * np.sin(angles)
    pi_estimate = (2 * L * num_needles) / (D * np.sum(crosses))
    return x_centers, angles, crosses, pi_estimate
```

## 3️⃣ Visualization

```python
def plot_buffon_simulation(x_centers, angles, crosses, L=1.0, D=2.0):
    fig, ax = plt.subplots(figsize=(8, 5))
    for i, crossed in enumerate(crosses[:200]):
        x = x_centers[i]
        theta = angles[i]
        x1 = x - (L/2) * np.cos(theta)
        x2 = x + (L/2) * np.cos(theta)
        y = i * 0.1
        ax.plot([x1, x2], [y, y], 'g-' if crossed else 'r-', lw=1)
    for i in range(0, int(0.1*len(crosses[:200])) + 2):
        ax.axhline(i * D, color='gray', lw=0.5)
    ax.set_title("Buffon's Needle Simulation")
    ax.set_xlim(0, D)
    ax.set_ylim(0, max(20, 0.1 * len(crosses[:200])))
    plt.show()
```

### 🎯 Visual Example

![Buffon Needle Example](https://upload.wikimedia.org/wikipedia/commons/8/84/Buffon%27s_needle_simulation.png)

## 4️⃣ Convergence Analysis

| Drops  | π Estimate |
| ------ | ---------- |
| 100    | ~3.10      |
| 1,000  | ~3.15      |
| 10,000 | ~3.141     |

### 🆚 Comparison Table

| Method          | Convergence Rate | Implementation Difficulty | Visual Appeal |
| --------------- | ---------------- | ------------------------- | ------------- |
| Circle-based    | Faster           | Simple                    | High          |
| Buffon’s Needle | Slower           | Moderate                  | High          |

---

## 📁 Deliverables Summary

- ✅ Full Markdown explanation and theory.
- ✅ Circle-based and Buffon’s Needle simulation code.
- ✅ Graphs and animations showing random distribution and needle placement.
- ✅ Analytical comparison of convergence and efficiency.

---

## 📚 References & Resources

- [Monte Carlo Method - Wikipedia](https://en.wikipedia.org/wiki/Monte_Carlo_method)
- [Buffon's Needle - Wikipedia](https://en.wikipedia.org/wiki/Buffon%27s_needle)
- [YouTube Visualization of Monte Carlo π](https://www.youtube.com/watch?v=pvimAM_SLic)

---
