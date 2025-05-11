# Problem 2


# Estimating $\pi$ Using Monte Carlo Simulation


## 1. Theoretical Foundation

Monte Carlo methods use randomness to approximate mathematical quantities. In this case, we estimate the value of $\pi$ by simulating the ratio of points that fall inside a unit circle to the total number of points within a bounding square.

### Concept:

- Consider a **unit circle** (radius = 1) centered at the origin.
- Enclose the circle in a **square** that spans from $-1$ to $1$ on both the $x$- and $y$-axes.
- Randomly generate points $(x, y)$ uniformly within the square.
- A point lies **inside the circle** if it satisfies:

$$x^2 + y^2 \leq 1$$

- The area of the square is:

$$A_{\text{square}} = (2 \times 1)^2 = 4$$

- The area of the circle is:

$$A_{\text{circle}} = \pi \cdot r^2 = \pi$$

- The **ratio** of the circle’s area to the square’s area is:

$$\frac{A_{\text{circle}}}{A_{\text{square}}} = \frac{\pi}{4}$$

- Hence, if we throw $N$ random points, and $M$ of them fall inside the circle, then:

$$\frac{M}{N} \approx \frac{\pi}{4} \Rightarrow \pi \approx 4 \cdot \frac{M}{N}$$

---

## 2. Simulation

We now implement a simple Monte Carlo simulation in Python to estimate $\pi$ using the above principle.

### Steps:

- Generate $N$ random points $(x, y)$ where $x, y \in [-1, 1]$
- Count the number of points $M$ for which $x^2 + y^2 \leq 1$
- Estimate $\pi$ using the formula:

$$\pi \approx 4 \cdot \frac{M}{N}$$

---

![alt text](monte_carlo_pi_estimation_final.gif)

---

![alt text](image-3.png)

---


## 3. Visualization


![alt text](image-4.png)

---

Visualizing the simulation helps to intuitively understand how Monte Carlo methods work in approximating π.

### Steps:

- Each generated point $(x, y)$ lies inside a square defined by $[-1, 1] \times [-1, 1]$.
  
- A point lies **inside the circle** if:
  
$$x^2 + y^2 \leq 1$$

- In the plot:
  - Use one color (e.g., **blue**) for points **inside** the circle.
    
  - Use another color (e.g., **red**) for points **outside** the circle.
    
  - Overlay a dashed boundary representing the **unit circle** for reference.

### Benefits:

- This scatter plot visually confirms that the density of points inside the circle reflects the area ratio $\frac{\pi}{4}$.
- As more points are added, the filled area more closely approximates the circle.

---

## 4. Analysis

To understand the effectiveness of the Monte Carlo method, we analyze how the π estimate changes as the number of points increases.

### Experimental Setup:

- Run the simulation multiple times with increasing values of $N$ (e.g., $10^2$, $10^3$, $10^4$, $10^5$, $10^6$).
  
- For each $N$:
  
  - Estimate π using:

$$\pi \approx 4 \cdot \frac{M}{N}$$

 where:

- $M$ is the number of points satisfying $x^2 + y^2 \leq 1$
  
- $N$ is the total number of points

- Store each π estimate and compare it to the actual value of $\pi \approx 3.1415926535$.

### Convergence:

- **Plot a graph** of estimated π vs. number of points on a log scale.
  
- Observe how the error decreases as $N$ increases.

$$\text{Error} = \left| \pi_{\text{estimate}} - \pi \right|$$

- The convergence is probabilistic:
  
- The **law of large numbers** ensures that as $N \to \infty$, the estimate converges to the true value of π.
    
- The **standard deviation** of the estimate decreases proportionally to $\frac{1}{\sqrt{N}}$.

### Computational Considerations:

- Monte Carlo methods are simple to implement but can require a large number of samples for high precision.
  
- Execution time grows linearly with $N$, so optimization or parallelization may be needed for very large simulations.

---

> 📈 Monte Carlo π estimation beautifully illustrates the trade-off between **accuracy**, **sample size**, and **computational cost**.

---


# Part 2: Estimating $\pi$ Using Buffon’s Needle


## 1. Theoretical Foundation

The **Buffon’s Needle** experiment is one of the oldest Monte Carlo methods and a classical problem in geometric probability. It provides a probabilistic way to estimate the value of $\pi$.

### Problem Setup:

