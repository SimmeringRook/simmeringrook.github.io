# PH 585: Atomic, Molecular, and Optical Physics, Week 3

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

Key facts so far:

1. $H' \approx -\frac{e}{m}\wrap{\vec{A}\cdot\vec{p}}{}$
2. $c_b(t)$
  - $= \delta_{ba} - \frac{i}{\hbar} \int_{0}^{t}{dt' \bra{b}H'\ket{a} e^{i\omega_{ba}t'}}$
  - $= \delta_{ba} - \frac{e}{2m} \int_{0}^{\infty}{d\omega A_0(\omega)\wrap{T_1+T_2}{}}$
    - $T_1 = M_{ba} e^{i\delta} \int_{0}^{t}{dt' e^{i(\omega_{ba}-\omega)t'}}$
    - $T_2 = \bar{M}_{ba} e^{-i\delta} \int_{0}^{t}{dt' e^{i(\omega_{ba}+\omega)t'}}$
3. Transition rate:
  - $W_{ba} = \frac{d}{dt} |c_b(t)|^2$
  - $= \frac{\pi}{\epsilon_0 c} \left(\frac{e}{m}\right)^2 \frac{I(\omega)}{\omega_{ba}^2} |M_{ba}|^2$

If $\omega=\pm \omega_{ba}$, the matrix element $M_{ba}$ determines both the transition rate and absorption cross-section, $\sigma_{ba}\ (cm^2)$.

$$\sigma_{ba} = \frac{|M_{ba}|^2}{\omega_{ba}} \left(\frac{4\pi^2 \hbar^2}{m^2}\right)\alpha$$

$$\alpha\equiv \frac{e^2}{4\pi\epsilon_0}$$

Example:

k-line of H, $\sigma_{ba}=10^{-19}\ cm^2$. If I had 1 photon per $cm^{-2}$ going through 1 hydrogen atom, the odds of absorption is $10^{-19}$:

$$N= N_0 e^{-\sigma_{ba}n\lambda}$$
$N$ is photons after absorption
$N_0$ is initial photons
$n$ is atom density $(cm^{-3})$
$\lambda$ is depth

Beer Lambert Law:
$$A=-\epsilon c l$$
$$\epsilon = \sigma$$
$$c = n$$
$$l = \lambda$$

#### Dipole Approximation

$$M_{ba} = \bra{b}e^{i\vec{k}\cdot\vec{r}}\hat{\epsilon}\cdot\nabla\ket{a}$$

Do a power series approximation:
- $e^{i\vec{k}\cdot\vec{r}} = 1 + i\vec{k}\cdot\vec{r} + \frac{1}{2}\left(\vec{k}\cdot\vec{r}\right)^2 +\ ...$
- How many terms do we need?
  - Depends on the experiment

For light-matter interactions, how big is $|\vec{k}\cdot\vec{r}|$?
  - Not concerned about angles at this moment, just the magnitude
  - Approximate the wavefunction for hydrogen atom is $r \approx 2 a_0 = 0.1\ nm$
  - Choose $\lambda= 500\ nm$, its a good typical wavelength for light
  - $k$ is then simply: $\frac{2\pi}{\lambda}$

$$|\vec{k}\cdot\vec{r}| = \frac{2\pi}{\lambda} r = \frac{0.4\pi}{500} \approx 10^{-3}$$

So, for a light-matter interaction, $10^{-3}\ll 1$; this means our expansion for $e^{i\vec{k}\cdot\vec{r}}$ is approximately $1$.

!> Be careful: if $\lambda$ gets small, these terms get big. $r$ can also get big, if the wavefunction gets big.

At the end of the day, this approximation is good for light-matter interactions, but not good for x-rays or big wavefunctions (crystals, etc). From the atom's view, the wavelength perturbs the electron such that it sees and oscillating wavefunction that looks like a dipole charge configuration.

Using this approximation, lets try can calculate $M_{ba}$:

$$\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial^2 #2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2\partial #3}}
\newcommand\bra[1]{\langle #1 |}
\newcommand\ket[1]{| #1 \rangle}
\newcommand\braket[3]{\bra{#1}#2\ket{#3}}
\begin{aligned}
M_{ba} &= \bra{b}e^{i\vec{k}\cdot\vec{r}}\hat{\epsilon}\cdot\nabla\ket{a} \\
&\approx \bra{b}\hat{\epsilon}\cdot\nabla\ket{a} \\
&\approx \hat{\epsilon}\cdot\bra{b}\nabla\ket{a} \\
&\approx \frac{i}{\hbar}\hat{\epsilon}\bra{b}\vec{p}\ket{a}
\end{aligned}$$

$$\vec{p} = m \dot{\vec{r}}$$

?>Bransden 2.113, Heisenberg Equation: $$\frac{dr}{dt} = \pder{r}{t} + \frac{1}{i\hbar}[r,\ H]$$

$$\begin{aligned}
M_{ba} &\approx \frac{i}{\hbar}\hat{\epsilon}\cdot\bra{b}\vec{p}\ket{a} \\
 &\approx \frac{i}{\hbar}\hat{\epsilon}\cdot\wrap{i m \omega_{ba}}{}\braket{b}{\vec{r}}{a} \\
 &= \frac{-m \omega_{ba}}{\hbar} \hat{\epsilon}\cdot\braket{b}{\vec{r}}{a}\\
 &= \frac{-m \omega_{ba}}{\hbar} r_{ba}\cos{\theta}\\
\end{aligned}$$

Going back to Transition Rate:

$$\begin{aligned}
W_{ba} &= \frac{\pi}{\epsilon_0 c} \left(\frac{e}{m}\right)^2 \frac{I(\omega)}{\omega_{ba}^2} |M_{ba}|^2 \\
&\approx \frac{\pi}{\epsilon_0 c\hbar} I(\omega) |\braket{b}{r}{a}|^2 \cos^2{\theta}
\end{aligned}$$

If $\theta = \frac{\pi}{2}$$, $W_{ba} = 0$, Orthogonal light is not absorbed


Unpolarized light:

$$\frac{1}{4\pi} \int_{}^{}{\cos^2{\theta}d\Omega} = \frac{1}{3}$$

$$\begin{aligned}
W_{ba} &= \frac{1}{3}\frac{\pi}{\epsilon_0 c\hbar} I(\omega) |D_{ba}|^2
\end{aligned}$$

Dipole Operator:
$$\vec{D}_{ba} = -e \braket{b}{\vec{r}}{a}$$

$$W_{ba} \propto \braket{b}{x}{a} \approx \int{{\Psi_b}^{*} x \Psi_a d\tau}$$
