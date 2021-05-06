# Week 1

## Day 1

Course Logistics

## Day 2

Classical free particles:

1. no net force
2. no acceleration
3. constant velocity
4. constant momentum

Quantum Free Particles:

1. no net force $\rightarrow$ no potential
    - In QM, we rely on Hamiltonians to discuss systems, not forces. We represent forces with potential energies
2. and 3. nothing to compare to
4. Constant momentum $\rightarrow$ momentum eigenstate

How do we describe Quantum Free particle?
  - we describe the state or wavefunction

First task is to derive the wavefunction of a QM free particle. We start with the standard Hamiltonian:

$$ H = \frac{p^2}{2m} + V(x)$$

where $p$ is the linear momentum operator as defined by (in the position basis):

$$\newcommand\pder[2]{\frac{\partial #1}{\partial #2}} p\equiv -i\hbar\pder{}{x}$$

?> We've seen this in previously in [PH 425](/courses/PH425.md) with [particle in a box].

So, we use the property that a free particle (in QM) has no potential with the Hamiltonian and the Energy eigenvalue equation:

$$H \psi(x) = E\psi(x)$$

>$$\newcommand\wrap[1]{\left(#1\right)}\begin{aligned}
\wrap{\frac{p^2}{2m} + V(x)}\psi(x) &= E\psi(x)\\
\text{Using: }V(x) = 0\Rightarrow\frac{p^2}{2m}\psi(x) &= E\psi(x)
\end{aligned}$$
> We have the relation that the second (partial) derivative is proportional to the function, which sounds like an exponential. Let's try the Anstaz: $\psi(x) = Ae^{ikx}$. $$\newcommand\wrap[1]{\left(#1\right)}\begin{aligned}
\wrap{\frac{p^2}{2m} + V(x)}\psi(x) &= E\psi(x)\\
\text{Using: }V(x) = 0\Rightarrow\frac{p^2}{2m}\psi(x) &= E\psi(x)
\end{aligned}$$
