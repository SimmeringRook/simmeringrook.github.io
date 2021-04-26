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
