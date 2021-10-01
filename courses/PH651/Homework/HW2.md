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
\underbrace{\braket{\psi A}{\varphi}}_{scalar}\bra{\varphi}\quad\text{or}\quad\bra{\psi}\  \underbrace{\ket{A \varphi}\bra{\varphi}}_{operator}=\bra{\psi '}$$

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

## Part B

> Find the Hermitian conjugate of the operator $X(d/dx)$, where $X$ is a position operator. Present your results as $XA+B$, where $A$ and $B$ are some operators. What are the operators $A$ and $B$?

\pagebreak

# Question 3

> Consider an operator: $$A=i(X^2 + 1)\frac{d}{dx} +iX$$

## Part A

> Show that $A$ is Hermitian.

## Part B

> Find the normalized state $\psi(x)$, where $x$ spans from $-\infty$ to $+\infty$, for which $A\psi(x)=0$.

## Part C

> Calculate the probability of finding the particle (represented by $\psi(x)$) in the region $-1\leq x \leq 1$.
