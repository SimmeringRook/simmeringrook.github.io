# MTH 537: General Relativity, Week 7


## Concepts


## Lecture Notes

### Day 1

## Day 1

Curvature 2-forms in Rain Coordinate for Schwarzschild:

$$\begin{aligned}
{\Omega^T}_\phi &= -\frac{m}{r^3} \sigma^T\wedge\sigma^\phi\\
{\Omega^T}_R &= \frac{2m}{r^3} \sigma^T\wedge\sigma^R\\

\end{aligned}$$

We have a $-1$ from the signature, but also a $-1$ from the *dot* product of $\hat{t}\cdot\hat{t}$:

$$\begin{aligned}
{\Omega^\phi}_T &= {\Omega^T}_\phi \\
{\Omega^R}_T &= {\Omega^T}_R \\
\end{aligned}$$

$$
{\Omega^i}_j = \frac{1}{2}{R^i}_{jk\ell}\sigma^k\wedge\sigma^\ell

{\Omega^\phi}_T = \frac{1}{2}{R^\phi}_{T\phi T}\sigma^\phi\wedge\sigma^T + \frac{1}{2}{R^\phi}_{TT \phi}\sigma^T\wedge\sigma^\phi + ...\\
&= -\frac{m}{r^3} \sigma^T\wedge\sigma^\phi
$$

$$
{R^\phi}_{T\phi T} = +\frac{m}{r^3}\\
{R^R}_{TRT} = - \frac{2m}{r^3}
$$

### Case 1

!> Q: Find $\ddot{(r\Delta\phi)}$

We know:

$$\begin{aligned}
\dot{r}^2 &= e^2 - f\\
\dot{\phi} = 0 &\Rightarrow \dot{(\Delta\phi)}=0\\
(\Delta s)^{\cdot\cdot} &= (r\Delta \phi)^{\cdot\cdot} = \ddot{r}\Delta\phi\\
\\
2\dot{r}\ddot{r} &= 0 - f' \dot{r}\\
\Rightarrow \ddot{r} &= - \frac{1}{2}f' = - \frac{m}{r^2}\\
\\
\ddot{r}\Delta\phi &= - \frac{m}{r^2}\Delta\phi = - \frac{m}{r^3}\Delta s
\end{aligned}$$

### Case 2

Use Rain Coordinates with Spherical symmetry for radial paths:

$$ds^2 = -dT^2 + \frac{2m}{r} dR^2$$

$$\Delta s = \sqrt{\frac{2m}{r}} \Delta R$$

!> Q: Find $(\Delta S)^{\cdot\cdot} = (\sqrt{\frac{2m}{r}})^{\cdot\cdot}\Delta R$

$$\begin{aligned}
\dot{r}^2 &= 1 - f\\
&= \frac{2m}{r}\\
\dot{r} = -\sqrt{\frac{2m}{r}}\\
\Rightarrow \ddot{r} &= - \frac{1}{2}f' = - \frac{m}{r^2}\\
\Delta s = \frac{2m}{r}\Delta R = -\dot{r}\Delta R\\
(\Delta s)^{\cdot} = -\ddot{r}\Delta R = + \frac{m}{r^2}\Delta R\\
(\Delta s)^{\cdot\cdot} = -\frac{2m}{r^3}\dot{r}\Delta R = \frac{2m}{r^3}\\
\end{aligned}$$
