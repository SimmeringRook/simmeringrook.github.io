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
$$\alpha_J \equiv \wrap{\pder{T}{V}}{E}$$

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

Start of Statistical Mechanics

Four ingredients of Statistical Mechanics:

1. Specification of the state of the system
$$\Psi=\psi(q_1, q_2,...,q_f)$$

?>**Example 1:**
?>A system that contains only one particle but is fixed in location in space, but has Spin-1/2; How do we describe the state of the system?
?>
?>$\qquad$ The spin quantum number: $m$. The state of the system is either $m=\frac{1}{2}$ or $m=-\frac{1}{2}$.

?>**Example 2:**
?>A system that contains $N$ particles that are fixed in location in space, but each has a Spin-1/2; How do we describe the state of the system?
?>
?>$\qquad$ We need the spin quantum number $m$ but for each particle, so a specific state is comprised of the information: $$(m_1, m_2, ..., m_N)$$

2. Statistical Ensemble

We are not necessarily concerned of an instance of the ensemble.

The macroscopic state should be distributed.

?>**Example:**
?>A system with three fixed particles; each particle has a spin-1/2, each particle also has a magnetic moment $\mu$ along the $z$-axis. The entire system is placed in an external magnetic field $H$.

| state index r | Quantum number | Total magnetic moment | Total Energy |
| --- | --- | --- | --- |
| 1 | +++ | 3$\mu$ | -3$\mu H$|
| 2 | ++- | $\mu$ | -$\mu H$|
| 3 | +-+ | $\mu$ | -$\mu H$|
| 4 | -++ | $\mu$ | -$\mu H$|
| 5 | +-- | -$\mu$ | $\mu H$|
| 6 | --+ | -$\mu$ | $\mu H$|
| 7 | -+- | -$\mu$ | $\mu H$|
| 8 | --- | -3$\mu$ | 3$\mu H$|

With the macroscopic constraint $E_{total} = -\mu H$, the states accessible to the system are:
$$(++-),\ (+-+),\ (-++)$$

### Day 3

Macroscopic state is specified by: $V$, $n$, $T$.

There can by many micro states for one specific macro state.

3. Basic Postulates

!> Statistical Weight: $\Omega(E,V,N,\alpha)$
The number of micro states corresponding to a macro state that is specified by $V$, $N$, $\alpha$, and having energy $E$ in a small interval $E$ to $E+\delta E$.

$$\alpha$$
Represents a set of parameters that represent when the system is not in equilibrium.

#### First Postulate

Each micro state is compatible with the macroscopic state. It is reasonable to make the assumption that each micro state that is compatible with the macroscopic constraint is equally likely to occur.

!> **For an isolated system**, All microscopic states that are compatible with the macroscopic constraints (i.e., $E$, $V$, $N$) are equally likely to occur.

$P$ -> Probability

$P(E, V, N, \alpha)\propto \Omega(E,V,N,\alpha)$


#### Second Postulate

!> Equilibrium corresponds to the value of $\alpha$ for which $\Omega(E,V,N,\alpha)$ reaches its maximum.

#### Boltzmann's Definition of Entropy

!> (Stat Mech) **Entropy** is defined as $S(E,V,N,\alpha) = k\ln{\Omega(E,V,N,\alpha)}$


Note, if $\Omega$ is at a maximum, that implies $S$ is at a maximum as well, when the isolate system is in equilibrium.

---

Consider a chamber that is separated by a diathermal wall. Call the partition on the left $1$ and the right $2$. Confine the container inside a rigid wall that is thermally insulated. The systems are weakly interacting thermally, but the entire system is insulated from the "outside".

$1$ is specified by $E_1$, $V_1$, $N_1$; $2$ is specified by $E_2$, $V_2$, $N_2$.

The systems will exchange heat and eventually reach thermal equilibrium.

$$E_1 + E_2 = E_{total} = constant$$

$$V_1 + V_2 = V_{total} = constant$$

$$N_1 + N_2 = N_{total} = constant$$

Only heat exchange, no particle exchange.

For example, assume the system starts in some non-equilibrium state. Let system 2 start at a slightly higher temperature and system 1 start at a slightly lower temperature.

Let $S$ be the entropy of the entire system: $S_1 + S_2$. When we reach equilibrium, $S$ will reach its maximum (Second postulate).

$$S(E_1, V_1, N_1, E_2, V_2, N_2)$$

If only $E_1$ changes, how do we determine the maxima? Do the 'first derivative test':

$$\wrap{\pder{S}{E_1}}{V, N, E, V_1, N_1} = 0$$

Recall $S = S_1 + S_2$, so, we obtain:

$$
\wrap{\pder{S}{E_1}}{V, N, E, V_1, N_1} &= \wrap{\pder{S_1}{E_1}}{V_1, N_1} + \wrap{\pder{S_2}{E_2}}{V_2, N_2} \frac{dE_2}{dE_1} \\
0 &= \wrap{\pder{S_1}{E_1}}{V_1, N_1} + \wrap{\pder{S_2}{E_2}}{V_2, N_2} \frac{dE_2}{dE_1}
$$


$$d(E)= d(E_1 + E_2)\\ 0 = dE_1 + dE_2 \\ \frac{dE_2}{dE_1}= -1$$

$$
0 &= \wrap{\pder{S_1}{E_1}}{V_1, N_1} + \wrap{\pder{S_2}{E_2}}{V_2, N_2}(-1)\\
\wrap{\pder{S_2}{E_2}}{V_2, N_2} &= \wrap{\pder{S_1}{E_1}}{V_1, N_1}\\
\frac{1}{T} &= \wrap{\pder{S_2}{E_2}}{V_2, N_2} = \wrap{\pder{S_1}{E_1}}{V_1, N_1}
$$

When the two systems are in equilibrium, they have the same energy. This is how temperature was introduced to microscopic. We can repeat the same process to introduce pressure, we just allow the partition to move. Repeating similar steps, we obtain:

$$P_i = T_i \wrap{\pder{S_i}{V_i}}{E_i, N_i}$$

#### Canonical distribution

The probability of occurrence for a microscopic state is given by:

$$P_r = \frac{\text{# of copies of the system in state r}}{n_0}$$

---

So, we're considering a system that is specified by three macroscopic parameters:

$$A(V, N, T)$$

And let it be in thermal contact with a thermal resivior (heat bath).

We know that $A$ will have many microscopic states. Not all micro states will have the same energy, but they will have the same constant mean energy. Describe the microstates of $A$ by: $1,\ 2,\ 3,\ ...,\ n$. We then order the microstates such that they ordered: $E_1 \leq E_2 \leq ... \leq E_n$.

Under what conditions of equilibrium, we ask what is the probability $P_r$ of finding the system in a particular micro state $r$ with Energy $E_r$
