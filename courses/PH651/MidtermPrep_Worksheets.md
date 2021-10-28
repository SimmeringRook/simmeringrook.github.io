---
title: "Midterm Prep: Worksheet Review"
subtitle: PH651, Fall 2021
author: Thomas Knudson
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{Knudson}
---

## de Brogile Wavelength

> You are an experimentalist in nanoscience who studies nanometer-size features. You have two microscopes: one is an optical microscope, in which you illuminate your sample with visible light ($\lambda$ ~ 400 nm), another one is an electron microscope, in which you bombard your sample with electrons accelerated to energies of 10 keV. Estimate how many orders of magnitude you (in theory) can gain in the resolution of your experiment by choosing the electron microscope over the optical one if the resolution is diffraction limited (i.e. limited by the wavelength). (In practice, electron microscope resolution is limited by aberrations of the electron optics, which reduces the resolution.) $$\ $$

Using the de Brogile wavelength formula, we can find the wavelength of an electron (assuming rest mass):

$$\lambda = \frac{h}{m\cdot v}$$

To find the speed of the electron, we can manipulate its energy and solve for speed and then substitute that expression back into the de Brogile equation.

$$\begin{aligned}
E &= \frac{m_{e^-}\cdot v^2}{2}\\
v &= \sqrt{\frac{2E}{m_{e^-}}}
\end{aligned}
\qquad\qquad\qquad
\begin{aligned}
\lambda_{e^-} &= \frac{h}{m_{e^-}\cdot v}\\
&= \frac{h}{m_{e^-}}\sqrt{\frac{m_{e^-}}{2E}}\\
&= \frac{h}{\sqrt{m_{e^-}2E}}
\end{aligned}$$

Finally, we calculate the wavelength by substituting in the values for Plank's constant ($h=6.63\times 10^{-34}\ J\cdot s$), the energy of the Electron ($E=10\ keV= 1.6\times 10^{-15}\ J$), and the (rest) mass the of Electron ($m_{e^-}=9.1\times 10^{-31}\ kg$)

$$\begin{aligned}
\lambda_{e^-} &= \frac{h}{\sqrt{m_{e^-}2E}}\\
&= \frac{6.63\times 10^{-34}\ J\cdot s}{\sqrt{(9.1\times 10^{-31}\ kg)\cdot 2(1.6\times 10^{-15}\ J)}}\\
&= 1.2\times 10^{-11}\ m = 12\ pm
\end{aligned}$$

Therefore, in theory, an electron microscope would give us four orders of magnitude in resolution over an optical microscope:

$$\underbrace{\lambda_{light} \rightarrow 10^{-7}\ m}_{\text{optical microscope}} \qquad\text{versus}\qquad \underbrace{\lambda_{e^-} \rightarrow 10^{-11}\ m}_{\text{electron microscope}}$$

## Linear Independence

> Are the following functions linearly independent or dependent: $$f(x) = \cos(x), g(x) = e^{ix}, h(x) = \sin(x)$$

Recalling Euler's identity, we know that $e^{ix}$ is the linear combination of $\cos{x}+i\sin{x}$, and we can immediately state that the set $\{f(x),\ g(x),\ h(x)\}$ is linearly dependent.

If we exclude $g(x)$ from consideration, we can then state that the set $\{f(x),\  h(x)\}$ is not only linearly independent, but also othornormal.[^1]

Similarly, if we only consider the set that contains $g(x)$ and either $f(x)$ or $h(x)$, each of those sets are linearly independent as well.

[^1]: Here we used the fact that $\sin{x}$ and $\cos{x}$ are orthogonal along a full period of $x$ from the Fourier basis and this result can be shown from the Harmonic integrals.

# Operators

## Identification and Hermitian Conjugates

> Consider operators: $A$, $B$, and $C$ as well as a complex number $\alpha$ and the bra $\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\psi}$. What kind of an object (bra, let, or operator) is the following:

> $\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\psi}AB\alpha$

