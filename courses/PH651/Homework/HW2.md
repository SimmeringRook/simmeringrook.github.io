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

The object is a bra. We can evaluate this two ways:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\underbrace{\braket{\psi A}{\varphi}}_{scalar}\bra{\varphi}\quad\text{or}\quad\bra{\psi}\  \underbrace{A\ket{\varphi}\bra{\varphi}}_{operator}=\bra{\psi '}$$

## Part B

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}A\ket{\varphi}\bra{\psi}$$

The object is an operator.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\underbrace{A}_{operator}\underbrace{\ket{\varphi}\bra{\psi}}_{operator}$$

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

\pagebreak

# Question 2

> In class, we looked at the "hermiticivity" of the operators $X$, $d/dx$, and $i\hbar d/dx$.

## Part A

> Use our results to explore whether the following operators are Hermitian: $e^X$, $e^{d/dx}$, and $e^{-i\hbar d/dx}$.

We discussed the property in lecture that if $A$ is Hermitian, then $F(A)$ is Hermitian only if $F$ is a real function. By inspection, $e$ is a real function, therefore we know that $e^X$ and $e^{-i\hbar d/dx}$ are Hermitian, and since $d/dx$ is anti-Hermitian we expect that $e^{d/dx}$ is anti-Hermitian.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\varphi}e^{d/dx}\ket{\psi} &= \int_{-\infty}^{\infty}{\varphi^*(x)e^{d/dx}\psi(x)dx}\\
&= \int_{-\infty}^{\infty}{\varphi^*(x) \sum_{n=0}^{\infty}{\frac{1}{n!}\frac{d^n\psi(x)}{{dx}^n}}dx}\\
&= \int_{-\infty}^{\infty}{\varphi^*(x)\psi(x)dx} + \int_{-\infty}^{\infty}{\varphi^*(x) \frac{d\psi(x)}{{dx}}dx} + ...\\
&= \left(\int_{-\infty}^{\infty}{\psi^*(x)\varphi(x)dx}\right)^* + \left(\bigg(\varphi^*(x)\psi(x)\bigg)_{-\infty}^{\infty} - \int_{-\infty}^{\infty}{\psi^*(x) \frac{d\varphi(x)}{{dx}}dx} - ...\right)^*\\
&= -\left(\int_{-\infty}^{\infty}{\psi^*(x) \sum_{n=0}^{\infty}{\frac{1}{n!}\frac{d^n\varphi(x)}{{dx}^n}} dx} \right)^*\\
&= -\bra{\psi}e^{d/dx}\ket{\varphi}^*\\
(e^{d/dx})^\dagger &= -e^{d/dx}
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

Break into pieces for sanity?

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\varphi}iX\ket{\psi} &= \int_{-\infty}^{\infty}{\varphi^*(x)(iX)\psi(x)dx}\\
&= \left(\int_{-\infty}^{\infty}{\psi^*(x)(-iX)\varphi(x)dx}\right)^*\\
&= -\bra{\psi}iX\ket{\varphi}^*\\
(iX)^\dagger &= -iX
\end{aligned}$$

The harder bit?

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

Combine efforts?

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



## Part C

> Calculate the probability of finding the particle (represented by $\psi(x)$) in the region $-1\leq x \leq 1$.