- Imagine a floor marked with **parallel lines** that are equally spaced by a distance $d$.
- A needle of length $\ell$ $(\ell \leq d)$ is randomly dropped onto the floor.
- The probability that the needle **crosses one of the lines** depends on both its length and the spacing between lines.

### Conditions:

- The position of the needle's **center** is uniformly distributed between the lines.
- The needle’s **angle** with respect to the parallel lines is uniformly distributed between $0$ and $\frac{\pi}{2}$.

### Derivation:

Let:

- $\ell$ = length of the needle
  
- $d$ = distance between the lines
  
- $T$ = number of needle throws
  
- $C$ = number of times the needle crosses a line

Then, the expected **probability of a crossing** is:

$$
P = \frac{2\ell}{d\pi}
$$

Rearranging this formula to solve for $\pi$ gives us an estimate:

$$
\pi \approx \frac{2 \cdot \ell \cdot T}{d \cdot C}
$$

---

## 2. Simulation

![alt text](buffon_creative_simulation.gif)

---


We simulate the dropping of needles on a floor to estimate $\pi$ using the above formula.

### Simulation Steps:

- Define values for:
  
- Needle length $\ell$
    
- Line spacing $d$ $(\ell \leq d)$
  
- Number of throws $T$

- For each throw:
  
- Randomly generate:
  
- A **distance** $y$ from the needle’s center to the nearest line (uniformly in $[0, d/2]$)
  
- An **angle** $\theta$ between the needle and the lines (uniformly in $[0, \pi/2]$)

  - The needle **crosses a line** if:

$$
y \leq \frac{\ell}{2} \cdot \sin(\theta)
$$

- Count the number of **crossings** $C$.
  
- Estimate $\pi$ as:

$$
\pi \approx \frac{2 \cdot \ell \cdot T}{d \cdot C}
$$

### Notes:

- This method relies on geometric probability and converges slowly compared to circle-based Monte Carlo simulations.
- The **accuracy** improves with a larger number of needle throws $T$.
- Ensure $\ell \leq d$ to satisfy classical Buffon’s Needle constraints.

---

> 🧪 Buffon’s Needle is a beautiful example of how geometry and probability can be combined to approximate mathematical constants like $\pi$.

---

## 3. Visualization

![alt text](image-5.png)

---


To visually demonstrate the geometric basis of Buffon’s Needle experiment, we plot the needle positions over a floor of equally spaced parallel lines.

### Visual Elements:

- The floor consists of **horizontal parallel lines** spaced at distance $d$ apart.
  
- Each **needle** of length $\ell$ is randomly dropped:
  
- A center position $(x, y)$ is chosen uniformly at random.
- An angle $\theta$ is selected uniformly from $[0, \pi]$.
  
- Each needle is represented as a line segment.
  
- If the needle **crosses a line**, it is shown in **red**.
  
- If the needle does **not cross a line**, it is shown in **green or blue**.

### Mathematical Condition for a Crossing:

Let:

- $y$ = vertical distance from the center of the needle to the nearest line.
  
- $\theta$ = angle the needle makes with the horizontal axis.

Then the needle crosses a line **if and only if**:

$$
y \leq \frac{\ell}{2} \cdot \sin(\theta)
$$

This condition is derived from projecting half the length of the needle vertically onto the axis perpendicular to the lines.

---

## 4. Analysis

To analyze the performance and convergence of Buffon's Needle method, we vary the number of needle drops $N$ and observe how the estimated value of $\pi$ evolves.

### Experimental Procedure:

- Fix:
- Needle length $\ell$ (e.g., 1)
    
- Line spacing $d$ (e.g., 2, such that $\ell \leq d$)
    
- For increasing values of $N$ (e.g., $10^2$, $10^3$, $10^4$, ..., $10^6$):
  
- Perform $N$ random needle drops.
  

- Count the number of **crossings** $C$.
  
  - Estimate π using:

$$
\pi \approx \frac{2 \cdot \ell \cdot N}{d \cdot C}
$$

- Record and plot:
  
- Estimated values of π.
    
- Absolute errors: $|\pi_{\text{estimate}} - \pi_{\text{actual}}|$.

### Convergence Behavior:

- The error generally decreases as $N$ increases, following a convergence trend similar to:

$$
\text{Error} \propto \frac{1}{\sqrt{N}}
$$

- However, this method has **slower convergence** and **higher variance** compared to the **circle-based Monte Carlo method**.

