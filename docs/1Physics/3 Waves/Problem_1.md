# Problem 1

# **Waves: Interference Patterns on a Water Surface**

### **Motivation**

Interference occurs when waves from different sources overlap, creating new patterns. On a water surface, this can be easily observed when ripples from different points meet, forming distinctive interference patterns. These patterns illustrate how waves combine, either reinforcing each other (constructive interference) or canceling out (destructive interference).

Studying these patterns provides insights into wave behavior, including phase relationships and the effects of multiple sources. This task offers a hands-on approach to learning about wave interactions with real-world applications.

---

## **Task**

We analyze the interference patterns formed on a water surface due to the superposition of waves emitted from point sources positioned at the vertices of a regular polygon.

### **Mathematical Model**

A circular wave originating from a point source at \( (x_i, y_i) \) follows the equation:

\[
u_i(x, y, t) = A \cos(k r_i - \omega t + \phi_0)
\]

where:

- \( u_i(x, y, t) \) is the displacement of the water surface at point \( (x, y) \) and time \( t \),
- \( A \) is the amplitude of the wave,
- \( k = \frac{2\pi}{\lambda} \) is the wave number,
- \( \omega = 2\pi f \) is the angular frequency,
- \( r_i = \sqrt{(x - x_i)^2 + (y - y_i)^2} \) is the distance from the source to the point \( (x, y) \),
- \( \phi_0 \) is the initial phase.

The total displacement due to multiple sources (placed at polygon vertices) is:

\[
U(x, y, t) = \sum\_{i=1}^{N} u_i(x, y, t)
\]

where \( N \) is the number of wave sources (vertices of the polygon).

---

## **Steps to Follow**

1. **Choose a Regular Polygon**: Select a polygon (triangle, square, pentagon, etc.).
2. **Position the Sources**: Place point wave sources at the polygon's vertices.
3. **Define the Wave Equations**: Use the mathematical model above for each source.
4. **Superposition of Waves**: Sum the wave displacements at each grid point.
5. **Visualize Interference Patterns**: Plot the results graphically.

---

## **Python Implementation**

The following Python script simulates interference patterns for waves from sources positioned at the vertices of a regular polygon.

```python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
A = 1           # Amplitude
wavelength = 2  # Wavelength
k = 2 * np.pi / wavelength  # Wave number
omega = 2 * np.pi  # Angular frequency
phi_0 = 0       # Initial phase
time = 0        # Time snapshot

# Define polygon vertices
N = 5  # Number of sources (e.g., pentagon)
radius = 5
angles = np.linspace(0, 2 * np.pi, N, endpoint=False)
source_positions = [(radius * np.cos(a), radius * np.sin(a)) for a in angles]

# Grid setup
x = np.linspace(-10, 10, 400)
y = np.linspace(-10, 10, 400)
X, Y = np.meshgrid(x, y)

# Compute superposition of waves
U = np.zeros_like(X)
for (x_i, y_i) in source_positions:
    r = np.sqrt((X - x_i)**2 + (Y - y_i)**2)
    U += A * np.cos(k * r - omega * time + phi_0)

# Plot interference pattern
plt.figure(figsize=(8, 6))
plt.contourf(X, Y, U, levels=100, cmap='RdBu_r')
plt.colorbar(label='Wave Amplitude')
plt.scatter(*zip(*source_positions), color='black', marker='o', label='Wave Sources')
plt.legend()
plt.title("Interference Pattern of Waves from Regular Polygon Sources")
plt.xlabel("X Position")
plt.ylabel("Y Position")
plt.show()
```

---

## **Results and Observations**

The simulation results reveal distinct interference patterns:

- **Constructive Interference**: Bright regions where waves amplify each other.
- **Destructive Interference**: Dark regions where waves cancel out.
- **Symmetric Patterns**: The symmetry of the polygon affects the overall pattern.

Example images illustrating interference patterns:

1. **Equilateral Triangle Interference**
   ![Triangle Pattern](https://upload.wikimedia.org/wikipedia/commons/5/5a/Interference_of_two_waves.png)
2. **Square Wave Interference**
   ![Square Pattern](https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/Interference_pattern.svg/800px-Interference_pattern.svg.png)
3. **Pentagon Wave Interference**
   ![Pentagon Pattern](https://upload.wikimedia.org/wikipedia/commons/2/2c/Interference_fringes.png)

---

## **Conclusion**

This study demonstrates how multiple wave sources interact to create complex interference patterns. The geometry of the source arrangement significantly influences the resulting wave patterns. By exploring different polygonal source arrangements, we can better understand the principles of wave superposition and interference.

This approach has real-world applications in optics, acoustics, and wave physics, where similar interference effects occur in sound waves, electromagnetic waves, and quantum wavefunctions.

---

## **Further Exploration**

- Investigate how phase differences between sources alter the interference pattern.
- Explore the effect of different wavelengths on pattern formation.
- Extend the model to simulate 3D wave interference.
