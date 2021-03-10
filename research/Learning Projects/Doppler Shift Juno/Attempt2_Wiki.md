LaTeX writeup: [[Media:Juno_Attempt2_Solution.pdf|Juno Attempt 2]]

== Abstract ==

This approach attempts to model the impact of the Doppler Effect (via gravity) on transmissions from Earth to Jupiter by considering the total effect on a transmission from either planet to flat spacetime. I utilize a series of ratios to describe the total shift to the wavelength of a signal at 3 key points: Earth, L1, and Jupiter. The result is a negligible effect (total blue shift by a factor of <math display="inline">1\times10^{-8}</math>) which is both expected and surprising.
<br /><br />

== Problem Setup ==

=== Problem Statement ===

Does the curvature of spacetime, due to the presence of Earth and Jupiter, effect how a transmission from Earth to the Juno spacecraft would be received? Is this effect significant enough that we design spacecraft to receive a wide band of frequencies or allow variable frequencies for contact?
<br /><br />

=== Assumptions/Simplifications ===

Consider an empty universe that only contains Earth and Jupiter. We will then treat this Earth and Jupiter as:

* non-rotating
* spherically symmetric
* and with uniform mass density.
<br /><br />

Note that uniform mass density implies the gravitation field about each planet is spherically symmetric. We then define three separate inertial reference frames for the system:

* Earth,
* Jupiter,
* Flat spacetime.
<br /><br />

==== Givens ====

