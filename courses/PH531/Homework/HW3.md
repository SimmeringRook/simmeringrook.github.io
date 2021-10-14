---
title: Homework 3
subtitle: PH531, Fall 2021
author: Thomas Knudson
date: Wednesday, October 13, 2021
papersize: a4
geometry: margin=2cm
linkcolor: blue
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz-3dplot}
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 531, Fall 2021}
    \fancyhead[CO,CE]{HW3}
    \fancyhead[LO,LE]{Knudson}
---

# Problem 3.9


\pagebreak

# Problem 3.16

> A cubical box (sides of length $a$) consists of five metal plates, which are welded together and grounded. The top is made of a separate sheet of metal, insulated from the others, and held at a constant potential $V_0$. Find the potential inside the box.

Consider the boundary conditions for this physical situation:

$$
\begin{array}{llcl}
(i) & V = 0 &\qquad & x = 0 \\
(ii) & V = 0 &\quad & x = a \\
(iii) & V = 0 &\quad & y = 0 \\
(iv) & V = 0 &\quad & y = a \\
(v) & V = 0 &\quad & z = 0 \\
(vi) & V = V_0(x,y) &\quad & z = a \\
\end{array}
$$

Recalling from pervious experience, we have a handful of patterns for inspiring our Ansatz:

- If: the boundary conditions are symmetric, the general solution to the second order ODE is a linear combination of sine and cosine
  - If: the boundary is 0 on both ends, the sine function is the correct description.
  - Else: the boundary is the same on both ends (and non-zero), the cosine function will correctly describe the physical situation.
- Else: the general solution is going to be a linear combination of real valued exponentials

Using this information, we consider a solution to Laplace's equation that is comprised of the product from three functions, each only dependent on one unique spatial variable: $V(x,y,z) = X(x)Y(y)Z(z)$. From this, we note that we are able to isolate each coordinate and its dependent function with the corresponding second (partial) derivative. From this, we note that changes to one variable cannot effect the values of the other derivatives, and so each second partial derivative must be equal to some constant.

$$\frac{1}{X(x)}\frac{\partial^2 X(x)}{\partial x^2} + \frac{1}{Y(y)}\frac{\partial^2 Y(y)}{\partial y^2} + \frac{1}{Z(z)}\frac{\partial^2 Z(z)}{\partial z^2} = C_1 + C_2 + C_3 = 0$$

$$\frac{1}{X(x)}\frac{d^2 X(x)}{dx^2} = C_1, \quad \frac{1}{Y(y)}\frac{d^2 Y(y)}{dy^2} = C_2, \quad \frac{1}{Z(z)}\frac{d^2 Z(z)}{dz^2}= C_3$$

Again, leveraging past experience (as mentioned above), we can see that $X(x)$ and $Y(y)$ will take negative values for their constant for the sine and cosine solutions, and that $C_3$ will be the additive inverse of $C_1$ and $C_2$:

$$\frac{d^2 X(x)}{dx^2} = -k^2 X(x), \quad \frac{d^2 Y(y)}{dy^2} = -\ell^2 Y(y), \quad \frac{d^2 Z(z)}{dz^2}= (k^2 +\ell^2) Z(z)$$

$$\begin{aligned}
X(x) &= \alpha_1 \sin{kx} + \alpha_2 \cos{kx}\\
Y(y) &= \beta_1 \sin{\ell y} + \beta_2 \cos{\ell y}\\
Z(z) &= \gamma_1 e^{\sqrt{k^2 +\ell^2}z} + \gamma_2 e^{-\sqrt{k^2 +\ell^2}z}
\end{aligned}$$

Applying boundary conditions in quick succession, we can see that $\alpha_2=\beta_2=0$ as neither cosine function are valid (using $(i)$ and $(iii)$). Then with $(ii)$ and $(iv)$, $k$ and $\ell$ must be integer multiples of $\pi/a$ such that when the corresponding coordinate value reaches $a$, the argument reduces to an integer multiple of $\pi$. Finally, since neither real exponential go to $0$ at $z=0$, $\gamma_1$ and $\gamma_2$ must be additive inverses of each other.

