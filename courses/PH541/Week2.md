# PH 541: Statistical Mechanics, Week 2

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

### Day 2

#### SWBQ from last class:
Show that for an ideal gas that undergoes a adiabatic expansion or compression, the equation of state satisfies:

$$\begin{aligned}
pV^\gamma &= \text{constant} \\
&\text{where }\gamma = (1+\frac{R}{C_V})=\frac{C_p}{C_V}
\end{aligned}$$

Zap with d:

$$\begin{aligned}
d(pV) &= nRdT \\
pdV+Vdp &= nRdT
\end{aligned}$$

Use first law:
$$\begin{aligned}
\bar{d}Q &= dE+\bar{d}W \\
&dQ = 0 \text{ (adiabatic)} \\
&dE = nC_v dT \\
&\bar{d}W = pdV \\
0 &= nC_v dT + pdV \\
pdV &= - nC_v dT
\end{aligned}$$

Substitute and continue:

$$\begin{aligned}
pdV+Vdp &= -\frac{Rp}{C_v}dV \\
pdV+\frac{Rp}{C_v}dV &= -Vdp
\end{aligned}$$

#### Entropy of an ideal gas

Ideal gas is sometimes referred to as a "perfect gas" (gas molecules do not interact to have any potential energy; all energy comes from kinetic)

SWBQ

Consider $n_0$ moles of an ideal gas that occupies a volume $V_0$ and at the temperature $T_0$. Let $S_0$ be the molar entropy of the gas at this specific macroscopic state (macro state).

> Molar entropy is the entropy of one mole of this gas.

Calculate the entropy $S(T,V,n)$ of the gas at $T$ and $V$.

- start with first law
- solve for dS
- use $dE$ in terms of molar specific heat capcity
  - we can only do this substitution because we have an ideal gas
  - energy does not depend on internal volume
- use $pV=nRT$ to rewrite $p$ in terms of given variables
- integrate
  - approximate that $C_V(T)$ is constant over small change in $T$


$$\begin{aligned}
\int_{(T_0, V_0)}^{(T,V)}{dS} &= \int_{T_0}^{T}{nC_V(T)\frac{dT}{T}} + \int \\
Sn-S_0 n_0 &= n\left(\ln{\left(\frac{T}{T_0}\right)}^{C_V} + \ln{\left(\frac{V}{V_0}\right)}^R\right) \\
Sn &= n\left(\ln{\left(\frac{T}{T_0}\right)}^{C_V} + \ln{\left(\frac{V}{V_0}\right)}^R\right) + S_0 n_0 \\
S &= \left(\ln{\left(\frac{T}{T_0}\right)}^{C_V} + \ln{\left(\frac{V}{V_0}\right)}^R\right) + S_0\frac{n_0}{n} \\
S(T,V,n) &= n\left(C_V\ln{(T)}+R\ln{(V)}+S_0(T_0,V_0)\right)
\end{aligned}$$

### Day 3

Today:

- Investigate general relation for homogeneous substance
  - E.g., liquids, gases, solids
- Derive Maxwell's Relations
  - page 161 to page 170

## Maxwell's Relations

### Recap

Start with the First Law:

$$\begin{aligned}
\bar{d}Q &= dE + \bar{d}W
\end{aligned}$$

In the case the system undergoes a quasi-static process (at each step, the system can be considered at equilibrium)

$$\begin{aligned}
TdS &= dE + pdV \\
dS &= \frac{1}{T}dE + \frac{p}{T}dV
\end{aligned}$$

!> recall that if we can write a differential as a total differential, we can conclude: $S=S(E,V)$

$$dS = \left(\frac{\partial S}{\partial E}\right)_V dE + \left(\frac{\partial S}{\partial V}\right)_E dV$$

This tells us that the partial derivatives must be equal to the coefficients of the differentials in the statement above:

$$\begin{aligned}
\left(\frac{\partial S}{\partial E}\right)_V &= \frac{1}{T}\\
\left(\frac{\partial S}{\partial V}\right)_E &= \frac{p}{T}
\end{aligned}$$

### From there

- We can choose any 2 parameters as independent variables

#### E with S and V independent

So, let's try choosing $S$ and $V$ as our independent variables:

$$\begin{aligned}
TdS &= dE + pdV \\
dE &= TdS - pdV \\
\\
E &= E(S,V) \\
\\
dE &= \left(\frac{\partial E}{\partial S}\right)_V dS + \left(\frac{\partial E}{\partial V}\right)_S dV \\
\\
\left(\frac{\partial E}{\partial S}\right)_V &= T \\
\left(\frac{\partial E}{\partial V}\right)_S &= -p
\end{aligned}$$

Order of second partial derivative doesn't matter -> Clauriet's Theorem

