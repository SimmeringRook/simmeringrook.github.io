# MTH 537: General Relativity, Week 4

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial^2 #2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2\partial #3}}
\newcommand\bra[1]{\langle #1 |}
\newcommand\ket[1]{| #1 \rangle}
\newcommand\braket[3]{\bra{#1}#2\ket{#3}}
\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}
$$

## Concepts

## Lecture Notes

### Day 1

#### Radial Geodesics

Recall:
$$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}
\theta = \frac{\pi}{2}\\
\dot{\phi} = \frac{\ell}{r^2} \Rightarrow \ell = 0, \phi = constant\\
\dot{t} = \frac{e}{\schwarzCurve}\\
\\
\dot{r}^2 = e^2 - \schwarzCurve
$$

Suppose:
$$
\dot{r}|_{r=r_0} = 0\\
\Rightarrow e^2 = 1-\frac{2M}{r_0}\\
\Rightarrow r_0 = \frac{2m}{1-e^2}$$

We can note that $|e| \leq 1$, and without loss of generality e is positive ($e\geq 0$).

Cases:

- $e=1 \leftrightarrow r_0 = \infty$
- $0<e<1 \leftrightarrow 2m < r_0 < \infty$
- $e = 0 \leftrightarrow r_0 = 2m$

If we consider the cases where $e=1$, we have the category of geodesics:

$$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}
\dot{r}^2 = \frac{2m}{r}
\\
\dot{r} = \sqrt{\frac{2m}{r}}\\
\dot{t} = \frac{1}{\schwarzCurve}$$

For in-falling, $\dot{r} = -\sqrt{\frac{2m}{r}}$

Far-away observer:

$$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}\begin{aligned}
speed &= \frac{dr}{dt}\\
 &= \frac{\dot{r}}{\dot{t}}\\
 &= -\schwarzCurve\sqrt{\frac{2m}{r}}
\end{aligned}$$

$$r\rightarrow 2M,\qquad \frac{dr}{dt} \rightarrow 0$$

Shell-observer:

$$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}\begin{aligned}
speed &= \frac{\frac{dr}{\sqrt{\schwarzCurve}}}{\sqrt{\schwarzCurve}dt}\\
 &= \frac{\sigma^r}{\sigma^t}\\
 &= \frac{1}{\schwarzCurve} \frac{\dot{r}}{\dot{t}}\\
 &= - \sqrt{\frac{2M}{r}}
\end{aligned}$$

### Day 2

$$\begin{aligned}
\sigma^r = \frac{dr}{\sqrt{\schwarzCurve}} \qquad & \qquad \sigma^t = \sqrt{\schwarzCurve} dt \\
\\
\dot{r}^2 = -\sqrt{\frac{2m}{r}} \qquad & \qquad \dot{t} = \frac{1}{\schwarzCurve}\\
\end{aligned}$$

### Day 3

Rain coordinates continued:

$$\begin{aligned}
\sigma^T = dt+\frac{\sqrt{\frac{2m}{r}}}{\schwarzCurve} \qquad & \qquad \sigma^R = \frac{dr}{\schwarzCurve} + \sqrt{\frac{2m}{r}} dt \\
\\
\dot{r}^2 = -\sqrt{\frac{2m}{r}} \qquad & \qquad \dot{t} = \frac{1}{\schwarzCurve}\\
\end{aligned}$$

- $\sigma^T$ is exact, so we define $dT$ to satisify that relationship. $T$ is proper time along the geodesic.
- $\sigma^R$ is inexact, but we can scale it such that it becomes an exact 1-form by multiplying by $\sqrt{\frac{2m}{r}}dR$.

This provides us with the rain coordinates of $(T,R)$; this is a orthogonal coordinate system.

A slight variation of this are the Painleve'-Gullstrand coordinates, which use $(T,r)$ (and is not an orthogonal coordinate system).

Paul Painleve was a French Mathematician that also served as the Prime Minister for France.
Gullstrand was a Swedish Ophthalmologist and also a Physicist. His ophthalmology writings were very mathematical and served on the Nobel committee for Physics. He was very opposed to the theory of General Relativity and most of his *contributions* were the result of trying to find problems in the theory.

Line element in Rain coordinates:

$$ds^2 = -dT^2 + \frac{2m}{r}dR^2$$

in Painleve-Gullstrand:

$$ds^2 = - \schwarzCurve dT^2 + 2\sqrt{\frac{2m}{r}} dT dr + dr^2$$

Properties:

- Same time symmetry as before
- $T,r$ constant -> we have spherical symmetry again
- No singularity at $r=2m$
- Metric is not degenerate
- $T = constant$ gives us the line element for spherical ${\mathbb E}^3$
- still a problem at $r=0$

What about a beam of light?

Radial null-path:

$$\begin{aligned}
\sigma^T &= \pm \sigma^R\\
\\
\Rightarrow dT &= \pm (dr + \sqrt{\frac{2m}{r}} dT)
\Rightarrow \pm dr &= (1 \mp \sqrt{\frac{2m}{r}}) dT
\\
\frac{dr}{dT} &= \pm \left(1\mp\sqrt{\frac{2m}{r}}\right)
\end{aligned}$$

When $r<2m$, $\frac{dr}{dT}$ is negative for both versions of this equation. This is the mathematical representation of light cannot escape the event horizon.


---

Office Hour questions:

1. What does it mean to have a degenerate metric? An example?
 - Non-degenerate metric means non-invertible
 - This would cause a lot of problems for us.
2. Doesn't the equivalence principle tell us all free-float frames think they are locally flat?
