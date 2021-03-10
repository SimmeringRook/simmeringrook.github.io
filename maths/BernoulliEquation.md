# Bernoulli Equations
?>**Definition**: A Bernoulli equation is an equation that has the form: $  y' + p(t)y = f(t)y^r$,  where $|r| > 1$, $r\in$**Z**.

## Methods
For any First Order Nonlinear equation that can be written in the form of:
$$  y' + p(t)y = f(t)y^r$$
where $|r|>1$

### Direct Substitution
We can reduce this equation to a linear First Order equation with a substitution in the form of:
$$  u = y^{1-r} $$

And then solve the first order linear equation of the form:
$$  u' + p(t)u = f(t) $$

### Separation of Variables
We can also solve this equation by doing the following substitution:
$$  y = u\cdot y_h$$
where $y_h$ is the solution to the [[Characteristic Equation]].


Performing the substitution:

$$\begin{aligned}
  y  &= u\cdot y_h \\
  y' &= u'\cdot y_h + u\cdot {y_{h}}'
\end{aligned}$$

Into:

$$  y' + p(t)y = f(t)y^r $$

Which simplifies:

$$\begin{aligned}
  (u'\cdot y_h + u\cdot {y_{h}}') + p(t)(u\cdot y_h)       &= f(t)(u\cdot y_h)^r \\
  u'\cdot y_h                   + u({y_{h}}' + p(t)y_{h})  &= f(t) u^r {y_h}^r
\end{aligned}$$

!> Note that: ${y_h}' + p(t)y_h = 0$, by definition. For more see [[Characteristic Equation]].

$$\begin{aligned}
  u'\cdot y_{h} &= f(t) u^r {y_h}^r \\
  u'            &= f(t)u^r\cdot {y_h}^{r-1} \\
  u^{-r} u'     &= f(t) \cdot {y_h}^{r-1}
\end{aligned}$$
The simplified form of the equation with the substitution applied can be solved by [[Separation of Variables]].

## Special Cases

#### r &#61; 0:
If $r = 0$, the equation then has the form of: $y' + p(t)y = f(t)$ And can be solved by:
  - if $f(t)$ is non-zero: [Integrating Factor](/maths/IntegratingFactor.md)
  - or by [Separation of Variables](/maths/SeparationOfVariables.md), if $f(t) = 0$

#### r &#61; 1:

If $r = 1$, the equation then has the form of: $ y' + p(t)y = f(t)y$
  - Which can be rewritten as $\frac{y'}{y} = f(t) - p(t)$ And be solved by separation of variables.

## Examples
### Example 1