$$\begin{aligned}
\left(\frac{\partial }{\partial V}\right)_S \left(\frac{\partial}{\partial S}\right)_V E &= \frac{\partial^2 E}{\partial V\partial S} \\
\frac{\partial^2 E}{\partial V\partial S} &= \frac{\partial^2 E}{\partial S\partial V}\\
\frac{\partial^2 E}{\partial S\partial V} &= \left(\frac{\partial }{\partial S}\right)_V \left(\frac{\partial}{\partial V}\right)_S E
\end{aligned}$$

We can use this to rewrite:

$$\begin{aligned}
\left(\frac{\partial }{\partial V}\right)_S T &= \left(\frac{\partial T}{\partial V}\right)_S \\
\left(\frac{\partial }{\partial S}\right)_V \left(-p\right) &= -\left(\frac{\partial p}{\partial S}\right)_V \\
\\
\left(\frac{\partial T}{\partial V}\right)_S &= -\left(\frac{\partial p}{\partial S}\right)_V
\end{aligned}$$

#### H with S and p independent

Start with First Law, be we want $dS$ and $dp$ (not $dV$)

$$\begin{aligned}
TdS &= dE + pdV \\
dE &= TdS - pdV - Vdp + Vdp\\
dE &= TdS - d(pV) + Vdp\\
dE + d(pV) &= TdS + Vdp\\
d(E+pV) &= TdS + Vdp\\
\\
H &= E + pV \equiv \text{ Enthalpy}\\
\\
dH &= TdS + Vdp\\
H &= H(S,p)\\
\\
dH &= \left(\frac{\partial H}{\partial S}\right)_p dS + \left(\frac{\partial H}{\partial p}\right)_S dp \\
\\
\left(\frac{\partial H}{\partial S}\right)_p &= T \\
\left(\frac{\partial H}{\partial p}\right)_S &= V
\end{aligned}$$

Order of second partial derivative doesn't matter -> Clauriet's Theorem

$$\begin{aligned}
\left(\frac{\partial }{\partial p}\right)_S \left(\frac{\partial}{\partial S}\right)_p H &= \frac{\partial^2 H}{\partial p\partial S} \\
\frac{\partial^2 H}{\partial p\partial S} &= \frac{\partial^2 H}{\partial S\partial p}\\
\frac{\partial^2 H}{\partial S\partial p} &= \left(\frac{\partial }{\partial S}\right)_p \left(\frac{\partial}{\partial p}\right)_S H
\end{aligned}$$

We can use this to rewrite:

$$\begin{aligned}
\left(\frac{\partial }{\partial p}\right)_S T &= \left(\frac{\partial T}{\partial p}\right)_S \\
\left(\frac{\partial }{\partial S}\right)_p V &= \left(\frac{\partial p}{\partial S}\right)_p \\
\\
\left(\frac{\partial T}{\partial p}\right)_S &= \left(\frac{\partial V}{\partial S}\right)_p
\end{aligned}$$

#### F with T and V independent

Start with First Law, be we want $dS$ and $dp$ (not $dV$)

$$\begin{aligned}
TdS &= dE + pdV \\
dE &= TdS - pdV + SdT + Vdp\\
dE &= TdS - d(pV) + Vdp\\
dE + d(pV) &= TdS + Vdp\\
d(E+pV) &= TdS + Vdp\\
\\
H &= E + pV \equiv \text{ Enthalpy}\\
\\
dH &= TdS + Vdp\\
H &= H(S,p)\\
\\
dH &= \left(\frac{\partial H}{\partial S}\right)_p dS + \left(\frac{\partial H}{\partial p}\right)_S dp \\
\\
\left(\frac{\partial H}{\partial S}\right)_p &= T \\
\left(\frac{\partial H}{\partial p}\right)_S &= V
\end{aligned}$$

Order of second partial derivative doesn't matter -> Clauriet's Theorem

$$\begin{aligned}
\left(\frac{\partial }{\partial p}\right)_S \left(\frac{\partial}{\partial S}\right)_p H &= \frac{\partial^2 H}{\partial p\partial S} \\
\frac{\partial^2 H}{\partial p\partial S} &= \frac{\partial^2 H}{\partial S\partial p}\\
\frac{\partial^2 H}{\partial S\partial p} &= \left(\frac{\partial }{\partial S}\right)_p \left(\frac{\partial}{\partial p}\right)_S H
\end{aligned}$$

We can use this to rewrite:

$$\begin{aligned}
\left(\frac{\partial }{\partial p}\right)_S T &= \left(\frac{\partial T}{\partial p}\right)_S \\
\left(\frac{\partial }{\partial S}\right)_p V &= \left(\frac{\partial p}{\partial S}\right)_p \\
\\
\left(\frac{\partial T}{\partial p}\right)_S &= \left(\frac{\partial V}{\partial S}\right)_p
\end{aligned}$$

### SWBQ

We've found the relations for:

- $S,p$
- $S,V$

What about:

- $T,V$?