$$\begin{aligned}
X(x) &= \alpha_1 \sin{\left(\frac{n\pi}{a}x\right)}\\
Y(y) &= \beta_1 \sin{\left(\frac{m\pi}{a}y\right)}\\
Z(z) &= 2\gamma_1 \text{sinh}\left(\frac{\pi}{a}\sqrt{n^2 + m^2}z\right)
\end{aligned}$$

This means our solution for the potential inside this box currently has the form:

$$V(x,y,z) = \sum_{n,m}{(2\alpha_n\beta_m\gamma_{n,m}) \sin{\left(\frac{n\pi}{a}x\right)}\sin{\left(\frac{m\pi}{a}y\right)} \text{sinh}\left(\frac{\pi}{a}\sqrt{n^2 + m^2}z\right)}$$

Using our final boundary condition, we wrap all the remaining constants inside $C_{n,m}$ and evaluate $(vi)$:

$$V(x,y, z=a) = \sum_{n,m}{(2\alpha_n\beta_m\gamma_{n,m}) \sin{\left(\frac{n\pi}{a}x\right)}\sin{\left(\frac{m\pi}{a}y\right)} \text{sinh}\left(\frac{\pi}{a}\sqrt{n^2 + m^2}a\right)} = V_0(x,y)$$

Remembering that sine functions are orthogonal to other sine functions (Fourier Series), we can take the inner product of both sides to eliminate the summation and solve for $C_{n,m}$ generally:

$$\begin{aligned}
V_0(x,y) &= \sum_{n,m}{C_{n,m} \sin{\left(\frac{n\pi}{a}x\right)}\sin{\left(\frac{m\pi}{a}y\right)} \text{sinh}\left(\pi\sqrt{n^2 + m^2}\right)} \\
\int_{0}^{a}{\int_{0}^{a}{V_0(x,y)\sin{\left(\frac{n'\pi}{a}x\right)}\sin{\left(\frac{m'\pi}{a}y\right)}dx}dy} &= \sum_{n,m}{C_{n,m}\text{sinh}\left(\pi\sqrt{n^2 + m^2}\right)\left(\frac{a}{2}\delta_{m,m'}\right)\left(\frac{a}{2}\delta_{n,n'}\right)} \\
C_{n,m} &= \frac{4 V_0}{a^2 \text{sinh}\left(\pi\sqrt{n^2 + m^2}\right)} \int_{0}^{a}{sin{\left(\frac{n\pi}{a}x\right)} dx}\int_{0}^{a}{\sin{\left(\frac{m\pi}{a}y\right)}dy}\\
C_{n,m} &= \frac{4 V_0}{a^2 \text{sinh}\left(\pi\sqrt{n^2 + m^2}\right)} \left(\frac{a}{m\pi}(1-\cos{m\pi})\right)\left(\frac{a}{n\pi}(1-\cos{n\pi})\right)
\end{aligned}$$

Note the two possible outcomes:

$$\begin{array}{llc} m,n & \qquad even \qquad & 0 \\ m,n & \qquad odd &  \frac{4}{nm\pi^2}\end{array}$$

Applying this simplification:

$$C_{n,m} = \left(\frac{16V_0}{nm\pi^2}\right)\frac{1}{\text{sinh}\left(\pi\sqrt{n^2 + m^2}\right)}$$

And with that, we obtain our solution for inside the box:

$$V(x,y,z) = \sum_{n,m\in\\ (2\mathbb{Z^+}+1)}^{\infty}{ \left(\frac{16V_0}{nm\pi^2}\right)\frac{ \sin{\left(\frac{n\pi}{a}x\right)} \sin{\left(\frac{m\pi}{a}y\right)} \text{sinh}\left(\frac{\pi}{a}\sqrt{n^2 + m^2}z\right) }{\text{sinh}\left(\pi\sqrt{n^2 + m^2}\right)}}$$

