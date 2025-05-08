#  Mechanics – Problem 1

### Investigating the Range as a Function of the Angle of Projection

---

###  Motivation

Projectile motion demonstrates key physical principles through accessible equations. The relationship between range and angle is non-linear and sensitive to parameters like initial speed and gravity. By exploring this systematically, we uncover how small changes in initial conditions can drastically alter outcomes.

---

###  Theoretical Foundation

From Newton’s second law, the motion of a projectile (ignoring air resistance) is governed by:

**Equations of motion:**

$$
x(t) = v_0 \cos(\theta) t \quad\text{and}\quad y(t) = v_0 \sin(\theta) t - \frac{1}{2}gt^2
$$

Set $y(t) = 0$ to find time of flight (assuming launch and landing heights are equal):

$$
0 = v_0 \sin(\theta) t - \frac{1}{2}gt^2 \Rightarrow t = \frac{2v_0 \sin(\theta)}{g}
$$

Substitute into $x(t)$ to get the **range**:

$$
R = v_0 \cos(\theta) \cdot \frac{2v_0 \sin(\theta)}{g} = \frac{v_0^2 \sin(2\theta)}{g}
$$

This shows that the range depends on $\sin(2\theta)$, reaching a maximum at $\theta = 45^\circ$.

---

### Analysis of the Range

* For fixed $v_0$ and $g$, $R(\theta)$ is symmetric around $45^\circ$.
* Increasing $v_0$ quadratically increases range.
* Higher gravity shortens the range.


---

###  Practical Applications

* **Sports**: Optimizing the angle for maximum distance in javelin or football.
* **Military**: Calculating artillery firing angles.
* **Engineering**: Launch dynamics of rockets or drones.

---

###  Limitations and Extensions

* **Air resistance** reduces range and shifts the optimal angle < 45°.
* **Uneven terrain** changes the final height, requiring a modified trajectory equation.
* **Wind** introduces lateral and vertical forces that must be modeled with differential equations.

---

Would you like help extending the simulation to include air resistance or varying launch height?
