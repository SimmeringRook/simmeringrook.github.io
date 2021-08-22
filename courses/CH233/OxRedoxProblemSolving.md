# Identifying Ox-Redox Reactions, Oxidizing Agents, and Reducing Agents

<br />

<!-- panels:start -->

<!-- div:title-panel -->

## Rules of Assigning Oxidation States

<!-- div:left-panel -->

Order of precedence is the order in which they are stated:

1. The oxidation state of a free element is 0.
2. The oxidation state of a (monoatomic) ion is its charge.
3. The sum of oxidation states for a substance is equal to its ionic charge ($0$ if neutral).
4. In compounds, metals always have positive states:
    - Group 1A are $+1$
    - Group 2A are $+2$
5. In compounds, nonmetals (respecting the same hierarchy):
    1. $F = -1$
    2. $H = +1$
    3. $O = -2$
    4. Group 7A $=-1$
    4. Group 6A $=-2$
    4. Group 5A $=-3$

<!-- div:right-panel -->

>[!ATTENTION|style:flat|label:The third rule must always be followed]
> For elements that don't have their states described above, their states can be inferred from the application of the rules above and by resolving the other elements in the compound first.

<br />

>[!TIP] For simplicity, one can note that Rules 1 and 2 can be summarized inside Rule 3.

<!-- div:title-panel -->

## Oxidation and Reduction Review

First, recall what definitions for the terminology:

| Term | Definition |
| - | --- |
| Oxidation | The loss of electrons |
| Reduction | The gain of electrons |
| Oxidizing Agent | The substance that causes the oxidation of another substance. This substance will be reduced in the reaction: it gains electrons from the other substance. |
| Reducing Agent | The substance that causes the reduction of another substance. This substance will be oxidized in the reaction: it losses electrons to the other substance. |

Now, let's consider the simple Redox reaction that creates table salt ($NaCl$).

$$2Na(s) + Cl_2(g) \rightarrow 2 NaCl(s)$$

Beginning with the left side of the equation, we note that both reactants present are either free elements ($Cl_2$) or neutral monoatomic ions ($Na$):

$$\underbrace{2Na(s)}_{0}, \qquad \underbrace{Cl_2(g)}_{0}$$

After the reaction occurs, we note that the resulting product is neutral in charge (not an ion). By rule 3, the compound has an oxidation state of $0$. Then, applying rule 4 (the next applicable rule), $Na$ is a Group 1A metal in a compound and therefor has an oxidation state of $+1$.

$$\underbrace{NaCl}_{0} = \underbrace{Na}_{+1} + \underbrace{Cl}_{-1}$$

We can then rewrite the chemical equation with these oxidation states noted and verify we have a logical statement (each side is equal to the other):

$$\underbrace{2Na(s)}_{0}+\underbrace{Cl_2(g)}_{0}\rightarrow 2 \underbrace{\underbrace{Na}_{+1}\underbrace{Cl}_{-1}}_{0}(s)$$

> The combination of 2 moles of solid Sodium with 1 mole of Chlorine gas causes an Oxidation-Reduction reaction. Sodium gives up an electron to Chlorine when forming a bond. The sodium is oxidized while the chlorine is reduced to create sodium chloride.

| Chemical Equation | Oxidized | Reduced | Oxidizing Agent | Reducing Agent |
| -- | - | - | - | - |
| $$2Na(s) + Cl_2(g) \rightarrow 2 NaCl(s)$$ | $$\underbrace{Na}_{0\rightarrow\ +1}$$ | $$\underbrace{Cl}_{0\rightarrow\ -1}$$ | $$\underbrace{Cl}_{\text{gains electron}}$$ | $$\underbrace{Na}_{\text{looses electron}}$$ |

# Balancing Redox Equations

In summary, these problems are just applying the Law of Mass Conservation alongside conservation of charge.

