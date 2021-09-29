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

\pagebreak

# Question 2

> Are the following sets of functions linearly independent or dependent? $$\begin{aligned}
S_1 &\equiv \{2+x^2,\ 3-x+4x^3,\ 2x+3x^2-8x^3\}\\
S_2 &\equiv \{\sinh^2{x},\ 1,\ \cosh^2{x}\}\\
S_3 &\equiv \{x,\ (x-1)^2,\ (x+1)^2\}\\
S_4 &\equiv \{\sin^2{x},\ \cos^2{x},\ \sin{2x}\}
\end{aligned}$$

## $S_1$

> $$S_1 \equiv \{2+x^2,\ 3-x+4x^3,\ 2x+3x^2-8x^3\}$$

$$c_1(2+x^2) + c_2(3-x+4x^3) + c_3(2x+3x^2-8x^3) = 0$$

This can then be written as the following system of linear equations:

$$\begin{aligned}
x^0(2c_1 + 3 c_2) &= 0 \\
x(-c_2 + 2c_3) &= 0 \\
x^2(c_1 + 3c_3) &= 0 \\
x^3(4c_2 - 8c_3) &= 0
\end{aligned}$$

We can immediately recognize some similarity between the second and fourth equation in the system, and by simplifying each expression, we can see that they provide the same constraint on the coefficients, $c_2 = 2c_3$. This would normally be cause for concern, but recalling that $S_1$ contains only 3 functions, we should expect that a fourth equation in our system would show the same information as another. Removing the extra equation, we can then note a similarity with the two unchanged equations.

$$\begin{aligned}
c_2 &= 2c_3 \\
\\
2c_1 + 3 c_2 &= 0 \\
c_1 + 3c_3 &= 0\\
\end{aligned}$$

Solving both for $c_1$ and then equating, we have another relation for $c_2$ to $c_3$. If we substitute in $c_2= 2c_3$ and obtain a contradictory statement, then $S_1$ will be linearly independent but we will see that this is not the case.

$$\begin{aligned}
c_1 &= -\frac{3}{2} c_2 \\
c_1 &= -3c_3\\
\\
-\frac{3}{2} c_2 &= -3 c_3 \\
-\frac{3}{2} (2c_3) &= -3 c_3\\
-3 c_3 &= -3 c_3
\end{aligned}$$

This result means there is a nontrivial solution to the original equation and therefore $S_1$ is linearly dependent.

## $S_2$

> $$S_2 \equiv \{\sinh^2{x},\ 1,\ \cosh^2{x}\}$$

Without calculation, we can recall the fact that $1$ can be expressed by a linear combination of $\sinh^2{x}$ and $\cosh^2{x}$ through a similar form of Euler's identity:

$$\begin{aligned}
\sinh^2{x} &= \left(\frac{1}{2}(e^x - e^{-x})\right)^2 \\
&= \frac{1}{4}(e^{2x}-2+e^{-2x})
\end{aligned}$$

$$\begin{aligned}
\cosh^2{x} &= \left(\frac{1}{2}(e^x + e^{-x})\right)^2 \\
&= \frac{1}{4}(e^{2x}+2+e^{-2x})
\end{aligned}$$

And by subtracting $\sinh^2{x}$ from $\cosh^2{x}$ we obtain $1$ and thereby show $S_2$ is linearly dependent.

$$\begin{aligned}
\cosh^2{x} - \sinh^2{x} &= \frac{1}{4}(e^{2x}+2+e^{-2x}) - \frac{1}{4}(e^{2x}-2+e^{-2x})\\
&= \frac{1}{4}\bigg[ (e^{2x}-e^{2x}) + \big(2- (-2)\big) + (e^{-2x} - e^{-2x}) \bigg]\\
1 &= \frac{4}{4}
\end{aligned}$$

## $S_3$

> $$S_3 \equiv \{x,\ (x-1)^2,\ (x+1)^2\}$$

