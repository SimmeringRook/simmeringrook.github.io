# Fourier Series

We want a mathematical tool to describe a given function as a linear combination of sinusoidal functions.

## Definition

The Fourier Series uses an (infinite) set of integer multiples of sinusoidal functions to form the [basis](/maths/Basis.md) of a [vector space](/maths/VectorSpace.md) for all functions that are "smooth enough" and meet the [boundary condition](/maths/BoundaryConditions.md) of being periodic.

$$
\sum_{n=0}^{\infty}{\bigg(a_n\cos{\left(n\omega t\right)} + b_n\sin{\left(n\omega t\right)}\bigg)},\qquad n\in{\mathbb Z}
$$

### Basis

Let $V$ represent the Vector Space whose basis vectors are the [complete](/maths/Completeness.md) [orthogonal](/maths/Orthogonal.md) set:

$$\{0,1,\cos{x},\sin{x},\cos{2x},\sin{2x},...,\cos{nx},\sin{nx}\}$$

#### Completeness

!> **TODO:** Add proof of Completeness.

#### Orthogonality

Recall that the basis comes from the [Harmonic Functions]. Recall that the [inner product](/maths/InnerProduct.md) in this space uses the integral definition, where the limits are one full period.

Requiring that $n,m\in{\mathbb Z}$, $n,m>0$, and $n\neq m$, we have that $\sin{(nx)}$ is orthogonal to $\sin{(mx)}$:

$$\begin{aligned}
\int_{0}^{T}{\left(\sqrt{\frac{2}{T}}\sin{(nx)}\right) \left(\sqrt{\frac{2}{T}}\sin{(mx)}\right) dx}
  &= \frac{2}{T}\left[\frac{n\sin{(mx)}\cos{(nx)} - m\cos{(mx)}\sin{(nx)}}{m^2 - n^2} \right]_{0}^{T} \\
  &= \frac{2}{T}\left[\frac{n(0)(1) - m(1)(0)}{m^2 - n^2} - 0\right] \\
  &= 0
\end{aligned}$$

As well as $\cos{(nx)}$ is orthogonal to $\cos{(mx)}$:

$$\begin{aligned}
\int_{0}^{T}{\left(\sqrt{\frac{2}{T}}\sin{(nx)}\right) \left(\sqrt{\frac{2}{T}}\sin{(mx)}\right) dx}
  &= \frac{2}{T}\left[\frac{m\sin{(mx)}\cos{(nx)} - n\cos{(mx)}\sin{(nx)}}{m^2 - n^2} \right]_{0}^{T} \\
  &= \frac{2}{T}\left[\frac{n(0)(1) - m(1)(0)}{m^2 - n^2} - 0\right] \\
  &= 0
\end{aligned}$$

And finally, when $\sin{(nx)}$ to $\cos{(mx)}$, we don't require that $n\neq m$:

$$\begin{aligned}
\int_{0}^{T}{\left(\sqrt{\frac{2}{T}}\sin{(nx)}\right) \left(\sqrt{\frac{2}{T}}\cos{(mx)}\right) dx}
  &= \frac{2}{T}\left[\frac{m\sin{(mx)}\sin{(nx)} + n\cos{(mx)}\cos{(nx)}}{m^2 - n^2} \right]_{0}^{T} \\
  &= \frac{2}{T}\left[\frac{n(0)(0) - m(0)(0)}{m^2 - n^2} - 0\right] \\
  &= 0
\end{aligned}$$

#### Normal
Requiring that $n\in{\mathbb Z}$ and $n>0$ we have that $\sin{(nx)}$ is parallel to itself:

$$\begin{aligned}
\int_{0}^{T}{\left(\sqrt{\frac{2}{T}}\sin{(nx)}\right) \left(\sqrt{\frac{2}{T}}\sin{(nx)}\right) dx} &= \frac{2}{T}\int_{0}^{T}{\sin^2{(nx)} dx} \\
  &= \frac{2}{T}\left[\frac{x}{2}-\frac{\sin{\left(2nx\right)}}{4n}\right]_{0}^{T} \\
  &= \frac{2}{T}\left[\frac{T}{2} - 0\right] \\
  &= 1
\end{aligned}$$

As well as $\cos{(nx)}$:

$$\begin{aligned}
\int_{0}^{T}{\left(\sqrt{\frac{2}{T}}\cos{(nx)}\right) \left(\sqrt{\frac{2}{T}}\cos{(nx)}\right) dx} &= \frac{2}{T}\int_{0}^{T}{\cos^2{(nx)} dx} \\
  &= \frac{2}{T}\left[\frac{2nx+\sin{(2nx)}}{4n}\right]_{0}^{T}\\
  &= \frac{2}{T}\left[\frac{T}{2}-0\right] \\
  &= 1
\end{aligned}$$
