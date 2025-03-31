# Problem 1

# Derivation of the Relationship Between Orbital Period and Orbital Radius

### Introduction
The relationship between the orbital period ($T$) and the orbital radius ($r$) for circular orbits is a fundamental result in celestial mechanics, known as **Kepler's Third Law**. This law states that the square of the orbital period is proportional to the cube of the orbital radius. In this section, we will derive the mathematical expression for the orbital period in terms of the orbital radius.

### Step-by-Step Derivation

1. **Gravitational Force and Centripetal Force**
   For an object in a circular orbit, the gravitational force provides the necessary centripetal force to keep the object in orbit. The gravitational force $F_g$ is given by:

   $$F_g = G \cdot M \cdot m \cdot r^{-2}$$

   where:
   - $G$ is the gravitational constant,
   - $M$ is the mass of the central object (e.g., the Sun or Earth),
   - $m$ is the mass of the orbiting object,
   - $r$ is the orbital radius (distance from the center of the central object).

   The centripetal force $F_c$ required to maintain the circular motion is:

   $$F_c = m \cdot v^2 \cdot r^{-1}$$

   where $v$ is the orbital velocity of the object.

2. **Equating Gravitational and Centripetal Forces**
   Since the gravitational force provides the centripetal force, we equate the two expressions:

   $$G \cdot M \cdot m \cdot r^{-2} = m \cdot v^2 \cdot r^{-1}$$

   Simplifying this equation by canceling out $m$ and one factor of $r$, we get:

   $$G \cdot M \cdot r^{-1} = v^2$$

   Therefore, the orbital velocity $v$ is given by:

   $$v = \sqrt{G \cdot M \cdot r^{-1}}$$

3. **Relating Velocity to Orbital Period**
   The orbital period $T$ is the time it takes for the object to complete one full revolution around the central object. The distance traveled in one revolution is the circumference of the orbit, $C = 2 \pi r$. The velocity $v$ is related to the period $T$ by the equation:

   $$v = C \cdot T^{-1} = 2 \pi r \cdot T^{-1}$$

   Substituting the expression for $v$ from the previous step:

   $$2 \pi r \cdot T^{-1} = \sqrt{G \cdot M \cdot r^{-1}}$$

4. **Solving for the Orbital Period $T$**
   Rearranging the equation to solve for $T$, we get:

   $$T = 2 \pi \sqrt{r^3 \cdot (G \cdot M)^{-1}}$$

### Final Expression
The orbital period $T$ is related to the orbital radius $r$ by the equation:

$$T^2 = k \cdot r^3$$

where $k$ is a proportionality constant. This shows that the square of the orbital period is directly proportional to the cube of the orbital radius, which is a direct statement of **Kepler's Third Law**.

### Kepler's Third Law and Its Implications

Kepler's Third Law, as derived above, states that for a circular orbit:

$$T^2 = \frac{4 \pi^2}{G \cdot M} \cdot r^3$$

This relationship is crucial for determining the period of orbiting objects when the mass of the central body is known. It also implies that the orbital period increases as the orbital radius increases, which is evident in the orbits of planets in our Solar System.

### Summary
- The **orbital period** $T$ is related to the **orbital radius** $r$ by the equation $T^2 = k \cdot r^3$, which is a form of Kepler's Third Law.
- The equation derived is $T = 2 \pi \sqrt{r^3 \cdot (G \cdot M)^{-1}}$, which allows calculation of the orbital period given the radius and the mass of the central body.

# Discussion on the Implications for Astronomy

### Introduction
Kepler's Third Law not only provides insight into the relationship between the orbital period and orbital radius but also has significant implications for the field of astronomy. This law plays a crucial role in calculating planetary masses, determining orbital distances, and understanding the dynamics of celestial bodies in our Solar System and beyond.

### Role of Kepler's Third Law in Calculating Planetary Masses and Distances

