# Problem 1



# **Orbital Period and Orbital Radius**  

## **Introduction**  

Orbital motion is governed by Newton’s laws of motion and the universal law of gravitation. A satellite, planet, or any celestial body orbiting another massive object follows a predictable path, determined by the balance between gravitational attraction and the object's inertia.  

Two key parameters define an orbit:  

- **Orbital Radius ($r$)**: The distance from the center of the central mass (e.g., the Earth or the Sun) to the orbiting object.  
- **Orbital Period ($T$)**: The time required for the object to complete one full revolution around the central body.  

For a stable orbit, the gravitational force must act as the centripetal force that keeps the object in circular motion.  

---

## **Theory**  

The gravitational force between two masses $M$ (central body) and $m$ (orbiting body) is given by Newton’s Law of Universal Gravitation:  

$F_g = \frac{GMm}{r^2}$

For an object in a circular orbit, the required centripetal force is:  

$F_c = \frac{m v^2}{r}$

Since gravity provides the necessary centripetal force, we set these two forces equal to each other:  

 $\frac{GMm}{r^2} = \frac{m v^2}{r}$

Canceling $m$ and solving for orbital velocity $v$:  

$v = \sqrt{\frac{GM}{r}}$

Since orbital period $T$ is the time taken to complete one full orbit, we use the relationship between velocity, circumference, and time:  

$T = \frac{2\pi r}{v}$

Substituting $v$:  

$T = 2\pi \sqrt{\frac{r^3}{GM}}$

### **Key Observations:**  

1. The orbital period increases with the cube root of the orbital radius. This is a direct consequence of **Kepler’s Third Law**, which states:  

   $T^2 \propto r^3$

2. The larger the central mass $M$, the stronger the gravitational pull, leading to shorter orbital periods for a given radius.  

3. Satellites closer to the Earth orbit faster than those farther away, explaining why the International Space Station (ISS) orbits in about **90 minutes**, while the Moon takes **27.3 days**.  

---

## **Example Problem**  

### **Problem Statement:**  
A satellite is launched into a circular orbit **500 km above Earth's surface**. Determine its orbital period.  

### **Given Data:**  

- **Mass of Earth:** $M = 5.972 \times 10^{24}$ kg  
- **Radius of Earth:** $R_E = 6.371 \times 10^6$ m  
- **Altitude of the satellite:** $h = 500 \times 10^3$ m  
- **Gravitational constant:** $G = 6.674 \times 10^{-11}$ Nm²/kg²  

### **Step 1: Calculate Orbital Radius**  

The orbital radius is the sum of Earth’s radius and the satellite’s altitude:  

$r = R_E + h = (6.371 \times 10^6) + (500 \times 10^3)$

$r = 6.871 \times 10^6 \text{ m}$

### **Step 2: Apply the Orbital Period Formula**  

$T = 2\pi \sqrt{\frac{r^3}{GM}}$

Substituting values:  

$T = 2\pi \sqrt{\frac{(6.871 \times 10^6)^3}{(6.674 \times 10^{-11}) (5.972 \times 10^{24})}}$

$T \approx 5674 \text{ s} \approx 94.6 \text{ min}$

### **Step 3: Interpretation**  

- The satellite completes one orbit in **approximately 94.6 minutes**.  
- This means an observer on Earth would see the satellite pass overhead multiple times per day.  
- Lower-altitude satellites orbit faster due to stronger gravitational pull, while higher-altitude satellites (e.g., geostationary satellites at **35,786 km**) have much longer periods, often **24 hours**.  

---

## **Applications and Real-World Importance**  

### **1. Satellites and Space Missions**  
- The orbital period determines how often communication satellites pass over a given location.  
- Geostationary satellites are positioned at a specific orbital radius so that their period matches Earth’s rotation (24 hours), keeping them fixed relative to the ground.  

### **2. Planetary Orbits**  
- Kepler’s Laws allow astronomers to determine the distances and periods of planets in our Solar System.  
- For example, Earth’s orbital radius around the Sun is **1 AU** $(1.496 \times 10^{11}$ m), giving it a **365.25-day period**.  

### **3. Space Travel and Orbital Transfers**  
- Understanding orbital mechanics is crucial for launching satellites, planning space missions, and docking with the ISS.  
- The Hohmann Transfer Orbit method is used to move satellites between different orbits using minimal fuel.  

---

## **Conclusion**  

The relationship between **orbital period and radius** is fundamental in astrophysics and engineering. The **$T = 2\pi \sqrt{r^3/GM}$** equation helps predict how celestial bodies and artificial satellites move in space. 

[simulation](orbital_period_simulatin.html)