Implementing this in Mathematica, we use the following code:

```Mathematica
NumberOfSteps = 3;
a = 1; V[x_, y_, z_] :=
 Sum[(16 Subscript[V, 0])/(n*m*\[Pi]^2)*Sin[(n*\[Pi])/a x]*
   Sin[(m*\[Pi])/a y]*Sinh[\[Pi]/a*Sqrt[n^2 + m^2]*z]/
   Sinh[\[Pi] Sqrt[n^2 + m^2]], {n, 1, 2*NumberOfSteps + 1, 2}, {m, 1,
    2*NumberOfSteps + 1, 2}]
N[V[a/2, a/2, a/2]]
```

And obtain the numeric approximated value of $1.\bar{6}V_0$ which is equivalent to $V_0/6$.

\pagebreak

# Problem 3.23

> A spherical shell of radius $R$ carries a uniform surface charge $\sigma_0$ on the "northern" hemisphere, $\theta\in[0,\pi/2]$, and a uniform surface charge $-\sigma_0$ on the "southern" hemisphere, $\theta\in[\pi/2,\pi]$. Find the potential inside and outside the sphere, calculating the coefficients explicitly up to $A_6$ and $B_6$.

Up until the boundary conditions, this is the same physical situation as Example 3.9 on page 147 of Griffiths, and so we expect the same general solution. The charge distribution has axial symmetry and so we conclude the potential anywhere in space (inside/out) must only be a function of $r$ and $\theta$. The general solution is then given as a product of the two series:

$$V(r,\theta) = R(r)\Theta(\theta) = \sum_{\ell=0}^{\infty}{\left(A_{\ell} r^{\ell} + \frac{B_\ell}{r^{\ell+1}}\right) P_\ell (\cos{\theta})}$$

The boundary conditions for this situation are more like book-keeping:

- $V$ needs to be well behaved at the origin,
- and since not specified, we assume the reference point of potential is out at $\infty$.

$$
\begin{array}{llcl}
(i) & V < \infty &\qquad & r\rightarrow 0 \\
(ii) & V\rightarrow 0 &\quad & r\rightarrow \infty \\
(iii) & \sigma(\theta) = \sigma_0 &\quad & \theta\in[0,\pi/2)\\
(iv) & \sigma(\theta) = -\sigma_0 &\quad & \theta\in(\pi/2,\pi] \\
(v) & V_{in}(R,\theta) = V_{out}(R,\theta) &\quad & r=R
\end{array}
$$

Applying the first boundary condition, $(i)$, we can see that for $r<R$, $B_\ell$ must identically be $0$ for all possible $\ell$, or the denominator will behave badly. Similarly, with $(ii)$, all $A_\ell$ must be identically $0$ such that the function can approach $0$ as $r\rightarrow\infty$. As such, we obtain the piecewise definition:

$$V(r,\theta) = \sum_{\ell=0}^{\infty}{ \left(\begin{cases} A_{\ell} r^{\ell} & r \leq R \\ \frac{B_\ell}{r^{\ell+1}} & r \geq R \end{cases}\right) P_\ell (\cos{\theta})}$$

We then use $(v)$ to begin resolving some of these coefficients:

