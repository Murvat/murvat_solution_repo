# Problem 1

# Orbital Period and Orbital Radius

## Motivation

The relationship between the square of the orbital period and the cube of the orbital radius, known as Kepler's Third Law, is a cornerstone of celestial mechanics. This simple yet profound relationship allows for the determination of planetary motions and has implications for understanding gravitational interactions on both local and cosmic scales. By analyzing this relationship, one can connect fundamental principles of gravity with real-world phenomena such as satellite orbits and planetary systems.

---

## Task

### 1. Theoretical Foundation

- Start with Newton's Law of Gravitation and centripetal force:

  \[ F = \frac{G M m}{r^2} \]

  \[ F = m \frac{v^2}{r} \]

- Equating the two forces for circular orbits and expressing velocity in terms of the orbital period \(T\):

  \[ v = \frac{2 \pi r}{T} \]

  \[ \frac{G M m}{r^2} = m \frac{(2 \pi r / T)^2}{r} \]

  - Simplifying gives Kepler’s Third Law:

  \[ T^2 = \frac{4 \pi^2 r^3}{G M} \]

### 2. Implications in Astronomy

- This relationship allows astronomers to determine planetary masses and distances without direct measurements.
- It explains why outer planets have longer orbital periods.
- Used in exoplanet detection and understanding binary star systems.

### 3. Real-World Examples

- **Earth-Moon System**: Applying the law to determine the Moon’s distance.
- **Solar System**: Predicting planetary orbits using known masses.
- **Satellite Orbits**: Verifying geostationary orbit conditions.

### 4. Computational Implementation

- Simulating circular orbits using Newton’s equations.
- Verifying Kepler’s Third Law numerically.

---

## Examples

### 1. Kepler's Third Law Visualization

![Kepler's Law](https://www.physicsclassroom.com/Class/circles/u3l4a2.gif)
_Graphical representation of T² ∝ r³ relationship_

### 2. Solar System Orbits

![Planetary orbits](https://scijinks.gov/wp-content/uploads/2023/08/orbits.png)
_Relative orbital radii and periods of planets_

### 3. Binary Star System

![Binary stars](https://www.researchgate.net/publication/334650187/figure/fig1/AS:781437319036928@1563550422668/Orbits-in-a-binary-star-system.png)
_Mutual orbit with common center of mass_

### 4. Geostationary Orbit

![Geo orbit](https://www.esa.int/var/esa/storage/images/esa_multimedia/images/2013/03/geostationary_orbit/12564070-1-eng-GB/Geostationary_orbit.jpg)
_Special case where T = 24 hours (r ≈ 42,164 km)_

### 5. Moon's Orbit

![Lunar orbit](https://moon.nasa.gov/system/resources/detail_files/614_moon-phases-2021.jpg)
_T = 27.3 days, r ≈ 384,400 km_

### 6. Exoplanet Transit Data

![Light curve](https://exoplanets.nasa.gov/system/resources/detail_files/313_transit-graph-1.jpg)
_Period detection from observed transits_

### 7. Hohmann Transfer Orbit

![Transfer orbit](https://www.esa.int/var/esa/storage/images/esa_multimedia/images/2013/03/hohmann_transfer_orbit/12564072-1-eng-GB/Hohmann_transfer_orbit.jpg)
_Orbital period matching for efficient transfers_

## Python Implementation

```python
import numpy as np
import matplotlib.pyplot as plt

def kepler_law(r, M, G=6.67430e-11):
    return np.sqrt((4 * np.pi**2 * r**3) / (G * M))

# Example: Earth orbiting the Sun
M_sun = 1.989e30  # Mass of the Sun in kg
r_values = np.linspace(1e10, 1e12, 100)  # Orbital radii in meters
T_values = kepler_law(r_values, M_sun)

plt.figure(figsize=(8, 6))
plt.plot(r_values, T_values**2, label='T^2 vs. r^3')
plt.xlabel('Orbital Radius (m)')
plt.ylabel('Orbital Period Squared (s^2)')
plt.title("Kepler's Third Law: T^2 vs. r^3")
plt.legend()
plt.grid()
plt.show()
```

---

## Results and Observations

- The graph confirms the linearity between \(T^2\) and \(r^3\).
- Increasing mass \(M\) decreases orbital periods for a given radius.
- Satellites closer to Earth have shorter periods than distant ones.

---

## Extension to Elliptical Orbits

- Kepler’s Third Law holds for elliptical orbits by considering the semi-major axis \(a\) instead of \(r\).
- Used in analyzing asteroid belts and multi-star systems.

---

## Conclusion

Kepler’s Third Law is fundamental in celestial mechanics, bridging theoretical physics with astronomical observations. By leveraging computational models, we can extend these principles to predict and analyze a variety of orbital phenomena, from planetary motion to artificial satellite deployment.
