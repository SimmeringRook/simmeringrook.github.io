---
title: Homework 3
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Wednesday, October 13, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{HW3}
    \fancyhead[LO,LE]{Knudson}
---

# Question 1

> Recall that $\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}\text{Tr}(A)=\sum_{n}{A_{nn}}=\sum_{n}{\bra{\varphi_n}A\ket{\varphi_n}}$, where $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\big\{\ket{\varphi_n}\big\}$ is a complete orthonormal basis. Using bra-ket algebra, prove the following relations:

## Part A

> $$\text{Tr}(ABC) = \text{Tr}(CAB) = \text{Tr}(BCA)$$ where $A$, $B$, $C$ are operators.

Recall that we can express the trace of an operator a few different ways:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\Tr}[1]{\text{Tr}\left(#1\right)}
\begin{aligned}
\Tr{A} &= \sum_{n}{A_{nn}}\\
&= \sum_{n}{\bra{\varphi_n}A\ket{\varphi_n}}\\
&= \sum_{i,j}{\bra{\varphi_i}A\ket{\varphi_j}}\\
&= \sum_{i,j}{a_{ij}\delta_{i,j}}
\end{aligned}$$

We can then proceed to demonstrate that the trace of $AB$ is equivalent to the trace of $BA$ to lay the framework for showing that the trace of cyclic permutations (of the product of $ABC$) are equivalent.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\Tr}[1]{\text{Tr}\left(#1\right)}
\begin{aligned}
\Tr{AB} &= \sum_{n}{(AB)_{nn}}\\
&= \sum_{n}{\bra{\varphi_n}AB\ket{\varphi_n}}\\
&= \sum_{i}{\bra{\varphi_i}A\left(\sum_{j}{\ket{\varphi_j}\bra{\varphi_j}}\right)B\ket{\varphi_i}} \\
&= \sum_{i,j}{\bra{\varphi_i}A\ket{\varphi_j}\bra{\varphi_j}B\ket{\varphi_i}} \\
&= \sum_{i,j}{a_{ij}b_{ji}\delta_{i,j}} = \sum_{j,i}{b_{ji}a_{ij}\delta_{j,i}} \\
&= \sum_{j,i}{\bra{\varphi_j}B\ket{\varphi_i}\bra{\varphi_i}A\ket{\varphi_j}} \\
&= \sum_{j}{\bra{\varphi_j}B\left(\sum_{i}{\ket{\varphi_i}\bra{\varphi_i}}\right)A\ket{\varphi_j}} \\
&= \sum_{j}{\bra{\varphi_j}BA\ket{\varphi_j}} \\
&= \sum_{n}{(BA)_{nn}}\\
&= \Tr{BA}
\end{aligned}$$

This two operator example was completely without assuming any properties about $A$ and $B$ other than they could be represented in the $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\big\{\ket{\varphi_n}\big\}$. Only cyclic permutations are possible with this method as the insertion and removal of the completeness relation is only possible if the indices match. This was not an issue with just two operators, but with three, we will see that there arises the opportunity to mismatch sets of indices and that without knowing if any of the operators commute, only $\newcommand{\Tr}[1]{\text{Tr}\left(#1\right)}\Tr{ABC}=\Tr{BCA}=\Tr{CAB}$ can be used.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\Tr}[1]{\text{Tr}\left(#1\right)}
\begin{aligned}
\Tr{ABC} &= \sum_{n}{(ABC)_{nn}}\\
&= \sum_{n}{\bra{\varphi_n}ABC\ket{\varphi_n}}\\
&= \sum_{i}{\bra{\varphi_i}A\left(\sum_{j}{\ket{\varphi_j}\bra{\varphi_j}}\right)B\left(\sum_{k}{\ket{\varphi_k}\bra{\varphi_k}}\right)C\ket{\varphi_i}} \\
&= \sum_{i,j,k}{\bra{\varphi_i}A\ket{\varphi_j}\bra{\varphi_j}B\ket{\varphi_k}\bra{\varphi_k}C\ket{\varphi_i}} \\
&= \sum_{i,j,k}{a_{ij}b_{jk}c_{ki}\delta_{i,j,k}} = \sum_{j,k,i}{b_{ji}c_{ki}a_{ij}\delta_{j,k,i}} = \sum_{k,i,j}{c_{ki}a_{ij}b_{ji}\delta_{k,i,j}}\\
&= \Tr{BCA} = \Tr{CAB}
\end{aligned}$$

Where this fails is if we try to create $Tr(ACB)$:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\Tr}[1]{\text{Tr}\left(#1\right)}
\begin{aligned}
\Tr{ABC} &= \sum_{i,j,k}{\bra{\varphi_i}A\ket{\varphi_j}\bra{\varphi_j}B\ket{\varphi_k}\bra{\varphi_k}C\ket{\varphi_i}} \\
&= \sum_{i,j,k}{\bra{\varphi_i}A\ket{\varphi_j}\bra{\varphi_k}C\ket{\varphi_i}\bra{\varphi_j}B\ket{\varphi_k}}
\end{aligned}$$

Fix:

$$\sum_{j,k}{\ket{\varphi_j}\bra{\varphi_k}} \neq \mathbb{I}$$

And so, we cannot resolve the reordering in this method, as we're unable to collapse the outer product back to the Identity operator: The only way we can equate $Tr(ABC) = Tr(ACB)$ is to require $[B,C]=0$ and then use commutivity in the step prior to introducing the completeness relations.

## Part B

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\text{Tr}\bigg(\ket{\psi}\bra{\varphi}\bigg) = \braket{\varphi}{\psi}
$$ where $\left|\varphi\right\rangle$, $\left|\psi\right\rangle$ are state vectors.


\pagebreak

# Question 2

>

\pagebreak

# Question 3

>