$$\begin{aligned}
V_{in}(R,\theta) &= V_{out}(R,\theta)\\
\sum_{\ell=0}^{\infty}{A_{\ell} R^{\ell} P_\ell (\cos{\theta})} &= \sum_{\ell=0}^{\infty}{ \frac{B_\ell}{r^{\ell+1}}P_\ell (\cos{\theta})} \\
\left(\sum_{\ell=0}^{\infty}{A_{\ell} R^{\ell} P_\ell (\cos{\theta})}\right) \left(\sum_{\ell^{\prime}=0}^{\infty}{P_{\ell^{\prime}} (\cos{\theta})}\sin{\theta}\right) &= \left(\sum_{\ell=0}^{\infty}{ \frac{B_\ell}{r^{\ell+1}}P_\ell (\cos{\theta})}\right) \left(\sum_{\ell^{\prime}=0}^{\infty}{P_{\ell^{\prime}} (\cos{\theta})}\sin{\theta}\right) \\
\sum_{\ell, \ell^{\prime}}^{\infty}{ \int_{0}^{\pi}{A_{\ell} R^{\ell} P_\ell (\cos{\theta})P_{\ell^{\prime}} (\cos{\theta})\sin{\theta} d\theta} } &= \sum_{\ell, \ell^{\prime}}^{\infty}{ \int_{0}^{\pi}{\frac{B_\ell}{R^{\ell+1}} P_\ell (\cos{\theta})P_{\ell^{\prime}} (\cos{\theta})\sin{\theta} d\theta} } \\
\\
\int_{0}^{\pi}{P_\ell (\cos{\theta})P_{\ell^{\prime}} (\cos{\theta})\sin{\theta} d\theta} &= \delta_{\ell,{\ell^{\prime}}} \\
\\
A_{\ell} R^{\ell} &=\frac{B_\ell}{R^{\ell+1}}
\end{aligned}
$$

\begin{equation}\label{Bcoeff}
B_\ell = A_{\ell} R^{2\ell + 1}
\end{equation}

Now, using Equation 2.36 from Page 90, we can introduce $\sigma(\theta)$ to the discussion by considering the discontinuity in the derivative of $r$ at $r=R$:

$$\frac{\partial V_{out}}{\partial r} - \frac{\partial V_{in}}{\partial r} = -\frac{\sigma(\theta)}{\epsilon_0}$$

$$\begin{aligned}
\frac{\partial V_{out}}{\partial r} &= - \sum_{\ell=0}^{\infty}{(\ell+1) \frac{B_\ell}{r^{\ell+2}}P_\ell (\cos{\theta})} \\
\frac{\partial V_{in}}{\partial r} &= \sum_{\ell=0}^{\infty}{(\ell) A_{\ell} r^{\ell - 1} P_\ell (\cos{\theta})}
\end{aligned}$$

$$\begin{aligned}
-\frac{\sigma(\theta)}{\epsilon_0} &= \left(- \sum_{\ell=0}^{\infty}{(\ell+1) \frac{B_\ell}{r^{\ell+2}}P_\ell (\cos{\theta})} - \sum_{\ell=0}^{\infty}{(\ell) A_{\ell} r^{\ell - 1} P_\ell (\cos{\theta})}\right)_{r=R}\\
&= -\sum_{\ell=0}^{\infty}{\left((\ell+1) \frac{A_{\ell} R^{2\ell + 1}}{R^{\ell+2}} +\ell A_{\ell} R^{\ell - 1}\right)} P_\ell (\cos{\theta}) \\
\frac{\sigma(\theta)}{\epsilon_0} &= \sum_{\ell=0}^{\infty}{A_{\ell}R^{\ell - 1}(2\ell+1) P_\ell (\cos{\theta})}  \\
\end{aligned}$$

The coefficients, $A_\ell$, can be isolated by using the inner product with the Legendre Polynomials again (as was done previous to isolate $B_\ell$):

$$\begin{aligned}
\int_{0}^{\pi}{P_{\ell^{\prime}} (\cos{\theta})\sin{\theta}\frac{\sigma(\theta)}{\epsilon_0} d\theta} &= \sum_{\ell=0}^{\infty}{\int_{0}^{\pi}{P_{\ell^{\prime}} (\cos{\theta})\sin{\theta}A_{\ell}R^{\ell - 1}(2\ell+1) P_\ell (\cos{\theta}) d\theta}} \\
2A_{\ell}R^{\ell - 1} &= \frac{1}{\epsilon_0}\left(\int_{0}^{\pi/2}{(\sigma_0)P_{\ell^{\prime}} (\cos{\theta})\sin{\theta} d\theta} + \int_{\pi/2}^{\pi}{(-\sigma_0)P_{\ell} (\cos{\theta})\sin{\theta} d\theta}\right) \\
A_{\ell} &= \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(\int_{0}^{\pi/2}{P_{\ell} (\cos{\theta})\sin{\theta} d\theta} - \int_{\pi/2}^{\pi}{P_{\ell} (\cos{\theta})\sin{\theta} d\theta}\right) \\
\end{aligned}$$