Similar to $S_2$, we can see that by subtracting $(x-1)^2$ from $(x+1)^2$ and scaling by an overall factor of $1/4$, we will obtain $x$. Therefore $S_3$ is linearly dependent.

$$\begin{aligned}
(x+1)^2 - (x-1)^2 &= (x^2 +2x +1) - (x^2 -2x + 1) \\
&= 4x\\
\\
\therefore
\frac{1}{4}\bigg((x+1)^2 - (x-1)^2\bigg) &= x
\end{aligned}$$

## $S_4$

> $$S_4 \equiv \{\sin^2{x},\ \cos^2{x},\ \sin{2x}\}$$

Recall that the Fourier series can expresses any periodic function as a linear combination of $\sin$ and $\cos$ and that the two trigonometric functions are not only linearly independent of each other, but also orthogonal to each other (via the "Harmonic Integrals"). From this, we can infer that the squares of the functions maintain the orthogonal relationship as we consider the orthogonality between polynomials of different order. From this, we can make a stronger statement about $S_4$ than just linear independence, but that the set is also orthogonal.

$$To\ Do: \text{ show scalar product between functions evaluates to 0}$$

$$\begin{aligned}
\int_{0}^{2\pi}{\sin^2{x}\cos^2{x}dx} &= 0\\
\int_{0}^{2\pi}{\sin^2{x}\sin{2x}dx} &= 0\\
\int_{0}^{2\pi}{\cos^2{x}\sin{2x}dx} &= 0
\end{aligned}$$

\pagebreak

# Question 3

> Consider the two states $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi} = 3i\ket{\phi_1}+\ket{\phi_2}$ and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\chi} = \frac{1}{\sqrt{2}} \bigg( i\ket{\phi_1}+\ket{\phi_2} \bigg)$, where $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\phi_1}$ and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\phi_2}$ form a complete and orthonormal basis.

## Part A

> Calculate $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\psi}{\psi}$, $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\psi}{\psi}$, $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\chi}{\psi}$, $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\psi}{\chi}$, and $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\chi}{\chi}$. Are the scalar products of $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\chi}{\psi}$ and $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\psi}{\chi}$ equal?

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\begin{aligned}
\braket{\psi}{\psi} &= (-3)(3)i^2 \braket{\phi_1}{\phi_1} + \braket{\phi_2}{\phi_2}\\
&= 9 + 1 = 10
\end{aligned}$$

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\begin{aligned}
\braket{\chi}{\psi} &= \frac{3i^2}{\sqrt{2}} + \frac{1}{\sqrt{2}}\\
&= \frac{-3 + 1}{\sqrt{2}} = -\sqrt{2}
\end{aligned}$$

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\begin{aligned}
\braket{\psi}{\chi} &= \frac{(-3i)(-i)}{\sqrt{2}} + \frac{1}{\sqrt{2}}\\
&= \frac{3i^2 + 1}{\sqrt{2}} = -\sqrt{2}
\end{aligned}$$

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\begin{aligned}
\braket{\chi}{\chi} &= \frac{(-i)(i)}{2} + \frac{1}{2}\\
&= \frac{1+1}{2} = 1
\end{aligned}$$

The scalar products of $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\chi}{\psi}$ and $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\psi}{\chi}$ are equal in this case because the result is a real number and taking the conjugate of a pure real number leaves it unchanged: $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}\braket{\chi}{\psi}=\braket{\psi}{\chi}^*=-\sqrt{2}$.

## Part B

> Calculate $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}} \braket{\psi+\chi}{\psi+\chi}$.

