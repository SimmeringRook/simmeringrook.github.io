---
title: Homework 2
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Friday, October 1, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{HW2}
    \fancyhead[LO,LE]{Knudson}
---

# Question 1

> In the following expressions, where $A$ is an operator, specify the nature of each expression (i.e. whether it's an operator, a bra, or a ket) and then find its Hermitian conjugate.

## Part A

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\bra{\psi}A\ket{\varphi}\bra{\varphi}$$

The object is a bra. We can determine this two ways:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\underbrace{\braket{\psi A}{\varphi}}_{scalar}\bra{\varphi}\quad\text{or}\quad\bra{\psi}\  \underbrace{A\ket{\varphi}\bra{\varphi}}_{operator}=\bra{\psi '}$$

### Conjugate

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\left(\underbrace{\braket{\psi A}{\varphi}}_{scalar}\bra{\varphi}\right)^\dagger &= \bigg(\braket{\psi A}{\varphi}\bigg)^* \ket{\varphi} \\
\end{aligned}$$

## Part B

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}A\ket{\varphi}\bra{\psi}$$

The object is an operator.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\underbrace{A}_{operator}\underbrace{\ket{\varphi}\bra{\psi}}_{operator}$$

### Conjugate

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bigg(A\ket{\varphi}\bra{\psi}\bigg)^\dagger &= \ket{\psi}\bra{\varphi} A^\dagger \\
\end{aligned}$$

## Part C

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\bra{\psi}A\ket{\varphi}\ket{\varphi}\bra{\psi}A$$

The object is an operator.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\psi}A\ket{\varphi}\ket{\varphi}\bra{\psi}A &= \left(\underbrace{\bra{\psi}A\ket{\varphi}}_{scalar}\right)\left(\underbrace{\ket{\varphi}\bra{\psi}}_{operator}\right)A\\
\end{aligned}$$

### Conjugate

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\left(\underbrace{\bra{\psi}A\ket{\varphi}}_{scalar}\underbrace{\ket{\varphi}\bra{\psi}}_{operator}A\right)^\dagger &= \bigg(\braket{\psi A}{\varphi}\bigg)^* A^{\dagger}\ket{\psi}\bra{\varphi} \\
\end{aligned}$$

## Part D

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\bra{\varphi}A\ket{\psi}\ket{\varphi}-iA\ket{\psi}$$

The object is a ket.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\varphi}A\ket{\psi}\ket{\varphi}-iA\ket{\psi} &= \left(\underbrace{\bra{\varphi}A\ket{\psi}}_{scalar}\right)\ket{\varphi}-i\left(\underbrace{A}_{operator}\right)\ket{\psi}\\
\end{aligned}$$

### Conjugate

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\left(\underbrace{\bra{\varphi}A\ket{\psi}}_{scalar}\ket{\varphi}-iA\ket{\psi}\right)^\dagger &= \bigg(\braket{\varphi A}{\psi}\bigg)^* \bra{\varphi} + i A^{\dagger}\bra{\psi} \\
\end{aligned}$$

## Part E

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\ket{\varphi}\bra{\varphi}(A+iA)\ket{\psi}\bra{\psi}$$

The object is an operator.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
\ket{\varphi}\bra{\varphi}(A+iA)\ket{\psi}\bra{\psi} &= \ket{\varphi}\bra{\varphi}A\ket{\psi}\bra{\psi} + i\ket{\varphi}\bra{\varphi}A\ket{\psi}\bra{\psi}\\ &= \left(\underbrace{\ket{\varphi}\bra{\varphi}}_{operator}\underbrace{A}_{operator}\underbrace{\ket{\psi}\bra{\psi}}_{operator}\right) + i\left(\underbrace{\ket{\varphi}\bra{\varphi}}_{operator}\underbrace{A}_{operator}\underbrace{\ket{\psi}\bra{\psi}}_{operator}\right)\\
\end{aligned}$$

### Conjugate

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\left(\underbrace{\ket{\varphi}\bra{\varphi}}_{operator}\underbrace{A}_{operator}\underbrace{\ket{\psi}\bra{\psi}}_{operator} + i\underbrace{\ket{\varphi}\bra{\varphi}}_{operator}\underbrace{A}_{operator}\underbrace{\ket{\psi}\bra{\psi}}_{operator}\right)^{\dagger} &= \bigg(\ket{\psi}\bra{\psi}A^{\dagger} \ket{\varphi}\bra{\varphi}\bigg) - i\bigg(\ket{\psi}\bra{\psi}A^{\dagger} \ket{\varphi}\bra{\varphi}\bigg) \\
\end{aligned}$$

\pagebreak

# Question 2

> In class, we looked at the "hermiticivity" of the operators $X$, $d/dx$, and $i\hbar d/dx$.

## Part A

