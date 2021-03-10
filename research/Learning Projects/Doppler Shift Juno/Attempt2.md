LaTeX writeup: [[File:Juno_Attempt2_Solution.pdf]]

## Abstract
This approach attempts to model the impact of the Doppler Effect (via gravity) on transmissions from Earth to Jupiter by considering the total effect on a transmission from either planet to flat spacetime. I utilize a series of ratios to describe the total shift to the wavelength of a signal at 3 key points: Earth, L1, and Jupiter. The result is a negligible effect (total blue shift by a factor of $1\times10^{-8}$) which is both expected and surprising.

## Problem Setup
### Problem Statement
Does the curvature of spacetime, due to the presence of Earth and Jupiter, effect how a transmission from Earth to the Juno spacecraft would be received? Is this effect significant enough that we design spacecraft to receive a wide band of frequencies or allow variable frequencies for contact?

### Assumptions/Simplifications
Consider an empty universe that only contains Earth and Jupiter. We will then treat this Earth and Jupiter as:

* non-rotating
* spherically symmetric
* and with uniform mass density.

Note that uniform mass density implies the gravitation field about each planet is spherically symmetric. We then define three separate inertial reference frames for the system:

* Earth,
* Jupiter,
* Flat spacetime.

#### Givens
* radius of Earth: $6\times10^{6}\ m$
* mass of Earth: $6\times10^{24}\ kg$
* radius of Jupiter : $7\times10^{7}\ m$
* mass of Jupiter : $2\times10^{24}\ kg$
* distance between Earth and Jupiter: $6\times10^{11}\ m$
* The distances for the L1 Lagrange point between Earth and Jupiter can be found listed [[here](https://www.wolframalpha.com/input/?i=lagrange+point+Earth+and+Jupiter)].

### Goal
We want to find the total gravitational shifting of a transmission from the surface of the Earth to the surface of Jupiter.

1. Calculate the Lagrange point between Earth and Jupiter
2. Calculate the total red shift that occurs as the signal leaves Earth and reaches the Lagrange point
    * Calculate the total blue shift that would occur from a signal originating in flat spacetime to Earth
3. Calculate the total blue shift that would occur as for a signal at the Lagrange point as it reaches Juno
    * Calculate the total blue shift that would occur from a signal originating in flat spacetime to Jupiter

### Diagrams/Figures
This section intentionally left blank at this time.

## Solution
### Applicable Concepts and Laws
#### Lagrange Points
The L1 Lagrange Point, or "Lagrangian Point", is the location directly between two masses where the gravitational attraction from each mass cancels out. The L1 point is located directly on the line between the two masses. We can calculate the L1 point from Earth and Jupiter by using the following formula [[1](https://en.wikipedia.org/wiki/Lagrangian_point#L1)]:
$$ \frac{M_1}{(R-r)^2} = \frac{M_2}{r^2} + \left( \frac{M_1 R}{M_1 + M_2} - r\right) \frac{M_1 + M_2}{R^3}$$


#### Gravitational Doppler Effect
We can describe the ratio of unshifted versus shifted wavelengths due to the Doppler Effect caused by gravity using the following expression [[2](https://en.wikipedia.org/wiki/Gravitational_redshift#Prediction_by_the_equivalence_principle_and_general_relativity)]:
$$\frac{\lambda_\infty}{\lambda_e} = \left(1 - \frac{r_s}{R_e} \right)^{-\frac{1}{2}}$$

* $\lambda_\infty$ is the wavelength in flat spacetime
* $\lambda_e$ is the wavelength measured at the source of emission
* $r_s$ is the Schwarzschild Radius: $2\frac{GM}{c^2}$
  * $G$ is Newton's gravitational constant, $6.67\times10^{11} \frac{m^3}{kg\ s^{-2}}$
  * $M$ is the mass of the massive object (the one that is curving spacetime), in $kg$
  * $c$ is the speed of light, $3\times10^8 \frac{m}{s}$
* $R_e$ is the radial distance at which the photon is emitted

### Derivation of Symbolic Solution
We can derive the expression to describe the total blue shifting a photon would experience being emitted from Earth to Jupiter by using combining the Gravitational Doppler Effect equation for various distances. Consider the first step: we need to express how much total gravitational red-shifting would occur for a photon, being emitted at the surface of the Earth, would experience as travels to flat spacetime. We also need to express the other half of the journey: how much gravitational red-shifting would occur for a photon emitted at the surface of Jupiter as it travels to flat spacetime. This naturally leads to the simple substitutions of the components for each planet in for $\lambda_e$:

\begin{equation} \label{eq1}
  \frac{\lambda_\infty}{\lambda_e} \mapsto \ \frac{\lambda_\infty}{\lambda_E}
\end{equation}
\begin{equation} \label{eq2}
  \frac{\lambda_\infty}{\lambda_e} \mapsto \ \frac{\lambda_\infty}{\lambda_J}
\end{equation}

Now, we could solve both Equations \ref{eq1} and \ref{eq2} for $\lambda_\infty$ and equate the two, but this would simply show us the Doppler Effect from a photon leaving Earth, reaching flat spacetime, and then diving down to Jupiter (or vice versa). This is not initially very useful or interesting, but does make a good sanity check point on the reasonableness of this approach. Now, if we similarly substitute in the L1 parameters and write the ratio in terms of:

\begin{equation} \label{eq3}
  \frac{\lambda_\infty}{\lambda_e} \mapsto \ \frac{\lambda_\infty}{\lambda_{L1_E}}
\end{equation}
\begin{equation} \label{eq4}
  \frac{\lambda_\infty}{\lambda_e} \mapsto \ \frac{\lambda_\infty}{\lambda_{L1_J}}
\end{equation}

We have a more useful common point between Earth and Jupiter we can discuss. Let us combine Equations \ref{eq1} and \ref{eq3} and Equations \ref{eq2} and \ref{eq4}, such that we have a way to discuss the amount of redshift from Earth to the L1 Lagrange Point and the amount of blueshift from the L1 Lagrange Point to Jupiter.

\begin{equation} \label{eq5}
  \frac{\frac{\lambda_\infty}{\lambda_E}}{\frac{\lambda_\infty}{\lambda_{L1_E}}} = \frac{\lambda_{L1_E}}{\lambda_E}
\end{equation}
\begin{equation} \label{eq6}
  \frac{\frac{\lambda_\infty}{\lambda_{L1_J}}}{\frac{\lambda_\infty}{\lambda_J}} = \frac{\lambda_J}{\lambda_{L1_J}}
\end{equation}

Due note the difference in Equations \ref{eq5} and \ref{eq6}. We can now solve both equations, \ref{eq5} for $\lambda_{L1_E}$ and \ref{eq6} for $\lambda_J$. We will then substitute in Equation \ref{eq5} for the $\lambda_{L1_J}$ term in Equation \ref{eq6}.

\begin{align*}
  \frac{\lambda_{L1_E}}{\lambda_E} &= \left(1 - \frac{r_{s_E}}{R_{L1_E}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_E}}{R_E} \right)^{-\frac{1}{2}}\\
  \lambda_{L1_E} &= \lambda_E\left(1 - \frac{r_{s_E}}{R_{L1_E}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_E}}{R_E} \right)^{-\frac{1}{2}}
\end{align*}
\begin{equation} \label{eq7}
\begin{split}
  \frac{\lambda_J}{\lambda_{L1_J}} &= \left(1 - \frac{r_{s_J}}{R_{J}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_J}}{R_{L1_J}} \right)^{-\frac{1}{2}}\\
  \lambda_J &= \lambda_{L1_J}\left(1 - \frac{r_{s_J}}{R_{J}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_J}}{R_{L1_J}} \right)^{-\frac{1}{2}}\\
  \lambda_J &= \lambda_E\left(1 - \frac{r_{s_E}}{R_{L1_E}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_E}}{R_E} \right)^{-\frac{1}{2}}\left(1 - \frac{r_{s_J}}{R_{J}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_J}}{R_{L1_J}} \right)^{-\frac{1}{2}}\\
  \frac{\lambda_J}{\lambda_E} &= \left(1 - \frac{r_{s_E}}{R_{L1_E}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_E}}{R_E} \right)^{-\frac{1}{2}}\left(1 - \frac{r_{s_J}}{R_{J}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_J}}{R_{L1_J}} \right)^{-\frac{1}{2}}
