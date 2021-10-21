---
title: Homework 4
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Wednesday, October 20, 2021
papersize: a4
geometry: margin=1.5cm
linkcolor: blue
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz-3dplot}
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 531, Fall 2021}
    \fancyhead[CO,CE]{HW4}
    \fancyhead[LO,LE]{Knudson}
---

\newcommand{\rprime}{r^{\prime}}
\newcommand{\vrprime}{ {\vec{r}\ }^{\prime} }
\newcommand{\magv}[1]{{\left\lvert \vec{#1} \right\rvert}}

# Problem 3.28

> A circular ring in the $xy$ plane (radius $R$, centered at the origin) carries a uniform line charge $\lambda$. Find the first three terms ($n=0,1,2$) in the multipole expansion for $V(r,\theta)$.

$$V_{mono} (r,\theta) = \frac{1}{4\pi\epsilon_0}\frac{2\pi\lambda R}{r}, \qquad V_{dipole} = 0, \qquad V_{n=3} (r,\theta) = \frac{1}{4\pi\epsilon_0}\frac{\pi\lambda R^3}{2r^3} \left(3\sin^2{\theta}  - 2 \right) \quad\text{or}\quad -\frac{1}{4\pi\epsilon_0}\frac{\pi\lambda R^3}{r^3} P_2(\cos{\theta})$$

Recall Equation 3.95:

$$V(\vec{r}) = \frac{1}{4\pi\epsilon_0} \sum_{n=0}^{\infty}{ \frac{1}{\magv{r}^{n+1}} \int{(\left\lvert \vrprime \right\rvert)^n P_n (\cos{\alpha}) \rho(\vrprime) d\tau^{\prime} } }$$

To use Equation 3.95, we must find $\vec{r}$, $\vrprime$, $\cos{\alpha}$, and $\rho(\vrprime)d\tau^{\prime}$ for this physical situation. Since we are dealing with a ring of uniform charge density, $\rho(\vrprime)d\tau^{\prime}$ is easy: $\lambda Rd\phi^{\prime}$. Considering our arbitrary point in space, we note that $\lambda$ is uniform, and as we rotate about the axis of symmetry for this ring ($\hat{z}$ in this case), the charge density we observe does not change and we can conclude that $\varphi$ will have no influence on the $V(\vec{r})$. Then, leveraging this symmetry, let us define our two position vectors:

$$\begin{aligned}
\begin{aligned}
\vec{r} &= r \hat{r} \\
&= r (\sin{\theta}\cos{\varphi}\hat{x} + \sin{\theta}\sin{\varphi} \hat{y} + \cos{\theta} \hat{z}) \\
\text{Set }\varphi &= 0\\
&= r (\sin{\theta}\hat{x} + \cos{\theta} \hat{z}) \\
\\
\magv{r} &= r
\end{aligned} \qquad & \qquad\begin{aligned}
\vrprime &= \rprime {\hat{r}\ }^{\prime} \\
&= R (\sin{\theta^{\prime}}\cos{\varphi^{\prime}}\hat{x} + \sin{\theta^{\prime}}\sin{\varphi^{\prime}} \hat{y} + \cos{\theta^{\prime}} \hat{z}) \\
xy\text{-plane}&\text{ is when }\theta^{\prime} = \frac{\pi}{2} \\
&= R (\cos{\varphi^{\prime}}\hat{x} + \sin{\varphi^{\prime}} \hat{y}) \\
\\
\left\lvert \vrprime \right\rvert &= R
\end{aligned}
\end{aligned}$$

Now we can just use the geometric definition of the inner product in $\mathbb{E}^3$ to find $\cos{\alpha}$:

$$\begin{aligned}
\cos{\alpha} &= \hat{r} \cdot {\hat{r}\ }^{\prime} \\
&= (\sin{\theta}\hat{x} + \cos{\theta} \hat{z}) \cdot (\cos{\varphi^{\prime}}\hat{x} + \sin{\varphi^{\prime}} \hat{y}) \\
&= \sin{\theta}\cos{\varphi^{\prime}} \\
\\
P_n(\cos{\alpha}) &= P_n(\sin{\theta}\cos{\varphi^{\prime}})
\end{aligned}$$

We have all of our unknowns, and can proceed with substituting into the equation for a multipole expansion about this ring:

| $n$ | $P_n(\sin{\theta}\cos{\varphi^{\prime}})$ | the Integrand |
| - | -- | --- |
| $$0$$ | $$1$$ | $$\lambda Rd\phi^{\prime}$$ |
| $$1$$ | $$x$$ | $$R(\sin{\theta}\cos{\varphi^{\prime}})\lambda Rd\phi^{\prime}$$ |
| $$2$$ | $$\frac{3x^2 -1}{2}$$ | $$R^2 \frac{3(\sin{\theta}\cos{\varphi^{\prime}})^2 - 1}{2}\lambda Rd\phi^{\prime}$$ |

$$\begin{aligned}
V_{mono} (r,\theta) &= \frac{1}{4\pi\epsilon_0}\frac{\lambda R}{r} \int_{0}^{2\pi}{d\phi^{\prime}} \\
&= \frac{1}{4\pi\epsilon_0}\frac{2\pi\lambda R}{r}
\end{aligned}$$

$$\begin{aligned}
V_{dipole} (r,\theta) &= \frac{1}{4\pi\epsilon_0}\frac{\lambda R^2}{r^2}\sin{\theta} \underbrace{\int_{0}^{2\pi}{\cos{\varphi^{\prime}}d\phi^{\prime}}}_{\text{integrating an even function}} \\
&= 0
\end{aligned}$$

$$\begin{aligned}
V_{n=3} (r,\theta) &= \frac{1}{4\pi\epsilon_0}\frac{\lambda R^3}{r^3} \frac{1}{2}\left(3\sin^2{\theta}\int_{0}^{2\pi}{ \cos^2{\varphi^{\prime}} d\phi^{\prime}} - \int_{0}^{2\pi}{d\phi^{\prime}}\right)  \\
&= \frac{1}{4\pi\epsilon_0}\frac{\lambda R^3}{r^3} \frac{1}{2}\left(3\sin^2{\theta} \left(\frac{\varphi^{\prime}}{2}+\frac{\sin{\varphi^{\prime}}\cos{\varphi^{\prime}}}{2}\right)_{0}^{2\pi} - 2\pi \right) \\
&= \frac{1}{4\pi\epsilon_0}\frac{\pi\lambda R^3}{2r^3} \left(3\sin^2{\theta}  - 2 \right)
\end{aligned}$$

If we want to be a little fancy, we can note that the $3\sin^2{\theta}  - 2$ term looks pretty close to $P_2(stuff)$, so let's play with a simple trig identity:

$$\begin{aligned}
V_{n=3} (r,\theta) &= \frac{1}{4\pi\epsilon_0}\frac{\pi\lambda R^3}{2r^3} \left(3\underbrace{\sin^2{\theta}}_{1-\cos^2{\theta}}  - 2 \right) \\
&= \frac{1}{4\pi\epsilon_0}\frac{\pi\lambda R^3}{2r^3} \left(1-3\cos^2{\theta}\right) \\
&= -\frac{1}{4\pi\epsilon_0}\frac{\pi\lambda R^3}{r^3} \underbrace{\frac{3\cos^2{\theta}-1}{2}}_{P_2(\cos{\theta})} \\
&= -\frac{1}{4\pi\epsilon_0}\frac{\pi\lambda R^3}{r^3} P_2(\cos{\theta}) \\
\end{aligned}$$

\pagebreak

# Problem 3.32

> Two point charges, $3q$ and $-q$ are separated by a distance $a$. For each of the arrangements in Figure 3.35, find ($i$) the monopole moment, ($ii$) the dipole moment, and ($iii$) the approximate potential at large $r$.

Note two facts from Page 157:

- Griffith's defines the *monopole moment* as just $Q$ (the net charge of the distribution)
- $Q$ is independent of the coordinate system, as $V_{mono}(\vec{r})$ depends only on $\magv{r}$

Examining each charge arrangement, we have:

- Each arrangement has the same monopole moment: $Q=2q$
- Part A:
  - $+3q$ point charge located at $\vrprime_1=a\hat{z}$
  - $-q$ point charge located at $\vrprime_2=\vec{0}$
  - $\vec{d} = a\hat{z} \Rightarrow \vec{p} = 3qa\hat{z}$
- Part B:
  - $+3q$ point charge located at $\vrprime_1=\vec{0}$
  - $-q$ point charge located at $\vrprime_2=-a\hat{z}$
  - $\vec{d} = a\hat{z} \Rightarrow \vec{p} = (-q)(-a\hat{z}) = qa\hat{z}$
- Part C:
  - $+3q$ point charge located at $\vrprime_1=a\hat{y}$
  - $-q$ point charge located at $\vrprime_2=\vec{0}$
  - $\vec{d} = a\hat{y} \Rightarrow \vec{p} = 3qa\hat{y}$

The final step, just to handle ($iii$) at the same time: define $\vec{r}$ to just be $r\hat{r}$, and so with Cartesian basis vectors, $\vec{r} = r (\sin{\theta}\cos{\varphi}\hat{x} + \sin{\theta}\sin{\varphi} \hat{y} + \cos{\theta} \hat{z})$. Now, let's find the potential for each arrangement:

| Charge Arrangement | $Q$ | $\vec{p}$ | $\hat{r}\cdot\vec{p}$ | $V(\vec{r})\approx$ |
| -- | - | - | -- | --- |
| $$A$$ | $$2q$$ | $$3qa\hat{z}$$ | $$3qa\cos{\theta}$$ | $$\frac{1}{4\pi\epsilon_0}\left(\frac{2q}{\magv{r}} + \frac{3qa\cos{\theta}}{\magv{r}^2}\right)$$ |
| $$B$$ | $$2q$$ | $$qa\hat{z}$$ | $$qa\cos{\theta}$$ | $$\frac{1}{4\pi\epsilon_0}\left(\frac{2q}{\magv{r}} + \frac{qa\cos{\theta}}{\magv{r}^2}\right)$$ |
| $$C$$ | $$2q$$ | $$3qa\hat{y}$$ | $$3qa\sin{\theta}\sin{\varphi}$$ | $$\frac{1}{4\pi\epsilon_0}\left(\frac{2q}{\magv{r}} + \frac{3qa\sin{\theta}\sin{\varphi}}{\magv{r}^2}\right)$$ |

\pagebreak

# Problem 3.34

> Three point charges are located as shown in Figure 3.38, each a distance $a$ from the origin. Find the approximate electric field at points far from the origin. Express your answer in spherical coordinates, and include the two lowest orders in the multipole expansion.

At this point, we can determine the monopole moment by inspection: $Q=-q$ and that the monopole term in the potential will simply be given by:

$$V_{mono}(\vec{r}) = \frac{1}{4\pi\epsilon_0} \frac{-q}{\magv{r}}$$

Then, leveraging our experience from 3.32, we can write down $\hat{r}$ for $\vec{r}$ and the corresponding information for each charge:

$$\vec{r} = r (\sin{\theta}\cos{\varphi}\hat{x} + \sin{\theta}\sin{\varphi} \hat{y} + \cos{\theta} \hat{z})$$

- $q_1=-q$ is at $\vrprime_1 = a \hat{y}$
- $q_2=q$ is at $\vrprime_2 = a \hat{z}$
- $q_3=-q$ is at $\vrprime_3 = -a \hat{y}$

Then, using Equation 3.100, we can find the dipole moment for the charge distribution:

$$\vec{p} = \sum_{i=1}^{3}{ q_i \vrprime_i} = qa(\hat{y}+\hat{z}-\hat{y}) = qa\hat{z}$$

And the potential dipole term takes the form:

$$V_{dipole}(\vec{r}) = \frac{1}{4\pi\epsilon_0} \frac{qa\hat{z}\cdot\hat{r}}{\magv{r}^2} = \frac{1}{4\pi\epsilon_0} \frac{qa\cos{\theta}}{\magv{r}^2}$$

Finally, we just combine the two terms and act the Gradient on the function (using the spherical basis):

$$\begin{aligned}
\vec{E}(\vec{r}) &= -\frac{1}{4\pi\epsilon_0} \vec{\nabla} \left(\frac{-q}{\magv{r}} + \frac{qa\cos{\theta}}{\magv{r}^2}\right) \\
&= -\frac{q}{4\pi\epsilon_0} \left(\frac{\partial}{\partial r} \hat{r} + \frac{1}{r} \frac{\partial}{\partial \theta} \hat{\theta}  + \frac{1}{r\sin{\theta}} \frac{\partial}{\partial \varphi} \hat{\varphi} \right)\left(\frac{-}{\magv{r}} + \frac{a\cos{\theta}}{\magv{r}^2}\right)\\
&= -\frac{q}{4\pi\epsilon_0} \left(\frac{\partial}{\partial r} \left(\frac{-1}{\magv{r}} + \frac{a\cos{\theta}}{\magv{r}^2}\right) \hat{r} + \frac{a}{\magv{r}^3} \frac{\partial}{\partial \theta}\cos{\theta} \hat{\theta} \right)\\
&= -\frac{q}{4\pi\epsilon_0} \left(\left(\frac{1}{\magv{r}^2} - \frac{2a\cos{\theta}}{\magv{r}^3}\right) \hat{r} + \frac{-a\sin{\theta}}{\magv{r}^3} \hat{\theta} \right)\\
&= \frac{1}{4\pi\epsilon_0} \frac{q}{\magv{r}^2}\left(-\hat{r} + \frac{a}{\magv{r}}\left(2\cos{\theta}\hat{r} + \sin{\theta}\hat{\theta} \right) \right)\\
\end{aligned}$$
