# Problem 3

# Trajectories of a Freely Released Payload Near Earth

## Motivation

When an object is released from a moving rocket near Earth, its trajectory depends on initial conditions and gravitational forces. This scenario presents a rich problem, blending principles of orbital mechanics and numerical methods. Understanding the potential trajectories is vital for space missions, such as deploying payloads or returning objects to Earth.

---

## Task

### 1. Types of Possible Trajectories

- **Elliptical Orbit**: If the payload's velocity is below escape velocity but above circular orbit velocity, it enters an elliptical orbit.
- **Parabolic Trajectory**: If the velocity equals the escape velocity, the payload follows a parabolic trajectory and escapes Earth’s gravity.
- **Hyperbolic Trajectory**: If the velocity exceeds escape velocity, the payload moves away on a hyperbolic path.
- **Suborbital Trajectory**: If the payload's velocity is too low, it falls back to Earth.

### 2. Mathematical Formulation

- **Newton’s Law of Gravitation**:

  \[ F = \frac{GMm}{r^2} \]

- **Equation of Motion**:

  \[ m \frac{d^2 r}{dt^2} = - \frac{GMm}{r^2} \]

- **Orbital Energy Equation**:

  \[ E = \frac{1}{2} m v^2 - \frac{GMm}{r} \]

  where \(E\) determines the type of trajectory:

  - If \( E < 0 \), the orbit is **elliptical**.
  - If \( E = 0 \), the trajectory is **parabolic**.
  - If \( E > 0 \), the trajectory is **hyperbolic**.

### 3. Numerical Simulation

- Compute the trajectory using numerical integration (Runge-Kutta method).
- Simulate different initial conditions (altitude, velocity, direction).
- Visualize the resulting paths.

---

## Python Implementation

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Constants
G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)
M_earth = 5.972e24  # Mass of Earth (kg)
R_earth = 6.371e6  # Radius of Earth (m)

# Equations of motion
def equations(t, y):
    x, vx, y, vy = y
    r = np.sqrt(x**2 + y**2)
    ax = -G * M_earth * x / r**3
    ay = -G * M_earth * y / r**3
    return [vx, ax, vy, ay]

# Initial conditions (position in meters, velocity in m/s)
altitude = 400e3  # 400 km above Earth
initial_speed = 7800  # Close to low Earth orbit velocity
initial_angle = np.radians(45)  # 45-degree release angle
x0, y0 = R_earth + altitude, 0
vx0, vy0 = initial_speed * np.cos(initial_angle), initial_speed * np.sin(initial_angle)

# Time span
t_span = (0, 10000)
t_eval = np.linspace(*t_span, 1000)

# Solve equations
sol = solve_ivp(equations, t_span, [x0, vx0, y0, vy0], t_eval=t_eval)

# Plot trajectory
plt.figure(figsize=(8, 8))
plt.plot(sol.y[0], sol.y[2], label='Payload Trajectory')
plt.plot(0, 0, 'ro', label='Earth')
plt.xlabel('x position (m)')
plt.ylabel('y position (m)')
plt.legend()
plt.title('Simulated Trajectory of a Released Payload')
plt.grid()
plt.show()
```

---

## Results and Observations

- By adjusting the initial velocity and angle, different trajectories are obtained.
- If the velocity is **too low**, the payload falls back to Earth.
- At the **orbital velocity**, the payload stays in orbit.
- If the velocity **exceeds escape velocity**, the payload moves on a hyperbolic path.

---

## Applications in Space Missions

- **Satellite Deployment**: Adjusting release velocity ensures successful orbit insertion.
- **Reentry Vehicles**: Understanding suborbital trajectories helps in designing safe reentry paths.
- **Deep Space Missions**: Proper velocity adjustments enable interplanetary travel.

---

## Conclusion

Simulating payload trajectories helps in mission planning and space exploration. By using numerical methods, we can predict the motion of objects near Earth and analyze how initial conditions affect their fate. This knowledge is essential for designing efficient satellite launches and interplanetary missions.
