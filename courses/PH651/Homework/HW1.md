---
title: Homework 1
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Friday, September 24, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{HW1}
    \fancyhead[LO,LE]{Knudson}
---

# Question 1

> Are the following sets of vectors linearly independent of dependent over the complex field? $$\begin{aligned}
S_1 &\equiv \{(2,\ -3,\ 0),\ (0,\ 0,\ 1),\ (2i,\ i,\ -i)\}\\
S_2 &\equiv \{(i,\ 1,\ 2),\ (3,\ i,\ -1),\ (-i,\ 3i,\ 5i)\}\\
S_3 &\equiv \{(0,\ 4,\ 0),\ (i,\ -3i,\ i),\ (2,\ 0,\ 1)\}
\end{aligned}$$

## $S_1$

> $$S_1\equiv \{(2,\ -3,\ 0),\ (0,\ 0,\ 1),\ (2i,\ i,\ -i)\}$$

Consider the following criteria for linear independence for a set of vectors.

$$c_1\vec{v_1} + ... + c_k\vec{v_k} = 0,\qquad c_1=...=c_k=0$$

If the vectors, $\vec{v_k}$, are non-zero and only the trivial solution exists, then the vectors are linearly independent. If there exists any solution where each coefficient does not have to identically be zero, then the set of vectors are linearly dependent.

$$c_1(2,\ -3,\ 0) + c_2(0,\ 0,\ 1) + c_3(2i,\ i,\ -i) = (0,\ 0,\ 0)$$

This can then be written as the following system of linear equations:

$$\begin{aligned}
2c_1 + 2i c_3 &= 0 \\
-3c_1 + i c_3 &= 0 \\
c_2 - i c_3 &= 0
\end{aligned}$$

If $c_3$ is given some complex scalar value $k$, then the system of equations can be simplified and we discover a contradiction given by the first and second equation in the system.

$$\begin{aligned}
c_1 &= -ik \\
c_1 &= \frac{ik}{3} \\
c_2 &= ik
\end{aligned}$$

The only way where $c_1$ can be both $-ik$ and $\frac{ik}{3}$ is if $k=0$. Therefore, the set of vectors, $S_1$ is linearly independent over the complex field $\mathbb{C}^3$.

## $S_2$

> $$S_2 \equiv \{(i,\ 1,\ 2),\ (3,\ i,\ -1),\ (-i,\ 3i,\ 5i)\}$$

Consider a matrix $M$ constructed from the three column vectors of $S_2$. If the $\det{M}\neq0$, then $S_2$ is a set of linearly independent vectors over $\mathbb{C}^3$.

$$\begin{aligned}
\begin{vmatrix}
i & 3 & -i \\
1 & i & 3i \\
2 & -1 & 5i
\end{vmatrix} &= i \begin{vmatrix} i & 3i \\ -1 & 5i\end{vmatrix} - 3 \begin{vmatrix} 1 & 3i \\ 2 & 5i\end{vmatrix} -i \begin{vmatrix} 1 & i \\ 2 & -1\end{vmatrix}\\
&= i \bigg(5i^2 - (-1)3i\bigg) -3 \bigg(5i - 2(3i)\bigg) -i \bigg(-1-i(2)\bigg)\\
&= i(-5+3i) -3 (-i)-i(-1-2i)\\
&= i(-5+3+1)+i^2(3+2)\\
&= -5-i\\
&\neq 0
\end{aligned}$$

Therefore, the set $S_2$ is linearly independent over $\mathbb{C}^3$.

## $S_3$

> $$S_3 \equiv \{(0,\ 4,\ 0),\ (i,\ -3i,\ i),\ (2,\ 0,\ 1)\}$$

We begin with a similar approach to the $S_1$ by constructing the equation that describes the condition of linear independence. This time, after decomposing into a system of linear equations, we represent this information in (augmented) matrix form.

$$c_1(0,\ 4,\ 0) + c_2(i,\ -3i,\ i) + c_3(2,\ 0,\ 1) = (0,\ 0,\ 0)$$

$$
\begin{pmatrix}
  0 &  i  & 2 &\bigm| & 0 \\
  4 & -3i & 0 &\bigm| & 0 \\
  0 &  i  & 1 &\bigm| & 0 \\
\end{pmatrix}
$$

Then using Gaussian Elimination, this augmented matrix can be shown in row reduced form to either reveal the underlying linear independence of the vectors or their dependence.

$$
\begin{array}{rcl}
R_1 &\leftrightarrow & R_2 \\
(new)\ R_2 &\leftrightarrow & R_3 \\
\end{array}
\quad\rightarrow\quad
\begin{pmatrix}
  4 & -3i & 0 &\bigm| & 0 \\
  0 &  i  & 1 &\bigm| & 0 \\
  0 &  i  & 2 &\bigm| & 0 \\
\end{pmatrix}
$$

$$
\begin{array}{rcl}
R_3 - R_2 &\rightarrow & R_3 \\
\frac{R_1}{4} &\rightarrow &R_1 \\
\end{array}
\quad\rightarrow\quad
\begin{pmatrix}
  1 & \frac{-3}{4}i & 0 &\bigm| & 0 \\
  0 &  i  & 1 &\bigm| & 0 \\
  0 &  0  & 1 &\bigm| & 0 \\
\end{pmatrix}
$$

$$
\begin{array}{rcl}
R_2 - R_3 &\rightarrow &R_2 \\
R_1 + (new)\ \frac{3}{4}R_2 &\rightarrow &R_1 \\
\end{array}
\quad\rightarrow\quad
\begin{pmatrix}
  1 & 0 & 0 &\bigm| & 0 \\
  0 &  i  & 0 &\bigm| & 0 \\
  0 &  0  & 1 &\bigm| & 0 \\
\end{pmatrix}
$$

Noting that all columns are pivot columns, we conclude that $S_3$ is a  linearly independent set over $\mathbb{C}^3$.