> Use our results to explore whether the following operators are Hermitian: $e^X$, $e^{d/dx}$, and $e^{-i\hbar d/dx}$.

We discussed the property in lecture that if $A$ is Hermitian, then $F(A)$ is Hermitian only if $F$ is a real function. By inspection, $e$ is a real function, therefore we know that $e^X$ and $e^{-i\hbar d/dx}$ are Hermitian, and since $d/dx$ is anti-Hermitian we expect that $e^{d/dx}$ is anti-Hermitian:

$$\bigg(F(A)\bigg)^{\dagger} = F^* (A^\dagger )$$

So, for $e^X$ and $e^{-i\hbar d/dx}$, we apply the substitution: $F\mapsto e$ and $A\mapsto X,\ -i\hbar \frac{d}{dx}$ and see the criteria for the property is valid ($F$ is a real function). To show $e^{d/dx}$ is anti-Hermitian, let us consider the power series expansion.

$$
\begin{aligned}
\bigg(e^{\frac{d}{dx}}\bigg)^{\dagger} &= \left(\sum_{n=0}^{\infty}{\frac{1}{n!}\frac{d^n}{dx^n}}\right)^{\dagger} \\
&= \left(I + \left(\frac{d}{dx}\right) + \frac{1}{2!} \left(\frac{d}{dx}\right)^2 + ...\right)^{\dagger} \\
&= I^{\dagger} + \left(\frac{d}{dx}\right)^{\dagger} + \frac{1}{2!} \left(\left(\frac{d}{dx}\right)^2\right)^{\dagger} + ... \\
&= I^{\dagger} - \left(\frac{d}{dx}\right) + \frac{1}{2!} \left(\frac{d}{dx}\right)^2 - ... \\
&= \left(\sum_{n=0}^{\infty}{\frac{(-1)^n}{n!}\frac{d^n}{dx^n}}\right) \\
&= \bigg(e^{-\frac{d}{dx}}\bigg)\\
\\
(e^{d/dx})^\dagger &= e^{-d/dx}
\end{aligned}$$

## Part B

> Find the Hermitian conjugate of the operator $X(d/dx)$, where $X$ is a position operator. Present your results as $XA+B$, where $A$ and $B$ are some operators. What are the operators $A$ and $B$?

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\varphi}X\frac{d}{dx}\ket{\psi} &= \int_{-\infty}^{\infty}{\varphi^*(x)X\frac{d}{dx}\psi(x)dx}\\
\\
dv = \psi^{\prime}(x)dx \quad &\Rightarrow \quad v = \psi(x) \\
u = \varphi(x)X \quad &\Rightarrow \quad du = (\varphi^{\prime}(x)X + \varphi(x))dx\\
\\
&= \bigg(\varphi^*(x)\psi(x)x\bigg)_{-\infty}^{\infty} - \int_{-\infty}^{\infty}{\psi^*(x)\varphi^{\prime}(x)xdx}- \int_{-\infty}^{\infty}{\psi^*(x)\varphi(x)dx}\\
&= -\int_{-\infty}^{\infty}{\psi^*(x)X\frac{d}{dx}\varphi(x)dx} - \int_{-\infty}^{\infty}{\psi^*(x)\varphi(x)dx}\\
&= -\bra{\psi}X\frac{d}{dx}+I\ket{\varphi}^*\\
(X\frac{d}{dx})^\dagger &= -(X\frac{d}{dx}+I)
\end{aligned}$$

\pagebreak

# Question 3

> Consider an operator: $$A=i(X^2 + 1)\frac{d}{dx} +iX$$

## Part A

> Show that $A$ is Hermitian.

For sanity, let's split this into two parts and then combine the results to demonstrate that the linear combination is Hermitian.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\varphi}iX\ket{\psi} &= \int_{-\infty}^{\infty}{\varphi^*(x)(iX)\psi(x)dx}\\
&= \left(\int_{-\infty}^{\infty}{\psi^*(x)(-iX)\varphi(x)dx}\right)^*\\
&= -\bra{\psi}iX\ket{\varphi}^*\\
(iX)^\dagger &= -iX
\end{aligned}$$

