
## Electromagnetism  
### Problem 1 — Simulating the Effects of the Lorentz Force

---

###  Motivation

The **Lorentz force** governs how charged particles move in the presence of **electric** and **magnetic** fields. It plays a central role in devices such as:

- **Cyclotrons and synchrotrons** (used in particle accelerators),
- **Mass spectrometers** (for analyzing atomic and molecular masses),
- **Plasma confinement devices** (e.g., in fusion reactors).

By simulating the motion of a charged particle under the Lorentz force, we gain insight into the fundamental mechanisms behind electromagnetic control and guidance systems.

---

###  Mathematical Background

The **Lorentz force** acting on a particle with charge $ q $, moving with velocity $ \vec{v} $, in electric field $ \vec{E} $ and magnetic field $ \vec{B} $ is given by:

$$
\vec{F} = q(\vec{E} + \vec{v} \times \vec{B})
$$

According to Newton's second law:

$$
\vec{F} = m \cdot \frac{d\vec{v}}{dt}
$$

Combining both expressions:

$$
m \cdot \frac{d\vec{v}}{dt} = q(\vec{E} + \vec{v} \times \vec{B})
$$

To simulate particle motion, we numerically solve this differential equation using time-stepping methods (e.g., **Euler** or **Runge-Kutta**).

---

###   Simulation Scenarios

We explore the particle's trajectory in three configurations:

1. **Uniform Magnetic Field Only**  
   - Expect circular or helical motion.
   - Larmor radius:  
     $$
     r_L = \frac{mv_\perp}{|qB|}
     $$
   - Cyclotron frequency:  
     $$
     \omega_c = \frac{|qB|}{m}
     $$

2. **Uniform Electric and Magnetic Fields**  
   - Complex trajectory depending on field orientations and strengths.

3. **Crossed $ \vec{E} \perp \vec{B} $** Fields  
   - **$ \vec{E} \times \vec{B} $** drift:
     $$
     \vec{v}_{\text{drift}} = \frac{\vec{E} \times \vec{B}}{B^2}
     $$

---

###   Numerical Method

We use the **Euler method** for simplicity, updating velocity and position iteratively:

$$
\vec{v}_{n+1} = \vec{v}_n + \frac{q}{m} (\vec{E} + \vec{v}_n \times \vec{B}) \cdot \Delta t
$$
$$
\vec{r}_{n+1} = \vec{r}_n + \vec{v}_{n+1} \cdot \Delta t
$$

(Alternatively, a **4th-order Runge-Kutta method** can be used for better accuracy.)

---

###  Parameters

| Symbol     | Meaning                     | Typical Value          |
|------------|-----------------------------|-------------------------|
| $q$    | Particle charge              | $ 1.6 \times 10^{-19} \, \text{C}$ |
| $m$    | Particle mass                | $ 9.1 \times 10^{-31} \, \text{kg}$ (electron) |
| $\vec{E}$ | Electric field vector     | e.g., $ (0, 0, 100) \, \text{V/m}$ |
| $\vec{B}$ | Magnetic field vector     | e.g., $ (0, 0, 1) \, \text{T}$ |
| $\vec{v}_0$ | Initial velocity vector | User-defined            |
| $\Delta t$ | Time step                | $ 1 \times 10^{-11} \, \text{s}$ |


---

###  Visual Output

For each simulation:

- **2D Trajectory**: $x(t), y(t)$
- **3D Trajectory**: $x(t), y(t), z(t)$
- Highlight:
  - Circular or spiral motion
  - Drift due to crossed fields
  - Larmor radius changes with field strength

---

###  Real-World Applications

| Application            | Lorentz Force Effect                            |
|------------------------|-------------------------------------------------|
| Cyclotron              | Particles spiral outward under magnetic field   |
| Mass Spectrometer      | Different trajectories reveal mass/charge ratio |
| Fusion Reactors (Tokamak) | Magnetic confinement of plasma              |

-