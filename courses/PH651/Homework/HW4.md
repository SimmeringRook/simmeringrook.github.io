---
title: Homework 4
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Wednesday, October 20, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{HW4}
    \fancyhead[LO,LE]{Knudson}
---

\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}

# Question 1

> Consider a physical system whose Hamiltonian and initial state are given by $$H=\epsilon_0 \begin{pmatrix} 1 & -1 & 0 \\ -1 & 1 & 0 \\ 0 & 0 & -1 \end{pmatrix}, \qquad \ket{\psi} \dot{=} \frac{1}{\sqrt{6}}\begin{pmatrix} 1 \\ 1 \\ 2\end{pmatrix}$$ where $\epsilon_0$ has the dimensions of energy.

Note that $H$ is block diagonal, so we know that the eigenvalue of $-\epsilon_0$ has the eigenvector of: $$\ket{-\epsilon_0}\dot{=}\begin{pmatrix} 0 \\ 0 \\ 1\end{pmatrix}$$

Next, we just need to diagonalize the subspace:

$$\begin{aligned}
\det{(H_{block}-\lambda \mathbb{I})} &= 0 \\
(1-\lambda)^2 - (-1)^2 &= 0 \\
1 + \lambda(\lambda - 2) -1 &= 0 \\
\lambda &= 0, \quad 2
\end{aligned}$$

This block diagonal is a common $2\times 2$ that we deal with a lot, this time we'll show the work explicitly for finding the eigenvectors:

$$\begin{aligned}
\begin{pmatrix} 1-\lambda & -1 \\ -1 & 1-\lambda \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} &= \begin{pmatrix} 0 \\ 0 \end{pmatrix} \\
(1-\lambda)x -y = 0, &\quad -x + (1-\lambda)y = 0 \\
y &= (1-\lambda)x \\
\\
\text{for }\lambda = 0, \quad \text{choose } x = 1 &\Rightarrow y=1\\
\text{for }\lambda = 2, \quad \text{choose } x = 1 &\Rightarrow y=-1
\end{aligned}$$

Our final two possible eigenvalues and their corresponding (normalized) states:

$$\begin{aligned}
0\epsilon_0 &\mapsto \ket{0\epsilon_0}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \\ 0\end{pmatrix} \\
2\epsilon_0 &\mapsto \ket{2\epsilon_0}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \\ 0\end{pmatrix}
\end{aligned}$$

## Part A

> What values will we obtain when measuring the energy and with what probabilities?

Let's decompose $\ket{\psi}$ into multiples of these energy states:

$$\begin{aligned}
\ket{\psi} &= \braket{-\epsilon_0}{\psi}\ket{-\epsilon_0} + \braket{0\epsilon_0}{\psi}\ket{0\epsilon_0} + \braket{2\epsilon_0}{\psi}\ket{2\epsilon_0} \\
&= \frac{2}{\sqrt{6}}\ket{-\epsilon_0} + \frac{2}{\sqrt{12}}\ket{0\epsilon_0} + 0\ket{2\epsilon_0}\\
&= \frac{\sqrt{2}}{\sqrt{3}}\ket{-\epsilon_0} + \frac{1}{\sqrt{3}}\ket{0\epsilon_0}\\
\end{aligned}$$

Since none of the eigenvalues are degenerate, we can just read off the norm square of the coefficients:

$$\begin{aligned}
\mathcal{P}_{-\epsilon_0} &= \frac{2}{3}\\
\mathcal{P}_{0\epsilon_0} &= \frac{1}{3}\\
\mathcal{P}_{2\epsilon_0} &= 0
\end{aligned}$$

When measuring the energy corresponding to $\ket{\psi}$, the only two possible values are $-\epsilon_0$ with a probability of $2/3$ and $0\epsilon_0$ with a probability of $1/3$.

## Part B

> Calculate the expectation value of the Hamiltonian in both ways: Using the results of Part A and by using the definition of an expectation value and given matrix $H$ and the initial state.

$$\left\langle H \right\rangle = -\epsilon_0 \frac{2}{3} +  0 \frac{1}{3} + 0(2\epsilon_0) = -\frac{2}{3}\epsilon_0$$

$$\frac{\bra{\psi}H\ket{\psi}}{\braket{\psi}{\psi}} = \frac{\bra{\psi} H\bigg( \frac{\sqrt{2}}{\sqrt{3}}\ket{-\epsilon_0} + \frac{1}{\sqrt{3}}\ket{0\epsilon_0}\bigg)}{1} = \bra{\psi}\bigg( -\frac{\sqrt{2}}{\sqrt{3}}\epsilon_0\ket{-\epsilon_0} \bigg)= - \frac{2}{3}\epsilon_0$$

\pagebreak

# Question 2

