---
geometry:
 - a4paper
 - margin=2cm
output:
  pdf_document:
    toc: true
    toc_depth: 2
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
---

# Introduction

$$\ $$

## Motivation

> TODO: Introduction (Ripped from Proposal, Refine Later)

When considering new systems and their interactions, we tend to gravitate towards two main features: energy and kinematics. As we move away from Newtonian Mechanics, each system or formalism strongly suggests, if not outright requires, we abandon our familiar and direct kinematic equations for a more enigmatic exploration through energy conservation.

One such example of this shift is from Classical Thermodynamics into Statistical Mechanics. The student, eager to discuss small numbers of particles, immediately recognizes the futility attempting to use kinematics to describe the evolution of the system. On one hand, this can be expected of quantum mechanical (QM) systems, but these complications arise in classical mechanics as velocities approach significant fractions of the speed of light. While Special Relativity (SR) does not "break" the discussion of kinematics in the same fashion as QM, SR plays havoc with the student's everyday intuition molded from Galilean Relativity.

Fortunately, we are still able to discuss trajectories in this more complicated formalism, but they require different terminology. The most immediate consequence of the relativistic formalism comes from the disagreement from observers on lengths and times measured and even the order in which events occur. To rectify this, we transition from a discussion of time and space as separate entities to a single entity: spacetime. The method in which we measure distances also changes from the very familiar Pythagorean (or Euclidean) distance formula to a hyperbolic distance formula. This is evident in the comparison of each space's line element:

\begin{equation}
\underbrace{ds^2 = dx^2 + dy^2}_{\mathbb{E}^2} \quad \text{v.s.} \quad \underbrace{ds^2 = dx^2 - dy^2}_{\mathbb{M}^2}
\end{equation}

In the exploration of flat spacetimes (or Minkowski space), we are obliged to refresh our understanding of and the importance of an inertial reference frame. This tool is largely disregarded in undergraduate physics courses due to the explicit requirement of the Newtonian mechanics’ model. From this reevaluation of what different inertial observers see, we ultimately arrive at two seemingly inconsequential invariant measurements: proper time and proper distance.

\begin{equation}
d\tau^2 = g(\sigma^t,\ \sigma^t ), \qquad ds^2= g(\sigma^i,\ \sigma^j) \qquad i,j\neq t
\end{equation}

The next complication comes from Einstein considering the presence of massive objects on spacetime. Simply put: mass distorts or curves spacetime. The simplest and most prominent example of this is the Schwarzschild solution to Einstein's field equations, in which an isolated, non-rotating, and spherically symmetric massive object is placed at the origin. It is easy to see from the line element (physicists tend to refer to Equation $(\ref{SchwarzschildWithC})$ as the metric for Schwarzschild) of this space why this particular geometry for spacetime is used as the first non-flat introduction to General Relativity (GR):

\begin{equation}\label{SchwarzschildWithC}
ds^2=- \left( 1 - \frac{2GM}{c^2\ r} \right)(c^2\ dt^2) + \frac{dr^2}{1-\frac{2GM}{c^2\ r}} + r^2 d^2\Omega
\end{equation}

The final hurdle, in our simplified case, arises from another required application of length contraction and time dilation. This second set is a direct manifestation from curved spacetime and is completely independent from using SR. The subtle problem here is that now we consider how our grid that describes the fabric of spacetime is affected by the presence of massive objects. In popular media, this effect is typically demonstrated in Science Fiction TV shows or movies such as: *Stargate: SG1* or *Interstellar*. In class rooms, the SR side of this is examined with geostationary satellites for the GPS system, but the GR aspect is often overlooked. The short answer is that we can adopt a coordinate system that is immune to these effects and is either referred colloquially as the Schwarzschild or Bookkeeper's coordinates: $r$, $\theta$, $\varphi$, $t$. This type of coordinate system is a geometric representation (unaffected by the curvature of spacetime).

