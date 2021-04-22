Orbits that stay greater than 300M -> Newtonian Mechanics can be used as a great approximation

# Project B: Inside the Black Hole

Nothing happens at the horizon -> these are coordinate singularities
everything continues to be smooth

There are no rest frames inside the horizon -> no shell can be constructed

Coordinate swap inside the horizon:
  - Nothing physically different occurs
  - r becoming time-like means "free float frame moves to small r with the inevitability that we ordinarily associate with the passage of time"

## Query 1

**Mass of the "20-year black hole":** Our chosen black hole has a mass such that it takes 20 years of wristwatch time for a diver who falls from rest starting from an infinite distance to pass from the horizon to the center.

### Part A:

?> Find the approximate mass of the "20-year black hole":
?> - in meters
?> - as a multiple of the mass of our Sun
?> - and in years

We can either work towards talking about the change in radial position for the in-falling object, $dr$, with respect to proper time, $d\tau$, and solve that expression for proper time or we can use the already constructed radial geodesic for an in-falling object. These are actually the same process but leverage different tools. Ultimately, we end up with the expression of:

$$\dot{r} = \frac{dr}{d\tau} = -\sqrt{\frac{2m}{r}}$$

Solving for $d\tau$, we then can integrate both sides to obtain the proper time for the entire journey:

$$\begin{aligned}
d\tau &= -\sqrt{\frac{r}{2m}} dr \\
\\
\int_{0}^{\tau}{d\tau'} &= \int_{2m}^{0}{-\sqrt{\frac{r}{2m}} dr} \\
\tau &= -\frac{1}{\sqrt{2m}}\frac{2}{3} \bigg(0 - (2m)^{3/2}\bigg) \\
&= \frac{4}{3}m
\end{aligned}$$

Now working backwards, we know that $\frac{\tau}{c} = 20 years$, so let's solve for this $m$:

$$\begin{aligned}
\frac{\tau}{c} &= \frac{4}{3}\frac{m}{c} \\
\frac{3}{4}(20 light-years) &= m \\
\\
m &= 15\ light-year
\end{aligned}$$

Converting to the requested units:

- in meters: $m = 1.4\times 10^{17}$
- as multiples of the Mass of our Sun: $9.607\times 10^{13}$
- and in light years: 15 light-years

### Part B:

?> On average, a galaxy consists of approximately $10^{11}$ stars similar to our Sun. The "20-year black hole" has the mass of approximately how many galaxies?

$$ \text{# of galaxies} = \frac{9.607\times 10^{13}}{10^{11}} \approx 960.7$$

### Part C:

?> What is the value of $r=2m$ at the horizon for the "20-year black hole" in light-years?

We already calculated the mass in lightyears as $15$, so $r=2m=2\times15=30$ lightyears.

### Part D:

We don't cross the horizon, we're already inside it before it has formed.