Recalling that the result of an operator acting to the left on a bra is some other bra (or scalar multiple if the bra is an eigenvector of the operator).

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\zeta}\Xi=\bra{\zeta'}$$

Therefore, we can use associativity to resolve $\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\psi}AB\alpha$ from left to right:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}\begin{aligned}
\bra{\psi}AB\alpha &= (\bra{\psi}A)B\alpha; &\bra{\psi'}=\bra{\psi}A\\
&=(\bra{\psi'}B)\alpha; &\bra{\psi''}=\bra{\psi'}B\\
&=\bra{\psi''}\alpha
\end{aligned}$$

And the resulting object is a bra. The Hermitian Conjugate is:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
(\bra{\psi''}\alpha)^{\dagger} &= \alpha^*\ket{\psi''} \\
&= \alpha^* B^\dagger A^\dagger \ket{\psi}
\end{aligned}$$

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}\newcommand{\ket}[1]{{\left|#1\right\rangle}} \ket{\psi}\bra{\varphi}$$

By definition, the outer product is an operator as it can act to the left on bras or to the right on kets. The Hermitian Conjugate is given by:

Recall that $(AB)^{\dagger} = B^{\dagger}A^{\dagger}$, therefore:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
(\ket{\psi}\bra{\varphi})^{\dagger} = \bra{\varphi}^{\dagger}\ket{\psi}^{\dagger} = \ket{\varphi}\bra{\psi}$$

## Unitary

> Consider unitary operators $A$, $B$, and $C$. Is their product a unitary operator? Show.

Recall that unitary operators are classified by their inverse being the adjoint of itself: $U^{-1}=U^\dagger$. We can then use this to show that the product of unitary operators is itself unitary:

$$\begin{aligned}
D&=(ABC)\\
D(ABC)^{\dagger} &= (ABC)(ABC)^{\dagger} \\
D(C^\dagger B^\dagger A^\dagger) &= (ABC)(C^\dagger B^\dagger A^\dagger) \\
D(C^{-1} B^{-1} A^{-1}) &= (ABC)(C^{-1} B^{-1} A^{-1}) \\
DD^{-1} &= I
\end{aligned}$$

> Consider Hermitian operators $A$ and $B$. Is is known that their product is also Hermitian, what does this imply about the "hermicitivity" of the commutator of $A$ and $B$?

Similar to Question 1, let us consider the product of the operators:

$$(AB)^{\dagger} = B^{\dagger} A^{\dagger}$$

And using the definition of Hermitian operators, we can simplify the right-hand side of this statement:

$$B^{\dagger} A^{\dagger} = BA$$

Let's now investigate the commutator of $A$ and $B$:

$$\begin{aligned}
\left[A,\ B\right] &= AB - BA\\
&= AB - (B^{\dagger} A^{\dagger})\\
&= AB - (AB)^{\dagger}\\
&= AB - AB \\
&= 0
\end{aligned}$$

Therefore, we can conclude that:

| | |
| --- | --- |
| **if** the product of two Hermitian operators is itself Hermitian, | **then** both operators commute with each other. |

## Measurements

> Consider an observable $A$ which is represented by a matrix in some basis: $$A \dot{=} \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}$$

> Is $A$ Hermitian?

$$\begin{aligned}
A^\dagger &= \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}^\dagger \\
&= \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}^{(T*)} \\
&= \begin{pmatrix} 0 & i \\ -i & 0 \end{pmatrix}^* \\
&= \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} = A
\end{aligned}$$

$A$ is Hermitian.

> If we perform a measurement of $A$, what are the possible outcomes?

The measurements of $A$ are going to correspond the eigenvalues of the matrix $A$, which for a $2\times 2$ matrix of this structure are $\pm 1$:

$$\begin{aligned}
\text{det}(A-\lambda I) &= \lambda^2 -1 \\
\lambda &= \pm 1
\end{aligned}$$

> What are the possible states of the system after the measurement?

The eigenvectors that correspond to these eigenvalues in this unknown basis are come from solving the eigenvalue equation:

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
A\ket{\psi} &= a_1\ket{a_1}\\
\begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} &= (+1) \begin{pmatrix} x \\ y \end{pmatrix}\\
\\
-i y = x, &\quad ix = y\\
x = 1, &\quad y= i\\
\ket{a_1} &\dot{=} \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ i \end{pmatrix}
\end{aligned}$$

The factor of $\sqrt{2}^{-1}$ comes from normalizing the eigenvector. $a_2$ follows the same process:

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
A\ket{\psi} &= a_2\ket{a_2}\\
\begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} &= (-1) \begin{pmatrix} x \\ y \end{pmatrix}\\
\\
-i y = -x, &\quad ix = -y\\
x = i, &\quad y= 1\\
\ket{a_2} &\dot{=} \frac{1}{\sqrt{2}} \begin{pmatrix} i \\ 1 \end{pmatrix}
\end{aligned}$$

