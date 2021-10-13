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

> Finish detailing:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}\sum_{j,k}{\ket{\varphi_j}\bra{\varphi_k}} \neq \mathbb{I}$$

And so, we cannot resolve the reordering in this method, as we're unable to collapse the outer product back to the Identity operator: The only way we can equate $Tr(ABC) = Tr(ACB)$ is to require $[B,C]=0$ and then use commutivity in the step prior to introducing the completeness relations.

## Part B

> $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\newcommand{\braket}[2]{{\left\langle #1 \middle| #2 \right\rangle}}
\text{Tr}\bigg(\ket{\psi}\bra{\varphi}\bigg) = \braket{\varphi}{\psi}
$$ where $\left|\varphi\right\rangle$, $\left|\psi\right\rangle$ are state vectors.

Suppose we define $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\psi}$ and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi}$ to have the following representations:

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\ket{\psi} = \sum_{i=0}^{n}{a_i\ket{\varphi_i}}, \quad \ket{\varphi} = \sum_{j=0}^{n}{b_j\ket{\varphi_j}}$$

Then, the outer product of these two vectors is simply:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\ket{\psi}\bra{\varphi} = \sum_{i,j}^{n}{a_i (b_j)^* \ket{\varphi_i}\bra{\varphi_j}}$$

This will create an $n\times n$ matrix where each element is given by $a_i {b_j}^*$. Then the trace of this matrix is just the sum of the main diagonal which is equivalent to introducing a Kronecker Delta:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\ket{\psi}\bra{\varphi} = \sum_{i,j}^{n}{a_i (b_j)^* \ket{\varphi_i}\bra{\varphi_j} \delta_{i,j}}=\sum_{n}{a_n (b_n)^* \ket{\varphi_n}\bra{\varphi_n}}$$

And as we've demonstrated in Part A, this is just the trace of the corresponding matrix representation.

\pagebreak

# Question 2

> Consider the following matrices,

$$A = \begin{pmatrix} 7 & 0 & 0 \\ 0 & 1 & -i \\ 0 & i & -1 \end{pmatrix}, \quad B = \begin{pmatrix} 1 & 0 & 3 \\ 0 & 2i & 0 \\ i & 0 & -5i \end{pmatrix}$$

## Part A

> Are $A$ and $B$ Hermitian? Write down the matrices representating $A^\dagger$ and $B^\dagger$.

By inspection $A$ is antisymmetric about the main diagonal with complex values, so we expect it to be Hermitian. $B$ is neither symmetric or antisymmetric and contains complex values on the main diagonal; and so we expect it to be neither Hermitian or Anti-Hermitian.

$$A^\dagger = \begin{pmatrix} 7 & 0 & 0 \\ 0 & 1 & -i \\ 0 & i & -1 \end{pmatrix}^\dagger = \begin{pmatrix} 7 & 0 & 0 \\ 0 & 1 & -i \\ 0 & i & -1 \end{pmatrix} = A$$

$$B^\dagger = \begin{pmatrix} 1 & 0 & 3 \\ 0 & 2i & 0 \\ i & 0 & -5i \end{pmatrix}^\dagger = \begin{pmatrix} 1 & 0 & -i \\ 0 & -2i & 0 \\ 3 & 0 & 5i \end{pmatrix} = \neg \bigg(B\vee (-B)\bigg)$$

And we can see that our expectations are valid.

## Part B

There are two well known properties regarding square matrices:

- The sum of the eigenvalues is equal to the trace of the matrix
- The product of the eigenvalues is equal to the determinant of the matrix

From this, we by looking at $A$, we can conclude to things:

1. $\text{Tr}(A)=7$
2. $\det{A}=7(-1+i^2)=-14$

And since $A$ is block diagonal, we know that one of the eigenvalues is $7$ and that the other two eigenvalues must be opposite signs and multiply to $-2$. Restricted to the reals, we then infer that the two eigenvalues of the sub-matrix are $\pm\sqrt{2}$.

