# Solving Thermochemistry Problems

## Change in Heat, Work, and Energy

### Conceptual

The conceptual version of these problems revolve around answering where energy flows during a process. These boil down to recognizing the presence or absence of a few key words:

| Heat | Common Descriptors |
| --- | --- |
| $\Delta Q > 0$ | absorbs, heated, warms |
| $\Delta Q < 0$ | emits, cools, releases |
| $\Delta Q = 0$ | insulated |

?> **Note**: Pay special care to the wording around *insulated*. Depending on the problem set up, the intent can be to treat it as a perfect insulator which allows no heat transfer to itself or the surroundings. While rare, sometimes the implication is that the *insulated container* can allow heat transfer with its contents and self, but does not permit heat transfer with itself and the surroundings: E.g., processes examined inside Constant Pressure Calorimeters.

| Work | Common Descriptors |
| --- | --- |
| $\Delta W > 0$ | expands |
| $\Delta W < 0$ | contracts |
| $\Delta W = 0$ | isobaric, isochoric |

| System | Interpretation |
| - | ----- |
| closed | Contents are constant; e.g. the number of particles or moles of the substance cannot change. |
| open | Contents are not necessarily constant. E.g., liquid water doesn't change, but a gas will diffuse into the surroundings |
| external | The surroundings most likely have an impact on the process: E.g., ".. the external atmospheric pressure .." will effect the amount of net work done by a process. |

### Calculation

The calculation version of these problems center on the (integrated) thermodynamic identity:

$$\Delta E = \Delta W + \Delta Q$$

Recall that through energy conservation, the following equation tells us that the total energy of the entire space must be constant:

$$\Delta E_{total} = \Delta E_{surroundings} + \Delta E_{system} = 0$$

When these problems focus on the change in energy of the system, two of types of energy will be specified and the third unknown. This ultimately is just a Thermodynamic coating on the algebriac statement: $x = y + z$.

| Goal | Given | Relation |
| -- | - | - |
| The heat absorbed/emitted by the system | $\Delta E$, $\Delta W$ | $\Delta Q = \Delta E - \Delta W$ |
| The work done on/by the system | $\Delta E$, $\Delta Q$ | $\Delta W = \Delta E - \Delta Q$ |
| The energy change of the system | $\Delta W$, $\Delta Q$ | $\Delta E = \Delta W + \Delta Q$ |

## Heat Capacity

In a broad sense, the heat capacity of a substance (element or compound), tells you how much energy is required to change its temperature by one degree. The higher the number, the more resistant to temperature change:

- Water has a relatively high specific heat capacity at $4.18\ J(g\ \,^{\circ}C)^{-1}$. This is why we used "water baths" in chemistry experiments for bring/keeping a system to/at a specified temperature: the water will easily accept and smooth out any temperature differences without drastic changes.
- The better a substance is at being an insulator, the bigger the value of its specific heat capacity. A *perfect* insulator would have a value of $\infty$, as in it would take an *infinite* amount of energy to change its temperature by just *one* degree.

The equation that fundamental describes these processes is sometimes colloquially referred to as "q equals m cat" or the "m cat equation":

$$Q = m C \Delta T$$

### Conceptual

There really are only two flavors for the conceptual questions for the heat equation:

Two (or more substances) are stated in the problem statement with some general inequality between their heat capacities: "..the heat capacity of Substance A is greater than that of Substance B". Where the two types of questions differ is in the amount of information provided.

Some information:

- Given Information: $C_A > C_B$, $m_A \propto m_B$, $T_i$ is the same for both substances, (sometimes $Q$).
- Prompt:
  - Choose which statement describes the correct outcome
  - Explain what happens when both substances are put into contact with each other.
  - Explain what happens when both have the same amount of heat transferred to/from them.

More information:

- Given Information: $C_A > C_B$, $m_A \propto m_B$, $Q$
- Prompt:
  - Choose which statement describes the correct outcome
  - Explain what happens when both substances are put into contact with each other.
  - Explain what happens when both have the same amount of heat transferred to/from them.

In version 1, the approach is to just consider the inequality between the specific heats: the smaller specific heat, $C$, will have a bigger $\Delta T$ than the others. If we think of $C$ as a measure of the substance's resistance to temperature change, this should intutively make sense.

If more specifics are given, then more specific statements about the outcome may be possible:

>**Statement:** The specifc heat of Substance A is twice that of Substance B. Assuming equal masses of Substance A and Substance B start at the same initial temperature of $0^{\circ}C$ and are placed apart on an insulated surface. The two masses are left to be in contact with the room air for a significant period of time.

