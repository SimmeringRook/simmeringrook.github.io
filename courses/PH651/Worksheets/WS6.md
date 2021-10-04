---
title: Worksheet 6
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Monday, October 4, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{WS6}
    \fancyhead[LO,LE]{Knudson}
---

$$\ $$

Consider an observable $A$ which is represented by a matrix in some basis:

$$A \dot{=} \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}$$

## Is $A$ Hermitian?

$$\begin{aligned}
A^\dagger &= \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}^\dagger \\
&= \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}^{(T*)} \\
&= \begin{pmatrix} 0 & i \\ -i & 0 \end{pmatrix}^* \\
&= \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} = A
\end{aligned}$$

$A$ is Hermitian.

## If we perform a measurement of $A$, what are the possible outcomes?

The measurements of $A$ are going to correspond the eigenvalues of the matrix $A$, which for a $2\times 2$ matrix of this structure are $\pm 1$:

$$\begin{aligned}
\text{det}(A-\lambda I) &= \lambda^2 -1 \\
\lambda &= \pm 1
\end{aligned}$$

## What are the possible states of the system after the measurement?

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

So, after the measurement, our state will either be in the $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{a_1}$ or $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{a_2}$ eigenstate[^1]. $$\ $$

[^1]: Alternatively, we could have represented $A$ in its own basis, in which case the eigenstates would have a simpler matrix representation which would inherently demonstrate the completeness and orthogonality of the set.

## Can we tell anything about the probability to find the system in each state?

Without an initial state, we have no way of actually carrying out the projection operation to determine the probabilities (and/or amplitudes) of obtaining $a_1$ or $a_2$. $$\ $$

## Do the eigenstates of $A$ form a basis? Show.

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
