# Problem 1

### **Investigating the Range as a Function of the Angle of Projection**  

Projectile motion describes the motion of an object launched into the air under the influence of gravity, assuming no air resistance. It follows a curved trajectory known as a **parabola** and is governed by Newton’s laws of motion. The motion is analyzed by breaking it into two perpendicular components:  

1. **Horizontal Motion** – Constant velocity (no acceleration).  
2. **Vertical Motion** – Accelerated motion due to gravity 


Let’s define key parameters:  
-$v_0$: Initial velocity (m/s).  
-$\theta$: Launch angle (degrees).  
-$g$: Acceleration due to gravity (m/s²).  
-$t$: Time (s).  
-$x, y$: Horizontal and vertical position (m).  

---

### **Equations of Motion**  

#### **Horizontal Motion (Constant Velocity)**  
Since no external force acts horizontally, the acceleration is zero:  

$$
a_x = 0, \quad v_x = v_0 \cos\theta
$$

The horizontal displacement over time is:

$$
x(t) = v_0 \cos\theta \cdot t
$$

#### **Vertical Motion (Accelerated Motion)**  
The object experiences acceleration due to gravity:  

$$
a_y = -g, \quad v_y = v_0 \sin\theta - g t
$$

The vertical displacement is given by the kinematic equation:

$$
y(t) = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
$$

---

### **Key Calculations**  

#### **Time of Flight**  
The total time the projectile stays in the air can be found by setting $y(T) = 0$(assuming it lands at the same height):  

$$
0 = v_0 \sin\theta \cdot T - \frac{1}{2} g T^2
$$

Solving for $T$:  

$$
T = \frac{2 v_0 \sin\theta}{g}
$$

For example, if $v_0 = 20$ m/s and $\theta = 45^\circ$:  

$$
T = \frac{2 (20) \sin 45^\circ}{9.81} = \frac{40 \times 0.707}{9.81} \approx 2.88 \text{ s}
$$

---

#### **Maximum Height**  
The highest point occurs when vertical velocity is zero $(v_y = 0)$:

$$
0 = v_0 \sin\theta - g t
$$

Solving for $t$(time to reach max height):

$$
t_{\text{max}} = \frac{v_0 \sin\theta}{g}
$$

The maximum height is:

$$ 
H = v_0  \sin\theta \cdot t_{\text{max}} - \frac{1}{2} g t_{\text{max}}^2
$$

$$
H = \frac{(v_0 \sin\theta)^2}{2g}
$$

Using $v_0 = 20$ m/s and $\theta = 45^\circ$:

$$
H = \frac{(20 \times 0.707)^2}{2 \times 9.81} = \frac{200}{19.62} \approx 10.19 \text{ m}
$$

---

#### **Range of the Projectile**  
The horizontal distance traveled before hitting the ground is:

$$
R = v_0 \cos\theta \cdot T
$$

Using the flight time equation:

$$
R = \frac{v_0^2 \sin 2\theta}{g}
$$

For $v_0 = 20$ m/s and $\theta = 45^\circ$:

$$
R = \frac{(20)^2 \sin 90^\circ}{9.81} = \frac{400}{9.81} \approx 40.8 \text{ m}
$$



### **Effect of Initial Conditions**  

- **Launch Angle ($\theta$)**:  
  - The maximum range is achieved at  $\theta = 45^\circ$.  
  - Angles $\theta$ and $90^\circ - \theta$ result in the same range.  

- **Initial Speed ($v_0$)**:  
  - Higher $v_0$ increases time in the air and range.  
  - If $v_0$ is doubled, the range increases four times.  

- **Gravity ($g$)**:  
  - Lower gravity increases both flight time and range.  
  - On the Moon ( $g$ \approx 1.62 m/s²), projectiles travel **six times farther** than on Earth.  

---

## **Implementation**

[3D Simulation](simulation_projecttile.html)