> Consider a system whose Hamiltonian and an operator $A$ are given by the matrices: $$H=\epsilon_0 \begin{pmatrix} 1 & -1 & 0 \\ -1 & 1 & 0 \\ 0 & 0 & -1 \end{pmatrix}, \qquad A \dot{=} a_0\begin{pmatrix} 0 & 4 & 0 \\ 4 & 0 & 1 \\ 0 & 1 & 0 \end{pmatrix}$$

Recall from Question 1, Part A, the eigen values and eigenvectors:

$$\begin{aligned}
-\epsilon_0 &\mapsto \ket{-\epsilon_0}\dot{=}\begin{pmatrix} 0 \\ 0 \\ 1\end{pmatrix} \\
0\epsilon_0 &\mapsto \ket{0\epsilon_0}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \\ 0\end{pmatrix} \\
2\epsilon_0 &\mapsto \ket{2\epsilon_0}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \\ 0\end{pmatrix}
\end{aligned}$$

The observable $A$ has the following eigenvalues and eigenvectors:

$$\begin{aligned}
\det{(A-\lambda \mathbb{I})} &= 0 \\
-\lambda((-\lambda)^2-1) - 4(-4\lambda) &= 0 \\
\lambda(-\lambda^2+17)  &= 0 \\
\lambda &= 0, \quad \pm\sqrt{17}
\end{aligned}$$

$$\begin{aligned}
\begin{pmatrix} -\lambda & 4 & 0 \\ 4 & -\lambda & 1 \\ 0 & 1 & -\lambda \end{pmatrix} \begin{pmatrix} x \\ y \\ z \end{pmatrix} &= \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} \\
-\lambda x + 4y &= 0\\
4x - \lambda y + z &= 0 \\
y -\lambda z &= 0 \\
\\
y &= \frac{\lambda}{4}x \\
y &= \lambda z\\
\\
\text{for }\lambda = 0, \quad \text{choose } x = -1 &\Rightarrow y=0, z=4\\
\text{for }\lambda = \sqrt{17}, \quad \text{choose } x = 4 &\Rightarrow y=\sqrt{17}, z=1\\
\text{for }\lambda = -\sqrt{17}, \quad \text{choose } x = 4 &\Rightarrow y=-\sqrt{17}, z=1
\end{aligned}$$

$$\begin{aligned}
0a_0 &\mapsto \ket{0a_0}\dot{=}\frac{1}{\sqrt{17}}\begin{pmatrix} -1 \\ 0 \\ 4\end{pmatrix} \\
\sqrt{17}a_0 &\mapsto \ket{0\epsilon_0}\dot{=}\frac{1}{\sqrt{34}}\begin{pmatrix} 4 \\ \sqrt{17} \\ 1\end{pmatrix} \\
-\sqrt{17}a_0 &\mapsto \ket{2\epsilon_0}\dot{=}\frac{1}{\sqrt{34}}\begin{pmatrix} 4 \\ -\sqrt{17} \\ 1\end{pmatrix}
\end{aligned}$$

## Part A

> If we measure the energy, what values will we obtain?

Since $H$ has the exact same definition as in Question 1, the three possible energy values we could measure in this system are: $-\epsilon_0$, $0\epsilon_0$, or $2\epsilon_0$.

## Part B

> Suppose that when we measure the energy, we obtain a value of $-\epsilon_0$. Immediately afterwards, we measure $A$. What values will we obtain for $A$ and with what probabilities?

$$\begin{aligned}
H\ket{\psi} &= \ket{-\epsilon_0}\\
A\ket{-\epsilon_0} &= \braket{0a_0}{-\epsilon_0}\ket{0_a0} + \braket{\sqrt{17}a_0}{-\epsilon_0}\ket{\sqrt{17}_a0} + \braket{-\sqrt{17}a_0}{-\epsilon_0}\ket{-\sqrt{17}_a0} \\
&= \frac{4\sqrt{2}}{\sqrt{34}}\ket{0a_0} + \frac{1}{\sqrt{34}}\ket{\sqrt{17}_a0} - \frac{1}{\sqrt{34}}\ket{-\sqrt{17}_a0}\\
\end{aligned}$$

Since none of the eigenvalues are degenerate, we can just read off the norm square of the coefficients. The following are the corresponding probabilities for the possible values of $A$ we could measure:

$$\begin{aligned}
\mathcal{P}_{0a_0} &= \frac{32}{34}\\
\mathcal{P}_{\sqrt{17}a_0} &= \frac{1}{34}\\
\mathcal{P}_{-\sqrt{17}a_0} &= \frac{1}{34}\\
\end{aligned}$$

## Part C

> What is the expectation value of $A$?

