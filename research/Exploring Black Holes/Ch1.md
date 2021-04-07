# Chapter 1: Speeding

## Notes
* [[Special Relativity]] is used to discuss objects moving very fast (in flat spacetime).

$$ v < c $$

### Spacetime

Consider a rock floating by with a wristwatch affixed to it. Record the time and position of at the start of a clock tick and then at then of the clock tick.

<blockquote><strong>Note:</strong> These times and positions must be recorded in a [[Inertial Reference Frame]]. Also, the time separation is not constrained to a single clock tick interval.</blockquote>

We now have the frame spacetime coordinates recorded for these two events and can convert the distances (both spatial and temporal) into invariant spacetime coordinates. This is useful because an observer moving in some different uniform motion compared to us will measure different separations between events than we will. Without these invariant coordinates, two different observers in inertial reference frames would have no way to agree on the separation between events.

<blockquote><strong>Note:</strong> Consult [[Spacetime Physics]] Chapter 1, Chapter 3, and Chapter 6 for more information.</blockquote>

This set of invariant coordinates of spacetime is called the [[Spacetime Interval|Spacetime Metric or Spacetime Interval]].
<br />

### Proper Time

Equations:
$$\tau^2 = t^2 - s^2$$

All observers (in inertial reference frames) will agree on this value as the number of time between ticks of the frame in question.

Note that $t$, the frame time, is measured in the same unit of length as the frame distance, $s$. An alternative form of this equation is to write $t$ as a measure of time, but multiplied by $c$ to convert to distance:

$$\tau^2 = (ct)^2 - s^2$$

This form is more explicit and used in [[The Geometry of Special Relativity]].
<br />

### Proper Distance

Equations:
$$\sigma^2 = s^2 - t^2$$

All observers (in inertial reference frames) will agree on this value as the distance between two events in the frame in question.

Similar to the previous section, the frame time $t$ is measured here in length. To be more explicit, we can rewrite the equation as:

$$\sigma^2 = s^2 - (ct)^2$$
<br />

#### Proper Length

This property gives rise to a similar measurement, the length of an object. We still use the Proper distance formula to calculate this value, but the proper length <strong>can only be calculated in a frame where the object is at rest</strong>.
<br />

### Speed

Given that we can now discuss the time or distance between any events (that are in an inertial reference frame), that means we can discuss the speed of an object that is causing these events:

$$ v = \frac{s}{t}$$

<blockquote><strong>Note:</strong> this speed value is a dimensionless constant, as $s$ and $t$ are both measured in the same units of length. This ratio represents the fraction of the speed of light the object in question is moving at.</blockquote><br />

This velocity is the speed at which the object is moving in its own frame. We expect that for any mass object in question, $s < t$ and as an upper bound, light in an inertial reference frame and in a vacuum will have:

$$s = t,\ \ v=\frac{s}{t}=1$$
<br />

### Principle of Extremal Aging

<blockquote>The path a free object takes between two events in spacetime is the path for which the time lapse between these events, recorded on the object's wristwatch, is an extremum.</blockquote>
<br />

### Energy

We can combine the [[Metric]] with the [[Principle of Extremal Aging]] to derive the relativistic expression of energy in flat spacetime. In general, the expression takes the form:

$$ \frac{E}{m} = \frac{dt}{d\tau}$$

In conventional units, the expression takes the form:

$$ \frac{E}{mc^2} = \frac{dt}{d\tau} $$

<blockquote>We use this equation to describe the energy of a particle in <strong>motion</strong>.</blockquote>

The derivation of these equations occur on pages 1-7 to 1-11.

For a particle at rest, we consider the timelike spacetime interval, $\tau^2 = (ct)^2 - s^2$ and note that $s=0$, making the expression $\tau = ct$. Note that then, $dt/d\tau = 1$. This leads to the infamous equation:

$$ E = mc^2 $$

<blockquote>We use this equation to describe the energy of a particle at <strong>rest</strong>.</blockquote>
<br />

### Momentum

$$ \frac{p}{m} = \frac{ds}{d\tau} $$

Seek [[Spacetime Physics]] Chapter 7 for more information.
<br />

### Mass

Particle mass $m$ is invariant. We can find this value by measuring the momentum and energy of the particle (in an inertial reference frame) while observing from an inertial reference frame.
<br />

##### Derivation

Take the timelike spacetime interval:

$$ \tau^2 = t^2 - s^2 $$

Consider the rates of change:

$$ (d\tau)^2 = (dt)^2 - (ds)^2 $$

Divide by $d\tau$:

$$ 1 = {\frac{dt}{d\tau}}^2 - {\frac{ds}{d\tau}}^2$$

Multiply by $m^2$:

$$ m^2 = m^2{\left(\frac{dt}{d\tau}\right)}^2 - m^2{\left(\frac{ds}{d\tau}\right)}^2$$

Substitute Energy and Momentum:

$$ m^2 = E^2 - p^2$$
<br />

## Exercises
