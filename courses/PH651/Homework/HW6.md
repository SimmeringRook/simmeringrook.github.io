---
title: Homework 6
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Wednesday, November 10, 2021
papersize: a4
geometry: margin=2cm
output:
  pdf_document:
    toc: true
    toc_depth: 2
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

\pagebreak

# Question 1

> Show that $[\vec{R}\cdot\vec{P}, H]= 2i\hbar T - i\hbar \vec{R}\cdot \nabla V$, where $\vec{R}$ is the position operator in 3D space, $\vec{P}$ is the momentum operator, $H$ is the Hamilotnian ($H=\vec{P}^2 /2m + V(\vec{R})$), and $T$ is the kinetic energy operator ($T=\vec{P}^2 /2m$).

Recall that the commutator is both anti-symmetric and distributes following $[A, BC] = [A,B]C + B[A,C]$, therefore $[\vec{R}\cdot\vec{P}, H]$ can be expanded as $-[A, BC]$:

$$\begin{aligned}
[\vec{R}\cdot\vec{P}, H] &= - [H, \vec{R}\cdot\vec{P}] \\
&= -([H,\vec{R}]\cdot\vec{P} + \vec{R}\cdot[H,\vec{P}]) \\
&= [\vec{R}, H]\cdot\vec{P} + \vec{R}\cdot[\vec{P}, H]
\end{aligned}$$

Next, recall that an operator and the function of an operator commute, $[A, F(A)]=0$, and so we can simplify the commutator of $[\vec{R}, H]$ first:

$$\begin{aligned}
[\vec{R}, H] &= \frac{1}{2m} [\vec{R}, \vec{P}^2] + \underbrace{[\vec{R}, V(\vec{R})]}_{0} \\
&= \frac{1}{2m} \left(\underbrace{[\vec{R}, \vec{P}]}_{i\hbar}\vec{P} + \vec{P}\underbrace{[\vec{R}, \vec{P}]}_{i\hbar}\right)\\
&= 2i\hbar \left(\frac{\vec{P}}{2m}\right)
\end{aligned}$$

Then, remembering that position commutes with momentum for any orthogonal direction ($[x_k, p_j] = 0, \quad k\neq j$), we examine $[p_j, \vec{R}]$ and generalize our results:

$$\begin{aligned}
[p_j, \vec{R}] &= [p_j, R_j] \hat{e}_j \\
&= -i\hbar \left(\frac{\partial R_j}{\partial R_j}\right) \hat{e}_j\\
\\
[p_j, V(\vec{R})] &= -i\hbar \left(\frac{\partial V(\vec{R})}{\partial R_j}\right) \\
[\vec{P}, V(\vec{R})] &= \sum_{j}{-i\hbar \left(\frac{\partial V(\vec{R})}{\partial R_j}\right)\hat{e}_j} \\
&= -i\hbar \nabla V(\vec{R})
\end{aligned}$$

Substituting these results back into the original commutator, we obtain the desired outcome:

$$\begin{aligned}
[\vec{R}\cdot\vec{P}, H] &= \underbrace{[\vec{R}, H]}_{ 2i\hbar \left(\frac{\vec{P}}{2m}\right) }\cdot\vec{P} + \vec{R}\cdot\underbrace{[\vec{P}, H]}_{-i\hbar \nabla V(\vec{R})} \\
&= 2i\hbar T - i\hbar \vec{R}\cdot\nabla V(\vec{R})
\end{aligned}$$

\pagebreak

# Question 2

> A particle of mass $m$, which moves inside an infinite 1D potential well of length $a$, is described by the following wave function at $t=0$: $$\psi(x,0) \dot{=} \frac{A}{\sqrt{a}} \sin{\left(\frac{\pi x}{a}\right)} + \sqrt{\frac{3}{5a}} \sin{\left(\frac{3\pi x}{a}\right)} + \sqrt{\frac{1}{5a}} \sin{\left(\frac{5\pi x}{a}\right)},$$ where $A$ is a real constant.

