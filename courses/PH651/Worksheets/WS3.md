---
title: Worksheet 3
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Monday, September 27, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[LO,LE]{Knudson}
---

# Question

> Are the following functions linearly independent or dependent: $$f(x) = \cos(x), g(x) = e^{ix}, h(x) = \sin(x)$$

Recalling Euler's identity, we know that $e^{ix}$ is the linear combination of $\cos{x}+i\sin{x}$, and we can immediately state that the set $\{f(x),\ g(x),\ h(x)\}$ is linearly dependent.

If we exclude $g(x)$ from consideration, we can then state that the set $\{f(x),\  h(x)\}$ is not only linearly independent, but also othornormal.[^1]

Similarly, if we only consider the set that contains $g(x)$ and either $f(x)$ or $h(x)$, each of those sets are linearly independent as well.

[^1]: Here we used the fact that $\sin{x}$ and $\cos{x}$ are orthogonal along a full period of $x$ from the Fourier basis and this result can be shown from the Harmonic integrals.
