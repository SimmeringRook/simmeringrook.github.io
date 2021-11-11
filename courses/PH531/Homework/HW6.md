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

Note: only Part B of 5.26 was submitted 'late'. In previous submissions, the work was shown, but context and explainations were not present.

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

$$\begin{aligned}
\nabla\cdot\vec{A} &= \frac{\partial}{\partial z} \left(\frac{\mu_0 I}{4\pi} 2\ln{ \left(\frac{C_1}{s}\right) }\right) (\hat{z}\cdot\hat{z}) \\
&= 0
\end{aligned}$$

\pagebreak


## Part B

> Find the magnetic potential inside the wire, if it has radius $R$ and the current is uniformly distributed.

$$\vec{J}\cdot (\pi R^2)\hat{z} = I$$

Now that the wire has thickness, we can use Ampere's Law to find magnetic field inside the wire:

$$\begin{aligned}
\oint{\vec{B}\cdot d\vec{\ell}} &= \mu_0 \int{\vec{J}\cdot d\vec{a}} \\
B2\pi s &= \mu_0 J \pi s^2 \\
B &= \frac{\mu_0}{2\pi s} \frac{\pi s^2}{\pi R^2} I \\
&= \frac{\mu_0 I}{2\pi} \frac{s}{R^2}
\end{aligned}$$

From here, we can then utilize the general work for reverse engineering (as was done previously) and note the only portion which changes is the final change in $A_z$ with respect to $s$:

$$\begin{aligned}
\frac{dA_z}{ds} &= - \frac{\mu_0 I}{2\pi} \frac{s}{R^2} \\
\int_{0}^{A_z(s)}{dA_z} &= - \frac{\mu_0 I}{2\pi} \int{\frac{s}{R^2}ds} \\
A_z(s) &= - \frac{\mu_0 I}{4\pi} \frac{s^2}{R^2} + C_2\\
\\
{C_3}^2 &\equiv \frac{4\pi}{\mu_0 I}\frac{C_2}{R^2}\\
\\
A_z(s) &= \frac{\mu_0 I}{4\pi} \bigg(\frac{{C_3}^2 - s^2}{R^2}\bigg)\\
\end{aligned}$$

Now, this vector potential must be continous at $R$, so let use that to find the integration constant values and verify the derivatives match:

$$\begin{aligned}
A_{out}(s)\rvert_{s=R} &= A_{in}(s)\rvert_{s=R} \\
\frac{\mu_0 I}{4\pi} 2\ln{ \left(\frac{C_1}{s}\right) }&= \frac{\mu_0 I}{4\pi} \bigg(\frac{{C_3}^2 - s^2}{R^2}\bigg) \\
2\ln{ \left(\frac{C_1}{R}\right) } &= \frac{{C_3}^2 - R^2}{R^2} \\
\ln{ \left(\frac{C_1}{R}\right) } &= \frac{{C_3}^2}{2R^2} - \frac{1}{2} \\
\end{aligned}$$

Since $C_1$ and $C_3$ both have dimensions of length and are represented as ratios of $R$, we can remove the physics and just consider the mathematical result: each fraction can be simplifed to some postive[^1] real valued scalar which describes the proportionality between $C_1$ and $C_3$ to $R$:

[^1]: These are lengths afterall.

$$\ln(a) = \frac{b^2-1}{2}$$

Taking a quick detour, we verify the derivatives are equal by using Equation 5.78:

$$\begin{aligned}
\mu_0 \vec{K} &= \frac{dA_{out}(s)}{ds} - \frac{dA_{in}(s)}{ds} &s\rightarrow R\\
\mu_0 \vec{K} &= \left( - \frac{\mu_0 I}{2\pi} \frac{s}{R^2}  \right) - \left( - \frac{\mu_0 I}{2\pi s} \right) \\
\lim_{s\rightarrow R}{\vec{K}} &= \lim_{s\rightarrow R}{\frac{I}{2\pi} \left( \frac{1}{s} -  \frac{s}{R^2}  \right)}\\
&= \frac{I}{2\pi} \left( \frac{1}{R} -  \frac{R}{R^2}  \right) \\
&= 0
\end{aligned}$$