Proof:

$$\begin{aligned}
\begin{vmatrix} 1-\lambda & -i \\ i & -1-\lambda \end{vmatrix} = -(1-\lambda)(1+\lambda) - (-i)i &= 0 \\
(1-\lambda^2)+i(-i) &= 0\\
\lambda &= \pm\sqrt{2}
\end{aligned}$$

The eigenvector corresponding to $7$, we take to simply be: $\begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}$. Then, knowing that the eigenvectors of a Hermitian matrix are orthogonal, we can guarantee this by setting the first value of the remaining eigenvectors to $0$, such that:

$$\begin{pmatrix} 0 \\ ? \\ ? \end{pmatrix}$$

Then, using the eigenvalue equation, we can find the two remaining eigenvectors for the subspace:

$$\begin{aligned}
\begin{pmatrix} 1 & -i \\ i & -1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} &= \lambda \begin{pmatrix} x \\ y \end{pmatrix}\\
x-iy=\lambda x, &\quad ix - y = \lambda y\\
x-\lambda x &= iy\\
x(1-\lambda) &= iy\\
&\rightarrow \text{choose }x=i\\
y&=1\mp\sqrt{2}
\end{aligned}$$

Now we just normalize:

$$\begin{aligned}
{N_1}^2 (0,\ -i,\ 1-\sqrt{2})\begin{pmatrix} 0 \\ i \\ 1-\sqrt{2} \end{pmatrix} &= 1 \\
{N_1}^2(1+(1-\sqrt{2})^2) &= 1 \\
{N_1}^2(1+1-2\sqrt{2}+2) &= 1 \\
{N_1}^2(4-2\sqrt{2}) &= 1 \\
{N_1} &= \frac{1}{\sqrt{4-2\sqrt{2}}}
\end{aligned}$$

$$\begin{aligned}
{N_2}^2 (0,\ -i,\ 1+\sqrt{2})\begin{pmatrix} 0 \\ i \\ 1+\sqrt{2} \end{pmatrix} &= 1 \\
{N_2}^2(1+(1+\sqrt{2})^2) &= 1 \\
{N_2}^2(1+1+2\sqrt{2}+2) &= 1 \\
{N_2}^2(4+2\sqrt{2}) &= 1 \\
{N_2} &= \frac{1}{\sqrt{4+2\sqrt{2}}}
\end{aligned}$$

$$\begin{aligned}
\lambda = \sqrt{2} \mapsto \frac{1}{\sqrt{2\sqrt{2}}}\begin{pmatrix} 0 \\ i \\ 1-\sqrt{2} \end{pmatrix}, &\qquad \lambda = -\sqrt{2} \mapsto \frac{1}{\sqrt{4+2\sqrt{2}}}\begin{pmatrix} 0 \\ i \\ 1+\sqrt{2} \end{pmatrix}
\end{aligned}$$

## Part C

> Show that the eigenvectors of $A$ form a (complete and orthonormal) basis.

Orthogonal:

$$N_2(1,\ 0,\ 0)\begin{pmatrix} 0 \\ i \\ 1-\sqrt{2} \end{pmatrix} = 0$$
$$N_1(1,\ 0,\ 0)\begin{pmatrix} 0 \\ i \\ 1+\sqrt{2} \end{pmatrix} = 0$$
$$N_1 N_2 (0,\ -i,\ 1-\sqrt{2})\begin{pmatrix} 0 \\ i \\ 1+\sqrt{2} \end{pmatrix} = N_1 N_2(1+(1-\sqrt{2})(1+\sqrt{2}))=N_1 N_2 (1+1-2)=0$$

Normal:

$$(1,\ 0,\ 0)\begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix} = 1$$
$${N_1}^2(0,\ -i,\ 1-\sqrt{2})\begin{pmatrix} 0 \\ i \\ 1-\sqrt{2} \end{pmatrix} = 1$$
$${N_2}^2(0,\ -i,\ 1+\sqrt{2})\begin{pmatrix} 0 \\ i \\ 1+\sqrt{2} \end{pmatrix} = 1$$

