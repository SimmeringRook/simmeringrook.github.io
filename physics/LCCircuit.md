# LC Circuit

?>**Definition**: A simple circuit that contains both an [Inductor](/physics/Inductor.md) and [Capacitor](/physics/Capacitor.md).

[[File:LC_Circuit_Schematic.png]]

## Differential Equation
### Derivation
This derivation will be analogous to that performed for a mechanical system in the [[Simple_Harmonic_Motion#Differential_Equation| Simple Harmonic Motion]]
page.

We begin by analyzing the circuit using [[Kirchhoff's Voltage Law]], which states that:

[[File:Kirchoff_VoltageLaw_LC.png]]

Replacing the voltage terms with their definitions in terms of charge, we arrive at the following differential equation:

[[File:LC_Circuit_ODE.png]]

Note that, in this case, we define ω_0 as the inverse of the capacitor multiplied by the inductor:

[[File:Angular_Frequency_LC.png]]

### General Solutions
Given that the differential equation has the same form as that derived for a mechanical harmonic oscillator, the same solutions are valid for this equation.

[[File:ABCD_Forms_SMH.png]]

---

## Internal Links
### Courses

- [PH411: Electronics](/courses/PH411.md)
- [PH424: Oscillations and Waves](/courses/PH424.md)

### Topics

- [Oscillations](/physics/Oscillations.md)
  - [Simple Harmonic Motion](/physics/SimpleHarmonicMotion.md)

### Similar
- [LRC Circuit](/physics/LCRCircuit.md)