The path a free-falling object takes is always correspond to a straight worldline from the perspective of its rest frame. These paths adopt a special name: geodesic, with a sub-classification that null geodesics are paths that can only be traveled by massless particles. As an example of the perplexing nature of geodesic equations (GR's EOM analog), below is the generalized geodesic equation for motion about the Schwarzschild geometry:

\begin{equation}\label{GeneralSchwarzschildEOM}
\frac{1}{2}\dot{r}^2 = \frac{E^2-kc^4}{2c^2} +k \frac{GM}{r} - \frac{ {L_z}^2 }{2r^2} + \frac{GM {L_z}^2}{c^2 r^3}
\end{equation}

While Equation $(\ref{GeneralSchwarzschildEOM})$ can be cleaned up by suppressing constants (typically $G_N$ and $c$), the functional form still conceals information about this object's trajectory: Where is it at some time t? How fast is it moving? What's the acceleration? Where did it start? How do I build an intuitive understanding? This is the focus of the project: to help translate these compact and foreign equations from General Relativity into visualizations and other representations that tie back into and build off already existing intuitions and reasoning skillsets.

\pagebreak

## A Primer on Spacetime and Relativity

$$\ $$

### The Breaking Point of Galileo's Relativity

> TODO: Possibly redirect to Appendix for a refresher on concepts from PH 315: Theoretical Mechanics (i.e., *The Surveyor's Parable*).

The crux of the problem with classical Netownian Physics is that the model does not behave well once the relative velocity between intertial frames of reference start approaching *significant* factors of the speed of light. If we make the modest assumption about the universe that the models of physics should be valid regardless of location (i.e. the same on Earth as on Mars, in the Milkway as in the Andromeda galaxy, etc) and that the speed at which information (read: light) can travel is constant, we can immediately discover problems with Galilean Relativity.

Consider a stunt-person jumping out of a moving car. We construct three reference frames in which to analyze the motion: the stunt-person, the car, and the cameraman. From the stunt-person's frame, they observe the surface of the Earth accelerating towards them at $9.8$ $m/s^2$. The car observes the stunt-person moving away laterally with a velocity of $5$ $m/s$. The cameraman, off axis from both the stunt-person and car, observes the stunt-person diving out from the car with the same lateral velocity but still moving away from the camera at $30$ $m/s$. Using vector addition, the cameraman concludes that the stunt-person, at this moment, is moving at a total speed of $\sqrt{925}$ $m/s$.

> TODO: Simple sketch/figure showing the view from each frame.

\begin{figure}[H]
    \centering
    \caption{\label{GalileanRelativity}An illustration of the above physical situtation as seen from three reference frames. }
\end{figure}

Now, we increase the speed of the stunt-person diving away from the car to $0.5c$ (half the speed of light) and the car to $0.9c$. The cameraman then would calculate a speed of the stunt-person of $\sqrt{1.06}c\approx 1.03c$. While a crude example, our method of determining relative velocities allows a description of a massive object moving faster than the speed of light. Our two modest assumptions about the universe are the same two ideas that Einstein uses as the postulates of Special Relativity.

$$\ $$

### Space into Spacetime

> TODO: How do we fix this problem? Measure time in the same dimensions as space. How do we convert time into space? The speed of light. But how is that supposed to fix the relative velocity problem? We need to switch from Euclidean Geometry to Minkowski (Pythagorus to Hyperbolic).

> TODO: Introduce/Refresh Proper Time and Proper Distance

$$\ $$

### Mass is Curvature

> TODO: Make sure to introduce terminology of geometric and physical distance to allow easier comparisions of quantities beyond Bookkeeper and Shell observers. Figure including the hyperbolic angle on a radial spacetime diagram would help. Also include figure if Cartographer generates embedding diagrams.

\begin{figure}[H]
    \centering
        \begin{tikzpicture}[scale=1.5]

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (L) at (5,0);
    \coordinate (P) at (0,-2);

    % Construct triangle
    \draw (P) -- (L) node [midway, below] {$dr_{shell}$};
    \draw (O) -- (L) node [midway, above] {$dr_{bk}$};
    \draw (O) -- (P) node [midway, left] {$\sqrt{1-\frac{2M}{r_{shell}}}$};

    \end{tikzpicture}
    \caption{\label{drvectorInSchwarz}A hyperbolic geometric representation of how the physical distance, $dr_{shell}$, is greater than the geometric distance, $dr_{bk}$, due to the curvature at that shell's $r$-coordinate. }
\end{figure}

> TODO: Remember $d\vec{r}$ from PH 422? Well, it's back and this time, its going to make life a lot easier.

\pagebreak

## Computational Physics Background

$$\ $$

### The Flaws of Doing Maths Computationally

> TODO: Describe the problems of using binary to represent base 10 numbers and the operations; i.e. Floating Point Precision

$$\ $$

### Variables, Dimensions, and their Representation

> TODO: Ripped from *Progress Report 11/22*, Refine Later

The main achievement of the codebase for Novemeber 12 was the implementation of the dimensionless quantities for the arrays. Spurred by comments from Dr. David Roundy during PH 36X and most recently by Dr. Oksana Ostroverkhova during PH 651 while solving the Harmonic Oscillator in the position representation: "*make everything dimensionless, especially when doing computational Physics*".

``` python
__r_domain = np.arange(
        start=int(__start_r / __r_step_resolution),
        stop=int(__stop_r / __r_step_resolution),
        step=__r_iteration_direction
    )
```

From a usability standpoint, this was very benifical, as each corresponding coordinate array would scale at runtime according to any changed paramter. For example, if the previous run considered the interval of $(2M,10M)$ with a $dr_{bookkeeper}=1\ m$, increasing the resolution by changing $dr_{bk}=0.1$ automatically increased the (integer) number of steps from $2M$ to $10M$. The other main benefit of being very strict about bookkeeping dimensions of quantities allowed for the use of dimensional analysis to verify proper representations of calculations and to check when something needed to be scaled. Comparing the relation of $dr_{shell}$ to $dr_{bk}$ is an excellent example:

$$dr_{shell} = \frac{dr_{bk}}{\sqrt{1-\frac{2M}{r}}}$$

```python
def bookkeeper_meter_stick_as_measured_from_shell(proper_distance):
  """Returns the proper distance as measured by each shell within the interval of __r_domain.
  
  The distance between each shell is determined at the start of runtime with the value 
  assigned to __r_step_resolution. This is analogous to Chapter 2, Exercise 3 from 
  *Exploring Black Holes: Introduction to General Relativity* by E.F Taylor and J. A. Wheeler.
  """
  for r in __r_domain :
    proper_distance[ (r - __r_domain[0]) * __r_iteration_direction ] = ..
      __r_step_resolution / np.sqrt(1 - (2*M)/(r*__r_step_resolution))
```

Recalling from above, `__r_domain` is a dimensionless interval of integer r-coordinates in the specified interval. `__r_step_resolution` serves as the bookkeeper's meter stick, $dr_{bk}$. Looking at the dimensions for the curvature factor, $\sqrt{1-2M/r}$, we see that in the program `r` is a dimensionless quantity, but in the mathematical formula, the entire expression is supposed to be dimensionless. This hints that `r` needs to be multiplied by something with dimensions of length to cancel out the dimensions from $2M$, but what should quantity should be used?

In this simple case, we add back the dimensions the same way we removed them: scaling by $dr_{bk}$; otherwise we would be obtaining the scale factor for some $r$-coordinate that was off by a factor of $1/dr_{bk}$. This can also be very quickly seen when calculating the corresponding lightclock tick rate with $$dt_{shell} = \sqrt{1-\frac{2M}{r}} dt_{bk}$$

```python
def bookkeeper_lightclock_tick_as_measured_from_shell(proper_time):
  """Returns the proper time as measured by each shell within the interval of __r_domain.
  
  The time separation between events for each shell is determined at the start of runtime 
  with the value assigned to __time_step_resolution. This is analogous to Chapter 2, 
  Exercise 3 from *Exploring Black Holes: Introduction to General Relativity* by E.F Taylor
  and J. A. Wheeler.
  """
  for r in __r_domain :
    proper_time[ (r - __r_domain[0]) * __r_iteration_direction ] =  ..
      np.sqrt(1 - (2*M)/(r*__r_step_resolution)) * __time_step_resolution
```

Knowing that time has dimensions of length in GR, due to scaling by $c$, we could naively ask about using `__r_step_resolution` or `__time_step_resolution`. At the surface, this feels like a straightforward answer, but there's an added layer of complexity.

We're talking about time and the resolution should depend on the precision as specified by $dt_{bk}$. However, at the same time, we're talking about what the difference in clock tick rates are at each distance along some `r` interval. The context is the deciding factor: we want to measure the disagreement between the physical observation and the geometric expectation along some distance, therefore we iterate over `__r_domain` and scale `r` by $dr_{bk}$.

\pagebreak