$$
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
\ket{\psi}+\ket{\chi} &= \left(3i-\frac{i}{\sqrt{2}}\right)\ket{\phi_1} + \frac{\sqrt{2}+1}{\sqrt{2}}\ket{\phi_2}\\
&=i\frac{3\sqrt{2}-1}{\sqrt{2}}\ket{\phi_1} + \frac{\sqrt{2}+1}{\sqrt{2}}\ket{\phi_2}\\
&=\frac{1}{2}\left(i(6-\sqrt{2})\ket{\phi_1} + (2+\sqrt{2})\ket{\phi_2}\right)
\end{aligned}$$

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\braket{\psi+\chi}{\psi+\chi} &= \left[\frac{1}{2}\left(i(6-\sqrt{2})\ket{\phi_1} + (2+\sqrt{2})\ket{\phi_2}\right)\right]^* \left[\frac{1}{2}\left(i(6-\sqrt{2})\ket{\phi_1} + (2+\sqrt{2})\ket{\phi_2}\right)\right]\\
&= \frac{1}{4} \left[-i^2(6-\sqrt{2})^2+(2+\sqrt{2})^2\right] \\
&= \frac{1}{4} \left[(36-12\sqrt{2}+2)+(4+4\sqrt{2}+2)\right]\\
&= \frac{1}{2} \left[(18+1+2+1)+(-6+2)\sqrt{2}\right] \\
&= \frac{1}{2} \left[22-4\sqrt{2}\right] \\
&= 11-2\sqrt{2}
\end{aligned}$$

## Part C

> Calculate $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi}\bra{\chi}$ and $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\chi}\bra{\psi}$. Are they equal?

Since the outer product does not result in a scalar value, the two outer products will not be equal as they are Hermitian Adjoints of eachother: not only is the product the complex conjugate, it is also the transpose.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
\ket{\psi}\bra{\chi} &= \frac{1}{\sqrt{2}} \bigg(3i^2\ket{\phi_1}\bra{\phi_1} + 3i\ket{\phi_1}\bra{\phi_2} + i\ket{\phi_2}\bra{\phi_1} + \ket{\phi_2}\bra{\phi_2}\bigg)\\
&\dot{=} \begin{pmatrix}
-3 & 3i \\
i & 1
\end{pmatrix}
\end{aligned}$$

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
\ket{\chi}\bra{\psi} &= \frac{1}{\sqrt{2}} \bigg((-3i)(-i)\ket{\phi_1}\bra{\phi_1} -i\ket{\phi_1}\bra{\phi_2} - 3i\ket{\phi_2}\bra{\phi_1} + \ket{\phi_2}\bra{\phi_2}\bigg)\\
&\dot{=} \begin{pmatrix}
-3 & -i \\
-3i & 1
\end{pmatrix}
\end{aligned}$$

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\ket{\psi}\bra{\chi}\neq\ket{\chi}\bra{\psi}, \qquad \ket{\psi}\bra{\chi}=\big(\ket{\chi}\bra{\psi}\big)^{\dagger}$$

## Part D

> Show that the states $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi}$ and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\chi}$ satisfy the triangle inequality.

Recall the triangle inequality states that the norm of the sum of two vectors is less than or equal to the sum of the norm between the two vectors:

$$\lVert\vec{x}+\vec{y}\rVert \leq \lVert\vec{x}\rVert + \lVert\vec{y}\rVert$$

Applying this to the two states in question, we obtain the expression:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\lVert\braket{\psi+\chi}{\psi+\chi}\rVert \leq \lVert\braket{\psi}{\psi}\rVert + \lVert\braket{\chi}{\chi}\rVert$$

Substituting in these values calculated in previous parts, we can square both sides of the equation and simplify to obtain a true statement.

$$\begin{aligned}
\sqrt{11-2\sqrt{2}} &\leq \sqrt{10} + \sqrt{1}\\
11-2\sqrt{2} &\leq (\sqrt{10} + 1)^2\\
11-2\sqrt{2} &\leq 11+2\sqrt{10}
\end{aligned}$$

## Part E

> Show that the states $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi}$ and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\chi}$ satisfy the Schwarz inequality.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
{\lvert\braket{\chi}{\psi}\rvert}^2 &\leq \braket{\psi}{\psi}\braket{\chi}{\chi}\\
2 &\leq (10)(1)\\
2 &\leq 10
\end{aligned}$$
