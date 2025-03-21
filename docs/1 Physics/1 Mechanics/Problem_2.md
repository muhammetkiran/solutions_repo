# Problem 2

Below is a revised version of the write-up for "Investigating the Dynamics of a Forced Damped Pendulum," starting with an explanation of differential equations before diving into the specific problem. I’ve kept it concise, added definitions and a numerical step as requested, and maintained the style of the GitHub example.

---

# Investigating the Dynamics of a Forced Damped Pendulum

## Differential Equations: The Foundation
Differential equations describe how quantities change over time, linking rates (derivatives) to the quantities themselves. They’re essential in physics for modeling dynamic systems. For a pendulum, we use:
- **Ordinary Differential Equations (ODEs)**: Functions of one variable (time, $ t $), like position or velocity.
- **Second-Order ODEs**: Involve second derivatives (e.g., acceleration), common for mechanical systems.
- **Nonlinear ODEs**: Contain terms like $ \sin(\theta) $, making analytical solutions difficult, requiring numerical methods.

Our goal is to formulate and solve such an equation for a pendulum with damping and forcing.

---

## Problem Statement
A pendulum (length $ L = 1 \, \text{m} $, mass $ m = 1 \, \text{kg} $) experiences:
- **Gravity**: Pulls it downward.
- **Damping**: Friction, coefficient $ b $ (s⁻¹), opposes motion.
- **Forcing**: Periodic torque $ A \cos(\omega_f t) $, with amplitude $ A $ (s⁻²) and frequency $ \omega_f $ (rad/s).

We’ll define its motion, solve numerically, and explore parameter effects.

---

## Theoretical Background
The pendulum’s angle $ \theta $ (radians) follows a second-order ODE. The **natural frequency** is $ \omega_0 = \sqrt{g/L} $, where $ g = 9.8 \, \text{m/s}^2 $. Including damping and forcing:
$
\frac{d^2\theta}{dt^2} = -\omega_0^2 \sin(\theta) - b \frac{d\theta}{dt} + A \cos(\omega_f t)
$
Split into first-order ODEs:
$
\frac{d\theta}{dt} = \omega
$
$
\frac{d\omega}{dt} = -\omega_0^2 \sin(\theta) - b \omega + A \cos(\omega_f t)
$

---

## Numerical Solution
We solve using the **Runge-Kutta 4th-order (RK4)** method, time step $ dt = 0.02 \, \text{s} $. Example step:
- Initial: $ \theta = 0.2 $, $ \omega = 0 $, $ t = 0 $, $ b = 0.2 $, $ A = 1.2 $, $ \omega_f = 0.67 $.
- $ k_1 = \omega = 0 $
- $ l_1 = -\omega_0^2 \sin(\theta) - b \omega + A \cos(\omega_f t) = -9.8 \sin(0.2) - 0.2 \cdot 0 + 1.2 \cos(0) \approx -1.951 + 1.2 = -0.751 $
- After RK4: $ \theta \approx 0.2 $, $ \omega \approx -0.015 $.

---


Parameters: $ b $ (0–1), $ A $ (0–2), $ \omega_f $ (0–2), $ \theta_0 $ (-π to π).

---

## Results
- **Low Forcing**: $ b = 0.2 $, $ A = 0.5 $, $ \omega_f = 1.0 $: Periodic decay, spiral phase plot.
- **High Forcing**: $ b = 0.2 $, $ A = 1.2 $, $ \omega_f = 0.67 $: Chaotic motion, strange attractor.





