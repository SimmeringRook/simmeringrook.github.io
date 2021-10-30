---
title: Homework 5
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Saturday, October 23, 2021
papersize: a4
geometry: margin=1.75cm
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
    \draw (-0.5,-1.25) -- (0,-1.25);

    \draw (-0.5,1.25) arc (90:270: 0.5 and 1.25);


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

Before substituting all these values in and integrating the resulting contribution as we extrude from a 1-D ring of current (with infinitesimal thickness) to a 2-D tube, we have one more consideration. As a singular ring of current, there were no 'turns' of the coil, but as we *stretch* the length of the ring into a finite solenoid, we need to scale the current $I$ by the number of turns per unit length $n$. 

$$\underbrace{I}_{\text{1D ring}} \rightarrow \underbrace{nI}_{\text{2D coil of rings}}$$

$$\begin{aligned}
\vec{B}(z) &= \int{d\vec{B}} \\
&= \frac{\mu_0 nI}{4\pi}2\pi \hat{z}\int{\frac{a^2}{\mathfrak{r}^3} dz} \\
&= \frac{\mu_0 nI}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\frac{a^2}{\sqrt{(a\cot{\theta})^2 + a^2}^3} \left(-\frac{a}{\sin^2{\theta}}\right) d\theta} \\
&= \frac{\mu_0 nI}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\frac{a^2}{a^3\sqrt{\cot^2{\theta} + 1}^3} \left(-\frac{a}{\sin^2{\theta}}\right) d\theta} \\
&= \frac{\mu_0 nI}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\frac{-1}{\csc^3{\theta}\sin^2{\theta}} d\theta} \\
&= \frac{\mu_0 nI}{4\pi}2\pi \hat{z}\int_{\theta_1}^{\theta_2}{\sin{\theta} d\theta} \\
&= \frac{\mu_0 nI}{4\pi}2\pi \bigg(\cos{\theta_2} - \cos{\theta_1}\bigg)\hat{z}
\end{aligned}$$

Now, consulting Figure 5.25 (page 229 of Griffiths), we can see that $\theta_1$ is the angle from *below* $P$ to the start of our finite solenoid, and $\theta_2$ follows the same set up but for the end. Thus, we the solenoid extends out to be infinitely long $\theta_1$ goes from $>0$ to $\pi$ and $\theta_2$ will *squish* down to $0$ as the end of the solenoid explodes away to $z\rightarrow -\infty$:

$$\vec{B}(z) = \frac{\mu_0 nI}{4\pi}2\pi \bigg(\cos{(\theta_2 = 0)} - \cos{(\theta_1 = \pi)}\bigg)\hat{z} = \frac{\mu_0 nI}{4\pi}4\pi\hat{z}$$

As expected, our answer matches Griffith's solution to Example 5.9 (Field inside a solenoid using Ampere's Law), $\vec{B}(z) = \mu_0 nI\hat{z}$.

\pagebreak

# Problem 5.14

> A steady current $I$ flows down a long cylindrical wire of radius $a$. Find the magnetic field, both inside and outside the wire, if:

## Part A

> The current is uniformly distributed over the outside surface of the wire.

We align our origin and cyldrincal coordiate axes to match that of the wire and so $\vec{I}=I\hat{z}$. Using the right-hand rule, with the current flowing in the positive $z$ direction, that implies the field will be curling about the wire in the positive $\phi$ direction. We place our Amperian Loop with its normal vector parallel to $\hat{z}$:

\begin{figure}[H]
    \centering
    \begin{tikzpicture}[scale=1.25]

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (A) at (0,1.25);
    \coordinate (P) at (4,0);

    % Create the cylinder on it's side
    \draw (3,0) ellipse (0.5 and 1.25);
    \draw (3,1.25) -- (-3,1.25);
    \draw (-3,1.25) arc (90:270: 0.5 and 1.25);
    \draw (-3,-1.25) -- (3,-1.25);

    % Label the radius
    \draw[dashed] (3,0) -- (3,1.25) node [midway, left] {$a$};

    % Draw z axis and label
    \draw[stealth-, gray] (-4,0) -- (0,0);
    \draw[-stealth, gray] (0,0) -- (5,0);
    \node at (5,0) [below] {$+\hat{z}$};
    \node at (-2,0) [above] {$\vec{I}=I\hat{z}$};

    % Create the Amperian loop
    \draw[dashed] (0,0) ellipse (0.5 and 1.5);
    \draw[-stealth] (0,0) -- (1,0);
    \node at (1,0.1) [right, above, fill=white] {$d\vec{A}=sd\phi\hat{z}$};

    % Label the radius
    \draw[dashed] (0,0) -- (0,1.5) node [midway, left] {$s$};

    \end{tikzpicture}
    \caption{A recreation of Figure 5.40 from Griffiths giving a visual indication for the placement of the Amperian Loop with respect to current and the wire.}
\end{figure}

And from here, we just walk around our loop in the direciton of the field and find the magnetic field from the wire:

