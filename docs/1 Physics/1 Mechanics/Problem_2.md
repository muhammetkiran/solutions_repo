# Problem 2

# Investigating the Dynamics of a Forced Damped Pendulum

### **Theoretical Foundations of the Forced Damped Pendulum**
  

The motion of a **forced damped pendulum** is governed by a second-order nonlinear differential equation that incorporates **inertia**, **damping**, **restoring force**, and **external driving force**:  

$\frac{d^2\theta}{dt^2} + \beta \frac{d\theta}{dt} + \frac{g}{L} \sin\theta = \frac{A}{mL^2} \cos(\omega t)$

where:  
- $\theta$ = Angular displacement (radians)  
- $\frac{d^2\theta}{dt^2}$ = Angular acceleration  
- $\frac{d\theta}{dt}$ = Angular velocity  
- $\beta$ = Damping coefficient (s\(^{-1}\))  
- $g$ = Acceleration due to gravity (9.81 m/s²)  
- $L$ = Length of the pendulum (m)  
- $A$ = Amplitude of the external driving torque (N·m)  
- $m$ = Mass of the pendulum bob (kg)  
- $\omega$ = Angular frequency of the driving force (rad/s)  
- $t$ = Time (s)  

---

### **Dimensionless Form of the Equation**  

To simplify the analysis, we introduce **dimensionless variables**:

$\tau = \sqrt{\frac{g}{L}} t, \quad Q = \frac{\beta}{\sqrt{\frac{g}{L}}}, \quad F = \frac{A}{mL^2 \sqrt{\frac{g}{L}}}, \quad \Omega = \frac{\omega}{\sqrt{\frac{g}{L}}}$

Thus, the equation becomes:

$\frac{d^2\theta}{d\tau^2} + Q \frac{d\theta}{d\tau} + \sin\theta = F \cos(\Omega \tau)$

---

### **Key Calculations and Numerical Examples**  

#### **1. Natural Frequency of an Undamped Pendulum**  
For a simple pendulum **without damping** ($\beta = 0$) and **no driving force** ($A = 0$), the equation simplifies to:

$\frac{d^2\theta}{dt^2} + \frac{g}{L} \sin\theta = 0$

For small angles ($\sin\theta \approx \theta$), this reduces to:

$\frac{d^2\theta}{dt^2} + \omega_0^2 \theta = 0$

where:

$\omega_0 = \sqrt{\frac{g}{L}}$

is the **natural frequency** of the pendulum. The solution is:

$\theta(t) = \theta_0 \cos(\omega_0 t + \phi)$

Example Calculation:  
If $L = 1$ m, then:

$\omega_0 = \sqrt{\frac{9.81}{1}} = 3.13 \text{ rad/s}$

The period is:

$T = \frac{2\pi}{\omega_0} = \frac{2\pi}{3.13} \approx 2.01 \text{ s}$

---

---

#### **3. Steady-State Solution with External Forcing**  
For a forced pendulum ($A \neq 0$), the steady-state solution can be found using:

$\theta_{\text{steady}}(t) = \theta_{\text{particular}}(t) + \theta_{\text{transient}}(t)$

where:

$\theta_{\text{particular}}(t) = \frac{F}{\sqrt{(\omega_0^2 - \omega^2)^2 + (\beta \omega)^2}} \cos(\omega t - \delta)$

$\tan\delta = \frac{\beta \omega}{\omega_0^2 - \omega^2}$



Thus, the steady-state response is:

$\theta_{\text{steady}}(t) = 0.14 \cos(2.5t - 35.3^\circ)$

### Practical Applications
Understanding the dynamics of forced damped pendulums is crucial in various fields:

**Engineering:**  Mechanical systems with oscillatory components, such as suspension bridges or clock mechanisms, can experience resonant vibrations leading to structural failures if not properly damped.

**Robotics:** The principles governing pendulum dynamics assist in designing stable walking robots and understanding bipedal locomotion.

**Seismology:** Modeling the Earth's response to periodic forces, such as tidal effects, benefits from insights into forced oscillatory systems.

### Implementation

[ Simulation](sım2.html)
