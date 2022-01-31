---
title: Homework 1
subtitle: AEC 353, W2022
author: Thomas Knudson
date: Thursday, January 6, 2022
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usepackage{fancyhdr}
    \usepackage{float}
    \usepackage{subcaption}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{AEC 353, W2022}
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
 - $\gamma = -0.2824$
 - $\chi = -6941.57$
 - $\varphi = \frac{2.5}{100}(3691.15)$

$$\begin{aligned}
\alpha\bigg(\beta + \gamma (1+2x)\bigg) &= \frac{\alpha}{100}\bigg(\alpha(\beta x + \gamma x^2) + \chi\bigg) + \varphi \\
\beta + \gamma + 2\gamma x &= \frac{\alpha\beta}{100} x + \frac{\alpha\gamma}{100} x^2 + \frac{\chi}{100} + \frac{\varphi}{\alpha} \\
\frac{\alpha\gamma}{100} x^2 + x \left(\frac{\alpha\beta}{100} - 2\gamma\right) &= \beta + \gamma - \left(\frac{\chi}{100} + \frac{\varphi}{\alpha}\right)
\end{aligned}$$

To further clean this and to reveal the underlying structure, let us introduce the following secondary substitutions,

$$a = \frac{\alpha\gamma}{100}, \quad b = \left(\frac{\alpha\beta}{100} - 2\gamma\right), \quad -c = \beta + \gamma - \left(\frac{\chi}{100} + \frac{\varphi}{\alpha}\right),$$

such that our expression now takes the form of $a x^2 + bx = -c$. Noting that this is the general form for a quadratic, we can immediately move to apply the quadratic formula and note that the roots of $x$ are given by:

$$\frac{-b\pm\sqrt{b^2 - 4ac}}{2a}$$

Undoing all of the substitution, we then obtain the following possible solutions:

$$\begin{aligned}
x &= \frac{-\left(\frac{\alpha\beta}{100} - 2\gamma\right)\pm\sqrt{\left(\frac{\alpha\beta}{100} - 2\gamma\right)^2 + 4\frac{\alpha\gamma}{100}\left(\beta + \gamma - \left(\frac{\chi}{100} + \frac{\varphi}{\alpha}\right)\right)}}{2\frac{\alpha\gamma}{100}}\\
&= \frac{-\left(\frac{2.5(141.2)}{100} + 2(0.2824)\right)\pm\sqrt{\left(\frac{2.5(141.2)}{100} + 2(0.2824)\right)^2 + 4\frac{2.5(-0.2824)}{100}\left(141.2 -0.2824) - \left(-\frac{6941.57}{100} + \frac{3691.15}{100}\right)\right)}}{2\frac{2.5(-0.2824)}{100}}\\
&= \frac{-4.0948 \pm \sqrt{4.0948^2-4(0.00706)(173.422)}}{2(-0.00706)}\\
&= 46,\ 534
\end{aligned}$$

\pagebreak

# Question 2

## Part A

\begin{figure}[H]
      \centering
\includegraphics[scale=.1]{2a.jpg}
\end{figure}

\pagebreak

## Part B

\begin{figure}[H]
      \centering
\includegraphics[scale=.1]{2b.jpg}
\end{figure}

\pagebreak

## Part C

\begin{figure}[H]
      \centering
\includegraphics[scale=.1]{2c.jpg}
\end{figure}

\pagebreak

# Question 3

\begin{figure}[H]
      \centering
\includegraphics[scale=.1]{3.jpg}
\end{figure}
