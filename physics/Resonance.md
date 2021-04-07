# Resonance

?>**Definition**: Resonance is when the velocity amplitude of an oscillating system reaches its global maximum. This effect becomes noticeable as the [driving frequency](/physics/ForcedOscillations.md), $\omega_d$, approaches the resonance frequency, $\omega_f$.

The value of $\omega_f$ is dependent on the amount of [damping](/physics/Damping.md) present in the system, as well as the system's [natural frequency](/physics/AngularFrequency#Characteristic-Angular-Frequency.md).

For systems with:
- no damping
  - $\omega_f=\omega_0$
- with damping:
  - $\omega_f=\sqrt{{\omega_0}^2-2{\beta}^2}\approx\omega_0$ (when $\beta\ll\omega_0$)

## Q Factor
Also known as **quality factor**, this is describes the ratio between the natural frequency and the damping present in the system. This dimensionless value directly and quantitatively describes how underdamped an [oscillator](/physics/Oscillations.md) is.

The following are the formulas for calculating the Q factor for:
- A Generalized Oscillator:
$$Q=\frac{\omega_0}{2\beta}$$
- A (series) [LCR Circuit](/physics/LCRCircuit.md):
$$\begin{aligned}
Q &=\frac{\omega_0}{2\beta} \\
 &=\frac{1}{\sqrt{LC}}\frac{1}{2}\left(\frac{R}{2L}\right)^{-1} \\
 &=\frac{2L}{2R\sqrt{LC}} =\frac{\sqrt{L}}{R\sqrt{C}} \\
 &=\frac{\sqrt{C}}{\sqrt{C}}\frac{\sqrt{L}}{R\sqrt{C}}=\frac{\sqrt{LC}}{RC} \\
 &=\frac{1}{\omega_0 RC}
\end{aligned}$$
- A mechanical system:
  - [[File:Q_Factor_Mech.png]]

## Bandwidth

!>**TODO**: Add description and content for Bandwidth.

---

## External Resources
- [Series Resonance Circuit](https://www.electronics-tutorials.ws/accircuits/series-resonance.html)
- Wikipedia: [Q Factor](https://en.wikipedia.org/wiki/Q_factor)

---

## Internal Links
### Courses

- [PH424: Oscillations and Waves](/courses/PH424.md)
- [PH481: Physical Optics]

### Topics

- [Oscillations](/physics/Oscillations.md)
  - [Damping](/physics/Damping.md)
  - [Characteristic Angular Frequency](/physics/AngularFrequency#Characteristic-Angular-Frequency.md)

### Similar

- [Interference Patterns]
