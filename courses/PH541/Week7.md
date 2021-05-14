# PH 541: Statistical Mechanics, Week 7

$$\newcommand\dbar{đ}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{{\partial}^2 #1}{{\partial} #2 {\partial} #3}}
\begin{aligned}
\text{The following is a } &\text{test of rendering 'dbar'}\\
đ &= \dbar
\end{aligned}
$$

## Concepts

- Validity of the classical Approximation
- Equiparition Theorem

## Lecture Notes

### Day 1

## Day 1

Describing a system by
$f$ generalized coordinates and $f$ generalized conjugate momentum

We can describe the energy of a system by:

$$E = E(q_1, q_2, ..., q_f, p_1, p_2, ..., p_f)$$

Let us suppose the system satisfies the following constraint(s):

1. The total energy splits additively in the following form: $$E=\epsilon_i(p_i)+ E'(q_1,..., p_f)$$
    - only the $i$-th Energy term depends on $p_i$
    - $E'$ does not depend on $p_i$
2. Assume that $\epsilon_i(p_i)$ is a quadratic term: $$\epsilon_i(p_i)=b{p_i}^2$$ where $b$ is a constant

?> What is $\bar{\epsilon_i}$?

> Answer: $$\bar{\epsilon_i}=\frac{1}{2}kT$$

### Proof

We assume that the system allows us to assume classical approximations.

$$
\begin{aligned}
\bar{\epsilon_i} &= \frac{\frac{1}{(h^3)^f}\int_{\text{all phase space}}^{}{e^{-\beta E}\epsilon_i dp_1 ... dp_f dq_1 ... dq_f}}{\frac{1}{(h^3)^f} \int_{\text{all phase space}}^{}{e^{-\beta E} dp_1 ... dp_f dq_1 ... dq_f} } \\
&= \frac{\int_{}^{}{e^{-\beta E}\epsilon_i dp_1 ... dp_f dq_1 ... dq_f}}{\int_{}^{}{e^{-\beta E} dp_1 ... dp_f dq_1 ... dq_f} } \\
&= \frac{\int_{}^{}{e^{-\beta(\epsilon_i(p_i)+E')}\epsilon_i(p_i) dp_1 ... dp_f dq_1 ... dq_f}}{\int_{}^{}{e^{-\beta (\epsilon_i(p_i)+E')} dp_1 ... dp_f dq_1 ... dq_f} } \\
&= \frac{\int_{}^{}{e^{-\beta\epsilon_i(p_i)}\epsilon_i(p_i) dp_i }\int_{}^{}{e^{-\beta E'} dp_1 ... dp_f dq_1 ... dq_f}}{\int_{}^{}{e^{-\beta\epsilon_i(p_i))} dp_i}\int_{}^{}{e^{-\beta E'} dp_1 ... dp_f dq_1 ... dq_f} } \\
&= \frac{\int_{}^{}{e^{-\beta\epsilon_i(p_i)}\epsilon_i(p_i) dp_i }}{\int_{}^{}{e^{-\beta\epsilon_i(p_i))} dp_i}} \\
\end{aligned}$$

> We now rewrite the integrand of the numerator as a partial derivative: $$\begin{aligned}
\int_{}^{}{e^{-\beta\epsilon_i(p_i)}\epsilon_i(p_i) dp_i } &\Rightarrow -\pder{}{\beta}\int_{}^{}{e^{-\beta\epsilon_i(p_i)}dp_i }\\
Z' &=\int_{}^{}{e^{-\beta\epsilon_i(p_i)}dp_i } \\
\bar{\epsilon_i} &= \frac{-\pder{}{\beta}Z'}{Z'}\\
&= -\pder{\ln{Z'}}{\beta}
\end{aligned}$$ Now we can use the second constraint.
$$\begin{aligned}
Z' &= \int_{-\infty}^{\infty}{e^{-\beta\epsilon_i(p_i)}dp_i } = \int_{-\infty}^{\infty}{e^{-\beta b{p_i}^2}dp_i }\\
&= \beta^{-\frac{1}{2}} \int_{-\infty}^{\infty}{e^{-\beta b{p_i}^2}d(\beta^{-\frac{1}{2}}p_i) }\\
&= \beta^{-\frac{1}{2}} \int_{-\infty}^{\infty}{e^{-b(\beta^{-\frac{1}{2}}p_i)^2}d(\beta^{-\frac{1}{2}}p_i)}\\
\text{Let $y$} &= \beta^{-\frac{1}{2}}p_i\\
Z' &= \beta^{-\frac{1}{2}} \int_{-\infty}^{\infty}{e^{-by^2}d(y}
\end{aligned}$$

Bringing this all together:

$$
\begin{aligned}
\bar{\epsilon_i} &= -\pder{\ln{Z'}}{\beta} \\
&= -\pder{}{\beta} \left[\ln{\beta^{-\frac{1}{2}} \int_{-\infty}^{\infty}{e^{-by^2}d(y}} \right] \\
&= -\pder{}{\beta} \left[\ln{\beta^{-\frac{1}{2}}} + \n{\int_{-\infty}^{\infty}{e^{-by^2}d(y}} \right]\\
&= -\pder{}{\beta} ln{\beta^{-1\frac{1}{2}}}\\
&= ... = \frac{1}{2}kT
\end{aligned}$$

### Heat Capacity of an ideal monatomic gas with N molecules

Kinetic energy of any ideal gas is:

$$E_k = \frac{{p_x}^2}{2m}$$

with a total energy:

$$E = \sum_{}{...}$$

$$\bar{E_{total}} = N\cdot \left(\frac{1}{2}kT + \frac{1}{2}kT + \frac{1}{2}kT \right)
&= N\frac{3}{2}kT$$

$$C_V = \wrap{\pder{\bar{E}}{T}}{V} = N\frac{3}{2}k = \frac{3}{2}R$$
