# PH 585: Atomic, Molecular, and Optical Physics, Week 4

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

#### Review of Dipole Selection Rules

$$\begin{aligned}
H' &= \frac{e}{m}\vec{A}\cdot\vec{p}\\
\\
M_{ba} &\tilde{=} \frac{m\omega_{ba}}{\hbar} \hat{\epsilon}\cdot \vec{r}_{ba}\\
\\
r_{ba,q} &= \braket{b}{r_q}{a}\\
&\text{    Let q represent a general coordinate system such that:}\\
\\
\hat{\epsilon} &= (\epsilon_{-1}, \epsilon_{0}, \epsilon_{1})\\
\\
\epsilon_{-1} &\rightarrow \text{Left-hand circular polarized light}\\
\epsilon_0 &\rightarrow \hat{z}\\
\epsilon_{1} &\rightarrow \text{Right-hand}\\
\\
\hat{\epsilon}\cdot\vec{r}_{ba} &= \epsilon_1 r_{ba,1} + \epsilon_0 r_{ba,z} + \epsilon_{-1} r_{ba,-1}\\
\\
r_{ba,q} &= \sqrt{\frac{4\pi}{3}} \int_{0}^{\infty}{{R_{n'\ell '}}^* {R_{n'\ell '}} r^3 dr} \int{{Y_{\ell 'm'}}Y_{1q}{Y_{\ell m}} d\Omega}\\
\end{aligned}$$

parity: $\pi Y_{\ell m} = (-1)^{\ell} Y_{\ell m}$

$(-1)^{\ell '+\ell \pm 1}$ must be even to be allowed.
$$\Delta \ell = \ell ' - \ell \neq 0$$

In the dipole approximation:
$$\Delta \ell = \pm 1$$

In the quadrupole approximation: $(Y_{2q})$
$$\Delta \ell = 0, 2$$

#### Magnetic Selection Rule


Consider:
$$\int{{Y_{\ell 'm'}}Y_{1q}{Y_{\ell m}} d\Omega} \propto \int_{0}^{2\pi}{e^{i(m-m'+q)\phi} d\phi}$$

The exponent's power must be $0$, $m-m'+q = 0$, otherwise this just oscillates, and therefore will make the probability of transition go to $0$.

- Case 1:

  $\qquad$$\Delta m\ell = 0$,$\qquad$ if $q = 0$
- Case 2:

  $\qquad$$\Delta m\ell = \pm 1$, $\qquad$ if $q = \pm 1$ (this corresponds to left or right-handed circular polarized light)

Case 2 is the most common. If you excite with LH Cir Pol, you'll created a wavefunction that has a magnetic property to it; $$\Delta m\ell = 1$$

----

#### Figures of Merit

!> Matt: After finishing PH 585, only calculate a figure of merit if someone pays you!

Examples:

- $\sigma_{ba}$
- $\tau^{spon} = ({W_{ab}}^{spon})^{-1}$
- $f_{ka}$

Oscillator strength, f_{ka}, is a **dimensionless** figure of merit of how strong a transition will be from state $E_a$ to $E_k$. (how strong a transition is relative to other transitions)
$\Rightarrow$ i.e., field-matter interaction dipole strength

$$f_{ka} \equiv \frac{2m\omega_{ka}}{3\hbar} {\left\vert\vec{r}_{ka}\right\vert}^2$$
$$\omega_{ka} = \frac{E_k - E_a}{\hbar}$$

The 'f-sum rule', if you take all the different oscillator strength frequencies and sum their together, they must add to unity:
$$\sum_{k}^{}{f_{ka}} = 1$$

Bransden: 4.6, page 212
Generalize $\sum_{k}^{}{f_{ka}} = \frac{1}{3} to = 1$

$f_{ka}$

- for 2p to 1s: 0.416
- for the ionized state: 0.435 (Vacuum)
- for 3p to 1s: 0.079
- for 4p to 1s: 0.029

The oscillation strength can be used to find the spontaneous emission lifetime (page 215).

$$\tau^{spon} = {W_{ka}}^{-1} = [\frac{2{\omega_{ka}}^2}{mc^3}\frac{e^2}{4\pi\epsilon_0}f_{ka}]^{-1}$$

| state | $\tau^{spon}$ (ns) |
| ---- | ---- |
| 2p | 1.6 |
| 3s | 160 |
| 3p | 5.4 |
| 3d | 15.6 |
| 4s | 230 |
| 4p | 12.4 |
| 4d | 36.5 |
| 4f | 73 |

This is how long it takes the electron to emit a photon.

?> Why does a 4p take longer than a 2p?

It's all about the overlap. Need a better mode matching for more diffuse wavefunctions, as there is poorer overlap.

?> Why is a s state lifetime longer than a p state?

3s doesn't localized the electrons in a direction, where as p states strongly localize them.

Considering trends:

1. initial/final wavefunction overlap
2. How many states are dipole allowed?
    - might have more routes for decay

### Day 2

### Day 3
