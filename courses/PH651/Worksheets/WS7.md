---
title: Worksheet 7
subtitle: PH651, Fall 2021
author: Thomas Knudson
date: Monday, October 11, 2021
papersize: a4
geometry: margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 651, Fall 2021}
    \fancyhead[CO,CE]{WS 7}
    \fancyhead[LO,LE]{Knudson}
---

$$\ $$

Consider observables represented by $$A\ \dot{=} \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$$ and $$B\ \dot{=} \begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}$$ in some orthonormal basis by $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi_1}$ and $\newcommand{\ket}[1]{{\left|#1\right\rangle}}\ket{\varphi_2}$.

# Is $A$ a "Complete Set of Compatible Observables"?

By inspection, no. With $A$ being a diagonal matrix, the eigenvalues are shown on the main diagonal. $a_1 = a_2 = 1$ and the dimension of this eigenspace is greater than $1$. E.g., specifying the eigenvalue of $1$ does not uniquely specify with eigenvector of $A$ we are talking about. $$\ $$

# Is $B$ a "Complete Set of Compatible Observables"?

$B$ isn't diagonal, so we need to find the eigenvalues:

$$\begin{aligned}
\det{B-\lambda I} &= (1-\lambda)^2 - 1 \\
1 - 2\lambda + \lambda ^2 - 1 &= 0 \\
\lambda (\lambda - 2) &= 0\\
\lambda &= 0, 2
\end{aligned}$$

Eigenvectors:

$$\begin{aligned}
\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} &= \lambda \begin{pmatrix} x \\ y \end{pmatrix} \\
\\
x + y = \lambda x, &\qquad x + y =\lambda y
\end{aligned}$$

$$\begin{aligned}
x + y = 0, &\qquad x + y =0\\
x = -y, &\quad \text{choose } x=1\\
\lambda = 0 &\mapsto \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix}
\end{aligned}$$

$$\begin{aligned}
x + y = 2x, &\qquad x + y =2y\\
-x = -y, &\quad \text{choose } x=1\\
\lambda = 2 &\mapsto \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix}
\end{aligned}$$

Specifying $b_n$ is enough to specify an eigenvector explicitly. $B$ is a C.S.C.O. $$\ $$

# Is a set $\{ A, B \}$ a "Complete Set of Compatible Observables" (do the eigenvectors common to $A$ and $B$ form a unique basis)? If yes, write down the basis common to $A$ and $B$.

By inspection, $[A, B]=0$, so we know they do share a common set of eigenvectors and since $B$ is A C.S.C.O, we can use their eigenvectors to specify which set of eigenvalues we're referring[^1]:

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\begin{aligned}
(AB)\ket{\varphi_1} &= (ab)_1 \ket{a=1,\ b=0} \\
(AB)\ket{\varphi_2} &= (ab)_2 \ket{a=1,\ b=2} \\
\end{aligned}$$

$$\newcommand{\ket}[1]{{\left|#1\right\rangle}}
\{\ket{a=1,\ b=0},\ \ket{a=1,\ b=2}\} \dot{=} \left\{\frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ -1 \end{pmatrix},\ \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix}\right\}$$

[^1]: Just on a personal note, I knew it existed, but I was unsure of how to find the set. Took me a bit of reading and research to discover "the trick", and ultimately found guidance from Page 44 of Shankar. I know what to review and practice in the future, but I think part of it was due to $A$ having the same form as the $\mathbb{I}$. Thanks for asking this question!
