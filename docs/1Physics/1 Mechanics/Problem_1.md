# Problem 1

# Investigating the Range as a Function of the Angle of Projection

## Motivation

Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Yet, beneath this simplicity lies a complex and versatile framework. The equations governing projectile motion involve both linear and quadratic relationships, making them accessible yet deeply insightful.

What makes this topic particularly compelling is the number of free parameters involved in these equations, such as initial velocity, gravitational acceleration, and launch height. These parameters give rise to a diverse set of solutions that can describe a wide array of real-world phenomena, from the arc of a soccer ball to the trajectory of a rocket.

---

## Task

### 1. Theoretical Foundation

- Derive the governing equations of motion from fundamental principles.
- Solve the basic differential equation to establish the general form of the motion.
- Highlight how variations in initial conditions lead to a family of solutions.

### 2. Analysis of the Range

- Investigate how the horizontal range depends on the angle of projection.
- Discuss how changes in other parameters, such as initial velocity and gravitational acceleration, influence the relationship.

### 3. Practical Applications

- Reflect on how this model can be adapted to describe various real-world situations, such as projectiles launched on uneven terrain or in the presence of air resistance.

### 4. Implementation

- Develop a computational tool or algorithm to simulate projectile motion.
- Visualize the range as a function of the angle of projection for different sets of initial conditions.

---

## Governing Equations

The equations for projectile motion under the influence of gravity (neglecting air resistance) are:

\[ x = v_0 \cos(\theta) t \]
\[ y = v_0 \sin(\theta) t - \frac{1}{2} g t^2 \]

The time of flight is given by:

\[ t_f = \frac{2 v_0 \sin(\theta)}{g} \]

The range \( R \) is given by:

\[ R = \frac{v_0^2 \sin(2\theta)}{g} \]

This equation shows that the maximum range is achieved at \( \theta = 45^\circ \).

---

## Python Implementation

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, g=9.81):
    angles = np.linspace(0, 90, num=100)
    ranges = (v0**2 * np.sin(np.radians(2 * angles))) / g

    plt.figure(figsize=(8, 6))
    plt.plot(angles, ranges, label=f'Initial Velocity = {v0} m/s')
    plt.xlabel('Angle of Projection (degrees)')
    plt.ylabel('Range (m)')
    plt.title('Projectile Range vs. Angle of Projection')
    plt.legend()
    plt.grid()
    plt.show()

# Example usage
projectile_range(v0=20)
```

---

## Examples

## Examples

### 1. Basic Projectile Trajectories

![Projectile at different angles](https://www.sciencefacts.net/wp-content/uploads/2022/06/Projectile-Motion-Range.jpg)
_Comparison of trajectories at 30°, 45°, and 60° launch angles_

### 2. Range vs Angle Graph

![Range vs angle plot](https://phys.libretexts.org/@api/deki/files/5246/clipboard_eeb6b6e5a4e3c1b7a5c0d6b5f5e8e8b1.png)
_Theoretical range as function of launch angle (peaks at 45°)_

### 3. Effect of Air Resistance

![With and without air drag](https://www.researchgate.net/publication/344416420/figure/fig2/AS:940551366553601@1601470306164/Trajectories-of-a-projectile-in-a-vacuum-red-and-in-air-blue.png)
_Red: Ideal vacuum trajectory; Blue: Real-world trajectory with air resistance_

### 4. Projectile Equations Diagram

![Key equations](https://www.physicsclassroom.com/Class/vectors/u3l2a2.gif)
_Visual representation of projectile motion equations_

### 5. Uneven Terrain Example

![Launch from cliff](https://www.physicsclassroom.com/Images/Class/vectors/u3l2a3.gif)
_Projectile launched from elevated position showing asymmetric range_

## Results and Observations

- The range follows a symmetric pattern, peaking at \(45^\circ\).
- Higher initial velocity increases the maximum range.
- Changing gravity (e.g., different planets) alters the range behavior.

---

## Limitations and Further Considerations

- Air resistance is neglected in this model.
- Uneven terrain is not accounted for.
- Real-world effects like wind and spin could be included in a more advanced model.

---

## Conclusion

This study of projectile motion highlights the elegance of physics and the practical implications of mathematical models. By extending this analysis to include drag or varying gravitational fields, we can better understand complex real-world scenarios, from sports to aerospace engineering.
