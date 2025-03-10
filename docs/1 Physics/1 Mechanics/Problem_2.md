# Problem 2
## **Theoretical Foundation of the Forced Damped Pendulum**

### **1. Governing Differential Equation**

The motion of a forced damped pendulum is described by the second-order nonlinear differential equation:

$$\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L}\sin\theta = A\cos(\omega t)$$

where:

- $\theta$ is the angular displacement,  
- $b$ is the damping coefficient,  
- $g$ is the acceleration due to gravity,  
- $L$ is the length of the pendulum,  
- $A$ is the amplitude of the external driving force,  
- $\omega$ is the driving frequency.

---

### **2. Approximate Solutions for Small-Angle Oscillations**

For small oscillations ($\theta \approx 0$), we use the small-angle approximation:

$$\sin\theta \approx \theta$$

Thus, the governing equation simplifies to:

$$\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L}\theta = A\cos(\omega t)$$

This is a linear nonhomogeneous differential equation, which has the general solution:

$$\theta(t) = \theta_h(t) + \theta_p(t)$$

where:

1. $\theta_h(t)$ is the solution to the homogeneous equation:

   $$\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L}\theta = 0$$

   which yields:

   $$\theta_h(t) = e^{-\frac{b}{2}t} \left(C_1\cos(\omega_0 t) + C_2\sin(\omega_0 t)\right)$$

   where $\omega_0 = \sqrt{\frac{g}{L} - \frac{b^2}{4}}$.

2. $\theta_p(t)$ is a particular solution due to the external forcing term:

   $$\theta_p(t) = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + (b\omega)^2}} \cos(\omega t - \phi)$$

   where the phase shift $\phi$ is given by:

$$
\tan\phi = \frac{b \cdot \omega}{\omega_0^2 - \omega^2}
$$


---

### **3. Resonance Conditions and Energy Considerations**

Resonance occurs when the driving frequency $\omega$ is close to the natural frequency of the system. The natural frequency (in the absence of damping) is given by:

$$\omega_0 = \sqrt{\frac{g}{L}}$$

For weak damping ($b \ll 1$), resonance approximately occurs when:

$$\omega \approx \omega_0$$

At resonance, the amplitude of oscillations becomes large, leading to significant energy absorption by the system. The total energy of the system consists of kinetic and potential energy:

- **Kinetic Energy:**

  $$KE = \frac{1}{2}mL^2\left(\frac{d\theta}{dt}\right)^2$$

- **Potential Energy:**

  $$PE = mgL(1 - \cos\theta)$$

The total energy:

$$E = KE + PE$$

Oscillates over time, with damping causing a gradual decay unless sustained by external forcing.

---

### **4. Conclusion**

The forced damped pendulum exhibits complex dynamics, ranging from periodic motion to chaotic behavior, depending on the values of $b, A, \omega$. Further analysis will involve numerical simulations and graphical representations of phase space and resonance conditions.


