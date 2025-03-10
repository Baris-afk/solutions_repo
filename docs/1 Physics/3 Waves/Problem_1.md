# Problem 1
# **Wave Interference Patterns on a Water Surface**

## **1. Selecting a Regular Polygon**

### **Introduction**
In wave physics, interference occurs when two or more waves overlap, resulting in regions of constructive and destructive interference. To systematically analyze these patterns, we consider multiple point wave sources positioned at the vertices of a **regular polygon**. This setup allows us to explore how symmetric arrangements of sources influence the resulting wave field.

### **Mathematical Definition of a Regular Polygon**
A **regular polygon** with $N$ sides is a closed geometric figure where all sides are of equal length and all internal angles are equal. The vertices of such a polygon, when inscribed in a circle of radius $R$, can be determined using trigonometric functions.

For a polygon centered at the origin, the coordinates of the $i$-th vertex are given by:

$$x_i=R\cos\left(\frac{2\pi i}{N}\right),\quad y_i=R\sin\left(\frac{2\pi i}{N}\right),\quad i=0,1,2,\dots,N-1$$

where:
- $R$ is the circumradius of the polygon,
- $N$ is the number of sides (hence, the number of sources),
- $i$ indexes the vertices counterclockwise starting from an initial reference point.

### **Choosing the Regular Polygon**
The choice of $N$ influences the symmetry of the interference pattern. Common selections include:
- **Equilateral Triangle ($N=3$)**: Yields a threefold symmetric interference pattern.
- **Square ($N=4$)**: Produces a fourfold symmetric pattern with central and diagonal wave reinforcements.
- **Pentagon ($N=5$)**: Generates more complex wave interactions with fivefold rotational symmetry.
- **Hexagon ($N=6$)**: Approximates circular symmetry while retaining noticeable interference fringes.

---

## **2. Positioning the Sources**

### **Determining the Coordinates of the Polygonal Vertices**
To systematically analyze interference, we must precisely position the wave sources at the vertices of a chosen regular polygon. Given a polygon inscribed within a circle of radius $R$, the coordinates of its vertices are:

$$x_i=R\cos\left(\frac{2\pi i}{N}\right),\quad y_i=R\sin\left(\frac{2\pi i}{N}\right),\quad i=0,1,2,\dots,N-1$$

### **Assigning Each Vertex as a Wave Source**
Each vertex serves as a point source emitting circular waves with identical amplitude and frequency. The total wave field results from the superposition of these waves.

Each wave propagates outward from its source with a displacement function:

$$\eta_i(x,y,t)=\frac{A}{r_i}\cos\left(kr_i-\omega t+\phi_i\right)$$

where:
- $r_i=\sqrt{(x-x_i)^2+(y-y_i)^2}$ is the radial distance to the observation point.

---

## **3. Defining the Wave Equations**

### **Mathematical Representation of Wave Motion**
Each wave emitted from a point source follows the equation:

$$\eta_i(x,y,t)=\frac{A}{r_i}\cos\left(kr_i-\omega t+\phi_i\right)$$

where:
- $A$ is the amplitude,
- $k=\frac{2\pi}{\lambda}$ is the wave number,
- $\omega=2\pi f$ is the angular frequency,
- $\phi_i$ is the phase,
- $r_i$ is the radial distance from the $i$-th source.

### **Uniformity Assumptions**
To maintain coherence in interference analysis, we assume:
- All waves have **the same amplitude**, i.e., $A$ is constant.
- All waves have **the same wavelength** $\lambda$ and frequency $f$.
- Initial phase differences between sources remain fixed.

---

## **4. Applying the Superposition Principle**

### **Summation of Wave Displacements**
According to the principle of superposition, the resultant displacement at any point on the water surface is the sum of individual wave contributions:

$$\eta_{\text{sum}}(x,y,t)=\sum_{i=1}^{N}\eta_i(x,y,t)$$

This summation captures constructive and destructive interference effects.

### **Constructive and Destructive Interference Conditions**
- **Constructive interference:** Occurs when phase differences satisfy:
  $$kr_i-\omega t+\phi_i=2m\pi,\quad m\in\mathbb{Z}$$
- **Destructive interference:** Occurs when phase differences satisfy:
  $$kr_i-\omega t+\phi_i=(2m+1)\pi,\quad m\in\mathbb{Z}$$

---

## **5. Analyzing the Interference Patterns**

### **Identifying Interference Zones**
By computing $\eta_{\text{sum}}(x,y,t)$, we can classify different regions:
- **High amplitude zones:** Result from constructive interference.
- **Low amplitude zones:** Result from destructive interference.

### **Temporal Evolution of the Pattern**
As time progresses, the interference pattern evolves dynamically, influenced by wave frequency and phase differences.

---

## **6. Visualization and Simulation**

### **Graphical Representations**
Using numerical simulations, we generate:
- **Static interference maps** for different polygons.
- **Time-evolving wave fields** to observe changing interference dynamics.

### **Python Implementation**
A Python script implementing the above equations will:
1. Define wave parameters.
2. Compute the interference pattern on a 2D grid.
3. Visualize results using heatmaps and contour plots.

The next step is to implement and analyze these interference patterns computationally.

# Python/Models
![alt text](image.png)

![alt text](image-1.png)

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Define parameters
wavelength = 1.0  # Wavelength of the waves
k = 2 * np.pi / wavelength  # Wave number
d = 5.0  # Distance between sources
amplitude = 1.0  # Amplitude of waves

# Create a grid
x = np.linspace(-10, 10, 400)
y = np.linspace(-10, 10, 400)
X, Y = np.meshgrid(x, y)

# Calculate distances from two point sources
r1 = np.sqrt((X - d/2)**2 + Y**2)
r2 = np.sqrt((X + d/2)**2 + Y**2)

# Calculate wave interference pattern
wave1 = amplitude * np.cos(k * r1)
wave2 = amplitude * np.cos(k * r2)
interference = wave1 + wave2

# 2D Heatmap
plt.figure(figsize=(8, 6))
plt.imshow(interference, extent=[-10, 10, -10, 10], origin='lower', cmap='jet', alpha=0.8)
plt.colorbar(label="Wave Displacement")
plt.title("2D Interference Pattern")
plt.xlabel("X Position")
plt.ylabel("Y Position")
plt.show()

# 3D Surface Plot
fig = plt.figure(figsize=(10, 7))
ax = fig.add_subplot(111, projection='3d')
ax.plot_surface(X, Y, interference, cmap='jet', edgecolor='none', alpha=0.8)
ax.set_title("3D Surface Plot of Interference Pattern")
ax.set_xlabel("X Position")
ax.set_ylabel("Y Position")
ax.set_zlabel("Wave Displacement")
plt.show()
```

[Colab](https://colab.research.google.com/drive/1zq2rWSl0EAovztR3_Qr1dIoJTZ0GwtFA?authuser=0)