$$\left\langle A \right\rangle = 0\cdot \frac{32}{34} +  \frac{1}{34}(-\sqrt{17} + \sqrt{17}) = 0$$

\pagebreak

# Question 3

> Consider a physical system whose state and two observables $A$ and $B$ are represented by: $$\ket{\psi} \dot{=} \frac{1}{6} \begin{pmatrix} 1 \\ 0 \\ 4 \end{pmatrix}, \quad A \dot{=} \frac{1}{\sqrt{2}} \begin{pmatrix} 2 & 0 & 0 \\ 0 & 1 & i \\ 0 & -i & 1 \end{pmatrix}, \quad B \dot{=} \begin{pmatrix} 1 & 0 & 0 \\ 0 & 0 & -i \\ 0 & i & 0 \end{pmatrix}$$

$A$ is block diagonal, and so the two remaining eigenvalues are $\text{Tr}(A)=\sqrt{2}+a_2+a_3=2\sqrt{2}$ and $\det(A)=0$: $a_2=0$ and $a_3=\sqrt{2}$.

$$\begin{aligned}
a=\sqrt{2} &\mapsto \ket{a=\sqrt{2},1}\dot{=}\begin{pmatrix} 1 \\ 0 \\ 0\end{pmatrix} \\
a=0 &\mapsto \ket{a=0}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ 1 \\ i\end{pmatrix} \\
a=\sqrt{2} &\mapsto \ket{a=\sqrt{2},2}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ 1 \\ -i\end{pmatrix}
\end{aligned}$$

$B$ is also block diagonal, and so the two remaining eigenvalues are $\text{Tr}(B)=b_1+b_2+b_3=1$ and $\det(B)=-1$: $b_2=1$ and $b_3=-1$.

$$\begin{aligned}
b=1 &\mapsto \ket{b=1,1}\dot{=}\begin{pmatrix} 1 \\ 0 \\ 0\end{pmatrix} \\
b=1 &\mapsto \ket{b=1,2}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ 1 \\ i\end{pmatrix} \\
b=-1 &\mapsto \ket{b=-1}\dot{=}\frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ 1 \\ -i\end{pmatrix}
\end{aligned}$$

We need to normalize our initial state by multiplying by a factor of $6/\sqrt{17}$:

$$\ket{\psi} \dot{=} \frac{1}{\sqrt{17}} \begin{pmatrix} 1 \\ 0 \\ 4 \end{pmatrix}$$

## Part A

> We first measure $A$ and then $B$. Find the probability of obtaining a value of $0$ for $A$ and a value of $1$ for $B$.

$$\ket{\psi} = \frac{1}{\sqrt{17}} \bigg(\ket{a=\sqrt{2},1} - i\sqrt{8} \ket{a=0} + i\sqrt{8} \ket{a=\sqrt{2},2} \bigg)$$

$$\begin{aligned}
\mathcal{P}_{a=0} &= \lvert\braket{a=0}{\psi}\rvert^2 = \frac{8}{17}\\
\mathcal{P}_{b=1} &= \lvert\braket{b=1,1}{a=0}\rvert^2 + \lvert\braket{b=1,2}{a=0}\rvert^2 \\
&= 1
\end{aligned}$$

$$\frac{8}{17}$$

## Part B

> We first measure $B$ then $A$. Find the probability of obtaining a value of $1$ for $B$ and a value of $0$ for $A$.

$$\ket{\psi} = \frac{1}{\sqrt{17}} \bigg(\ket{b=1,1} - i\sqrt{8} \ket{b=1,2} + i\sqrt{8} \ket{b=-1} \bigg)$$

$B$ is degenerate with respect to $1$:

$$\begin{aligned}
\mathcal{P}_{b=1} &= \lvert\braket{b=1,1}{\psi}\rvert^2 + \lvert\braket{b=1,2}{\psi}\rvert^2 \\
&= \frac{8}{17} + \frac{1}{17} = \frac{9}{17} \\
\mathcal{P}_{a=0} &= \lvert\braket{a=0}{b=1}\rvert^2 = \lvert\bra{a=0}\bigg(\frac{1}{\sqrt{9}}\ket{b=1,1}+\frac{-i\sqrt{8}}{\sqrt{9}}\ket{b=1,2}\bigg)\rvert^2\\
&= \frac{8}{9}
\end{aligned}$$

$$\frac{8}{17}$$

## Part C

$A$ has no degeneracy with respect to obtaining the value of $0$, so the measurement collapses into a single state. This state then corresponds directly to one of the eigenstates of $B$ for $b=1$, and so the probability of obtaining $a=0$ and $b=1$ is just $8/17$. By measuring $B$ first, the state collapses into a superposition of the $b=1$ eigenstates, but since $[A,B]=0$, the superposition of the two $b=1$ states is not equal and the probability of measuring $a=0$ is $8/9$. Since we multiply the probabilities of successive measurements, this simplifies down to the same answer as before. We could avoid most of this mess just by using the C.S.C.O basis of $a,b$ to simplify calculations going forward.

