---
title: Homework 6
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Wednesday, Novemeber 10, 2021
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
    \fancyhead[LO,LE]{Knudson}
---

\pagebreak

# 5.26

## Part A

> By whatever means you can think of, find the vector potential a distance $s$ from an infinite straight wire carrying a current I. Check that $\nabla\cdot\vec{A} = 0$ and $\nabla\times\vec{A} = \vec{B}$.

### Finite Wire

Consider the simpler problem of a finite wire of total length $2L$ and let us examine the vector potential at a point $P$ a distance $s$ away. For this scenario to be beneficial, let the length of this wire be greater than the wire's separatation with respect to the point: $2L>s$. We are not concerned with edge effects and in the extreme case of this wire stretching out to infinity, there will be no edge effects. Since this wire is finite, we begin with Equation 5.66:

$$\vec{A} = \frac{\mu_0}{4\pi} \int{ \frac{\vec{I}}{\lvert \vec{\mathfrak{r}} \rvert} d\ell}$$

\begin{figure}[H]
    \centering
    \begin{tikzpicture}[scale=1.5]

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (Z) at (3,0);
    \coordinate (L) at (4,0);
    \coordinate (P) at (0,1);


    % Create the cylinder on it's side
    \draw (4,0) ellipse (0.1 and 0.1);

    \draw (4,0.1) -- (-4,0.1);
    \draw (-4,-0.1) -- (4,-0.1) node [midway, below] {$2L$};

    \draw (-4,0.1) arc (90:270: 0.1 and 0.1);


    % Draw z axis and label
    \draw[stealth-, gray] (-5,0) -- (0,0);
    \draw[-stealth, gray] (0,0) --++ (5,0);
    \node at (5,0) [below] {$+\hat{z}$};

    % Label the point
    \node at (P) [above] {$P$};

    % Construct triangle
    \draw[dashed] (P) -- (Z);
    \node at (1.5,0.7) [above] {$\mathfrak{r}=\sqrt{s^2 + z^2}$};
    \draw (O) -- (Z);
    \node at (1.5,-0.1) [below] {$z$};
    \draw[dashed] (O) -- (P) node [midway, left] {$s$};
    \tkzFillAngle[fill=orange, opacity=0.4, size=0.3](O,P,Z);
    \tkzLabelAngle[pos=0.5](O,P,Z){$\alpha$};

    \end{tikzpicture}
    \caption{A visual representation of the angle, $\alpha$, from the midpoint of the wire to some distance $z$ along its length. }
\end{figure}

Redefining $\vec{I}d\ell$ as $Idz\hat{z}$, we can then use this figure to set up a few trigonmetric relations that will make evaluating this integral much easier. Note the choice of naming the angle $\alpha$ between $s$ and $\mathfrak{r}$. From this $\tan{\alpha}$ can be solved for $z$ and this also provides a relation to find $d\alpha$ in order to change the variable of integration.

$$z=s\tan{\alpha} \Rightarrow dz = s\sec^2{\alpha} d\alpha$$

Substituting into 5.66, we obtain an integral that is easy enough to do by hand after simplification.

$$\begin{aligned}
\vec{A} &= \frac{\mu_0 I}{4\pi}\hat{z} \int_{-L}^{L}{ \frac{dz}{\sqrt{s^2 + z^2}} }\\
&= \frac{\mu_0 I}{2\pi}\hat{z} \int_{0}^{\beta}{ \frac{s\sec^2{\alpha}d\alpha}{z\sqrt{1 + \tan^2{\alpha}}} }\\
&= \frac{\mu_0 I}{2\pi}\hat{z} \int_{0}^{\beta}{ \sec{\alpha} d\alpha } \\
&= \frac{\mu_0 I}{2\pi}\hat{z} \ln{\left(\sec{\alpha}+\tan{\alpha}\right)}_{0}^{\beta}\\
&= \frac{\mu_0 I}{2\pi}\hat{z} \bigg(\ln{\left(\sec{\beta}+\tan{\beta}\right)} - \ln{\left(1 + 0 \right)} \bigg)
\end{aligned}$$

