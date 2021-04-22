# PH 585: Atomic, Molecular, and Optical Physics, Week 1

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

Brief History and Overview:
- Blackbody Radiation
  - Ultraviolet Catastrophe
  - $E_n = nh\nu$
- Models of the Atom
  - Plumb pudding
    - smeared out positive charge
    - no idea about Protons
    - Ernest Rutherford performed the experiment that required a new model
      - most particles went through the gold foil
      - few were reflected
      - implies core that was concentrated such that alpha particles were deflected
  - Bohr Model
- Emission and Absorption Spectra
- Particle Wave Duality
  - De Broglie
  - $\lambda = \frac{h}{p} \Leftrightarrow p\lambda = h$
  - Diffraction and interference patterns for electrons
- Heisenberg Uncertainty Principle

Looking ahead:
- Day 1
  - build the electromagnetic toolbox
  - quantize the field
    - take the classical EM wave and write as Quantum Harmonic Oscillator
    - $\vec{A}(\vec{r},t)=\frac{A_0}{2}\hat{\epsilon}\exp{ikr-\omega t}$
- Day 2
  - build the quantum mechanical toolbox
  - how to make the quantized EM field interact with matter
    - Take Lorentz force and what is the equivalent Hamiltonian
    - $\vec{F}_{EM} = q(\vec{E}+\vec{v}\times\vec{B}) \rightarrow \hat{H}$
    - **Question:** How does an EM-field interact with matter?
      - Assumptions:
        - no sources (just the field; not dealing with point charges)
        - field described by $\vec{A}$ and $\Phi$
          - $\vec{A}\rightarrow$ vector potential (for B-field)
          - $\Phi\rightarrow$ scalar potential (for E-field)
      - Goal:
        - $H_{EM}=\frac{1}{2m}(\vec{p}-q\vec{A})^2+q\Phi$