>**Solution:** Both substances will absorb the same amount of heat: exposed to room temperature air for the same amount of time. From this, we can set both equations equal to eachother. $$\begin{aligned} Q_A = m_A C_A (T_{f_A} - T_i), &\quad Q_B = m_B C_B (T_{f_B} - T_i) \\
m_A C_A (T_{f_A} - T_i) &= m_B C_B (T_{f_B} - T_i)
\end{aligned}$$ And then we can substitute in the relations that we were given, namely: $m_A = m_B$ and $C_A = 2C_B$. Then we can simplify until we have a more clear relation between the final temperatures. $$\begin{aligned}
m_A C_A (T_{f_A} - T_i) &= m_B C_B (T_{f_B} - T_i) \\
m_B 2C_B (T_{f_A} - T_i) &= m_B C_B (T_{f_B} - T_i) \\
2(T_{f_A} - T_i) &= (T_{f_B} - T_i)\\
2T_{f_A} &= T_{f_B} + T_i \\
T_{f_A} &= \frac{1}{2}\bigg(T_{f_B} + T_i \bigg)
\end{aligned}$$ Conclusion: Substance A's final temperature will be less than Substance B's.

While the above example borders is essentially a calculation version of the conceptual prompt, it is worth noting in detail as the omission of one or two bits of information can drastically alter the possible conclusions. Consider two variations of the same general problem statement:

- $Q$ is the same for each substance, $C_A = 2C_B$, and $m_A \neq m_B$
- $Q$ is the same for each substance, $C_A > C_B$, and $m_A \propto m_B$

However, we now remove the that both substances start at the same initial temperature.

What can we conclude now?

Surprisingly little: Even with the specific proportionality between the masses in the second version or the exact inequality between specific heats won't help. Without the initial temperatures being given (or the proportionality between them), we can only make a general statement with specific caveats.

The best conclusion that can be made about the finial temperatures of Substance A versus Substance B is "it depends". Here's a few examples of why its not clear cut:

- Substance A starts at a one degree less than room temperature while Substance B starts at two degrees less than room temperature. If $Q$ is the same, it becomes very important just how much mass of Substance A and B are present and the relationship between their specific heats.
  - Even if $C_A > C_B$, if there's a proportionally small mass of $A$ compared to $B$, it can end at a higher final temperature.
  - If the masses are the same, then we know $B$ will end at a higher final temperature than $A$.
- Substance B could have a lot less mass than Substance A and start at a very low relative initial temperature.
  - If all we know is that $C_A > C_B$, we can't really say anything we certainty.
  - If we know the proportionality between $C_A$ and $C_B$, we can give general intervals where $B$ or $A$ has the higher final temperature.

At the end, even with conceptual questions, its important to realize how much information you have versus how much you don't.

### Calculation

For questions involving only one substance present, everything is given except one variable and these questions are just algebraic manipulations to find the requested quantity.

$$ Q = m C \Delta T$$

| Goal | Given | Relation |
| -- | - | - |
| The heat absorbed/emitted by the process | $m$, $C$, $\Delta T$ | $$Q = m C \Delta T$$ |
| The specific heat of the substance | $Q$, $m$, $\Delta T$ | $$C = \frac{Q}{m\Delta T}$$ |
| The finial temperature of the substance | $Q$, $m$, $C$, $T_i$ | $$T_f = \frac{Q}{mC}+T_i$$ |

These can be expanded slightly by giving either the molar mass or the concentration of solution in place of mass.

$$\mathcal{M} = \frac{mass}{\#\ of\ mols} = \frac{m}{n}, \qquad M = \frac{mols}{liter} = \frac{n}{V}$$

For questions involving two substances, we use Conservation of Energy and this formulation of heat to answer questions about either or both substances (process is assumed to occur at constant volume $W = \pm p\Delta V = 0$).

$$\begin{aligned}
\Delta E_{sys} &= \Delta E_{A} + \Delta E_{B} = 0\\
\Delta E_{A} &= -\Delta E_{B} \\
Q_A &= - Q_B \\
m_A C_A (T_{f_A} - T_i) &= - m_B C_B (T_{f_B} - T_i)
\end{aligned}$$

| Goal | Given | Relation |
| --- | --- | --- |
| The finial temperature of the substances | $Q_A = -Q_B$, $m_A$, $m_B$, $C_A$, $C_B$, $T_{i_A}$, $T_{i_B}$ | $$T_f = \frac{m_A C_A T_{i_A} + m_B C_B T_{i_B}}{m_A C_A + m_B C_B}$$ |