\end{split}
\end{equation}

### Numeric Solution
The L1 Lagrange point for Earth and Jupiter, as calculated by [WolframAlpha](https://www.wolframalpha.com/input/?i=lagrange+point+earth+and+jupiter):

* $L1_E$ is $6.4\times10^{10}\ m$ from Earth
* $L1_J$ is $5.9\times10^{11}\ m$ from Jupiter

Recall we symbolically solved Equation \ref{eq7} to describe the ratio that a signal from Earth would be gravitationally red/blue shifted:
\begin{equation*}
  \frac{\lambda_J}{\lambda_E} = \left(1 - \frac{r_{s_E}}{R_{L1_E}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_E}}{R_E} \right)^{-\frac{1}{2}}\left(1 - \frac{r_{s_J}}{R_{J}} \right)^{\frac{1}{2}} \left(1 - \frac{r_{s_J}}{R_{L1_J}} \right)^{-\frac{1}{2}}
\end{equation*}

Evaluating with the following values:

\begin{align*} \label{given_numeric}
  \frac{r_{s_E}}{R_{E}} &= \frac{2( 6.67408\times10^{-11}\ \frac{m^3}{kg\ s^{2}})(6\times10^{24}\ kg)(6\times10^{6}\ m^{-1})}{(3\times10^{8}\ \frac{m}{s})^2}\\
  \frac{r_{s_E}}{R_{L1_E}} &= \frac{2( 6.67408\times10^{-11}\ \frac{m^3}{kg\ s^{2}})(6\times10^{24}\ kg)(6\times10^{10}\ m^{-1})}{(3\times10^{8}\ \frac{m}{s})^2}\\
  \frac{r_{s_J}}{R_{J}} &= \frac{2( 6.67408\times10^{-11}\ \frac{m^3}{kg\ s^{2}})(2\times10^{27}\ kg)(7\times10^{7}\ m^{-1})}{(3\times10^{8}\ \frac{m}{s})^2}\\
  \frac{r_{s_J}}{R_{L1_J}} &= \frac{2( 6.67408\times10^{-11}\ \frac{m^3}{kg\ s^{2}})(2\times10^{27}\ kg)(6\times10^{11}\ m^{-1})}{(3\times10^{8}\ \frac{m}{s})^2}
