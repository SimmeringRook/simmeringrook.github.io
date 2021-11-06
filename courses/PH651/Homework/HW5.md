---
title: Homework 5
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Wednesday, November 3, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{HW5}
    \fancyhead[LO,LE]{Knudson}
---

\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\newcommand{\expectation}[1]{{\left\langle #1 \right\rangle}}
\newcommand{\pprime}{{\prime\prime}}

# Question 1.23

> Evaluate the $x$-$p$ uncertainty product ${\left\langle \Delta x \right\rangle}^2 {\left\langle \Delta p \right\rangle}^2$ for a one-dimensional particle confined between two rigid walls $$V = \begin{cases} 0 & \text{for } 0 < x < a \\ \infty & \text{otherwise.}\end{cases}$$ Do this for both the ground and excited states.

Recall the solution to the time-independent *particle-in-a-box* system from an introductory Quantum Mechanics course is given as:

$$\begin{aligned}
H \varphi_n (x) &= \frac{n^2 \pi^2 \hbar^2}{2m a^2} \varphi_n(x) \\
\text{where } & n\in\mathbb{Z^+},\\
& \varphi_n (x) = \sqrt{\frac{2}{a}}\sin{\frac{n\pi x}{a}}
\end{aligned}$$

## $x$

$$\begin{aligned}
\expectation{x} &= \bra{\varphi_n}\hat{x}\ket{\varphi_n} \\
&= \int_{0}^{a}{ {\varphi_n}^* (x) x \varphi_n (x) dx} \\
&= \frac{2}{a} \int_{0}^{a}{x \left(\sin{\frac{n\pi x}{a}}\right)^2 dx} \\
&= \frac{2}{a} \left(\frac{x^2}{4} - \frac{x}{4\left(\frac{n\pi}{a}\right)}\sin{2\left(\frac{n\pi x}{a}\right)} - \frac{1}{8\left(\frac{n\pi}{a}\right)^2} \cos{\left(2\frac{n\pi x}{a}\right)} \right)_0^{a}\\
&= \frac{2}{a} \left(\frac{a^2}{4} - \frac{a}{4\left(\frac{n\pi}{a}\right)}\sin{2n\pi} - \frac{1}{8\left(\frac{n\pi}{a}\right)^2} \cos{2n\pi} + \frac{1}{8\left(\frac{n\pi}{a}\right)^2} \cos{0} \right)\\
&= \frac{a}{2}
\end{aligned}$$

$$\begin{aligned}
\expectation{x^2} &= \int_{0}^{a}{ {\varphi_n}^* (x) x^2 \varphi_n (x) dx} \\
&= \frac{2}{a} \int_{0}^{a}{x^2 \left(\sin{\frac{n\pi x}{a}}\right)^2 dx} \\
&= \frac{2}{a} \left(\frac{x^3}{6} - \left(\frac{x^2}{4\left(\frac{n\pi}{a}\right)} - \frac{1}{8\left(\frac{n\pi}{a}\right)^3} \right)\sin{2\left(\frac{n\pi x}{a}\right)} - \frac{x}{4\left(\frac{n\pi}{a}\right)^2} \cos{\left(2\frac{n\pi x}{a}\right)} \right)_0^{a}\\
&= \frac{2}{a} \left(\frac{a^3}{6} - \frac{a}{4\left(\frac{n\pi}{a}\right)^2} \right)\\
&= \frac{a^2}{3} - \frac{a^2}{4 (n\pi)^2}\\
\end{aligned}$$

## $p$

$$\begin{aligned}
\expectation{p} &= \bra{\varphi_n}\hat{p}\ket{\varphi_n} \\
&= \int_{0}^{a}{ {\varphi_n}^* (x) \left(-i\hbar\frac{d}{dx}\right) \varphi_n (x) dx} \\
&= -i\hbar\frac{2}{a} \left(\frac{n\pi}{a}\right) \int_{0}^{a}{ \sin{\frac{n\pi x}{a}} \cos{\frac{n\pi x}{a}} dx} \\
&= -i\hbar\frac{2}{a} \left(\frac{n\pi}{a}\right) \left(\frac{1}{2\left(\frac{n\pi}{a}\right)} \sin^2{\frac{n\pi x}{a}}\right)_0^a \\
&= 0
\end{aligned}$$

$$\begin{aligned}
\expectation{p^2} &= \int_{0}^{a}{ {\varphi_n}^* (x) \left(-\hbar^2 \frac{d^2}{dx^2}\right) \varphi_n (x) dx} \\
&= \hbar^2 \frac{2}{a} \left(\frac{n\pi}{a}\right)^2 \int_{0}^{a}{\left(\sin{\frac{n\pi x}{a}}\right)^2 dx} \\
&= \hbar^2 \frac{2}{a} \frac{(n\pi^2)}{a^2} \left(\frac{x}{2} - \frac{1}{2a}\sin{\left(\frac{n\pi x}{a}\right)}\cos{\left(\frac{n\pi x}{a}\right)} \right)_0^{a}\\
&= \hbar^2 \frac{(n\pi^2)}{a^2}
\end{aligned}$$

## Uncertainties

Having a symmetric potential, we expect that $\expectation{x}$ is the middle of the box and $\expectation{p}$ is $0$, as no particle should have a preference for direction of travel.

$$\begin{aligned}
{\left\langle \Delta x \right\rangle}^2 {\left\langle \Delta p \right\rangle}^2 &= (\expectation{x^2} - \expectation{x}^2) (\expectation{p^2} - \expectation{p}^2) \\
&= \left(\frac{a^2}{3} - \frac{a^2}{4 (n\pi)^2} - \frac{a^2}{4}\right)\left(\hbar^2 \frac{(n\pi^2)}{a^2}\right) \\
&= \hbar^2 \left(\frac{(n\pi^2)}{12} - \frac{1}{2} \right)\\
\\
n = 1 \quad &\sqrt{\hbar^2 \left(\frac{\pi^2}{12} - \frac{1}{2} \right)} \\
& \sqrt{\frac{\pi^2}{12} - \frac{1}{2}} \approx 0.56786180838...  > \frac{1}{2}
\end{aligned}$$

As $n$ increases in integer value, the uncertainty product increases further away from the minimum of $\hbar/2$.

\pagebreak

# Question 1.29

## Part A

> Suppose that $f(A)$ is a funciton of a Hermitian operator $A$ with the property $A\ket{a^{\prime}} = a^{\prime} \ket{a^{\prime}}$. Evaluate $\bra{b^{\pprime}} f(A) \ket{b^{\prime}}$ when the transformation matrix from the $a^{\prime}$ basis to the $b^{\prime}$ basis is known.

Recall that we also know: $f(A)\ket{a^{\prime}} = f(a^{\prime}) \ket{a^{\prime}}$. Instead of trying to convert the entire expression into a different basis, let us only focus on the ket near the operator by inserting the completeness relation (or correspoding transformation matrix):

$$\begin{aligned}
\bra{b^{\pprime}} f(A) \ket{b^{\prime}} &= \bra{b^{\pprime}} f(A) \mathbb{I} \ket{b^{\prime}} \\
&= \bra{b^{\pprime}} f(A) \left(\sum_{n}{\ket{a^{\prime}}\bra{a^{\prime}}}\right) \ket{b^{\prime}} \\
&= \bra{b^{\pprime}}  \left(\sum_{n}{f(A)\ket{a^{\prime}}\braket{a^{\prime}}{b^{\prime}}}\right)  \\
&= \bra{b^{\pprime}}  \left(\sum_{n}{f(a^{\prime})\ket{a^{\prime}}\braket{a^{\prime}}{b^{\prime}} }\right)  \\
&= \sum_{n}{f(a^{\prime})\braket{b^{\pprime}}{a^{\prime}}\braket{a^{\prime}}{b^{\prime}} }
\end{aligned}$$

## Part B

$$\begin{aligned}
\bra{\vec{p}^{\pprime}} f(r) \ket{\vec{p}^{\prime}} &= \bra{\vec{p}^{\pprime}} f(r) \mathbb{I} \ket{\vec{p}^{\prime}} \\
&= \bra{\vec{p}^{\pprime}} f(r) \int_{-\infty}^{\infty}{\ket{\vec{x}^{\prime}}\braket{\vec{x}^{\prime}}{\vec{p}^{\prime}} d^3 x^{\prime} }  \\
&= \int_{-\infty}^{\infty}{\bra{\vec{p}^{\pprime}} f(r) \ket{\vec{x}^{\prime}}\braket{\vec{x}^{\prime}}{\vec{p}^{\prime}} d^3 x^{\prime} }  \\
&= \int_{-\infty}^{\infty}{f(r^{\prime}) \braket{\vec{p}^{\pprime}}{\vec{x}^{\prime}}\braket{\vec{x}^{\prime}}{\vec{p}^{\prime}} d^3 x^{\prime} }  \\
&= \int_{-\infty}^{\infty}{f(r^{\prime}) \left(\frac{1}{{(2\pi\hbar)^{3/2}}} \exp{\left(\frac{-i \vec{p}^{\pprime}\cdot\vec{x}^\prime}{h}\right)} \right) \left(\frac{1}{ {(2\pi\hbar)^{3/2}} } \exp{\left(\frac{i \vec{p}^{\prime}\cdot\vec{x}^\prime}{h}\right)} \right) d^3 x^{\prime} }  \\
&=\left(\frac{1}{{(2\pi\hbar)^3}}\right) \int_{-\infty}^{\infty}{f(r^{\prime}) \exp{\left((\nabla^{\pprime}+\nabla^{\prime})\cdot\vec{x}^\prime\right)} d^3 x^{\prime} }  \\
\end{aligned}$$

\pagebreak

# Question 1.36a

> Prove the following.

## (i)

$$\bra{p^{\prime}}x\ket{\alpha} = i\hbar \frac{\partial}{\partial p^{\prime}} \braket{p^{\prime}}{\alpha}$$

$$\begin{aligned}
\bra{p^{\prime}}x\ket{\alpha} &= \int_{-\infty}^{\infty}{\bra{p^{\prime}}\hat{x}\ket{x^{\prime}}\braket{x^{\prime}}{\alpha} dx^\prime} \\
&= \int_{-\infty}^{\infty}{x^\prime \braket{p^{\prime}}{x^{\prime}}\braket{x^{\prime}}{\alpha} dx^\prime} \\
&= \int_{-\infty}^{\infty}{x^\prime \left(\frac{1}{\sqrt{2\pi\hbar}} \exp{\left(\frac{ip^{\prime}x^{\prime}}{\hbar}\right)} \right) \braket{x^{\prime}}{\alpha} dx^\prime}\\
&= \int_{-\infty}^{\infty}{\left(\frac{i\hbar x^{\prime}}{-i\hbar}\right) \left(\frac{1}{\sqrt{2\pi\hbar}} \exp{\left(\frac{ip^{\prime}x^{\prime}}{\hbar}\right)} \right) \braket{x^{\prime}}{\alpha} dx^\prime}\\
\\
\frac{\partial}{\partial p^\prime} \exp{\left(\frac{ip^{\prime}x^{\prime}}{\hbar}\right)} &= \frac{ix^{\prime}}{\hbar}\exp{\left(\frac{ip^{\prime}x^{\prime}}{\hbar}\right)}\\
\\
&= \frac{\hbar}{-i}\int_{-\infty}^{\infty}{ \left(\frac{\partial}{\partial p^\prime} \braket{p^{\prime}}{x^{\prime}} \right)  \braket{x^{\prime}}{\alpha} dx^\prime}\\
&= i\hbar\frac{\partial}{\partial p^\prime}  \int_{-\infty}^{\infty}{ \braket{p^{\prime}}{x^{\prime}}\braket{x^{\prime}}{\alpha} dx^\prime}\\
&= i\hbar\frac{\partial}{\partial p^\prime} \braket{p^{\prime}}{\alpha} \\
\end{aligned}$$

## (ii)

$$\bra{\beta}x\ket{\alpha} = \int{dp^{\prime} {\phi_\beta}^* (p^\prime) i\hbar \frac{\partial}{\partial p^{\prime}} \phi_\alpha (p^\prime) }$$

$$\begin{aligned}
\bra{\beta}x\ket{\alpha} &= \int_{-\infty}^{\infty}{\int_{-\infty}^{\infty}{\braket{\beta}{p^{\pprime}}\bra{p^{\pprime}}\hat{x}\ket{p^{\prime}}\braket{p^{\prime}}{\alpha} dp^\pprime dp^\prime}} \\
&= \int_{-\infty}^{\infty}{\int_{-\infty}^{\infty}{{\phi_\beta}^* (p^\pprime) \left(i\hbar\frac{\partial}{\partial p^\prime} \delta(p^\pprime - p^\prime) \right) {\phi_\alpha} (p^\prime) dp^\pprime dp^\prime}}\\
&= \int_{-\infty}^{\infty}{{\phi_\beta}^* (p^\prime) i\hbar\frac{\partial}{\partial p^\prime} {\phi_\alpha} (p^\prime) dp^\prime}
\end{aligned}$$

\pagebreak

# Question 4

> Consider a Gaussian wave packet. Find expectation values of $X^2$ and $P^2$ using two approaches (i.e. expressing the states in terms of $p$-basis and $x$-basis).

\newcommand{\gwpx}[1]{{\exp{\left(ik #1 - \frac{{#1}^2}{2d^2}\right)} }}
\newcommand{\gwpxcnj}[1]{{\exp{\left(-ik #1 - \frac{{#1}^2}{2d^2}\right)} }}

## $x$-basis

Recall the $x$-basis Gaussian wave packet has the form:

$$\braket{x^\prime}{\alpha} = \frac{1}{{\pi}^{1/4} \sqrt{d}} \gwpx{x^{\prime}}$$

$$\begin{aligned}
\expectation{X^2} &= \int_{-\infty}^{\infty} { dx^{\prime} \frac{1}{{\pi}^{1/4} \sqrt{d}} \gwpxcnj{x^{\prime}} X^2 \frac{1}{{\pi}^{1/4} \sqrt{d}} \gwpx{x^{\prime}} }\\
&= \frac{1}{\sqrt{\pi} d} \int_{-\infty}^{\infty} { dx^{\prime} (x^{\prime})^2 \exp{\left(-\frac{x^{\prime}}{d}\right)^2} }\\
\\
\int_{-\infty}^{\infty}{x^2 \exp{\left(-\frac{x^2}{\alpha^2}\right)}dx } &= \sqrt{\pi} \frac{\alpha^{3}}{2} \\
\\
&= \frac{1}{\sqrt{\pi} d} \left(\sqrt{\pi} \frac{d^{3}}{2}\right) \\
&= \frac{d^2}{2}
\end{aligned}$$

Noting that $P^2$ in $x$-basis is $-\hbar^2 \frac{\partial}{\partial x^2}$, let's use some substitution to clean up the second derivative of the Gaussian:

$$\begin{aligned}
u &= \left(ikx - \frac{x^2}{2d^2}\right) \\
du &= \left(ik - \frac{x}{d^2}\right)dx \\
d^2 u &= -\frac{1}{d^2} d^2 x\\
\\
d(e^u) &= du e^u \\
d(du e^u) &= d^2 u e^u + (du)^2 e^u \\
&= (d^2 u + (du)^2) e^u\\
\\
P^2 \left( \gwpx{x} \right) &= -\hbar^2\left(-\frac{1}{d^2} + {\left(ik - \frac{x}{d^2}\right)}^2 \right) \gwpx{x}\\
&= -\hbar^2\left(-\frac{1}{d^2} -k^2 -\frac{2ikx}{d^2} + \frac{x^2}{d^4} \right) \gwpx{x}
\end{aligned}$$

$$\begin{aligned}
\expectation{P^2} &= -\hbar^2\frac{1}{\sqrt{\pi} d} \int_{-\infty}^{\infty} { dx^{\prime} \left(-\frac{1}{d^2} -k^2 -\frac{2ikx^{\prime}}{d^2} + \frac{(x^{\prime})^2}{d^4} \right) \exp{\left(-\frac{x^{\prime}}{d}\right)^2} }\\
\\
& -\hbar^2\frac{1}{\sqrt{\pi} d}\left(-\frac{1}{d^2} -k^2\right) \int_{-\infty}^{\infty} { dx^{\prime} \exp{\left(-\frac{x^{\prime}}{d}\right)^2} }\\
& \Rightarrow \hbar^2\left(\frac{1}{d^2} + k^2\right)\\
\\
& \frac{1}{\sqrt{\pi} d} \int_{-\infty}^{\infty} { dx^{\prime} \left(-\frac{2ik}{d^2}\right) x^\prime \exp{\left(-\frac{x^{\prime}}{d}\right)^2} }\\
& \Rightarrow 0 \qquad \text{integrating odd function} \\
\\
& \frac{1}{\sqrt{\pi} d} \int_{-\infty}^{\infty} { dx^{\prime} \left(\frac{(x^{\prime})^2}{d^4} \right) \exp{\left(-\frac{x^{\prime}}{d}\right)^2} }\\
& \Rightarrow -\hbar^2\frac{1}{\sqrt{\pi} d^5}\left(\sqrt{\pi} \frac{d^{3}}{2}\right) = \frac{\hbar^2}{2d^2}\\
\\
&= \hbar^2\left(\frac{1}{d^2} + k^2\right) + 0 - \frac{\hbar^2}{2d^2} \\
&= \frac{\hbar^2}{2d^2} + \hbar^2k^2
\end{aligned}$$


## $p$-basis

\newcommand{\gwpp}{{\sqrt{\frac{d}{\hbar\sqrt{\pi}}} \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{2\hbar^2}\right)} }}

Same procedure: noting that $X^2$ in $p$-basis is $-\hbar^2 \frac{\partial}{\partial p^2}$, let's use some substitution to clean up the second derivative of the Gaussian:

$$\begin{aligned}
u &= -\frac{ d^2}{2\hbar^2} (p^\prime -\hbar k)^2 \\
du &= -\frac{d^2}{\hbar^2} (p^\prime -\hbar k) dp^\prime \\
d^2 u &= -\frac{d^2}{\hbar^2} d^2 p^\prime\\
\\
d(e^u) &= du e^u \\
d(du e^u) &= d^2 u e^u + (du)^2 e^u \\
&= (d^2 u + (du)^2) e^u\\
\\
X^2 \left( \gwpp \right) &= -\hbar^2\left( -\frac{d^2}{\hbar^2} + \frac{d^4}{\hbar^4}(p^\prime -\hbar k)^2 \right) \gwpp\\
&= d^2\left(1 - \frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2} \right) \gwpp\\
\end{aligned}$$

$$\begin{aligned}
\expectation{X^2} &= d^2\frac{d}{\hbar\sqrt{\pi}} \int_{-\infty}^{\infty} { dp^{\prime} \left(1 - \frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2} \right) \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2}\right)} }\\
\\
& d^2\frac{d}{\hbar\sqrt{\pi}}\int_{-\infty}^{\infty} { dp^{\prime} \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2}\right)} }\\
& \Rightarrow d^2\\
\\
& \frac{d^4}{\hbar^2}\frac{d}{\hbar\sqrt{\pi}}\int_{-\infty}^{\infty} { dp^{\prime} {p^\prime}^2 \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2}\right)} }\\
& \frac{d^4}{\hbar^2}\frac{d}{\hbar\sqrt{\pi}}\left(\sqrt{\pi}\frac{\hbar^3}{4d^3}\right) = \frac{d^2}{4}\\
\\
& \frac{d^4}{\hbar^2}\frac{d}{\hbar\sqrt{\pi}}\int_{-\infty}^{\infty} { dp^{\prime} (-2{p^\prime}\hbar k) \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2}\right)} }\\
& \Rightarrow 0 \qquad \text{integrating odd function} \\
\\
& \frac{d^4}{\hbar^2}\frac{d}{\hbar\sqrt{\pi}}\int_{-\infty}^{\infty} { dp^{\prime} (\hbar^2 k^2) \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2}\right)} }\\
& \Rightarrow d^4 k^2\\
\\
&= d^2 - \frac{d^2}{4} + 0 - d^4k^2\\
&\neq \frac{d^2}{2}
\end{aligned}$$

Tried to figure out where I went wrong, couldn't find the mistake.

$$\begin{aligned}
\expectation{P^2} &= \frac{d}{\hbar\sqrt{\pi}}\int_{-\infty}^{\infty} { dp^{\prime} \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{2\hbar^2}\right)} P^2 \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{2\hbar^2}\right)} }\\
&= \frac{d}{\hbar\sqrt{\pi}} \int_{-\infty}^{\infty} { dp^{\prime} (p^{\prime})^2 \exp{\left(-\frac{(p^\prime -\hbar k)^2 d^2}{\hbar^2}\right)} }\\
&= \frac{\hbar^2}{2d^2} + \hbar^2 k^2
\end{aligned}$$
