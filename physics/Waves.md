## Types of Waves
### Standing
### Traveling

## Properties of Waves
### Reflection
When a traveling wave encounters a change in medium, a portion of the incident wave is reflected back down the original medium.
In the context of waves traveling down a coaxial cable, this happens when two cables are connected, and the second cable has a different impedance value than the first.
We can calculate the ratio of the amplitude for this reflected wave with the following relationship:

[[File:Reflected_Equals_B_Over_A.png]]

This relationship was derived during the process of solving the 1-D Non-dispersive Wave PDE, as shown in the following section.
The '''sign''' of the amplitude for this wave depends on the type of boundary encountered when changing mediums:
*If the boundary is '''hard''': The sign is ''flipped''.
**Example: A wave traveling down two coaxial cables. The impedance of the first cable is less than the second cable, '''Z_1 < Z_2'''.
*If the boundary is a '''soft''': The sign remains ''unchanged''.
**Example: A wave traveling down a chain connected to a string. The transition from the chain to string is a soft boundary.

Also note that, the reflected wave is traveling in the same medium as the incident wave did. This can be particularly useful if you're trying to answer questions about
the incident wave using only the reflected and transmitted wave. The impact of this effect is that the '''width''' of the reflected wave and incident wave will be the
'''same'''.
### Transmission
Like with reflection, when the incident wave encounters a boundary, a portion of the incident wave continues to travel in the original direction.
The transmission coefficient is the ratio of the amplitudes between the transmitted wave and incident wave and has the similar relationship:

[[File:Transmitted_Equals_C_Over_A.png]]

The transmitted wave '''does not''' change polarity when encountering either type of boundary (hard or soft). The transmitted wave will have a
different width and amplitude from the incident wave. If there is no difference between the incident and transmitted wave, then the boundary crossed
by the incident wave is negligible and should be verifiable by a 0 reflection coefficient.

## One Dimensional Waves
### Deriving the Non-dispersive Wave Equation
Depending on the physical system we are discussing, there are a variety of ways that we can arrive at the '''Non-dispersive Wave Equation'''.
*For a string, we can use [[Tension|tension]] and [[Newton's Second Law]]
*For [[Electromagnetism|electromagnetic]] [[Electromagnetic Radiation|waves]], we can use [[Maxwell's Equations]]
*For a circuit, we can use [[Kirchhoff's Voltage Law]]

### Guide to Solve the Non-dispersive PDE
*[[Media:PDE_Solution_Guide.pdf|General Solution]]
*[[Media:Dirichlet_Boundary_Conditions.pdf|Dirichlet Boundary Conditions]]
*[[Media:Neumann_Boundary_Conditions.pdf|Neumann Boundary Condtions]]

### Accounting for Attenuation
