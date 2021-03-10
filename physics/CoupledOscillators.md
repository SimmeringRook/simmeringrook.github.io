## Normal Modes
We are interested in when all the spring constants and all the masses are the same.

  M becomes m·I; where m is now a scalar value

This lets us rewrite the eigenvalue equation:

  KX=-\omega^2 mX

X is an eigenvector of the K matrix with an eigenvalue of -\omega^2 m.

We want to be able to guess the solution.
## Solving a Coupled Harmonic Oscillator
We can always write the normal modes down for the Coupled Oscillator problem in the form:

KX=-\omega^2 MX

X is a column vector that describes the deviation for the mass from equilibrium

M is a diagonal matrix which represents each coupled mass as a matrix


--
We assume that the spring constant k and the masses are the same.

K is a diagonal matrix of the forces on each mass, where ∆x is omitted and is comprised of only
scalar multiples of k.

M becomes a scalar, m

We then rewrite the eigenvalue equation, noting the following:

X represents an eigenvector of K
with an eigenvalue of -\omega^2m

KX = -\omega^2m X

--
Next step: how to solve for values of K, we guess the solution:

### Find the K matrix
'''Example''': 3 Mass system between 2 walls

K is a 3x3 matrix:

Rows: force on mass (row #)

Cols: movement of mass (col #)

Move m1 -> ∆x to the right
  --
  R1,C1: -2k
  --
  Movement exerts a force of k∆x on m2
  R2,C1: k
  --
  movement exerts a force of 0 on m3
  R3,C1: 0

Move m2 -> ∆x to the right
  --
  Movement exerts a force of k∆x on m1
  R1,C2: k
  --
  R2,C2: -2k
  --
  movement exerts a force of k∆x on m3
  R3,C2: k

Move m2 -> ∆x to the right
  --
  Movement exerts a force of 0 on m1
  R1,C3: 0
  --
  Movement exerts a force of k∆x on m2
  R2,C1: k
  --
  R3,C1: -2k

### Find the Eigenvalues of K matrix
#### Find solution from Physical Intuition
Consider the motion of the masses and their normal modes:

if mass 1 and 3 move towards mass 2, we have:

'''X''' = (1,0,-1)^T

#### Plug into Eigenvalue Equation

KX = (-2k, 0, -2k)^T = -2k1,0,-1)^T

This means that '''X''' = (1,0,-1)^T is an eigenvector of the system with an
eigenvalue of -2k.

This also tells us that:

-2k = -m\omega^2 -> \omega = sqrt (2k/m)

You should find ''n'' eigenvectors for an ''n \times n'' K matrix, because K is
diagonalizable we know that you need to have the same number of eigenvectors as
the dimension of the matrix. Each eigenvalue should have an algebraic multiplicity of 1.
