# Problem 1

# 🧪 Measuring Earth's Gravitational Acceleration with a Pendulum

## 🎯 Motivation

The acceleration due to gravity \\( g \\) is a fundamental constant crucial in physics and engineering. This experiment explores a classic and accessible method for determining \\( g \\) using a simple pendulum and emphasizes experimental accuracy and uncertainty analysis.

---

## 🔧 Materials

- String (1–1.5 meters)
- Small weight (e.g., keychain, coin bag)
- Stopwatch or smartphone timer
- Ruler or measuring tape (resolution: 0.01 m recommended)

---

## ⚙️ Setup

1. Suspend the weight from the string attached to a stable point.
2. Measure the pendulum length \\( L \\) from the suspension point to the center of mass of the weight.
3. Record the measurement tool resolution (e.g., 0.01 m → uncertainty \\( u_L = 0.005 \\) m).

---

## 📊 Data Collection

- Displace the pendulum by less than 15°.
- Measure the time for 10 full oscillations, 10 times.
- Record the data:

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

### 🔍 Calculated Averages

- Mean time \\( \\overline{t}\_{10} = 20.312 \\) s
- Period \\( T = \\frac{\\overline{t}\_{10}}{10} = 2.0312 \\) s
- Standard deviation \\( \\sigma = 0.020 \\) s
- Uncertainty in mean time \\( u_T = \\frac{\\sigma}{\\sqrt{10} \\cdot 10} = 0.00063 \\) s

---

## 🧮 Calculations

### 1️⃣ Compute \\( g \\) from:

\\[
g = \\frac{4\\pi^2 L}{T^2}
\\]

Given:

- \\( L = 1.000 \\pm 0.005 \\) m
- \\( T = 2.0312 \\pm 0.00063 \\) s

\\[
g = \\frac{4\\pi^2 \\cdot 1.000}{(2.0312)^2} \\approx 9.55 \\ \\text{m/s}^2
\\]

### 2️⃣ Uncertainty Propagation

\\[
\\frac{u_g}{g} = \\sqrt{\\left(\\frac{u_L}{L}\\right)^2 + \\left(2\\frac{u_T}{T}\\right)^2}
\\]

\\[
\\frac{u_g}{g} = \\sqrt{\\left(\\frac{0.005}{1.000}\\right)^2 + \\left(2\\cdot\\frac{0.00063}{2.0312}\\right)^2} \\approx 0.00515
\\]

\\[
u_g = 9.55 \\cdot 0.00515 \\approx 0.049 \\ \\text{m/s}^2
\\]

### ✅ Final Result

\\[
g = 9.55 \\pm 0.05 \\ \\text{m/s}^2
\\]

---

## 📌 Analysis

### 🔍 Comparison to Standard Value

- Accepted value of \\( g \\approx 9.81 \\ \\text{m/s}^2 \\)
- Relative error: \\( \\frac{|9.55 - 9.81|}{9.81} \\approx 2.65\\% \\)

### ⚠️ Sources of Uncertainty

- **Length Measurement:** Accuracy limited by visual alignment and ruler resolution.
- **Timing Variability:** Human reaction time affects stopwatch results.
- **Air Resistance and Friction:** Minor but can accumulate over time.
- **Amplitude Assumption:** Small angle approximation may introduce error at larger displacements.

---

## 📁 Deliverables Summary

- 📋 Tabulated time measurements.
- 🔢 Calculations for mean, standard deviation, and period.
- 🧠 Final gravity estimate with uncertainty.
- 🗣 Discussion of experimental limitations and uncertainty propagation.

---

## 📚 References

- [Simple Pendulum - Wikipedia](<https://en.wikipedia.org/wiki/Pendulum_(mathematics)>)
- [Uncertainty Propagation - Wikipedia](https://en.wikipedia.org/wiki/Propagation_of_uncertainty)
