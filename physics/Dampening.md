?>**Definition**: Typically referred to as $\beta$, damping is when an external force reduces or removes energy from the system. For a mechanical system, this typically takes the form of friction. In an electrical oscillator, this takes the form of a [[Resistor|resistor]].

## Equations
### Mechanical
[[File:Beta_Mech.png]]
### Electrical
[[File:Beta_LRC.png]]
### Other Forms
[[File:Beta_omega1_omega0.png]]

## Changes to the Differential Equation
### For Standing Waves
This example will show the changes made to the [[LC Circuit]] when dampening is added. Like with the original derivations, the same process is valid and applies to the mechanical case (which is not shown).
The addition of a resistor makes the LC Circuit into a [[LCR Circuit]] and using [[Kirchhoff's Voltage Law]] we obtain:

[[File:Kirchoff_VoltageLaw_LCR.png]]

Once again, rewriting the voltage definitions of these components in terms of charge and its derivatives, we arrive at:

[[File:LRC_Voltage_To_Qterms.png]]

Just like we used ω_0 to generalize the previous iteration of this ODE, we will now use β to represent the dampening of the system.

[[File:LRC_ODE.png]]

The same ansatzes apply to this ODE as well, and the process remains the same. The notable difference is that because there is dampening, the [[Characteristic Angular Frequency]] of the system is changed.
We call this new characteristic frequency of the system ω_1:

[[File:Omega1_Definition.png]]

### For Traveling Waves
For electrical systems, this is often referred to as [[Attenuation|attenuation]].

## Behavior
### Decay over time

### Underdamped
β<ω_0

It is important to note that in an underdamped oscillator, the motion is no longer strictly periodic, that is, the length of the period increases as the amplitude exponentially decays.

[[File:Graph_of_Underdamped.png]]
### Overdamped
β>ω_0

[[File:Graph_of_Overdamped.png]]
### Critically Damped
β=ω_0

[[File:Graph_of_CriticallyDamped.png]]

## See Also
*[[Oscillations]]
*[[LCR Circuit]]

## Further Reading
*[http://hyperphysics.phy-astr.gsu.edu/hbase/oscda.html Damped Harmonic Oscillator on HyperPhysics]
