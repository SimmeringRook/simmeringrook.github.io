# Chapter 9: Thermochemistry

## Heat

$$ q = m\times C \times \Delta T $$

$$\begin{aligned}
q_1 &= m_1 C_1 (T_f - T_1)\\
q_2 &= m_2 C_2 (T_f - T_2)\\
\\
q_2 &= - q_1 \\
m_2 C_2 (T_f - T_2) &= - m_1 C_1 (T_f - T_1) \\
T_f (m_2 C_2 + m_1 C_1) &= m_2 C_2 T_2 + m_1 C_1 T_1 \\
T_f &= \frac{m_2 C_2 T_2 + m_1 C_1 T_1}{m_2 C_2 + m_1 C_1}
\end{aligned}$$

## Enthalpy

- $\Delta H$ (for chemical reaction) is the amount of thermal energy transfer during the reaction (at constant pressure - isobaric process)
    - $\Delta H = +$ - endothermic reaction (absorbs heat from surroundings)
    - $\Delta H = -$ - exothermic reaction (gives heat to surroundings)

Hess's Law:

$$\Delta H_{rxn} = \sum_{i}^{products}{n_i\Delta H_i} - \sum_{j}^{reactants}{n_j \Delta H_j}$$

Puzzle problems:

  - Multiply chemical equation by a factor $\rightarrow$ scale $\Delta H$ for that equation by the same factor.
    - $2(A+2B\rightarrow C) \rightarrow 2(\Delta H)$
  - Change order of chemical equation $\rightarrow$ change sign of $\Delta H$
    - $(A+2B\rightarrow C \Rightarrow C\rightarrow A + 2B) \rightarrow -(\Delta H)$
  - If equation can be expressed as the sum of a series of steps, $\Delta H_{rxn}$ is the sum of the $\Delta H$'s

Bond Energies - Table 9.3 Page 390

### Table of Specific Heat

| Element | Specific Heat |
| --- | --- |
| $Pb$, Lead | $0.128$ |
| $Au$, Gold | $0.128$ |
| $Ag$, Silver | $0.235$ |
| $Cu$, Copper | $0.385$ |
| $Fe$, Iron | $0.449$ |
| $Al$, Aluminum | $0.903$ |

| Compound | Specific Heat |
| --- | --- |
| $C_2H_6O$, Ethanol | $2.42$ |
| $H_2O$, Water | $4.18$ |

| Material | Specific Heat |
| --- | --- |
| Glass (Pyrex) | $0.75$ |
| Granite | $0.79$ |
| Sand | $0.84$ |

\pagebreak

# Chapter 10: Ideal Gas Law

$$pV = nRT$$

## Common versions:

- $p_i V_i = p_f V_f$
  - $n=T=$ constant
- $\frac{p_i}{T_i} = \frac{p_f}{T_f}$
  - $n=V=$ constant
- $\frac{n_i}{V_i} = \frac{n_f}{V_f}$
  - $p=T=$ constant
- $\frac{V_i}{T_i} = \frac{V_f}{T_f}$
  - $n=p=$ constant

Solved for Molar Mass:

$$\begin{aligned}
\mathcal{M} = \frac{m}{n} &\rightarrow n = \frac{m}{\mathcal{M}}\\
pV &= nRT\\
\frac{1}{n} &= \frac{RT}{pV} \\
\mathcal{M} &= \frac{mRT}{pV}
\end{aligned}$$

Solved for Density:

$$\rho = \frac{molar\ mass}{molar\ volume} \frac{p\mathcal{M}}{RT}$$

!> Molar Volume: $$V=\frac{(1\ mol)R(273\ K)}{1\ atm}$$ The volume occupied by 1 mol of a gas at STP.

## Partial Pressures

$$P_{tot} = P_0 + ... + P_n$$

$$P_0 = \chi_0 P_{tot}$$

Vapor Pressure - Table 10.3 page 438

## Temperature and Energy

$$KE=\frac{1}{2}mv^2$$

$$v = \sqrt{\frac{3RT}{\mathcal{M}}}$$

