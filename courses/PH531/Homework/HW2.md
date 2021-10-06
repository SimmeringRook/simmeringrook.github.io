---
title: Homework 2
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Wednesday, September 29, 2021
papersize: a4
geometry: margin=2cm
linkcolor: blue
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz-3dplot}
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 531, Fall 2021}
    \fancyhead[CO,CE]{HW2}
    \fancyhead[LO,LE]{Knudson}
---

# Problem 2.43

> Find the capacitance per unit length of two coaxial metal cylindrical tubes, of radii $a$ and $b$.

Using Example 2.12 from Page 106 of Griffiths for inspiration, let us define the charge density of the coaxial cable to be uniform and given by $\sigma = Q/2\pi rL$. The inner cylinder, with radius $a$, then has a charge of $+Q$ while the inner surface (radius $b$) of the *outer* cylinder has a surface charge of $-Q$. Then, we can use Gauss's Law to determine the electric field strength outside and inside the coaxial cable. By inspection, there is no electric field external to the cable as the net enclosed charge for any Gaussian cylinder whose radius is greater than $b$ is $0$. Similarly, there is no enclosed charge for a Gaussian cylinder whose radius is less than $a$, and we are left only with the electric field between the two surfaces.

\begin{equation}
\vec{E}(s,\phi,z) = E_s (s,\phi,z) \hat{s} + E_\phi (s,\phi,z) \hat{\phi} + E_z (s,\phi,z) \hat{z}, \quad s\in(a,b)
\end{equation}

Noting that both charge densities are uniform:

- As we consider an observer at some arbitrary position $z$ along the symmetry of axis, we conclude that there cannot be any $z$ coordinate dependence of the resulting electric field as the observer is unable to discern any change to the charge configuration as $z$ is varied. Similarly, we can conclude that there cannot be a $\hat{z}$ component to the field by orienting an observer such that 'their feet' point radially inward and we assume that the $\vec{E}$ has a positive $\hat{z}$ component. Once the observer is rotated to face the $-\hat{z}$ direction, they would observe the same charge configuration and determine that they must be facing $+\hat{z}$ as before. This contradiction can only be resolved if there is no $\hat{z}$ component.
- Next, we apply the same test with respect to the $\phi$ coordinate and $\hat{\phi}$ direction. Since the $z$-axis is an axis of symmetry for the coaxial cable, it requires little argument for why there cannot be any dependence on the $\phi$ coordinate or $\hat{\phi}$.
- As the observer moves radially away from and towards $a$ (and $b$), they do observe a change in the charge configuration and cannot rule out $s$ coordinate or $\hat{s}$ directional dependence.

Therefore, the electric field between $a$ and $b$ must have the functional form of: $\vec{E}(s) = E_s(s)\hat{s}$. The normal vector to the $d\vec{A}$ element of the Gaussian sphere must be in the $\hat{s}$ direction, in order to be perpendicular for all values of $\phi$, and so we can resolve the inner product in the integral to be $\vec{E}(s)\cdot d\vec{A} = \lvert\vec{E}\rvert \lvert d\vec{A}\rvert \cos{\psi}$, where $\psi=0$.

$$\begin{aligned}
\int_{S}{\lvert\vec{E}\rvert \lvert d\vec{A}\rvert} &= \frac{Q_{enc}}{\epsilon_0}\\
\lvert\vec{E}\rvert \int_{\phi=0}^{\phi=2\pi}{ \int_{z=-\frac{L}{2}}^{z=\frac{L}{2}}{ sd\phi dz } } &= \frac{+Q}{\epsilon_0} \\
\lvert\vec{E}\rvert (2\pi L s) &= \frac{+Q}{\epsilon_0} \\
\lvert\vec{E}\rvert &= \frac{+Q}{2\pi L s\epsilon_0} \\
\end{aligned}$$

# Problem 2.52

# Problem 3.3

# Problem 3.12

# Problem 3.16
