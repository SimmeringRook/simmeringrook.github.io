# MTH 537: General Relativity, Week 4

$$
\newcommand\wrap[2]{\left( #1 \right)_{ #2 }}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial^2 #2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2\partial #3}}
\newcommand\bra[1]{\langle #1 |}
\newcommand\ket[1]{| #1 \rangle}
\newcommand\braket[3]{\bra{#1}#2\ket{#3}}
\newcommand\schwarzCurve{\left(1-\frac{2M}{r}\right)}
$$

## Concepts

## Lecture Notes

### Day 1

#### Radial Geodesics

Recall:
$$
\theta = \frac{\pi}{2}
\dot{\phi} = \frac{\ell}{r^2} \Rightarrow \ell = 0, \phi = constant
\dot{t} = \frac{e}{\schwarzCurve}

\dot{r}^2 = e^2 - \schwarzCurve
$$

Suppose:
$$
\dot{r}|_{r=r_0} = 0
\Rightarrow e^2 = 1-\frac{2M}{r_0}
\Rightarrow r_0 = \frac{2m}{1-e^2}

We can note that \abs{e} \leq 1, and without loss of generality e is positive (e\geq 0).

Cases:
e=1 <-> r_0 = \infty
0<e<1 <-> 2m < r_0 < \infty
e = 0 <-> r_0 = 2m

If we consider the cases where e=1, we have the category of geodesics:

\dot{r}^2 = \frac{2m}{r}

\dot{r} = \sqrt{\frac{2m}{r}}
\dot{t} = \frac{1}{\schwarzCurve}

For infalling, \dot{r} = -\sqrt{\frac{2m}{r}}
Far-away observer:

speed = \frac{dr}{dt}
 = \frac{\dot{r}}{\dot{t}}
 = -\schwarzCurve\sqrt{\frac{2m}{r}}

r-> 2M, \frac{dr}{dt} -> 0

Shell-observer:

speed = \frac{\frac{dr}{\sqrt{\schwarzCurve}}}{\sqrt{\schwarzCurve}dt}
 = \frac{\sigma^r}{\sigma^t}
 = \frac{1}{\schwarzCurve} \frac{\dot{r}}{\dot{t}}
 = - \sqrt{\frac{2M}{r}}

### Day 2

### Day 3