So, after the measurement, our state will either be in the $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{a_1}$ or $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{a_2}$ eigenstate[^2]. $$\ $$

[^2]: Alternatively, we could have represented $A$ in its own basis, in which case the eigenstates would have a simpler matrix representation which would inherently demonstrate the completeness and orthogonality of the set.

> Can we tell anything about the probability to find the system in each state?

Without an initial state, we have no way of actually carrying out the projection operation to determine the probabilities (and/or amplitudes) of obtaining $a_1$ or $a_2$. $$\ $$

> Do the eigenstates of $A$ form a basis? Show.

We already normalized each eigenstate when determining their matrix representation. Mathematically, we can make the argument that the eigenstates do form a complete orthogonal basis by $A$ being able to be represented as a diagonal matrix whose algebraic multiplicity is equal to its geometric multiplicity. By finding the eigenvalues of $A$ and the corresponding eigenstates, we see that there are two distinct eigenvalues and that the dimensionality of each eigenspace is exactly equal to the algebraic multiplicity of each eigenvalue.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\braket{a_1}{a_1} &= \frac{1}{2}(1 -i^2) &= 1\\
\braket{a_2}{a_1} &= \frac{1}{2}(-i + i) &= 0\\
\braket{a_1}{a_2} &= \frac{1}{2}(i - i) &= 0\\
\braket{a_2}{a_2} &= \frac{1}{2}(-i^2 + 1) &= 1\\
\end{aligned}$$

Completeness:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\sum_{n=1}^{2}{\ket{a_n}\bra{a_n}} &= \ket{a_1}\bra{a_1} + \ket{a_2}\bra{a_2} \\
&\dot{=} \frac{1}{2}\begin{pmatrix} 1(1) & 1(-i) \\ i(1) & i(-i) \end{pmatrix} + \frac{1}{2} \begin{pmatrix} i(-i) & i(1) \\ 1(-i) & 1(1) \end{pmatrix}\\
&= \frac{1}{2}\begin{pmatrix} 1-i^2 & -i+i \\ i-i & -i^2+1 \end{pmatrix} \\
&= \frac{1}{2}\begin{pmatrix} 2 & 0 \\ 0 & 2 \end{pmatrix} = I
\end{aligned}$$

## Complete Set of Compatible Observables

> Consider observables represented by $$A\ \dot{=} \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$$ and $$B\ \dot{=} \begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}$$ in some orthonormal basis by $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi_1}$ and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi_2}$.

> Is $A$ a "Complete Set of Compatible Observables"?

By inspection, no. With $A$ being a diagonal matrix, the eigenvalues are shown on the main diagonal. $a_1 = a_2 = 1$ and the dimension of this eigenspace is greater than $1$. E.g., specifying the eigenvalue of $1$ does not uniquely specify with eigenvector of $A$ we are talking about. $$\ $$

> Is $B$ a "Complete Set of Compatible Observables"?

$B$ isn't diagonal, so we need to find the eigenvalues:

$$\begin{aligned}
\det{B-\lambda I} &= (1-\lambda)^2 - 1 \\
1 - 2\lambda + \lambda ^2 - 1 &= 0 \\
\lambda (\lambda - 2) &= 0\\
\lambda &= 0, 2
\end{aligned}$$

Eigenvectors:

$$\begin{aligned}
\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} &= \lambda \begin{pmatrix} x \\ y \end{pmatrix} \\
\\
x + y = \lambda x, &\qquad x + y =\lambda y
\end{aligned}$$

$$\begin{aligned}
x + y = 0, &\qquad x + y =0\\
x = -y, &\quad \text{choose } x=1\\
\lambda = 0 &\mapsto \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix}
\end{aligned}$$

$$\begin{aligned}
x + y = 2x, &\qquad x + y =2y\\
-x = -y, &\quad \text{choose } x=1\\
\lambda = 2 &\mapsto \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix}
\end{aligned}$$

Specifying $b_n$ is enough to specify an eigenvector explicitly. $B$ is a C.S.C.O. $$\ $$

> Is a set $\{ A, B \}$ a "Complete Set of Compatible Observables" (do the eigenvectors common to $A$ and $B$ form a unique basis)? If yes, write down the basis common to $A$ and $B$.