Since the derivaties are continous at the boundary and can offer no restrictions on these arbritrary constants of integration, the remaining choice is to find when these two equations intersect. Checking for easy solutions: the $\ln{}$ goes to $0$ if $a=1$, and solving the parabola for when $0=(b^2-1)/2$ reveals a similar value of $b$. A quick plot of both functions reveal only one intersection $a=b=1$, and so we conclude that for $A_out$ and $A_in$ to be an accurate physical description, $C_3=C_1=R$.

$$\vec{A}(\vec{r}) = \frac{\mu_0 I}{4\pi} \left( \Theta(R-s)\frac{R^2 - s^2}{R^2} + \Theta(s-R)2\ln{ \left(\frac{R}{s}\right) } \right)\hat{z}$$

\pagebreak

# 5.38 (a and c)

> For a volume current $\vec{J}$:

## Part A

> Write down the multipole expansion, analogous to Equation 5.80.

$$\vec{A}(\vec{r}) = \frac{\mu_0 I}{4\pi} \sum_{n=0}^{\infty}{ \frac{1}{r^{n+1}} \oint{ (r^\prime)^n P_n (\cos{\alpha}) d\vec{\ell}^\prime } }$$

Recall that linear current density (along an oriented path) is just the simplifed case of the more general volume current density over all space. In electrostatics, this was represented by: $$\rho(\vec{r}^\prime)d\tau^\prime = \rho(\vec{r}^\prime) \delta^3 (\vec{r}^\prime) d\tau^\prime$$ where $d\tau^\prime$ keeps the definition general for any coordinate system (and contains the correct scale factors and differentials). 

$$\int{\lambda d\ell} = \iint{\sigma\delta(\vec{r}^\prime)dA^\prime} = \iiint{\rho\delta^2(\vec{r}^\prime)d\tau^\prime} \underbrace{\longrightarrow}_{more\ general} \iiint_{all\ space}{\rho\delta^3(\vec{r}^\prime)d\tau^\prime}$$

In that sense, an oriented closed path integral is the manifestation of restricting the directional (current -> vector) dimensionality as the volume integral is evaluated. Just as a volume integral over all space with a delta function specifiying a particular radius creates a spherical shell,  the volume integral functionally becomes the integral of the boundary (surface). This same effect is present here but with an explicit addendum: the directionality in the higher dimension encodes the instructions for 'how to walk the boundary' $\rightarrow$ oreintation for the closed path. Thus:

$$\oint{\vec{I}d\ell} = \iint{\vec{K}\delta(\vec{r}^\prime)dA^\prime} = \iiint{\vec{J}\delta^2(\vec{r}^\prime)d\tau^\prime} \underbrace{\longrightarrow}_{more\ general} \iiint_{all\ space}{\vec{J}\delta^3(\vec{r}^\prime)d\tau^\prime}$$

And Equation 5.80 is then a simply rexpressed more generally by bringing $I$ inside the integral, and rewriting in terms of $\vec{J}$ as discussed above:

$$\begin{aligned}
\vec{A}(\vec{r}) &= \frac{\mu_0 I}{4\pi} \sum_{n=0}^{\infty}{ \frac{1}{r^{n+1}} \oint{ (r^\prime)^n P_n (\cos{\alpha}) d\vec{\ell}^\prime } } \\
&= \frac{\mu_0}{4\pi} \sum_{n=0}^{\infty}{ \frac{1}{r^{n+1}} \oint{ (r^\prime)^n P_n (\cos{\alpha}) \vec{J} d\tau^\prime } }
\end{aligned}$$

\pagebreak

## Part C

> Using Equations 1.107 and 5.86, show that the dipole moment can be written as $$\vec{m} = \frac{1}{2} \int{(\vec{r}\times\vec{J})d\tau}$$

Equation 1.107: $$\vec{a} = \frac{1}{2} \oint{\vec{r}\times d\vec{\ell}}$$

Equation 5.86: $$\vec{m} = I \int{d\vec{a}} = I\vec{a}$$

