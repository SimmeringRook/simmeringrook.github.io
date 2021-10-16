---
title: Worksheet 8
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Wednesday, October 13, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{WS 8}
    \fancyhead[LO,LE]{Knudson}
---

$$\ $$

# Prompt

Consider unitary transformation of the position operator $X$:

$$X' = U X U^\dagger$$

If $U=I+i\epsilon G$, where:

- $I$ is the identity operator,
- $\epsilon$ is a real infinitesimal number,
- and $G$ is a Hermitian operator whichs is a generator of the space translation along $x$ $$G=\frac{P_x}{\hbar}$$

What is $X'$? In your derivation, neglect a term proportional to $\epsilon^2$.

# Solution

Let's carry this out symbolically, before substitutions:

$$\begin{aligned}
X' &= U X U^\dagger \\
&= (I + i\epsilon G) X (I - i\epsilon G) \\
&= (I + i\epsilon G) (X- i\epsilon XG)\\
&= X + i\epsilon GX - i\epsilon XG -i^2 \epsilon^2 GXG\\
&= X + i\epsilon [G,X] + \mathcal{O}(\epsilon^2)
\end{aligned}$$

$$X' \simeq X + i\epsilon\left[\frac{P_x}{\hbar}, X\right]$$

> Under what condition would $X$ not change under space translation?

If $G$ and $X$ commuted, $[G,X]=\left[\frac{P_x}{\hbar}, X\right]=0$, then under this translation $X'$ would simplify down to $X$.