1. **Calculating Planetary Masses**  
   Kepler's Third Law can be used to estimate the mass of a central object (such as a star or planet) based on the orbital characteristics of an object orbiting it. Given the orbital period ($T$) and orbital radius ($r$), we can calculate the mass $M$ of the central object using the rearranged form of Kepler's Third Law:

   $$M = \frac{4 \pi^2 \cdot r^3}{G \cdot T^2}$$

   - **Example 1: Estimating the Mass of the Sun**  
     By observing the orbital period of a planet (e.g., Earth) and its distance from the Sun, we can estimate the Sun's mass. Using Earth’s orbital period ($T = 365.25$ days) and radius ($r = 1$ AU), we can substitute these values into the formula above to calculate the Sun's mass.

   - **Example 2: Estimating the Mass of Jupiter**  
     Similarly, the mass of Jupiter can be determined by observing the orbital period and radius of one of its moons or artificial satellites.

2. **Calculating Orbital Distances**  
   Kepler's Third Law also allows astronomers to determine the orbital distance $r$ of an object when the orbital period $T$ is known. For example, by knowing the orbital period of a satellite or moon and the mass of the central body (such as a planet), we can use the rearranged equation to calculate the orbital radius:

   $$r = \left(\frac{G \cdot M \cdot T^2}{4 \pi^2}\right)^{1/3}$$

   - **Example: Determining the Distance of the Moon from Earth**  
     By measuring the orbital period of the Moon around Earth and knowing the mass of Earth, we can calculate the Moon's orbital distance using the formula above.

3. **Extrapolating to Exoplanets**  
   Kepler's Third Law has been instrumental in the discovery of exoplanets, planets orbiting stars outside our Solar System. By observing the orbital periods and distances of exoplanets, we can estimate the masses of the stars they orbit. This allows for the classification of stars based on their masses and the characterization of planetary systems.

   - **Example: Kepler Mission**  
     The Kepler Space Telescope used this principle to detect thousands of exoplanets by measuring their orbital periods and distances from their parent stars, leading to the discovery of many potentially habitable planets.

---
### Importance of Kepler's Law for Understanding Celestial Mechanics

1. **Understanding Planetary Motions**  
   - Kepler’s Laws, especially the Third Law, form the foundation for understanding the motions of planets and other celestial bodies. The relationship between orbital period and radius provides a tool for calculating and predicting the behavior of celestial objects.  
   - This understanding is essential not only for studying planetary systems but also for understanding the dynamics of binary star systems, moons, and satellites orbiting planets.

2. **Orbit Determination for Space Missions**  
   - Kepler's Third Law is fundamental to space mission planning, including calculating the correct orbital paths for satellites, spacecraft, and probes. The equation provides the basis for calculating fuel requirements, mission durations, and rendezvous points for interplanetary missions.  
   - For example, calculating the orbit of a spacecraft to rendezvous with a planet or moon relies on the principles of orbital mechanics, of which Kepler's Laws are a key component.

3. **Orbital Resonances and Gravitational Interactions**  
   - Kepler's Third Law helps explain the phenomenon of **orbital resonances**, where two orbiting bodies exert regular, periodic gravitational influences on each other. These resonances are important in understanding the dynamics of moons and planets within a system.  
   - An example of this is the resonance between Jupiter’s moons Io, Europa, and Ganymede, which leads to periodic tidal heating of the moons.

4. **Gravitational Interactions Between Celestial Bodies**  
   - Understanding the relationship between orbital period and radius helps astronomers predict the gravitational interactions between objects. For example, the gravitational influence of one planet on another can alter their orbital characteristics over time.  
   - This principle is also crucial in understanding phenomena like planetary migrations, where a planet’s orbit may change due to the gravitational pull of nearby objects.

### Summary of Key Points  
- **Kepler's Third Law** plays a key role in calculating the **mass** of central objects and determining the **orbital distance** of orbiting objects.  
- The law is widely used to estimate the masses of stars, planets, and moons, as well as to calculate the orbital radii of objects in various celestial systems.  
- Kepler’s Laws are fundamental to our understanding of **planetary motions**, **space mission planning**, and the gravitational interactions between celestial bodies.  
- The law also provides insights into **orbital resonances** and the long-term dynamics of planetary and satellite systems.

---

### Analysis of Real-World Examples

### Introduction
Kepler's Third Law provides a fundamental tool for understanding the orbital characteristics of various celestial bodies. In this section, we will analyze the orbits of the Moon around Earth and the orbits of planets in the Solar System. We will also discuss how the relationship between orbital period and radius applies to different celestial bodies.

### Analysis of the Moon's Orbit Around Earth