\pagebreak

# Question 4

> Consider a physical system whose state and two observables $A$ and $B$ are represented by: $$A \dot{=} \begin{pmatrix} 1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0 \end{pmatrix}, \quad B \dot{=} \begin{pmatrix} 0 & 0 & -1 \\ 0 & 0 & i \\ -1 & -i & 4 \end{pmatrix}, \quad C \dot{=} \begin{pmatrix} 2 & 0 & 0 \\ 0 & 1 & 3 \\ 0 & 3 & 1 \end{pmatrix}$$

I spent a lot of time working through and finding the eigenvalues and eigenvectors of $B$, making a lot of mistakes and resolved to give in and use technology on this question. In doing so, I learned a painful lesson with Mathematica that telling two matrices to multiply each other via $*$ does not give the expected result, and so I spent a long while trying to figure out the common basis for all 3 matrices, since the computer was telling me that they commute. Finally, after a sanity check and suggestion to use the $.$ (`Dot[ , ]`) style of multiplication, I discovered my error.

Using the following Mathematica code, I obtained:

```Mathematica
MatA = ({
    {1, 0, 0},
    {0, 0, 1},
    {0, 1, 0}
   });
MatB = ({
    {0, 0, -1},
    {0, 0, I},
    {-1, -I, 4}
   });
MatC = ({
    {2, 0, 0},
    {0, 1, 3},
    {0, 3, 1}
   });
Dot[MatA, MatB] - Dot[MatB, MatA] // MatrixForm
Dot[MatA, MatC] - Dot[MatC, MatA] // MatrixForm
Dot[MatB, MatC] - Dot[MatC, MatB] // MatrixForm
{aMeasurements, aStates} = Eigensystem[MatA]
{bMeasurements, bStates} = Eigensystem[MatB]
{cMeasurements, cStates} = Eigensystem[MatC]
```

$$[A,B] = \begin{pmatrix} 0 & 1 & -1 \\ -1 & -2i & 4 \\ 1 & -4 & 2i \end{pmatrix}, \quad [A,C] = 0, \quad [B,C] = \begin{pmatrix} 0 & -3 & 1 \\ 3 & 6i & -12 \\ -1 & 12 & -6i \end{pmatrix}$$

## Part A

> Which among these observables are compatible? Find the results of the measurements of the compatible observables.

Only $[A,C]=0$.

| $A$ eigenvalues | $C$ eigenvalues | Corresponding $A$ and $C$ eigenvectors |
| -- | -- | --- |
| $-1$ | $-2$ | $$\frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ -1 \\ 1 \end{pmatrix}$$ |
| $1$ | $4$ | $$\frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ 1 \\ 1 \end{pmatrix}$$ |
| $1$ | $2$ | $$\begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}$$ |

## Part B

> Give a basis of eigenvectors common to these observables.

Noting that $C$ does not have any degeneracy, we can use that to remove the degeneracy in $A$'s $a=1$ measurement:

$$\ket{a=-1,c=-2} \dot{=} \frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ -1 \\ 1 \end{pmatrix}, \quad \ket{a=1,c=4} \dot{=} \frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ 1 \\ 1 \end{pmatrix}, \quad  \ket{a=1,c=2} \dot{=} \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}$$

## Part C

> Do the following constitute a C.S.C.O.: $\{A\}$, $\{B\}$, $\{C\}$, $\{A,B\}$, $\{B,C\}$, $\{A,C\}$?

### Not C.S.C.O

$\{A\}$ is not a C.S.C.O. due to the degeneracy in its eigenvalues. From Part A, only $[A,C]=0$, so $\{A,B\}$ and $\{B,C\}$ do not form a C.S.C.O.

### C.S.C.O

$\{A,C\}$ is a C.S.C.O as noted in Parts A and B. $\{B\}$ and $\{C\}$ are C.S.C.O.'s as there is no degeneracy in their eigenvalues and the eigenvectors are unique from each other:

$$2+\sqrt{6} \mapsto \begin{pmatrix} -\frac{1}{2+\sqrt{6}} \\ \frac{i}{2+\sqrt{6}} \\ 1 \end{pmatrix}, \quad 2-\sqrt{6} \mapsto \begin{pmatrix} \frac{1}{-2+\sqrt{6}} \\ -\frac{i}{-2+\sqrt{6}} \\ 1 \end{pmatrix}, \quad 2+\sqrt{6} \mapsto \frac{1}{\sqrt{2}}\begin{pmatrix} -i \\ 1 \\ 0 \end{pmatrix}$$