### Comparison with Circle-Based Monte Carlo:

| Method            | Strengths                          | Weaknesses                       |
|-------------------|------------------------------------|----------------------------------|
| Circle Method     | Faster convergence, simpler math   | Requires point-in-circle check   |
| Buffon’s Needle   | Geometric elegance, historical     | Slower convergence, angle math   |

---

> 🎯 Visual simulations and convergence plots of Buffon’s Needle highlight the probabilistic elegance of this method, while also illustrating its limitations in terms of efficiency compared to other Monte Carlo techniques.
---

## Python Codes

```python
import numpy as np
import matplotlib.pyplot as plt

def estimate_pi(num_points=10000, show_plot=True, save_plot=False, filename="pi_estimate_plot.png"):
    """
    Estimate the value of π using Monte Carlo simulation.
    
    Parameters:
        num_points (int): Number of random points to generate.
        show_plot (bool): Whether to display a scatter plot.
        save_plot (bool): Whether to save the plot as an image file.
        filename (str): Filename for saving the plot.
    
    Returns:
        float: Estimated value of π.
    """
    # Generate random (x, y) coordinates in the square [-1, 1] x [-1, 1]
    x = np.random.uniform(-1, 1, num_points)
    y = np.random.uniform(-1, 1, num_points)

    # Boolean mask for points inside the unit circle
    inside_circle = x**2 + y**2 <= 1
    count_inside = np.sum(inside_circle)

    # Monte Carlo estimation of π
    pi_estimate = 4 * count_inside / num_points

    # Plotting
    if show_plot:
        plt.figure(figsize=(6, 6))
        plt.scatter(x[inside_circle], y[inside_circle], color='dodgerblue', s=1, label='Inside Circle')
        plt.scatter(x[~inside_circle], y[~inside_circle], color='tomato', s=1, label='Outside Circle')

        # Draw a unit circle for reference
        circle = plt.Circle((0, 0), 1, color='black', fill=False, linestyle='--', linewidth=2)
        plt.gca().add_patch(circle)
        plt.gca().set_aspect('equal')
        plt.title(f'π Estimation with {num_points:,} Points\nEstimated π ≈ {pi_estimate:.6f}')
        plt.xlabel('x')
        plt.ylabel('y')
        plt.grid(True)
        plt.legend(loc='upper right')

        if save_plot:
            plt.savefig(filename, dpi=300)
        plt.show()

    return pi_estimate

# Example run
estimate_pi(num_points=100000)
```
---

```python
import numpy as np
import matplotlib.pyplot as plt

def monte_carlo_pi_convergence(sample_sizes=None):
    """
    Estimates π using Monte Carlo method for increasing sample sizes and
    plots the convergence of π estimates and the corresponding absolute error.

    Parameters:
        sample_sizes (list): A list of integers specifying number of points for simulation.
    """
    if sample_sizes is None:
        sample_sizes = [10**2, 10**3, 10**4, 10**5, 10**6]

    pi_actual = np.pi
    pi_estimates = []
    errors = []

    # Run simulations for each sample size
    for N in sample_sizes:
        x = np.random.uniform(-1, 1, N)
        y = np.random.uniform(-1, 1, N)
        inside_circle = x**2 + y**2 <= 1
        estimate = 4 * np.sum(inside_circle) / N
        pi_estimates.append(estimate)
        errors.append(abs(estimate - pi_actual))

    # Set up the figure
    plt.figure(figsize=(14, 6))

    # Plot 1: Estimated π vs Number of Points
    plt.subplot(1, 2, 1)
    plt.plot(sample_sizes, pi_estimates, 'o--', color='dodgerblue', label='Estimated π')
    plt.axhline(pi_actual, color='green', linestyle='-', linewidth=1.5, label='Actual π')
    plt.xscale('log')
    plt.xlabel('Number of Points (log scale)', fontsize=12)
    plt.ylabel('Estimated π', fontsize=12)
    plt.title('Monte Carlo Estimation of π', fontsize=14)
    plt.legend()
    plt.grid(True, linestyle='--', alpha=0.6)

    # Plot 2: Absolute Error vs Number of Points
    plt.subplot(1, 2, 2)
    plt.plot(sample_sizes, errors, 'o--', color='crimson')
    plt.xscale('log')
    plt.yscale('log')
    plt.xlabel('Number of Points (log scale)', fontsize=12)
    plt.ylabel('Absolute Error (log scale)', fontsize=12)
    plt.title('Convergence of Estimation Error', fontsize=14)
    plt.grid(True, linestyle='--', alpha=0.6)

    plt.tight_layout()
    plt.show()

# Run the function
monte_carlo_pi_convergence()
```
---


