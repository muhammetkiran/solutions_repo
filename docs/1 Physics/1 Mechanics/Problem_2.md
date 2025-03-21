# Problem 2

### **Theoretical Foundations of the Forced Damped Pendulum**

### **Differential Equations Governing the Forced Damped Pendulum**  

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

#### **2. Damped Motion Without External Force**  
If damping is present but no external force ($A = 0$), the equation becomes:

$\frac{d^2\theta}{dt^2} + \beta \frac{d\theta}{dt} + \omega_0^2 \theta = 0$

The general solution depends on the damping coefficient $\beta$:

- **Underdamped Motion ($\beta < 2\omega_0$)**:
  $\theta(t) = \theta_0 e^{-\frac{\beta}{2} t} \cos\left(\omega_d t + \phi \right)$
  where:
  $\omega_d = \sqrt{\omega_0^2 - \left(\frac{\beta}{2}\right)^2}$

  Example Calculation:  
  If $\beta = 1$ s\(^{-1}\) and $L = 1$ m:

  $\omega_d = \sqrt{(3.13)^2 - (0.5)^2} = \sqrt{9.80} \approx 3.13 \text{ rad/s}$

  The oscillations decay exponentially due to the damping term $e^{-\frac{\beta}{2} t}$.

- **Critically Damped Motion ($\beta = 2\omega_0$)**:  
  $\theta(t) = (\theta_0 + v_0 t) e^{-\omega_0 t}$

- **Overdamped Motion ($\beta > 2\omega_0$)**:
  $\theta(t) = e^{-\frac{\beta}{2} t} (C_1 e^{r_1 t} + C_2 e^{r_2 t})$
  where:
  $r_{1,2} = -\frac{\beta}{2} \pm \sqrt{\left(\frac{\beta}{2}\right)^2 - \omega_0^2}$

---

#### **3. Steady-State Solution with External Forcing**  
For a forced pendulum ($A \neq 0$), the steady-state solution can be found using:

$\theta_{\text{steady}}(t) = \theta_{\text{particular}}(t) + \theta_{\text{transient}}(t)$

where:

$\theta_{\text{particular}}(t) = \frac{F}{\sqrt{(\omega_0^2 - \omega^2)^2 + (\beta \omega)^2}} \cos(\omega t - \delta)$

$\tan\delta = \frac{\beta \omega}{\omega_0^2 - \omega^2}$

Example Calculation:  
For $\omega_0 = 3.13$ rad/s, $\beta = 1$ s\(^{-1}\), $F = 0.5$, and $\omega = 2.5$ rad/s:

$\theta_{\text{particular}} = \frac{0.5}{\sqrt{(3.13^2 - 2.5^2)^2 + (1 \times 2.5)^2}}$

$\approx \frac{0.5}{\sqrt{(9.80 - 6.25)^2 + (2.5)^2}} = \frac{0.5}{\sqrt{12.56}} \approx 0.14$

$\tan\delta = \frac{1 \times 2.5}{9.80 - 6.25} = \frac{2.5}{3.55} \approx 0.704 \quad \Rightarrow \quad \delta \approx 35.3^\circ$

Thus, the steady-state response is:

$\theta_{\text{steady}}(t) = 0.14 \cos(2.5t - 35.3^\circ)$

---


#### **Equations of Motion**

The dynamics of a forced damped pendulum are governed by the following second-order nonlinear differential equation:

$\frac{d^2\theta}{dt^2} + \beta \frac{d\theta}{dt} + \frac{g}{L} \sin\theta = \frac{A}{mL^2} \cos(\omega t)$

Where:

- $\theta$: Angular displacement (radians)
- $\beta$: Damping coefficient (s\(^{-1}\))
- $g$: Acceleration due to gravity (9.81 m/s\(^2\))
- $L$: Length of the pendulum (meters)
- $A$: Amplitude of the external driving torque (N·m)
- $m$: Mass of the pendulum bob (kg)
- $\omega$: Angular frequency of the driving force (rad/s)
- $t$: Time (seconds)

This equation balances the inertial term ($\frac{d^2\theta}{dt^2}$), damping term ($\beta \frac{d\theta}{dt}$), restoring force ($\frac{g}{L} \sin\theta$), and the external driving force ($\frac{A}{mL^2} \cos(\omega t)$).

#### **Dimensionless Form**

To simplify analysis, we often convert the equation into a dimensionless form by introducing scaled variables:

$
\frac{d^2\theta}{d\tau^2} + Q \frac{d\theta}{d\tau} + \sin\theta = F \cos(\Omega \tau)
$

Where:

- $\tau = \sqrt{\frac{g}{L}} t$: Dimensionless time
- $Q = \frac{\beta}{\sqrt{\frac{g}{L}}}$: Dimensionless damping coefficient
- $F = \frac{A}{mL^2 \sqrt{\frac{g}{L}}}$: Dimensionless driving amplitude
- $\Omega = \frac{\omega}{\sqrt{\frac{g}{L}}}$: Dimensionless driving frequency

This form highlights the key parameters influencing the system's behavior: damping ($Q$), driving amplitude ($F$), and driving frequency ($\Omega$).

### **Behavioral Dynamics**

The forced damped pendulum exhibits a rich tapestry of dynamical behaviors depending on the system parameters:

- **Periodic Motion**: For small driving amplitudes and specific frequencies, the pendulum oscillates periodically, often synchronizing with the driving force.

- **Period Doubling**: As the driving amplitude increases, the system may undergo bifurcations where the period of oscillation doubles, leading to motions with periods that are integer multiples of the driving period. This phenomenon is a precursor to chaos. citeturn0search3

- **Chaotic Motion**: At certain parameter thresholds, the pendulum exhibits chaotic behavior, characterized by sensitive dependence on initial conditions and aperiodic trajectories. This means that tiny differences in starting conditions can lead to vastly different outcomes, making long-term prediction impossible. citeturn0search0

### **Phase Space and Poincaré Sections**

Analyzing the system's behavior often involves examining its phase space—a plot of angular velocity ($\frac{d\theta}{dt}$) versus angular displacement ($\theta$). In chaotic regimes, the phase space reveals strange attractors, indicating complex, non-repeating trajectories.

**Poincaré sections** are a valuable tool for visualizing the system's dynamics. By plotting the pendulum's state at regular intervals synchronized with the driving period, we obtain a discrete map that can reveal fixed points, periodic orbits, and chaotic scatterings, providing insight into the underlying structure of the motion.

### **Practical Implications**

Understanding the dynamics of forced damped pendulums is crucial in various fields:

- **Engineering**: Mechanical systems with oscillatory components, such as suspension bridges or clock mechanisms, can experience resonant vibrations leading to structural failures if not properly damped.

- **Robotics**: The principles governing pendulum dynamics assist in designing stable walking robots and understanding bipedal locomotion.

- **Seismology**: Modeling the Earth's response to periodic forces, such as tidal effects, benefits from insights into forced oscillatory systems.

### **Conclusion**

The forced damped pendulum serves as a fundamental model for exploring nonlinear dynamics, chaos theory, and complex oscillatory behavior. Its study not only deepens our understanding of mathematical physics but also informs practical applications across engineering, robotics, and natural sciences. 