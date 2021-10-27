---
title: Worksheet 4
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Wednesday, September 29, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[LO,LE]{Knudson}
---

# Question

> Consider operators: $A$, $B$, and $C$ as well as a complex number $\alpha$ and the bra $\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\psi}$. What kind of an object (bra, let, or operator) is the following:

## Part A

> $\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\psi}AB\alpha$


Recalling that the result of an operator acting to the left on a bra is some other bra (or scalar multiple if the bra is an eigenvector of the operator).

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\zeta}\Xi=\bra{\zeta'}$$

Therefore, we can use associativity to resolve $\newcommand{\bra}[1]{{\left\langle#1\right|}}\bra{\psi}AB\alpha$ from left to right:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}\begin{aligned}
\bra{\psi}AB\alpha &= (\bra{\psi}A)B\alpha; &\bra{\psi'}=\bra{\psi}A\\
&=(\bra{\psi'}B)\alpha; &\bra{\psi''}=\bra{\psi'}B\\
&=\bra{\psi''}\alpha
\end{aligned}$$

And the resulting object is a bra.

### Hermitian Conjugates

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
(\bra{\psi''}\alpha)^{\dagger} &= \alpha^*\ket{\psi''} \\
&= \alpha^* B^\dagger A^\dagger \ket{\psi}
\end{aligned}$$

## Part B

> $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}} \ket{\psi}\bra{\varphi}$

By definition, the outer product is an operator as it can act to the left on bras or to the right on kets.

### Hermitian Conjugates

Recall that $(AB)^{\dagger} = B^{\dagger}A^{\dagger}$, therefore:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
(\ket{\psi}\bra{\varphi})^{\dagger} = \bra{\varphi}^{\dagger}\ket{\psi}^{\dagger} = \ket{\varphi}\bra{\psi}$$
