---
title: Homework 1
subtitle: MTH 438, S2022
author: Thomas Knudson
date: April 15, 2022
papersize: a4
geometry: margin=2cm
toc: true
toc_depth: 2
header-includes: |
    \usepackage{fancyhdr}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usepackage{float}
    \usepackage{subcaption}
    \pagestyle{fancy}
    \usetikzlibrary{shapes.geometric}
    \usetikzlibrary{calc}
    \usetikzlibrary{angles}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{MTH 438, S2022}
    \fancyhead[CO,CE]{HW1}
    \fancyhead[LO,LE]{Knudson}
---

\pagebreak

## Problem 1.1

> Let $z=1+2i$ and $w=2-i$.

### Part B

>Compute $\bar{w}-z$

\begin{align*}
\bar{w}=2+i, \qquad \bar{w}-z &= (2+i) - (1+2i) \\
&= 1 - i
\end{align*}

### Part D

>Compute $\text{Re}(w^2+w)$

\begin{align*}
\text{Re}(w^2+w) &= \text{Re}\bigg((2-i)^2+(2-i)\bigg) \\
&= \text{Re}\bigg((4-4i+(-1))+2-i\bigg) \\
&= \text{Re}(5-5i) \\
&= 5
\end{align*}

## Problem 1.2

> Find the real and imaginary parts of each of the following and let $z=x+iy$ with $x,y\in\mathbb{R}$:

### Part A

> $$\frac{z-a}{z+a}, \quad \forall a \in \mathbb{R}$$

\begin{equation*}
\begin{aligned}
\text{Re}(z) &= x\\
\\
\text{Re}\left(\frac{z-a}{z+a}\right) &= \frac{\text{Re}(z-a)}{\text{Re}(z+a)} \\
&= \frac{x-a}{x+a}
\end{aligned}, \qquad
\begin{aligned}
\text{Im}(z) &= y \\
\\
\text{Im}\left(\frac{z-a}{z+a}\right) &= \frac{\text{Im}(z-a)}{\text{Im}(z+a)} \\
&= \frac{y}{y} = 1
\end{aligned}
\end{equation*}

### Part D

> $i^n$ for any $n\in\mathbb{Z}$

\begin{align*}
\text{if } n \mod 4 = 0, \quad & i^n = 1 \\
\text{if } n \mod 4 = 1, \quad & i^n = i \\
\text{if } n \mod 4 = 2, \quad & i^n = -1 \\
\text{if } n \mod 4 = 3, \quad & i^n = -i
\end{align*}

Then:

\begin{equation*}
\text{Re}(i^n) = \begin{cases}
\ \ 1, & n \mod 4 = 0 \\
\ \ 0, & n \mod 4 = 1 \\
-1, & n \mod 4 = 2 \\
\ \ 0, & n \mod 4 = 3
\end{cases}, \qquad
\text{Im}(i^n) = \begin{cases} 
\ \ 0, & n \mod 4 = 0 \\
\ \ 1, & n \mod 4 = 1 \\
\ \ 0, & n \mod 4 = 2 \\
-1, & n \mod 4 = 3
\end{cases}
\end{equation*}

## Problem 1.3, Part C

> Find the absolute value and conjugate of $$\frac{3-i}{\sqrt{2}+3i}$$

\begin{equation*}
\begin{aligned}
\bar{z} &= \frac{3+i}{\sqrt{2}-3i}
\end{aligned}, \qquad
\begin{aligned}
\vert z \vert &= \sqrt{z\bar{z}} \\
&= \sqrt{\left(\frac{3-i}{\sqrt{2}+3i}\right)\left(\frac{3+i}{\sqrt{2}-3i}\right)} \\
&= \sqrt{\frac{9+1}{2+9}} \\
&= \sqrt{\frac{10}{11}}
\end{aligned}
\end{equation*}

## Problem 1.4, Part B

>Write $z=1+i$ in polar form.

\begin{equation*}
z = 1 + i = re^{i\phi}
\end{equation*}

\begin{equation*}
\begin{aligned}
r &= \sqrt{x^2 + y^2} \\
&= \sqrt{1+1} \\
&= \sqrt{2}
\end{aligned}, \qquad
\begin{aligned}
\phi &= \arctan{\frac{y}{x}} \\
&= \arctan{1} \\
&= \frac{\pi}{4}
\end{aligned}
\end{equation*}

\begin{equation*}
z = \sqrt{2}\exp{\left(i\frac{\pi}{4}\right)}
\end{equation*}

## Problem 1.9

>Find all solutions of the equation $z^2 + 2z + (1-i) = 0$.

Consider two complex numbers $z$ and $w$ and the quadratic 

\begin{equation}
az^2 + bz + w = 0,
\end{equation}

with the scalars $a,b\in\mathbb{R}$. Then we can find what values of $z$, dependent on $w$, to cause this expression to be true by completing the square. We ignore the cases of $a,b=0$ as the expression simplifies to $w=0$, and $z$ could be any complex number and $w$ must be $0$. For the case where $b$ is zero and $a$ is non-zero, the solution is $z=\pm \sqrt{-w/a}$, but this is unhelpful for the proposed equation. Similarly, for the case where $a$ is zero and $b$ is non-zero, the equation has solutions of $z=-b/a$ but is also not applicable to the requested equation. So, we then consider the quadratic whose $a$ and $b$ scalars are non-zero.

