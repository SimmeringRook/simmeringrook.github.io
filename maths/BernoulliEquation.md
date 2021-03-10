# Bernoulli Equations
A Bernoulli equation is an equation that has the form:
$$  y' + p(t)y = f(t)y^r ,  where |r| > 1$$

### Tips
#### $r\leq 1$:
Note for the cases of $0 \leq r < 1$:
- If $r = 0$, the equation then has the form of: $y' + p(t)y = f(t)$ And can be solved by:
  - if $f(t)$ is non-zero: [Integrating Factor](/maths/IntegratingFactor.md)
  - or by [Separation of Variables](/maths/SeparationOfVariables.md), if $f(t) = 0$
- If $r = 1$, the equation then has the form of: $ y' + p(t)y = f(t)y$
  - Which can be rewritten as $\frac{y'}{y} = f(t) - p(t)$ And be solved by separation of variables.

==Method==
For any First Order Nonlinear equation that can be written in the form of:
  y' + p(t)y = f(t)y^r ,  where |r|>1
===Direct Substitution===
We can reduce this equation to a linear First Order equation with a subsitution in the form of:
  u = y^(1-r)

And then solve the first order linear equation of the form:
  u' + p(t)u = f(t)

===Separation of Variables===
We can also solve this equation by doing the following substitution:
  y = u·y_h
where y_h is the solution to the [[Characteristic Equation]]

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Details:</div>
<div class="mw-collapsible-content">
Performing the substitution:
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
  y = u·y_h
  y' = u'·y_h + u·y_h'
</div>
Into:
  y' + p(t)y = f(t)y^r
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
Which simplifies:
<div class="mw-collapsible-content">
  (u'·y_h + u·y_h') + p(t)(u·y_h) = f(t)(u·y_h)^r
  u'·y_h + u(y_h' + p(t)y_h) = f(t)u^r y_h^r
Note that: y_h' + p(t)y_h = 0, by definition. For more see [[Characteristic Equation]].
  u'·y_h = f(t)u^r y_h^r
  u' = f(t)u^r·y_h^(r-1)
</div></div>
  u^(-r) u' = f(t)·y_h^(r-1)
</div></div>
The simplified form of the equation with the substitution applied can be solved by [[Separation of Variables]].

==Examples==
===Example 1===
