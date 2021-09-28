---
title: Homework 1
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Monday, September 27, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{HW1}
    \fancyhead[LO,LE]{Knudson}
---

# Problem 2.7

> Find the electric field at a distance $z$ from the center of a spherical surface of radius $R$ that carries a uniform charge density $\sigma$. Treat both the case of inside and outside the shell and express your answer in terms of the total charge $q$ on the sphere.

Since no thickness is specified, we will assume that the spherical surface can be considered as a shell with infinitesimal thickness or similarly treated as a $S^2$ (2-sphere). Since the *surface* charge density is given as being uniform across $S^2$, we can immediately assume that the electric field will also respect this inherent symmetry. This exercise is trivial using the integrated form of Gauss's law, as the electric field outside a spherical symmetric charge is equivalent to that of a point mass and as the shell is hollow, the enclosed charge is zero, and so must be the field.

$$\begin{aligned}
\int_{S^2}{\lvert\vec{E}\rvert dA} &= \frac{Q_{enc}}{\epsilon_0}\\
\lvert\vec{E}\rvert\left(\int^{\phi=2\pi}_{\phi=0}{\int_{\theta=0}^{\theta=\pi}{r^2\sin{\theta}d\theta d\phi}}\right) &= \frac{Q_{enc}}{\epsilon_0}\\
\lvert\vec{E}\rvert 4\pi r^2 &= \frac{Q_{enc}}{\epsilon_0}\\
\vec{E} &= \frac{1}{4\pi \epsilon_0}\frac{q}{r^2}\Theta(r-R)\hat{r}
\end{aligned}$$

Alternatively, instead of just citing [Newton's Shell theorem](https://en.wikipedia.org/wiki/Shell_theorem) or symmetry, we can verify the results of Gauss's Law are true by integrating the electric field as measured at $z$. Without loss of generality, let us set the spherical shell centered on the origin and the point of interest at length $z$ away. Due to the spherical nature of the physical situation, we can define our position vectors in spherical coordinates.

$$\vec{r}=z\hat{r}, \qquad \vec{r}'=R\hat{r}'$$

Recalling that $\hat{r}$ doesn't always point in the same direction as $\hat{r}'$, we can convert these vectors[^1] to a coordinate system that has constant directions across all space: Cartesian.

$$\vec{r}=z(\sin{\theta}\cos{\phi}\hat{x}+\sin{\theta}\sin{\phi}\hat{y}+\cos{\theta}\hat{z}), \qquad \vec{r}'=R(\sin{\theta'}\cos{\phi'}\hat{x}+\sin{\theta'}\sin{\phi'}\hat{y}+\cos{\theta'}\hat{z})$$

[^1]: Here, we leverage the endpages of Griffth's 4th Edition in which he kindly provides the basis vectors for Cartesian, Cylindrical, and Spherical coordinate systems in terms of each other.

Using the fact that as we change the angle $\phi$ and $\theta$ of $\vec{r}$, the charge distribution observed by the point of interest a distance $z$ from the origin looks the same, we conclude that the field cannot depend on the $\phi$ or $\theta$ coordinates of $\vec{r}$. Similarly, we can repeat this process inside the sphere and be unable to tell if the sphere has been rotated about $\vec{r}$ in $\phi'$ or $\theta'$ or if $\vec{r}$ itself has been rotated ($\phi$, $\theta$) as the charge density is uniform. We then leverage this to remove all $\phi$ and $\phi'$ from consideration in our calculations by choosing the convent value of $\phi=\phi'=0$.

