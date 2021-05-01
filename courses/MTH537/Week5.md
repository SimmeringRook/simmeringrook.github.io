# MTH 537: General Relativity, Week 5

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

#### Null Coordinates

Starting in Minkowski Flat space, Let $u=t-x$ and $v=t+x$

Then the line element is trivially:

$$ds^2 = dx^2 - dt^2 = -dudv$$

#### Rindler Coordinates

These are hyperbolic polar coordinates:

$\rho$ measures hyperbolic radius
$\alpha$ measures angle along the hyperbolas

$$ds^2 = dx^2 - dt^2 = d\rho^2 - \rho^2 d\alpha^2$$

Origin is not a well defined concept for this coordinate system. $\alpha\rightarrow\pm\infty$ corresponds to the light-like paths. $\rho\rightarrow 0$ describes the lines of constant $\alpha$ for $\alpha\rightarrow\pm\infty$. This breaks up Minkowski space into 4 quadrants or **wedges**.

Properties of note:

- $rho=0$ is a singularity
- $s=-1$ (negative signature)
- $\partial/\partial\alpha$ is a Killing Vector
- $\vec{v}=d\vec{r}/d\lambda = \dot{\vec{r}}$
- geodesics
