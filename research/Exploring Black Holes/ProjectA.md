# Project A

## Query 1
!>**TODO::** Add Prompt

Consider two atomic clocks, one inside a GPS satellite and one on the surface of the Earth. Let us assume that both clocks have no polar offset from the equator such that we can describe each clock’s events with the Schwarzschild metric in polar coordinates. Recall that this equation takes the form:

$$ d\tau^2 = \left(1-\frac{2M}{r}\right)dt^2 - \left(1-\frac{2M}{r}\right)^{-1} dr^2 - r^2 d\phi^2$$

Assume the radial distance is not changing, $dr=0$:

$$ d\tau^2 = \left(1-\frac{2M}{r}\right)dt^2 - r^2 d\phi^2$$

Divide both sides by the rate of change for far-away time:

$$\left(\frac{d\tau}{dt}\right)^2 = \left(1-\frac{2M}{r}\right) - \left(\frac{rd\phi}{dt}\right)^2$$

Note that the final term is a constant radius with changing azimuthal angle with respect to time, we can write this as tangential velocity:

$$\left(\frac{d\tau}{dt}\right)^2 = \left(1-\frac{2M}{r}\right) - v^2$$

Let us now define this equation in terms of our two (synchronized) atomic clocks:

$$\begin{aligned}
\left(\frac{d\tau}{dt_{satellite}} \right)^2 &= \left(1-\frac{2M}{r_{satellite}} \right) - {v_{satellite}}^2 \\
\left(\frac{d\tau}{dt_{Earth}} \right)^2 &= \left(1-\frac{2M}{r_{Earth}} \right) - {v_{Earth}}^2
\end{aligned}$$

?> **Note:** $d\tau$, the interval between wristwatch ticks, has no subscript for each equation. This is because we are talking about two identical clocks, and in the same free-float frame, they would tick at the same rate.

Using these two equations, let us discuss the change in time between the two separate free-float frames as a ratio:

$$\left(\frac{dt_{satellite}}{dt_{Earth}} \right)^2 = \frac{\left(1-\frac{2M}{r_{satellite}} \right) - {v_{satellite}}^2}{\left(1-\frac{2M}{r_{Earth}} \right) - {v_{Earth}}^2}$$

Next, let us consider how this difference looks when we assume that both clocks are stationary, $v_{satellite}=v_{Earth}=0$ and take the square root of both sides.

$$\begin{aligned}
\left(\frac{dt_{satellite}}{dt_{Earth}} \right)^2 &= \frac{\left(1-\frac{2M}{r_{satellite}} \right)}{\left(1-\frac{2M}{r_{Earth}} \right)} \\
\\
\frac{dt_{satellite}}{dt_{Earth}} &= \pm \sqrt{\frac{1-\frac{2M}{r_{satellite}}}{1-\frac{2M}{r_{Earth}}}}
\end{aligned}$$

?> **Note:**  The order of events is important here. In a simple view, let us consider the time of the first event, $t_1$, which corresponds to the satellite transmitting its signal. We then define $t_2$ to be when the clock on the Earth receives this signal. Regardless of free-float reference frame, all observers agree that the order of events matters: the clock on the Earth cannot receive a signal that has not been transmitted, and all observers agree that $t_1$ occurs before $t_2$.

Because of this fact, we require that the time separation between events be positive such that causality is obeyed; therefore, we discard the negative solution as it does not match the physical properties of this system. This leaves us with:

$$\frac{dt_{satellite}}{dt_{Earth}} = \sqrt{\frac{1-\frac{2M}{r_{satellite}}}{1-\frac{2M}{r_{Earth}}}}$$

Note that $2M$ is another representation for the Schwarzschild radius, which can also be written as: $2\left(G\cdot\frac{m}{c^2}\right)$, where:
- $G$ is Newton’s universal constant of gravity,
- $c$ is the speed of light,
- $m$ is the mass of the object in kilograms.

