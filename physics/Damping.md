# Damping

?>**Definition**: Typically referred to as $\beta$, damping is when an external force reduces or removes energy from the system. For a mechanical system, this typically takes the form of friction. In an electrical oscillator, this takes the form of a [Resistor](/physics/Resistor.md).

## Equations
### Mechanical

$$\beta=\frac{b}{2m}$$

- $b$ is the decay factor
- $m$ is the mass of the oscillator

### Electrical

$$\beta=\frac{R}{2L}$$

- $R$ is the resistance of the [Resistor](/physics/Resistor.md) in the circuit
- $L$ is the inductance of the [Inductor](/physics/Inductor.md) in the circuit

### Other Forms

$$\beta=\sqrt{{\omega_1}^2-{\omega_0}^2}$$

- $\omega_0$ is the [characteristic angular frequency](/physics/AngularFrequency#Characteristic-Angular-Frequency.md) of the system
- $\omega_1$ is the ...

## Changes to the Differential Equation
### For Standing Waves
This example will show the changes made to the [LC Circuit](/physics/LCCircuit.md) when damping is added. Like with the original derivations, the same process is valid and applies to the mechanical case (which is not shown). The addition of a resistor makes the LC Circuit into a [LRC Circuit](/physics/LCRCircuit.md) and using [Kirchhoff's Voltage Law](/physics/KirchhoffVoltageLaw.md) we obtain the following equation:

$$\sum_i{V_i}=V_L+V_R+V_C=0$$

Once again, rewriting the voltage definitions of these components in terms of charge and its derivatives, we arrive at:

$$V_L=L\ddot{q},\qquad V_R=R\dot{q},\qquad V_C=\frac{q}{C}$$

$$L\ddot{q}+R\dot{q}+\frac{q}{C}=0$$

Just like we used $\omega_0$ to generalize the previous iteration of this ODE, we will now use $\beta$ to represent the damping of the system:

$$\ddot{q}+2\beta\dot{q}+\omega_0 q = 0$$

The same Ansatz-es apply to this ODE as well, and the process remains the same. The notable difference is that because there is damping, the [characteristic angular frequency](/physics/AngularFrequency#Characteristic-Angular-Frequency.md) of the system is changed. We call the characteristic frequency of this new system $\omega_1$, which is defined as follows:

$$i\omega_1\equiv\sqrt{\beta^2-{\omega_0}^2}$$

### For Traveling Waves

For electrical systems, damping is often referred to as [Attenuation].

## Behavior
### Decay over time

### Underdamped

$$\beta<\omega_0$$

It is important to note that in an underdamped oscillator, the motion is no longer strictly periodic, that is, the length of the period increases as the amplitude exponentially decays.

[[File:Graph_of_Underdamped.png]]
### Overdamped

$$\beta>\omega_0$$

[[File:Graph_of_Overdamped.png]]
### Critically Damped

$$\beta=\omega_0$$

[[File:Graph_of_CriticallyDamped.png]]

---

## External Resources
- [Damped Harmonic Oscillator on HyperPhysics](http://hyperphysics.phy-astr.gsu.edu/hbase/oscda.html)

---

## Internal Links
### Courses

- [PH424: Oscillations and Waves](/courses/PH424.md)

### Topics

- [Oscillations](/physics/Oscillations.md)
- [LRC Circuit](/physics/LCRCircuit.md)

### Similar
- [Friction]
