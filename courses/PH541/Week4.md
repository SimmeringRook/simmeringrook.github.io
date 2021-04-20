# PH 541: Statistical Mechanics, Week 4

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

Reading assignment:
- Pages 47-61 in Reif.
- Chapter 2.1 - 2.4
- This will provide a brief introduction to Statistical Mechanics

Today is the final lecture on macroscopic thermodynamics.

Free expansion and Throttling Processes
- Page 175 - 181 in Reif

#### Joule effect

> You can increase the temperature of a solution by doing work or heat transfer.

Consider some gas that is initially in the left-hand side of a rigid and thermally isolated container. We don't know what type of gas it is (no assumptions like ideal gas). If we instantaneously remove the plug, the gas moves into the vacuum on the right-hand side of the container.

?> How does the temperature change? Do we expect to see a temperature change as the gas expands to fill the container?

- There is no work done during this process: the gas cannot do work on the vacuum.
- There is no heat exchange as the container is thermally isolated.

Therefore, we conclude that $dE=0$.

But is the temperature unchanged?
- For an ideal gas:
  - There is no interaction between gas molecules
    - the potential between molecules is so weak, all the internal energy is purely determined by the kinetic energy
  - internal energy is proportional to temperature, so if $dE = 0$, $dT = 0$
- For a real gas:
  - with a non-weak potential interaction, the expansion will decrease the potential energy
  - Because $dE=0$, the kinetic energy must also decrease to conserve energy
  - therefore, the temperature of the gas will decrease

Joule coefficient:
$$\alpha_J \equiv \wrap{\pder{T}{V}}{E}

$$
dE(T,V) = 0
\wrap{\pder{E}{T}}{V} dT + \wrap{\pder{E}{V}}{T} dV = 0
$$

Using the cyclic chain rule:

$$
\alpha_J = \wrap{\pder{T}{V}}{E} = ... = - \frac{\wrap{\pder{E}{V}}{T}}{\wrap{\pder{E}{T}}{V}}
= - \frac{1}{C_V}\left[T\wrap{\pder{p}{T}}{V}-p\right]
$$

If we know the heat capacity and the equation of state, we should be able to calculate the change in temperature due to the change in volume during this free expansion.

For a real gas, we can write the equation of state (for one mole of gas) as a power series expansion:

$$pV = RT \left[1+\frac{B_2}{V}+\frac{B_3}{V^2}+...\right]$$

$B_i$ is the ith Viral Coefficient.

At low density, we only need to expand to the second term:

$$pV = RT\wrap{1+\frac{B_2}{V}}{}$$

#### Joule-Thomson Process

Consider a thermally insulated pipe. Somewhere along the pipe is a porous plug which acts as a constriction. Inside the plug, we have a constant stream of gas, that flows from the left to the right.
The gas pressure on the left is $p_1$ with temperature $T_1$. After the plug, the pressure is $p_2$ with temperature $T_2$.

Does this process always cause $T_2<T_1$?

> An equivalent model is to use two pistons on either side of a value. The gas on the left has initial values of $p_1$ $V_1$ with the piston full retracted. As the piston on the left forces the gas through the value, we ultimately end with all the gas on the right with values of $p_2$ and $V_2$. There is no heat transfer during this process, so we conclude $\dbar Q =0 \Rightarrow \dbar Q = dE +pdV$. Therefore, the change in internal energy must be equal to the work done by the system. We then need to account for the system working on the gas and that leads us to the following statement: $$\Delta E = (E_2 - E_1) = (p_2 V_2 - p_1 V_1) = 0$$ $$(E_2 + p_2 V_2) - (E_1 + p_1 V_1) = 0$$ $$(E_2 + p_2 V_2) = (E_1 + p_1 V_1)$$

Note that this also corresponds to [enthalpy](/physics/Enthalpy.md), so we can conclude during the Joule-Thomson process that Enthalpy is conserved.

The Joule-Thomson coefficient is defined as:

$$\alpha_{JH} = \wrap{\pder{T}{P}}{H}$$

$$
dH = dh(p,T) = 0

\wrap{\pder{H}{p}}{T} dp + \wrap{\pder{H}{T}}{P} dT = 0

\wrap{\pder{T}{P}}{H} \Rightarrow - \frac{\wrap{\pder{H}{p}}{T}}{\wrap{\pder{H}{T}}{p}}

\wrap{\pder{H}{T}}{p}
 = \wrap{\pder{E+pV}{T}}{p} = \left(\frac{\Delta E + p\Delta V + V\Delta p}{\Delta T}\right)_p

\Delta p = 0 for constant pressure;

= \left(\frac{\Delta Q}{\Delta T}\right)_p = C_p

--

dH = TdS + Vdp

dS = \frac{1}{T}dH - \frac{V}{T} dp
= \frac{1}{T} \left[\wrap{\pder{H}{T}}{p} dT + \wrap{\pder{H}{p}}{T} dp \right] - \frac{V}{T}dp
= \frac{1}{T}\wrap{\pder{H}{T}}{p} dT + \left[\frac{1}{T}\wrap{\pder{H}{p}}{T} - \frac{V}{T} \right] dp
= C_p dT = \wrap{\pder{S}{p}}{T} dp

$$

Aside:

$$
\wrap{\pder{}{p}}{T}\wrap{\pder{S}{T}}{p} = \wrap{\pder{}{T}}{p}\wrap{\pder{S}{p}}{T} \Rightarrow \wrap{\pder{}{p}}{T} \left[\frac{1}{T}\wrap{\pder{H}{T}}{p}\right]
= \wrap{\pder{}{T}}{p} \left[ \frac{1}{T} \left( \wrap{\pder{H}{p}}{T} - \frac{V}{T} \right) \right]

\wrap{\pder{H}{p}}{T} = V - T \wrap{\pder{V}{T}}{p}
$$

Now we should be able to write the Joule-Thomson coefficient:

$$
\alpha_{JH} = \wrap{\pder{T}{p}}{H} = \frac{1}{C_p}\left[T\wrap{\pder{V}{T}}{p} - V\right]
$$


### Day 2

### Day 3
