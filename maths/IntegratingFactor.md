## Method
### First Order Linear
Given a First order linear ODE in the form:
y' + p(t)y = f(t)
#  Multiply both sides of the equation by mu(t), where t is the independent variable. Rewrite the Left-hand side such that the equation is now in the form of:
#*  (mu(t)y(t))'y = mu(t)f(t)
#  Find mu(t):
#*  mu(t) = exp( Integrate(p(t) dt) )
#  Integrate both sides. If solving an equation with initial value problems, it might be easier to solve for C now before moving onto step 4.
#  Solve for y(t). General solution will have the form:
#*  y = 1/mu(t) · Integrate (mu(s)f(s)ds) + C
### Second Order Linear
<strong>TODO:: Elaborate</strong>
[https://en.wikipedia.org/wiki/Integrating_factor#Solving_second_order_linear_ordinary_differential_equations Wikipedia on using the method to solve Second Order Linear ODEs]
## Explanation of Method
#### Step 1
Multiply both sides of equation by mu(t). mu(t) has not been defined at this stage.

  mu(t)y' + mu(t)p(t)y = mu(t)f(t)

#### Step 2
Find a mu(t) such that the left hand side can be written as:

  (mu(t)y)'

  (mu(t)y)' = mu(t)y' + u(t)p(t)y
  mu'(t)y + mu(t)y' = mu(t)y' + u(t)p(t)y
  mu'(t)y = mu(t)p(t)y
  mu'(t) = mu(t)p(t)

Assume mu(t) > 0

  mu'(t) / mu(t) = p(t)

Integrate both sides

  Integrate(mu'(t)/mu(t) dt) = Integrate(p(t) dt)
  ln(mu(t)) = Integrate(p(t) dt)
  mu(t) = exp( Integrate(p(t) dt) )

#### Step 3

  (mu(t)y)' = mu(t)f(t)

Integrate w.r.t. some placeholder variable

  Integrate ((mu(t)y)' ds) = Integrate (mu(s)f(s)ds) + C
  mu(t)y = Integrate (mu(s)f(s)ds) + C
  y = 1/mu(t) · Integrate (mu(s)f(s)ds) + C

## Examples
### Example 1
Solve the Initial Value Problem:

  ty'+2y=4t^2, y(1) = 2

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
Rewrite the equation in standard form:

  y' + (2/t)y = 4t
  p(t) = 2/t
  q(t) = 4t

Find integrating Factor:

  mu(t) = exp( Integrate((2/t)dt) )
  mu(t) = exp(2 ln|t|)
  mu(t) = t^2

Multiply standard form by mu(t) and integrate

  t^2y' + 2ty = 4t^3
  (t^2y)' = 4t^3
  t^2y = Integrate ( 4s^3 ds + C)
  t^2y = t^4 + C
  y = (t^4 + C)/t^2

Solve IVP

  y(1)=2
  1^2·2=1^4+C
  2=1+C
  C=1

General Solution:
  y = (t^4 + C)/t^2

Specific Solution:
  y = t^2 + 1/t^2, t > 0
</div></div>
