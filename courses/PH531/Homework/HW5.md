---
title: Homework 5
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Saturday, October 23, 2021
papersize: a4
geometry: margin=1.7cm
linkcolor: blue
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usepackage{fancyhdr}
    \usepackage{float}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 531, Fall 2021}
    \fancyhead[CO,CE]{HW5}
    \fancyhead[LO,LE]{Knudson}
---

Notation:

> Let $\vec{\mathfrak{r}}$ denote the equivalent shorthand of Griffith's cursive `r` for the vector representing the difference between the source charge and a point in space: $\vec{r}-{\vec{r}\ }^{\prime}$. Thus $\mathfrak{r}$ implies the magnitude of $\vec{r}-{\vec{r}\ }^{\prime}$ as given by: $\sqrt{(\vec{r}-{\vec{r}\ }^{\prime})\cdot (\vec{r}-{\vec{r}\ }^{\prime})}$.

# Problem 5.11

> Find the magnetic field at point $P$ on the axis of a tightly wound solenoid (helical coil) consisting of $n$ turns per unit length wrapped around a cylindrical tube of radius $a$ and carrying current $I$. Express your answer in terms of $\theta_1$ and $\theta_2$. Consider the turns to be essentially circular and use the result of Example 5.6. What is the field on the axis of an *infinite* solenoid (infinite in both directions)?

Per Griffith's recommendation, we will heavily use the results from Example 5.6. Recall that this example gives the magnetic field for a 1-Dimensional circular ring with the results summarized by Equation 5.41:

$$\vec{B}(z) = \frac{\mu_0 I}{4\pi} \left( \frac{\cos{\theta}}{\mathfrak{r}^2}\right)2\pi R \hat{z} = \frac{\mu_0 I}{4\pi}2\pi \left( \frac{R^2}{\mathfrak{r}^3}\right) $$

where $\cos{\theta}$ was the portion of the magnetic field *felt* at an arbirtray point along the axis of symmetry of the ring. Note that $R$ was given as the radius of this ring of steady current $I$ with assumed direction of counter-clockwise flow about the ring: the $+\hat{\phi}$ direction. Given that our solenoid has a radius of $a$, we perform this substitution for the radius and then assume the 1-D loop can be treated more accurately as having a thickness of $dz$. 

\begin{figure}[H]
    \centering
    \begin{tikzpicture}[scale=1.25]

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (A) at (0,1.25);
    \coordinate (P) at (4,0);

    % Create the cylinder on it's side
    \draw (0,0) ellipse (0.5 and 1.25);
    \draw (0,1.25) -- (-0.5,1.25) node [above] {$dz$};
    \draw (-0.5,1.25) arc (90:270: 0.5 and 1.25);
    \draw (-0.5,-1.25) -- (0,-1.25);

    % Label the radius
    \draw[dashed] (0,0) -- (0,1.25) node [midway, right] {$a$};

    % Draw z axis and label
    \draw[-stealth, gray] (0,0) --++ (5,0);
    \node at (5,0) [below] {$+\hat{z}$};

    % Label the point
    \node at (P) [below] {$P$};

    % Construct triangle
    \draw[dashed] (0,1.25) -- (4,0) node[midway, above] {$\vec{\mathfrak{r}}$};
    \draw (0,0) -- (4,0) node[midway, below] {$z$};
    \tkzFillAngle[fill=orange, opacity=0.4](A,P,O);
    \tkzLabelAngle[pos=1.2](A,P,O){$\theta$};

    \end{tikzpicture}
    \caption{A visual representation of the angle, $\theta$, from the edge of the solenoid (approximated as ring of current $\vec{I}=I\hat{\phi}$ with thickness $dz$) to the point $P$ located on the axis of symmetry.}
\end{figure}

As shown in Figure 1, $\mathfrak{r}$ is $\sqrt{z^2 + a^2}$. Noting the requirement of the problem statement to parameterize the magnetic field in terms of $\theta_1$ and $\theta_2$ (angles describing the relation of the start/end points of the finite solenoid to the point along the axis of symmetry), we can take the hint to parameterize $z$ in terms of $\theta$. Rewriting Equation 5.41 in terms of this new situation, the given field is really a small portion of the solenoid:

$$d\vec{B}(z) = \frac{\mu_0 I}{4\pi}2\pi \frac{a^2}{\mathfrak{r}^3} dz\hat{z}$$

Recalling Figure 1, we can see that $\tan{\theta}=\frac{a}{z}$ which gives us a way to find $dz$: 

$$\begin{aligned}
z &= a\cot{\theta} \\
dz &= -\frac{a}{\sin^2{\theta}}d\theta
\end{aligned}$$

Substituting all these values in, and integrating the resulting contribution as we extrude from a 1-D ring of current (with infinitesimal thickness) to a 2-D tube, we can find the field due to a finite solenoid:

$$\begin{aligned}
\vec{B}(z) &= \int{d\vec{B}} \\
&= \frac{\mu_0 I}{4\pi}2\pi \hat{z}\int{\frac{a^2}{\mathfrak{r}^3} dz} \\
&= \frac{\mu_0 I}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\frac{a^2}{\sqrt{(a\cot{\theta})^2 + a^2}^3} \left(-\frac{a}{\sin^2{\theta}}\right) d\theta} \\
&= \frac{\mu_0 I}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\frac{a^2}{a^3\sqrt{\cot^2{\theta} + 1}^3} \left(-\frac{a}{\sin^2{\theta}}\right) d\theta} \\
&= \frac{\mu_0 I}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\frac{-1}{\csc^3{\theta}\sin^2{\theta}} d\theta} \\
&= \frac{\mu_0 I}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\sin{\theta} d\theta} \\
&= \frac{\mu_0 I}{4\pi}2\pi \bigg(\cos{\theta_2} - \cos{\theta_1}\bigg)\hat{z}
\end{aligned}$$

Now, consulting Figure 5.25 (page 229 of Griffiths), we can see that $\theta_1$ is the angle from *below* $P$ to the start of our finite solenoid, and $\theta_2$ follows the same set up but for the end. Thus, we the solenoid extends out to be infinitely long $\theta_1$ goes from $>0$ to $\pi$ and $\theta_2$ will *squish* down to $0$ as the end of the solenoid explodes away to $z\rightarrow -\infty$:

$$\vec{B}(z) = \frac{\mu_0 I}{4\pi}2\pi \bigg(\cos{(\theta_2 = 0)} - \cos{(\theta_1 = \pi)}\bigg)\hat{z} = \frac{\mu_0 I}{4\pi}4\pi\hat{z}$$

If we so wanted, we could take the liberty to discuss $I$ as being proportional to *how tightly* the coil is wrapped in terms of *turns per unit Length*: E.g. the steady current $I'\equiv nI$, and with simplifications, our answer matches Griffith's solution to Example 5.9 (Field inside a solenoid using Ampere's Law), $\vec{B}(z) = \mu_0 nI\hat{z}$.

\pagebreak

# Problem 5.14

> A steady current $I$ flows down a long cylindrical wire of radius $a$. Find the magnetic field, both inside and outside the wire, if:

## Part A

> The current is uniformly distributed over the outside surface of the wire.