1. **Orbital Parameters of the Moon**  
   The Moon's orbit around Earth is almost circular with the following parameters:
   - Orbital period ($T$): 27.3 days
   - Orbital radius ($r$): 384,400 km (distance from the center of the Earth to the center of the Moon)

2. **Application of Kepler's Third Law**  
   Using Kepler's Third Law, we can estimate the mass of Earth based on the Moon's orbit. The formula we use is:

   $$T^2 = \frac{4 \pi^2 r^3}{G M}$$

   Rearranging to solve for Earth's mass ($M$):

   $$M = \frac{4 \pi^2 r^3}{G T^2}$$

   Substituting the known values:
   - $r = 384,400$ km $= 3.844 \times 10^8$ m
   - $T = 27.3$ days $= 2.358 \times 10^6$ s
   - $G = 6.674 \times 10^{-11}$ m³/kg/s²

   We can compute Earth's mass using this equation.

3. **Implications**  
   - The Moon’s orbital period and radius allow astronomers to calculate the mass of the Earth with high precision.
   - This relationship is critical for understanding tidal interactions and other dynamical effects between the Earth and the Moon.

### Examination of the Orbits of Planets in the Solar System

1. **Orbital Parameters of Planets**  
   The orbits of planets in the Solar System are elliptical, but for simplicity, we can approximate them as circular for most practical purposes. Below are some key orbital parameters:

   - **Earth:**
     - Orbital period ($T$): 365.25 days
     - Orbital radius ($r$): 1 AU $= 1.496 \times 10^{11}$ m

   - **Mars:**
     - Orbital period ($T$): 687 days
     - Orbital radius ($r$): 1.524 AU $= 2.279 \times 10^{11}$ m

   - **Jupiter:**
     - Orbital period ($T$): 11.86 years
     - Orbital radius ($r$): 5.203 AU $= 7.783 \times 10^{11}$ m

2. **Kepler's Third Law for Planetary Orbits**  
   We can apply Kepler's Third Law to calculate the masses of the Sun using the orbital data of planets. For example, using Earth’s orbital data, we can estimate the mass of the Sun. The formula is:

   $$T^2 = \frac{4 \pi^2 r^3}{G M_{\text{sun}}}$$

   Rearranging to solve for $M_{\text{sun}}$:

   $$M_{\text{sun}} = \frac{4 \pi^2 r^3}{G T^2}$$

   Substituting known values for Earth:
   - $r = 1$ AU $= 1.496 \times 10^{11}$ m
   - $T = 365.25$ days $= 3.156 \times 10^7$ s

   The mass of the Sun can be calculated using this equation.

3. **Comparing Planetary Orbits**  
   - From Kepler’s Third Law, it is evident that planets with larger orbital radii have longer orbital periods. For example, **Mars** has a longer period than **Earth** because its orbital radius is greater.
   - **Jupiter**, being further from the Sun, has a significantly longer orbital period, which is nearly 12 years.

4. **Implications**  
   - By observing the orbital periods and radii of planets, we can calculate the mass of the Sun with remarkable precision.
   - The relationship also helps in understanding the differences in orbital dynamics, such as why outer planets take longer to orbit the Sun than inner planets.

### Application of Kepler's Third Law to Other Celestial Bodies

1. **Satellites and Moons**  
   - Kepler's Third Law is widely applied to artificial satellites orbiting Earth or other celestial bodies. For example, by knowing the orbital period and radius of a satellite, we can calculate the mass of the planet or moon it orbits.
   - **Example: International Space Station (ISS)**  
     The ISS orbits Earth with a period of about 90 minutes and an average orbital radius of approximately 400 km from the Earth's surface. By applying Kepler's Third Law, we can estimate the Earth's mass.

2. **Exoplanets and Exostellar Systems**  
   - Kepler’s Third Law has been crucial in the discovery and study of **exoplanets**—planets orbiting stars outside the Solar System. By measuring the orbital periods and distances of exoplanets, astronomers can calculate the masses of the parent stars.
   - **Example: Kepler-22b**  
     Using the orbital data of **Kepler-22b**, an exoplanet discovered by NASA’s Kepler mission, scientists can estimate the mass of the star it orbits and the planet’s orbital characteristics.

3. **Comets and Asteroids**  
   - The orbits of **comets** and **asteroids** can also be described using Kepler's Third Law. For example, the **orbital period** of Halley's Comet is about 76 years, and by applying the law, we can predict when it will return to the inner Solar System.
   - Similarly, asteroid belts and their orbital characteristics can be studied to understand their interaction with planets and the formation of the Solar System.