?> **Note:** If we only are considering the magnitudes for Earth’s values, we can see how small $2M$ really is:
?> $2M_{Earth} = 2\frac{10^{-11}}{10^{16}\cdot 10^{24}} = \frac{10^{24}}{10^{27}} = 10^{-3}$
?> Also note that this value is in the numerator, therefore: $\frac{10^{-3}}{10^6}\rightarrow 10^9, 10^{-9}\ll 1$

?> Recall the binomial power series approximation: $$(1+z)^p = 1 + pz + \frac{p(p-1)z^2}{2!} + ...$$
  (1+z)^p=1+pz/1!+(p(p-1) z^2)/2!+⋯≈1+pz,|z|≪1 and |pz|≪1

Convince yourself that if $2M/r_Earth$ is $\ll 1$, that 2M/r_satellite would be even smaller. Also note that the interior of this approximation is dimensionless which is a necessary condition to approximate by power series. Applying the power series approximation to the first order, we obtain the following:
  (dt_satellite)/(dt_Earth) = (1 - 2M/r_satellite)^(1/2) (1 - 2M/r_Earth)^(-1/2)
  (dt_satellite)/(dt_Earth) ≈ (1 + (1/2)2M/r_satellite)(1 + (-1/2)2M/r_Earth)
  (dt_satellite)/(dt_Earth) ≈ (1 + M/r_satellite)(1 - M/r_Earth)


  (dt_satellite)/(dt_Earth) ≈ 1 + M/r_satellite - M/r_Earth - (M/r_Earth)(M/r_satellite)    (Eq I.4)
</div></div>
## Query 2
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
Recall that we showed M/r_Earth and M/r_satellite were significantly smaller than 1. Note that their product will result in a value that has an approximate order of magnitude of 10^(-18) (assuming that M/r_satellite ≥ M/r_Earth), and therefore we can exclude this term from our approximation without introducing much error:

  (dt_satellite)/(dt_Earth) ≈ 1 + M/r_satellite - M/r_Earth    (Eq II.1)

</div></div>
## Query 3
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
Using Equation II.1, we can calculate this numerical approximation by substituting in values for M, r_satellite, and r_Earth: ([https://www.wolframalpha.com/input/?i=%286.6726*10%5E-11%29%2F%282.99792458*10%5E8%29%5E2*%285.9742*10%5E24%29 1])
*  r_satellite=26.6×10^6  m,
*  r_Earth=6.3710×10^6  m
*  M_Earth=((6.6726×10^(-11)  m^3/(kg⋅s^2 ))/(2.99792458×10^8  m/s)^2 ⋅(5.9742×10^24  kg)/1)=4.4×10^(-3)  m

Substituting into Equation II.1: ([https://www.wolframalpha.com/input/?i=1%2B%28%286.6726*10%5E-11%29%2F%282.99792458*10%5E8%29%5E2*%285.9742*10%5E24%29%29%281%2F%2826.6*10%5E6%29-1%2F%286.3710*10%5E6%29%29 2])
  (dt_satellite)/(dt_Earth) ≈ 1 + (4.4×10^(-3) m)(1/(26.6×10^6 m) - 1/(6.3710×10^6 m))


  (dt_satellite)/(dt_Earth ) ≈ 0.9999999994

From this ratio being less than 1, we can see that means the interval between far-away time ticks for the satellite is less than the interval for the clock on the Earth. From an outside observer (in a free-float frame), they would observe, ever so slightly, time passing slower on the surface of the Earth when compared to the Satellite.
</div></div>
## Query 4
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
Due note that the approximated value we found in Query 3 means that the period between (far-away) time ticks for the satellite is 1×10^(-9)  s faster than the Earth. We will now explore just how desynchronized the two clocks will be after just 24 hours.
</div></div>
## Query 5
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Solution </strong>
</div></div>
## Query 6
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Solution </strong>
</div></div>
## Query 7
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Solution </strong>
</div></div>
## Query 8
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Solution </strong>
</div></div>
## Query 9
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Solution </strong>
</div></div>
## Query 10
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Prompt:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Prompt </strong>
</div></div>
<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">
<div style="font-weight:bold;line-height:1.6;">Solution:</div>
<div class="mw-collapsible-content">
<strong> TODO:: Add Solution </strong>
</div></div>
