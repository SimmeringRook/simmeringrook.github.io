= Chapter 2: Curving =

## Distances Determine Geometry

The spacetime interval is the “distance” between events

<blockquote>
“Distance” here means not just spatial but also temporal. Its the <strong>Spacetime</strong> distance between events.
</blockquote>
<br />

## Reference Frames are Secondary

* Spacetime geometry exists regardless of reference frame (and even without a frame)
** As such, all frames are equally valid <br />

## Free Float Frames

* Relative accelerations are called “tidal accelerations”
* Reference frame can be as
** tiny as a nucleus
** short as a gamma ray emission
* Schwarzschild coordinates apply to slowly spinning or non-rotating bodies
** We can talk about the Earth and Sun using Schwarzschild coordinates <br />

## The r-coordinate: the Reduced Circumference

* Due to space stretching in the presence of massive objets, we don’t measure radial distances (Euclidean Geometry doesn’t work for spacetime)
** The is especially apparent with black holes
* walk around the shell of constant radius, measuring the Circumference. Divide by <math display="inline">2\pi</math> to obtain.
** Radial distance between shells is <math display="inline">d\sigma</math> which will be greater than the difference from two concentric shells
* We can do this for spherically symmetric objects that are rotating “slow enough”
** angle doesn’t matter
** only depends on <math display="inline">r</math>-coordinate
** density doesn’t have to be uniform
*** change with <math display="inline">r</math> okay; change with <math display="inline">\phi</math> or <math display="inline">\theta</math> is violates symmetry

Schwarzschild Metric describes spacetime external to any <strong>isolated</strong>, slowly rotating, and spherically symmetric body. <br />

## Gravitational Red Shift

* <math display="inline">dt_{shell}</math> time between clock ticks &gt; <math display="inline">dt_{far-away}</math> time between clock ticks <br />

## Mass in Units of Length

* Conversion factor: <math display="block">\frac{G}{c^2}</math> Where:
** G is Gravitational constant: <math display="inline">6.6726\times10^{-11} \frac{m^3}{kg\ s^2}</math>
** c is the speed of light: <math display="inline">2.99792458\times10^{8} \frac{m}{s}</math>

Such that: <math display="block">M_{in\ m} = \frac{G}{c^2}M_{in\ kg}</math> <br />

## Satellite Motion in a Plane

* A satellite is restricted to its plane of motion because of spherical symmetry
** There is nothing to displace or alter it from its plane of motion
** So we only need two coordinates to describe the location of the satellite: <math display="inline">r, \phi</math>

<blockquote>
<strong>??</strong> <br />How do we know if a given distance is a Euclidean or Non-Euclidean distance? E.g. the distance from Earth to Moon?
</blockquote>
<br />

## Metric for Flat Spacetime

* From Ch1, we have the spacetime interval as: <math display="block"> \tau^2 = t^2 - s^2 \\
\sigma^2 = -t^2 + s^2 </math>

Expanding into two dimensions of space:

<math display="block"> s^2 = x^2 + y^2 \\
\tau^2 = t^2 - (x^2 + y^2) = t^2 - x^2 - y^2 \\
\sigma^2 = -t^2 + (x^2 + y^2) = -t^2 + x^2 + y^2
</math>

Changing into spherical coordinates: <math display="block">
(d\tau)^2 = (dt)^2 - (dr)^2 - (rd\phi)^2 \\
(d\sigma)^2 = -(dt)^2 + (dr)^2 + (rd\phi)^2
</math> <br />

## Schwarzschild Metric

We take the [[#metric-for-flat-spacetime|Metric for Flat Spacetime]]:

<math display="block"> (d\tau)^2 = (dt)^2 - (dr)^2 - (rd\phi)^2 </math>

and account for the curvature between two concentric shells:

<math display="block"> (d\tau)^2 = \left(1 - \frac{2M}{r}\right)(dt)^2 - \left(1 - \frac{2M}{r}\right)^{-1}(dr)^2 - (rd\phi)^2 </math>

And then we can describe two events close to one another, where <math display="inline">d\phi</math> is small such that <math display="inline">rd\phi</math> describes an arc length for a straight line. <math display="inline">r</math> is the <math display="inline">r</math>-coordinate which is a Non-Euclidean distance.

<math display="block"> (d\sigma)^2 = -\left(1 - \frac{2M}{r}\right)(dt)^2 + \left(1 - \frac{2M}{r}\right)^{-1}(dr)^2 + (rd\phi)^2 </math> <br />

Sense Making

# The <strong>curvature factor</strong> only depends on <math display="inline">r</math>, not <math display="inline">\phi</math>
#* <math display="inline">\left(1 - \frac{2M}{r}\right)</math>
#* We expect only <math display="inline">r</math> dependence from a spherically symmetric body.
# As <math display="inline">r\rightarrow\infty</math>, curvature factor approaches unity and the Schwarzschild metric becomes the [[#metric-for-flat-spacetime|Metric for Flat Spacetime]].
# As <math display="inline">M\rightarrow0</math>, curvature factor approaches unity and the Schwarzschild metric becomes the [[#metric-for-flat-spacetime|Metric for Flat Spacetime]].
# Two events only separated by an <math display="inline">r</math> distance:
#* <math display="inline">d\phi=0,\ dt=0</math>

<math display="block">
d\sigma = dr_{shell} = \left(1 - \frac{2M}{r}\right)^{-1/2} dr
</math>

<ol start="5" style="list-style-type: decimal;">
<li>Two events only separated by time on the same shell:
<ul>
<li><math display="inline">d\phi = 0,\ dr = 0</math></li></ul>
</li></ol>

<math display="block">
(d\tau)^2 = (dt_{shell})^2 = \left(1 - \frac{2M}{r}\right)(dt)^2 - \left(1 - \frac{2M}{r}\right)^{-1}(dr)^2 - (rd\phi)^2 \\
d\tau = dt_{shell} = \left(1 - \frac{2M}{r}\right)^{1/2}dt
</math>

<blockquote>
<strong>Note</strong> that <math display="inline">dt</math> is the time between ticks with respect to [[#far-away-time|Far-away Time]].
</blockquote>
<br />

## Far-away Time

* <math display="inline">t</math>-coordinate
** also called “ephemeris time”
* time lapse between two events, <math display="inline">dt</math>, is recorded by a far-away observer on their clock (far-away time)
** this is the clock tick rate for flat spacetime
