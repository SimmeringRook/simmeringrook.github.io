# PH 585: Atomic, Molecular, and Optical Physics, Week 5

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

[Particle Exchange]
[Slater Determinant]


## Lecture Notes

### Day 1

If we can construct Hartree-Fock Wavefunctions, we can use the variation method.

Recall that wavefunctions also have spin, $\chi$, so for the 2$e^-$ wavefunction, we have position and spin:

$$\Psi(q_1, q_2) = \psi(r_1, r_2)\chi(1,2)$$

Let spin-up be denoted by $\alpha$ or $\uparrow$ and spin-down be $\beta$ or $\downarrow$. All possible spin configurations are given by:

$$\chi(1,2) = \begin{cases} \alpha(1)\alpha(2) &\rightarrow &\uparrow\uparrow \\
\alpha(1)\beta(2) &\rightarrow &\uparrow\downarrow \\
\beta(1)\alpha(2) &\rightarrow &\downarrow\uparrow \\
\beta(1)\beta(2) &\rightarrow &\downarrow\downarrow \\
\end{cases}$$

However, Quantum Mechanics must remain true in the "Looking-glass" world under particle exchange. The representation must respect parity and be invariant under particle exchange.

> E.g., if $r_1$ was $\uparrow$, and we *swapped* electrons, then $\psi(r_1, r_2) = \pm \psi(r_2, r_1)$.

 - The $+$ condition is called the ortho state (bosons).
 - The $-$ condition is called the para state (fermions).

Now, if we include spin in the wavefunction, $\Psi(q_1, q_2) = \psi(r_1, r_2)\alpha(1)\beta(2)$ and exchanging: $\psi(r_2, r_1)\alpha(1)\beta(1)$. But this violates particle exchange $\big(\psi(r_2, r_1)\neq\Psi(q_1, q_2)\big)$.

$$\begin{aligned}
\Psi(q_1, q_2) &= \frac{1}{\sqrt{2}}\psi(r_1, r_2)\bigg(\alpha(1)\beta(2) - \alpha(2)\beta(1)\bigg)\\
\\
\downarrow & \quad\text{parity}\\
\\
&= \frac{1}{\sqrt{2}}\psi(r_2, r_1)\bigg(\alpha(2)\beta(2) - \alpha(1)\beta(2)\bigg)
\end{aligned}$$

---

Step 1 to the electronic structure calculation:

Solve the central field schrodinger equation:

$$H_c \psi_c = E\psi_c,\qquad H=\frac{p^2}{2m_i}+V_{pseudo}$$

We have to solve this *by hand*:
$$\psi_c = u_1(r_1) u_2(r_2) ... u_N (r_N)$$

But these wavefunctions don't have spin yet.

>Example for a Helium atom in $1s^2$ Possible configurations:
>
>- $s=1$, triplet:
>    1. $u_{1s}(r_1) u_{1s}(r_2)\alpha(1)\alpha(2)$
>    2. $u_{1s}(r_1) u_{1s}(r_2)\beta(1)\beta(2)$
>- para, $s=0$, singlet:
>    3. $$\psi_c = \frac{1}{\sqrt{2}} \begin{vmatrix}
u_{1s}(r_1)\alpha(1) & u_{1s}(r_1)\beta(1) \\
u_{1s}(r_2)\alpha(2) & u_{1s}(r_2)\beta(2)
\end{vmatrix}$$
>- ortho function:
>    4. $u_{1s}(r_1) u_{1s}(r_2) \frac{1}{\sqrt{2}} \bigg[\alpha(1)\beta(2)+\alpha(2)\beta(1)\bigg]$

This just gives us the wavefunctions, we still need to find the correction.

---

Calculating the Central Field Hamiltonian for $Fr$:

$$\begin{aligned}
H_{Fr} &= H_C + H'\\
H_C &= \sum_{i=1}^{N=87}{-\frac{\hbar^2}{2m_i}{\nabla_i}^2 + V_{psuedo}(r_i)}\\
\\
H' &= \sum_{i<j=1}^{N=87}{\frac{e^2}{4\pi\epsilon_0 r_{ij}}} - \sum_{i=1}^{N=87}{\frac{Ze^2}{4\pi\epsilon_0 r_i} + V_{psuedo}(r_i)}\\
\\
V_{pseudo}(r_i) &= -\frac{Ze^2}{4\pi\epsilon_0 r_i} + \left\langle\sum_{i<j=1}^{N=87}{\frac{e^2}{4\pi\epsilon_0 r_{ij}}}\right\rangle
\end{aligned}$$

### Day 2

### Day 3

Coherent Matter Excitations

Fox -> 9.3-9.4: "How can we resolve QM oscillations?"

Question: Suppose you instead apply a constant E-field in the $\hat{z}$ direction.

$$\vec{E} = E_0 \hat{z}$$

Use our master equation:

$$H = \frac{1}{2m} \left(\vec{p}-e\vec{A}\right)^2 -e\phi$$

Consider a gauge transformation to be able to insert our $E$ field into this equation. In the Coloumb gague:
$\vec{A}=-\pder{E}{t}$ implies that $\vec{A}=0$ since the $E$ field has no time dependence.

Instead, let us look at the scalar potential:

$$H' = - e\phi$$

