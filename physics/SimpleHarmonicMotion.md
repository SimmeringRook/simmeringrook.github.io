# Simple Harmonic Motion

?>**Definition:** *Concise definition goes here*

## Frequency and Period
The rate at which a system oscillates is called the frequency of the system. (Cyclic) Frequency is measured in hertz ($Hz$ or $s^-1$) as cycles per second. The time one full cycle takes to complete (start to stop) is called the period of the system. Period and frequency are related through the following relationship:

$$T=\frac{1}{f}$$

Angular Frequency is an extension of this relationship, such that every full period corresponds to $2\pi$ about the unit circle (or Argand diagram). As such, its relationship to period and frequency is defined as:

$$\omega=2\pi f=\frac{2\pi}{T}$$

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

And this is true for any SHM that experiences the restoring force from Hooke's Law. $\omega_0$ is often referred to as the [Natural Angular Frequency(or Characteristic angular frequency)](/physics/AngularFrequency#Characteristic-Angular-Frequency.md) of the system.

### General Solutions

This differential equation has many solutions, but the four standard versions are as follows:
- A-form:
  - $A\cos{(\omega_0 t+\phi)}$
- B-form:
  - $B_p\cos{(\omega_0 t)} + B_q\sin{(\omega_0 t)}$
    - $p$ is *phase*
    - $q$ is *quadrature*
- C-form:
  - $Ce^{i\omega_0 t}+C^* e^{-i\omega_0 t}$
- D-form:
  - $\Re e(De^{i\omega_0 t})$

#### Initial Conditions

Given the following general initial conditions:
- $x_0=x(t=0)$
- $v_0=\dot{x}(t=0)$

##### A-form
We can then take the (time) derivative of our position function to obtain an expression for velocity as a function of time:

$$\begin{aligned}\frac{d}{dt}\left(A\cos{(\omega_0 t+\phi)}\right) &= -A\omega_0\sin{(\omega_0 t+\phi)}\\
\dot{x}(t) &= -\omega_0 A\sin{(\omega_0 t+\phi)}\end{aligned}$$

Then we equate our initial conditions:
$$\begin{aligned}
x(t=0) &= A\cos{(\omega_0\cdot0+\phi)}\\
x_0 &= A\cos{(\phi)}
\\ \\
\dot{x}(t=0) &= -\omega_0 A\sin{(\omega_0\cdot 0+\phi)}\\
v_0 &= -\omega_0 A\sin{(\phi)}\end{aligned}$$

We can manipulate these two equations to find ways to solve for $A$ and $\phi$ given the initial conditions of $x_0$ and $v_0$.
- To obtain the expression for $A$, we can square both equations and add them:
$$\begin{aligned}
{x_0}^2+\frac{{v_0}^2}{{\omega_0}^2} &= A^2(\sin^2{\phi}+\cos^2{\phi}) \\
A^2 &= {x_0}^2+\frac{{v_0}^2}{{\omega_0}^2} \\
A &= \sqrt{{x_0}^2+\frac{{v_0}^2}{{\omega_0}^2}}\\
A &= x_0\sqrt{1+\frac{{v_0}^2}{{x_0}^2 {\omega_0}^2}}
\end{aligned}$$

- To obtain the expression for $\phi$, we then just divide both equations:
$$\begin{aligned}
\frac{v_0}{x_0} &= \frac{-\omega_0 A\sin{(\phi)}}{A\cos{(\phi)}} \\
\frac{v_0}{x_0} &= -\omega_0\tan{\phi}\\
\tan{\phi} &= -\frac{v_0}{\omega_0 x_0}\\
\phi &= \arctan{\left(-\frac{v_0}{\omega_0 x_0}\right)}
\end{aligned}$$

##### B-form
Given the B-form, we have the position as a function of time given by:

$$x(t)=B_p\cos{(\omega_0 t)}+B_q\sin{(\omega_0 t)}$$

And so, taking the (time) derivative gives us velocity as a function of time:

$$\begin{aligned}
\frac{d}{dt}x(t) &= -\omega_0 B_p\sin{(\omega_0 t)} + \omega_0B_q\cos{(\omega_0 t)} \\ \dot{x}(t) &= -\omega_0 B_p\sin{(\omega_0 t)} + \omega_0B_q\cos{(\omega_0 t)}\end{aligned}
$$

Now let us explore these equations when $t=0$:

$$\begin{aligned}
x(t=0) &= B_p\cos{(\omega_0\cdot 0)}+B_q\sin{(\omega_0\cdot 0)}\\
x_0 &= B_p \\
\\ \\
\dot{x}(t=0) &= -\omega_0 B_p\sin{(\omega_0\cdot 0)} + \omega_0 B_q\cos{(\omega_0\cdot 0)}\\
v_0 &= \omega_0 B_q
\end{aligned}
$$

And we can relate this form to the A-form through the following:

$$\begin{aligned}
x_0 &= A\cos(\phi) = B_p \\
v_0 &= A\omega_0\sin(\phi) = \omega_0 B_q \\
\\
A\cos(\phi) &= B_p \\
A\omega_0\sin(\phi) &= \omega_0 B_q
\end{aligned}$$

Using the same methods as when solving the A-form for $A$ and $\phi$, we relate $B_p$ and $B_q$ to $A$ and $\phi$:

$$\begin{aligned}
A^2 &= {B_p}^2 + {B_q}^2 \\
\tan{(\phi)} &= -\frac{B_q}{B_p}
\end{aligned}$$

##### C-form

The third way we can represent position as a function of time for [SHM](/physics/SimpleHarmonicMotion.md) is by using complex numbers:

$$x(t)=C e^{i\omega_0 t}+C^* e^{-i\omega_0 t}$$

Where:
- $C$ is a complex number

Much more simply, the amplitude can be found by adding the conjugate to its complex value, e.g:
$$(a+bi)+(a-bi)=2a$$


## Other Notes

For systems being described by the A form, it is easy to see the following relationships between maximal and minimal values for position, velocity, and acceleration:

- Displacement is at a maximum value when displacement is equal to the amplitude
- Velocity is at a maximal value when displacement is equal to the equilibrium point
- Acceleration is at a maximal value when displacement is equal to the amplitude

[[File:Graph_of_AForm_SMH.png]]

The terms used above directly relate to mechanical systems, but the math and concepts are equally applicable to electrical simple harmonic [[Oscillations|oscillators]].

## See Also
- [Oscillations](/physics/Oscillations.md)
- [LC Circuit](/physics/LCCircuit.md)