```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

# Parameters
needle_length = 1.0
line_spacing = 2.0
num_needles = 100
line_count = 5

# Generate random positions and angles
centers_x = np.random.uniform(0, line_spacing * (line_count - 1), num_needles)
centers_y = np.random.uniform(0, line_spacing * line_count, num_needles)
angles = np.random.uniform(0, np.pi, num_needles)

# Set up the figure
fig, ax = plt.subplots(figsize=(10, 6))
ax.set_xlim(0, line_spacing * (line_count - 1))
ax.set_ylim(0, line_spacing * line_count)
ax.set_title("🎯 Buffon's Needle Simulation", fontsize=16, weight='bold')
ax.set_xlabel("x-position")
ax.set_ylabel("y-position")

# Draw floor lines
for i in range(line_count + 1):
    ax.axhline(y=i * line_spacing, color='gray', linestyle='--', linewidth=1)

needle_lines = []

def init():
    return []

def update(frame):
    if frame < len(needle_lines):
        needle_lines[frame].remove()

    x0 = centers_x[frame]
    y0 = centers_y[frame]
    theta = angles[frame]

    dx = (needle_length / 2) * np.cos(theta)
    dy = (needle_length / 2) * np.sin(theta)

    x_start = x0 - dx
    y_start = y0 - dy
    x_end = x0 + dx
    y_end = y0 + dy

    crosses = int(np.floor(y_start / line_spacing) != np.floor(y_end / line_spacing))
    color = '#D7263D' if crosses else '#1B998B'

    line, = ax.plot([x_start, x_end], [y_start, y_end], color=color, linewidth=2, alpha=0.9)
    if crosses:
        ax.plot([x0], [y0], marker='o', color=color, markersize=5)
    needle_lines.append(line)
    return [line]

ani = animation.FuncAnimation(fig, update, frames=num_needles, init_func=init, blit=True, interval=120, repeat=False)

# Save and display the GIF
ani.save("buffon_creative_simulation.gif", writer='pillow', fps=10)
from IPython.display import Image
Image(filename="buffon_creative_simulation.gif")
```
---


```python
import numpy as np
import matplotlib.pyplot as plt

# Actual value of π
pi_actual = np.pi

# Simulation parameters
needle_length = 1.0
line_spacing = 2.0
sample_sizes = [10**2, 10**3, 10**4, 10**5, 10**6]

# Storage for estimates and errors
buffon_estimates = []
buffon_errors = []

circle_estimates = []
circle_errors = []

# Run both simulations for each sample size
for N in sample_sizes:
    # --- Buffon's Needle ---
    y = np.random.uniform(0, line_spacing / 2, N)
    theta = np.random.uniform(0, np.pi / 2, N)
    crosses = y <= (needle_length / 2) * np.sin(theta)
    crossings = np.sum(crosses)

    if crossings == 0:
        buffon_estimate = np.nan  # avoid division by zero
    else:
        buffon_estimate = (2 * needle_length * N) / (line_spacing * crossings)

    buffon_estimates.append(buffon_estimate)
    buffon_errors.append(abs(buffon_estimate - pi_actual) if crossings > 0 else np.nan)

    # --- Monte Carlo Circle ---
    x = np.random.uniform(-1, 1, N)
    y = np.random.uniform(-1, 1, N)
    inside = x**2 + y**2 <= 1
    circle_estimate = 4 * np.sum(inside) / N
    circle_estimates.append(circle_estimate)
    circle_errors.append(abs(circle_estimate - pi_actual))

# --- Plotting ---

fig, axs = plt.subplots(2, 2, figsize=(14, 10))

# 1. π Estimates
axs[0, 0].plot(sample_sizes, buffon_estimates, 'o--', label="Buffon's Needle", color='red')
axs[0, 0].plot(sample_sizes, circle_estimates, 's--', label='Monte Carlo (Circle)', color='blue')
axs[0, 0].axhline(pi_actual, color='green', linestyle='-', linewidth=1.5, label='Actual π')
axs[0, 0].set_xscale('log')
axs[0, 0].set_title('Estimated π vs. Sample Size')
axs[0, 0].set_xlabel('Number of Points (log scale)')
axs[0, 0].set_ylabel('Estimated π')
axs[0, 0].legend()
axs[0, 0].grid(True)

# 2. Absolute Errors
axs[0, 1].plot(sample_sizes, buffon_errors, 'o--', label="Buffon's Needle", color='red')
axs[0, 1].plot(sample_sizes, circle_errors, 's--', label='Monte Carlo (Circle)', color='blue')
axs[0, 1].set_xscale('log')
axs[0, 1].set_yscale('log')
axs[0, 1].set_title('Absolute Error vs. Sample Size')
axs[0, 1].set_xlabel('Number of Points (log scale)')
axs[0, 1].set_ylabel('Absolute Error (log-log scale)')
axs[0, 1].legend()
axs[0, 1].grid(True)

# 3. Buffon's Needle Estimates
axs[1, 0].plot(sample_sizes, buffon_estimates, 'o-', color='red')
axs[1, 0].axhline(pi_actual, color='green', linestyle='--')
axs[1, 0].set_xscale('log')
axs[1, 0].set_title("Buffon's Needle π Estimate")
axs[1, 0].set_xlabel('Sample Size (log scale)')
axs[1, 0].set_ylabel('π Estimate')
axs[1, 0].grid(True)

# 4. Circle Method Estimates
axs[1, 1].plot(sample_sizes, circle_estimates, 'o-', color='blue')
axs[1, 1].axhline(pi_actual, color='green', linestyle='--')
axs[1, 1].set_xscale('log')
axs[1, 1].set_title("Monte Carlo Circle π Estimate")
axs[1, 1].set_xlabel('Sample Size (log scale)')
axs[1, 1].set_ylabel('π Estimate')
axs[1, 1].grid(True)

plt.tight_layout()
plt.show()
```
---


