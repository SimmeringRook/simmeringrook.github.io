---
title: Homework 2
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Wednesday, October 6, 2021
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

Using our work from Problem 2.43, we can see that the electric field for each individual wire (in isolation) is the same:

\begin{equation}
\vec{E}(s) = \frac{Q}{2\pi\epsilon_0 L} \frac{1}{s} \hat{s} = \frac{\pm\lambda}{2\pi\epsilon_0}\frac{1}{s}\hat{s}
\end{equation}

The potential for $+\lambda$ is:

$$\begin{aligned}
V_{+} &= - \int_{a}^{s}{\vec{E}(s)\cdot d\vec{\ell}}\\
&= - \frac{\lambda}{2\pi\epsilon_0} \int_{a}^{s}{\frac{1}{s}ds}\\
&= - \frac{\lambda}{2\pi\epsilon_0}\ln{\frac{s}{a}}\\
\end{aligned}$$

And so we would then expect the opposite result for $-\lambda$:

$$\begin{aligned}
V_{-} &= - \int_{a}^{s}{\vec{E}(s)\cdot d\vec{\ell}}\\
&= - \frac{-\lambda}{2\pi\epsilon_0} \int_{a}^{s}{\frac{1}{s}ds}\\
&= + \frac{\lambda}{2\pi\epsilon_0}\ln{\frac{s}{a}}\\
\end{aligned}$$

Next, by utilizing the principle of superposition, we subtract the lower potential, $V_+$, from the  higher, $V_-$, to find a generalized form of the potential *almost* anywhere in $\mathbb{R}^3$:

$$\begin{aligned}
V_{tot} &= V_{-} - V_{+}  \\
&= \frac{\lambda}{2\pi\epsilon_0} \left(\ln{\frac{s_-}{a}} - \ln{\frac{s_+}{a}}\right)\\
&= \frac{\lambda}{2\pi\epsilon_0} \ln{\frac{s_-}{s_+}}
\end{aligned}$$

Recalling that the $s$-coordinate corresponds to the *radial* distance away from the axis of symmetry and that the $x$-axis is the axis parallel to both wires, each $s_\pm$ coordinate then must correspond to the $y$ and $z$ coordinates away from each respective wire. For the case of one wire positioned at $x=0$, we would define the coordinate transformation of $s$ to be the distance away from $x=0$ in the $y$-$z$ plane: $\sqrt{(y)^2 + (z)^2}$. Applied to this physical situation, the $s_\pm$ distance just needs to be offset by the respective wire's $y'$ value of $\mp a$:

$$s_+ = \sqrt{(y-a)^2 + z^2}, \qquad s_- = \sqrt{(y+a)^2 + z^2}$$

Our final step is to substitute these coordinate transformations into the superposition of potential and we will obtain an expression for determining the potential at any $(x,y,z)$:

\begin{equation}
V(x,y,z) = \frac{\lambda}{2\pi\epsilon_0} \ln{\frac{\sqrt{(y+a)^2 + z^2}}{\sqrt{(y-a)^2 + z^2}}}
\end{equation}

\pagebreak

## Part B

> For any equipotential $V$, define the constant $K = \exp{\left(4 \pi \epsilon_0 \frac{V}{\lambda}\right)}$ and prove that the equipotentials are cylinders centered on $y_0 = \pm a \frac{K+1}{K-1}$ with radius $R = 2 a\frac{\sqrt{K}}{\lvert K-1 \rvert}$

What we know (in general):

- Linear combinations of $e^x$ and $e^{-x}$ can be rewritten as factors of $\sinh{x}$ and $\cosh{x}$. $$e^x = \sinh(x) + \cosh(x)$$
- WolframAlpha can provide inside into alternate formations of the $K+1$ and $K-1$ quantities: $$e^x - 1 = \frac{2}{\coth{(x/2)}-1}, \qquad e^x +1 = 2+\frac{2}{\coth{(x/2)}-1}$$ $$\frac{e^x + 1}{e^x -1} = \coth{\frac{x}{2}}$$
- From Vector Calculus: the gradient is perpendicular to level curves (equipotentials) and due to the cylindrical symmetry of each wire (when $|y|,|z|<|a|$) and of the combined system (when $\lvert y\rvert ,|z| \gg \pm a$), we expect these equipotential surfaces to respect that same symmetry.
  - Our potential function from Part A has no dependence on the $x$-coordinate, so if we can demonstrate that a circle about the wire as the same value of potential $V$ along it, we will have created our equipotential (cylindrical) surface
- The equation for a circle has the form: $$(z-z_0)^2 + (y-y_0)^2 = R^2, \qquad z_0,y_0 \text{ describe the center}$$
  - $z_0=0$, $y_0 = \pm a \frac{\exp{\left(4 \pi \epsilon_0 \frac{V}{\lambda}\right)}+1}{\exp{\left(4 \pi \epsilon_0 \frac{V}{\lambda}\right)}-1}$

---

Playing around:

$$R = 2a \frac{\sqrt{\exp{\left(4 \pi \epsilon_0 \frac{V}{\lambda}\right)}}}{\lvert \exp{\left(4 \pi \epsilon_0 \frac{V}{\lambda}\right)} - 1 \rvert}$$

$$R = 2a \frac{\sqrt{ \sinh{x}+\cosh{x} }}{\lvert \frac{2}{\coth{(x/2)}-1} \rvert}$$

$$R = 2a \frac{\sqrt{ e^x }}{ \sqrt{(e^x -1)^2} } \Rightarrow R^2 = 4a^2 \frac{e^x}{(e^x -1)^2}$$

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

$$\ $$

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

Using Griffith's Hint of exploiting Problem 2.52, we have:

- The electric field due to an infinitely long wire, $\vec{E}(s) = \frac{Q}{2\pi\epsilon_0 L} \frac{1}{s} \hat{s}$
  - The field inside each pipe (caused by its own charge density), is $0$ by Gauss's Law.
- The potential everywhere in space, $V(x,y,z) = \frac{\lambda}{2\pi\epsilon_0} \ln{\frac{\sqrt{(y+a)^2 + z^2}}{\sqrt{(y-a)^2 + z^2}}}$
- The distance between wires, $2a$, is equivalent to the distance between the two pipes and their radii, $2(d+R)$.

> Upon further reflection of the problem statement, I've found the wording to be a bit ambiguous: From what points of reference on the pipes is the $2d$ distance measured? Practically, I would assume that you would measure the *exterior* distance between each pipe, and so the total distance between the centers of each pipe would correspond to: $R+d+d+R$. This is the setup I will proceed with (opposed to $-R+2d-R$ being the distance from the exterior of one pipe to the other).

Without imposing unusual expectations, we can consider the physical situation extremely similar to Problem 2.52 and treat our pipes as being infinitely long hollow cylinders with their length parallel to the $x$-axis. Then, the $y$-coordinate offset for each pipe can directly be mapped to $|a|\mapsto |d+R|$ and center each pipe along the $y$-axis. Substituting these changes into the potential function, we obtain the following:

$$V(x,y,z) = \frac{\lambda}{2\pi\epsilon_0} \ln{\frac{\sqrt{(y+(d+R))^2 + z^2}}{\sqrt{(y-(d+R))^2 + z^2}}}$$
