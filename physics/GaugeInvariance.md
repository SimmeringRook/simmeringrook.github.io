$$\gdef\wrap[2]{\left( #1 \right)_{ #2 }}$$
$$\gdef\pder[2]{\frac{\partial #1}{\partial #2}}$$

# Gauge Invariance

!> **Definition:** $\vec{A}$ and $\phi$ are **not** unique potentials. Many $\vec{A}$ and $\phi$ may exist that give the same measurables for $\vec{E}$ and $\vec{B}$

We can formalize this by visualizing some $\vec{A}'=\vec{A}+\nabla f$ and similarly some $\phi ' = \phi-\frac{1}{c}\pder{f}{t}$. Now to demonstrate how this works, say we have some $\vec{B}$ which is $\nabla\times\vec{A}'$. We can write this as follows:

$$\begin{aligned}
\vec{B} &= \nabla\times\vec{A}' \\
 &=\nabla\times\vec{A}+\nabla\times\nabla f \\
 &= \nabla\times\vec{A}
\end{aligned}$$

## Coulomb Gauge

Set the $\nabla\cdot\vec{A}=0$.

!> Also requires $\phi=0$

Revisiting Maxwell's Equations:

$$\begin{aligned}
\nabla\cdot\vec{E} &= \frac{\rho}{\epsilon_0} = 0 \\
-\pder{}{t}\nabla\cdot\vec{A}-\nabla^2 \phi &= 0 \\
\nabla^2 \phi &= 0
\end{aligned}$$

## Landau Gauge
