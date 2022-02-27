---
title: Homework 4
subtitle: AEC 353, W2022
author: Thomas Knudson
date: Monday, February 7, 2022
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usepackage{fancyhdr}
    \usepackage{float}
    \usepackage{subcaption}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{AEC 353, W2022}
    \fancyhead[CO,CE]{HW4}
    \fancyhead[LO,LE]{Knudson}
---

# Prompt

A homeowner faces the risk of property damage from a severe tropical storm. The home is valued at $200,000. If a severe storm occurs, the homeowner expects that damage will result in a $50,000 from flood damage.

The homeowner’s utility from monetary payoffs is given by $U(x)=\ln{(10x)}$. $\ln{}$ is the natural log function and $x$ is a monetary amount.

> Suppose that private flood insurance is available that will fully cover the flood damage. The annual cost of the policy is $5,000. If there is a chance of flood damage from a storm each year, will the homeowner will be willing to buy the policy? Justify your response with supporting calculations and, optionally, one or more economics graphs.

# Set-up/Symbolic Solution

We can determine if the homeowner will purchase flood insurance by comparing the expected utility against their utility of the difference between the expected property value and the risk premium. Recall that the expectation of a quantity, $\langle A \rangle$ is given by sum of the products for each outcome's probability, $\mathcal{P_i}$, and the outcome's value, $A_i$.

Therefore, the expected value for this situation is represented as the weighted average of both the value of the property after flood damage and the value of the property if no tropical storm occurs. Similarly, we can quanity the expected utility of the homeowner by using their utility function, $U(x)$, and the same process.

If the homeowner's utility, for the property minus the cost of insurance, is greater than the expected utility, then a (rational) homeowner would purchase the insurance. Therefore, by varying the probabilty of flood damage, we can quantify the homeowner's decisions by evaluating the converse: 

$$\begin{cases}\label{eqn:condition}
EU > U(W-C) &\Rightarrow \qquad \text{no insurance}\\
EU \leq U(W-C) &\Rightarrow \qquad \text{insurance}\end{cases}$$

With this simplifed view, we can equally evaluate the three given scenarios for a homeowner facing a purchase cost $C=\$5,000$, property value $W=\$200,000$, and a reduction by $L=\$50,000$. We can immediately calculate our constant threshold of $U(W-C)$ as

\begin{align}
U(W-C) &= \ln{\bigg(10(W-C)\bigg)}\\
&= \ln{\bigg(10(\$195,000)\bigg)}\\
&= 14.4833. \label{eqn:UThreshold}
\end{align}

\pagebreak

## Situation 1

> 5% chance of flood damage from a storm each year.

Since we really only need to find the expected utility, this calculation is straightforward:

\begin{align}
EU &= \langle U \rangle = \sum_{i}{\mathcal{P}_i U_i}\\
&= 0.05 U(W-L)+ (1-0.05) U(W)\\
&= 0.05\ln{(10\times\$150,000)} + 0.95\ln{(10\times\$200,000)}\\
&= 14.4943. \label{eqn:Sit1EU}
\end{align}

Now we just compare the results from Equation \ref{eqn:Sit1EU} to Equation \ref{eqn:UThreshold}:

\begin{align}
EU &\stackrel{?}{>} U(W-C) \\
14.4943 &> 14.4833
\end{align}

Therefore, with the only a 5% chance of $50,000 flood damage from a storm a year, the homeowner will not purchase the insurance at these rates.

## Situation 2

> 10% chance of flood damage from a storm each year.

Again, only calculating the expected utility:

\begin{align}
EU &= \langle U \rangle = \sum_{i}{\mathcal{P}_i U_i}\\
&= 0.1 U(W-L)+ (1-0.1) U(W)\\
&= 0.1\ln{(10\times\$150,000)} + 0.9\ln{(10\times\$200,000)}\\
&= 14.4799. \label{eqn:Sit2EU}
\end{align}

Now we just compare the results from Equation \ref{eqn:Sit1EU} to Equation \ref{eqn:UThreshold}:

\begin{align}
EU &\stackrel{?}{>} U(W-C) \\
14.4799 &\leq 14.4833
\end{align}

With a %5 increase to the flood damage, the homeowner would purchase the insurance to ensure maximum utility from the property.

## Subsidized

The maximum value the homeowner would be willing to pay for insurance will be the risk premimum, $P$, such that the utility of the difference of the expected value of the property and the insurance's cost will exactly equal the expected utility. Given $U(x)=\ln{10(x)}$, we set $x$ to $EV-P$ and $U$ to $\langle U \rangle$ while solving for $P$:

\begin{align}
U(EV-P) &= \langle U \rangle\\
\ln{\bigg(10(\langle V\rangle - P)\bigg)} &= \langle U \rangle\\
10(\langle V\rangle - P) &= e^{\langle U \rangle}\\
10\cdot P &= 10\langle V\rangle - e^{\langle U \rangle}\\
P &= \langle V\rangle - \frac{\$ e^{\langle U \rangle}}{10} \label{eqn:Risk}
\end{align}

Then, we substitute in Situation 1's given values and find that

\begin{align}
P &= \bigg(0.05 (W-L)+ (1-0.05)W\bigg) - \frac{\$ e^{14.4943}}{10}\\
&= \bigg(0.05 (\$150,000)+ 0.95(\$200,000)\bigg) - \frac{\$ e^{14.4943}}{10}\\
&= \$197,500 - \frac{\$ e^{14.4943}}{10}\\
&= \$356.229 = \$356.23
\end{align}

Assuming no other special behaviour from the subsidized plan, the homeowner is only willing to pay a total of $356.23 before the utility of the insurance will be less favorable than not particpating.