Complete:

This one got pretty messy with the normalization constants, and I needed to use Mathematica to find where I was making algebraic mistakes:

```Mathematica
Subscript[A, 1] = ({
    {1},
    {0},
    {0}
   });
Subscript[A, 2] = ({
    {0},
    {I},
    {1 - Sqrt[2]}
   });
Subscript[A, 3] = ({
    {0},
    {I},
    {1 + Sqrt[2]}
   });

Subscript[N, 2] =
 FullSimplify[(1/Sqrt[
    Dot[ConjugateTranspose[Subscript[A, 2]], Subscript[A,
     2]]])[[1]][[1]]]
Subscript[N, 3] =
 FullSimplify[(1/Sqrt[
    Dot[ConjugateTranspose[Subscript[A, 3]], Subscript[A,
     3]]])[[1]][[1]]]
```

This will create the eigenvectors and verify the normalization constants for the not-immediately-normal eigenvectors. Then this next bit will verify the form of the outer product for each eigenvector:

```Mathematica
KroneckerProduct[ConjugateTranspose[Subscript[A, 1]], Subscript[A,
  1]] // MatrixForm
KroneckerProduct[Subscript[N, 2]*ConjugateTranspose[Subscript[A, 2]],
  Subscript[N, 2]* Subscript[A, 2]] // MatrixForm
KroneckerProduct[Subscript[N, 3]*ConjugateTranspose[Subscript[A, 3]],
  Subscript[N, 3]* Subscript[A, 3]] // MatrixForm
```

And Finally, we can verify it is complete as the sum of each results in the identity:

```Mathematica
FullSimplify[
  KroneckerProduct[ConjugateTranspose[Subscript[A, 1]], Subscript[A,
    1]] + KroneckerProduct[
    Subscript[N, 2]*ConjugateTranspose[Subscript[A, 2]],
    Subscript[N, 2]* Subscript[A, 2]] +
   KroneckerProduct[
    Subscript[N, 3]*ConjugateTranspose[Subscript[A, 3]],
    Subscript[N, 3]* Subscript[A, 3]]] // MatrixForm
```

![Results from the Mathematica Notebook](/Users/remember-the-cant/Documents/simmeringrook.github.io/courses/PH651/Homework/mathematica.png)

\pagebreak

# Question 3

> Consider a system whose Hamiltonian is given by $$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}} H = \alpha \bigg(\ket{\varphi_1}\bra{\varphi_2}+\ket{\varphi_2}\bra{\varphi_1}\bigg)$$ where $\alpha$ is a real number with dimensions of energy.

## Part A

> Is $H$ a projection operator? What about $\alpha^{-2}H^2$?

If we assume nothing about the $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\{\ket{\varphi_i}\}$ basis other than it has two normalized elements, we can consider $H$ acting on a state from this set:

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
H\ket{\varphi_1} &= \alpha \bigg(\ket{\varphi_1}\bra{\varphi_2}+\ket{\varphi_2}\bra{\varphi_1}\bigg)\ket{\varphi_1}\\
&= \alpha \bigg(\ket{\varphi_1}\bra{\varphi_2}\ket{\varphi_1}+\ket{\varphi_2}\bra{\varphi_1}\ket{\varphi_1}\bigg)\\
&= \alpha \bigg(\varphi_{1,2}^* \ket{\varphi_1} + \ket{\varphi_2}\bigg)\\
\\
H\ket{\varphi_2} &= \alpha \bigg(\ket{\varphi_1}+\varphi_{1,2} \ket{\varphi_2}\bigg)
\end{aligned}$$

And we can see that continued actions by $H$ on either ket will not yield the same state: even if we add the constraint that $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\{\ket{\varphi_i}\}$ is orthogonal. Therefore, $H$ is not a projection operator.