\end{align*}

We obtain [[3](https://www.wolframalpha.com/input/?i=x%3D%28sqrt%281-a%2Fb%29%2Fsqrt%281-a%2Fc%29%29%28sqrt%281-d%2Ff%29%2Fsqrt%281-d%2Fg%29%29%3B+a%3D%287*10%5E-11%29%286*10%5E24%29%2F%289*10%5E16%29%3B+b%3D6*10%5E10+%3B+c+%3D6*10%5E6%3B+d%3D%287*10%5E-11%29%282*10%5E27%29%2F%289*10%5E16%29%3B+f%3D7*10%5E7%3B+g%3D6*10%5E11)]:

\begin{equation*}
  \frac{\lambda_J}{\lambda_E} = \sqrt{\frac{24299999459998110000042}{24299999981037000000049}} = 0.999999989\ldots
\end{equation*}

Which is equivalent to a relative blue shift of $1\times10^{-8}$.

## Sense Making
### Unit Check
Checks out! (add later)

### Physicality
As we discussed during the derivation of Equations \eqref{eq1} and \eqref{eq2}, we started with the simplest approach: relate the Doppler Effect from gravity by sending the signal from Earth to flat spacetime and back to Jupiter. We then added a step of complexity by considering the Lagrange point between them, almost like:

$$Earth \rightarrow L1 \rightarrow Flat\ Spacetime \rightarrow L1 \rightarrow Jupiter$$

Except with Equations \eqref{eq3} and \eqref{eq4}, we just wanted an expression that we could combine with Equations \eqref{eq1} and \eqref{eq2}, respectively, such that we could describe the effect form the surface of the plane to L1 (on either half). This was formalized in Equations \eqref{eq5} and \eqref{eq6}. From this point, it was simply a matter of substituting in the red shift form leaving Earth (Equation \ref{eq5}) into $\lambda_{L1_J}$ in Equation \eqref{eq6}.

Our result is a dimensionless ratio, which we expect, where a value less than 1 corresponds to a blue shift (shorter wavelength, higher frequency) and a value greater than 1 corresponds to a red shift (longer wavelength, smaller frequency).

We can note that in the final equation, Equation \eqref{eq7}, the ratio depends on values that are all constant. We can also see from inspecting the general form of the equation that this Doppler Effect being caused by gravity is only going to have a noticeable effect when $\frac{1}{R_e} < 1$ and not $\frac{1}{R_e} \ll 1$. This is to say, the receiver or sender of a transmission only needs to begin to account for this effect when they are able to be significantly closer to the Schwarzschild radius of a massive object.

### Numeric Reasonableness
The measured total effect of the shifting for a signal from Earth to Jupiter (not Juno) is by a factor of $1\times10^{-8}$. This value does match expectations, as if this were a noticeable effect for objects of size and mass equivalent to the Earth and Jupiter, there would be material discussing this situation as an example.

This finding is interesting, however, as I did expect a stronger effect due to the prevalence of accounting for time dilation for GPS satellites. Having to account for clocks ticking at different rates (with respect to flat spacetime), I expected the Doppler Effect to  show a similar problem with the accuracy of frequencies/wavelengths of transmissions from Earth to our intra-solar spacecraft.