Note that $\beta$ will be the full angle as the distance along the wire $z\rightarrow L$ as shown in Figure 2. From this, we can see that $\sec{\beta}=\sqrt{s^2+L^2}/s$ and $\tan{\beta}=L/s$.

\begin{figure}[H]
    \centering
    \begin{tikzpicture}[scale=1.5]

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (L) at (6,0);
    \coordinate (P) at (0,1);

    % Construct triangle
    \draw[dashed] (P) -- (L) node [midway, above] {$\sqrt{s^2 + L^2}$};
    \draw (O) -- (L) node [midway, below] {$L$};
    \draw[dashed] (O) -- (P) node [midway, left] {$s$};
    \tkzFillAngle[fill=violet, opacity=0.4, size=0.3](O,P,L);
    \tkzLabelAngle[pos=0.5](O,P,L){$\beta$};

    \end{tikzpicture}
    \caption{A visual representation of the full angle, $\beta$, from the midpoint of the wire to one end of the wire (exagerated for effect). }
\end{figure}

$$\begin{aligned}
\vec{A} &= \frac{\mu_0 I}{2\pi}\hat{z} \ln{\left(\frac{\sqrt{s^2 + L^2}+ L}{s}\right)}\\
&= \frac{\mu_0 I}{2\pi}\hat{z} \bigg(\ln{\left(\sqrt{s^2 + L^2} + L\right)} - \ln{\left(s\right)} \bigg)\\
2L \gg s &\Rightarrow L\sqrt{\frac{s^2}{L^2} + 1} \approx L\\
&\approx \frac{\mu_0 I}{2\pi}\hat{z} \bigg(\ln{\left(2L\right)} - \ln{\left(s\right)} \bigg)
\end{aligned}$$

Note that in electrostatics, we'd typically divide by the length of the wire to obtain a quanity of 'per unit length'; however, the wire's length is wrapped up inside the $\ln{}$, and so we must unfortunately deal with the fact that as $2L \rightarrow \infty$, $\vec{A} \rightarrow \infty$. 

### Reverse Engineering the Vector Potential

Recall from Equation 5.39 that the magnetic field due to an infinitely long straight wire of uniform current $I$ is given as $$\vec{B} = \frac{\mu_0 I}{2\pi s} \hat{\phi}$$ We know that the curl of our vector potential must generate this field, so without assuming any values of the components of $\vec{A}$, let us begin by taking the curl:

$$\begin{aligned}
\nabla\times\vec{A} &= \left(\frac{1}{s}\frac{\partial A_z}{\partial \phi} - \frac{\partial A_\phi}{\partial z} \right) \hat{s} + \left(\frac{\partial A_s}{\partial z} - \frac{\partial A_z}{\partial s} \right) \hat{\phi} + \frac{1}{s}\left(\frac{\partial (s A_\phi)}{\partial s} - \frac{\partial A_s}{\partial \phi} \right) \hat{z} \\
\\
0 &= \left(\frac{1}{s}\frac{\partial A_z}{\partial \phi} - \frac{\partial A_\phi}{\partial z} \right) \\
\frac{\mu_0 I}{2\pi s} &= \frac{\partial A_s}{\partial z} - \frac{\partial A_z}{\partial s} \\
0 &= \frac{1}{s}\left(\frac{\partial (s A_\phi)}{\partial s} - \frac{\partial A_s}{\partial \phi} \right)
\end{aligned}$$

Then, using Stokes' Theorem, we can compare the circulation of $\vec{A}$ about an Amperian Loop and the magnetic flux through it:

$$\oint{\vec{A}\cdot d\vec{\ell}} = \int{\vec{B}\cdot d\vec{a}}$$

\begin{figure}[H]
    \centering
    \begin{tikzpicture}[scale=1.25]

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (A) at (0,1.25);
    \coordinate (P) at (4,0);


    % Create the cylinder on it's side
    \draw (0,0) ellipse (0.5 and 1.25);
    \draw (0,1.25) arc (90:270: 0.5 and 1.25);


    % Label the radius
    \draw[dashed] (0,0) -- (0,1.25) node [midway, right] {$s$};

    % Draw z axis and label
    \draw[-stealth] (-2,0) --++ (4,0) node [right] {$\vec{I}$};

    \end{tikzpicture}