$$\vec{r}=z(\sin{\theta}\hat{x}+\cos{\theta}\hat{z}), \qquad \vec{r}'=R(\sin{\theta'}\hat{x}+\cos{\theta'}\hat{z})$$

Both inside and outside the shell, we note that $\theta$ does not impact the charge distribution observed from $\vec{r}$, and so we again choose the extremely convenient value of $\theta=0$, which is the equivalent of lining up $\hat{r}$ parallel to the $z$-axis (and which makes the most logical sense given the arbitrary name for the distance in question).

$$\vec{r}=z\hat{z}, \qquad \vec{r}'=R(\sin{\theta'}\hat{x}+\cos{\theta'}\hat{z})$$

The same cannot be said for $\vec{r}'$, however, as we consider each bit of $dq$ on the $S^2$. Intuitively, this small dependence on $\theta'$ makes sense as the total distance from $z$ to the *North* pole ($\theta'=0$) is the minimum (implicitly assuming $z>R>0$ at this moment) with a total distance of $z-R$ and that the total distance from $z$ to the *South* pole ($\theta'=\pi$) is the maximum with $z+R$. Now that our position vectors are happily sharing the same basis vectors, we can subtract them to find the distance between each bit of $dq$ and $z$.

$$\vec{r}-\vec{r}'=(-R\sin{\theta'})\hat{x}+(z-R\cos{\theta'})\hat{z}$$

We now all the components required to sum up all of the $d\vec{E}$ contributions from each bit of $dq$[^2]:

[^2]: Recall that $q=\int{\lambda dr}=\int_{S}{\sigma dA}=\int_{V}{\rho dV}$ and therefore, $dq=\sigma dA = \sigma {r'}^2 \sin{\theta'}d\phi'd\theta'$

$$\begin{aligned}
d\vec{E}(\vec{r}) &= \frac{dq}{4\pi\epsilon_0}\frac{\vec{r}-\vec{r}'}{{\lvert \vec{r}-\vec{r}'\rvert}^3}\\
&= \frac{\sigma}{4\pi\epsilon_0}\frac{\vec{r}-\vec{r}'}{{\lvert \vec{r}-\vec{r}'\rvert}^3}R^2 \sin{\theta'}d\phi'd\theta'
\end{aligned}$$

Now we finish the substitution and recall that nothing in the integrand depends on $\phi'$:

$$\begin{aligned}
\vec{E}(\vec{r}) &= \frac{\sigma}{4\pi\epsilon_0}\int_{\phi'=0}^{\phi'=2\pi}{ \int_{\theta'=0}^{\theta'=\pi}{ \frac{\vec{r}-\vec{r}'}{{\lvert \vec{r}-\vec{r}'\rvert}^3}R^2 \sin{\theta'}d\phi'd\theta' } } \\
&= \frac{\sigma 2\pi}{4\pi\epsilon_0} \int_{\theta'=0}^{\theta'=\pi}{ \frac{(-R\sin{\theta'})\hat{x}+(z-R\cos{\theta'})\hat{z}}{(z^2 + R^2 (\sin^2{\theta'}+\cos^2{\theta'}) - 2zR\cos{\theta'})^{(3/2)}}R^2 \sin{\theta'}d\theta' } \\
&= \frac{\sigma 2\pi}{4\pi\epsilon_0} \int_{\theta'=0}^{\theta'=\pi}{ \frac{(-R\sin{\theta'})\hat{x}+(z-R\cos{\theta'})\hat{z}}{(z^2 + R^2 - 2zR\cos{\theta'})^{(3/2)}}R^2 \sin{\theta'}d\theta' }
\end{aligned}$$

Note that an alternate derivation of $\vec{r}$ and $\vec{r}'$ could have required Griffith's hint to use the Law of Cosines to simplify the denominator, but we avoided that complication by involving the $x$-component in $\vec{r}'$. I will now argue from the symmetry expressed earlier, that the only directional component that matters for $\vec{E}$ is the $\hat{z}$, as all non-$\hat{z}$ components will cancel each other out as we walk $S^2$. We can then recall the advantage (or necessity) of using Cartesian directions: they are constant throughout all space (and time), and so we may move them outside the integral without problem. Next, we can work on cleaning up this integral into something more reasonable with a u-substitution, Let:

$$u=\cos{\theta'}, \qquad du = -\sin{\theta'}d\theta'$$
$$\theta'=\pi \mapsto u=-1, \qquad theta'=0 \mapsto u=1$$

$$\begin{aligned}
\vec{E}(\vec{r}) &= \frac{\sigma 2\pi R^2}{4\pi\epsilon_0} \hat{z} \int_{\theta'=0}^{\theta'=\pi}{ \frac{(z-R\cos{\theta'})\sin{\theta'}d\theta'}{(z^2 + R^2 - 2zR\cos{\theta'})^{(3/2)}}}\\
&= \frac{\sigma 2\pi R^2}{4\pi\epsilon_0} \hat{z} \int_{u=1}^{u=-1}{ \frac{(z-Ru)}{(z^2 + R^2 - 2zRu)^{(3/2)}}}(-du)\\
&= \frac{\sigma 2\pi R^2}{4\pi\epsilon_0} \hat{z} \int_{u=-1}^{u=1}{ \frac{(z-Ru)}{(z^2 + R^2 - 2zRu)^{(3/2)}}}du\\
\end{aligned}$$

Now, while this doesn't appear to really lead to anything easier to integrate, with some inspiration from WolframAlpha that this is in fact something that can be solved not only analytically but also by hand, we can proceed with a very clever and complex second u-substitution. Let:

$$\xi=\sqrt{z^2+R^2-2zRu}, \qquad d\xi =\frac{-zR}{\sqrt{z^2+R^2-2zRu}}du$$

If we substitute at this stage, we'll note that it almost works perfectly with the exception of that pesky $z-Ru$ in the numerator:

$$I = \int_{u=-1}^{u=1}{ \frac{(z-Ru)}{\xi^2}\frac{(-d\xi)}{zR}}$$

However, if we work a little creatively and square $\xi$, we can solve for a relation to replace $-Ru$:

$$\xi^2 = z^2+R^2-2zRu \quad\rightarrow\quad -Ru = \frac{\xi^2 - z^2 - R^2}{2z}$$

And now this becomes a rather elementary integral.

$$\begin{aligned}
I &= \int_{u=-1}^{u=1}{ \frac{(z+\frac{\xi^2 - z^2 - R^2}{2z})}{\xi^2}\frac{(-d\xi)}{zR}}\\
&= -\frac{1}{zR}\int_{u=-1}^{u=1}{ \frac{2z^2 + \xi^2 - z^2 - R^2}{2z\xi^2}d\xi}\\
&= -\frac{1}{2z^2R}\int_{u=-1}^{u=1}{ \frac{z^2 + \xi^2 - R^2}{\xi^2}d\xi}\\
&= - \left(\frac{z^2-R^2}{2z^2 R}\left(\frac{-1}{\xi}\right)-\frac{1}{2z^2 R}{\xi}\middle)\right)^{u=1}_{u=-1}\\
&= \frac{zu-R}{z^2 \sqrt{z^2+R^2-2zRu}}\bigg\rvert^{u=1}_{u=-1}\\
&= \frac{1}{z^2}\left(\frac{z(1)-R}{\sqrt{z^2+R^2-2zR(1)}}-\frac{z(-1)-R}{sqrt{z^2+R^2-2zR(-1)}}\right)\\
&= \frac{1}{z^2}\left(\frac{z-R}{\sqrt{(z-R)^2}}+\frac{z+R}{\sqrt{(z+R)^2}}\right)\\
\end{aligned}$$

Adding back the rest of the the integral, we can proceed with the final steps of this solution. Since the square root in the denominators came from the distance formula and has to be a positive value to make physical sense, we take a moment to note the subtlety of this situation. Recall that the result of $x^2$ is always a positive number (for $x\in\mathbb{R}$), but $x$ can be positive or negative; because the square root is removing the square, we must wrap each denominator with absolute value bars to preserve the functional form.

$$\begin{aligned}
\vec{E}(\vec{r}) &= \frac{\sigma 2\pi R^2}{4\pi\epsilon_0} \hat{z} \underbrace{\int_{u=-1}^{u=1}{ \frac{(z-Ru)}{(z^2 + R^2 - 2zRu)^{(3/2)}}}du}_{I}\\
&= \frac{\sigma 2\pi R^2}{4\pi\epsilon_0} \hat{z} \frac{1}{z^2}\left(\frac{z-R}{\sqrt{(z-R)^2}}+\frac{z+R}{\sqrt{(z+R)^2}}\right)\\
&= \frac{\sigma 2\pi R^2}{4\pi\epsilon_0} \frac{1}{z^2}\left(\frac{z-R}{\lvert z-R \rvert}+\frac{z+R}{\lvert z-R \rvert}\right) \hat{z}
\end{aligned}$$

Functionally, the resulting fractions are similar to the Kronecker Delta in that they have a magnitude of $\pm 1$ but the numerator serves as a mechanism for determining the sign. The sign, $sgn$, or signum function is defined as follows:

$$\text{sgn}(x) \equiv \begin{cases} 1 \quad & x > 0 \\ 0 \quad & x = 0 \\ -1 \quad & x < 0 \\ \end{cases}$$

And so now we evaluate the field inside and outside the hollow sphere:

$$|z| > |R| \mapsto \begin{cases} z+R > z-R > 0 \quad & \text{sgn}(z-R)+\text{sgn}(z+R)=2 \\ 0 > z-R > z+R \quad & \text{sgn}(z-R)=\text{sgn}(z+R)=-2 \\ \end{cases}$$

$$|z| < |R| \mapsto \begin{cases} 0 > z+R > z-R \quad & \underbrace{\text{sgn}(z-R)}_{-1} + \underbrace{\text{sgn}(z+R)}_{1} = 0 \\ z-R > 0 > z+R \quad & \underbrace{\text{sgn}(z-R)}_{1} + \underbrace{\text{sgn}(z+R)}_{-1} = 0 \\ \end{cases}$$

We then substitute this into our calculate $\vec{E}$:

$$\begin{aligned}
\vec{E}(\vec{r}) &= \frac{\sigma 2\pi R^2}{4\pi\epsilon_0} \frac{\text{sgn}(z-R) + \text{sgn}(z+R)}{z^2} \hat{z} \\
&= \frac{1}{4\pi\epsilon_0}\begin{cases} \pm 4\pi R^2 \sigma \frac{\hat{z}}{z^2} \quad & |z| > |R| \\ 0 \quad & |z| < |R|
\end{cases}
\end{aligned}$$

Having confirmed our findings from Gauss's Law, we then unfix $z$ from the $z$-axis as only the radial distance from the origin matters and we can express the field in its more common form:

$$
\vec{E}(\vec{r}) = \frac{1}{4\pi\epsilon_0}\begin{cases} \frac{q}{r^2}\hat{r} \quad & |r| > |R| \\ 0 \quad & |r| < |R|
\end{cases}
$$