Now, looking at Table 3.1 on Page 142, we are given a table of the first 6 Legendre Polynomials ($\ell\in[0,5]$) as functions of $x$:

| $\ell$ | $P_{\ell} (x)$ |
| - | --- |
| $$0$$ | $$1$$ |
| $$1$$ | $$x$$ |
| $$2$$ | $$\frac{3x^2 - 1}{2}$$ |
| $$3$$ | $$\frac{5x^3 - 3x}{2}$$ |
| $$4$$ | $$\frac{35x^4 - 30x^2 + 3}{8}$$ |
| $$5$$ | $$\frac{63x^5-70x^3+15x}{8}$$ |

Drawing on experience, the long path to a solution is to evaluate each inner product; the short path is that there's typically a pattern in the coefficients (normally odd vs even). Reexamining the $\ell$-th coefficient, we'll do a change of variables as suggested by Table 3.1, but not until after we do something non-obvious at first: Let us exploit that $\cos{\theta}=\cos{-\theta}$ to flip the intervals of integration first:

$$\begin{aligned}
A_{\ell} &= \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(-\int_{\pi/2}^{0}{P_{\ell} (\cos{\theta})\sin{\theta} d\theta} -(-1) \int_{\pi}^{\pi/2}{P_{\ell} (\cos{\theta})\sin{\theta} d\theta}\right) \\
\varphi = -\theta, &\quad \sin{\varphi}d\varphi = \sin{(-\theta)}d\theta = -\sin{\theta}d\theta\\
&= \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(-\int_{\pi/2}^{0}{P_{\ell} (\cos{\varphi})\ (-\sin{\varphi}) d\varphi} -(-1) \int_{\pi}^{\pi/2}{P_{\ell} (\cos{\varphi})\ (-\sin{\varphi}) d\varphi}\right) \\
&= \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(\int_{\pi/2}^{0}{P_{\ell} (\cos{\varphi})\sin{\varphi}d\varphi} - \int_{\pi}^{\pi/2}{P_{\ell} (\cos{\varphi})\sin{\varphi} d\varphi}\right) \\
\text{Rename } &\varphi \mapsto \theta\\
A_{\ell} &= \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(\int_{\pi/2}^{0}{P_{\ell} (\cos{\theta})\sin{\theta}d\theta} - \int_{\pi}^{\pi/2}{P_{\ell} (\cos{\theta})\sin{\theta} d\theta}\right)
\end{aligned}$$

Now we proceed with the $u$-subsitution inspired by Table 3.1:

$$x=\cos{\theta}, \quad \begin{cases} x = \cos{0} = 1 \text{,} & \theta=0 \\
x = \cos{\pi/2} = 0 \text{,} & \theta=\pi/2 \\
x = \cos{\pi} = -1 \text{,} & \theta=\pi  \end{cases} \\
A_{\ell} = \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(\int_{0}^{1}{P_{\ell} (x)dx} - \int_{-1}^{0}{ P_{\ell} (x)dx}\right)$$

We can also note the trend in the provided polynomials that even values of $\ell$ correspond to even powers of $x$ and that odd values of $\ell$ give odd powers of $x$. With this, we can reflect the interval of integration on the second integral through a sneaky $u$-sub: Let $-u=x$, $-du=dx$:

