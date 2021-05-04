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

- $\rho=0$ is a singularity
- $s=-1$ (negative signature)
- $\partial/\partial\alpha$ is a Killing Vector
- $\vec{v}=d\vec{r}/d\lambda = \dot{\vec{r}}$
- geodesics
  - timelike killing vector -> geodesic '$e$'
  - "straight lines"

##### Rindler Null Coordinates

Start with the line element:

> 1. Factor:
> $$\begin{aligned}
ds^2 &= d\rho^2 - \rho^2 d\alpha^2\\
&= (d\rho + \rho d\alpha)(d\rho - \rho d\alpha)
\end{aligned}$$

But this isn't good enough, these differentials are not exact.

> 2. Make Exact
> $$\begin{aligned}
ds^2 &=\rho^2 \left(\frac{d\rho}{\rho} + d\alpha\right)\left(\frac{d\rho}{\rho} - d\alpha\right)\\
\end{aligned}$$
>Let:
$$dv = d\alpha-\frac{d\rho}{\rho},\qquad dv = d\alpha + \frac{d\rho}{\rho}$$
>Integrating provides:
>$$\begin{aligned}
u = \alpha - \ln{\rho}\qquad & \qquad v = \alpha + \ln{\rho}
\end{aligned}$$

Which gives us the line element:

$$ds^2 = -\rho^2 du dv$$

But we still want to be able to cross $\rho=0$:

>3. Exponentiate:
$$\begin{aligned}v-u = 2\ln{\rho}&\rightarrow e^{v-u}=\rho^2\\
ds^2 &= -e^{v-u} du dv\end{aligned}$$

>4. Separate:
$$\begin{aligned}
ds^2 &= -(e^{-u}du)(e^{v}dv)
\end{aligned}$$

Let's define:

$$dU\equiv e^{-u}du,\qquad dV = e^{v}dv$$

And we then have the line element:

$$ds^2 = -dUdV$$

Which describes Minkowski space.

### Day 2

Agenda:

- Introduce Kruskal Geometry
- Extend Kruskal using the algorithm:
    1. Factor
    2. Make Exact
    3. Exponentiate
    4. Separate

We start with the Schwarzschild line element:

> 2. Make Exact and then 1. Factor:
>$$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}\begin{aligned}
ds^2 &= -\schwarzCurve dt^2 + \frac{dr^2}{\schwarzCurve} +\ ...\\
&= \schwarzCurve \left(-dt^2 + \frac{dr^2}{\schwarzCurve^2}\right) \\
&= -\schwarzCurve \left(dt + \frac{dr}{\schwarzCurve}\right)\left(dt - \frac{dr}{\schwarzCurve}\right)\\
\\
dv\equiv dt +\frac{dr}{\schwarzCurve} \qquad &\&\qquad du\equiv dt - \frac{dr}{\schwarzCurve}\\
\\
ds^2 &= -\schwarzCurve du dv
\end{aligned}$$



> 3. Exponentiate:
> $$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}\begin{aligned}
2\frac{dr}{\schwarzCurve} = dv-du &\Rightarrow r+2M\ln{\left(\frac{r}{2M}-1\right)}=\frac{v-u}{2}\\
e^{\frac{r}{2M}}\left(\frac{r}{2M}-1\right) &= e^{\frac{v-u}{4M}}\\
\\
\schwarzCurve &= \frac{2M}{r}\left(\frac{r}{2M}-1\right) \\
&=\frac{2M}{r}e^{\frac{v-u}{4M}}e^{-\frac{r}{2M}}\\
\\
ds^2 &= -\frac{2M}{r}e^{\frac{v-u}{4M}}e^{-\frac{r}{2M}} du dv
\end{aligned}$$



> 4. Separate:
> $$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}\begin{aligned}
ds^2 &= -\frac{2M}{r}e^{\frac{v-u}{4M}}e^{-\frac{r}{2M}} du dv \\
&= -\frac{2M}{r}e^{-\frac{r}{2M}}(e^{-\frac{u}{4M}}du)(e^{\frac{v}{4M}}dv)\\
\\
dU = e^{-\frac{u}{4M}}du\qquad &\&\qquad dV = e^{\frac{v}{4M}}dv
\end{aligned}$$

!> **Convention:** to set the dimensions of $dU$ and $dV$ accordingly, we introduce the follow factors,
$$\begin{aligned}
dU = e^{-\frac{u}{4M}}\frac{du}{4M}\qquad &\&\qquad dV = e^{\frac{v}{4M}}\frac{dv}{4M} \\
\\
ds^2 &= -\frac{32M^3}{r}e^{-\frac{r}{2M}} dU dV
\end{aligned}$$

And so we obtain the Kruskal-Szekeres line element:

$$ds^2 = -\frac{32M^3}{r}e^{-\frac{r}{2M}} dU dV + r^2 (d\theta^2+\sin^2{\theta}d\phi^2)$$

?> What is $r$?
> It is not a coordinate, its a function (now). From above, we have the relation that: $$\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)} \schwarzCurve =\frac{2M}{r}e^{\frac{v-u}{4M}}e^{-\frac{r}{2M}}$$ which tells us we have the implicit relation: $$UV = -e^{\frac{v-u}{4M}} = e^{\frac{r}{4M}}\schwarzCurve$$ and there is no nice closed form solution for $r=r(U,V)$. Note that at $r=0$, $UV = 1$ and at $r=2m$, $UV = 0$

### Day 3
