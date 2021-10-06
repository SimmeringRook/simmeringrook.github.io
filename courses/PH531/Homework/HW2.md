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

\begin{equation}
\vec{E}(s) = \frac{Q}{2\pi\epsilon_0 L} \frac{1}{s} \hat{s}, \qquad s\in(a,b)
\end{equation}

Now that we have the electric field, finding the capacitance is trivial when using the relation: $C=Q/V$. Since the electric field is $0$ for $s\notin(a,b)$, when integrating across the domain of $s$, the only non-zero integrand in inside that interval[^1].

$$\begin{aligned}
V &= - \int_{b}^{a}{\vec{E}(s)\cdot d\vec{\ell}}\\
&= - \frac{Q}{2\pi\epsilon_0 L} \int_b^a{\frac{ds}{s}} \\
&= - \frac{Q}{2\pi\epsilon_0 L} \ln{\frac{a}{b}} \\
&= \frac{Q}{2\pi\epsilon_0 L} \ln{\frac{b}{a}}
\end{aligned}$$

[^1]: While not necessary to change the order in this case, it is prudent to verify that the potential described is that form the view point of the positive conductor, per page 105 of Griffiths.

$$\begin{aligned}
C &= \frac{Q}{V} \\
&= \frac{Q}{\frac{Q}{2\pi\epsilon_0 L} \ln{\frac{b}{a}}} \\
&= \frac{2\pi\epsilon_0 L}{\ln{\frac{b}{a}}}\\
\end{aligned}$$

\begin{equation}
\frac{C}{L} = \frac{2\pi\epsilon_0}{\ln{\frac{b}{a}}}
\end{equation}

\pagebreak

# Problem 2.52

> Two infinitely long wires running parallel to the $x$ axis carry uniform charge densities $+\lambda$ and $-\lambda$.

## Part A

> Find the potential at any point $(x,y,z)$, using the origin as your reference.

## Part B

> For any equipotential $V$, define the constant $K = \exp{\left(4 \pi \epsilon_0 \frac{V}{\lambda}\right)}$ and prove that the equipotentials are cylinders centered on $y_0 = \pm a \frac{K+1}{K-1}$ with radius $R = 2 a\frac{\sqrt{K}}{\lvert K-1 \rvert}$

\pagebreak

# Problem 3.3

> Find the general solution to Laplace's equation in spherical coordinates, for the case where $V$ depends only on $r$. Do the same for cylindrical coordinates, assuming $V$ depends only on $s$.

Recall Laplace's Equation:

\begin{equation}
\nabla^2 V = 0
\end{equation}

### Spherical

Since Laplace's equation must be true for all values of $r$, we can conclude that the derivative with respect to $r$ of $r^2 \frac{dV}{dr}$ must be 0. This implies that this quantity must be some constant and without loss of generality:

$$\begin{aligned}
\frac{1}{r^2} \frac{d}{dr} \left(r^2 \frac{dV}{dr}\right) &= 0\\
\frac{d}{dr} \left(r^2 \frac{dV}{dr}\right) &= 0\\
r^2 \frac{dV}{dr} &= c, \quad c\in\mathbb{R} \\
dV &= \frac{c}{r^2} dr \\
V &= - \frac{c}{r} + \xi
\end{aligned}$$

\begin{equation}
V(r) = - \frac{c}{r} + \xi, \qquad c,\xi\in\mathbb{R}
\end{equation}

### Cylindrical

Using the same logic, we obtain a similar potential for cylindrical coordinates.

$$\begin{aligned}
\frac{1}{s} \frac{d}{ds} \left(s \frac{dV}{ds}\right) &= 0\\
\frac{d}{ds} \left(s \frac{dV}{ds}\right) &= 0\\
s \frac{dV}{ds} &= c, \quad c\in\mathbb{R} \\
dV &= \frac{c}{s} ds \\
V &= c\ln{s} + \xi
\end{aligned}$$

\begin{equation}
V(s) = c\ln{s} + \xi, \qquad c,\xi\in\mathbb{R}
\end{equation}

\pagebreak

# Problem 3.12

> Two long, straight copper pipes, each of radius $R$, are held a distance $2d$ apart. One is at potential $V_0$, the other at $-V_0$. Find the potential everywhere.

Using Griffith's Hint of exploiting Problem 2.52...
