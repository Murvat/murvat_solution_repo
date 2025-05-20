# Problem 1

# 🧪 Measuring Earth's Gravitational Acceleration with a Pendulum

## 🎯 Motivation

The acceleration due to gravity $g$ is a foundational physical constant central to fields such as mechanics, civil engineering, aerospace design, and physics education. One of the most accessible and elegant ways to estimate $g$ is using the simple pendulum — a system studied since the era of Galileo.

This experiment demonstrates how basic tools and data analysis can be used to produce an accurate estimate of $g$, while introducing essential scientific skills: measurement precision, data handling, and uncertainty quantification.

![Pendulum Experiment](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/Pendulum_animation.gif/480px-Pendulum_animation.gif)

---

## 🔧 Materials Required

| Item                    | Purpose                                |
| ----------------------- | -------------------------------------- |
| String (1–1.5 meters)   | Acts as the pendulum arm               |
| Small mass/weight       | Creates the pendulum bob               |
| Stopwatch/smartphone    | Measures time intervals                |
| Ruler or measuring tape | Measures the length $L$                |
| Clamp/stand (optional)  | Provides stable support for suspension |

> 🔍 Note: Ensure that the environment is free of strong air currents and the mass swings freely without obstruction.

---

## ⚙️ Experimental Setup

1. **Assembly**: Tie one end of the string to a fixed support and attach the mass to the other end.
2. **Length Measurement**: Measure the length $L$ from the suspension point to the mass center. Use a ruler with millimeter resolution if possible.
3. **Displacement**: Gently pull the pendulum back by **less than 15°** from the vertical to maintain the small-angle approximation.
4. **Measurement Uncertainty**: If using a ruler with 1 cm divisions, uncertainty in $L$ is $u_L = 0.005$ m.

![Simple Pendulum Setup](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Pendulum.svg/800px-Pendulum.svg.png)

---

## 📊 Data Collection

Conduct **10 trials**, each measuring the time for **10 full oscillations**. Record your observations in a table:

| Trial | Time for 10 Oscillations (s) |
| ----- | ---------------------------- |
| 1     | 20.31                        |
| 2     | 20.29                        |
| 3     | 20.33                        |
| 4     | 20.28                        |
| 5     | 20.32                        |
| 6     | 20.35                        |
| 7     | 20.30                        |
| 8     | 20.34                        |
| 9     | 20.29                        |
| 10    | 20.31                        |

---

## 🔎 Calculated Averages and Uncertainties

### 🧮 Period Calculation

- Mean time for 10 oscillations: $\overline{t}_{10} = 20.312$ s
- Period $T = \frac{\overline{t}_{10}}{10} = 2.0312$ s
- Standard deviation: $\sigma = 0.020$ s
- Uncertainty in mean: $u_T = \frac{\sigma}{\sqrt{10} \cdot 10} = 0.00063$ s

---

## 🧠 Theoretical Basis and Calculations

### 1️⃣ Formula for Gravity

$$
  g = \frac{4\pi^2 L}{T^2}
$$

Given:

- $L = 1.000 \pm 0.005$ m
- $T = 2.0312 \pm 0.00063$ s

Substitute:

$$
  g = \frac{4\pi^2 \cdot 1.000}{(2.0312)^2} \approx 9.55 \ \text{m/s}^2
$$

### 2️⃣ Propagating Uncertainty

$$
\frac{u_g}{g} = \sqrt{\left(\frac{u_L}{L}\right)^2 + \left(2\cdot\frac{u_T}{T}\right)^2}
$$

$$
\frac{u_g}{g} = \sqrt{\left(\frac{0.005}{1.000}\right)^2 + \left(2\cdot\frac{0.00063}{2.0312}\right)^2} \approx 0.00515
$$

$$
  u_g = 9.55 \cdot 0.00515 \approx 0.049 \ \text{m/s}^2
$$

### ✅ Final Result

$$
  \boxed{g = 9.55 \pm 0.05 \ \text{m/s}^2}
$$

---

## 📌 Results Interpretation

### 📉 Comparison to Standard Value

- Standard gravitational acceleration: $g = 9.81 \ \text{m/s}^2$
- Absolute error: $|9.55 - 9.81| = 0.26 \ \text{m/s}^2$
- Relative error: $\frac{0.26}{9.81} \approx 2.65\%$

### ⚠️ Sources of Uncertainty

| Source               | Impact                                               |
| -------------------- | ---------------------------------------------------- |
| Length measurement   | Inexact center-of-mass estimation and parallax error |
| Timing error         | Manual stopwatch handling introduces latency         |
| Air resistance       | Can slightly dampen the motion and alter period      |
| Amplitude assumption | Over 15° leads to nonlinear behavior                 |

> 🧠 Improving reliability: Use light gates or motion sensors for precise time tracking.

---

## 📈 Visualization Examples

### 📍 Time vs. Trial Plot

```python
import matplotlib.pyplot as plt

trials = list(range(1, 11))
times = [20.31, 20.29, 20.33, 20.28, 20.32, 20.35, 20.30, 20.34, 20.29, 20.31]

plt.figure(figsize=(8, 4))
plt.plot(trials, times, marker='o', linestyle='-', color='navy')
plt.axhline(sum(times)/len(times), color='red', linestyle='--', label='Mean Time')
plt.title("Pendulum Oscillation Time per Trial")
plt.xlabel("Trial")
plt.ylabel("Time for 10 Oscillations (s)")
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

---

## 🧰 Optional Extensions

- Try different lengths $L$ and observe how $T$ changes.
- Plot $T^2$ vs $L$; the slope will be $\frac{4\pi^2}{g}$.
- Fit a linear regression to determine $g$ experimentally.

![T Squared vs L](https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Simple_pendulum_period_length_graph.svg/640px-Simple_pendulum_period_length_graph.svg.png)

---

## 📁 Deliverables Summary

✅ Table of oscillation times
✅ Calculated mean, standard deviation, and period
✅ Final gravity value with uncertainty
✅ Discussion of errors and result interpretation
✅ Python plots and optional data visualization
✅ Recommendations for improving measurement reliability

---

## 📚 References & Resources

- [Simple Pendulum - Wikipedia](https://en.wikipedia.org/wiki/Pendulum_%28mathematics%29)
- [Uncertainty Propagation - Wikipedia](https://en.wikipedia.org/wiki/Propagation_of_uncertainty)
- [Pendulum Calculator](https://www.omnicalculator.com/physics/pendulum)
- [YouTube - How to Measure g with a Pendulum](https://www.youtube.com/watch?v=6AGD0_-B3MI)
