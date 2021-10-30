---
title: "Thermodynamics Problem Solving Guide"
author: Thomas Knudson
papersize: a4
geometry: margin=2cm
linkcolor: blue
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz,tikz-3dplot}
    \usepackage{tkz-euclide}
    \usepackage{fancyhdr}
    \usepackage{float}
    \pagestyle{fancy}
    \fancyhead[LO,RE]{Thermodynamics Problem Solving Guide}
    \fancyhead[RO,LE]{Knudson}
---

## Algorithm

### 1. Reading The Problem Statement

- What are we asked to find?
- What quantities are given/known?
- What processes are occurring? Do they have names?
    -  E.g. "...the gas is compressed **adiabatically**..."

### 2. Start with the First Law

$U=Q+W$ is always true, so let's talk about (in broad strokes) how energy is transferred (or not) in this system.

- Equation of State can also influence how/what changes the internal energy

If the processes **are** quasistatic:

- $đQ$ and $đW$ are now exact differentials (This means we can now integrate them!)
    - $đQ \rightarrow dQ = TdS$
    - $đW \rightarrow dW = -pdV$
- If $U(S,V)$ isn't a helpful state function, we can use Legendre transforms to obtain a different thermodynamic identity
    - $F = U(T,V) = U(S,V) - TS \rightarrow dF = -SdT - pdV$
    - $H = U(S,p) = U(S,V) + pV \rightarrow dH = TdS + Vdp$
    - $G = U(T,p) = U(S,V) - TS + pV \rightarrow dG = -SdT + Vdp$
- This is where the keywords or process names from Step 1 should really shine: eliminating differentials in what ever thermodynamic identity fits the situation.

If the processes **are not** quasistatic:

- We want to get out of this stage very quickly: All we have is $dU = đQ + đW$ and we **cannot** do anythin with this!
    - $đQ$ and $đW$ being inexact differentials means that we don't know what they are: $Q$ and $W$ are not functions.
    - **You cannot do anything with inexact differentials**
- The ultimate goal here is to justify why we can approximate the process that is occurring with a similar one that is quasistatic.
    - Use the same initial and final conditions with the same state variables and functions
    - Then follow the steps for a quasistatic process

### 3. Use the Second Law

- Clearly define the system (and any relevant subsystems)
- Is the system in thermal contact with other systems? The environment?
- Always ensure that $\Delta S_{universe} \geq 0$
    - A system's (or subsystem's) change in entropy can be negative, but it has to balance out somehow

### 4. Use what you know

- If you haven't already solved the problem at this stage, you have everything about the system written out.
- Remember that all of the final conditions for the state are once the system has reached **equilibrium**.
    - This is sometimes enough of a powerful statement that it lets you set up a relationship between two separate state functions and then everything is just algebra/calculus from here.
- Leverage your prior scientific (physics and chemistry) knowledge!
    - You know a lot about different systems that we've talked about in 21X: that knowledge is still important as we're often taking those systems and just focusing on the energy side of things instead of equations of motion.
    - You might need to check out some other useful versions of the Equation of State or Internal energy of your system. 
        - E.g. *Ideal Gas Law encompasses the versions of the gas laws: Boyle's Law, etc; you might need to ensure that a condition is met in order to use this other form, but this is fair game*