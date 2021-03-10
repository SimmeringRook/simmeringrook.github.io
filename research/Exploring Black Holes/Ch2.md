# Chapter 2: Curving

## Distances Determine Geometry

The spacetime interval is the "distance" between events

<blockquote> "Distance" here means not just spatial but also temporal. Its the <strong>Spacetime</strong> distance between events.</blockquote>

<br />

## Reference Frames are Secondary

- Spacetime geometry exists regardless of reference frame (and even without a frame)
  - As such, all frames are equally valid
<br />

## Free Float Frames

- Relative accelerations are called "tidal accelerations"
- Reference frame can be as
  - tiny as a nucleus
  - short as a gamma ray emission
- Schwarzschild coordinates apply to slowly spinning  or non-rotating bodies
  - We can talk about the Earth and Sun using Schwarzschild coordinates
<br />

## The r-coordinate: the Reduced Circumference

- Due to space stretching in the presence of massive objets, we don't measure radial distances (Euclidean Geometry doesn't work for spacetime)
  - The is especially apparent with black holes
- walk around the shell of constant radius, measuring the Circumference. Divide by $2\pi$ to obtain.
  - Radial distance between shells is $d\sigma$ which will be greater than the difference from two concentric shells
- We can do this for spherically symmetric objects that are rotating "slow enough"
  - angle doesn't matter
  - only depends on $r$-coordinate
  - density doesn't have to be uniform
    - change with $r$ okay; change with $\phi$ or $\theta$ is violates symmetry

Schwarzschild Metric describes spacetime external to any <strong>isolated</strong>, slowly rotating, and spherically symmetric body.
<br />

## Gravitational Red Shift

- $dt_{shell}$ time between clock ticks > $dt_{far-away}$ time between clock ticks
<br />

## Mass in Units of Length

- Conversion factor:
$$\frac{G}{c^2}$$
Where:
  - G is Gravitational constant: $6.6726\times10^{-11} \frac{m^3}{kg\ s^2}$
  - c is the speed of light: $2.99792458\times10^{8} \frac{m}{s}$

Such that:
$$M_{in\ m} = \frac{G}{c^2}M_{in\ kg}$$
<br />

## Satellite Motion in a Plane

- A satellite is restricted to its plane of motion because of spherical symmetry
  - There is nothing to displace or alter it from its plane of motion
  - So we only need two coordinates to describe the location of the satellite: $r, \phi$

<blockquote><strong>??</strong>
<br />How do we know if a given distance is a Euclidean or Non-Euclidean distance? E.g. the distance from Earth to Moon?</blockquote>
<br />

## Metric for Flat Spacetime

- From Ch1, we have the spacetime interval as:
$$ \tau^2 = t^2 - s^2 \\
\sigma^2 = -t^2 + s^2 $$

Expanding into two dimensions of space:

$$ s^2 = x^2 + y^2 \\
\tau^2 = t^2 - (x^2 + y^2) = t^2 - x^2 - y^2 \\
\sigma^2 = -t^2 + (x^2 + y^2) = -t^2 + x^2 + y^2
$$

Changing into spherical coordinates:
$$
(d\tau)^2 = (dt)^2 - (dr)^2 - (rd\phi)^2 \\
(d\sigma)^2 = -(dt)^2 + (dr)^2 + (rd\phi)^2
$$
<br />

## Schwarzschild Metric

We take the [Metric for Flat Spacetime]:

$$ (d\tau)^2 = (dt)^2 - (dr)^2 - (rd\phi)^2 $$

and account for the curvature between two concentric shells:

$$ (d\tau)^2 = \left(1 - \frac{2M}{r}\right)(dt)^2 - \left(1 - \frac{2M}{r}\right)^{-1}(dr)^2 - (rd\phi)^2 $$

And then we can describe two events close to one another, where $d\phi$ is small such that $rd\phi$ describes an arc length for a straight line. $r$ is the $r$-coordinate which is a Non-Euclidean distance.

$$ (d\sigma)^2 = -\left(1 - \frac{2M}{r}\right)(dt)^2 + \left(1 - \frac{2M}{r}\right)^{-1}(dr)^2 + (rd\phi)^2 $$
<br />

### Sense Making

1. The <strong>curvature factor</strong> only depends on $r$, not $\phi$
    - $\left(1 - \frac{2M}{r}\right)$
    - We expect only $r$ dependence from a spherically symmetric body.

2. As $r\rightarrow\infty$, curvature factor approaches unity and the Schwarzschild metric becomes the [Metric for Flat Spacetime].

3. As $M\rightarrow0$, curvature factor approaches unity and the Schwarzschild metric becomes the [Metric for Flat Spacetime].

4. Two events only separated by an $r$ distance:
    - $d\phi=0,\ dt=0$

$$
d\sigma = dr_{shell} = \left(1 - \frac{2M}{r}\right)^{-1/2} dr
$$

5. Two events only separated by time on the same shell:
    - $d\phi = 0,\ dr = 0$

$$
(d\tau)^2 = (dt_{shell})^2 = \left(1 - \frac{2M}{r}\right)(dt)^2 - \left(1 - \frac{2M}{r}\right)^{-1}(dr)^2 - (rd\phi)^2 \\
d\tau = dt_{shell} = \left(1 - \frac{2M}{r}\right)^{1/2}dt
$$

<blockquote><strong>Note</strong> that $dt$ is the time between ticks with respect to [Far-away Time].</blockquote>
<br />

## Far-away Time

- $t$-coordinate
  - also called "ephemeris time"
- time lapse between two events, $dt$, is recorded by a far-away observer on their clock (far-away time)
  - this is the clock tick rate for flat spacetime
