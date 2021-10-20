---
title: Worksheet 9
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Monday, October 18, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{WS 9}
    \fancyhead[LO,LE]{Knudson}
---

$$\ $$

# Prompt

A $1D$ system is in a state describe by a well-behaved real wave function: $\psi(x)$. Find the expectation value of the momentum.

# Solution

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\psi}\hat{P}\ket{\psi} &= \int_{-\infty}^{\infty}{dx^{\prime} dx^{\prime\prime} \braket{\psi}{x^{\prime}}\bra{x^{\prime}}\hat{P}\ket{x^{\prime\prime}}\braket{x^{\prime\prime}}{\psi} }\\
&= \int_{-\infty}^{\infty}{dx^{\prime} dx^{\prime\prime} \psi^* (x^{\prime})\bra{x^{\prime}} \left(-i\hbar\frac{\partial}{\partial x^{\prime}}\delta(x^{\prime}-x^{\prime\prime})\right) \ket{x^{\prime\prime}} \psi(x^{\prime\prime}) }\\
&= -i\hbar\int_{-\infty}^{\infty}{dx^{\prime} \psi (x^{\prime})\frac{\partial}{\partial x^{\prime}}\psi(x^{\prime}) }
\end{aligned}$$

Let $u(x^{\prime}) = \psi(x^{\prime})$ such that $du = \frac{d\psi(x^{\prime})}{dx^{\prime}}dx^{\prime}$. Recall since $\psi(x^{\prime})$ is well-behaved, the wavefunction goes to $0$ at $\pm\infty$: $u(-\infty) = \psi(-\infty) = 0$ and $u(\infty) = \psi(\infty) = 0$.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\begin{aligned}
\bra{\psi}\hat{P}\ket{\psi} &= -i\hbar\int_{0}^{0}{udu} \\
&= 0
\end{aligned}$$

Which is what we anticipate in the general case. The position wavefunction only works to describe location, not the direction of travel, and without more information (a perturbation), we assume the particle would be equally likely to be traveling in the $+x^{\prime}$ direction as $-x^{\prime}$.