$$\begin{aligned}
\oint{\vec{B}\cdot d\vec{\ell}} &= \mu_0 I_{enc} \\
2\pi s B &= \mu_0 I_{enc} \\
B &= \frac{\mu_0}{2\pi s} I_{enc}
\end{aligned}$$

By inspection, we see that for radial distances of $s>a$, the enclosed current is just the given current from the problem statement: $I_{enc}=I$. For $s<a$, there is no current enclosed from the wire as it flows only on the surface, and so $I_{enc}=0$. 

$$\vec{B} = \begin{cases} \frac{\mu_0}{2\pi s} I \hat{\phi} & s>a \\ \vec{0} & s<a \end{cases}$$

\pagebreak

## Part B

>The current is distributed in such a way that $J$ is proportional to $s$, the distance from the axis.

For this case, we can draw inspiration from Example 5.4, in which we introduce a variable $k$ to represent the proportionality: $J\equiv ks$. Keeping everything else the same, we can begin with our general results from Part A, but we must integrate $J$ to find a description for $k$ in terms of $I$:

$$\begin{aligned}
I &= \int_{0}^{a}{(ks^{\prime})(2\pi s^{\prime}ds^{\prime})}\\
&= 2\pi k \int_{0}^{a}{{s^{\prime}}^2 ds^{\prime})}\\
&= \frac{2\pi k a^3}{3}\\
k &= \frac{3}{2\pi a^3}I
\end{aligned}$$

For our loop when $s>a$, the current density has reached its maximum value and $I_{enc}=I$. In contrast to Part A, our current density now also exists below $s=a$, and so $I_{enc}$ for $s<a$, we use our result from above but substitute $s$ in for $a$:

$$I_{enc} = \frac{2\pi s^3}{3}k = \frac{2\pi s^3}{3}\frac{3}{2\pi a^3}I = \frac{s^3}{a^3}I$$

$$\vec{B}(s) = \frac{\mu_0}{2\pi s} I \hat{\phi} \begin{cases} & s>a \\ 
\frac{s^3}{a^3} & s<a \end{cases}$$

\pagebreak

# Problem 5.16

> Two long coaxial solenoids each carry current $I$, but in opposite directions, as shown in Figure 5.42. The inner solenoid (radius $a$) has $n_1$ turns per unit length, and the outer one (radius $b$) has $n_2$. Find $\vec{B}$ in each region.

The solution to this problem is straightforward. Recall that from Example 5.9 (and Problem 5.11), the magnetic field outside a solenoid is $\vec{0}$ and inside it is $\mu_0 n I$. Also recall that magnetic fields obey the principle of superposition. In summary the only work to be done is to determine from the figure in the book the intended direction of current flowing: since the arrows *curl down* for the outer solenoid, the right-hand rule indicates that the sign of the $\vec{B}$ should be in the positive $z$ direction and opposite for the inner solenoid.

| Region | $$\vec{B}_{inner}$$ | $$\vec{B}_{outer}$$ | $$\vec{B}_{net}$$ |
| --- | --- | --- | --- |
| $$b<s$$ | $$\vec{0}$$ | $$\vec{0}$$ | $$\vec{0}$$ |
| $$a<s<b$$ | $$\vec{0}$$ | $$\mu_0 n_2 I \hat{z}$$ | $$\mu_0 n_2 I \hat{z}$$ |
| $$s<a$$ | $$-\mu_0 n_1 I \hat{z}$$ | $$\mu_0 n_2 I \hat{z}$$ | $$\mu_0 (n_2-n_1) I \hat{z}$$ |

\pagebreak

# Problem 5.39

> Analyze the motion of a particle (charge $q$, mass $m$) in the magnetic field of a long straight wire carrying a steady current $I$.

## Part A

> Is kinetic energy conserved?

Recall that from Equation 5.11, a magnetic field cannot do work, therefore kinetic energy is conserved. $$\ $$

## Part B

> Find the force on the particle, in cylindrical coordinates, with $I$ along the $z$ axis.

We shall use the Lorentz Force Law, Equation 5.1, without an $\vec{E}$ as we don't know how to calculate the $\vec{E}$ from the moving charge in the wire. Recall in Problem 5.14A, we found the $\vec{B}$ outside a wire. If we shrink the radius down from $a$ to something infinitesimally small, we can make this wire 1-D and then we have the $\vec{B}$ over all space:

$$\vec{B} = \frac{\mu_0}{2\pi s} I \hat{\phi}$$

Now we just need to find the arbritrary velocity vector for particle in cylindrical coordinates. Starting with the time derivative of the basis vectors:

$$\begin{aligned}
\hat{s} &= \cos{\phi}\hat{x} + \sin{\phi}\hat{y}\\
\dot{\hat{s}} &= (\underbrace{-\sin{\phi}\hat{x} + \cos{\phi}\hat{y}}_{\hat{\phi}}) \dot{\phi} \\
&= \dot{\phi}\hat{\phi}
\end{aligned} \qquad\qquad \begin{aligned}
\hat{\phi} &= -\sin{\phi}\hat{x} + \cos{\phi}\hat{y}\\
\dot{\hat{\phi}} &= -(\underbrace{\cos{\phi}\hat{x} + \sin{\phi}\hat{y}}_{\hat{s}}) \dot{\phi}\\
&= -\dot{\phi}\hat{s}
\end{aligned}$$

