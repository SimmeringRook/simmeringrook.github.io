# PH 541: Statistical Mechanics, Week 1

[[toc]]

$$\newcommand\dbar{đ}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{{\partial}^2 #1}{{\partial} #2 {\partial} #3}}
\begin{aligned}
đ &= \dbar
\end{aligned}
$$

## Concepts

## Lecture Notes

### Day 1

First 2-3 Weeks:

 - Review Thermal Physics (Macroscopic)

Week 4-10:

 - Statistical Physics
 - Microscopic thermodynamics

#### Macroscopic Thermodynamics

There are four laws of Thermodynamics: (page 122-123)

1. Thermal Equilibrium
2. $dE = -{đ}W + {đ}Q$
3. Principle of the Increase of Entropy
4. Minimal Entropy

##### The Zeroth Law

?> if two thermodynamic systems are each in thermal equilibrium with a third system, then they are in thermal equilibrium with each other.

##### The First Law

- Conservation of Energy
- $E$ is the internal energy of the system
  - $dE$ is a change of the internal energy ([exact](/maths/Differentials.md) & total differential)
  - a function of the state of the system
    - E.g., for a gas in a bottle, the state of the system is described by number of molecules, volume, and temperature.
- $W$ is work
  - ${đ} W$ is an [inexact](/maths/Differentials.md) differential
  - The work you have to do is not determined by the state of the system; but by the process.
  - Not a state function
- $Q$ is heat transfer
  - ${đ}Q$ is the heat absorbed by the system.

Reversible

- The first law becomes: $dE={đ}Q-pdV$
  - an Isolated system receives no heat energy, so $dE=-pdV$
  - Otherwise, the system absorbs heat through a quasistatic process:
    - ${đ}Q=TdS$


##### The Second Law

Describes the direction of natural processes.

  - E.g., heat cannot (naturally) transfer from a colder body to a hotter body

We can quantify the macroscopic state of a system using [Entropy](/physics/Entropy.md).
For an isolated system:
$$\Delta S_{system} \geq 0$$

If the system is not isolated and undergoes a quasistatic infinitesimal process in which it absorbs heat $dQ$, then:
$$dS=\frac{{đ}Q}{T} \Leftrightarrow TdS={đ}Q$$

### Day 2

Review of last class's concepts:

- ${đ}Q=dE+{đ}W$
  - We can decompose the heat into kinetic and potential energy.
- Definition of change of entropy:
  - if the system is isolated and undergoes an infinitesimal quasistatic process
    - $dS=\frac{{đ}Q}{T}$
  - if the system is isolated and we go from one macroscopic state to another:
    - $\Delta S \geq 0$
    - **Thermally Isolated**, $\Delta S$ cannot be less than $0$
  - called the: Principle of the Increase of Entropy
  - Clausius's Statement:
    - "Heat cannot, by itself, pass from a colder to a hotter body"

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
\Delta S &= -\frac{\dbar Q}{T_A}+\frac{\dbar Q}{T_B} \\
&= \dbar Q\left(\frac{1}{T_B}-\frac{1}{T_A}\right) < 0
\end{aligned}$$

  - Kelvin's Statement:
    - "A process whose **only** effect is the **complete** conversion of Heat (energy) into Work cannot occur."
      - ${đ}Q\rightarrow {đ}W$
      - $dS = -\frac{{đ}Q}{T} < 0$
    - This is why engines cannot have $100$ % efficiency

!> Statements in Thermodynamics must be precise. Lacking keywords can invalidate the entire statement.

##### The Third Law

The limiting property of entropy:

?> As the temperature of a system approaches absolute zero, all processes cease and the entropy of the system approaches a minimum value.  $T\rightarrow 0_+,\qquad S\rightarrow S_0 = 0$

We'll discuss this later in the course.

#### Review of Math in Thermodynamics

##### Rules of total derivatives

Consider two single variable functions: $f(x),\ g(x)$

###### Linearity

$$\frac{d}{dx}(f(x)+g(x))=\frac{d}{dx}f(x)+\frac{d}{dx}g(x)$$

###### Product rule

$$\frac{d}{dx}(f(x)\cdot g(x))=f(x)\frac{d}{dx}g(x)+g(x)\frac{d}{dx}f(x)$$
$$\frac{d}{dx}\left(\frac{f(x)}{g(x)}\right)=\left(f(x)\frac{d}{dx}g(x)-g(x)\frac{d}{dx}f(x)\right)\cdot\left(\frac{1}{g(x)^2}\right)$$

###### Chain rule

$$f(U(x))$$
$$\frac{df}{dx}=\frac{df}{du}\cdot\frac{du}{dx}$$

##### Rules for Partial derivatives

Let $E$ be the energy of the system.
$$E=E(T,V) = E(p, V) = E(p, T)$$

Any two thermodynamic variables are independent. However, if you look at three parameters together, you cannot change them independently of each other.

Consider the multivariable function $f(x,y)$:

$$\left(\frac{\partial f}{\partial x}\right)_y$$

- Describes the change of $f$ as the result of the change of $x$ while keeping $y$ fixed/constant

!> Always write the specific parameters that are held constant.

###### Clauriet's Theorem

$$\left(\frac{\partial}{\partial y}\right)_x \left(\frac{\partial f}{\partial x}\right)_y = \frac{\partial^2 f}{\partial x\partial y} = \frac{\partial^2 f}{\partial y\partial x} = \left(\frac{\partial}{\partial x}\right)_y \left(\frac{\partial f}{\partial y}\right)_x$$

We use this to derive [Maxwell's Relations].

###### Reciprocal Rule

$f(x,y)=0$

$$df=\left(\frac{\partial f}{\partial x}\right)_y dx + \left(\frac{\partial f}{\partial y}\right)_x dy$$
Consider $df=0$ because $f(x,y)=0$:
$$0=\left(\frac{\partial f}{\partial x}\right)_y dx + \left(\frac{\partial f}{\partial y}\right)_x dy$$
$$\left(\frac{\partial f}{\partial x}\right)_y dx = - \left(\frac{\partial f}{\partial y}\right)_x dy$$
$$\left(\frac{dx}{dy}\right) = - \frac{ \left(\frac{\partial f}{\partial y}\right)_x}{\left(\frac{\partial f}{\partial x}\right)_y}$$

We can rewrite: $f(x,y)=0$ as $x(f,y)$ or $y(f,x)$ which means the left-hand side should really be partial derivatives

$$\left(\frac{\partial x}{\partial y}\right)_f = - \frac{ \left(\frac{\partial f}{\partial y}\right)_x}{\left(\frac{\partial f}{\partial x}\right)_y}$$

Repeat the same process and we obtain the following:

$$\left(\frac{\partial y}{\partial x}\right)_f = - \frac{ \left(\frac{\partial f}{\partial x}\right)_y}{\left(\frac{\partial f}{\partial y}\right)_x}$$

Which shows us that they're inversely related to each other:

$$\left(\frac{\partial x}{\partial y}\right)_f = \frac{1}{\left(\frac{\partial x}{\partial y}\right)_f}$$

###### Cyclic Rule:

$f(x,y,z)=0$

$$\left(\frac{\partial x}{\partial y}\right)_z \left(\frac{\partial z}{\partial x}\right)_y \left(\frac{\partial y}{\partial z}\right)_x = -1$$

Proving this rule is the same as the Reciprocal Rule.
- $df(x,y,z)=0$
  - $df = \left(\frac{\partial f}{\partial x}\right)_{y,z} dx + \left(\frac{\partial f}{\partial y}\right)_{x,z} dy + \left(\frac{\partial f}{\partial z}\right)_{x,y} dz$
- treat $z$ constant
  - $df = 0 = dz$
  - $\left(\frac{\partial x}{\partial y}\right)_z = - \frac{\left(\frac{\partial f}{\partial y}\right)_{x,z}}{\left(\frac{\partial f}{\partial x}\right)_{y,z}}$
- treat $x$ constant
  - $df = 0 = dx$
  - $\left(\frac{\partial y}{\partial z}\right)_x = - \frac{\left(\frac{\partial f}{\partial z}\right)_{x,y}}{\left(\frac{\partial f}{\partial y}\right)_{x,z}}$
- treat $y$ constant
  - $df = 0 = dy$
  - $\left(\frac{\partial z}{\partial x}\right)_y = - \frac{\left(\frac{\partial f}{\partial x}\right)_{y,z}}{\left(\frac{\partial f}{\partial z}\right)_{x,y}}$

$$\left(\frac{\partial x}{\partial y}\right)_z \left(\frac{\partial z}{\partial x}\right)_y \left(\frac{\partial y}{\partial z}\right)_x = -1$$

### Day 3

We're going to use the math tools from the previous class to look at:
- Van der Waals gas
- Volumetric compressibility

Simple Application of Macroscopic Thermodynamics (page 152-200)

#### Van der Waals gas

$$p=\frac{nRT}{V-nb}-a\frac{n^2}{V^2}$$

- $V$ is the total volume
- $nb$ is a correct term to subtract the volume occupied by the molecules

##### Isothermal compressibility: $K_t$

$$K_t\equiv -\frac{1}{V}\left(\frac{\partial V}{\partial p}\right)_T$$

- normalized with respect to the volume

##### Isobaric Volumetric thermal expansion coefficient

$$\alpha \equiv \frac{1}{V}\left(\frac{\partial V}{\partial T}\right)_p$$


$$P=p(V,T)$$
$$P=p(V,T)=\frac{nRT}{V-nb}-a\frac{n^2}{V^2}$$

$$\left(\frac{\partial p}{\partial T}\right)_V = \frac{nR}{V-nb}$$
$$\left(\frac{\partial p}{\partial V}\right)_T = -\frac{nRT}{(V-nb)^2} + 2\frac{an^2}{V^3}$$

Using Reciprocal Rule:
$$K_t\equiv -\frac{1}{V}\left(\frac{\partial V}{\partial p}\right)_T = -\frac{1}{V}\frac{1}{\frac{nR}{V-nb}} = -\frac{1}{V}\frac{V-nb}{nr} $$

Using the Cyclic Rule:
$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
\alpha &= \frac{1}{V}\left(\frac{\partial V}{\partial T}\right)_p \\
&= \frac{1}{V} \left( -\left(\frac{\partial T}{\partial p}\right)_V \left(\frac{\partial p}{\partial V}\right)_T \right)^{-1} \\
&= -\frac{1}{V} \left( \left(\frac{V-nb}{nr}\right) \left(-\frac{nRT}{(V-nb)^2} + 2\frac{an^2}{V^3}\right) \right)^{-1}
\end{aligned}$$

#### Properties of Ideal Gas

Equation of State:
$$pV=nRT$$

For an ideal gas, we can take the following statement:
$E=E(T,V)$ and show that $E$ only depends on $T$: $E=E(T)$ which implies
$$\left(\frac{\partial E}{ \partial V}\right)_T \equiv 0$$

First, we take the total derivative:

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
dE &= dE(T,V) \\
&=\left(\frac{\partial E}{ \partial T}\right)_V dT + \left(\frac{\partial E}{ \partial V}\right)_T dV
\end{aligned}$$

Then also consider the First Law of Thermo:

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
TdS &= dE + pdV \\
dS &= \frac{1}{T}dE + \frac{p}{T}dV
\end{aligned}$$

Note that because we can write the differential of entropy as a total derivative, this tells us that $dS$ is an exact differential, which means we can write:
$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
S &= S(E,V) \\
 &= \left(\frac{\partial S}{\partial E}\right)_V dE + \left(\frac{\partial S}{\partial V}\right)_E dV
\end{aligned}$$

Because there is only one way to write the total derivative, we know the coefficients for the differntials are equal to the partial derivatives stated above:

$$\frac{1}{T} = \left(\frac{\partial S}{\partial E}\right)_V$$

- Which is the definition of temperature in macroscopic Thermodynamics

$$\frac{p}{T} = \left(\frac{\partial S}{\partial V}\right)_E$$

- Which is the definition of temperature without knowing Microscopic details

Also recall that with mixed partial derivatives, the order of operations doesn't matter (Clauriet's Theorem):

$$\frac{\partial ^2 S}{\partial V \partial E} = \frac{\partial ^2 S}{\partial E \partial V}$$

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
\mpder{S}{V}{E} &= \wrap{\pder{}{V}}{E} \wrap{\pder{S}{E}}{V} \\
\mpder{S}{E}{V} &= \wrap{\pder{}{E}}{V} \wrap{\pder{S}{V}}{E}
\end{aligned}$$

---

$$\newcommand\dbar{{đ}}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}
\begin{aligned}
dS &= \frac{1}{T}dE + \frac{p}{T}dV \\
dE &= \wrap{\pder{E}{T}}{V} dT + \wrap{\pder{E}{V}}{T} dV \\
\\
dS &= \frac{1}{T} \left( \wrap{\pder{E}{T}}{V} dT + \wrap{\pder{E}{V}}{T} dV \right) + \frac{p}{T}dV \\
&= \frac{1}{T}\wrap{\pder{E}{T}}{V} dT + \left(\frac{1}{T}\wrap{\pder{E}{V}}{T} + \frac{p}{T}\right)dV \\
\\
dS &= \wrap{\pder{S}{T}}{V} dT + \wrap{\pder{S}{V}}{T} dV \\
\\
\\
\wrap{\pder{S}{T}}{V} &= \frac{1}{T} \wrap{\pder{E}{T}}{V} \\
\wrap{\pder{S}{V}}{T} &= \left( \frac{1}{T} \wrap{\pder{E}{V}}{T} + \frac{p}{T} \right)
\end{aligned}$$

Then:

$$\newcommand\dbar{đ}
\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\newcommand\pdersq[2]{\frac{\partial^2 #1}{\partial {#2}^2}}
\newcommand\mpder[3]{\frac{{\partial}^2 #1}{{\partial} #2 {\partial} #3}}
\begin{aligned}
\wrap{\pder{}{V}}{T} \wrap{\pder{S}{T}}{V} &\equiv \wrap{\pder{}{T}}{V} \wrap{\pder{S}{V}}{T} \\
\frac{1}{T} \wrap{\mpder{E}{V}{T}}{} &= \wrap{\pder{}{T}}{V} \left[\frac{1}{T}\wrap{\pder{E}{V}}{T} + \frac{p}{T}\right] \\
\frac{1}{T} \wrap{\mpder{E}{V}{T}}{} &= \frac{1}{T} \wrap{\mpder{E}{V}{T}}{} + \frac{1}{T^2} \wrap{\pder{E}{V}}{T} \\
0 &= \frac{1}{T^2} \wrap{\pder{E}{V}}{T}
\end{aligned}$$