$$\text{Let } -u=x,\ -du=dx \\
-u=-1,\ -u=0 \quad\rightarrow u\in[0,1]\\
\int_{-1}^{0}{ P_{\ell} (x)dx} = \int_{1}^{0}{ P_{\ell} (-u)(-du)} = +\int_{0}^{1}{ (-1)^\ell P_{\ell} (u)du}$$

And since $u$ is a "dummy variable", we can rename it back to $x$ to make comparisons with the other integrand simpler.

$$A_{\ell} = \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(\int_{0}^{1}{P_{\ell} (x)dx} - \int_{0}^{1}{ (-1)^\ell P_{\ell} (x)dx}\right)$$

And finally, we end up at a very simple pattern. By factoring the integral out to the right, we're left with a very simple expression that can be evaluated based on the odd/evenness of $\ell$:

$$A_{\ell} = \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left(1 - (-1)^\ell\right)\int_{0}^{1}{P_{\ell} (x)dx} = \frac{\sigma_0}{2\epsilon_0 R^{\ell - 1}}\left\{\begin{array}{ll} 0, \qquad & \text{if }\ell\in 2\mathbb{Z^+} \\ 2, &  \text{if }\ell\in (2\mathbb{Z^+} +1)  \end{array}\right\}\int_{0}^{1}{P_{\ell} (x)dx}$$

\pagebreak

All even values of $\ell$ cause our $A_\ell$ and $B_\ell$ coefficients to evaluate to $0$ (recall Equation \ref{Bcoeff}), and so we only have to truly integrate 3 of the Legendre Polynomials:

| $$\ell$$ | $$\int_{0}^{1}{P_{\ell} (x)dx}$$ | $$A_{\ell} = \frac{\sigma_0}{\epsilon_0 R^{\ell - 1}}\int_{0}^{1}{P_{\ell} (x)dx}$$ | $$B_\ell = A_{\ell} R^{2\ell + 1}$$ |
| - | --- | -- | -- |
| $$0$$ | $$-$$ | $$0$$ | $$0$$ |
| $$1$$ | $$\int_{0}^{1}{xdx}=\frac{1}{2}$$ | $$\frac{\sigma_0}{2\epsilon_0}$$ | $$\frac{\sigma_0}{2\epsilon_0}R$$ |
| $$2$$ | $$-$$ | $$0$$ | $$0$$ |
| $$3$$ | $$\int_{0}^{1}{\frac{5x^3 - 3x}{2}dx}=-\frac{1}{8}$$ | $$-\frac{\sigma_0}{8\epsilon_0 R^{3-1}}$$ | $$-\frac{\sigma_0 R^{2(3)+1}}{8\epsilon_0 R^{2}}$$ |
| $$4$$ | $$-$$ | $$0$$ | $$0$$ |
| $$5$$ | $$\int_{0}^{1}{\frac{63x^5-70x^3+15x}{8}dx}=\frac{1}{16}$$ | $$\frac{\sigma_0}{16\epsilon_0 R^{5-1}}$$ | $$\frac{\sigma_0 R^{2(5)+1}}{16\epsilon_0 R^{4}}$$ |
| $$6$$ | $$-$$ | $$0$$ | $$0$$ |

Finally, putting it all together, we obtain the potential everywhere in space:

$$V(r,\theta) = \frac{\sigma_0}{\epsilon_0} \left\{
\begin{array}{lc}
\frac{1}{2} - \frac{1}{8 R^2} + \frac{1}{16 R^4} & r \leq R \\
\frac{R}{2} - \frac{R^5}{8} + \frac{R^7}{16} & r \geq R
\end{array}\right\} + \sum_{\ell=7}^{\infty}{\begin{cases} \frac{\sigma_0}{\epsilon_0 R^{\ell - 1}}\int_{0}^{1}{P_{\ell} (x)dx} & r \leq R \\ \frac{\sigma_0 R^{2\ell + 1}}{\epsilon_0 R^{\ell - 1}}\int_{0}^{1}{P_{\ell} (x)dx} & r \geq R \end{cases}}$$
