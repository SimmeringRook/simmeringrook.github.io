# MTH 537: General Relativity, Week 3

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

$$ds^2 = \frac{a^2}{a^2-r^2} dr^2 + r^2 d\phi^2$$

Given this line element, what do you notice?
- signature is $0$
- $a^2 = r^2$ is weird
- $r\rightarrow\infty$
  - Asymptotically Flat?
- Killing Vector: $\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\propto \pder{}{\phi}$
  - axially symmetric

This was really a sphere in a cylindrical coordinates:
$$\begin{aligned}
r^2 + z^2 = a^2 &= const\\
rdr+zdz &=0 \\
\\
ds^2 &= dr^2 + r^2 d\phi^2 + dz^2 \\
 &= dr^2 + r^2 d\phi^2 + \frac{r^2}{z^2} dr^2 \\
 &= \frac{a^2}{a^2-r^2} dr^2 + r^2 d\phi^2
 \end{aligned}$$

'Physical radius'  $\int{ds}$

Further recap and information of [Schwarzschild Geometry](/physics/Schwarzschild.md).

#### Physics of GR

1. Principle of Relativity
   - Galilean Relativity:
     - All frames are equivalent
     - Velocity addition is simple and linear
     - Results of experiments do not depend on relative uniform motion of observers
   - Einstein:
     - Maxwell's equations for Electromagnetism
       - imply $c=3\times10^{8} \frac{m}{s}$
       - speed of light is independent of observer
       - This leads to Special Relativity
2. Equivalence Principle
   - Gravity affects everything the same way.
   - Free fall $\equiv$ no gravity
     - acceleration <-> gravity
     - Free objects move on geodesics
       - straight worldlines
3. Mach's Principle:
   - All the matter in the universe affects local notion of acceleration
   - matter $\equiv$ curvature
     - Leads to General Relativity

Eddington preformed an experiment that demonstrated gravitational lensing.

### Day 2

Geodesics in Schwarzschild Geometry:

What is $d\vec{r}$?

$$d\vec{r} = \sqrt{1-\frac{2M}{r}}dt\hat{t} + \frac{1}{\sqrt{1-\frac{2M}{r}}} dr \hat{r} + r(d\theta \hat{\theta} + r\sin{\theta}d\phi\hat{\phi})$$

The orthonormal basis of 1-forms are different:

$$\begin{aligned}
\sigma^{t} &= \sqrt{1-\frac{2M}{r}}dt \\
\sigma^{r} &= \frac{1}{\sqrt{1-\frac{2M}{r}}}dr \\
\sigma^{\theta} &= rd\theta \\
\sigma^{\phi} &= r\sin{\theta}d\phi
\end{aligned}$$

Gradient of a $0-form$ looks like what we're used to:

$$\begin{aligned}
df &= \pder{f}{t}dt + \pder{f}{r}dr + \pder{f}{\theta}d\theta + \pder{f}{\phi}d\phi \\
\\
\nabla f &= -\frac{1}{\sqrt{1-\frac{2m}{r}}} \pder{f}{t}dt\hat{t} + \sqrt{1-\frac{2m}{r}}\pder{f}{r}dr\hat{r} + \frac{1}{r}\pder{f}{\theta}d\theta\hat{\theta} + \frac{1}{r\sin{\theta}}\pder{f}{\phi}d\phi\hat{\phi}
\end{aligned}$$

And so, our scale factors for this space are:

$$\begin{aligned}
h_{t} &= \frac{1}{\sqrt{1-\frac{2m}{r}}} \\
h_{r} &= \sqrt{1-\frac{2m}{r}} \\
h_{\theta} &= \frac{1}{r} \\
h_{\phi} &= \frac{1}{r\sin{\theta}}
\end{aligned}$$

#### Killing Vectors

If we have a vector field that corresponds just to a symmetry coordinate, that field is a Killing Vector. So, we have two vectors that satisfy this:

$$\begin{aligned}
\vec{\Phi}\cdot\nabla f = \pder{f}{\phi} &\Rightarrow \vec{\Phi} = r\sin{\theta}\hat{\phi} \\
\vec{T}\cdot\nabla f = \pder{f}{t} &\Rightarrow \vec{T} = \sqrt{1-\frac{2m}{r}}\hat{t}
\end{aligned}$$

#### Geodesics

Velocity vector is just $d\vec{r}$ divided by $d\lambda$:

$$
\vec{v}=\dot{\vec{r}}= \frac{d\vec{r}}{d\lambda} = \sqrt{1-\frac{2m}{r}}\dot{t}\hat{t} + ... + r\sin{\theta}\dot{\phi}\hat{\phi}
$$

Constants of the motion:
- associated with angular momentum:
$$l = \vec{\Phi}\cdot\vec{v}=r^2\sin^2{\theta}\dot{\phi}$$
- associated with energy:
$$e = \vec{T}\cdot\vec{v}=\left(1-\frac{2m}{r}\right)\dot{t}$$

Geodesic Equations:

$$\begin{aligned}
\dot{t} &= \frac{e}{1-\frac{2m}{r}} \\
\dot{\theta} &= 0 \leftarrow \qquad \text{ Equatorial plane},\quad \theta=\frac{\pi}{2}\\
\dot{\phi} &= \frac{l}{r^2}
\end{aligned}$$

Our equations imply that we traverse geodesics uniformly. If the object is timelike, assume $\vec{v}\cdot\vec{v}=-1$.

$$\begin{aligned}
-1 &= - \left(1-\frac{2m}{r}\right)\dot{t}^2 + \frac{\dot{r}^2}{1-\frac{2m}{r}} + r^2 (\dot{\theta}^2 + \sin^2{\theta}\dot{\phi}^2)\\
&= -\frac{e^2}{1-\frac{2m}{r}}+\frac{\dot{r}^2}{1-\frac{2m}{r}}+0+\frac{l^2}{r^2}\\
\\
\dot{r}^2 &= e^2 - \left(1+\frac{l^2}{r^2}\right)\left(1-\frac{2m}{r}\right)
\end{aligned}$$

In a sense, we're looking at: $\dot{r}^2 = \text{ "energy" } + \text{ "effective potential"}$

### Day 3