\end{figure}

$$\begin{aligned}
A_\phi 2\pi s &= 0 \qquad \Rightarrow A_\phi = 0\\
\\
0 &= \frac{1}{s}\frac{\partial A_z}{\partial \phi} - \frac{\partial A_\phi}{\partial z} &\Rightarrow 0 = \frac{\partial A_z}{\partial \phi}\\
\\
0 &= \frac{1}{s}\left(\frac{\partial (s A_\phi)}{\partial s} - \frac{\partial A_s}{\partial \phi} \right) &\Rightarrow 0 = \frac{\partial A_s}{\partial \phi}\\
\end{aligned}$$

As a result, our system of equations simplifies down to just one. Without loosing our generality, let us make the possible $A_s$ dependence on $z$ explicit in terms of a polynomial: $z^p$. By inspecting the resulting $B$ field, we see no special functions or hint of their derivatives, only a constant term with respect to $z$.

$$\begin{aligned}
\frac{\mu_0 I}{2\pi s} &= \frac{\partial A_s}{\partial z} - \frac{\partial A_z}{\partial s}\\
\frac{\mu_0 I}{2\pi s} &= \frac{\partial (z^p A_s)}{\partial z} - \frac{\partial A_z}{\partial s}\\
\frac{\mu_0 I}{2\pi s} &= p (A_s) z^{p-1} - \frac{\partial A_z}{\partial s}\\
\end{aligned}$$

Now the only way for the $z^{p-1}$ polynomial to vanish would be if $A_z$ had a similar construction, but since the left-hand side of the equation is non-zero, we need to remove the variable without causing both partial derivatives subtracting to 0. Therefore, we see that $A_s$ having $z^p$ dependence (in this case) will not work. Physically, we know that the vector potential is parallel to the direction of the current density, and since $\vec{I}$ flows in the $+z$ direction (along the wire), we only expect $\vec{A}$ to have a $z$ component: $A_z$. Furthermore, if the vector potential had explicit $z$ coordinate dependence, the current would not be steady state and would violate the given set of assumptions for magnetostatics. Setting $p=0$, we obtain a simple separable ordinary differential equation that can be solve for $A_z$:

$$\begin{aligned}
\frac{dA_z}{ds} &= - \frac{\mu_0 I}{2\pi s} \\
\int_{0}^{A_z(s)}{dA_z} &= - \frac{\mu_0 I}{2\pi} \int{\frac{1}{s}ds} \\
A_z(s) &= - \frac{\mu_0 I}{2\pi} \ln{s} + C_0\\
\\
\ln{C_1} &\equiv \frac{2\pi}{\mu_0 I}C_0\\
\\
A_z(s) &= \frac{\mu_0 I}{2\pi} \bigg(\ln{C_1} - \ln{s}\bigg)\\
&= \frac{\mu_0 I}{2\pi} \bigg(\ln{C_1} - \ln{s}\bigg)\\
&= \frac{\mu_0 I}{4\pi} 2\ln{ \left(\frac{C_1}{s}\right) }
\end{aligned}$$

Comparing this result with that of the finite case, we see that if we set $C_1 = 2L$ and let $2L\rightarrow\infty$, we obtain the extreme case for the finite wire being stretched out to infinity. This claim should not be considered outlandish: we expected to obtain a constant term (with respect to $s$ and strictly no $\phi$ or $z$ coordinate dependence) from undoing the derivative. In addition the physical meaning of the constant (as well as dimensions) match that of the situation. The only remaining step is to verify this vector potential has no diveregence:

\pagebreak


## Part B

> Find the magnetic potential inside the wire, if it has radius $R$ and the current is uniformly distributed.


\pagebreak

# 5.38 (a and c)



# 5.41

# 6.3 