Using what was discussed in-depth in Part A, we start with Equation 5.86 and rexpress $\vec{a}$ with Equation 1.107. Then, pulling the current $I$ inside the integral, we can rexpressed it in terms of a volume current density $\vec{J}=I\delta^2(\vec{r}^\prime)$.

$$\begin{aligned}
\vec{m} &= I\vec{a}\\
&= I\frac{1}{2} \oint{\vec{r}\times d\vec{\ell}} \\
&= \frac{1}{2} \oint{\vec{r}\times Id\vec{\ell}} \\
&= \frac{1}{2} \iiint{(\vec{r}\times (I\delta^2(\vec{r}^\prime) )d\tau^\prime} \\
&= \frac{1}{2} \int{(\vec{r}\times \vec{J} )d\tau^\prime}
\end{aligned}$$

Where in the last step, we replaced the initial representation of the volume current density with a more general $\vec{J}$ and used the shorthand of surpressing three integral signs as just one with the implied domain of all space.

\pagebreak

# 5.41

> A current $I$ flows to the right through a rectangular bar of conducting material, in the presence of a uniform magnetic field $\vec{B}$ point out of the page.

## Part A

> If the moving charges are positive, in which direction are they deflected by the magnetic field?

Using the Lorentz force law, $\vec{F} = q(\vec{v} \times \vec{B})$, we can use the right-hand rule to find the resulting direction for the force. To remove some ambiguity, consider the experimental setup such that $\vec{I}=I\hat{x}$ (the flow from left-to-right of the page mapping to the $x$-direction) and the magnetic field as $\vec{B}=B\hat{y}$ (out of the page). Then, since $q$ is positive (positive charges), the resulting direction for the force is $\hat{z}$ or: 'down the page'.

## Part B

> Find the resulting potential difference between the top and bottom of the bar, in terms of $B$, $v$, and the relevant dimensions of the bar.

Because of this deflection, we can think of the bar as becoming similar to a parallel plate capacitor, in which case the voltage is described by: $$V = \frac{Q}{A\epsilon_0}d$$

The separation of the 'plates' is given by the thickness $t$, and the area is (crudely) $w\ell$. For a steady current, the forces need to balance between the deflection from the Lorentz force law and the increased 'charge' of the bottom plate[^2]:

[^2]: If the system is not at equilibrium, we do not have the tools to describe or answer questions about it.

$$\begin{aligned}
F_net &= (qvB) - qE = 0 \\
qvB &= qE \\
E &= vB
\end{aligned}$$

Since the field is uniform inside the slab, we can use Equation 2.48 to rewrite the field as: $$E = \frac{\sigma}{\epsilon_0} = \frac{Q}{A\epsilon_0}$$ and then the potential is simply:

$$\begin{aligned}
V &= \frac{Q}{A\epsilon_0}d \\
\\
Q &= A\epsilon_0 E = w\ell\epsilon_0 vB\\ d &= t\\
\\
V&= \frac{ w\ell\epsilon_0 vB}{w\ell\epsilon_0}t \\
&= vBt
\end{aligned}$$

Therefore, the potential difference, from higher potential bar to lower (the bottom of the bar to the top), is $vBt$. 

## Part C

> How would your analysis change if the moving charges were negative?

The only change that occurs to the calculations can be resolved by introducing a negative sign in Part A: $\vec{I}=(-I)\hat{x}$, where we are simply treating it as though the current were flowing the opposite direction. This doesn't change the magnitude of any of the findings, just that the negative charges would be deflected up and the top of the bar would have the higher potential.

\pagebreak

# 6.3 

> Find the force of attraction between two magnetic dipoles, $\vec{m}_1$ and $\vec{m}_2$, oriented as shown in Figure 6.7, a distance $r$ apart.

## Part A

> Use Equation 6.2: $$F = 2\pi I R B \cos{\theta}$$

Equation 6.2 requires us to model the dipole moment $\vec{m}_2$, initially as a finite loop of current, $I$, with radius $R$. The magnetic field exprienced by $\vec{m}_2$ is generated by $\vec{m}_1$ using Equation 5.89:

$$\vec{B}_{\begin{subarray}{l} \text{from 1} \\ \text{on 2} \end{subarray}}(\vec{r}) = \frac{\mu_0}{4\pi} \frac{3(\vec{m}_1\cdot\hat{r})\hat{r}-\vec{m}_1}{\sqrt{r^2+R^2}^3}$$

\begin{figure}[H]
    \centering
    \begin{tikzpicture}[scale=1.5]

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (L) at (-6,0);
    \coordinate (P) at (0,2);

    % Construct triangle
    \draw[dashed] (P) -- (L) node [midway, above] {$\sqrt{r^2 + R^2}$};
    \draw (O) -- (L) node [midway, below] {$r$};
    \draw[dashed] (O) -- (P) node [midway, right] {$R$};
    \tkzFillAngle[fill=violet, opacity=0.4, size=0.3](O,L,P);
    \tkzLabelAngle[pos=0.7](O,L,P){$\varphi$};

    \node at (O) [right] {$\vec{m}_2$};
    \node at (L) [left] {$\vec{m}_1$};

    \end{tikzpicture}
\end{figure}

Then we can work to replace each quantity in 6.2 in terms of what is given. Note that the cosine of the angle between $\hat{\mathfrak{r}}$ and $\hat{R}$ is the complementary angle of $\varphi$, and so we can rephrase that as the phase shifted $\sin{\varphi}$.

$$\begin{aligned}
B_{1,2}\cos{\theta} &= \frac{\mu_0}{4\pi} \frac{3(m_1 \cos{\varphi})\hat{\mathfrak{r}}-\vec{m}_1}{\sqrt{r^2+R^2}^3}\cdot \hat{R}\\
&=\frac{\mu_0}{4\pi} \frac{3(m_1 \cos{\varphi})\sin{\varphi}}{\sqrt{r^2+R^2}^3}\\
\\
\vec{m}_2 &= I\vec{a} = \pi I R^2 \hat{r}\\
\\
F&= \frac{m_2}{R} \left( \frac{\mu_0}{4\pi} \frac{3(m_1 \cos{\varphi})\sin{\varphi}}{\sqrt{r^2+R^2}^3} \right) \\
&= \frac{\mu_0}{4\pi} \frac{ 3m_1 m_2}{R\sqrt{r^2+R^2}^3} \underbrace{\frac{r}{\sqrt{r^2+R^2}}}_{\cos{\varphi}} \underbrace{\frac{R}{\sqrt{r^2+R^2}}}_{\sin{\varphi}} \\
&= \frac{\mu_0}{4\pi} \frac{ 3m_1 m_2 r}{\sqrt{r^2+R^2}^5}\\
\\
\lim_{r>>R}{F} &= \frac{\mu_0}{4\pi} \frac{ 3m_1 m_2 r}{\sqrt{r^2+R^2}^5}\\
F &= \frac{\mu_0}{4\pi} \frac{ 3m_1 m_2 r}{r^5}\\
&= \frac{\mu_0}{4\pi} \frac{ 3m_1 m_2}{r^4}\\
\end{aligned}$$

\pagebreak

## Part B

> Use Equation 6.3: $$\vec{F} = \nabla (\vec{m}\cdot\vec{B})$$

$$\begin{aligned}
\vec{B}_{\begin{subarray}{l} \text{from 1} \\ \text{on 2} \end{subarray}}(\vec{r}) &= \frac{\mu_0}{4\pi} \frac{3(\vec{m}_1\cdot\hat{r})\hat{r}-\vec{m}_1}{r^3} \\
&= \frac{\mu_0}{4\pi} \frac{2m_1}{r^3}\hat{r} \\
\\
\vec{F} &= \nabla \left(\frac{\mu_0}{4\pi} \frac{2m_1m_2}{r^3}\right)\\
&= \frac{\partial}{\partial r} \left(\frac{\mu_0}{4\pi} \frac{2m_1m_2}{r^3}\right) \hat{r}\\
&= - \left(3\frac{\mu_0}{4\pi} \frac{2m_1m_2}{r^4}\right) \hat{r}\\
\end{aligned}$$