- Day 3
  - time-dependent perturbation theory
  - QM that you can get paid to do
    - [ab initio](https://en.wikipedia.org/wiki/Ab_initio_quantum_chemistry_methods) electronic
    - absorption, cross-section $\sigma$
    - NMR/MRI

### Day 2

Starting with Maxwell's Equations,

?> Note 1: If $\nabla\cdot\vec{B}=0$, the $\vec{B}$ must be the curl of some vector potential $\vec{A}$:
$\vec{B}=\nabla\times\vec{A}$

?> Note 2: If the $\nabla\times\vec{E}=-\pder{}{t}\wrap{\nabla\times\vec{A}}{}$, then we can group like terms:
$\nabla\times\wrap{E+\pder{}{t}\vec{A}}{} = 0$ which tells us that $E+\pder{}{t}\vec{A}$ must just be the gradient of some scalar potential: $-\nabla\phi$

Choices of $\phi$ and $\vec{A}$ are not unique, this allows us to apply [Gauge Invariance](/physics/GaugeInvariance.md).

Looking at the vacuum (no source charges), we simplify Maxwell's Equations:

$$\begin{aligned}
\nabla\cdot\vec{E} &= 0 \\
\nabla\times\vec{E} &= -\pder{\vec{B}}{t} \\
\nabla\cdot\vec{B} &= 0 \\
\nabla\times\vec{B} &= \frac{1}{c^2}\pder{\vec{E}}{t}
\end{aligned}$$

Finally, let us rewrite the 4th equation in terms of $\vec{A}$ and $\phi$ using the [Coulomb Gauge](/physics/GaugeInvariance#Coulomb-Gauge.md):

$$\begin{aligned}
\nabla\times\vec{B} &= \frac{1}{c^2}\pder{\vec{E}}{t} \\
\nabla\times\wrap{\nabla\times\vec{A}}{} &= -\frac{1}{c^2}\pder{}{t}\wrap{\pder{\vec{A}}{t}+\nabla\phi}{} \\
\nabla^2 \vec{A} &= \frac{1}{c^2}\pdersq{\vec{A}}{t}\\
\end{aligned}$$

And we see this is just another form of the [Wave Equation].

$$\begin{aligned}
\nabla^2 \vec{A} &= - k^2 = \frac{1}{c^2}\frac{\partial^2 \vec{A}}{\partial^2 t}\\
\\
\nabla^2 u + k^2 u &= 0 \\
\frac{\partial^2 \vec{A}}{\partial^2 t} + ac^2 k^2 &= 0
\end{aligned}$$

We then know the solutions take the form:
$$\begin{aligned}
u_{k}(\vec{r}) &= \frac{u_k}{2}\left(e^{i\vec{k}\cdot\vec{r}}+e^{-i\vec{k}\cdot\vec{r}}\right) \\
a_{k}(t) &= \frac{a_k}{2}\left(e^{i\omega t}+e^{-i\omega t}\right) \\
\end{aligned}$$

General Solution is a superposition of all oscillating modes $k$ where $\hat{\epsilon}_k$ denotes the polarization:
$$
\begin{aligned}
\vec{A}\wrap{\vec{r},t}{} &= \sum_{k}^{}{\hat{\epsilon}_k \left(c_k u_k(r) a_k(t) + \left(c_k u_k(r) a_k(t)\right)^{*}\right)} \\
  &= \sum_{k}^{}{\hat{\epsilon}_k |A_{vac, k=1}|\left(a_k e^{i(\vec{k}\cdot\vec{r}-\omega t)} + {a_k}^* e^{-i(\vec{k}\cdot\vec{r}-\omega t)}\right)}
\end{aligned}
$$


?> Recall:
$$
\vec{E} &= -\pder{\vec{A}}{t} = i\omega \vec{A} \\
\vec{B} &= \nabla\times\vec{A}
$$

> What is a particular solution for one mode?
$$
\vec{A}\wrap{\vec{r},t}{} = \frac{A_0}{2} \hat{\epsilon} \wrap{e^{i(\vec{k}\cdot\vec{r}-\omega t+\phi)} + e^{-i(\vec{k}\cdot\vec{r}-\omega t+\phi)}}{}
$$

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\bra[1]{\langle #1 |}
\newcommand\ket[1]{| #1 \rangle}
\newcommand\braket[3]{\bra{#1}#2\ket{#3}}
\begin{aligned}
|\vec{E}| &= \omega |\vec{A}| \\
\vec{B} &= \frac{A_0}{2} i(\vec{k}\times\hat{\epsilon}) \wrap{e^{i(\vec{k}\cdot\vec{r}-\omega t +\phi)} - e^{-i(\vec{k}\cdot\vec{r}-\omega t +\phi)}}{} \\
|\vec{B}| &= \frac{|\vec{k}|}{\omega} |\vec{E}| = \frac{1}{c} |\vec{E}|
\end{aligned}
$$

> What is the intensity of the light?

Intensity is an energy flow through space, typically measured in Watts/$m^2$, and called $I$. We use the [Poynting Vector](/physics/PoyntingVector.md):

$$
\vec{S} = \frac{1}{\mu_0} \vec{E}\times\vec{B}
$$

Then:

$$
\begin{aligned}
I &= \equiv |\vec{S}|_{avg} \\
  &= \frac{1}{\mu_0} |\vec{E}| |\vec{B}| \sin{\theta} \\
  &= \frac{1}{c \mu_0} |\vec{E}|^2 \sin{\frac{\pi}{2}} \\
  &= \frac{\epsilon_0 c}{2} |\vec{E}|^2
\end{aligned}
$$

#### Quantize the field

> What is the lowest energy a photon of mode $k$ can have?

$$E_k =\frac{\hbar\omega_k}{2}$$

In a vacuum:

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\begin{aligned}
U &= \frac{1}{2}\wrap{\epsilon_0 E^2 + \frac{1}{\mu_0}B^2}{} \\
  &= \frac{1}{2}E^2 \wrap{\epsilon_0+\frac{1}{\mu_0 c}} \\
  &= \epsilon_0 E^2\\
  \\
E_{total} &= \int{UdV} \\
 &= \epsilon_0 E^2 V \\
 \\
\frac{\hbar\omega_k}{2} &= \epsilon_0 E^2 V \\
|E_{vac}| &= \sqrt{\frac{\hbar\omega_k}{2V\epsilon_0}}
\end{aligned}
$$

This gives us the electric field created per photon in a vacuum of volume $V$. The wavelength that matches the cavity will be the photon that will be created.

### Day 3
