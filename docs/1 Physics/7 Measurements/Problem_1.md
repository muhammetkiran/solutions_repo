# Problem 1

## **Problem 1: Measuring Earth's Gravitational Acceleration with a Pendulum**

### **Motivation**

The gravitational acceleration $g$ is approximately **9.80665 m/s²** at sea level. It governs the motion of objects under the influence of Earth's gravity and is essential in both theoretical and experimental physics. A simple and elegant method for measuring $g$ is using the **period of a simple pendulum**, whose motion is governed by the relationship:

$$
T = 2\pi \sqrt{\frac{L}{g}}
$$

Where:

* $T$: Period of one full oscillation (in seconds)
* $L$: Length of the pendulum (in meters)
* $g$: Gravitational acceleration (in m/s²)

By measuring the length of the pendulum and the period, we can solve for $g$.

---

### **Task**

Perform a pendulum experiment to measure $g$ and analyze the **uncertainties** involved in the length and timing measurements. This task emphasizes good experimental practices and error propagation.

---

### **Procedure**

#### 1. Materials

* String of length ≈ 1.00 or 1.50 meters
* Small dense weight (e.g., metal washer, keychain, bag of coins)
* Stopwatch or smartphone timer (resolution ±0.01 s)
* Ruler or measuring tape (resolution ±0.01 m or ±0.005 m)

#### 2. Setup

* Secure the string to a stable support (e.g., tripod, shelf).
* Measure the **length $L$** from the point of suspension to the center of mass of the weight.
  For example:

  $$
  L = 1.000 \text{ m}, \quad \delta L = \pm 0.005 \text{ m}
  $$

#### 3. Data Collection

* Displace the pendulum by a small angle (<15° to ensure simple harmonic motion).
* Measure the time for **10 oscillations**, denoted as $t_{10}$.
* Repeat this measurement **10 times**, recording all values.
* Compute:

  * Mean time for 10 oscillations:

    $$
    \overline{t_{10}} = \frac{1}{10} \sum_{i=1}^{10} t_{10,i}
    $$
  * Standard deviation $\sigma$
  * Uncertainty in mean:

    $$
    \delta \overline{t_{10}} = \frac{\sigma}{\sqrt{n}}
    $$
  * Period:

    $$
    T = \frac{\overline{t_{10}}}{10}
    $$

---

### **Calculations**

#### 1. Determining Gravitational Acceleration:

From:

$$
T = 2\pi \sqrt{\frac{L}{g}} \Rightarrow g = \frac{4\pi^2 L}{T^2}
$$

For example, if:

* $L = 1.000 \text{ m}$
* $\overline{t_{10}} = 20.05 \text{ s} \Rightarrow T = 2.005 \text{ s}$

Then:

$$
g = \frac{4\pi^2 \cdot 1.000}{(2.005)^2} \approx 9.832 \text{ m/s}^2
$$

#### 2. Propagation of Uncertainty

Using:

$$
\delta g = g \cdot \sqrt{\left( \frac{\delta L}{L} \right)^2 + \left( 2 \cdot \frac{\delta T}{T} \right)^2}
$$

If:

* $\delta L = 0.005 \text{ m}$, $L = 1.000 \text{ m}$
* $\delta T = 0.02 \text{ s}$, $T = 2.005 \text{ s}$

Then:

$$
\delta g \approx 9.832 \cdot \sqrt{(0.005)^2 + \left( 2 \cdot \frac{0.02}{2.005} \right)^2} \approx 0.12 \text{ m/s}^2
$$

Final result:

$$
g = 9.83 \pm 0.12 \text{ m/s}^2
$$

---

### **Analysis**

#### 1. Comparison with Accepted Value:

* Experimental $g = 9.83 \pm 0.12 \text{ m/s}^2$
* Standard $g = 9.80665 \text{ m/s}^2$
* The measured value is within **experimental uncertainty**, indicating good accuracy.

#### 2. Uncertainty Sources:

* **Length uncertainty ($\delta L$)** arises from reading error and string flexibility.
* **Timing uncertainty ($\delta T$)** due to reaction time and stopwatch resolution.
* Assumes:

  * No air resistance
  * Small-angle approximation holds (valid for θ < 15°)
  * Fixed pivot point, negligible damping

---
[Measuring Earth's Gravity with Free Fall](sim1.html)