* radius of Earth: <math display="inline">6\times10^{6}\ m</math>
* mass of Earth: <math display="inline">6\times10^{24}\ kg</math>
* radius of Jupiter : <math display="inline">7\times10^{7}\ m</math>
* mass of Jupiter : <math display="inline">2\times10^{24}\ kg</math>
* distance between Earth and Jupiter: <math display="inline">6\times10^{11}\ m</math>
* The distances for the L1 Lagrange point between Earth and Jupiter can be found listed [https://www.wolframalpha.com/input/?i=lagrange+point+Earth+and+Jupiter|here].
<br /><br />

=== Goal ===

We want to find the total gravitational shifting of a transmission from the surface of the Earth to the surface of Jupiter.

# Calculate the Lagrange point between Earth and Jupiter
# Calculate the total red shift that occurs as the signal leaves Earth and reaches the Lagrange point
#* Calculate the total blue shift that would occur from a signal originating in flat spacetime to Earth
# Calculate the total blue shift that would occur as for a signal at the Lagrange point as it reaches Juno
#* Calculate the total blue shift that would occur from a signal originating in flat spacetime to Jupiter
<br /><br />

=== Diagrams/Figures ===

This section intentionally left blank at this time.
<br /><br />

== Solution ==

=== Applicable Concepts and Laws ===

==== Lagrange Points ====

The L1 Lagrange Point, or “Lagrangian Point”, is the location directly between two masses where the gravitational attraction from each mass cancels out. The L1 point is located directly on the line between the two masses. We can calculate the L1 point from Earth and Jupiter by using the following formula [<nowiki/>[https://en.wikipedia.org/wiki/Lagrangian_point#L1 1]]:
<br /><br />

<math display="block"> \frac{M_1}{(R-r)^2} = \frac{M_2}{r^2} + \left( \frac{M_1 R}{M_1 + M_2} - r\right) \frac{M_1 + M_2}{R^3}</math>
<br /><br />

==== Gravitational Doppler Effect ====

We can describe the ratio of unshifted versus shifted wavelengths due to the Doppler Effect caused by gravity using the following expression [<nowiki/>[https://en.wikipedia.org/wiki/Gravitational_redshift#Prediction_by_the_equivalence_principle_and_general_relativity 2]]:
<br /><br />

<math display="block">\frac{\lambda_\infty}{\lambda_e} = \left(1 - \frac{r_s}{R_e} \right)^{-\frac{1}{2}}</math>
* <math display="inline">\lambda_\infty</math> is the wavelength in flat spacetime
* <math display="inline">\lambda_e</math> is the wavelength measured at the source of emission
* <math display="inline">r_s</math> is the Schwarzschild Radius: <math display="inline">2\frac{GM}{c^2}</math>
** <math display="inline">G</math> is Newton’s gravitational constant, <math display="inline">6.67\times10^{11} \frac{m^3}{kg\ s^{-2}}</math>
** <math display="inline">M</math> is the mass of the massive object (the one that is curving spacetime), in <math display="inline">kg</math>
** <math display="inline">c</math> is the speed of light, <math display="inline">3\times10^8 \frac{m}{s}</math>
* <math display="inline">R_e</math> is the radial distance at which the photon is emitted
<br /><br />

=== Derivation of Symbolic Solution ===

We can derive the expression to describe the total blue shifting a photon would experience being emitted from Earth to Jupiter by using combining the Gravitational Doppler Effect equation for various distances. Consider the first step: we need to express how much total gravitational red-shifting would occur for a photon, being emitted at the surface of the Earth, would experience as travels to flat spacetime. We also need to express the other half of the journey: how much gravitational red-shifting would occur for a photon emitted at the surface of Jupiter as it travels to flat spacetime. This naturally leads to the simple substitutions of the components for each planet in for <math display="inline">\lambda_e</math>:
<br /><br />

Now, we could solve both Equations  and  for <math display="inline">\lambda_\infty</math> and equate the two, but this would simply show us the Doppler Effect from a photon leaving Earth, reaching flat spacetime, and then diving down to Jupiter (or vice versa). This is not initially very useful or interesting, but does make a good sanity check point on the reasonableness of this approach. Now, if we similarly substitute in the L1 parameters and write the ratio in terms of:
<br /><br />

We have a more useful common point between Earth and Jupiter we can discuss. Let us combine Equations  and  and Equations  and , such that we have a way to discuss the amount of redshift from Earth to the L1 Lagrange Point and the amount of blueshift from the L1 Lagrange Point to Jupiter.
<br /><br />

Due note the difference in Equations  and . We can now solve both equations,  for <math display="inline">\lambda_{L1_E}</math> and  for <math display="inline">\lambda_J</math>. We will then substitute in Equation  for the <math display="inline">\lambda_{L1_J}</math> term in Equation .
<br /><br />

=== Numeric Solution ===

The L1 Lagrange point for Earth and Jupiter, as calculated by [https://www.wolframalpha.com/input/?i=lagrange+point+earth+and+jupiter WolframAlpha]:

* <math display="inline">L1_E</math> is <math display="inline">6.4\times10^{10}\ m</math> from Earth
* <math display="inline">L1_J</math> is <math display="inline">5.9\times10^{11}\ m</math> from Jupiter
<br /><br />

Recall we symbolically solved Equation  to describe the ratio that a signal from Earth would be gravitationally red/blue shifted:
<br /><br />

Evaluating with the following values:
<br /><br />

We obtain [<nowiki/>[https://www.wolframalpha.com/input/?i=x%3D%28sqrt%281-a%2Fb%29%2Fsqrt%281-a%2Fc%29%29%28sqrt%281-d%2Ff%29%2Fsqrt%281-d%2Fg%29%29%3B+a%3D%287*10%5E-11%29%286*10%5E24%29%2F%289*10%5E16%29%3B+b%3D6*10%5E10+%3B+c+%3D6*10%5E6%3B+d%3D%287*10%5E-11%29%282*10%5E27%29%2F%289*10%5E16%29%3B+f%3D7*10%5E7%3B+g%3D6*10%5E11 3]]:
<br /><br />

Which is equivalent to a relative blue shift of <math display="inline">1\times10^{-8}</math>.
<br /><br />

== Sense Making ==

=== Unit Check ===

Checks out! (add later)
<br /><br />

=== Physicality ===

As we discussed during the derivation of Equations  and , we started with the simplest approach: relate the Doppler Effect from gravity by sending the signal from Earth to flat spacetime and back to Jupiter. We then added a step of complexity by considering the Lagrange point between them, almost like:
<br /><br />

<math display="block">Earth \rightarrow L1 \rightarrow Flat\ Spacetime \rightarrow L1 \rightarrow Jupiter</math>
<br /><br />

Except with Equations  and , we just wanted an expression that we could combine with Equations  and , respectively, such that we could describe the effect form the surface of the plane to L1 (on either half). This was formalized in Equations  and . From this point, it was simply a matter of substituting in the red shift form leaving Earth (Equation ) into <math display="inline">\lambda_{L1_J}</math> in Equation .
<br /><br />

Our result is a dimensionless ratio, which we expect, where a value less than 1 corresponds to a blue shift (shorter wavelength, higher frequency) and a value greater than 1 corresponds to a red shift (longer wavelength, smaller frequency).
<br /><br />

We can note that in the final equation, Equation , the ratio depends on values that are all constant. We can also see from inspecting the general form of the equation that this Doppler Effect being caused by gravity is only going to have a noticeable effect when <math display="inline">\frac{1}{R_e} < 1</math> and not <math display="inline">\frac{1}{R_e} \ll 1</math>. This is to say, the receiver or sender of a transmission only needs to begin to account for this effect when they are able to be significantly closer to the Schwarzschild radius of a massive object.
<br /><br />

=== Numeric Reasonableness ===

The measured total effect of the shifting for a signal from Earth to Jupiter (not Juno) is by a factor of <math display="inline">1\times10^{-8}</math>. This value does match expectations, as if this were a noticeable effect for objects of size and mass equivalent to the Earth and Jupiter, there would be material discussing this situation as an example.
<br /><br />

This finding is interesting, however, as I did expect a stronger effect due to the prevalence of accounting for time dilation for GPS satellites. Having to account for clocks ticking at different rates (with respect to flat spacetime), I expected the Doppler Effect to show a similar problem with the accuracy of frequencies/wavelengths of transmissions from Earth to our intra-solar spacecraft.
<br /><br />
