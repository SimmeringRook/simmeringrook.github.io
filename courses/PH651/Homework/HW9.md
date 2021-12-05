---
title: Homework 9
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Wednesday, December 1, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{HW6}
    \fancyhead[LO,LE]{Knudson}
---

\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\newcommand{\expectation}[1]{{\left\langle #1 \right\rangle}}
\newcommand{\pprime}{{\prime\prime}}

# Question 1

> Consider a $1$-D harmonic oscillator.

## Part A

> Evaluate: $[P_H(t_1), P_H(t_2)]$

Recall that $P_H(t)= i\sqrt{\frac{m\hbar\omega}{2}}(-a_H(t)+{a^\dagger}_H(t))$ where $a_H(t) = ae^{-i\omega t}$ and $a_H(t) = {a^\dagger}e^{i\omega t}$, then:

$$\begin{aligned}
[P_H(t_1), P_H(t_2)] &= \left(i\sqrt{\frac{m\hbar\omega}{2}}\right)^2 \left[(-ae^{-i\omega t_1}+{a^\dagger}e^{i\omega t_1})(-ae^{-i\omega t_2}+{a^\dagger}e^{i\omega t_2}) - (-ae^{-i\omega t_2}+{a^\dagger}e^{i\omega t_2})(-ae^{-i\omega t_1}+{a^\dagger}e^{i\omega t_1}) \right] \\
\\
\text{Let } \Delta t = t_2 - t_1 &\Rightarrow - \Delta t = t_1 - t_2 \\
t_3 &= t_1 + t_2 \\
\\
&= -\frac{m\hbar\omega}{2} \left[(a^2 e^{-i\omega t_3} -{a^\dagger}ae^{-i\omega \Delta t} - a{a^\dagger}e^{i\omega \Delta t} + {a^\dagger}^2 e^{i\omega t_3}) - (a^2 e^{-i\omega t_3} -{a^\dagger}ae^{i\omega \Delta t} - a{a^\dagger}e^{-i\omega \Delta t} + {a^\dagger}^2 e^{i\omega t_3}) \right] \\
&= -\frac{m\hbar\omega}{2} \left[(a^2 - a^2)e^{-i\omega t_3} - {a^\dagger}a (e^{i\omega \Delta t}-e^{-i\omega \Delta t}) + a{a^\dagger}(e^{i\omega \Delta t}-e^{-i\omega \Delta t} + ({a^\dagger}^2 - {a^\dagger}^2) e^{i\omega t_3})\right] \\
&= -\frac{m\hbar\omega}{2} \left[{a^\dagger}a - a{a^\dagger}\right] (e^{-i\omega \Delta t}-e^{-i\omega \Delta t}) \\
&= \frac{m\hbar\omega}{2} \left(-\left[{a^\dagger},\ a\right]\right) (2i\sin{(\omega\Delta t)}) \\
&= im\hbar\omega\left(\left[a,\ {a^\dagger}\right]\right)\sin{(\omega (t_2 - t_1))} \\
&= im\hbar\omega\sin{(\omega (t_2 - t_1))} \\
\end{aligned}$$

\pagebreak

## Part B

> Evaluate: $[X_H(t_1), X_H(t_2)]$

Recall that $X_H(t)= \sqrt{\frac{\hbar}{2m\omega}}(a_H(t)+{a^\dagger}_H(t))$ and note that this is almost identical to Part A. Only the sign of the cross terms will be different as: $(a+a^\dagger)^2$ vs $(a^\dagger - a)^2$.

$$\begin{aligned}
[X_H(t_1), X_H(t_2)] &= \left(\sqrt{\frac{\hbar}{2m\omega}}\right)^2 \left[(ae^{-i\omega t_1}+{a^\dagger}e^{i\omega t_1})(ae^{-i\omega t_2}+{a^\dagger}e^{i\omega t_2}) - (ae^{-i\omega t_2}+{a^\dagger}e^{i\omega t_2})(ae^{-i\omega t_1}+{a^\dagger}e^{i\omega t_1}) \right] \\
\\
\text{Let } \Delta t = t_2 - t_1 &\Rightarrow - \Delta t = t_1 - t_2 \\
t_3 &= t_1 + t_2 \\
\\
&=\frac{\hbar}{2m\omega} \left[(a^2 e^{-i\omega t_3} + {a^\dagger}ae^{-i\omega \Delta t} + a{a^\dagger}e^{i\omega \Delta t} + {a^\dagger}^2 e^{i\omega t_3}) - (a^2 e^{-i\omega t_3} +{a^\dagger}ae^{i\omega \Delta t} + a{a^\dagger}e^{-i\omega \Delta t} + {a^\dagger}^2 e^{i\omega t_3}) \right] \\
&= \frac{\hbar}{2m\omega} \left[(a^2 - a^2)e^{-i\omega t_3} + {a^\dagger}a (e^{i\omega \Delta t}-e^{-i\omega \Delta t}) - a{a^\dagger}(e^{i\omega \Delta t}-e^{-i\omega \Delta t} + ({a^\dagger}^2 - {a^\dagger}^2) e^{i\omega t_3})\right] \\
&= \frac{\hbar}{2m\omega} \left[{a^\dagger}a - a{a^\dagger}\right] (e^{-i\omega \Delta t}-e^{-i\omega \Delta t}) \\
&= \frac{i\hbar}{m\omega}\sin{(\omega (t_2 - t_1))} \\
\end{aligned}$$

\pagebreak

# Question 2

> Consider a particle that behaves like a $1$-D H.O. but now add the complication that the particle is charged and inside a uniform electric field $\mathcal{E}$ along the $x$-axis.

## Part A

> Find the allowed energy levels and corresponding eigenfunctions.

If the particle has a charge $q$ in the electric field $\mathcal{E}$, then the force on the particle is given by $q\mathcal{E}\hat{x}$. Integrating, we obtain the work done by the field on the particle as $q\mathcal{E}x$. We can then perturb the regular $1$-D HO with this additional potential energy term: $$H = \frac{p^2}{2m}+\frac{m\omega^2}{2}x^2 + q\mathcal{E}x$$

Grouping position operators together, we can complete the square of the form $x^2 +2bx$ where $b\equiv \frac{q\mathcal{E}}{m\omega^2}$:

$$V(x) = x^2 + 2\frac{q\mathcal{E}}{m\omega^2}x \qquad\qquad \begin{aligned}
x^2+2bx &= 0\\
x^2 +2bx +b^2 - b^2 &=0\\
(x+b)^2 -b^2 &= 0\\
\end{aligned}$$

We then rewrite the Hamiltonian and proceed to represent it in an indentical dimensionless form as we did when solving analytically in the coordinate basis:

$$H = \frac{p^2}{2m}+\frac{m\omega^2}{2}(x+b)^2 - \frac{m\omega^2}{2} b^2, \qquad \xi\equiv\alpha x,\ \alpha\equiv\sqrt{\frac{m\omega}{\hbar}},\ \lambda\equiv \frac{2E}{\hbar\omega}$$

$$\begin{aligned}
-\frac{\hbar^2}{2m}\frac{d^2 \psi}{dx^2} + \left(\frac{m\omega^2}{2}(x+b)^2 - \left(\frac{m\omega^2}{2} b^2 + E\right)\right)\psi &= 0 \\
-\frac{\hbar}{m\omega}\frac{d^2 \psi}{dx^2} + \left(\frac{m\omega}{\hbar}(x+b)^2 - \left(\frac{m\omega}{\hbar} b^2 + \frac{2E}{\hbar\omega}\right)\right)\psi &= 0 \\
\\
\text{Let } x^\prime = x+b &\Rightarrow \xi^\prime = \alpha x^\prime\\
\lambda^\prime &= \lambda + \frac{m\omega}{\hbar} b^2 \\
\\
-\frac{1}{\alpha^2}\frac{d^2 \psi}{d(x^\prime)^2} + \left(\alpha^2(x^\prime)^2 - \lambda^\prime\right)\psi &= 0 \\
-\frac{d^2 \psi}{d(\xi^\prime)^2} + \left((\xi^\prime)^2 - \lambda^\prime\right)\psi &= 0 \\
\end{aligned}$$

Noting that we have indeed obtained the same linear second order ODE, we just need to substitute the translation into the energy values and eigenfunctions. Recall that $\lambda = 2n + 1$ and that $2n+1=\lambda =\frac{2E}{\hbar\omega}$, $\lambda^\prime$ is now the value that needs to cause the infinite series to terminate:

$$\begin{aligned}
\lambda^\prime &= 2n + 1 = \frac{2E}{\hbar\omega} + \frac{m\omega}{\hbar} \left(\frac{q\mathcal{E}}{m\omega^2}\right)^2\\
2E &= 2\hbar\omega \left(n+\frac{1}{2}\right) - \frac{m\hbar\omega^2}{\hbar} \left(\frac{q^2\mathcal{E}^2}{m^2\omega^4}\right) \\
E_n &= \hbar\omega \left(n+\frac{1}{2}\right) - \frac{q^2\mathcal{E}^2}{2m\omega^2}
\end{aligned}$$

And $$\psi_n(\xi) = \frac{\alpha^{1/2}}{\pi^{1/4}}\frac{1}{\sqrt{2^n n!}} H_n \left(\xi\right) \exp{\left(-\frac{\xi^2}{2}\right)}$$

$$\begin{aligned}
\psi_n(\xi^\prime) &= \frac{\alpha^{1/2}}{\pi^{1/4}}\frac{1}{\sqrt{2^n n!}} H_n \left(\xi^\prime\right) \exp{-\frac{(\xi^\prime)^2}{2}}\\
\psi_n(x) &= \left(\frac{m\omega}{\pi\hbar}\right)^{\frac{1}{4}} \frac{1}{\sqrt{2^n n!}} H_n \left(\sqrt{\frac{m\omega}{\hbar}}\left(x+\frac{q\mathcal{E}}{m\omega^2}\right)\right) \exp{\left(-\frac{\frac{m\omega}{\hbar}(x+\frac{q\mathcal{E}}{m\omega^2})^2}{2}\right)}\\
\end{aligned}$$

Which is just the translation we expected to see.

## Part B

> At $t<0$ the particle is in the ground state. At $t=0$, the field is suddenly turned off. What is the probability to find the particle in the ground state and in the first excited state?

If we recall the Heisenberg picture, a coherent state (for a harmonic oscillator) is just the harmonic oscillator translated a finite distance: this is exactly what we showed in Part A. Therefore, if we treat the HO + field ground state as a coherent state for the Heisenberg picture of an unperturbed HO, we can use the property that at $t=0$, $\hat{A}_H = \hat{A}_S$, to bypass time evolution and simplify the projection from the perturbed system to the unperturbed by using Equation 2.175 from Page 90 of Sakurai:

$$\mathcal{P_n} = \left(\frac{\bar{n}^n}{n!}\right)\exp{(-\bar{n})}$$

Remember that the linear momentum operator is the generator of translations in coordinate space, and the unitary operation takes the form: $\hat{U}_{\Delta x}=\exp{\left(-\frac{i \hat{p}_x \Delta x^\prime}{\hbar}\right)}$ and the energy eigenket for the perturbed system can then be represented by the translation from the unperturbed system: $\ket{0}_\mathcal{E} = \hat{U}_{\Delta x} \ket{0}$. We then note that the mean value $\bar{n}$ for the Poisson distrubtion is proportional to the translation $\Delta x^\prime$ which we found in Part A as: $b= \frac{q\mathcal{E}}{m\omega^2}$. More explictly:

$$\begin{aligned}
\ket{0}_\mathcal{E} &= \exp{\left(-\frac{i \hat{p}_x \Delta x^\prime}{\hbar}\right)}\ket{0} \\
&= \exp{\left(-\frac{i}{\hbar} i\sqrt{\frac{m\hbar\omega}{2}}(-a+{a^\dagger})\frac{q\mathcal{E}}{m\omega^2}\right)}\ket{0} \\
&= \exp{\left(\frac{\alpha}{\sqrt{2}}b(-a+{a^\dagger})\right)}\ket{0} \\
\end{aligned}$$

Then using the Baker-Campbell-Hausdorff theorem which states that the commutation relation for two operators whose commutator commutes with each operator: $\hat{A}$ and $\hat{B}$, $[\hat{A},[\hat{A},\hat{B}]]=[\hat{B},[\hat{A},\hat{B}]]=0$ has the identity:

$$\exp{\hat{A}+\hat{B}} = \exp{\hat{A}}\exp{\hat{B}}\exp{\left(\frac{[\hat{A},\hat{B}]}{2}\right)}$$

And since $[-\hat{a},\hat{a}^\dagger]=-\hat{a}\hat{a}^\dagger + \hat{a}^\dagger \hat{a} = - (1 + N) + N = -1$, we can conclude through inspection that both $\hat{a}$ and $\hat{a}^\dagger$ will commute with the negative of the Identity operator. Also recall that $[c\hat{A},c\hat{B}] = c^2 [\hat{A}, \hat{B}]$:

$$\begin{aligned}
\ket{0}_\mathcal{E} &= \exp{\left(\frac{\alpha}{\sqrt{2}}b(-a)\right)}\exp{\left(\frac{\alpha}{\sqrt{2}}b{a^\dagger}\right)}\exp{\left(\frac{\alpha^2}{2}b^2 \left(\frac{[-a,a^\dagger]}{2}\right)\right)}\ket{0} \\
&= \exp{\left(\frac{\alpha}{\sqrt{2}}b(-a)\right)}\exp{\left(\frac{\alpha}{\sqrt{2}}b{a^\dagger}\right)}\exp{\left(-\frac{\alpha^2}{4}b^2\right)}\ket{0} \\
\end{aligned}$$

Now we can proceed with expressing $\ket{0}_\mathcal{E}$ in the unpeturbed basis by inserting the completeness relation and then considering each coefficient:

$$\left(\sum_{n=0}^{\infty}{\ket{n}\bra{n}}\right)\ket{0}_\mathcal{E} = \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\sum_{n=0}^{\infty}{\left(\bra{n}\exp{\left(\frac{\alpha}{\sqrt{2}}b(-a)\right)}\exp{\left(\frac{\alpha}{\sqrt{2}}b{a^\dagger}\right)}\ket{0}\right) \ket{n}}$$

$$\begin{aligned}
c_n &= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\bra{n}\exp{\left(\frac{\alpha}{\sqrt{2}}b(-a)\right)}\exp{\left(\frac{\alpha}{\sqrt{2}}b{a^\dagger}\right)}\ket{0} \\
&= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\bra{n} \left(\sum_{j=0}^{\infty}{\frac{\alpha}{\sqrt{2}}b\frac{{a^\dagger}^j}{j!} }\right)\left(\sum_{k=0}^{\infty}{\frac{\alpha}{\sqrt{2}}b\frac{(-1)^k {a^\dagger}^k}{k!} }\right) \ket{0} \\
\end{aligned}$$

Using that the annihilation operator acting on $\ket{0}$ terminates the sequence, any power of $k>0$ gives the value of $0$, and so the power series acting on $\ket{0}$ is of finite length (just $1$ term and $\infty$'ly many $0$s). Also recall that the $m$-th energy eigenket can be represented as $m$ operations of the creation operator on $\ket{0}$ as shown in Equation 2.142 (page 86 of Sakurai).

$$\begin{aligned}
c_n &= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\bra{n} \left(\sum_{j=0}^{\infty}{\left(\frac{\alpha}{\sqrt{2}}b \right)^j \frac{{a^\dagger}^j}{j!} }\right)\left(\sum_{k=0}^{\infty}{\left(\frac{\alpha}{\sqrt{2}}b \right)^k \frac{(-1)^k {a}^k}{k!} }\right) \ket{0} \\
&= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\bra{n} \left(\sum_{j=0}^{\infty}{\left(\frac{\alpha}{\sqrt{2}}b \right)^j \frac{{a^\dagger}^j}{j!} }\right)\left((1)*\mathbb{I} + 0 + ... \right) \ket{0} \\
&= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\bra{n} \left(\sum_{j=0}^{\infty}{\left(\frac{\alpha}{\sqrt{2}}b \right)^j \frac{1}{j!} {a^\dagger}^j\ket{0} }\right) \\
&= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\bra{n} \left(\sum_{j=0}^{\infty}{\left(\frac{\alpha}{\sqrt{2}}b \right)^j \frac{1}{j!} \sqrt{j!}\ket{j} }\right) \\
&= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\left(\sum_{j=0}^{\infty}{\left(\frac{\alpha}{\sqrt{2}}b \right)^j \frac{1}{\sqrt{j!}} \braket{n}{j} }\right) \\
&= \exp{\left(-\frac{\alpha^2}{4}b^2\right)}\left(\frac{\alpha}{\sqrt{2}}b \right)^n \frac{1}{\sqrt{n!}}\\
\end{aligned}$$

Which gives us the Poisson distribution we expected for a coherent state, along with $\bar{n}=\left(\frac{\alpha}{\sqrt{2}}b \right)^2=\frac{q^2\mathcal{E}^2}{2\hbar m \omega^3}$:

$$\mathcal{P_n} = {\lvert c_n \rvert}^2 = \exp{\left(-\left(\frac{\alpha}{\sqrt{2}}b\right)^2\right)}\left(\frac{\alpha}{\sqrt{2}}b \right)^2n \frac{1}{n!}$$

And finally, we calculate the probabilities of the charged particle being in the unpeturbed ground and first excited states after the field is turned off (at $t=0$):

$$P_0 = \exp{\left(-\frac{q^2\mathcal{E}^2}{2\hbar m \omega^3}\right)}, \qquad P_1 = \frac{q^2\mathcal{E}}{2\hbar m \omega^3}\exp{\left(-\frac{q^2\mathcal{E}^2}{2\hbar m \omega^3}\right)}$$
