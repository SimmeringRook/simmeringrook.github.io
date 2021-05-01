# PH 541: Statistical Mechanics, Week 5

$$\newcommand\dbar{đ}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{{\partial}^2 #1}{{\partial} #2 {\partial} #3}}
\begin{aligned}
\text{The following is a } &\text{test of rendering 'dbar'}\\
đ &= \dbar
\end{aligned}
$$

## Concepts

## Lecture Notes

### Day 1

?>*Recap from last lecture:*
Microstates from system A labeled by: $E_1 \leq E_2 \leq ... \leq E_r$. We left off with wanting to know the probability of finding the system A in a particular microstate $r$ with the energy $E_r$.


Remember that the heat bath, $A'$, is vasy and surrounded by a rigid, thermal isolating wall. We can talk about the total isolated system as the combination of the two: $A^0 = A' + A$. As a result, we let $E^{(0)} = E_r + E'$ and note that the total energy of the system is constant. If $A$ is in state $r$, what is the statisical weight $\Omega '(E^{{0}}-E_r)$ of the bath?

This is also the statisical weight of the entire combined system $A^{(0)}$ when $A$ is in the particular microstate $r$. Recalling that:

> **For an isolated system**, all microscopic states that are compatible with the macroscopic constraints (i.e., $E$, $V$, $N$) are equally likely to occur.

Each microstate in $\Omega '(E^{{0}}-E_r)$ is equally likely to occur, this means the probability of being in $r$ is given by the relation $P_r\propto \Omega '(E^{(0)})-E_r)$:

$$P_r = c' \Omega '(E^{(0)})-E_r)$$

> Recalling $S(E,V,N,\alpha) = k\ln{\Omega(E,V,N,\alpha)}$, we solve for $\Omega '$. $$\Omega '(E^{(0)})-E_r) = \exp{\frac{1}{k}S'(E^{(0)}-E_r)}$$
>
>We then note that the energy of the heat bath, $E^{(0)}\gg E_r$, we can do a power series expansion:
>$$\newcommand\E0{E^{(0)}}\newcommand\sPrime{S'(\E0)}
\begin{aligned}
\frac{1}{k}S'(E^{(0)}-E_r) &= \frac{1}{k}\left[\sPrime - E_r \pder{\sPrime}{\E0} + ... \right]
\end{aligned}$$

> FIll in stuff $$\Omega '(E^{(0)})-E_r) \approx \exp{\frac{1}{k} S'(\E0)}\exp{-\frac{E_r}{kT}}$$

$$\begin{aligned}
P_r &= c' \Omega '(E^{(0)})-E_r)\\
&= c'\exp{\frac{1}{k} S'(\E0)}\exp{-\frac{E_r}{kT}}\\
&= c''\exp{-\frac{E_r}{kT}}\\
\\
\sum_{r}{P_r} = 1 &\Rightarrow c'' \sum_{r}{\exp{-\frac{E_r}{kT}}} = 1\\
\Rightarrow c'' &= \frac{1}{\sum_{r}{\exp{-\frac{E_r}{kT}}}}, &\beta\equiv\frac{1}{kT}\\
&= \frac{1}{\sum_{r}{\exp{-\beta E_r}}}, &Z\equiv \sum_{r}{e^{-\beta E_r}}\\
\\
P_r = \frac{e^{-\beta E_r}}{Z}
\end{aligned}$$

!> Note that $Z$ is called the partition function.

?> Let $g(E_r)$ be the degeneracy of the $E_r$ energy.

---

$A(V, N, T)$

$y$ is a quantity that assumes the value of $y_r$ in the state $r$ of the system $A$. Let $\bar{y}$ be the mean value of $y$.

$$\bar{y} = \sum_{r}{P_r y_r} = \sum_{r}{\frac{e^{-\beta E_r}}{\sum_{r}{e^{-\beta E_r}}} y_r} = \frac{\sum_{r}{e^{-\beta E_r} y_r}}{Z}$$

### Day 2



### Day 3

#### Breakout Room Activity

> 