By inspection, $[A, B]=0$, so we know they do share a common set of eigenvectors and since $B$ is A C.S.C.O, we can use their eigenvectors to specify which set of eigenvalues we're referring:

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
(AB)\ket{\varphi_1} &= (ab)_1 \ket{a=1,\ b=0} \\
(AB)\ket{\varphi_2} &= (ab)_2 \ket{a=1,\ b=2} \\
\end{aligned}$$

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\{\ket{a=1,\ b=0},\ \ket{a=1,\ b=2}\} \dot{=} \left\{\frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix},\ \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix}\right\}$$

## Unitary Transformation

> Consider unitary transformation of the position operator $X$: $$X' = U X U^\dagger$$ If $U=I+i\epsilon G$, where:
>
> - $I$ is the identity operator,
> - $\epsilon$ is a real infinitesimal number,
> - and $G$ is a Hermitian operator whichs is a generator of the space translation along $x$ $$G=\frac{P_x}{\hbar}$$
>
> What is $X'$? In your derivation, neglect a term proportional to $\epsilon^2$.

Let's carry this out symbolically, before substitutions:

$$\begin{aligned}
X' &= U X U^\dagger \\
&= (I + i\epsilon G) X (I - i\epsilon G) \\
&= (I + i\epsilon G) (X- i\epsilon XG)\\
&= X + i\epsilon GX - i\epsilon XG -i^2 \epsilon^2 GXG\\
&= X + i\epsilon [G,X] + \mathcal{O}(\epsilon^2)
\end{aligned}$$

$$X' \simeq X + i\epsilon\left[\frac{P_x}{\hbar}, X\right]$$

> Under what condition would $X$ not change under space translation?

If $G$ and $X$ commuted, $[G,X]=\left[\frac{P_x}{\hbar}, X\right]=0$, then under this translation $X'$ would simplify down to $X$.

## Expectation

> A $1D$ system is in a state describe by a well-behaved real wave function: $\psi(x)$. Find the expectation value of the momentum.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\psi}\hat{P}\ket{\psi} &= \int_{-\infty}^{\infty}{dx^{\prime} dx^{\prime\prime} \braket{\psi}{x^{\prime}}\bra{x^{\prime}}\hat{P}\ket{x^{\prime\prime}}\braket{x^{\prime\prime}}{\psi} }\\
&= \int_{-\infty}^{\infty}{dx^{\prime} dx^{\prime\prime} \psi^* (x^{\prime})\bra{x^{\prime}} \left(-i\hbar\frac{\partial}{\partial x^{\prime}}\delta(x^{\prime}-x^{\prime\prime})\right) \ket{x^{\prime\prime}} \psi(x^{\prime\prime}) }\\
&= -i\hbar\int_{-\infty}^{\infty}{dx^{\prime} \psi (x^{\prime})\frac{\partial}{\partial x^{\prime}}\psi(x^{\prime}) }
\end{aligned}$$

Let $u(x^{\prime}) = \psi(x^{\prime})$ such that $du = \frac{d\psi(x^{\prime})}{dx^{\prime}}dx^{\prime}$. Recall since $\psi(x^{\prime})$ is well-behaved, the wavefunction goes to $0$ at $\pm\infty$: $u(-\infty) = \psi(-\infty) = 0$ and $u(\infty) = \psi(\infty) = 0$.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\psi}\hat{P}\ket{\psi} &= -i\hbar\int_{0}^{0}{udu} \\
&= 0
\end{aligned}$$

Which is what we anticipate in the general case. The position wavefunction only works to describe location, not the direction of travel, and without more information (a perturbation), we assume the particle would be equally likely to be traveling in the $+x^{\prime}$ direction as $-x^{\prime}$.

## Time Evolution

