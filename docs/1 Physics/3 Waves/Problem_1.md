# Problem 1
---
## **Theoretical Foundation: Governing Equations of Projectile Motion**

### **1. Introduction**
Projectile motion describes the motion of an object under the influence of gravity, assuming no air resistance. The motion occurs in two dimensions: horizontal ($x$-axis) and vertical ($y$-axis). We derive the governing equations starting from Newton’s laws of motion.

### **2. Equations of Motion**
Newton’s second law states:

$$F=ma$$

For projectile motion, the only force acting on the object (neglecting air resistance) is gravity:

$$F_y=-mg,\quad F_x=0$$

Thus, the acceleration components are:

$$a_x=0,\quad a_y=-g$$

where $g$ is the acceleration due to gravity.

Using kinematic equations:

#### **2.1 Horizontal Motion**
Since there is no horizontal acceleration,

$$v_x=v_0\cos(\theta)$$

$$x=v_0\cos(\theta)t$$

#### **2.2 Vertical Motion**
Using the kinematic equations for constant acceleration,

$$v_y=v_0\sin(\theta)-gt$$

$$y=v_0\sin(\theta)t-\frac{1}{2}gt^2$$

### **3. Time of Flight**
The time of flight is found by solving for when the projectile returns to $y=0$:

$$0=v_0\sin(\theta)t-\frac{1}{2}gt^2$$

Factoring out $t$:

$$t(v_0\sin(\theta)-\frac{1}{2}gt)=0$$

Ignoring the trivial solution $t=0$, we solve for $t$:

$$t=\frac{2v_0\sin(\theta)}{g}$$

### **4. Range of the Projectile**
The horizontal range is given by:

$$R=v_x\times t_{flight}$$

Substituting $v_x=v_0\cos(\theta)$ and $t_{flight}$:

$$R=v_0\cos(\theta)\times\frac{2v_0\sin(\theta)}{g}$$

Using the identity $2\sin(\theta)\cos(\theta)=\sin(2\theta)$,

$$R=\frac{v_0^2\sin(2\theta)}{g}$$

### **5. Maximum Height**
At maximum height, $v_y=0$:

$$0=v_0\sin(\theta)-gt_{max}$$

Solving for $t_{max}$:

$$t_{max}=\frac{v_0\sin(\theta)}{g}$$

Using the vertical displacement equation:

$$h_{max}=v_0\sin(\theta)t_{max}-\frac{1}{2}gt_{max}^2$$

Substituting $t_{max}$:

$$h_{max}=\frac{v_0^2\sin^2(\theta)}{2g}$$

### **6. Influence of Initial Conditions**
- **Initial Velocity $v_0$**: Higher velocity increases both range and height.
- **Launch Angle $\theta$**: The range is maximized at $\theta=45^\circ$.
- **Gravity $g$**: Higher gravity decreases range and height.

### **7. Conclusion**
These equations provide a fundamental description of projectile motion. In further analysis, we will explore numerical simulations and practical applications, including air resistance and varying terrains.

---

# Python/Plot

![alt text](image.png)

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

def projectile_motion_no_drag(v0, theta, g=9.81):
    """Computes the range of projectile motion without air resistance."""
    theta_rad = np.radians(theta)
    range_ = (v0**2 * np.sin(2 * theta_rad)) / g
    return range_

def projectile_motion_with_drag(v0, theta, mass, Cd, A, rho=1.225, g=9.81):
    """Solves the projectile motion equations numerically with air resistance."""
    theta_rad = np.radians(theta)
    vx0 = v0 * np.cos(theta_rad)
    vy0 = v0 * np.sin(theta_rad)
    
    def equations(t, y):
        vx, vy, x, y_pos = y
        v = np.sqrt(vx**2 + vy**2)
        drag_force = 0.5 * rho * Cd * A * v**2
        ax = -drag_force * vx / (mass * v)
        ay = -g - (drag_force * vy / (mass * v))
        return [ax, ay, vx, vy]
    
    sol = solve_ivp(equations, [0, 10], [vx0, vy0, 0, 0], max_step=0.01, events=lambda t, y: y[3])
    return sol.y[2][-1]  # Return final x-position (range)

def plot_range_vs_angle(v0_values, drag=False):
    """Plots range vs. angle for different initial speeds."""
    angles = np.linspace(0, 90, 50)
    plt.figure(figsize=(8, 5))
    
    for v0 in v0_values:
        ranges = []
        for theta in angles:
            if drag:
                range_ = projectile_motion_with_drag(v0, theta, mass=0.145, Cd=0.47, A=0.0014)
            else:
                range_ = projectile_motion_no_drag(v0, theta)
            ranges.append(range_)
        plt.plot(angles, ranges, label=f'v0 = {v0} m/s')
    
    plt.xlabel('Angle of Projection (degrees)')
    plt.ylabel('Range (m)')
    plt.title('Range vs. Angle of Projection')
    plt.legend()
    plt.grid()
    plt.show()

# Example usage:
plot_range_vs_angle([10, 20, 30], drag=False)
```

link: [colab](https://colab.research.google.com/drive/1K0bk1_H0wlBIUVxtvneTUBV-p0d_W_Ti?usp=sharing)
 
