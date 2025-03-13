# Problem 1

[simulation](simulation_projecttile.html)


Let’s dive into this problem step by step, exploring the mechanics of projectile motion with enthusiasm and clarity. We’ll derive the equations, analyze the range, discuss practical applications, and outline a computational approach—all while keeping the physics intuitive and engaging.

---

### 1. Theoretical Foundation

Projectile motion is a classic example of motion under constant acceleration, where the only force acting is gravity (assuming no air resistance for now). Let’s derive the governing equations from first principles.

#### Step 1: Set Up the Problem

Consider a projectile launched from the origin \((x_0, y_0) = (0, 0)\) with an initial velocity \(v_0\) at an angle \(\theta\) above the horizontal. The acceleration due to gravity \(g\) acts downward. We split the motion into horizontal (x) and vertical (y) components:

- **Initial velocities:**

  - \(v_{0x} = v_0 \cos\theta\) (horizontal, constant since no horizontal acceleration)
  - \(v_{0y} = v_0 \sin\theta\) (vertical, affected by gravity)

- **Accelerations:**

  - \(a_x = 0\) (horizontal)
  - \(a_y = -g\) (vertical, downward)

#### Step 2: Derive Equations via Kinematics

Using the kinematic equations \(s = ut + \frac{1}{2}at^2\) and \(v = u + at\):

- **Horizontal motion:**

  - Velocity: \(v_x = v_{0x} = v_0 \cos\theta\)
  - Position: \(x(t) = v_{0x} t = (v_0 \cos\theta) t\)

- **Vertical motion:**

  - Velocity: \(v_y = v_{0y} - gt = v_0 \sin\theta - gt\)
  - Position: \(y(t) = v_{0y} t - \frac{1}{2} g t^2 = (v_0 \sin\theta) t - \frac{1}{2} g t^2\)

Alternatively, we could solve the differential equations:
- $\frac{d^2 x}{dt^2} = 0$, so $x(t) = (v_0 \cos\theta) t$
- $\frac{d^2 y}{dt^2} = -g$, integrating twice with initial conditions gives $y(t) = (v_0 \sin\theta) t - \frac{1}{2} g t^2$.

#### Step 3: Family of Solutions

These equations describe a parabola, and the trajectory depends on the parameters \(v_0\), \(\theta\), and \(g\). Changing \(v_0\) scales the size of the parabola, \(\theta\) adjusts its shape and orientation, and \(g\) (e.g., 9.8 m/s² on Earth vs. 1.6 m/s² on the Moon) alters the curvature. Launch height \(h\) (if \(y_0 \neq 0\)) shifts the starting point, adding versatility to the solutions.

---

### 2. Analysis of the Range

The **range** is the horizontal distance traveled when the projectile returns to \(y = 0\).

#### Step 1: Time of Flight

Set \(y(t) = 0\):
$$
0 = (v_0 \sin\theta) t - \frac{1}{2} g t^2
$$
Factorize:
$$
t \left( v_0 \sin\theta - \frac{1}{2} g t \right) = 0
$$
Solutions:
- \(t = 0\) (launch)
- \(t = \frac{2 v_0 \sin\theta}{g}\) (landing)

Time of flight is $T = \frac{2 v_0 \sin\theta}{g}$.

#### Step 2: Range Equation

Substitute $t = T$ into $x(t)$:
$$
R = x(T) = (v_0 \cos\theta) \cdot \frac{2 v_0 \sin\theta}{g} = \frac{2 v_0^2 \sin\theta \cos\theta}{g}
$$
Using the identity $\sin 2\theta = 2 \sin\theta \cos\theta$:
$$
R = \frac{v_0^2 \sin 2\theta}{g}
$$

#### Step 3: Dependence on \(\theta\)

- **Maximum Range:** $R$ is maximized when $\sin 2\theta = 1$, so $2\theta = 90^\circ$, or \(\theta = 45^\circ\). Then, $R_{\text{max}} = \frac{v_0^2}{g}$.
- **Symmetry:** $R(\theta) = R(90^\circ - \theta)$ because \(\sin(180^\circ - 2\theta) = \sin 2\theta\). E.g., \(\theta = 30^\circ\) and \(60^\circ\) yield the same range.
- **Extremes:** At \(\theta = 0^\circ\) or \(90^\circ\), $\sin 2\theta = 0$, so $R = 0$.

#### Step 4: Other Parameters

- **Initial Velocity (\(v_0\)):** $R \propto v_0^2$, a quadratic scaling. Doubling \(v_0\) quadruples the range.
- **Gravity (\(g\)):** $R \propto \frac{1}{g}$. Lower gravity (e.g., on the Moon) increases range for the same \(v_0\) and \(\theta\).

---

### 3. Practical Applications

This model is a starting point for real-world scenarios:
- **Uneven Terrain:** If launched from height \(h\), the time to hit \(y = 0\) comes from solving $0 = h + (v_0 \sin\theta) t - \frac{1}{2} g t^2$, a quadratic in \(t\). Range becomes:
  $$
  R = v_0 \cos\theta \cdot \frac{v_0 \sin\theta + \sqrt{(v_0 \sin\theta)^2 + 2gh}}{g}
  $$
  Optimal \(\theta\) shifts below 45° as \(h\) increases.
- **Air Resistance:** Adds a drag force proportional to velocity (or its square), turning the equations into nonlinear differential equations. Range decreases, and the optimal angle shifts (typically < 45°).
- **Examples:** Soccer kicks (low \(\theta\) for speed), basketball shots (higher \(\theta\) for arc), or artillery (adjusting for terrain and wind).

---

### 4. Implementation

Let’s outline a Python simulation to compute and visualize the range.

#### Algorithm

1. Define parameters: \(v_0\), \(g\), and a range of \(\theta\) (e.g., 0° to 90°).
2. Compute $R = \frac{v_0^2 \sin 2\theta}{g}$ for each \(\theta\).
3. Plot $R$ vs. \(\theta\).

#### Sample Code

```python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
v0 = 20.0  # m/s
g = 9.8    # m/s^2
theta_deg = np.linspace(0, 90, 181)  # angles in degrees
theta_rad = np.radians(theta_deg)

# Range calculation
R = (v0**2 * np.sin(2 * theta_rad)) / g

# Plot
plt.plot(theta_deg, R, label=f'v₀ = {v0} m/s, g = {g} m/s²')
plt.xlabel('Angle of Projection (degrees)')
plt.ylabel('Range (meters)')
plt.title('Range vs. Angle of Projection')
plt.grid(True)
plt.legend()
plt.show()

# Maximum range
max_R = max(R)
optimal_theta = theta_deg[np.argmax(R)]
print(f'Max Range: {max_R:.2f} m at θ = {optimal_theta}°')
```

#### Enhancements

- Vary \(v_0\) or \(g\) and overlay curves.
- Add trajectories $y(x) = x \tan\theta - \frac{g x^2}{2 v_0^2 \cos^2\theta}$ for selected \(\theta\).

---

### Conclusion

The range’s dependence on \(\theta\) peaking at 45° is a beautiful result of symmetry in projectile motion. Tweaking \(v_0\), \(g\), or adding real-world factors like height or drag opens up a playground of exploration—perfect for physics enthusiasts and practical applications alike!