### Summary  
- **The Moon's orbit** around Earth allows us to calculate the mass of Earth and study tidal interactions.  
- **Planetary orbits** in the Solar System follow Kepler's Third Law, with planets farther from the Sun having longer orbital periods.  
- **Kepler's Third Law** applies to artificial satellites, exoplanets, moons, and other celestial bodies, providing a universal framework for understanding orbital dynamics.

---
# Extended Discussion on Elliptical Orbits

Kepler's Laws provide a fundamental framework for understanding planetary motion. While we have mainly discussed circular orbits, Kepler's First Law states that planets move in **elliptical orbits** with the Sun at one focus, not in perfect circles. Let’s explore how Kepler’s Third Law extends to elliptical orbits and the differences between circular and elliptical orbits.

## 1. Kepler’s Third Law for Elliptical Orbits

Kepler's Third Law can still be applied to elliptical orbits, but with a slight modification. For **elliptical orbits**, the law states:

$$T^2=\frac{4\pi^2a^3}{GM}$$

Where:
- $T$ is the orbital period,
- $a$ is the semi-major axis of the ellipse (the longest radius),
- $M$ is the mass of the central body,
- $G$ is the gravitational constant.

This equation tells us that the square of the orbital period is still proportional to the cube of the **semi-major axis** ($a$) of the elliptical orbit, rather than the orbital radius ($r$) as in the case of circular orbits.

## 2. Difference Between Circular and Elliptical Orbits

While both circular and elliptical orbits adhere to Kepler’s Third Law, there are key differences between the two:

- **Circular Orbits**:  
  In circular orbits, the orbital radius is constant and equal to the **semi-major axis**. The object’s distance from the central body does not change during the orbit. The orbital period is determined solely by the radius (or semi-major axis).
  
  For circular orbits, the relationship is straightforward:
  $$T^2\propto r^3$$

- **Elliptical Orbits**:  
  In elliptical orbits, the object moves closer and farther from the central body throughout its orbit. The distance varies, and thus the orbital speed also changes. The central body is located at one of the two foci of the ellipse, and the object’s distance from the focus is not constant.
  
  Despite the varying distance, the orbital period is still determined by the **semi-major axis** ($a$), not by the instantaneous distance of the orbiting body. This means that the orbital period remains the same even though the object’s speed changes throughout its elliptical orbit. The orbit is longer when the object is farther from the central body (at aphelion) and shorter when it’s closer (at perihelion).

## 3. Orbital Speed in Elliptical Orbits

Unlike in circular orbits where the object’s speed is constant, **orbital speed** in elliptical orbits varies depending on the object’s distance from the central body. The object moves fastest when it is closest to the focus (at perihelion) and slowest when it is farthest from the focus (at aphelion). This behavior is explained by **Kepler’s Second Law**, which states:

- **Kepler’s Second Law**:  
  A line joining a planet and the Sun sweeps out equal areas during equal intervals of time. This means that when a planet is closer to the Sun, it moves faster to sweep out the same area.

## 4. Visualizing Elliptical Orbits

To better understand elliptical orbits, let’s discuss the main characteristics:
- **Semi-major axis ($a$)**: The longest axis of the ellipse, running from one end (aphelion) to the other (perihelion).
- **Eccentricity ($e$)**: A measure of how “stretched out” the ellipse is. An eccentricity of 0 corresponds to a perfect circle, while an eccentricity close to 1 indicates a very elongated ellipse.
  
For an elliptical orbit, we can express the relationship between the perihelion ($r_p$) and aphelion ($r_a$) as:
$$r_p=a(1-e)$$
$$r_a=a(1+e)$$
where $e$ is the **eccentricity** of the ellipse.

## 5. Orbital Period and Elliptical Orbits

In elliptical orbits, even though the distance from the central body varies, the orbital period still depends only on the **semi-major axis** ($a$). This is the key takeaway from Kepler’s Third Law for elliptical orbits: the **semi-major axis** is the defining parameter for the orbital period, just as the orbital radius determines the period in a circular orbit.

## Conclusion

- **Circular Orbits**: The orbital period depends directly on the orbital radius, and the relationship is simple: $T^2\propto r^3$.
  