\begin{align*}
z^2 + \frac{b}{a}z &= -\frac{w}{a} \\
z^2 + \frac{b}{a}z + \frac{b^2}{4a^2} - \frac{b^2}{4a^2} &= -\frac{w}{a} \\
z^2 + \frac{b}{a}z + \frac{b^2}{4a^2} &= \frac{b^2}{4a^2} -\frac{w}{a}
\end{align*}

\begin{align*}
\left(z + \frac{b}{2a}\right)^2 &= \frac{b^2}{4a^2} -\frac{4aw}{4a^2} \\
z + \frac{b}{2a} &= \pm \sqrt{\frac{b^2 - 4aw}{4a^2}} \\
z &= - \frac{b}{2a} \pm \frac{\sqrt{b^2 - 4aw}}{2a} \\
&= - \frac{b \pm \sqrt{b^2 - 4aw}}{2a}
\end{align*}

We note that for the case of $b^2 > 4aw$ and $w$ only has a real component, this gives the quadratic formula and $z$ has real solutions as we would expect. Substituting in $a=1$, $b=2$, and $w=1-i$, we find the two possible solutions for $z$ (in rectangular form) to be

\begin{equation}\label{eqn:9sol}
z = -1 + \sqrt{i}, \qquad z= -1 - \sqrt{i}.
\end{equation}

Alternatively, we can express these solutions without $\sqrt{i}$ by considering the polar form of $z^\prime$ as $$\sqrt{\exp{\left(i\frac{\pi}{2}\right)}}.$$ Then $z^\prime$ simplifies to $\exp{(i\frac{\pi}{4})}$ and its correspond rectangular form is given by $r^\prime = \sqrt{(x^\prime)^2 + (y^\prime)^2}$. Plotting this complex number in the complex plane,

\begin{figure}[H]
    \centering
    \begin{tikzpicture}

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (Y) at (0,4);
    \coordinate (X) at (4,0);
    \coordinate (R) at (3,3);
    \coordinate (x) at (3,0);
    \coordinate (y) at (0,3);

    % Draw axes and label
    \draw[-stealth, gray] (O) --++ (X);
    \node at (X) [below, font=\fontsize{12}{0}] {$x$};
    \draw[-stealth, gray] (O) --++ (Y);
    \node at (Y) [left, font=\fontsize{12}{0}] {$y$};

    % Label the point
    \node at (R) [above, right, font=\fontsize{12}{0}] {$z^\prime$};

    % Construct triangle
    \draw[dashed] (x) -- (R) node[midway, right] {$y^\prime$};
    \draw[dashed] (O) -- (x) node[midway, below] {$x^\prime$};
    \draw[-stealth, line width=2pt] (O) --++ (R) node[midway, above] {$r^\prime$};
    \tkzFillAngle[fill=orange, opacity=0.4](X,O,R);
    \tkzLabelAngle[pos=0.8](X,O,R){$\frac{\pi}{4}$};

    \end{tikzpicture}
\end{figure}

we can see that it does not correspond to a pure imaginary or pure real number, and in fact must have equal contributions from $x^\prime$ and $y^\prime$. The triangle with side lengths of $x^\prime$ and $y^\prime$ with a hypotenuse of $r^\prime$ form a $45$-$45$-$90$ triangle which allows us to conclude that $x^\prime = y^\prime = 1/\sqrt{2}$. Substituting this back into Equation \ref{eqn:9sol}, we obtain the equivalent solutions of

\begin{equation*}
z = -1 + \left(\frac{1+i}{\sqrt{2}}\right), \qquad z= -1 - \left(\frac{1+i}{\sqrt{2}}\right).
\end{equation*}

\pagebreak

## Problem 1.17

> Fix a positive integer $n$. Prove that the solutions to the equation $z^n = 1$ are precisely $z=e^{2\pi i \frac{m}{n}}$ where $m\in\mathbb{Z}$.

First, let us begin by considering the polar form of $z$. If $z=re^{i\phi}$, then $z^n = r^n e^{i\phi n}$. While trivial, we proceed to argue that $r=1$ is the only possible valid value for $z^n$.

1. Suppose $r=0$, then $z^n = 0^n e^{i \phi n} = 0$, which contradicts the given equality. If $\vert r \vert >0$, then $r^n > 1$ for $n\in 2\mathbb{Z}$ and $r^n < 1$ for $n\in (2\mathbb{Z}+1)$. Similarly, if $1 > \vert r \vert > 0$, then $r^n < 1$ for both $n\in 2\mathbb{Z}$ and $n\in (2\mathbb{Z}+1)$. The only possible value for $r$ that does not contradict the given equality is for $r$ to be equal to unity.

2. With $r=1$, $z^n$ can then be simplified to $e^{i\phi n}$. If we then consider the series expansion of $e^{i \phi n}$, we can decompose this summation into two sums: one real and one imaginary. \begin{align*}
e^{i\phi n} &= \sum_{k=0}^{\infty}{\frac{(i\phi n)^k}{k!}}, \quad k\in\mathbb{N}\\
&= \sum_{k=0}^{\infty}{\frac{(i\phi n)^{2k}}{(2k)!}} + \sum_{k=0}^{\infty}{\frac{(i\phi n)^{2k+1}}{(2k+1)!}} \\
&= \sum_{k=0}^{\infty}{\frac{(-1)^k (\phi n)^{2k}}{(2k)!}} + i\sum_{k=0}^{\infty}{\frac{(-1)^k (\phi n)^{2k+1}}{(2k+1)!}} \\
&= \cos{(\phi n)} + i \sin{(\phi n)} \\
\end{align*} Let $\theta$ represent the product of $\phi$ and $n$.