\newcommand{\iswef}[1]{{ \sqrt{\frac{2}{a}} \sin{ \left( \frac{#1 \pi x}{a} \right) } }}

First, recall that for the `particle-in-a-box` system[^1], the $n$-th energy eigenfunction is defined as:

[^1]: Also referred to as the `infinite square well`.

$$\ket{\varphi_n} \dot{=} \varphi_n (x) \equiv \iswef{n}$$

Rewriting $\psi(x,0)$ in terms of eigenfunctions, we obtain:

$$\begin{aligned}
\psi(x,0) &= \frac{1}{\sqrt{2}} \left(A \iswef{ } + \sqrt{\frac{3}{5}}\iswef{3} + \sqrt{\frac{1}{5}}\iswef{5} \right) \\
&= \frac{A}{\sqrt{2}} \varphi_1 (x) + \sqrt{\frac{3}{10}} \varphi_3 (x) + \sqrt{\frac{1}{10}} \varphi_5 (x)
\end{aligned}$$

## Part A

> Find $A$ so that $\psi(x,0)$ is normalized.

Recall that these energy eigenfunctions are orthogonal, $$\int_{0}^{a}{{\varphi_m}^* (x) \varphi_n (x) dx} = \delta_{m,n},$$ so normalizing $\psi(x,0)$ is very straightforward after simplifying its representation:

$$\begin{aligned}
1 &= \int_{0}^{a}{ {\psi}^* (x,0) \psi(x,0) dx} \\
&= \frac{A^2}{2} + \frac{3}{10} + \frac{1}{10} \\
10 &= 5A^2 + 4 \\
A &= \sqrt{\frac{6}{5}}
\end{aligned}$$

$$\psi(x,0) = \sqrt{ \frac{6}{10} } \varphi_1 (x) + \sqrt{\frac{3}{10}} \varphi_3 (x) + \sqrt{\frac{1}{10}} \varphi_5 (x)$$

## Part B

> If measurements of the energy are carried out at $t=0$, what are the values that will be found and what are the corresponding probabilities?

The wave function, at $t=0$, is just a superposition of three energy eigenfunctions: $\varphi_1 (x)$, $\varphi_3 (x)$, and $\varphi_5 (x)$; therefore the only possible energy measurements that can be obtained are the energy (eigen)values corresponding to these states, given by $$E_n = \frac{n^2 \pi^2 \hbar^2}{2ma^2}$$

+-------+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
| $n$   | $E_n$                             | $\mathcal{P}_{E_n}$                                                                                                       |
+:=====:+:==================================+:==========================================================================================================================+
| $1$   | $$\frac{\pi^2 \hbar^2}{2ma^2}$$   | $${\lvert \int_{0}^{a}{ {\varphi_1}^* (x) \psi(x,0) dx}\rvert}^2 = {\lvert \sqrt{\frac{6}{10}} \rvert}^2 = \frac{6}{10}$$ |
+-------+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
| $3$   | $$\frac{9\pi^2 \hbar^2}{2ma^2}$$  | $${\lvert \int_{0}^{a}{ {\varphi_3}^* (x) \psi(x,0) dx}\rvert}^2 = {\lvert \sqrt{\frac{3}{10}} \rvert}^2 = \frac{3}{10}$$ |
+-------+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
| $5$   | $$\frac{25\pi^2 \hbar^2}{2ma^2}$$ | $${\lvert \int_{0}^{a}{ {\varphi_5}^* (x) \psi(x,0) dx}\rvert}^2 = {\lvert \sqrt{\frac{1}{10}} \rvert}^2 = \frac{1}{10}$$ |
+-------+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+

A quick sanity check reveals that all three probabilities sum to unity and we reaffirm our confidence in the correctness of these results.

## Part C

> What is the average energy?

The average value of energy that will be measured from states prepared as $\psi(x,0)$ will be:

$$\begin{aligned}
\expectation{H} &= \sum_{j}{\mathcal{P}_{E_j} E_j}, \qquad j=1,3,5 \\
&= \frac{6}{10}\left(\frac{\pi^2 \hbar^2}{2ma^2}\right) + \frac{3}{10}(9)\left(\frac{\pi^2 \hbar^2}{2ma^2}\right) + \frac{1}{10}(25)\left(\frac{\pi^2 \hbar^2}{2ma^2}\right) \\
&= \left(\frac{6+27+25}{10}\right)\frac{\pi^2 \hbar^2}{2ma^2} \\
&= \frac{58}{10} \frac{\pi^2 \hbar^2}{2ma^2}
\end{aligned}$$

## Part D

> Find the wave function $\psi(x,t)$ at a later time $t$.

Since the prompt doesn't specify a specific picture, let us proceed with Schrödinger time evolution. Recall that for a state already represented in the energy basis, this corresponds to multiplying each eigenstate by a time-dependent complex phase for the respective energy: $\ket{\xi} = \sum_{n}{ c_n(0) \exp{\left(-\frac{i E_n t}{\hbar}\right)} \ket{E_n} }$. Applying this to $\psi$, we obtain:

$$\psi(x,t) = \sqrt{ \frac{6}{10} } \exp{\left(-\frac{i E_1 t}{\hbar}\right)} \varphi_1 (x) + \sqrt{\frac{3}{10}} \exp{\left(-\frac{i E_3 t}{\hbar}\right)} \varphi_3 (x) + \sqrt{\frac{1}{10}} \exp{\left(-\frac{i E_5 t}{\hbar}\right)} \varphi_5 (x)$$

## Part E

> Determine the probability of finding the system, at a time $t$, in the state of $$\varphi (x,t) = \iswef{5}\exp{\left(-\frac{i E_5 t}{\hbar}\right)}$$

Note that the time-dependent state vector obtained in Part D does not contain probability amplitudes that change with time and so the answer is $1/10$.

$$\begin{aligned}
\mathcal{P}_{E_5,\ t=t} &= {\left\lvert \int_{0}^{a}{ {\varphi_5}^* (x,t) \psi(x,t) dx} \right\rvert}^2 \\
&= {\left\lvert \sqrt{\frac{1}{10}} \right\rvert}^2 = \frac{1}{10}
\end{aligned}$$

## Part F

> Same as Part E, but for $$\chi (x,t) = \iswef{2}\exp{\left(-\frac{i E_2 t}{\hbar}\right)}$$

Recall the results from Part B: $c_2 = 0$ and Part E: the probabilities are time independent; therefore, for any time $t$, the probability of $\psi(x,t)$ being in the eigenstate of $\chi(x,t)$ is $0$.

\pagebreak

# Question 3: Sakurai 2.10

> Let $\ket{a^\prime}$ and $\ket{a^\pprime}$ be eignestates of a Hermitian operator $A$ with eigenvalues $a^\prime$ and $a^\pprime$, respectively ($a^\prime \neq a^\pprime$). The Hamiltonian operator is given by $$H = \ket{a^\prime} \delta \bra{a^\pprime} + \ket{a^\pprime} \delta \bra{a^\prime},$$ where $\delta$ is just a real number.

## Part A

> Clearly, $\ket{a^\prime}$ and $\ket{a^\pprime}$ are not eigenstates of the Hamiltonian. Write down the eigenstates of the Hamiltonian. What are their energy eigenvalues?

Since $A$ is Hermitian and we are given $H$ in $A$'s basis, we can use the knowledge that $A$ is diagonal in its own basis to find simple matrix representations for the basis kets, $$\ket{a^\prime} \dot{=} \begin{pmatrix} 1 \\ 0 \end{pmatrix}\qquad\text{and}\qquad \ket{a^\pprime} \dot{=} \begin{pmatrix} 0 \\ 1 \end{pmatrix},$$ such that they are orthogonal and normalized. Then, we rewrite the Hamiltonian in this representation and solve the eigenvalue equation:

$$\begin{aligned}
H\ &\dot{=} \begin{pmatrix} 1 \\ 0 \end{pmatrix} \delta \begin{pmatrix} 0 & 1 \end{pmatrix} + \begin{pmatrix} 0 \\ 1 \end{pmatrix} \delta \begin{pmatrix} 1 & 0 \end{pmatrix} \\
&= \begin{pmatrix} 0 & \delta \\ \delta & 0 \end{pmatrix}
\end{aligned}$$

Eigenvalues:

$$\begin{aligned}\begin{vmatrix} -\lambda & \delta \\ \delta & -\lambda \end{vmatrix} &= \lambda^2 - \delta ^2 = 0 \\ \lambda &= \pm\delta\end{aligned}$$

Eigenvectors:

$$\begin{pmatrix} 0 & \delta \\ \delta & 0 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \pm\delta \begin{pmatrix} x \\ y \end{pmatrix}$$

$$\begin{aligned}
y &= \pm x \\
x &= \pm y \\
\\
\text{choose: } x &= 1\\
y&= \pm 1
\end{aligned}$$

$$\ket{+\delta} \dot{=} \sqrt{\frac{1}{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix} \qquad\text{and}\qquad \ket{-\delta} \dot{=} \sqrt{\frac{1}{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix}$$

\pagebreak

## Part B

> Suppose the system is known to be in state $\ket{a^\prime}$ at $t=0$. Write down the state vector in the Schrödinger picture for $t>0$.

Before we can time evolve, we need to find the superposition of energy eigenstates to represent $\ket{a^\prime}$. Using the completeness relation, we find:

$$\begin{aligned}
\ket{\psi;t=0} &= \ket{a^\prime}\\
&= \bigg( \ket{+\delta}\bra{+\delta} + \ket{-\delta}\bra{-\delta} \bigg) \ket{a^\prime}\\
&= \braket{+\delta}{a^\prime}\ket{+\delta} + \braket{-\delta}{a^\prime}\ket{-\delta}\\
\\
\braket{+\delta}{a^\prime}\ &\dot{=} \sqrt{\frac{1}{2}} \begin{pmatrix} 1 & 1 \end{pmatrix} \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \sqrt{\frac{1}{2}} \\
\braket{-\delta}{a^\prime}\ &\dot{=} \sqrt{\frac{1}{2}} \begin{pmatrix} 1 & -1 \end{pmatrix} \begin{pmatrix} 1 \\ 0 \end{pmatrix} = \sqrt{\frac{1}{2}} \\
\\
\ket{\psi;t=0} &= \braket{+\delta}{a^\prime}\ket{+\delta} + \braket{-\delta}{a^\prime}\ket{-\delta} \\
&= \sqrt{\frac{1}{2}} \bigg(\ket{+\delta} + \ket{-\delta}\bigg)\\
\\
\text{time evolve:}&\\
\ket{\psi;t} &= \sqrt{\frac{1}{2}} \left(\exp{\left(-\frac{i \delta t}{\hbar}\right)}\ket{+\delta} + \exp{\left(\frac{i \delta t}{\hbar}\right)}\ket{-\delta}\right)
\end{aligned}$$

## Part C

> What is the probability for finding the system in $\ket{a^\pprime}$ for $t>0$ if the system is known to be in state $\ket{a^\prime}$ at $t=0$?

$$\begin{aligned}
P_{a^\pprime} &= \bigg(\ket{a^\pprime}\bra{a^\pprime}\bigg)\ket{\psi;t} \\
\\
\braket{a^\pprime}{+\delta}\ &\dot{=} \sqrt{\frac{1}{2}} \begin{pmatrix} 0 & 1 \end{pmatrix} \begin{pmatrix} 1 \\ 1 \end{pmatrix} = \sqrt{\frac{1}{2}} \\
\braket{a^\pprime}{-\delta}\ &\dot{=} \sqrt{\frac{1}{2}} \begin{pmatrix} 0 & 1 \end{pmatrix} \begin{pmatrix} 1 \\ -1 \end{pmatrix} = -\sqrt{\frac{1}{2}} \\
\\
&= \sqrt{\frac{1}{2}} \left(\exp{\left(-\frac{i \delta t}{\hbar}\right)}\braket{a^\pprime}{+\delta} + \exp{\left(\frac{i \delta t}{\hbar}\right)}\braket{a^\pprime}{-\delta}\right)\ket{a^\pprime} \\
&= \frac{1}{2} \left(\exp{\left(-\frac{i \delta t}{\hbar}\right)} - \exp{\left(\frac{i \delta t}{\hbar}\right)}\right)\ket{a^\pprime} \\
&= - \underbrace{\frac{1}{2} \left(\exp{\left(\frac{i \delta t}{\hbar}\right)} - \exp{\left(\frac{-i \delta t}{\hbar}\right)}\right)}_{ i\sin{\left(\frac{\delta t}{\hbar}\right)} }\ket{a^\pprime} \\
&= - i\sin{\left(\frac{\delta t}{\hbar}\right)} \ket{a^\pprime}
\end{aligned}$$

$$\begin{aligned}
\mathcal{P}_{a^\pprime} &= {\left\lvert \braket{a^\pprime}{\psi ;t} \right\rvert}^2 \\
&= \sin^2{\left(\frac{\delta t}{\hbar}\right)}
\end{aligned}$$

At $t=0$, we recover the initial state of $\ket{a^\prime}$ as expected.

## Part D

> Can you think of a physical situation corresponding to this problem?

A spin-1/2 system where the Hamiltonian describes spin with respect to a uniform magnetic field in the $x$ direction and the operator $A$ corresponds to spin-1/2 in the $z$ direction; this question then describes the precision of spin for this particle.

\pagebreak

# Question 4

> Consider a particle of mass $m$ in the 1-D potential well given by $V(x) = 0$ if $\lvert x \rvert <a$ and $V(x) = +\infty$ if $\lvert x \rvert > a$. Let's say that the particle is in the ground state (i.e. in the state with the lowest energy). Suddenly, the well symmetrically expands to twice its size. What is the probability to find the particle in the ground state of this new well?

Recall the ground state for the infinite square well with width $2a$ and centered about the origin is given as:

$$\varphi_1 (x) = \frac{1}{\sqrt{a}}\sin{\left(\frac{\pi (x+a)}{2a}\right)}$$

If we assume that the symmetric expansion of the well doesn't effect the wave function other than as a projection into a slightly different energy basis, then we can find the resulting superposition of energy eigenfunctions through the completeness relation for the new basis[^2] and the addition of two Heaviside functions to the original ground state.

$${\varphi_m}^\prime (x) = \frac{1}{\sqrt{2a}}\sin{\left(\frac{m\pi (x+2a)}{4a}\right)}$$
$$\varphi_1 (x) = \frac{1}{\sqrt{a}}\sin{\left(\frac{\pi (x+a)}{2a}\right)}\bigg(\Theta(x+a)-\Theta(x-a)\bigg)$$

[^2]: Recall that the limits of integration will come from the space we are projecting into: $[-2a,2a]$ and not the space where the wave function currently is: $[-a,a]$.

$$\begin{aligned}
\ket{\psi} &= \ket{\varphi_1} \\
\ket{\psi^\prime} &= \sum_{m=odd}^{\infty}{\ket{{\varphi_m}^\prime}\braket{{\varphi_m}^\prime}{\psi}} \\
\\
\braket{{\varphi_m}^\prime}{\varphi_1} &= \int_{-2a}^{2a}{ \left(\sqrt{\frac{1}{2a}}\sin{\left(\frac{m\pi (x+2a)}{4a}\right)}\right)\left(\sqrt{\frac{1}{a}}\sin{\left(\frac{\pi (x+a)}{2a}\right)}\right)\bigg(\Theta(x+a)-\Theta(x-a)\bigg) dx} \\
&= \frac{1}{a\sqrt{2}} \int_{-a}^{a}{ \sin{\left(\frac{m\pi x}{4a} + \frac{m\pi}{2}\right)} \sin{\left(\frac{\pi x}{2a} + \frac{\pi}{2}\right)} dx}
\end{aligned}$$

Using the sum formula for sine, we can simplify the integrand for two general cases:

$$
\begin{aligned}
\sin{(\alpha + \beta)} &= \sin{\alpha}\cos{\beta} + \cos{\alpha} \sin{\beta} \\
\\
\sin{\left(\frac{\pi x}{2a} + \frac{\pi}{2}\right)} &= \sin{\left(\frac{\pi x}{2a}\right)}\cos{\frac{\pi}{2}} + \cos{\left(\frac{\pi x}{2a}\right)}\sin{\frac{\pi}{2}} \\
&= \cos{\left(\frac{\pi x}{2a}\right)}\\
\\
\sin{\left(\frac{m\pi x}{4a} + \frac{m\pi}{2}\right)} &= \sin{\left(\frac{m\pi x}{4a}\right)}\cos{\frac{m\pi}{2}} + \cos{\left(\frac{m\pi x}{4a}\right)}\sin{\frac{m\pi}{2}} \\
\text{for odd m } &\rightarrow \cos{\frac{m\pi}{2}} = 0, \quad \sin{\frac{m\pi}{2}} = 1 \\
&\Rightarrow \cos{\left(\frac{m\pi x}{4a}\right)}\\
\text{for even m } &\rightarrow \cos{\frac{m\pi}{2}} = 1, \quad \sin{\frac{m\pi}{2}} = 0 \\
&\Rightarrow \sin{\left(\frac{m\pi x}{4a}\right)}\\
\end{aligned}$$

This allows us to rewrite the integrand in a cleaner form:

$$\begin{aligned}
m\in(2\mathbb{Z}),\quad \braket{{\varphi_m}^\prime}{\varphi_1} &= \frac{1}{a\sqrt{2}} \int_{-a}^{a}{ \sin{\left(\frac{m\pi x}{4a}\right)} \cos{\left(\frac{\pi x}{2a}\right)} dx} \\
m\in(2\mathbb{Z}+1),\quad \braket{{\varphi_m}^\prime}{\varphi_1} &= \frac{1}{a\sqrt{2}} \int_{-a}^{a}{ \cos{\left(\frac{m\pi x}{4a}\right)} \cos{\left(\frac{\pi x}{2a}\right)} dx} \\
\end{aligned}$$

We can disregard the '$m$ is even' set of solutions as: $\cos{nx}$ is orthogonal to $\sin{mx}$ for all integer values of $n,m$ (i.e. the 'Harmonic Integrals' or more commonly known as the basis for Fourier Series) and due to the parity of the potential ($V(x)$ is symmetric $\Rightarrow$ $V(x)$ is even $\Rightarrow$ $V(x)$ will only permit even wave functions). We can proceed with the odd integer solutions of $m$ by using a $u$-substitution and referencing an integral table.

$$\begin{aligned}
\text{let } u &= \frac{\pi x}{4a} \Rightarrow du = \frac{\pi}{4a}dx \\
u &\in \left[-\frac{\pi}{4}, \frac{\pi}{4}\right] \\
\\
&= \frac{4a}{a\pi\sqrt{2}} \int_{-\pi/4}^{\pi/4}{ \cos{(mu)} \cos{(2u)} du}
\end{aligned}$$

Consulting the integral table at the back of D. McIntyre's *Quantum Mechanics*, we find Equation F.2:

$$\int{\cos{mx}\cos{nx} dx} = \frac{\sin{((m-n)x)}}{2(m-n)} + \frac{\sin{((m+n)x)}}{2(m+n)}, \quad m^2 \neq n^2$$

$$\begin{aligned}
\braket{{\varphi_m}^\prime}{\varphi_1} &= \frac{4a}{a\pi\sqrt{2}} \left[ \frac{\sin{((m-2)u)}}{2(m-2)} + \frac{\sin{((m+2)u)}}{2(m+2)} \right]_{u=-\pi/4}^{u=\pi/4} \\
&= \frac{2\sqrt{2}}{\pi} \left[ \left(\frac{\sin{\left(\frac{\pi m}{4} - \frac{\pi}{2} \right)}}{2m-4} + \frac{\sin{\left(\frac{\pi m}{4} + \frac{\pi}{2} \right)}}{2m+4}\right) - \left(\frac{\sin{\left(-\frac{\pi m}{4} + \frac{\pi}{2} \right)}}{2m-4} + \frac{\sin{\left(-\frac{\pi m}{4} - \frac{\pi}{2} \right)}}{2m+4}\right) \right] \\
\\
\sin(x\pm \pi/2) &= \pm\cos(x)\\
\sin(-x) &= -\sin(x)\\
\\
&= \frac{2\sqrt{2}}{\pi}  \left[ \left(\frac{-1}{2m-4} + \frac{1}{2m+4}\right) + \left(\frac{-1}{2m-4} + \frac{1}{2m+4}\right) \right]\cos{\left(\frac{\pi m}{4}\right)} \\
&= \frac{2\sqrt{2}}{\pi}  \left[ \frac{1}{m+2} - \frac{1}{m-2} \right] \cos{\left(\frac{\pi m}{4}\right)} \\
&= -\frac{2\sqrt{2}}{\pi}  \left[ \frac{4}{m^2-4} \right] \cos{\left(\frac{\pi m}{4}\right)} \\
&= -\frac{ 8\sqrt{2} }{ \pi(m^2-4) } \cos{\left(\frac{\pi m}{4}\right)} \\
\text{for } &\begin{cases} m=1,5,9..., \quad &\cos{\left(\frac{\pi m}{4}\right)} = +\frac{1}{\sqrt{2}} \\ m=3,7,11..., \quad &\cos{\left(\frac{\pi m}{4}\right)} = -\frac{1}{\sqrt{2}} \end{cases}
\end{aligned}$$

$$\braket{{\varphi_m}^\prime}{\varphi_1} = \frac{(-1)^{m-1} 8}{ \pi(m^2-4) }, \qquad m\in(2\mathbb{Z^+} +1),\ m>0$$

Since we are projecting into a non-degenerate basis, we are guaranteed that the transformation to $\ket{\psi^\prime}$ will be normalized, as $\ket{\psi}$ was normalized to start with. Therefore, the probability of being in the ground state for this new potential is straightforward:

$$\mathcal{P}_{E_1} = {\left\lvert \braket{{\varphi_1}^\prime}{\psi^\prime} \right\rvert}^2 = {\left\lvert \frac{8}{ \pi(-3) } \right\rvert}^2 = \frac{64}{9\pi^2} \approx 0.72$$

## Verifying the Projected State Vector is Normalized

To verify work accomplished by hand, the following Mathematica code was used to verify the results of calculations:

> $\ $

### 1. Defining the energy eigenfunctions

```Mathematica
$Assumptions = a > 0 && a \[Element] Reals && m > 0 && m \[Element] Integers;

groundStateOld[x_] :=  1/Sqrt[a]
  * Sin[(\[Pi] (x + a))/(2 a)]*(UnitStep[x + a] - UnitStep[x - a])

energyEigenfunctionNew[m_, x_] :=  1/Sqrt[2 a] * Sin[(m*\[Pi] (x + 2 a))/(4 a)]

```

> $\ $

### 2. Sanity check: Are these orthogonal and normalized (in their own basis)?

```Mathematica
innerProductOld = \!\(
    \*SubsuperscriptBox[\(\[Integral]\), \(-a\), \(a\)]\(\((Conjugate[
       groundStateOld[x]]*\ groundStateOld[x])\) \[DifferentialD]x\)\);

innerProductNew = \!\(
    \*SubsuperscriptBox[\(\[Integral]\), \(\(-2\) a\), \(2  
     a\)]\(\((Conjugate[energyEigenfunctionNew[2, x]]*\
      energyEigenfunctionNew[2, x])\) \[DifferentialD]x\)\);

```

> $\ $

### 3. Find the $m$-th probability amplitude: (and verify the structure of the integrand)

```Mathematica
integrand[x] =
  FullSimplify[
   Conjugate[energyEigenfunctionNew[2, x]]* groundStateOld[x]];

Subscript[c, m][m_] := \!\(
    \*SubsuperscriptBox[\(\[Integral]\), \(\(-2\) a\), \(2  
    a\)]\(\((Conjugate[energyEigenfunctionNew[m, x]]*\
     groundStateOld[x])\) \[DifferentialD]x\)\)

```

> $\ $

### 4. Calculate $c_1$ and verify that the sum of all $\lvert c_m \rvert^2$ is unity.

``` Mathematica
Subscript[c, 1] = \!\(
    \*SubsuperscriptBox[\(\[Integral]\), \(\(-2\) a\), \(2  
    a\)]\(\((Conjugate[energyEigenfunctionNew[1, x]]*\
     groundStateOld[x])\) \[DifferentialD]x\)\)

FullSimplify[
 Sum[Conjugate[Subscript[c, m][j]]*Subscript[c, m][j], {j, 1,
   Infinity, 2}]]
```
