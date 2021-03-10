## Frequency and Period
The rate at which a system oscillates is called the '''frequency''' of the system.
Frequency is measured in hertz ('''Hz''' or '''s^-1''') as cycles per second.
The time one full cycle takes to complete (start to stop) is called the '''period''' of the system.
Period and frequency are related through the following relationship:

[[File:Period_to_frequency_relation.png]]

'''Angular Frequency''' is an extension of this relationship, such that every full period corresponds to 2π about the unit circle (or Argand diagram).
As such, its relationship to period and frequency is defined as:

[[File:Angular_Frequency_to_period_and_frequency.png]]

## Differential Equation
### Derivation
We derive the equation of motion for a simple harmonic system by starting off with [[Newton's Second Law]].
In the simple case of a mass being suspended from the ceiling by a spring, there are two forces acting on the mass:
# The restoring force, [[Hooke's Law]]
# [[Gravity]]
From this, we can describe the net force of the system as the [[superposition]] of these two forces.
Replacing F_net with [[mass]] times [[acceleration]], we arrive at the following [[differential equation]]:

[[File:Force_Balance_ODE_SMH.png]]

After rearranging terms and performing a variable substitution, we can arrive at the more common version of this equation,
which is the [[Second Order]] [[homogeneous]] ordinary differential equation with constant coefficients:

[[File:SMH_ODE.png]]

Note that we define ω_0 in this context to be:

[[File:Angular_Frequency_Hookes_Law.png]]

And this is true for any SHM that experiences the restoring force from Hooke's Law. ω_0 is often referred to as the [[Characteristic Angular Frequency|Natural Angular Frequency]] (or Characteristic angular frequency) of the system.
### General Solutions

This differential equation has many solutions, but the four standard versions are as follows:

[[File:ABCD_Forms_SMH.png]]

## Other Notes

For systems being described by the A form, it is easy to see the following relationships between maximal and minimal values for position, velocity, and acceleration:

*Displacement is at a maximum value when displacement is equal to the amplitude
*Velocity is at a maximal value when displacement is equal to the equilibrium point
*Acceleration is at a maximal value when displacement is equal to the amplitude

[[File:Graph_of_AForm_SMH.png]]

The terms used above directly relate to mechanical systems, but the math and concepts are equally applicable to electrical simple harmonic [[Oscillations|oscillators]].

## See Also
*[[Oscillations]]
*[[LC Circuit]]