> Recalling from E&M, $\vec{E}\equiv-\nabla\phi = E_0\hat{z}$; $\Rightarrow\phi=-E_0 z$. (Might have seen this with the [Stark Effect](/physics/StarkEffect.md)

So, our perturbation looks like:

$$H' = eE_0z$$

?> The [Stark Effect](/physics/StarkEffect.md), $H' = eE_0z$, looks like a dipole operator, how is it different?
?>
?> 1. No time dependence
?> 2. The field is polarized in the direction of propagation, so the field can't impart angular momentum. The selection rule for Stark is $\Delta m_\ell = 0$ compared to the selection rule for Dipole: $\Delta m_\ell = \pm1$.

Consider a 2-level System:

$$H = \frac{1}{2m} \left(\vec{p}-e\vec{A}\right)^2 -e\phi + V_{Coulomb}$$

Approximate $A^2\approx 0$, which gives us the perturbation as:

$$H' \approx \frac{e}{m}\vec{A}\cdot\vec{p}$$

In the dipole approximation, we get that $e^{i\vec{k}\cdot\vec{r}}\tilde{=}1$.

$$H' = \frac{e}{m}\left[\frac{A_0}{2}\left(e^{i\omega t}+ e^{-i\omega t}\right)\right]\cdot(-i\hbar\nabla)$$

$${H'}_{21}\equiv \braket{2}{H'}{1}= \frac{e^2}{m}\braket{2}{A(t)}{1}M_{21}$$

> Recall: $$M_{21} = \frac{m\omega_{21}}{\hbar e}\braket{2}{\hat{\epsilon}\cdot\vec{r}_{1q}}{1} \tilde{=} \frac{m\omega_{21}}{\hbar e}\braket{2}{x}{1}$$

?> $$A(t)=\frac{A_0}{2}\left[e^{i(\omega -\omega_{21})t}+e^{-i(\omega -\omega_{21})t}\right]$$ Remember in the Coulomb gauge: $$\vec{E}=-\pder{A}{t}\\ \pder{A}{t}\approx i\omega_{21} A(t) = \vec{E}(t)$$

And we'll find that:

$$H' = -i \frac{e E_0 x}{2} \left(e^{i\omega t}+e^{-i\omega t}\right)$$

#### 2-state time dependent pertubation review

$T_1$ describes $\ket{1}\rightarrow\ket{2}$
$T_2$ describes $\ket{2}\rightarrow\ket{1}$

So, our wavefunction is:

$$\ket{\psi} = c_1 (t) e^{-i \frac{E_1}{\hbar}t} \ket{1} + c_2 (t) e^{-i \frac{E_2}{\hbar}t} \ket{2}$$

And our Hamiltonian is:

$$H = H_0 + H'(t)\\
H'(t) = \frac{-eE_0x}{2}\left(e^{i\omega t}+e^{-i\omega t}\right)$$

Step 1: Operate on both sides of $\ket{\psi}$ with Schrodinger's Equation.

$$\left[\frac{i}{\hbar}\pder{}{t}-(H_0+H')\right]\ket{\psi}=0$$

$$0 = \left[i\hbar\dot{c_1}-E_1+E_1-H'c_1(t)\right] e^{-i \frac{E_1}{\hbar}t} \ket{1} + \left[i\hbar\dot{c_2}-E_2+E_2-H'c_2(t)\right] c_2 (t) e^{-i \frac{E_2}{\hbar}t} \ket{2}$$

$$0 = \left[i\hbar\dot{c_1}-H'c_1(t)\right] e^{-i \frac{E_1}{\hbar}t} \ket{1} + \left[i\hbar\dot{c_2}-H'c_2(t)\right] c_2 (t) e^{-i \frac{E_2}{\hbar}t} \ket{2}$$

Step 2: Take the inner product with the final state.

Final state is: $\bra{2}e^{i\frac{E_2}{\hbar}t}$.

$$\omega_0 \equiv \frac{E_2 - E_1}{\hbar} = \omega_{21}$$

$$0 = -\braket{2}{H'}{1}e^{i\omega_0 t} c_1(t)+i\hbar\dot{c_2}(t)\braket{2}{}{2}-\braket{2}{H'}{2} c_2(t)$$

$$\dot{c_2}(t)=-\frac{i}{\hbar}\left({H'}_{21}e^{i\omega_0 t}c_1(t)-{H'}_{22}c_2(t)\right)$$

?> To get $\dot{c_1}$, we do the same thing but with $\bra{1}e^{i\frac{E_1}{\hbar}t}$ leading to the equation: $$\dot{c_1}(t)=-\frac{i}{\hbar}\left({H'}_{12}e^{i\omega_0 t}c_2(t)-{H'}_{11}c_1(t)\right)$$

In the **dipole approximation**, these imply $\Delta \ell =0$:
$${H'}_{22}~\braket{2}{x}{2}=0$$
$${H'}_{11}~\braket{1}{x}{1}=0$$

Then:
$$\dot{c_2}(t)=-\frac{i}{\hbar}{H'}_{21}e^{i\omega_0 t}c_1(t)$$
$$\dot{c_1}(t)=-\frac{i}{\hbar}{H'}_{12}e^{i\omega_0 t}c_2(t)$$

**Weak field** approximation:
$$c_1(t=0)=1$$

$$c_1(t)\approx1$$

$$\dot{c_1}(t)=0$$
$$\dot{c_2}(t)=-\frac{i}{\hbar}{H'}_{21}e^{i\omega_0 t}$$

**Strong Coupling limit**:

$$\dot{c_2}(t)=\frac{i\Omega_R}{2}(e^{-i(\omega-\omega_0)t}+e^{i(\omega-\omega_0)t})c_1(t)$$
Rotating wave approximation.

Rabi Frequency, $\Omega_R$:
$$\Omega_R \equiv \frac{eE_0}{\hbar}\braket{2}{x}{1}$$
