## Unbound States

States whose wavefunctions do not decay to 0 at infinity.

Psi(x-> +/- infty) -/-> 0

Unbound states cannot be normalized. All equations and formulas that require
integration from -infty to +infty do not apply, because the integral is not
finite.

Typically superpositions of free particle states.

Unbound state takes the form:

sum (n=1 to N) of: c_n*exp(ik_n x)

Note that this has the form of: sum of momentum eigenstates

Can do:
* Measure everything that depends only on momentum
**Expectation of momentum
**Kinetic Energy
**Uncertainty of momentum
**Uncertainty of Kinetic Energy


Cannot do:
* Calculate the expectation value
**Integral does not converge
* Normalize

## Bound States

## Finite Square Well/Scattering Problem

The particle is considered free until it interacts with the potential (wall).
We want to consider the probability that the particle will reflect or transmit.

Classically:
*''E < V_0''
**We expect 100% reflection
*''E > V_0''
**We expect 100% transmission

Quantum Mechanically:
*''E < V_0''
**We expect some reflection
**We also expect some transmission via tunneling
*''E > V_0''
**We expect some reflection
**We also expect some transmission

### Steps To Solve
#### Ansatz
*When ever we see a jump in potential, we denote a new region.
*Then we define Psi(x) to be a piecewise wavefunction:
**For each region, consider the linear combination of either:
***If E > V: use exp(+-ikx)
***If E < V: use exp(+-βx)
**Give each exponential a different unknown scalar coefficient
*Use Physical arguments to simplify Anstaz:
**Assume k,β are positive real numbers
**It is not physical for a wavefunction to grow to infinity
**For unbounded states:
***It is convention for the incoming wave to have a coefficient of 1.

#### Ensure Anstaz satisfies the Energy Eigenvalue Problem
The Hamiltonian for this system is:

H = p^2 / 2m + V

*Solve the Energy Eigenvalue equation for each region
**Consider the Hamiltonian for each region
<br>
=#### General Forms of k & β=====
*k is sqrt(2mE / hbar^2)
*β is sqrt((V-E)2m / hbar^2)

#### Apply Boundary Conditions
The main method for doing this step is using the [[Continuty Condition|continuity condition]],
which provides the following result:

=#### If potential has a finite jump=
*Psi(x) is continuous
This means the wavefunction for one region must be equal to the wavefunction for the other region at the shared region boundary
*Psi'(x) is also continuous
This means the derivative of the wavefunction for one region must be equal to the derivative of the wavefunction for the other region at the shared region boundary

<br>
=#### If potential has infinite jump=
This means the region is defined by a [[Dirac Delta Function]].

*Psi(x) is continous
This means the wavefunction for one region must be equal to the wavefunction for the other region at the shared region boundary
*Psi'(x)|(x=a+ε) - Psi'(x)|(x=a-ε) = (2mγ)/(hbar^2) Psi(a)

#### Solve for Coefficients
You should have a set of simplified linear equations of coefficients and k & β.

### Physical Interpretation
The norm squared of the coefficients corresponding to the reflected wave packets are called the [[Waves#Reflection|Reflection coefficient]].
This is the probability that the particle will be reflected by the interaction with the potential.

## Further Reading

## See Also
