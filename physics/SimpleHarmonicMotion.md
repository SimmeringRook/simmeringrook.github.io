## Frequency and Period
The rate at which a system oscillates is called the '''frequency''' of the system. (Cyclic) Frequency is measured in hertz ($Hz$ or $s^-1$) as cycles per second. The time one full cycle takes to complete (start to stop) is called the period of the system. Period and frequency are related through the following relationship:

$$T=\frac{1}{f}$$

'''Angular Frequency''' is an extension of this relationship, such that every full period corresponds to $2\pi$ about the unit circle (or Argand diagram). As such, its relationship to period and frequency is defined as:

$$\omega=2\pi f=\frac{1}{T}$$

## Differential Equation
### Derivation
We derive the equation of motion for a simple harmonic system by starting off with [Newton's Second Law](/physics/NewtonsLaws.md). In the simple case of a mass being suspended from the ceiling by a spring, there are two forces acting on the mass:
- The restoring force, often called [Hooke's Law](/physics/HookesLaw.md)
- [Gravity](/physics/Gravity.md)
$$F_{net}=m\ddot{x} \\ F_{net}= kx - mg$$
From this, we can describe the net force of the system as the [superposition](/physics/Superposition.md) of these two forces. Setting both equations equal to each other, we arrive at the following differential equation:

$$m\ddot{x}-kx=-mg$$

After rearranging terms and performing a variable substitution, we can arrive at the more common version of this equation,
which is the [Second Order](/maths/SecondOrderODE.md) [linear homogeneous ordinary differential equation](/maths/DifferentialEquations.md) with constant coefficients:

$$\ddot{x}-\omega_0 x=-g$$

Note that we define $\omega_0$ in this context to be:

$$\omega_0 = \frac{k}{m}$$

And this is true for any SHM that experiences the restoring force from Hooke's Law. $\omega_0$ is often referred to as the [Natural Angular Frequency(or Characteristic angular frequency)](/physics/AngularFrequency.md) of the system.

### General Solutions

This differential equation has many solutions, but the four standard versions are as follows:
- A-form:
  - $Acos(\omega_0 t+\phi)$
- B-form:
  - $B_p\cos{\omega_0 t} + B_q\sin{\omega_0 t}$
  - $p$ is *phase*
  - $q$ is *quadrature*
- C-form:
  - $Ce^{i\omega_0 t}+C^* e^{-i\omega_0 t}$
- D-form:
  - $\Re(De^{i\omega_0 t})$

## Other Notes

For systems being described by the A form, it is easy to see the following relationships between maximal and minimal values for position, velocity, and acceleration:

- Displacement is at a maximum value when displacement is equal to the amplitude
- Velocity is at a maximal value when displacement is equal to the equilibrium point
- Acceleration is at a maximal value when displacement is equal to the amplitude

[[File:Graph_of_AForm_SMH.png]]

The terms used above directly relate to mechanical systems, but the math and concepts are equally applicable to electrical simple harmonic [[Oscillations|oscillators]].

## See Also
*[[Oscillations]]
*[[LC Circuit]]
