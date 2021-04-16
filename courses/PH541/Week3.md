# PH 541: Statistical Mechanics, Week 3

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

Won't be asked to derive the Maxwell Relations again, but we may want to use them to answer questions asked that either don't provide an easy or straightforward avenue.

Objectives:
 - Specific Heats
  - heat capacity at constant volume
    - $\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
    C_V = \wrap{\pder{Q}{T}}{V} = \wrap{\frac{TdS}{dT}}{V} = T\wrap{\pder{S}{T}}{V}$
    - Alternatively: $\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}C_V = \wrap{\pder{dE+pdV}{T}}{V} = \wrap{\pder{E}{T}}{V}$
    - Molar specific heat: $c_V = \frac{C_V}{n}$
  - heat capacity at constant pressure
    - $\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}C_p = \wrap{\frac{dQ}{dT}}{p} = T\wrap{\pder{S}{T}}{p}$
    - Alternatively:
  - $C_p - C_V = VT \frac{\alpha^2}{\kappa}$ where:
    - $\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\alpha\equiv \frac{1}{V}\wrap{\pder{V}{T}}{p}$ is the Volume coefficient of Expansion
    - $\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\kappa\equiv -\frac{1}{V}\wrap{\pder{V}{p}}{T}$ is Isothermal compressibility
 - Determine homogeneous substance undergoes a state change from macroscopic state A to macroscopic state B
  - $\Delta S=S(T,V) - S(T_0, V_0)$
  - $\Delta E=E(T,V) - E(T_0, V_0)$

#### Show stuff

Starting with First Law:
$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
dQ = TdS &= TdS(T,p) \\
 &= T \wrap{ \wrap{ \pder{S}{T}}{p} dT + \wrap{\pder{S}{p}}{T} dp}{} \\
 &= C_p dT + T \wrap{ \pder{S}{p} }{T} dp
\end{aligned}$$

Now let us expand the total differential of pressure:

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
&= C_p dT + T \wrap{\pder{S}{p} }{T} \wrap{ \wrap{\pder{p}{V}}{T} dV + \wrap{\pder{p}{T}}{V} dT }{} \\
dQ &= \wrap{C_p + T \wrap{\pder{S}{p} }{T} \wrap{\pder{p}{T}}{V} }{} dT + T \wrap{\pder{S}{p} }{T}\wrap{\pder{p}{V}}{T} dV
\end{aligned}$$

Now we can Calculate the change in heat at fixed volume: $dV = 0$

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
dQ &= \wrap{ C_p + T \wrap{\pder{S}{p} }{T} \wrap{\pder{p}{T}}{V} }{}dT \\
\\
\wrap{\pder{Q}{T}}{V} &= C_p + T \wrap{\pder{S}{p} }{T} \wrap{\pder{p}{T}}{V} \\
\\
\wrap{\pder{Q}{T}}{V} & \text{ is really just the specific heat at constant volume} \\
\\
C_V &= C_p + T \wrap{\pder{S}{p} }{T} \wrap{\pder{p}{T}}{V} \\
\\
C_p - C_V &= -T \wrap{\pder{p}{T}}{V}\wrap{\pder{S}{p} }{T}
\end{aligned}$$

?> Recall with Maxwell: $$\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\wrap{\pder{S}{p}}{T} = -\wrap{\pder{V}{T}}{p} $$

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
C_p - C_V &= -T \wrap{\pder{p}{T}}{V}\wrap{-\pder{V}{T}}{p} \\
&= T \wrap{\pder{p}{T}}{V}\wrap{\pder{V}{T}}{p}
\end{aligned}$$

?> Recall the coefficients we introduced at the start of class: $$\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\alpha\equiv \frac{1}{V}\wrap{\pder{V}{T}}{p}$$ and $$\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\kappa\equiv -\frac{1}{V}\wrap{\pder{V}{p}}{T}$$

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
C_p - C_V &= T \wrap{\pder{p}{T}}{V}\wrap{\pder{V}{T}}{p} \\
  &= T \wrap{ \frac{\wrap{\pder{V}{T}}{p}} {\wrap{\pder{V}{p}}{T}}}{} \wrap{V\alpha}{p} \\
  &= T \wrap{ \frac{-V\alpha}{-V\kappa} \frac{V\alpha}{p} }{} \\
  C_p - C_V &= TV \frac{\alpha^2}{\kappa}
\end{aligned}$$

#### SWBQ

Use the following relationship to show that for an ideal gas $C_p - C_V = nR$:

$$C_p - C_V = TV \frac{\alpha^2}{\kappa}$$

Work:

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
\alpha & \equiv \frac{1}{V}\wrap{\pder{V}{T}}{p} \\
  &= \frac{1}{V}\wrap{\frac{nR}{p}}{} \\
  &= \frac{nR}{Vp} \\
  \\
\kappa & \equiv -\frac{1}{V}\wrap{\pder{V}{p}}{T} \\
  &= -\frac{-nRT}{V p^2} \\
  \\
C_p - C_V &= TV \frac{\alpha^2}{\kappa} \\
&= TV \frac{\left(\frac{nR}{Vp}\right)^2}{-\frac{-nRT}{V p^2}} \\
&= nR TV \frac{nR}{V^2 p^2}\frac{V p^2}{nRT} \\
&= nR
\end{aligned}$$

