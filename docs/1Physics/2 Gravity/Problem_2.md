# Problem 2

# Escape Velocities and Cosmic Velocities

## Motivation

The concept of escape velocity is crucial for understanding the conditions required to leave a celestial body's gravitational influence. Extending this concept, the first, second, and third cosmic velocities define the thresholds for orbiting, escaping, and leaving a star system. These principles underpin modern space exploration, from launching satellites to interplanetary missions.

---

## Task

### 1. Definition of Cosmic Velocities

- **First Cosmic Velocity (Orbital Velocity)**: The minimum velocity required to maintain a stable circular orbit around a celestial body.

  \[ v_1 = \sqrt{\frac{GM}{r}} \]

- **Second Cosmic Velocity (Escape Velocity)**: The minimum velocity needed to escape a celestial body's gravitational field without further propulsion.

  \[ v_2 = \sqrt{\frac{2GM}{r}} = \sqrt{2} v_1 \]

- **Third Cosmic Velocity (Interstellar Escape Velocity)**: The velocity required to escape the gravitational pull of a star system.

  \[ v*3 = \sqrt{\frac{2G M*{sun}}{r\_{orbit}}} \] (For a planet escaping the Solar System)

### 2. Mathematical Analysis and Influencing Parameters

- The gravitational constant \( G = 6.67430 \times 10^{-11} \) \(m^3 kg^{-1} s^{-2}\).
- The mass \( M \) of the celestial body significantly affects escape velocity.
- The radius \( r \) of the celestial body determines the strength of gravity at its surface.

### 3. Real-World Applications

- **Launching Satellites**: Achieving the first cosmic velocity allows satellites to remain in orbit.
- **Interplanetary Travel**: Rockets must surpass the second cosmic velocity to travel to other planets.
- **Interstellar Missions**: Missions like Voyager 1 have exceeded the third cosmic velocity to escape the Solar System.

---

## Python Implementation

```python
import numpy as np
import matplotlib.pyplot as plt

def cosmic_velocities(M, R):
    G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)
    v1 = np.sqrt(G * M / R)  # First cosmic velocity
    v2 = np.sqrt(2) * v1  # Second cosmic velocity
    return v1, v2

# Celestial bodies (mass in kg, radius in meters)
bodies = {
    "Earth": (5.972e24, 6.371e6),
    "Mars": (6.417e23, 3.3895e6),
    "Jupiter": (1.898e27, 6.9911e7)
}

velocities = {body: cosmic_velocities(*bodies[body]) for body in bodies}

# Plotting
labels = list(velocities.keys())
v1_values = [velocities[b][0] for b in labels]
v2_values = [velocities[b][1] for b in labels]
x = np.arange(len(labels))

plt.figure(figsize=(8, 6))
plt.bar(x - 0.2, v1_values, 0.4, label='First Cosmic Velocity')
plt.bar(x + 0.2, v2_values, 0.4, label='Second Cosmic Velocity')
plt.xticks(x, labels)
plt.xlabel('Celestial Body')
plt.ylabel('Velocity (m/s)')
plt.title('Cosmic Velocities for Different Celestial Bodies')
plt.legend()
plt.grid()
plt.show()
```

---

## Results and Observations

- **Earth**: First cosmic velocity ≈ 7.91 km/s, escape velocity ≈ 11.2 km/s.
- **Mars**: First cosmic velocity ≈ 3.55 km/s, escape velocity ≈ 5.03 km/s.
- **Jupiter**: First cosmic velocity