- **Elliptical Orbits**: The orbital period depends on the **semi-major axis** ($a$) of the ellipse, and the relationship remains: $T^2\propto a^3$. Despite the varying distance, the period is determined by the semi-major axis and remains the same for any elliptical orbit with the same semi-major axis.

## Differences Between Circular and Elliptical Orbits

| Characteristic        | Circular Orbits        | Elliptical Orbits     |
|-----------------------|------------------------|-----------------------|
| **Shape**             | Perfect circle         | Ellipse (stretched circle) |
| **Orbital Radius**    | Constant               | Varies (closest at perihelion, farthest at aphelion) |
| **Orbital Speed**     | Constant               | Varies (fastest at perihelion, slowest at aphelion) |
| **Orbit Period**      | Depends on radius      | Depends on semi-major axis (same as for circular orbits with same semi-major axis) |

Kepler's Third Law applies to both, but the shape and speed variation in elliptical orbits make them more complex, requiring a more thorough understanding of orbital mechanics. However, the fundamental relationship that $T^2\propto a^3$ holds true for both circular and elliptical orbits.

---
# Python/Plot
 ![alt text](image.png)
 ---
 ![alt text](image-1.png)
 ---
 ![alt text](image-2.png)

```python
 import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant in m^3 kg^-1 s^-2
M_sun = 1.989e30  # Mass of the Sun in kg
M_earth = 5.972e24  # Mass of Earth in kg

# Function to calculate orbital period
def orbital_period(radius, mass):
    return 2 * np.pi * np.sqrt(radius**3 / (G * mass))

# Plotting Circular Orbits
def plot_orbit(radius, mass, central_body):
    # Time for one full orbit
    T = orbital_period(radius, mass)
    
    # Number of points for plotting the orbit
    num_points = 1000
    theta = np.linspace(0, 2*np.pi, num_points)  # Angle for parametric plot
    
    # Parametric equations for circular orbit
    x = radius * np.cos(theta)  # x-coordinates
    y = radius * np.sin(theta)  # y-coordinates
    
    # Plot the orbit
    plt.figure(figsize=(8, 8))
    plt.plot(x, y, label=f'{central_body} Orbit (Radius = {radius/1e6:.2f} km)', color='b')
    plt.scatter(0, 0, color='r', label=f'{central_body} Position', s=200)  # Central body at origin
    plt.xlim(-radius*1.1, radius*1.1)
    plt.ylim(-radius*1.1, radius*1.1)
    plt.gca().set_aspect('equal', adjustable='box')
    plt.xlabel('x (m)', fontsize=12)
    plt.ylabel('y (m)', fontsize=12)
    plt.title(f'Orbital Path of a Body around {central_body}', fontsize=14)
    plt.legend()
    plt.grid(True)
    plt.show()

# Plotting the relationship between orbital period and radius (log-log scale)
def plot_period_radius():
    # Radii for various celestial bodies (in meters)
    radii = np.array([1.496e11, 7.783e11, 1.524e11, 5.203e11])  # 1 AU, Jupiter, Mars, Saturn in meters
    masses = np.array([M_sun, M_sun, M_sun, M_sun])  # Mass of Sun (for all planets)

    # Calculate orbital periods for the given radii
    periods = np.array([orbital_period(r, m) for r, m in zip(radii, masses)])

    # Log-Log plot of orbital period vs. orbital radius
    plt.figure(figsize=(8, 6))
    plt.loglog(radii, periods, 'bo-', label="Orbital Period vs. Radius", markersize=8)
    
    # Adding labels and title
    plt.xlabel('Orbital Radius (m)', fontsize=12)
    plt.ylabel('Orbital Period (s)', fontsize=12)
    plt.title('Log-Log Plot: Orbital Period vs. Orbital Radius', fontsize=14)
    plt.grid(True, which='both', linestyle='--', linewidth=0.5)
    plt.legend(fontsize=12)
    plt.tight_layout()
    plt.show()

# Example: Plot the orbit of Earth around the Sun
plot_orbit(1.496e11, M_sun, "Sun")

# Example: Plot the relationship between orbital period and radius (log-log)
plot_period_radius()
```
[Colab](https://colab.research.google.com/drive/122pc_OFXzgVKgNtfWSa5msNpUsuvOO8W?authuser=0)
