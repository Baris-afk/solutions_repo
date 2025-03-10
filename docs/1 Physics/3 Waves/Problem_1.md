# Problem 1
# **Wave Interference Patterns on a Water Surface**

## **1. Selecting a Regular Polygon**

### **Introduction**
In wave physics, interference occurs when two or more waves overlap, resulting in regions of constructive and destructive interference. To systematically analyze these patterns, we consider multiple point wave sources positioned at the vertices of a **regular polygon**. This setup allows us to explore how symmetric arrangements of sources influence the resulting wave field.

### **Mathematical Definition of a Regular Polygon**
A **regular polygon** with $N$ sides is a closed geometric figure where all sides are of equal length and all internal angles are equal. The vertices of such a polygon, when inscribed in a circle of radius $R$, can be determined using trigonometric functions.

For a polygon centered at the origin, the coordinates of the $i$-th vertex are given by:

$$
x_i = R \cos \left( \frac{2 \pi i}{N} \right), \quad y_i = R \sin \left( \frac{2 \pi i}{N} \right), \quad i = 0,1,2,\dots, N-1
$$

where:
- $R$ is the circumradius of the polygon,
- $N$ is the number of sides (hence, the number of sources),
- $i$ indexes the vertices counterclockwise starting from an initial reference point.

### **Wave Emission from Polygonal Vertices**
Each vertex acts as a coherent wave source emitting circular waves. The displacement of the water surface at any point $(x, y)$ and time $t$ due to a single wave source located at $(x_0, y_0)$ follows the equation:

$$
\eta_i(x, y, t) = \frac{A}{r_i} \cos \left( k r_i - \omega t + \phi_i \right)
$$

where:
- $\eta_i(x, y, t)$ is the surface displacement due to source $i$,
- $A$ is the wave amplitude,
- $r_i = \sqrt{(x - x_i)^2 + (y - y_i)^2}$ is the radial distance from the $i$-th source to the observation point,
- $k = \frac{2\pi}{\lambda}$ is the wave number,
- $\omega = 2\pi f$ is the angular frequency,
- $\phi_i$ is the initial phase of the $i$-th wave.

### **Wave Superposition and Interference Pattern Formation**
Using the principle of superposition, the total displacement at any given point is given by:

$$
\eta_{\text{sum}}(x, y, t) = \sum_{i=1}^{N} \eta_i(x, y, t)
$$


Regions where waves add constructively (i.e., maxima align) will experience **amplification**, whereas destructive interference (opposite phase alignment) results in **cancellation**.

### **Choosing the Regular Polygon**
The choice of $N$ influences the symmetry of the interference pattern. Common selections include:
- **Equilateral Triangle ($N=3$)**: Yields a threefold symmetric interference pattern.
- **Square ($N=4$)**: Produces a fourfold symmetric pattern with central and diagonal wave reinforcements.
- **Pentagon ($N=5$)**: Generates more complex wave interactions with fivefold rotational symmetry.
- **Hexagon ($N=6$)**: Approximates circular symmetry while retaining noticeable interference fringes.

### **Visual Representation**
To understand how wave sources interact, we visualize the resulting interference pattern using **Python simulations**. The next steps will involve:
1. Implementing the above equations in Python.
2. Computing interference patterns numerically.
3. Generating graphical representations of the wave field.

---

In the next section, we will define the mathematical formulation of the **wave equations** for each source and explore how the **superposition principle** governs interference phenomena.