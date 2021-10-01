---
title: Worksheet 5
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Friday, October 1, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[LO,LE]{Knudson}
---

# Question 1

> Consider unitary operators $A$, $B$, and $C$. Is their product a unitary operator? Show.

Recall that unitary operators are classified by their inverse being the adjoint of itself: $U^{-1}=U^\dagger$. We can then use this to show that the product of unitary operators is itself unitary:

$$\begin{aligned}
(ABC)(ABC)^{\dagger} &= I \\
(ABC)(C^\dagger B^\dagger A^\dagger) &= I \\
(ABC)(C^{-1} B^{-1} A^{-1}) &= I \\
I &= I
\end{aligned}$$

# Question 2

> Consider Hermitian operators $A$ and $B$. Is is known that their product is also Hermitian, what does this imply about the "hermicitivity" of the commutator of $A$ and $B$?

Similar to Question 1, let us consider the product of the operators:

$$(AB)^{\dagger} = B^{\dagger} A^{\dagger}$$

And using the definition of Hermitian operators, we can simplify the right-hand side of this statement:

$$B^{\dagger} A^{\dagger} = BA$$

Let's now investigate the commutator of $A$ and $B$:

$$\begin{aligned}
[A,B] &= AB - BA\\
&= AB - (B^{\dagger} A^{\dagger})\\
&= AB - (AB)^{\dagger}\\
&= AB - AB \\
&= 0
\end{aligned}$$

Therefore, we can conclude that if the product of two Hermitian operators is itself Hermitian, then both operators commute with each other.
