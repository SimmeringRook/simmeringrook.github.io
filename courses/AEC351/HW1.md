---
title: Homework 1
subtitle: AEC 351, W2022
author: Thomas Knudson
date: Thursday, January 6, 2022
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{AEC 351, W2022}
    \fancyhead[CO,CE]{HW1}
    \fancyhead[LO,LE]{Knudson}
---

# Question 1

> Solve each of the following equations for the unknown variable $x$.

## Part A

$$\begin{aligned}
2x -3 &= 13 \\
2x &= 16 \\
x &= 8
\end{aligned}$$

## Part B

$$\begin{aligned}
10 + \frac{x}{2} &= 80 + \frac{3}{7}x \\
x \left(\frac{3}{7} - \frac{1}{2}\right) &= - 70 \\
x \left(\frac{3 - 7}{14}\right) &= - 70 \\
x &= -70\left(-\frac{14}{4}\right)\\
x &= 70\left(\frac{7}{2}\right)\\
&= 245
\end{aligned}$$

## Part C

$$\begin{aligned}
\sqrt{x^2 + 5x} &= 5 \\
x^2 + 5x &= 25
\end{aligned}$$

Recall the strategy of completing the square:

$$x^2 + bx + \left(\frac{b^2}{4}-\frac{b^2}{4}\right) \Rightarrow \left(x+\frac{b}{2}\right)^2 - \frac{b}{2}$$

$$\begin{aligned}
x^2 + 5x + \frac{25}{4} - \frac{25}{4} &= 25 \\
\left(x + \frac{5}{2}\right)^2 &= 25\left(1+\frac{1}{4}\right) \\
x + \frac{5}{2} &= \pm \sqrt{25 \cdot \frac{5}{4}} \\
x + \frac{5}{2} &= \pm \frac{5}{2} \sqrt{5} \\
x &= \frac{5}{2} \left(\pm\sqrt{5}-1\right)
\end{aligned}$$

## Part D

For this to be a valid expression we note that the products of $r\left(1-\frac{x}{K}\right)$ and $qE$ must be dimensionless, as both the arguement of $e$ and $e$ itself are dimensionless quanitities. We also assume that $x\neq 0$ during the first step of simplification:

$$\begin{aligned}
x\exp{\left( r\left(1-\frac{x}{K}\right) \right)} &= qE x\\
\exp{\left( r\left(1-\frac{x}{K}\right) \right)} &= qE\\
r\left(\frac{K-x}{K}\right) &= \ln{qE} \\
K-x &= \frac{K}{r} \ln{qE} \\
x &= K - \frac{K}{r} \ln{qE} \\
 &= K \left(1 - \frac{\ln{qE}}{r}\right)
\end{aligned}$$

## Part E

$$2.5\bigg(141.2 - 0.2824 (1+2x)\bigg) = 0.025\bigg(2.5(141.2x-0.2824x^2)-6941.57\bigg) + 0.025(3691.15)$$

Let:
 - $\alpha = 2.5$
 - $\beta = 141.2$
 - $\xi = -0.2824$
 - $\varphi = -6941.57$
 - $\chi = 3691.15$

$$\alpha\bigg(\beta + \xi (1+2x)\bigg) = \frac{\alpha}{100}\bigg(\alpha(\beta x + \xi x^2) + \varphi\bigg) + \frac{\alpha}{100}\chi$$

Expanding out, we can work to isolate powers of $x$ to one side and all other constants to the other:

Divide both sides by the reciprocal of $\alpha/100$:
$$\begin{aligned}
\frac{100}{\alpha}\alpha\bigg(\beta + \xi (1+2x)\bigg) &= \frac{100}{\alpha} \bigg [\frac{\alpha}{100}\bigg(\alpha(\beta x + \xi x^2) + \varphi\bigg) + \frac{\alpha}{100}\chi \bigg] \\
100\bigg(\beta + \xi (1+2x)\bigg) &= \bigg(\alpha(\beta x + \xi x^2) + \varphi\bigg) + \chi \\
100(\beta + \xi) + 200\xi x &= \alpha\beta x + \alpha\xi x^2 + \varphi + \chi \\
\alpha\xi x^2 + (\alpha\beta -200\xi)x &= \varphi + \chi - 100(\beta + \xi) \\
\end{aligned}$$

To further clean this up before completing the square, let's introduce the following substitutions,

$$a = \alpha\xi, \quad b = \alpha\beta - 200\xi, \quad c=\varphi+\chi-100(\beta+\xi),$$

such that our expression now takes the form of $a x^2 + bx = c$.

$$\begin{aligned}
a x^2 + bx &= c\\
x^2 + \frac{b}{a}x + 0 &= \frac{c}{a}\\
x^2 + \frac{b}{a}x + \left(\frac{b}{2a}\right)^2 - \left(\frac{b}{2a}\right)^2 &= \frac{c}{a} \\
\left(x + \frac{b}{2a} \right)^2 &= \frac{c}{a} + \frac{b^2}{4a^2} \\
\sqrt{\left(x + \frac{b}{2a} \right)^2} &= \sqrt{\frac{4ac+b^2}{4a^2}} \\
x + \frac{b}{2a} &= \frac{\sqrt{4ac+b^2}}{2a} \\
x &= \frac{-b+\sqrt{4ac+b^2}}{2a}
\end{aligned}$$
