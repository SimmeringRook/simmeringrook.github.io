---
title: Homework 4
subtitle: AEC 351, W2022
author: Thomas Knudson
date: February 22, 2022
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
    \fancyhead[RO,RE]{AEC 351, W2022}
    \fancyhead[CO,CE]{HW4}
    \fancyhead[LO,LE]{Knudson}
---

# Question 2

## Part A

> Suppose the owner approaches you and asks for your advice on how to best manage the forest land for timber production. What formula would you apply to choose the best rotation length?

As is the typical case for maximizing good production, we should consider the intersection of marginal benefit and marginal cost to find the optimum rotation length for the owner's forest. This is accomplished by finding where the net present value (difference between discounted revenue and costs) is a maximium.

The marginal benefit corresponds to the (time) derivative of the forest's growth rate, $W(t)$, scaled by the value of $ per board foot. That is, the instantaneous rate of change of value as a function of time, $\Delta V(t)$, is given by

\begin{equation}\label{eqn:MB}
\Delta V(t) = p\dot{W}(t).
\end{equation}

The marignal cost for the owner is then given by the difference between the value of harvesting at time $t$, 

\begin{equation}\label{eqn:V}
V(t)=pW(t),
\end{equation}

the cost of harvesting, $C$, summed with the value of the land cleared of trees,

\begin{equation}\label{eqn:pi}
\pi(t) = \frac{pW(t)-C}{e^{rT}-1},
\end{equation}

all scalled by the discount rate $r$:

\begin{equation}\label{eqn:MC}
r\left(pW(t)-C + \pi(t) \right) = r(pW(t)-C)\left(1+\frac{1}{e^{rt}-1}\right).
\end{equation}

Therefore, the owner can find the best rotation length by equating Equation \ref{eqn:MB} to Equation \ref{eqn:MC}:

\begin{equation}\label{eqn:OptimalHarvest}
p\dot{W}(T) = r(pW(T)-C)\left(1+\frac{1}{e^{rT}-1}\right).
\end{equation}

To the owner, this condition represents not having left any money 'on the table' by harvesting too early and not having lost money by harvesting too soon.

$$\ $$

## Part B

> What rotation length would you recommend for this forest land?

We can find the optimal rotation length $T$ by either solving Equation \ref{eqn:OptimalHarvest} for $t=T$ algebraically, or by plotting both marginal functions (Equations \ref{eqn:MB} and \ref{eqn:MC}) and finding their intersection graphically. If $W(T)$ could be factored out of every term on the right-hand side of Equation \ref{eqn:MC}, the algebraic solution would be fairly straight-forward. In this case, I think its much simpler to plot both functions and use tools to find the numeric solution. Considering that $T$ should be some period of time greater than $0$, we can use Mathematica to plot both functions over some arbritrary interval $[1,100]$:

$$\ $$

```Mathematica
a = -34.01; b = -20.65; d = 9.51; p = 0.1; HarvestCost = 84; r = 0.03;
W[t_] := Exp[a/t^2 + b/t + d]
LandValue[t_] := (p*W[t] - HarvestCost)/(Exp[r*t] - 1)
Plot[{p*W'[t], r*(p*W[t] - HarvestCost + LandValue[t])}, {T, 1, 100}, PlotLabels -> Automatic]
```

$$\ $$

Where we relabled $\pi(t)$, Equation \ref{eqn:pi}, to `LandValue` and $C$ to `HarvestCost` as both $\pi$ and $C$ are reserved names in Mathematica.

\begin{figure}[H]
  \centering
  \includegraphics{351_HW4_Intersection.png}
  \caption{A plot showing the intersection between the marginal benefit and marginal cost, Equations \ref{eqn:MB} and \ref{eqn:MC}, respectively.}
  \label{fig:OptimalHarvest}
\end{figure}

Then we can use Mathematica to find $T$ such that Equation \ref{eqn:OptimalHarvest} is satisfied by providing it a guess to start its search:

```Mathematica
FindRoot[p*W'[T] == r*(p*W[T] - HarvestCost + LandValue[T]), {T, 20}]
```

From Figure \ref{fig:OptimalHarvest}, we can see the marginal benefit (blue) function intersects the marginal cost (orange) function around $t=20$. Mathematica provides the value of $$T=21.36348709304875$$ for the optimal rotation length, which is also the point where $\pi(t)$ has its maximum value as shown in Figure \ref{fig:LandValue}.

\begin{figure}[H]
  \centering
  \includegraphics{351_HW4_Pi.png}
  \caption{A plot of Equation \ref{eqn:pi}.}
  \label{fig:LandValue}
\end{figure}

## Part C

> Suppose that, in order to promote conservation, a harvest tax is imposed that increases the fixed costs of harvest by close to $50\%$ (so now $C=\$150$ per acre). Given this change, how would you advise the land owner to adjust the rotation length for this forest land?

The effect of varying $C$ only causes a horizontal translation to the marginal cost function. Since the marginal benefit function is unchanged, this simply increases the value of $T$ for the intersection between both functions as subtracting a bigger number corresponds to a graphical shift to the right.

\begin{figure}[H]
  \centering
  \includegraphics{351_HW4_Intersection_Shifted.png}
  \caption{The plot after changing $C$ to $\$150$, showing that the intersection between the marginal benefit and marginal cost shifted to the right.}
  \label{fig:OptimalHarvest2}
\end{figure}

$$T_{after} = 23.564322784210454$$

$\therefore$ The owner should increase their rotation to maximize revenue.