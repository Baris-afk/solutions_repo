# Problem 1
---
## **Theoretical Foundation: Governing Equations of Projectile Motion**

### **1. Introduction**
Projectile motion describes the motion of an object under the influence of gravity, assuming no air resistance. The motion occurs in two dimensions: horizontal (
$x$-axis) and vertical (
$y$-axis). We derive the governing equations starting from Newton’s laws of motion.

### **2. Equations of Motion**
Newton’s second law states:

$$F= m a$$

For projectile motion, the only force acting on the object (neglecting air resistance) is gravity:

$$ F_y = -mg, \quad F_x = 0 $$

Thus, the acceleration components are:

$$ a_x = 0, \quad a_y = -g $$

where \( g \) is the acceleration due to gravity.

Using kinematic equations:

#### **2.1 Horizontal Motion**
Since there is no horizontal acceleration,

$$ v_x = v_0 \cos(\theta) $$

$$ x = v_0 \cos(\theta) t $$

#### **2.2 Vertical Motion**
Using the kinematic equations for constant acceleration,

$$ v_y = v_0 \sin(\theta) - gt $$

$$ y = v_0 \sin(\theta) t - \frac{1}{2} g t^2 $$

### **3. Time of Flight**
The time of flight is found by solving for when the projectile returns to \( y = 0 \):

$$ 0 = v_0 \sin(\theta) t - \frac{1}{2} g t^2 $$

Factoring out \( t \):

$$ t ( v_0 \sin(\theta) - \frac{1}{2} g t ) = 0 $$

Ignoring the trivial solution \( t = 0 \), we solve for \( t \):

$$ t = \frac{2 v_0 \sin(\theta)}{g} $$

### **4. Range of the Projectile**
The horizontal range is given by:

$$ R = v_x \times t_{flight} $$

Substituting \( v_x = v_0 \cos(\theta) \) and \( t_{flight} \):

$$ R = v_0 \cos(\theta) \times \frac{2 v_0 \sin(\theta)}{g} $$

Using the identity $2 \sin(\theta) \cos(\theta) = \sin(2\theta)$,

$$ R = \frac{v_0^2 \sin(2\theta)}{g} $$

### **5. Maximum Height**
At maximum height, \( v_y = 0 \):

$$ 0 = v_0 \sin(\theta) - g t_{max} $$

Solving for \( t_{max} \):

$$ t_{max} = \frac{v_0 \sin(\theta)}{g} $$

Using the vertical displacement equation:

$$ h_{max} = v_0 \sin(\theta) t_{max} - \frac{1}{2} g t_{max}^2 $$

Substituting \( t_{max} \):

$$ h_{max} = \frac{v_0^2 \sin^2(\theta)}{2g} $$

### **6. Influence of Initial Conditions**
- **Initial Velocity \( v_0 \)**: Higher velocity increases both range and height.
- **Launch Angle \( \theta \)**: The range is maximized at \( \theta = 45^\circ \).
- **Gravity \( g \)**: Higher gravity decreases range and height.

### **7. Conclusion**
These equations provide a fundamental description of projectile motion. In further analysis, we will explore numerical simulations and practical applications, including air resistance and varying terrains.

---