Now the messier set:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\varphi}i(X^2 + 1)\frac{d}{dx}\ket{\psi} &= i\int_{-\infty}^{\infty}{\varphi^*(x)(X^2 + 1)\frac{d}{dx}\psi(x)dx}\\
&= i\int_{-\infty}^{\infty}{\varphi^*(x)x^2 \frac{d}{dx}\psi(x)dx} + i\int_{-\infty}^{\infty}{\varphi^*(x)\frac{d}{dx}\psi(x)dx}\\
\\
dv = \psi^{\prime}(x)dx \quad &\Rightarrow \quad v = \psi(x) \\
u = \varphi(x)x^2 \quad &\Rightarrow \quad du = (\varphi^{\prime}(x)x^2 + 2x\varphi(x))dx\\
\\
&= i\left(\bigg(\varphi^*(x)x^2\psi(x)\bigg)_{-\infty}^{\infty} - \int_{-\infty}^{\infty}{\psi^*(x)x^2\varphi^{\prime}(x) dx}- \int_{-\infty}^{\infty}{\psi^*(x)2x\varphi(x)dx}\right) + i\int_{-\infty}^{\infty}{\varphi^*(x)\frac{d}{dx}\psi(x)dx}\\
&= i\left(-\int_{-\infty}^{\infty}{\psi^*(x)x^2\varphi^{\prime}(x) dx} - \int_{-\infty}^{\infty}{\psi^*(x)2x\varphi(x)dx}\right) + i\left(\bigg(\varphi^*(x)\psi(x)\bigg)_{-\infty}^{\infty} - \int_{-\infty}^{\infty}{\psi(x)^* \varphi^{\prime}(x)dx}\right)\\
&= -i\left(\int_{-\infty}^{\infty}{\psi^*(x)x^2\varphi^{\prime}(x) dx} + \int_{-\infty}^{\infty}{\psi^*(x)2x\varphi(x)dx} + \int_{-\infty}^{\infty}{\psi(x)^* \varphi^{\prime}(x)dx}\right)\\
&= -i\left(\int_{-\infty}^{\infty}{\psi^*(x)(x^2+1)\varphi^{\prime}(x) dx} + \int_{-\infty}^{\infty}{\psi^*(x)2x\varphi(x)dx}\right)\\
&= -i\bra{\psi}(X^2+1)\frac{d}{dx} + 2X\ket{\varphi}\\
\\
\left(i(X^2 + 1)\frac{d}{dx}\right)^\dagger &= -\left(i(X^2+1)\frac{d}{dx} + 2iX\right)\\
&= \left(i(X^2+1)\frac{d}{dx} + 2iX\right)^*\\
\end{aligned}$$

Combining the results, the demonstration becomes much clearer:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
A^\dagger &= \left(i(X^2 + 1)\frac{d}{dx}+iX\right)^\dagger\\
&= \left(i(X^2 + 1)\frac{d}{dx}\right)^\dagger + (iX)^\dagger\\
&= i(X^2+1)\frac{d}{dx} + 2iX - iX\\
&= i(X^2+1)\frac{d}{dx} + iX\\
\end{aligned}$$

## Part B

> Find the normalized state $\psi(x)$, where $x$ spans from $-\infty$ to $+\infty$, for which $A\psi(x)=0$.

Finding a wave function that is well behaved across $(-\infty,\infty)$ just requires us to solve the First Order differential equation. For ease of demonstration I will change $\psi(x)$ to $y(x)$:

$$\begin{aligned}
\bigg(i(X^2 + 1)\frac{d}{dx} +iX\bigg)\psi(x) &=0\\
(X^2 + 1)\frac{dy}{dx} + xy &= 0\\
(X^2 + 1)\frac{dy}{dx} &= -xy \\
\frac{dy}{y} &= - \frac{x}{x^2 +1} dx\\
\\ u = x^2 + 1, &\quad du = 2x dx \\
\\
\int{\frac{dy}{y}} &= -\frac{1}{2}\int{\frac{du}{u}} \\
\ln{y} &= -\frac{1}{2}\ln{u} + C\\
y &= e^{\ln{u^{-1/2}}+C} \\
y &= \frac{C}{\sqrt{x^2+1}}
\end{aligned}$$

Now the value of $C$ can be determined by normalizing our wavefunction:

$$\begin{aligned}
\int_{-\infty}^{\infty}{\left(\frac{C}{\sqrt{x^2+1}}\right)^2 dx} &= 1 \\
C^2 \bigg(\arctan{x}\bigg)_{-\infty}^{\infty} &= 1 \\
C &= \frac{1}{\sqrt{\frac{\pi}{2}- \frac{-\pi}{2}}} \\
&= \frac{1}{\sqrt{\pi}}
\end{aligned}$$

$$\psi(x) = \frac{1}{\sqrt{\pi}\sqrt{x^2 + 1}}$$

\pagebreak

## Part C

> Calculate the probability of finding the particle (represented by $\psi(x)$) in the region $-1\leq x \leq 1$.

The probability of finding the particle in the region of $[-1,1]$ is just the norm squared of the wavefunction integrated over the interval:

$$\begin{aligned}
\mathcal{P} &= \int_{-1}^{1}{\left(\frac{1}{\sqrt{\pi}\sqrt{x^2 + 1}}\right)^2 dx} \\
 &= \frac{1}{\pi} \bigg(\arctan{x}\bigg)_{-1}^{1} \\
 &= \frac{1}{\pi} \bigg(\frac{\pi}{4}- \frac{-\pi}{4}\bigg) \\
&= \frac{1}{2}
\end{aligned}$$