>[!NOTE|label:Recall] Conservation of mass (Law of Mass Conservation) is just balancing a chemical equation. E.g. balance the following: $$Na + Cl_2 \rightarrow NaCl$$ Note two chlorines present on the left hand side; at a minimum, we need 2 $NaCl$ to ensure all chlorine atoms are accounted for. $$Na+Cl_2\rightarrow 2NaCl$$ Now that chlorine is resolved, we have too few $Na$ on the reactant side; increasing the amount of $Na$ accordingly, we obtain the balanced chemical equation (all atoms are accounted for): $$2Na + Cl_2 \rightarrow 2NaCl$$

The process of ensuring charge conservation is typically given in most of these situations (see example above and the previous section). Examining Redox of compounds inside aqueous solutions adds a complication: $H_2O(\ell)$ can disassociate into protons, $H^+$ (or Hydronium ions as $H_3O^+$, depending on preference), and Hydrogen Oxide, $OH^-$.

## General Algorithm

If it can be solved by inspection, do it: There is a unique solution for minimized whole number coefficients. Verify mass and charged are conserved.

If the solution is non-obvious:

1. Assign [oxidation states](#rules-of-assigning-oxidation-states).
    - Classify what is being oxidized and what is being reduced.
2. Split the chemical equation into two separate equations.
3. Balance each equation, individually, with respect to mass:
    1. Balance everything not $H$ or $O$.
    2. Balance $O$ by adding $H_2O (\ell)$.
    3. Balance $H$ by adding $H^+$ (or $H_3O^+$, if desired)
    4. If **basic** solution: Neutralize the $H^+$ charge by adding $OH^-$ to both sides of equation.
4. Balance (each equation) with respect to charge by adding $e^-$.
5. Scale each equation such that the number of $e^-$ in each equation are equal.
6. Recombine equations and simplify.
    - Verify.

<!-- div:title-panel -->

### Acidic Solution Example

>[!NOTE|style:flat|label:Problem Statement|iconVisibility:hidden] Given the following reaction, ensure that it is balanced. $$H^+ (aq) + Cr(s) \rightarrow H_2 (g) + Cr^{2+} (aq)$$

<!-- div:title-panel -->

>[!NOTE|style:flat|label:Step 0|iconVisibility:hidden]

<!-- div:left-panel -->

First, we notice that solid Chromium is reacting with Hydronium ions contained in an aqueous solution. Recalling that an aqueous solution with large concentrations of $H^+$ is acidic (see pH in the Acid & Base Problem Solving set), we can omit Step 3.4 of our algorithm.

<!-- div:right-panel -->

>[!TIP] If not immediately clear from the problem statement, this step serves as a clue for more complex problem statements; E.g., the reactants and products are described by name (and not equation) and possibly done so that the pH or pOH of the aqueous solution needs to be determined before balancing of the equation can be completed.

<!-- div:title-panel -->

>[!NOTE|style:flat|label:Step 1|iconVisibility:hidden] Assign [oxidation states](#rules-of-assigning-oxidation-states).

<br />

<!-- div:left-panel -->

| Substance | Oxidation State | Reasoning |
| - | - | -- |
| $$H^+$$ | $$+1$$ | Rule 2: charge of ion is $1+$ |
| $$Cr$$ | $$0$$ | Rule 1: free element |
| $$H_2$$ | $$0$$ | Rule 3: Neutral compound |
| $$Cr^{2+}$$ | $$+2$$ | Rule 2: charge of ion is $2+$ |

<!-- div:right-panel -->

Since the hydrogen decreases in oxidation states, it is reduced during the reaction from $H^+ (aq)$ to $H_2 (g)$. Similarly, Chromium increases in oxidation states, which corresponds to being oxidized in the transition from $Cr(s)$ to $Cr^{2+} (aq)$.

<!-- div:title-panel -->

<br />

>[!NOTE|style:flat|label:Step 2|iconVisibility:hidden] Classify and Split the chemical equation into two separate equations.

<br />

<!-- div:left-panel -->

| Oxidation Equation | Oxidized | Reducing Agent |
| --- | --- | --- |
| $$Cr(s) \rightarrow Cr^{2+} (aq)$$ | $$\underbrace{Cr (s)}_{0}\rightarrow\underbrace{Cr^{2+} (aq)}_{+2}$$ |  $$\underbrace{Cr(s)}_{\text{looses electrons}}$$ |

<!-- div:right-panel -->

| Reduction Equation | Reduced | Oxidizing Agent |
| --- | --- | --- |
| $$H^+(aq) \rightarrow H_2 (g)$$ | $$\underbrace{H^+(aq)}_{+1}\rightarrow\underbrace{H_2 (g)}_{0}$$ |  $$\underbrace{H^+(aq)}_{\text{looses electrons}}$$ |

<!-- div:title-panel -->

>[!TIP|label:Aside] We can see that through mass conservation, the simple solution is to increase the coefficient on the Hydronium Ion to 2. $$2H^+ (aq) + Cr(s) \rightarrow H_2 (g) + Cr^{2+} (aq)$$ This would then balance the charges on each side of the reaction (as well as total oxidation states). Let's continue the example explicitly in order to verify this prediction.

<br />

>[!NOTE|style:flat|label:Step 3|iconVisibility:hidden] Balance each equation, individually, with respect to mass:
    1. Balance everything not $H$ or $O$.
    2. Balance $O$ by adding $H_2O (\ell)$.
    3. Balance $H$ by adding $H^+$ (or $H_3O^+$, if desired)

<br />

<!-- div:left-panel -->

**Oxidation**

$$Cr(s) \rightarrow Cr^{2+} (aq)$$

We have equal amounts of Chromium on both sides and there's no $O$ or $H$ to balance.

<!-- div:right-panel -->

**Reduction**

$$H^+(aq) \rightarrow H_2 (g)$$

We only have $H$ present, so we balance by increasing the number of $H^+$ on the left such that the total amount of hydrogen is equal on both sides of the reduction reaction.

$$2H^+(aq) \rightarrow H_2 (g)$$

<!-- div:title-panel -->

>[!NOTE|style:flat|label:Step 4|iconVisibility:hidden] Balance (each equation) with respect to charge by adding $e^-$.

<!-- div:left-panel -->

**Oxidation**

$$\underbrace{Cr (s)}_{0}\rightarrow\underbrace{Cr^{2+} (aq)}_{+2}$$

Since the left-hand side of the oxidation reaction is neutral, we need to make the right-hand side neutral by adding 2 $e^-$:

$$ 0 = 2 + x \rightarrow x=-2$$

$$\underbrace{Cr (s)}_{0}\rightarrow\underbrace{Cr^{2+} (aq)+ 2e^-}_{+2-2=0}$$

<!-- div:right-panel -->

**Reduction**

$$\underbrace{2H^+(aq)}_{2(+1)}\rightarrow\underbrace{H_2 (g)}_{0}$$

This is the opposite case of the oxidation reaction: we have 2 positive charges on the reactant side of the reduction reaction and a neutral charge on the products; therefore, we need to add $2e^-$ to the reactant side to balance charges.

$$ x + 2 = 0 \rightarrow x=-2$$

$$\underbrace{2H^+(aq) + 2e^-}_{2(+1)-2=0}\rightarrow\underbrace{H_2 (g)}_{0}$$

<!-- panels:end -->

>[!NOTE|style:flat|label:Step 5|iconVisibility:hidden] Scale each equation such that the number of $e^-$ in each equation are equal.

By inspection, we can see that there are equal numbers of electrons, on each side, in each equation:

$$Cr (s) \rightarrow Cr^{2+} (aq)+ 2e^-, \qquad 2H^+(aq) + 2e^-\rightarrow H_2 (g)$$


>[!NOTE|style:flat|label:Step 6|iconVisibility:hidden] Recombine equations and simplify. Verify.

$$\begin{aligned}
Cr (s) &\rightarrow Cr^{2+} (aq)+ 2e^-\\
2H^+(aq) + 2e^- &\rightarrow H_2 (g)\\
\hline
2H^+(aq) + Cr(s) &\rightarrow Cr^{2+} (aq) + H_2 (g)
\end{aligned}$$