$$\newcommand{\bra}[1]{{\left\langle#1\right|}}
\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
\alpha^{-2} H^2 &= \alpha \bigg(\ket{\varphi_1}\bra{\varphi_2}+\ket{\varphi_2}\bra{\varphi_1}\bigg)^2\\
&= \alpha \bigg( \ket{\varphi_1}\bra{\varphi_2}\ket{\varphi_1}\bra{\varphi_2}+ \ket{\varphi_1}\bra{\varphi_2}\ket{\varphi_2}\bra{\varphi_1} + \ket{\varphi_2}\bra{\varphi_1}\ket{\varphi_1}\bra{\varphi_2} + \ket{\varphi_2}\bra{\varphi_1}\ket{\varphi_2}\bra{\varphi_1} \bigg)\\
&= \alpha \bigg( \varphi_{1,2}^*\ket{\varphi_1}\bra{\varphi_2}+ \ket{\varphi_1}\bra{\varphi_1} + \ket{\varphi_2}\bra{\varphi_2} + \varphi_{1,2}\ket{\varphi_2}\bra{\varphi_1} \bigg)\\
\end{aligned}$$

Similarly, we can see that the 'opposite' outer products remain, as in $H$, and that without more information about $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\{\ket{\varphi_i}\}$, we would see that successive measurements do not yield the same resulting state. However, if we assume that $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\{\ket{\varphi_i}\}$ is orthonormal, then the 'cross' terms vanish and $\alpha^{-2}H^2$ takes the functional form of the Identity operator (scaled by a constant), and then we can state that $\alpha^{-2}H^2$ would satisfy the criteria for being a projection operator.

## Part B

> Are $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\{\ket{\varphi_i}\}$ eigenstates of $H$?

Using our work from Part A: even in the generous case of assuming orthonormality of the set, $H$ acting on one of these basis kets does not return the same ket, and from this we can conclude that they are not eigenstates of $H$.

## Part C

> Assuming that $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\{\ket{\varphi_i}\}$ form a complete and orthonormal basis, find the matrix representing $H$ in this basis. What are the eigenvalues and eigenvectors of this matrix?

Using the following representations,

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi_1}\dot{=}\begin{pmatrix} 1 \\ 0 \end{pmatrix}, \quad \ket{\varphi_2}\dot{=}\begin{pmatrix} 0 \\ 1 \end{pmatrix}$$

we find the matrix representation of $H$ to be:

$$H\dot{=}\alpha \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$$

Then using our trick from 2 Part B:

- $\text{Tr}(H)=0 \Rightarrow \lambda_1 +\lambda_2 = 0$
- $\det{H}=-1 \Rightarrow \lambda_1 = -\lambda_2 \Rightarrow \lambda = \pm 1$
- This was for the matrix in isolation: scaling by our constant energy value: $\lambda = \pm \alpha$

And the eigenvectors are given by normalizing the result of the system of equations:

$$\begin{aligned}
\alpha \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} &= \pm\alpha \begin{pmatrix} x \\ y \end{pmatrix}\\
y=\pm x, &\quad x=\pm y\\
\\
\text{choose } & x=1
\end{aligned}$$

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
+\alpha \mapsto \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix} & =\frac{1}{\sqrt{2}}\bigg(\ket{\varphi_1} + \ket{\varphi_2}\bigg)\\
-\alpha \mapsto \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix} &=\frac{1}{\sqrt{2}}\bigg(\ket{\varphi_1} - \ket{\varphi_2}\bigg)
\end{aligned}$$

\pagebreak

# Question 4

> Show that for any two operators $A$ and $B$, $$e^B A e^{-B} = A + [B,A]+ \frac{1}{2!}[B,[B,A]]+...$$

Using the Taylor Series expansion, we obtain:

$$\bigg(\sum_{n=0}^{\infty}{\frac{B^n}{n!}}\bigg)A\bigg(\sum_{n=0}^{\infty}{\frac{(-1)^nB^n}{n!}}\bigg)$$

Expanding out $e^{-B}$ to $n=3$:

