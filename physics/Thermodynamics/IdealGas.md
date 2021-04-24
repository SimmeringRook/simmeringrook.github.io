# Ideal Gas (Thermodynamics)

?> **Definition:**

## Equation of State

### General

$$pV=nRT$$

### Undergoing Adiabatic Process

$$pV^\gamma = constant \qquad\text{or}\qquad V^{\gamma-1}T = constant$$

## Properties

- The internal energy of an ideal gas only depends on its Temperature

### Proof of $E\propto T$

For an ideal gas, we can take the following statement:
$E=E(T,V)$ and show that $E$ only depends on $T$: $E=E(T)$ which implies
$$\left(\frac{\partial E}{ \partial V}\right)_T \equiv 0$$

First, we take the total derivative:

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
dE &= dE(T,V) \\
&=\left(\frac{\partial E}{ \partial T}\right)_V dT + \left(\frac{\partial E}{ \partial V}\right)_T dV
\end{aligned}$$

Then also consider the First Law of Thermo:

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
TdS &= dE + pdV \\
dS &= \frac{1}{T}dE + \frac{p}{T}dV
\end{aligned}$$

Note that because we can write the differential of entropy as a total derivative, this tells us that $dS$ is an exact differential, which means we can write:
$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
S &= S(E,V) \\
 &= \left(\frac{\partial S}{\partial E}\right)_V dE + \left(\frac{\partial S}{\partial V}\right)_E dV
\end{aligned}$$

Because there is only one way to write the total derivative, we know the coefficients for the differentials are equal to the partial derivatives stated above:

$$\frac{1}{T} = \left(\frac{\partial S}{\partial E}\right)_V$$

- Which is the definition of temperature in macroscopic Thermodynamics

$$\frac{p}{T} = \left(\frac{\partial S}{\partial V}\right)_E$$

- Which is the definition of temperature without knowing Microscopic details

Also recall that with mixed partial derivatives, the order of operations doesn't matter (Clauriet's Theorem):

$$\frac{\partial ^2 S}{\partial V \partial E} = \frac{\partial ^2 S}{\partial E \partial V}$$

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
\mpder{S}{V}{E} &= \wrap{\pder{}{V}}{E} \wrap{\pder{S}{E}}{V} \\
\mpder{S}{E}{V} &= \wrap{\pder{}{E}}{V} \wrap{\pder{S}{V}}{E}
\end{aligned}$$

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
dS &= \frac{1}{T}dE + \frac{p}{T}dV \\
dE &= \wrap{\pder{E}{T}}{V} dT + \wrap{\pder{E}{V}}{T} dV \\
\\
dS &= \frac{1}{T} \left( \wrap{\pder{E}{T}}{V} dT + \wrap{\pder{E}{V}}{T} dV \right) + \frac{p}{T}dV \\
&= \frac{1}{T}\wrap{\pder{E}{T}}{V} dT + \left(\frac{1}{T}\wrap{\pder{E}{V}}{T} + \frac{p}{T}\right)dV \\
\\
dS &= \wrap{\pder{S}{T}}{V} dT + \wrap{\pder{S}{V}}{T} dV \\
\\
\\
\wrap{\pder{S}{T}}{V} &= \frac{1}{T} \wrap{\pder{E}{T}}{V} \\
\wrap{\pder{S}{V}}{T} &= \left( \frac{1}{T} \wrap{\pder{E}{V}}{T} + \frac{p}{T} \right)
\end{aligned}$$

Then:

$$\newcommand\dbar{đ}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{{\partial}^2 #1}{{\partial} #2 {\partial} #3}}
\begin{aligned}
\wrap{\pder{}{V}}{T} \wrap{\pder{S}{T}}{V} &\equiv \wrap{\pder{}{T}}{V} \wrap{\pder{S}{V}}{T} \\
\frac{1}{T} \wrap{\mpder{E}{V}{T}}{} &= \wrap{\pder{}{T}}{V} \left[\frac{1}{T}\wrap{\pder{E}{V}}{T} + \frac{p}{T}\right] \\
\frac{1}{T} \wrap{\mpder{E}{V}{T}}{} &= \frac{1}{T} \wrap{\mpder{E}{V}{T}}{} + \frac{1}{T^2} \wrap{\pder{E}{V}}{T} \\
0 &= \frac{1}{T^2} \wrap{\pder{E}{V}}{T}
\end{aligned}$$

### Entropy

Ideal gas is sometimes referred to as a "perfect gas" (gas molecules do not interact to have any potential energy; all energy comes from kinetic)

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

---

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

---

## External Resources

- *Fundamentals of Statistical and Thermal Physics* by F. Reif
- *Thermodynamics: A complete undergraduate course* by Andrew F. Steane
- *An Introduction to Thermal Physics* by Daniel V. Schroeder

---

## Internal Links
### Courses

- [PH423: Paradigms: Energy and Entropy ](/courses/PH423.md)
- [PH541: Capstone: Statistical Mechanics](/courses/PH541.md)
