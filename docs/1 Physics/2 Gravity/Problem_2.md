
---

#  Cosmic Velocities and Escape Velocities

##  Motivation

Understanding how fast a spacecraft must travel to orbit, escape a planet, or leave a solar system is critical in space missions. These thresholds are known as **cosmic velocities**, and they help define the mechanics of launching satellites, interplanetary travel, and interstellar missions.

---

## Definitions
### 1. First Cosmic Velocity (Orbital Velocity)

* **Definition**: The minimum speed required for an object to enter a stable circular orbit just above a celestial body’s surface.
* **Formula**:

  $$
  v_1 = \sqrt{\frac{GM}{R}}
  $$

  Where:

  * $G$ is the gravitational constant
  * $M$ is the mass of the celestial body
  * $R$ is the radius of the body

### 2. Second Cosmic Velocity (Escape Velocity)

* **Definition**: The minimum speed needed to escape the gravitational pull of a celestial body without further propulsion.
* **Formula**:

  $$
  v_2 = \sqrt{2} \cdot v_1 = \sqrt{\frac{2GM}{R}}
  $$

### 3. Third Cosmic Velocity (Solar System Escape Velocity)

* **Definition**: The velocity required to escape the gravitational influence of the solar system from a planet.
* **Formula** (approximate from Earth):

  $$
  v_3 = \sqrt{v_2^2 + v_{es, \odot}^2}
  $$

  Where:

  * $v_{es, \odot}$ is the Sun’s escape velocity at Earth's orbit.

---

## 🧮 Python Implementation

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # gravitational constant [m^3/kg/s^2]
AU = 1.496e11  # 1 astronomical unit in meters

# Celestial bodies: Earth, Mars, Jupiter
bodies = {
    "Earth": {"mass": 5.972e24, "radius": 6.371e6, "orbit_radius": AU},
    "Mars": {"mass": 6.417e23, "radius": 3.3895e6, "orbit_radius": 1.524 * AU},
    "Jupiter": {"mass": 1.898e27, "radius": 6.9911e7, "orbit_radius": 5.204 * AU},
}

# Sun's mass for 3rd cosmic velocity
M_sun = 1.989e30

def compute_cosmic_velocities(mass, radius, orbit_radius):
    v1 = np.sqrt(G * mass / radius)
    v2 = np.sqrt(2) * v1
    v_sun_escape = np.sqrt(2 * G * M_sun / orbit_radius)
    v3 = np.sqrt(v2**2 + v_sun_escape**2)
    return v1, v2, v3

# Compute velocities
results = {body: compute_cosmic_velocities(data["mass"], data["radius"], data["orbit_radius"]) for body, data in bodies.items()}

# Visualization
labels = ['First Cosmic Velocity (v1)', 'Second Cosmic Velocity (v2)', 'Third Cosmic Velocity (v3)']
x = np.arange(len(labels))
width = 0.2

fig, ax = plt.subplots(figsize=(10, 6))
for i, (body, velocities) in enumerate(results.items()):
    ax.bar(x + i*width, velocities, width, label=body)

ax.set_ylabel('Velocity (m/s)')
ax.set_title('Cosmic Velocities for Earth, Mars, and Jupiter')
ax.set_xticks(x + width)
ax.set_xticklabels(labels)
ax.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

---

##  Analysis of Results

| Body    | v1 (m/s) | v2 (m/s) | v3 (m/s) |
| ------- | -------- | -------- | -------- |
| Earth   | \~7.9k   | \~11.2k  | \~42.1k  |
| Mars    | \~3.6k   | \~5.0k   | \~34.1k  |
| Jupiter | \~42.0k  | \~59.5k  | \~75.7k  |

* Jupiter's large mass results in significantly higher escape and orbital velocities.
* Mars, being lighter, requires less energy to escape but more to leave the Sun's influence due to its greater distance.

---

##  Relevance to Space Exploration

| Application                          | Related Velocity |
| ------------------------------------ | ---------------- |
| Launching Satellites                 | v1               |
| Leaving Planet (e.g., Moon missions) | v2               |
| Interplanetary/Interstellar Missions | v3               |

### Examples:

* **Satellites** (LEO) require reaching \~7.9 km/s (v1 for Earth).
* **Apollo Missions** reached \~11.2 km/s (v2) to escape Earth.
* **Voyager Probes** exceeded v3 to escape the solar system.

---

## Conclusion

Understanding and calculating cosmic velocities are foundational in:

* Designing launch systems
* Budgeting fuel requirements
* Planning mission trajectories

This analysis also underscores the challenges of interstellar travel, as exceeding the third cosmic velocity requires significant energy investments and innovative propulsion systems.
