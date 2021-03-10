### First Order ODE
The general form of a first order ODE is:

  f(t,y,y') = 0

or, once solved:

  y'= f(t,y)

## Forms
### General
The general form of a first order linear ODE is:

  a_1(t)·y'+a_0(t)·y=f(t)

### Standard Form
The standard from for a first order linear equation is when the leading coefficient on y' is 1. To do this, we divide the equation by a_1(t), and define the following to create a cleaner form of what we call the standard form of a first order linear equation:

<strong>TODO: replace with picture that is easier to read</strong>
  y' + p(t)y = q(t)

Note that:
*Leading coefficient is 1.
  p(t) = a_0(t)/a_1(t)
  q(t) = f(t)/a_1(t)
  a_1(t) /= 0
*Also, for all t, where a_1(t) = 0 will be excluded from the domain

## Problem solving techniques
### Integrating Factor
#### Step 1
Multiply both sides of equation by mu(t). mu(t) has not been defined at this stage.

  mu(t)y' + mu(t)p(t)y = mu(t)q(t)

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

#### [$1]

  (mu(t)y)' = mu(t)q(t)

Integrate w.r.t. some placeholder variable

  Integrate ((mu(t)y)' ds) = Integrate (mu(s)q(s)ds) + C
  mu(t)y = Integrate (mu(s)q(s)ds) + C
  y = 1/mu(t) · Integrate (mu(s)q(s)ds) + C

### Integrating Factor Examples
Solve the Initial Value Problem:

  ty'+2y=4t^2, y(1) = 2

Solution:

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

### Separable Equation
If in the first order ODE, y'=f(t,y), we can write f(t,y) = g(t)h(y), then the equation is called separable. We can write f(t,y) as a product of a function of t and a function of y.
