---
title: Homework 5
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Saturday, October 23, 2021
papersize: a4
geometry: margin=1.5cm
linkcolor: blue
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usepackage{fancyhdr}
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

$$B(z) = \frac{\mu_0 I}{2\pi} \left( \frac{\cos{\theta}}{\mathfrak{r}^2}\right)2\pi R$$

where $\cos{\theta}$ was the angle of $\vec{\mathfrak{r}}$ from the $xy$ plane to an arbritary point along the axis of symmetry of the ring. Note that $R$ was given as the radius of this ring of steady current $I$ with assumed direction of counter-clockwise flow about the ring: the $+\hat{\phi}$ direction.

Given that our solenoid has a radius of $a$, we perform this substitution and then assume the 1-D loop can be approximated has having a thickness of $dz$.

\begin{figure}
    \centering
    \begin{tikzpicture}

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