And since we will need the general acceleration, we might as well find $\dot{\vec{r}}$ and $\ddot{\vec{r}}$ at the same time:

$$\begin{aligned}
\vec{r} &= s\hat{s} + z\hat{z}\\
\\
\dot{\vec{r}} &= \dot{s}\hat{s} + s\dot{\hat{s}} + \dot{z}\hat{z}\\
&= \dot{s}\hat{s} + s\dot{\phi}\hat{\phi} + \dot{z}\hat{z}\\
\\
\ddot{\vec{r}} &= (\ddot{s}\hat{s} + \dot{s}\dot{\hat{s}}) + (\dot{s}\dot{\phi}+s\ddot{\phi})\hat{\phi} + s\dot{\phi}\dot{\hat{\phi}} + \ddot{z}\hat{z} \\
&= (\ddot{s} - s\dot{\phi}^2)\hat{s} + (2\dot{s}\dot{\phi} + s\ddot{\phi})\hat{\phi} + \ddot{z}\hat{z}
\end{aligned}$$

Now we have each quantity in the Lorentz Force Law, we just need to carry out the cross product:

$$\begin{aligned} \vec{F} &= q(\dot{\vec{r}}\times\vec{B}) \\ &= q(\dot{s}\hat{s} + s\dot{\phi}\hat{\phi} + \dot{z}\hat{z})\times\frac{\mu_0}{2\pi s} I \hat{\phi} \\ \hat{s} \times \hat{\phi} = \hat{z} &\qquad \hat{z} \times \hat{\phi} = -\hat{s} \\ &= q\frac{\mu_0}{2\pi s} I (-\dot{z}\hat{s}+\dot{s}\hat{z})\end{aligned}$$

\pagebreak

## Part C

> Obtain the equations of motion.

Assuming that Newton's Second Law $\vec{F} = m \ddot{\vec{r}}$ is applicible to this situation, we obtain the following system of equations:

$$\begin{aligned}
(\ddot{s} - s\dot{\phi}^2) &= - \frac{q}{m}\frac{\mu_0}{2\pi} I \frac{1}{s} & \leftarrow\hat{s}\\
(2\dot{s}\dot{\phi} + s\ddot{\phi}) &= 0 & \leftarrow\hat{\phi}\\
\ddot{z} &= \frac{q}{m}\frac{\mu_0}{2\pi} I \frac{\dot{s}}{s} & \leftarrow\hat{z}
\end{aligned}$$

## Part D

> Suppose $\dot{z}$ is constant. Describe the motion

For the moment, let us introduce $\alpha\equiv \frac{q}{m}\frac{\mu_0}{2\pi} I$ to reveal the coupled nature better:

$$\begin{aligned}
s\ddot{s} - s^2\dot{\phi}^2 &= - \alpha\\
\dot{\phi}^2 &= \frac{1}{s^2}\alpha + \frac{\ddot{s}}{s}
\end{aligned} \qquad
\begin{aligned}
2\dot{s}\dot{\phi} + s\ddot{\phi} &= 0\\
s\ddot{\phi} &= 2\dot{s}\dot{\phi} \\
\frac{\ddot{\phi}}{\dot{\phi}} &= 2\frac{\dot{s}}{s}
\end{aligned}
\qquad
\begin{aligned}
\ddot{z} &= \alpha \frac{\dot{s}}{s}
\end{aligned}$$

Now using $\dot{z}$ constant, $\ddot{z}=0$. $\alpha$ is inherently non-zero, and if $s=0$, $\ddot{z}$ would be exploding towards infinity. Therefore $\dot{s}$ must also be identically $0$:

$$\ddot{z} = \alpha \frac{\dot{s}}{s} \Rightarrow \dot{s} = 0$$

Given that $\dot{s}=0$, we then note the $\ddot{\phi}$ equation faces a similar outcome: $\ddot{\phi}$ must be $0$ and $\dot{\phi} = constant$. 

$$\frac{\ddot{\phi}}{\dot{\phi}} = 2\frac{\dot{s}}{s} \Rightarrow \ddot{\phi} = 0$$

Finally, we examine the last equation: If $s$ is constant from $\dot{s}=0$, then $\ddot{s}$ must also be $0$ and our system of couple ODEs reduces to a simple first order linear ODE:

$$\dot{\phi}^2 = \frac{\alpha}{s^2}$$

$$\phi(t) = \frac{\sqrt{\alpha}}{s}t + \phi_0 = \frac{t}{s}\sqrt{\frac{q}{m}\frac{\mu_0}{2\pi} I} + \phi_0$$

The motion of this charged particle, once we restrict it to constant $\dot{z}$, becomes helical: any previous inward/outward motion with respect to $s$ stops and the particle just rotates cyclically about the wire as it moves in the $z$ direction.