```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

# Settings
frame_points = 500
total_frames = 100
total_points = frame_points * total_frames

np.random.seed(42)
x = np.random.uniform(-1, 1, total_points)
y = np.random.uniform(-1, 1, total_points)

# Set up the plot
fig, ax = plt.subplots(figsize=(6, 6))
ax.set_xlim(-1, 1)
ax.set_ylim(-1.2, 1.2)
ax.set_aspect('equal')
ax.set_title("Monte Carlo Simulation: Estimating π", fontsize=14, weight='bold')
ax.set_xlabel("x-axis")
ax.set_ylabel("y-axis")

# Draw circle outline
circle = plt.Circle((0, 0), 1, color='black', fill=False, linestyle='--', linewidth=2)
ax.add_patch(circle)

# Prepare point plots
inside = ax.plot([], [], 'o', color='#2a9d8f', markersize=2, label='Inside Circle')[0]
outside = ax.plot([], [], 'o', color='#e76f51', markersize=2, label='Outside Circle')[0]

# Create text: top left (small), middle (larger)
text_total = ax.text(-0.95, 1.13, "", fontsize=9, bbox=dict(facecolor='white', alpha=0.7, edgecolor='gray'))
text_pi = ax.text(-0.95, 1.05, "", fontsize=11, bbox=dict(facecolor='white', alpha=0.7, edgecolor='gray'))

def init():
    inside.set_data([], [])
    outside.set_data([], [])
    text_total.set_text("")
    text_pi.set_text("")
    return inside, outside, text_total, text_pi

def update(frame):
    end = (frame + 1) * frame_points
    x_f = x[:end]
    y_f = y[:end]
    inside_mask = x_f**2 + y_f**2 <= 1

    inside.set_data(x_f[inside_mask], y_f[inside_mask])
    outside.set_data(x_f[~inside_mask], y_f[~inside_mask])
    
    pi_est = 4 * np.sum(inside_mask) / len(x_f)
    text_total.set_text(f"Total Points: {len(x_f)}")
    text_pi.set_text(f"Estimated π ≈ {pi_est:.6f}")
    
    return inside, outside, text_total, text_pi

ani = animation.FuncAnimation(fig, update, frames=total_frames, init_func=init, blit=True, interval=100, repeat=False)

# Save GIF
ani.save("monte_carlo_pi_estimation_final.gif", writer='pillow', fps=10)

# Show in Colab
from IPython.display import Image
Image(filename="monte_carlo_pi_estimation_final.gif")
```