$$e^B A e^{-B} = \bigg(\sum_{n=0}^{\infty}{\frac{B^n}{n!}}\bigg) \bigg(A\frac{B^0}{0!} + A \frac{(-1)B^1}{1!} + A \frac{(-1)^2 B^2}{2!} + A \frac{(-1)^3 B^3}{3!} + \mathcal{O}(A B^{-4})\bigg)$$

$$e^B A e^{-B} = \bigg(\sum_{n=0}^{\infty}{\frac{B^n}{n!}}\bigg) \bigg(A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!} + \mathcal{O}(A B^{-4})\bigg)$$

Now expanding out $e^{B}$ to $n=3$:

$$e^B A e^{-B} = \bigg(1 + B + \frac{B^2}{2!} + \frac{B^3}{3!} + \mathcal{O}(B^{4})\bigg) \bigg(A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!} + \mathcal{O}(A B^{-4})\bigg)$$

$$\begin{aligned}
e^B A e^{-B} &= \mathbb{I}\bigg(A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!} + \mathcal{O}(A B^{-4})\bigg) \\
&+ B\bigg(A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!} + \mathcal{O}(A B^{-4})\bigg) \\
&+ \frac{B^2}{2!}\bigg(A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!} + \mathcal{O}(A B^{-4})\bigg) \\
&+ \frac{B^3}{3!} \bigg(A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!} + \mathcal{O}(A B^{-4})\bigg) \\
&+ \mathcal{O}(B^{4}) \bigg(A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!} + \mathcal{O}(A B^{-4})\bigg)
\end{aligned}$$

For ease of clarity, I'll just omit the higher order terms for now by wraping them inside $\mathcal{O}(B^4)A\mathcal{O}(B^{-4})$:

$$\begin{aligned}
e^B A e^{-B}
&= A - AB + \frac{AB^2}{2!} -\frac{AB^3}{3!}\\
&+ BA - BAB + \frac{BAB^2}{2!} -\frac{BAB^3}{3!} \\
&+ \frac{B^2}{2!}A - \frac{B^2}{2!}AB + \frac{B^2}{2!}\frac{AB^2}{2!} - \frac{B^2}{2!}\frac{AB^3}{3!} \\
&+ \frac{B^3}{3!}A - \frac{B^3}{3!}AB + \frac{B^3}{3!}\frac{AB^2}{2!} -\frac{B^3}{3!}\frac{AB^3}{3!} \\
&+ \mathcal{O}(B^4)A\mathcal{O}(B^{-4})
\end{aligned}$$

Recall from the desired outcome, we need something that looks like $[B,[B,A]]$, so working that out, we can use this to guide what terms need to group together to collapse, $[B,[B,A]] = [B,BA - AB] = B(BA-AB) - (BA-AB)B = B^2A - BAB - BAB - A B^2$.

$$\begin{aligned}
e^B A e^{-B}
&= A + (BA - AB) \\
&+ \frac{1}{2!}\bigg(B^2 A - (2!)BAB + AB^2\bigg)\\
&+ \frac{1}{3!} \bigg(B^3A - 2B^2 AB - BAB^2 - B^2AB + 2BAB^2 + AB^3\bigg)\\
&+ \mathcal{O}(B^4)A\mathcal{O}(B^{-4})
\end{aligned}$$

> $$\begin{aligned}{}
[B,[B,[B,A]]] &= [B, B^2A -2BAB - A B^2] \\
&= B(B^2A -2BAB - A B^2) - (B^2A -2BAB - A B^2)B\\
&= B^3A - 2B^2 AB - BAB^2 - B^2AB + 2BAB^2 + AB^3\end{aligned}$$

$$\begin{aligned}
e^B A e^{-B} &= A + [B,A] + \frac{1}{2!}[B,[B,A]] + \frac{1}{3!} [B,[B,[B,A]]] + \mathcal{O}(B^4)A\mathcal{O}(B^{-4})
\end{aligned}$$