Page 171-175

### Day 2

Entropy and Energy

!> **Objective:** We want to develop an approach or formula to calculate:
- $S(T,V)$ from $S(T_0, V_0)$
- $E(T,V)$ from $E(T_0, V_0)$


Entropy is a bit more simple: we just want to calculate $\Delta S$.

$$\Delta S = S(T,V) - S(T_0, V_0)$$


Recall that if we say Entropy is a function of $T$ and $V$, then we can write:

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\begin{aligned}
dS(T,V) &= \wrap{\pder{S}{T}}{V} dT + \wrap{\pder{S}{V}}{T} dV \\
  &= \frac{1}{T}\cdot T\wrap{\pder{S}{T}}{V} dT + \wrap{\pder{p}{T}}{V} dV \\
  &= \wrap{\frac{1}{T} C_V}{} dT + \wrap{\pder{p}{T}}{V} dV
\end{aligned}$$

Note that $C_V$ is a function of temperature itself, so if we were to integrate the above expression, we'd need to know what $C_V$ is, as the more longform way of writing this: $C_V (T,V)$.

So, now we want/need to calculate $C_V (T,V)$, we state the following: If we know
  - The equation of state
  - $C_V(T,V_0)$

We can claim that we can calculate $C_V (T,V)$.

#### Proof of finding Specific Heat at Constant Volume

First, we want to know:
  - how $C_V$ varies in response to change in volume (at fixed T):

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\begin{aligned}
\wrap{\pder{C_V}{V}}{T} &= \wrap{\pder{}{V}}{T} C_V \\
&= \wrap{\pder{}{V}}{T} \left[ T \wrap{\pder{S}{T}}{V} \right] \\
&= T \wrap{\pder{}{V}}{T} \wrap{\pder{S}{T}}{V} \\
&= T \wrap{\pder{}{T}}{V} \wrap{\pder{S}{V}}{T} \\
&= T \wrap{\pder{}{T}}{V} \wrap{\pder{p}{T}}{V} \\
&= T \wrap{\pdersq{p}{T}}{V}
\end{aligned}$$

Where this is $0$ for an ideal gas.

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\begin{aligned}
C_V(T,V) - C_V(T,V_0) &= \int_{V_0}^{V}{T \wrap{\pdersq{p}{T}}{V'} dV'}\\
&= \wrap{\pder{}{V}}{T} \left[ T \wrap{\pder{S}{T}}{V} \right] \\
&= T \wrap{\pder{}{V}}{T} \wrap{\pder{S}{T}}{V} \\
&= T \wrap{\pder{}{T}}{V} \wrap{\pder{S}{V}}{T} \\
&= T \wrap{\pder{}{T}}{V} \wrap{\pder{p}{T}}{V} \\
&= T \wrap{\pdersq{p}{T}}{V}
\end{aligned}$$

----

Now that we have a method for finding $C_V (T,V)$, we can return to Entropy.

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\begin{aligned}
dS(T,V) &= \wrap{\frac{1}{T} C_V}{} dT + \wrap{\pder{p}{T}}{V} dV \\
\\
\Delta S &= S(T,V) - S(T_0, V_0) \\
\Delta S &= \int_{T_0}^{T}{\frac{1}{T} C_V (T,V) dT} + \int_{V_0}^{V}{\wrap{\pder{p}{T}}{V'} dV'}
\end{aligned}$$

$S$ being a state function should be independent of path. So, we break this up into two paths: we transition into a state $(T_0, V)$ and then to $(T,V)$.

### Day 3

Similarly to entropy, we can do this for internal energy:

$$
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\begin{aligned}
\Delta E &= E(T,V) - E(T_0,V_0) \\
\\
dE &= \bar{d}Q-pdV \\
&= TdS - pdV \\
&= T \left[ \wrap{\pder{S}{T}}{V} dT + \wrap{\pder{S}{V}}{T} dV \right] - pdV\\
&= T \wrap{\pder{S}{T}}{V} dT + \left[ T\wrap{\pder{S}{V}}{T}-p\right] dV \\
&= C_V dT + \left[ T\wrap{\pder{p}{T}}{V} - p\right] dV\\
\end{aligned}
$$

Applying the lesson learned from last lecture, we can find $\Delta E$ using path independence to evaluate these integrals:

$$
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\begin{aligned}
\Delta E &= E(T,V) - E(T_0,V_0) \\
\\
\int_{E_0}^{E}{dE'} &= \int_{T_0}^{T}{C_V dT} + \int_{V_0}^{V}{\wrap{T\wrap{\pder{p}{T}}{V} - p}{}dV}
\end{aligned}
$$

#### SWBQ

Example from page 173,
Consider a Van der Waals gas that follows the equation of state:
$$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\wrap{p+\frac{a}{V^2}}{}\wrap{\frac{V}{n}-b}{}= RT$$

- Calculate $\wrap{\pder{p}{T}}{V}$
- Show: $\wrap{\pder{C_V}{V}}{T} = 0$
- determine the molar entropy change:
  - $\Delta s = s(T,V) - s(T_0, V_0)$
- determine the molar energy change:
  - $\Delta e = e(T,V) - e(T_0, V_0)$