> Consider a system whose initial state at $t_0=0$ is given in terms of eigenvectors of the (time-independent) Hamiltonian as follows: $$\newcommand{\bra}[1]{{\left\langle#1\right|}}\newcommand{\ket}[1]{{\left|#1\right\rangle}}\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\ket{\psi(0)} = \frac{1}{\sqrt{2}}\ket{\varphi_1} + \frac{1}{2}\ket{\varphi_2} - \frac{1}{2}\ket{\varphi_3}$$

> If the energies corresponding to $\newcommand{\bra}[1]{{\left\langle#1\right|}}\newcommand{\ket}[1]{{\left|#1\right\rangle}}\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\ket{\varphi_1}$, $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi_2}$, and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi_3}$, are $E_1$, $E_2$, and $E_3$, respectively, what is the state of the system at $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi(t)}$ at any later time $t$?

Time evolution of a state is equivalent to multiplying by a complex phase; recall, in general, $$\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi(t)} = \sum_{n}{c_n e^{-\frac{i E_n}{\hbar}t}\ket{\varphi_n}}$$

And so, $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi(t)}$ takes the form:

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi(t)} = \frac{1}{\sqrt{2}}e^{-\frac{i E_1}{\hbar}t}\ket{\varphi_1} + \frac{1}{2}e^{-\frac{i E_2}{\hbar}t}\ket{\varphi_2} - \frac{1}{2}e^{-\frac{i E_3}{\hbar}t}\ket{\varphi_3}$$

> How is the average energy at $t=0$ compared to that at a later time $t$? Explain.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\psi(t=0)}H\ket{\psi(t=0)} &= \bra{\psi(t=0)} \bigg(\frac{E_1}{\sqrt{2}}\ket{\varphi_1} + \frac{E_2}{2}\ket{\varphi_2} - \frac{E_3}{2}\ket{\varphi_3}\bigg) \\
&= \frac{E_1}{2} + \frac{E_2}{4} - \frac{E_3}{4}
\end{aligned}$$

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\psi(t)}H\ket{\psi(t)} &= \bra{\psi(t)} \bigg(\frac{E_1}{\sqrt{2}}e^{-\frac{i E_1}{\hbar}t}\ket{\varphi_1} + \frac{E_2}{2}e^{-\frac{i E_2}{\hbar}t}\ket{\varphi_2} - \frac{E_3}{2}e^{-\frac{i E_3}{\hbar}t}\ket{\varphi_3}\bigg) \\
&= \frac{E_1}{2} + \frac{E_2}{4} - \frac{E_3}{4}
\end{aligned}$$

The average energy at any later time $t$ is the same as that average energy at $t_0=0$ due to conservation of energy. It's not until we measure $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi(t)}$ that the state is changed and from that time onward, the average energy measured at a later time, $t_{late}$, would diverge from the average energy of the unmeasured state.

## Commutation

> For the $1D$ system described by the Hamiltonian, $H={P}^2 /(2m) + V(x)$, derive the following commutators: $$[P,H]=? \qquad [X,H] = ?$$

#### $[P,\ H]$

$$\begin{aligned}
[P,\ H] &= [P,\ \frac{P^2}{2m} + V(x)] \\
&= \underbrace{[P,\ \frac{P^2}{2m}]}_{[A,BC] = [A,B]C + B[A,C]} + [P,\ V(x)]\\
&= \frac{1}{2m}\left( \underbrace{[P,P]}_{0}P + P\underbrace{[P,P]}_{0} \right) + [P,\ V(x)]\\
&= [P,\ V(x)]\\
\\
\text{Let }\psi(x) &\text{ be a dummy test function} \\
&= -i\hbar \frac{\partial}{\partial x} \left(V(x)\psi(x)\right) + V(x)i\hbar \frac{\partial}{\partial x} \left(\psi(x)\right)\\
&= -i\hbar \left(\frac{\partial V(x)}{\partial x}\psi(x) + V(x)\frac{\partial \psi(x)}{\partial x}\right) + V(x)i\hbar \frac{\partial}{\partial x} \left(\psi(x)\right)\\
&= -i\hbar \frac{\partial V(x)}{\partial x}\psi(x) \\
\\
\therefore [P,\ H] &= -i\hbar \frac{\partial V(x)}{\partial x}
\end{aligned}$$

#### $[X,\ H]$

$$\begin{aligned}
[X,\ H] &= [X,\ \frac{P^2}{2m} + V(x)] \\
&= \underbrace{[X,\ \frac{P^2}{2m}]}_{[A,BC] = [A,B]C + B[A,C]} + [X,\ V(x)]\\
&= \frac{1}{2m}\left( \underbrace{[X,P]}_{-i\hbar}P + P\underbrace{[X,P]}_{-i\hbar} \right)\\
&= \frac{-i\hbar}{2m}\left( 2P \right)\\
&= -i\hbar\frac{P}{m}
\end{aligned}$$