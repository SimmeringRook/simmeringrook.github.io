# Reference Sheet

In-depth Links:

- Thermodynamic [Systems](/physics/Thermodynamics/Systems.md)
    - Isothermal Compressibility
    - Isobaric Volumetric Expansion Coefficient
    - Specific Heat Capacities
  - Models:
    - [Ideal Gas](/physics/Thermodynamics/IdealGas.md)
    - [Van der Waals](/physics/Thermodynamics/VanderWaalsGas.md)
    - [*Real* Gas](/physics/Thermodynamics/RealGas.md)
- The [Laws of Thermodynamics](/physics/Thermodynamics/ThermoLaws.md)
    1. [The Zeroth Law](/physics/Thermodynamics/ThermoLaws#The-Zeroth.md)
    2. [The First Law](/physics/Thermodynamics/ThermoLaws#The-First.md) (Energy conservation)
    3. [The Second Law](/physics/Thermodynamics/ThermoLaws#The-Second.md) (Entropy Increases)
    3. [The Third Law](/physics/Thermodynamics/ThermoLaws#The-Third.md) (Minimal Entropy)
- Thermodynamic [Processes](/physics/Thermodynamics/Processes.md)
    - [Quasistatic](/physics/Thermodynamics/Processes#Quasistatic.md)
    - [Reversible](/physics/Thermodynamics/Processes#Reversible.md) vs [Irreversible](/physics/Thermodynamics/Processes#Irreversible.md)
    - [Iso and Adia](/physics/Thermodynamics/Processes#Iso-and-Adia.md) Processes

## Overview


| [Thermodynamic Functions](/physics/Thermodynamics/Functions.md) | Internal Energy Parameterization | Describing a Quasistatic Process | Function (mixed Partials) | Partial to Coefficient Relation | Maxwell Relation |
| --- | --- | --- | --- | --- | --- |
| [Identity](/physics/Thermodynamics/Functions#Thermodynamic-Identity.md) | $$E(S,V)$$ | $$dE = T dS - p dV$$ | $$\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}\begin{aligned}\mpder{E}{S}{V}&=\mpder{E}{V}{S}\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned} \wrap{\pder{E}{S}}{V} &= T \\ \wrap{\pder{E}{V}}{S} &= -p\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned}\wrap{\pder{T}{V}}{S} &= -\wrap{\pder{p}{S}}{V}\end{aligned}$$ |
| [Enthalpy](/physics/Thermodynamics/Functions#Enthalpy.md) | $$H(S,p)\equiv E+pV$$ | $$dH = TdS + Vdp$$ | $$\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}\begin{aligned}\mpder{H}{S}{p}&=\mpder{H}{p}{S}\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned} \wrap{\pder{H}{S}}{p} &= T \\ \wrap{\pder{H}{p}}{S} &= V\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned}\wrap{\pder{T}{p}}{S} &= \wrap{\pder{V}{S}}{p}\end{aligned}$$ |
| [Helmholtz](/physics/Thermodynamics/Functions#Helmholtz.md) | $$F(T,V)\equiv E - TS$$ | $$dF = - SdT - pdV$$ | $$\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}\begin{aligned}\mpder{F}{V}{T}&=\mpder{F}{T}{V}\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned} \wrap{\pder{F}{V}}{T} &= -p \\ \wrap{\pder{F}{T}}{V} &= -S\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned}\wrap{\pder{S}{V}}{T} &= \wrap{\pder{p}{T}}{V}\end{aligned}$$ |
| [Gibbs](/physics/Thermodynamics/Functions#Gibbs.md) | $$G(T,p)\equiv E - TS + pV$$ | $$dG = - SdT + Vdp$$ | $$\newcommand\mpder[3]{\frac{\partial^2 #1}{\partial #2 \partial #3}}\begin{aligned}\mpder{G}{T}{p}&=\mpder{G}{p}{T}\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned} \wrap{\pder{G}{T}}{p} &= -S \\ \wrap{\pder{G}{p}}{T} &= V\end{aligned}$$ | $$\newcommand\wrap[2]{\left(#1\right)_{#2}}\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}\begin{aligned}-\wrap{\pder{S}{p}}{T} &= \wrap{\pder{V}{T}}{p}\end{aligned}$$ |

### Homogeneous Substances

#### Specific Heats

$$\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
c_y &= \frac{1}{n}\wrap{\pder{Q}{T}}{y} &\Leftarrow \text{Specific Heat per Mole}\\
c_y &= \frac{1}{m}\wrap{\pder{Q}{T}}{y} &\Leftarrow \text{Specific Heat per gram}\\
\\
\gamma &= \frac{c_p}{c_v} = 1 + \frac{R}{c_v}
\end{aligned}$$

#### Heat Capacities

$$\newcommand\wrap[2]{\left(#1\right)_{#2}}
\newcommand\pder[2]{\frac{\partial #1}{\partial #2}}
\begin{aligned}
C_y &= n c_y = m c_y \Rightarrow C_y = T \wrap{\pder{S}{T}}{y}\\
\\
&C_p - C_V = VT\frac{\alpha^2}{\kappa} = nR
\end{aligned}$$

#### Isothermal compressibility

$$\kappa\equiv -\frac{1}{V}\left(\frac{\partial V}{\partial p}\right)_T$$

#### Volumetric Thermal Expansion Coefficient

$$\alpha \equiv \frac{1}{V}\left(\frac{\partial V}{\partial T}\right)_p$$
