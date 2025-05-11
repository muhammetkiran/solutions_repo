Elbette! Aşağıda, **Monte Carlo yöntemleriyle π'nin tahmini** problemini içeren açıklamayı **biraz daha uzun**, **daha fazla sayısal ifade içeren** ve teknik yönleri öne çıkaran bir şekilde sunuyorum. Bu versiyon, hem teorik hem de uygulamalı yönleri dengeli şekilde açıklar:

---

## **Problem 2: Estimating π Using Monte Carlo Methods**

### **Motivation**

The number **π (pi)** is a fundamental mathematical constant that represents the ratio of a circle’s circumference to its diameter, approximately **3.1415926535…**. Despite its apparent simplicity, π cannot be expressed exactly as a fraction and has an infinite non-repeating decimal expansion. Estimating π numerically is an excellent example of how randomness and probability can be used to solve deterministic problems.

**Monte Carlo methods** are a family of computational algorithms that rely on repeated random sampling to obtain numerical results. These methods are widely used in fields such as **physics**, **finance**, **AI**, and **engineering**, especially when deterministic methods become too complex or infeasible.

This problem uses two classical Monte Carlo approaches to estimate π:

1. **The Circle Method** (Geometric probability)
2. **Buffon's Needle Experiment** (Probabilistic geometry)

---

## **Part 1: Estimating π Using a Circle**

### **Theoretical Foundation**

Imagine a **unit circle** (radius $r = 1$) centered at the origin and inscribed in a square with side length 2. The area of the circle is:

$$
A_{\text{circle}} = \pi r^2 = \pi
$$

The area of the square is:

$$
A_{\text{square}} = (2r)^2 = 4
$$

Therefore, the probability that a randomly chosen point inside the square also lies inside the circle is:

$$
P = \frac{A_{\text{circle}}}{A_{\text{square}}} = \frac{\pi}{4}
$$

Thus, if we generate **N** random points $(x, y)$ uniformly in the square $[-1, 1] \times [-1, 1]$ and count how many of them fall inside the circle (i.e., satisfy $x^2 + y^2 \leq 1$), then:

$$
\pi \approx 4 \cdot \frac{N_{\text{inside}}}{N}
$$

### **Numerical Results Example**

* For **N = 1,000** points → π ≈ 3.14
* For **N = 10,000** points → π ≈ 3.141
* For **N = 1,000,000** points → π ≈ 3.14159

The accuracy improves with **$\sqrt{N}$** convergence behavior — to get one more digit of accuracy, we need roughly **100×** more samples.

---

## **Part 2: Estimating π Using Buffon’s Needle**

### **Theoretical Foundation**

**Buffon's Needle Problem** is one of the earliest problems in geometric probability. Consider a floor with equally spaced parallel lines, **d** units apart. If we randomly drop a needle of length **L ≤ d**, the probability that the needle crosses a line is given by:

$$
P = \frac{2L}{\pi d}
$$

Solving for π:

$$
\pi \approx \frac{2L \cdot N}{d \cdot H}
$$

Where:

* $N$ = total number of needle drops
* $H$ = number of times the needle crosses a line

For example, if we drop **10,000 needles** of length 1 on lines spaced 2 units apart, and **6,366** cross a line, we estimate:

$$
\pi \approx \frac{2 \cdot 1 \cdot 10,000}{2 \cdot 6366} \approx 3.1413
$$

### **Statistical Behavior**

Buffon's method tends to converge more slowly than the circle method due to its dependence on trigonometric functions and geometric constraints. The accuracy also depends heavily on having a large number of hits $H$, making small sample sizes unstable.

---

## **Comparison of Methods**

| Method             | Convergence Rate        | Complexity      | Suitable For                            |
| ------------------ | ----------------------- | --------------- | --------------------------------------- |
| Circle Monte Carlo | $O(\frac{1}{\sqrt{N}})$ | Simple Geometry | Quick Estimation                        |
| Buffon’s Needle    | Slower, probabilistic   | Trigonometry    | Historical curiosity, advanced problems |

---