## Real Gases

$$\left(p + a\left(\frac{n}{V}\right)^2 \right) \times \left(V - nb\right) = nRT$$

Table 10.4 - Van der Waals Constants

> Example: $$2Al + 3CL_2 \rightarrow 2AlCl_3$$ Given a mass of $Al$, what is the volume of $Cl_2 (g)$ to completely react? $$\frac{m_{Al}}{\mathcal{M}_{Al}}\cdot \frac{3\ Cl_2}{2\ Al} = n_{Cl_2}$$ $$V_{Cl_2} = \frac{n_{Cl_2}\cdot R \cdot T}{p}$$

\pagebreak

# Chapter 13

Freezing point Depression / Boiling Point Elevation:

$$\Delta T_{f/b} = i\times m \times K_{f/b}$$

> Example: Find molar mass of unknown of solute to change freezing/boiling point by $\Delta T$.$$\begin{aligned}
m &= \frac{\Delta T}{i\times K}\\
\frac{n}{m_{solvent}} &= \frac{\Delta T}{i\times K}\\
\frac{m_{solute}}{\mathcal{M}} &= \frac{m_{solvent}\times\Delta T}{i\times K}\\
\\
\mathcal{M} &= \frac{i\times K\times m_{solute}}{m_{solvent}\times\Delta T}
\end{aligned}$$

Osmotic Pressure:

$$\Pi = MRT,\quad M=\frac{n}{V}$$

$$\mathcal{M} = \frac{mRT}{V\Pi}$$

\pagebreak

# Chapter 14

$$rate = -\frac{1}{a}\frac{\Delta [A]}{\Delta t} = ... = + \frac{1}{c} \frac{\Delta [C]}{\Delta t}$$

- $\frac{\Delta [A]}{\Delta t} = a\cdot rate$
- $\frac{\Delta [C]}{\Delta t} = \frac{c}{a} \frac{\Delta [A]}{\Delta t}$

## Reaction Orders

| Order | dependence on [A] | Rate Law | Integrated |  Half-life |
| --- | --- | --- | --- | --- |
| 0 | independent | $rate=k$ | $[A]_t = -kt + [A]_0$ | $t_{1/2} = \frac{[A]_0}{2k}$ |
| 1 | proportional | $rate = k [A]$ | $\ln{\frac{[A]_t}{[A]_0}} = -kt$ | $t_{1/2} = \frac{\ln{2}}{k}$ |
| 2 | proportional | $rate = k [A]^2$ | $\frac{1}{[A]_t} = kt + \frac{1}{[A]_0}$ | $t_{1/2} = \frac{1}{k[A]_0}$ |

$$ k = \frac{rate}{[A]^n [B]^m}$$

## Arrhenius

$$\ln{k}= -\frac{E_a}{RT} +\ln{A}$$

\pagebreak

# Chapter 15

| | | |
| --- | --- | --- |
| $K << 1$ | reactants | left |
| $K \approx 1$ | neither | center |
| $K >> 1$ | products | right |

Hess's Law like properties:

- reverse chemical equation $\rightarrow$ $K^{-1}$
- scale by factor $n$ $\rightarrow$ raise by $n$: $K^{n}$
- Add equations $\rightarrow$ multiply $K$s together

## Le Chatelier's Principle:

Concentration

- Increase
  - [reactants] $(Q<K)$ $\rightarrow$ towards products
  - [products] $(Q>K)$ $\rightarrow$ towards reactants
- Decrease
  - [reactants] $(Q>K)$ $\rightarrow$ towards reactants
  - [products] $(Q<K)$ $\rightarrow$ towards products

Volume

- Decrease $\rightarrow$ towards fewer moles
- Increase $\rightarrow$ towards greater moles
- Unchanged
  - inert gas
  - equal moles on both sides of Chem Eq.

Temp

- exothermic (heat is product)
  - $+T\rightarrow$ towards reactants
  - $-T\rightarrow$ towards products
- endothermic (heat is reactant)
  - $-T\rightarrow$ towards products
  - $+T\rightarrow$ towards reactants
