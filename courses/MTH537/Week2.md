# MTH 537: General Relativity, Week 2

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial^2 #2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2\partial #3}}
\newcommand\bra[1]{\langle #1 |}
\newcommand\ket[1]{| #1 \rangle}
\newcommand\braket[3]{\bra{#1}#2\ket{#3}}
$$

## Concepts

## Lecture Notes

### Day 1



### Day 2

#### Geodesics:
Rectangular
$$\ddot{x}=0=\ddot{y}$$
- constant velocity
- linear momentum is conserved

Polar
$$\ddot{r}-r\dot{\phi}^2=0=r\ddot{\phi}+2\dot{r}\dot{\phi}$$

solve $r\ddot{\phi}+2\dot{r}\dot{phi}$:
$$\begin{aligned}
0 &= \frac{\ddot{\phi}}{\dot{phi}} + 2 \frac{\dot{r}}{r} \\
  &= \left(\ln{\dot{\phi}}\right)^\cdot + 2\left(\ln{r}\right)^\cdot \\
  \text{const} &= \ln{\dot{\phi}} + 2\ln{r} \\
  \text{const} &= r^2\dot{\phi}
\end{aligned}$$

Multiply this by mass and we obtain an angular momentum, implying conservation of angular momentum.

$$\vec{v}d\lambda = d\vec{r} = \sigma^i \hat{e}_i$$

"$\vec{v}=\frac{d\vec{r}}{d\lambda}$" $\rightarrow$ $\sigma^i = v^i d\lambda$

For Geodesic, we want $d\vec{v}=0$

$$\begin{aligned}
d\vec{v} &= d(v^j \hat{e}_j) \\
  &= dv^j \hat{e}_j + v^j {\omega^i}_j \hat{e}_j \\
  &= (dv^i + v^j {\omega^i}_j) \hat{e}_j
\end{aligned}$$

For the vector to be $0$, we need each component to be $0$, so we drop the basis vectors:

$$\begin{aligned}
d\vec{v} &= 0 \\
0 &= dv^i + v^j {\omega^i}_j \\
  &= dv^i + v^j {\Gamma^i}_{jk} \sigma^k\\
  &= dv^i + v^j {\Gamma^i}_{jk} v^k d\lambda \\
  \\
0 &= \dot{v}^i + v^j {\Gamma^i}_{jk} v^j v^k
\end{aligned}$$

This gives us a 2nd Order, coupled, ODE.

---
##### Aside

?> Note: If $\dot{\vec{v}}=0$, then $\left(\vec{v}\cdot\vec{v}\right)^{\cdot} = 2\vec{v}\cdot\dot{\vec{v}} = 0$; But, $|\vec{v}| = \text{const}$ on geodesic! Therefore, we assume $|\vec{v}|=\pm 1$ (for the non-null case).

---

#### Symmetries

Rectangular:
$\dot{x} = \text{const}$
$\vec{v} = \dot{x}\hat{x} + \dot{y}\hat{y}$
$\dot{x} = \hat{x}\cdot\vec{v}$

Polar:
$r^2 \dot{\phi} = \text{const}$
$\vec{v} = \dot{r}\hat{r} + r\dot{\phi}\hat{\phi}$
$r^2 \dot{\phi} = r\hat{\phi}\cdot\vec{v}$

!> Try to find variables that don't show up in the line element.

#### Killing Vector
Subpage: [Killing Vector](/physics/KillingVector.md)

A vector field that satisfies the following property:

$$d\vec{X}\cdot d\vec{r}=0$$

They change orthogonally to the line element.

Example:
Rectangular
$$\hat{x},\qquad d\hat{x}=0 \Rightarrow d\hat{x}\cdot d\vec{r}=0$$

Polar
$$\begin{aligned}
d(r\hat{\phi}) &= dr\hat{\phi} + rd\hat{\phi} \\
&= dr\hat{\phi} - r d\phi\hat{r}\\
\\
d\vec{r} &= dr\hat{r} + rd\phi \hat{\phi} \\
\\
d(r\hat{\phi})\cdot d\vec{r} &= 0
\end{aligned}$$

Spherical:
Left it as an exercise to the reader.

##### Theorem
Given:
- $\vec{X}$, Killing Vector
- $\vec{v}$, geodesic

$$\left(\vec{X}\cdot \vec{v}\right)^{\cdot} = 0$$

There are 10 independent solutions to the Killing Vectors equation in $M^4$.

### Day 3

#### Polar
$$\vec{\Phi}=r\hat{\phi}$$
$$\vec{v}=\dot{r}\hat{r}+r\dot{\phi}\hat{\phi}$$

$$\vec{\Phi}\cdot\vec{v}=\text{const along a geodesic}$$
$$=r^2\dot{\phi}$$

$$\therefore r^2\dot{\phi}=l$$

Recall:

$$\left\|\vec{v}\right\|^{\cdot}=0 \qquad\text{on geodesic}$$

Normalize it:
$$\left\|\vec{v}\right\|=1$$
$$1=\vec{v}\cdot\vec{v}=\dot{r}^2+r^2\dot{\phi}^2$$

Now we just have two First Order PDEs..

> $\dot{r}^2=1-\frac{l}{r^2}$

#### Spherical

$$\begin{aligned}
\vec{\Phi} = r\sin{\theta}\hat{\phi}& \\
\vec{v} = r\dot{\theta}\hat{\theta}+r\sin{\theta}\dot{\phi}\hat{\phi}& \\
\\
\vec{\Phi}\cdot\vec{v} &= \text{const along a geodesic} \\
&= r^2\sin^2{\theta}\dot{\phi}=l \\
\\
\\
|{\vec{v}}| &= r\sqrt{\dot{\theta}^2+\sin^2{\theta}\dot{\phi}^2} \\
\\
\\
\frac{\vec{v}}{|\vec{v}|} &= \frac{r\dot{\theta}\hat{\theta}+r\sin{\theta}\dot{\phi}\hat{\phi}}{r\sqrt{\dot{\theta}^2+\sin^2{\theta}\dot{\phi}^2}} \\
&= \frac{\dot{\theta}\hat{\theta}+\sin{\theta}\dot{\phi}\hat{\phi}}{\sqrt{\dot{\theta}^2+\sin^2{\theta}\dot{\phi}^2}} \\
\\
\\
\frac{\vec{v}}{|\vec{v}|}\cdot\frac{\vec{v}}{|\vec{v}|} &=
\frac{\dot{\theta}\hat{\theta}+\sin{\theta}\dot{\phi}\hat{\phi}}{\sqrt{\dot{\theta}^2+\sin^2{\theta}\dot{\phi}^2}} \cdot \frac{\dot{\theta}\hat{\theta}+\sin{\theta}\dot{\phi}\hat{\phi}}{\sqrt{\dot{\theta}^2+\sin^2{\theta}\dot{\phi}^2}} \\
\\
1 &= \vec{v}\cdot\vec{v}=r^2\dot{\theta}^2+r^2\sin^2{\theta}\dot{\phi}^2
\end{aligned}$$

#### Schwarzschild

The Line Element
$$ds^2 = -\left(1-\frac{2M}{r}\right)dt^2 + \left(1-\frac{2M}{r}\right)^{-1} + r^2(d\theta^2 + \sin^2{\theta}d\phi^2)$$
