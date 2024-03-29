---
title: "Cartographer: Using Python to Create Maps of Curved Spacetime and Differential Scattering Cross-sections of Low-Mass Objects about a Schwarzschild Black Hole"
author:
  - Thomas Knudson `\\\\`{=latex} Department of Physics, OSU
  - Dr. Kathryn Hadley (Research Advisor) `\\\\`{=latex} Department of Physics, OSU
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

\pagebreak

# Abstract

> TODO: Figure out how modify pandoc's template to move about table of contents.

\pagebreak

# Table of Contents

> TODO: Replace with auto generated table

## Table of Figures

> TODO: Figure out how to modif pandoc's template to auto generate

## Table of Tables

> TODO: Figure out how to modif pandoc's template to auto generate

\pagebreak

# Introduction

> Introduction, $$\text{Ripped from Proposal, Refine Later}$$

## Motivation

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

The next complication comes from Einstein considering the presence of massive objects on spacetime. Simply put: mass distorts or curves spacetime. The simplest and most prominent example of this is the Schwarzschild solution to Einstein's field equations, in which an isolated, non-rotating, and spherically symmetric massive object is placed at the origin. It is easy to see from the line element (physicists tend to refer to Equation 3 as the metric for Schwarzschild) of this space why this particular geometry for spacetime is used as the first non-flat introduction to General Relativity (GR):

\begin{equation}
ds^2=- \left( 1 - \frac{2GM}{c^2\ r} \right)(c^2\ dt^2) + \frac{dr^2}{1\frac{2GM}{c^2\ r}} + r^2 d^2\Omega
\end{equation}

The final hurdle, in our simplified case, arises from another required application of length contraction and time dilation. This second set is a direct manifestation from curved spacetime and is completely independent from using SR. The subtle problem here is that now we consider how our grid that describes the fabric of spacetime is affected by the presence of massive objects. In popular media, this effect is typically demonstrated in Science Fiction TV shows or movies such as: *Stargate: SG1* or *Interstellar*. In class rooms, the SR side of this is examined with geostationary satellites for the GPS system, but the GR aspect is often overlooked. The short answer is that we can adopt a coordinate system that is immune to these effects and is either referred colloquially as the Schwarzschild or Bookkeeper's coordinates: $r$, $\theta$, $\varphi$, $t$. This type of coordinate system is a geometric representation (unaffected by the curvature of spacetime).

The path a free-falling object takes is always correspond to a straight worldline from the perspective of its rest frame. These paths adopt a special name: geodesic, with a sub-classification that null geodesics are paths that can only be traveled by massless particles. As an example of the perplexing nature of geodesic equations (GR's EOM analog), below is the generalized geodesic equation for motion about the Schwarzschild geometry:

\begin{equation}
\frac{1}{2}\dot{r}^2 = \frac{E^2-kc^4}{2c^2} +k \frac{GM}{r} - \frac{ {L_z}^2 }{2r^2} + \frac{GM {L_z}^2}{c^2 r^3}
\end{equation}

While Equation 4 can be cleaned up by suppressing constants (typically G_N and c), the functional form still conceals information about this object's trajectory: Where is it at some time t? How fast is it moving? What's the acceleration? Where did it start? How do I build an intuitive understanding? This is the focus of the project: to help translate these compact and foreign equations from General Relativity into visualizations and other representations that tie back into and build off already existing intuitions and reasoning skillsets.

\pagebreak

## Mathematical Background

> TODO: Geometric first approach? Tray's DFGGR?

## Phyiscal Background

> TODO: 315? Curvature?

> TODO: Make sure to introduce terminology of geometric and physical distance to allow easier comparisions of quantities beyond Bookkeeper and Shell observers. Figure including the hyperbolic angle on a radial spacetime diagram would help. Also include figure if Cartographer generates embedding diagrams.

\pagebreak

# Methodology

> Plan of Work, $$\text{Ripped from Proposal, Refine Later}$$

We will study the equations of motion for massive and massless particles in the presence of curved spacetime. A Schwarzschild black hole will serve as the source of curvature for analysis of limiting cases that will be used as the foundation for sense making and error checking in computational runtimes. The project itself has been subdivided into three major phases: Scaffolding, Curving, and Refinement.
The core of the toolset depends on a series of key design and implementation decisions about the underlying framework. One of the key features is to have an intuitive code base for physicists to use, which implies a latticework of grid points mapping out the space. Ideally, this latticework will be agnostic with respect to the active geometry and type of curvature. This stage will focus on the creation of the latticework, its documentation and the manifestation of key mathematical tools such as differential scattering and the representation and parameterization of a geodesic. Examples of this design process are shown on the following page with Figure 1 and Figure 2.

> TODO: Replace if final implementation is no longer OOP.

\begin{figure}
    \caption{Latticework design implementation document detailing desired behaviour and properties. }
\end{figure}

\begin{figure}
    \caption{SpacetimeGeometry design implementation document outlining the use of object-oriented class inheritance to allow modularity for future different descriptions of curvature in spacetime and to ensure the framework does not implicitly assume any behaviour of the geometry: “Spacetime agnostic”. }
\end{figure}

The differential scattering cross-section has a general form that can be parameterized based off the impact parameter, $\sigma\left(b\right)=\int{\frac{d\sigma\left(b\right)}{d\Omega}\left(\theta,\ \phi\right)d\Omega}$ [5], but we will need to still solve the EOM, Equation 4, and mesh the two together. Care will need to be taken to avoid any implicit assumptions about the object traversing the spacetime to avoid unphysical geodesics and cross-sections: e.g., the impact parameter has a different form for massive versus massless particles [1,3]. Below, in Figure 3, the general user story has been mapped out to provide insight into the conceptual process of the toolset.

> TODO: Replace with final version's flow system. Maybe keep original for comparision

\begin{figure}
    \caption{Flow chart detailing the typical user story for interacting with the toolset. }
\end{figure}

\pagebreak

# Results

## Cartographer's Capabilities

> TODO: Design decisions, trade-offs, numerical stability, optimizations?

## Placeholder, Progress 11/05

### Framework Scafolding

#### Python

I learned a few interesting things about how Python deals with inheritance and classes.

- Class variables
    - 'Global' in scope, C# comparison is a 'static' class variable (shared across all instances)
- Polymorphism
    - either doesn't exist
    - or you just assume the thing you've been passed has the attributes you want to call
        - makes it harder to treat an abstract object
    - overriding methods is weird
        - sometimes still class the base class when executing
        - isn't horrible but requires a mental model reframing

#### Latticework.py

Part of the focus here was to remove the dynamic initialization and population of the `nodes` array: E.g., this horrible abomination that was bound to break and cause issues in the future:

``` python
    def __populate_Lattice(self):
        # numpy.shape() returns a tuple describe the dimensions of the numpy array
        # We can asked for the
        numberOfDimensions = len(numpy.shape(self._nodes))
        print("Number of Dimensions:", numberOfDimensions)

        for dimension in range(numberOfDimensions):
            print("Length of Dimension:", numpy.shape(self._nodes)[dimension])

        for x in range(numpy.shape(self._nodes)[numberOfDimensions - numberOfDimensions]):
            for y in range(numpy.shape(self._nodes)[numberOfDimensions
                - numberOfDimensions + 1]):
                if (numberOfDimensions - numberOfDimensions + 2) < numberOfDimensions:
                    for z in range(numpy.shape(self._nodes)[numberOfDimensions -
                        numberOfDimensions + 2]):
                        if (numberOfDimensions - numberOfDimensions + 3) <
                            numberOfDimensions:
                            for t in range(numpy.shape(self._nodes)[numberOfDimensions
                                - numberOfDimensions + 3]):
                                self._nodes[x,y,z,t] = Node(tuple((x,y,z,t)))
                        else:
                            self._nodes[x,y,z] = Node(tuple((x,y,z)))
                else:
                    self._nodes[x,y] = Node(tuple((x,y)))
```

The concept was to implement some pre-optimization in which the N-dimensional `nodes` array only created the correct number of dimensions as required by the given `SpacetimeGeometry` being used as the basis. For example, if Cartographer was told to create a 1+1 representation of Schwarzschild spacetime, `nodes` only needs to be a 2-dimensional array: 1 spatial and 1 temporal. The above function could be cleaned up, to remove all the redundant `numberOfDimensions - numberOfDimensions` calculations [^1]:

[^1]: Ironically, the design decision behind this was to avoid hardcoding the indices for the different dimensions in each loop, but ultimately failed as the `Node` class wants to know its index position in the N-dimensional array. This design decision came about from previous hobby experience in game design where it becomes very useful for each tile in a board to be able to inform you of its coordinates: E.g., very helpful when needing to access neighbors.

``` python
    def __populate_Lattice(self):
        # ...
        for x in range(numpy.shape(self._nodes)[0]):
            for y in range(numpy.shape(self._nodes)[1]):
                if 2 < numberOfDimensions:
                    for z in range(numpy.shape(self._nodes)[2]):
                        if 3 < numberOfDimensions:
                            for t in range(numpy.shape(self._nodes)[3]):
                                self._nodes[x,y,z,t] = Node(tuple((x,y,z,t)))
                        else:
                            self._nodes[x,y,z] = Node(tuple((x,y,z)))
                else:
                    self._nodes[x,y] = Node(tuple((x,y)))
```

But that doesn't solve the underlying problem that this implementation:

- is hard to read and interpret
- makes assumptions about the geometry

While the loop variables have no 'direct' influence on what information is stored in `nodes`, they are revealing an implicit intended structure which is intentionally supposed to be absent. Ultimately, this was supposed to be resolved by having the onus be placed on Cartographer. If the user is asking for a specific latticework structure, they would be able to tell Cartographer how big each dimension needs to be and how many via the `gridShape` parameter in the class constructor:

```python
    def __init__(self, gridShape = tuple((4,4)), spacetime = EuclideanGeometry(2)):
        self._spacetime = spacetime
        self._nodes = numpy.empty(gridShape, dtype=object)
```
The details of initializing each `Node` in `nodes` was delayed until later, with a focus to getting a simple deliverable ready by Friday. Cartographer is supposed to generate plots of objects in spacetime and so figuring out how to generate those figures became more of a priority than the architecture of the framework.

#### Cartographer.py

After resolving the weirdness of inheritance (and lack of polymorphism?) in Python, work focused on getting correct 'measurements' in Spacetime. Euclidean geometry uses the Pythagorean theorem to measure distances, so creating two points in separate orthogonal directions would be a simple test of the implementation. Similarly, the implementation of the metric for Minkowski spacetime should require only minor tweaking and both cases will serve as simple tests to verify the implementation works regardless of the geometry. In `Cartographer.py`, the following was added for this purpose:

```python
def main():
    gridsize = tuple((4,4,4,1))
    lattice = Latticework(gridsize)

    dx = tuple((2,0,0,0))
    dy = tuple((0,2,0,0))
    dt = tuple((0,0,0,4))

    euclideanPath = mark_out_path(dx,dy)
    minkowskiPath = mark_out_path(dx,dt)

    print("Euclidean:", euclideanPath, lattice._spacetime.Act_Metric_On(
        euclideanPath,euclideanPath))
    lattice._spacetime = SchwarzschildGeometry()
    print("Schwarzschild:", minkowskiPath, lattice._spacetime.Act_Metric_On(
        minkowskiPath,minkowskiPath))

def mark_out_path(start, stop):
    return tuple(map(lambda i, j: i - j, start, stop))
```

`mark_out_path` is just a minor helper function to create the (directed) line segment that connect the second point to the first. `lattice` was initialized with default parameters and so the type of `SpacetimeGeometry` assigned to `lattice._spacetime` was a 2-dimensional `EuclideanGeometry`. This child class really only serves to assign the correct metric signature to be used in calculations. The result given by `lattice._spacetime.Act_Metric_On` is then equivalent to asking for the squared magnitude of the vector. Taking the square root was omitted at this step as that's something to occur after the metric is used.

```
/GitHub/Cartographer/Cartographer.py
Creating Geometry with the metric: (1, 1)
Euclidean: (2, -2, 0, 0) 8
Creating Geometry with the metric: (1, 1, 1, -1)
Schwarzschild: (2, 0, 0, -4) -12
```

##### EuclideanGeometry.py

```python
from SpacetimeGeometry import SpacetimeGeometry

class EuclideanGeometry(SpacetimeGeometry):

    __Metric = tuple(( tuple((1,)), tuple((1,1)), tuple((1,1,1)) ))

    def __init__(self, dimesionality=2):
        super().__init__(EuclideanGeometry.__Metric[
            len(EuclideanGeometry.__Metric) - dimesionality])
```

##### SpacetimeGeometry.py

Since the default metric in `SpacetimeGeometry` (at this time) is 3+1 Minkowski, a `MinkowskiGeometry` has not been implemented yet.

```python
class SpacetimeGeometry:

    #__Metric = tuple((1,1,1,-1))

    def __init__(self, metric=tuple((1,1,1,-1))):
        print("Creating Geometry with the metric:", metric)
        self.__metric = metric

    def get_Dimensionality(self):
        return len(self.__metric)

    def Act_Metric_On(self, pForm1, pForm2):
        metricResult = 0
        for i in range(len(self.__metric)):
            metricResult += pForm1[i] * self.__metric[i] * pForm2[i]
        return metricResult
```

#### Final Woes of Architecture

The natural next step was to move on to implementing `SchwarzschildGeometry` and that's where this approach came to a halt. Mathematically, it's a trivial matter to tell you how the metric acts on 1-forms for Schwarzschild:

$$\begin{aligned}
g(dr,dr) &= \frac{1}{1-\frac{2M}{r}} \\
g(r\sin{\theta}d\phi, r\sin{\theta}d\phi) &= 1 \\
g(rd\theta, rd\theta) &= 1 \\
g(dt,dt) &= -(1-\frac{2M}{r})
\end{aligned}$$

And in other Computer-Aided Algebra systems like Mathematica, the parameterization is equally as trivial: we just declare the dependence on the parameter called `r`. Python won't immediately freak out if we try to do this:

```python
#...
    self.__metric = tuple( (1/math.sqrt(1-2*M/r), 1, 1, math.sqrt(1-2*M/r)) )
```

We can always specify the mass of the black hole (in meters), `M`, globally or handle the scope differently. The problem is "what is `r`?" and "how do we tell the script later on that `r` now has a new value?". There are workarounds to avoid hardcoding the value, but this was just deeper and deeper into the weeds of architecture and no where closer to even getting a simple plot of Minkowski (or even Euclidean!) space.

\pagebreak

### Design Shift: Figures first, Grand Architecture later

With even more focused being place on the generation of figures, the question shifted to "how?". At this point, it is out of scope to build a plotting/graphic framework from scratch and I intended for Cartographer to be able to both export data (save on calculations in the future) and generate the figures, with the inkling of utilizing Matplotlib to format everything. So, keeping things as simple as possible and mentally reframing the project as a simple PH36X: Computational Lab assignment, the ingloriously named `plot.py` file was created. In defiance of experience, caution about future interoperability and extension was thrown to the wind to focus on direct implementation of equations of motion in Schwarzschild.

#### Arrays

Matplotlib prefers to have an array for both the horizontal and vertical axes[^2] and so `tcoord` and `rcoord` are created with a size to represent the desired time and r-coordinate range.

[^2]: This makes a lot more sense in hindsight, considering how Microsoft Excel or Google Sheets require the columns for both as well.

``` python
tcoord = np.arange(0, int(tau_final/bookkeeper_timestep))
rcoord = np.arange( int(2*M), int( (r_max*M)/bookkeeper_rstep ) )
```

##### Resolution Factor Explaination

This is done using the [Numpy `arange`](https://numpy.org/doc/stable/reference/generated/numpy.arange.html) function which finds the integer distance between the given `start` and `stop` parameters such that the total length is the integer value of $$\frac{\text{stop} - \text{start}}{\text{step size}}$$ and initializes each element to the corresponding integer between `start` and `stop` (in increments of `step`). To avoid the singularity of $r=0$, `rcoord` is being initialized at $r=2M$. Both coordinate arrays also have their stop value scaled inversely by the `bookeeper_step` variables which represent the resolution of each calculation. For example, consider the implementation of finding the area under the curve of $x^2$:

``` python
dx = 1
xcoord = np.arange(0, a)

approximate_area = 0

for x in xcoord:
    approximate_area += np.power(x, 2) * dx
```

In this Riemann sum approximation of the integral, we can decrease the magnitude of `dx` to correspond to smaller width rectangles and increase our precision. However, `xcoord`'s size doesn't change dynamically to reflect this, and so we need to scale the length of this array proportionally. I've already revealed the method in which I intend to handle this dynamically and so I'll keep the derivation short: In the current form, if we want to reduce the width from $1$ unit to $0.1$, we then scale $a$ by $10$:

``` python
dx = 0.1
xcoord = np.arange(0, 10*a)
```

After playing around with different scale factors and inevitably forgetting to update all the values at the same time, the trick to notice is that inverse linear relationship. The only extra step involved is to ensure the result of dividing $a$ by $dx$ is an integer and so we arrive at the implementation for `rcoord` and `tcoord`:

``` python
bookkeeper_timestep = 0.1
bookkeeper_rstep = 1

tcoord = np.arange(0, int(tau_final/bookkeeper_timestep))
rcoord = np.arange( int(2*M), int( (r_max*M)/bookkeeper_rstep ) )
```

##### Calculation Results

Since the plots I'm creating (at this stage) are scatter plots (with line segments connecting the points), I need a equivalently sized array to store the values for each calculation. Luckily, this is a very common use case for the developers/maintainers of Numpy, and their array constructing function calls accept a `np.shape()` call as a parameter to define the size. At the current moment, I could just ask the corresponding coordinate array for its `length` and construct it this way, but the power of using `np.shape()` is that this construction dynamically scales for whatever dimensionality of the given coordinate array. Since `np.shape()` returns a `tuple` (ordered and unchangeable collection) describing the dimensionality of the given array, this drastically simplifies the construction of a multidimensional array:

> Consider an example in which we need to store the results from $f(x,y,z)$ with $x\in[x_1, x_2]$, $y\in[y_1, y_2]$, and $z\in[z_1, z_2]$:

``` python
x_length = int(x2 - x1)
y_length = int(y2 - y1)
z_length = int(z2 - z1)

dimensionality_for_array = (x_length, y_length, z_length)

results = np.zeros( dimensionality_for_array )
```

This only leaves the function call of `np.zeros()`, which creates the array of specified dimensions and initializes each element to $0$. At this point, we're not iterating through the array's to check for specific values and this could foreseeably hide a bug in some calculation in which the results are returning $0$ incorrectly, but it does give us a starting point. If there is a significant math error it should manifest itself as a runtime error at this stage. It might be safer in the future to default to a `NaN` initialization, since the type returned from each math function call is a float and we can use `NaN` to spot bad behavior.

``` python
radial_position_at_time_t = np.zeros( np.shape(tcoord) )
v_effective = np.zeros( np.shape(rcoord) )
phi_position_at_rcoord = np.zeros( np.shape(rcoord) )
```

#### Math Functions

With the basic groundwork for plotting laid out, it came time to encoding the mathematical functions into Python. For ease of immediate implementation, J. Hartle's *Gravity: An Introduction to Einstein's General Relativity* was consulted for the analytic solutions to simple motion in Schwarzschild spacetime. Radial (reduced-circumference) position as a function of proper time was implemented first, as it was the most straightforward and simple (and to verify that Python and it's libraries were playing nice).

``` python
def radial_position_at_propertime(tau):
    '''
    Using Equation 9.38 from Page 198 of Hartle:
        r(tau) = (3/2)^(2/3) * (2M)^(1/3) * (tau_final - tau)^(2/3)

    Since (3/2) and (2M) are constant values, we can save some efficency by calculating
    these at the start of the script and just reference the pre-calcualted value using
    `rad_const`
    '''
    return ( rad_const * np.power( (tau_final - tau), (2/3.0) ) )
```

$$r(\tau) = \left(\frac{3}{2}\right)^{2/3}\left(2M\right)^{1/3}\left(\tau_{final} - \tau \right)^{2/3}$$

The results were ... unenlightening: an almost perfect linear relationship. Having spent much time in the past plotting and changing the parameters of the effective potential function, that became the next focus of implementation as it would be easier to notice unexpected behaviour and determine the likely cause. Equation 9.30 from page 194 of Hartle defines the effective potential as:

$$V_{eff}(r) = \frac{1}{c^2}\left(-\frac{GM}{r} + \frac{\ell^2}{2r^2}-\frac{GM\ell^2}{c^2r^3}\right)$$

``` python
def effective_potential(rcoordinate, orbitalAngularMomentum):
    return (- (G*M)/rcoordinate + np.power( (orbitalAngularMomentum / rcoordinate), 2)
    * 0.5 - ( (G*M)/np.power(c, 2) ) * (np.power(orbitalAngularMomentum, 2)
        / np.power(rcoordinate, 3)) ) * (1/ np.power(c, 2))
```

For $\ell=5$, this creates the expected peak in the curve as $r\rightarrow 3M$ before decaying to $-\infty$ as $r\rightarrow 0$. Shortly before the scheduled meeting on 11/05, an attempt was made to implement a plot describing the scattering of a non-radial plunge trajectory. Equation 9.49 from page 201 of Hartle describes the change as:

$$\frac{d\phi}{dr} = \pm \frac{\ell^2}{r^2} \left[e^2 - \left(1-\frac{2M}{r}\right)\left(1+\frac{\ell^2}{r^2}\right)\right]^{-1/2}$$

And crudely implemented as:

``` python
def shape_of_bound_orbit(rcoordinate, orbitalAngularMomentum, totalenergy_per_unitrestmass):
    return (orbitalAngularMomentum / np.power(rcoordinate, 2))
     * 1 / np.power(( np.power(totalenergy_per_unitrestmass, 2) - (1 - (2*M)/rcoordinate)
     * (1 + np.power( (orbitalAngularMomentum / rcoordinate), 2) ) ), 0.5)
```

#### plot.py

This is the full code file before the meeting began.

``` python
'''These are standard aliases for the packages; so I will opt to use standard notation for
 increased future readability'''
import numpy as np
import matplotlib.pyplot as plt

'''Physical constants'''
c = 1
M = 1
G = 1

'''Runtime constants'''
rad_const = np.power(1.5, (2/3.0)) * np.power(2*M, (1/3.0))
tau_final = 20.0
r_max = 40.0

'''Set Geometric scale factors'''
bookkeeper_timestep = 0.1
bookkeeper_rstep = 1

'''Arrays'''
tcoord = np.arange(0, int(tau_final/bookkeeper_timestep))
rcoord = np.arange( int(2*M), int( (r_max*M)/bookkeeper_rstep ) )

radial_position_at_time_t = np.zeros( np.shape(tcoord) )
v_effective = np.zeros( np.shape(rcoord) )
phi_position_at_rcoord = np.zeros( np.shape(rcoord) )

def shape_of_bound_orbit(rcoordinate, orbitalAngularMomentum, totalenergy_per_unitrestmass):
    return (orbitalAngularMomentum / np.power(rcoordinate, 2))
     * 1 / np.power(( np.power(totalenergy_per_unitrestmass, 2) - (1 - (2*M)/rcoordinate)
     * (1 + np.power( (orbitalAngularMomentum / rcoordinate), 2) ) ), 0.5)

def radial_position_at_propertime(tau):
    '''
    Using Equation 9.38 from Page 198 of Hartle:
        r(tau) = (3/2)^(2/3) * (2M)^(1/3) * (tau_final - tau)^(2/3)

    Since (3/2) and (2M) are constant values, we can save some efficency by calculating
    these at the start of the script and just reference the pre-calcualted value using
    `rad_const`
    '''
    return ( rad_const * np.power( (tau_final - tau), (2/3.0) ) )

def effective_potential(rcoordinate, orbitalAngularMomentum):
    return (- (G*M)/rcoordinate + np.power( (orbitalAngularMomentum / rcoordinate), 2)
    * 0.5 - ( (G*M)/np.power(c, 2) ) * (np.power(orbitalAngularMomentum, 2)
        / np.power(rcoordinate, 3)) ) * (1/ np.power(c, 2))

def make_plot(horizontalValues, verticalValues):
    fig, ax = plt.subplots()
    ax.plot(horizontalValues, verticalValues)
    plt.show()

def main():

    # for tau in tcoord:
    #     radial_position_at_time_t[tau - tcoord[0]] = radial_position_at_propertime(
        tau * bookkeeper_timestep)
    # make_plot(radial_position_at_time_t, tcoord)

    for r in rcoord:
        v_effective[r - rcoord[0]] = effective_potential(r, 5)
    #rescale the rcoordinates to be factors of M
    scaled_rcoord = np.multiply(rcoord, (bookkeeper_rstep/M) )
    make_plot(scaled_rcoord, v_effective)

if __name__ == '__main__':
    main()
```

\pagebreak

## Placeholder, Progress 11/22

### Refactoring

#### Making Dimensions Meaningful

The main achievement of the codebase for Novemeber 12 was the implementation of the dimensionless quantities for the arrays. Spurred by comments from Dr. David Roundy during PH 36X and most recently by Dr. Oksana Ostroverkhova during PH 651 while solving the Harmonic Oscillator in the position representation: *make everything dimensionless, especially when doing computation Physics*.

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
  '''
  Bookkeepr: This is a meter stick
  Shell: Uh, you should get a refund, because that's 5 times longer than its supposed to be!
  '''
  for r in __r_domain :
    proper_distance[ (r - __r_domain[0]) * __r_iteration_direction ] = .. 
      __r_step_resolution / np.sqrt(1 - (2*M)/(r*__r_step_resolution))
```

Recalling from above, `__r_domain` is a dimensionless interval of integer r-coordinates in the specified interval. `__r_step_resolution` serves as the bookkeeper's meter stick, $dr_{bk}$. Looking at the dimensions for the curvature factor, $\sqrt{1-2M/r}$, we see that in the program `r` is a dimensionless quantity, but in the mathematical formula, the entire expression is supposed to be dimensionless. This hints that `r` needs to be multiplied by something with dimensions of length to cancel out the dimensions from $2M$, but what should quantity should be used?

In this simple case, we add back the dimensions the same way we removed them: scaling by $dr_{bk}$; otherwise we would be obtaining the scale factor for some $r$-coordinate that was off by a factor of $1/dr_{bk}$. This can also be very quickly seen when calculating the corresponding lightclock tick rate with $$dt_{shell} = \sqrt{1-\frac{2M}{r}} dt_{bk}$$

```python
def bookkeeper_lightclock_tick_as_measured_from_shell(proper_time):
  for r in __r_domain :
    proper_time[ (r - __r_domain[0]) * __r_iteration_direction ] =  ..
      np.sqrt(1 - (2*M)/(r*__r_step_resolution)) * __time_step_resolution
```

Knowing that time has dimensions of length in GR, due to scaling by $c$, we could naively ask about using `__r_step_resolution` or `__time_step_resolution`. At the surface, this feels like a straightforward answer, but there's an added layer of complexity.

We're talking about time and the resolution should depend on the precision as specified by $dt_{bk}$. However, at the same time, we're talking about what the difference in clock tick rates are at each distance along some `r` interval. The context is the deciding factor: we want to measure the disagreement between the physical observation and the geometric expectation along some distance, therefore we iterate over `__r_domain` and scale `r` by $dr_{bk}$.

\pagebreak

#### Breaking the Monolith

With the plots of physical vs geometric measurements working as expected, it was time to refactor the code. Most of what existed in `dimensionless_plot.py` was already fairly descriptive and narrative, there wasn't much to add in terms of comments or renaming variables. What was apparent, however, was the growing friction in changing the runtime parameters to see how the plots changed for different mass black holes or for different intervals.

One of the original design concepts behind Cartographer was to allow a configuration file to be supplied to specify these parameters. Then the comparision between different situations would be a simple matter of swapping out configuration files and allowing for a method to easily save the state that generated a series of plots.

This is then the perfect time to start dividing up sections of the code into logical files:

```
/Cartographer/
              spacetime/
                        schwarzschild.py
              Cartographer.py
              configuration_reader.py
              coordinate_array.py
              runtime_configurations.yaml
```

Cartographer, as its name suggests, should really just focus on generating the plots, and while being the namesake of the project, should also be the host of the service.

```
Cartographer.py
    | -- make_plot(...)
    | -- main(...)
```

In order to begin to calculate or plot anything, we first need to read in the configuration file:

``` python
import configuration_reader as cf_r

def main():
  coordinate_domains = cf_r.get_configuration_settings()
  if len(coordinate_domains) == 0:
    print('''Error in loading runtime_configurations.yaml.
     Check to make sure the file is located in the 
     same directory and has content.''')
    return
```

`configuration_reader.py` only has one function: parse the content we've specified in the configuration file. Since its is the only one who does any reading, in future iterations, it should also house any of the error checking for badly formatted config files. `get_configuration_settings()` does a simple reading of the `runtime_configurations.yaml` file and rips out the content.

I choose the `yaml` type as it offers benefits to both interacting as a user and for the program, as shown in the excerpt below:

```yaml
physical_constants: 
  speed_of_light: 1
  gravitational_constant: 1
spacetime_parameters:
  mass: 
    in_meters: 500
  charge: 0
  angular_momentum: 0
coordinate_domains:
  - dimension: "time"
    start: 0
    stop: 10
    step: 0.1
  - dimension: "reduced circumference" # as factors of M
    start: 2
    stop: 100
    step: 0.1
```

The indentation and dashes allow for logical distinction when the file is being read, similar to JSON files. Essentially, at the uppermost level, we have a dictionary with three keys: `physical_constants`, `spacetime_parameters`, and `coordinate_domains`. From there, its just another logical extension into further nested dictionaries. The power behind this implementation, is that not everything has to be specified.

By removing the `- dimension: "time"` entry, Cartographer will simply not create the time coordinate array. Also, by specifying the values for the physical constants here, it removes the possibility for incorrect plots when trying to use more accurate values for $c$ and $G$, and unintentionally forgetting to change one (or both) after running test data.

`schwarzschild.py` is where most of this data should live during runtime: as the arbiter of spacetime geometry, it should know the mass of the black hole and be responsible for answering questions asked about the geometry. I'm not sure exactly how to deal with different geometeries explicitly in the future, but for the moment, this seems to be the logical way forward.

`coordinate_array.py` is just a wrapper class for the `numpy` arrays.

```python
class Coordinate_Array:

  def __init__(self, start = int(), stop = int(), resolution = float()):
    dimensionless_start_value = remove_dimensions(start, resolution)
    dimensionless_stop_value = remove_dimensions(stop, resolution)
    self.step_resolution = resolution
    self.iteration_direction = (1 if (start < stop) else -1 )
    self.domain = np.arange( 
        dimensionless_start_value,
        dimensionless_stop_value,
        self.iteration_direction
      )

def remove_dimensions(value_to_remove_dimensions_from, dimensions_to_remove):
    return int(value_to_remove_dimensions_from / dimensions_to_remove)

def add_dimensions(value_to_add_dimensions_to, dimensionful_variable):
    return (value_to_add_dimensions_to * dimensionful_variable)
```

The only downside to splitting everything up into silos was that I still needed a way to ask about $dr_{bk}$ and $dt_{bk}$, but couldn't find out a way that using just the $initial$ and $final$ values with the $size$ of the array. 

\pagebreak

### Speed In Schwarzschild

#### Optimizations

The next logical step for plot functionality was implementing Equation 21 from *Exploring Black Holes*:

$$\frac{dr}{dt}=-\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}$$

```py
def get_bk_speed_at_geometric_position(r_coord):
  M = get_blackhole_mass_in_meters()
  speed = np.ones(np.shape(r_coord.domain))
  for r in r_coord.domain:
    speed[(r - r_coord.domain[0]) * r_coord.iteration_direction] = - (1 - (2*M)/(r*r_coord.step_resolution)) * np.sqrt((2*M)/(r*r_coord.step_resolution))
  return speed
```

Both the speed measure by the Bookkeeper and the speed recorded as the stone passes each shell were trivial to implement after having broken the monolith, however, runtimes have started to increase. In parallel, I had been consuming some content about `numpy` and `python` and was inspired to benchmark the results of this function call to see just how bad it was.

Fortunately, timing is very straightforward:

```py
import time
...
start = time.perf_counter()
speed = #result of function call
stop = time.perf_counter()
print(f"Elapsed time: {stop-start}")
```

Where `time.perf_counter()` is described by the [docs](https://docs.python.org/3/library/time.html#functions) as:

> Return the value (in fractional seconds) of a performance counter, i.e. a clock with the highest available resolution to measure a short duration. It does include time elapsed during sleep and is system-wide. The reference point of the returned value is undefined, so that only the difference between the results of two calls is valid.

At the time, I was calculating $dr_{shell}(r)$ and $dt_{shell}(r)$ for a black hole with mass $M=500\ meters$, an $r$-coordinate interval from $(2M+1,\ 100M)$, and a $dr_{bk}=0.1\ meters$. This meant that `r_coord` was an array with $4.8999\times 10^5$ elements. Recall the functional definitions:

```python
def bookkeeper_meter_stick_as_measured_from_shell(proper_distance):
  for r in __r_domain :
    proper_distance[ (r - __r_domain[0]) * __r_iteration_direction ] = .. 
      __r_step_resolution / np.sqrt(1 - (2*M)/(r*__r_step_resolution))

def bookkeeper_lightclock_tick_as_measured_from_shell(proper_time):
  for r in __r_domain :
    proper_time[ (r - __r_domain[0]) * __r_iteration_direction ] =  ..
      np.sqrt(1 - (2*M)/(r*__r_step_resolution)) * __time_step_resolution
```

The corresponding computation time for both operations came out to be:

```
  Distance: 1.7440086
  Time: 1.7440086
Elements in array: 489990
```

And, in this scenario, would scale linearly with the size of the array: (Just changing $dr_{bk}$ to $0.01\ meters$)

```
  Distance: 17.5974859
  Time: 17.728677
Elements in array: 4989990
```

So, we're already at almost 2 seconds of runtime per function call, and these are the two simplest equations I can numerically evaluate in the entirety of General Relativity. As mentioned above, after reading some more detail about the `Numpy` documentation, I noticed that `np.multiply` and the other maths functions can *operate in place*. Essentially, the way the following statement would evaluate `proper_distance[ ... ] = __r_step_resolution / np.sqrt(1 - (2*M)/(r*__r_step_resolution))` is that this calculation would occur for each `r`. On its face, this isn't a ground breaking statement, but during the runtime, `__r_step_resolution` is constant, as well as `r_coord`. So, at the very least, we're doubling the amount of calculations that need to occur. Caching the results in a global `CURVATURE_FACTORS` variable that calculates $1-\frac{2M}{r}$ for each `r` at the start of the program can almost cut the total elapsed time in half.

$$1-\frac{2M}{r}$$

The only thing that is not constant in this expression (in code) is the `r` from `r_coord`, but this is where we can actually start to leverage the power of `Numpy`. They have gone through great lengths to optimize operations like scalar multiplication, and by sacrificing some readability:

```py 
__r_step_resolution / np.sqrt(1 - (2*M)/(r*__r_step_resolution))
```

We can let the compiler optimize and reduce computation time by being very explict that each operation needs to occur to the entire array:

```py
ALMOST_CURVATURE_FACTOR = np.reciprocal(np.true_divide(np.multiply(r_coord_local.domain, r_coord_local.step_resolution), 2*M))
CURVATURE_FACTORS = np.sqrt(np.ones(np.shape(r_coord_local.domain)) - ALMOST_CURVATURE_FACTOR)
```

Where `ALMOST_CURVATURE_FACTOR` is $2M/r$. The caching of `CURVATURE_FACTORS` means we save the entire time it would take to do it again, and then since both functions are just scalar multiples of `CURVATURE_FACTORS`, their definition simplifies (at the cost of readability):

```py 
def get_bookkeeper_meter_stick_as_measured_from_shell(dr):
  return np.multiply(np.reciprocal(get_curvature_factor()), dr)

def get_bookkeeper_lightclock_tick_as_measured_from_shell(dt):
  return np.multiply(get_curvature_factor(), dt)
```

And the resulting computation time for the same parameters:

```
Old:
  Distance: 17.5974859
  Time: 17.728677
Optimized:
  Curvature: 0.0580259
  Distance: 0.007410
  Time: 0.00830
Elements in array: 4989990
```

That is a $99.79\%$ reduction in runtime.

\pagebreak

#### Limiting Cases

For a stone (read: some arbitrary low-mass object), the simplest path it can traverse in Schwarzschild is to fall radially into the Black Hole, starting at rest. For the sake of this arguement, what we are doing is stating that the stone is starting at some $r$-coordinate so far away, $r\ggg 2M$, that the curvature factor, $1-2M/r$ is approaching unity and the energy of the stone is just its rest mass. From this, we can describe energy (per unit mass) in Schwarzschild geometry as being affected by the curvature (Equation 12, Page 3-9 [1]):

$$\frac{E}{m} = \left(1-\frac{2M}{r}\right)\frac{dt}{d\tau} \qquad \Rightarrow \qquad 1 = \left(1-\frac{2M}{r}\right)\frac{dt}{d\tau}$$

We can then track the change using geometric coordinates (from the Bookkeeper) through using the line element for proper time, $d\tau$. From the Bookkeeper's *frame*, the stone moves as described by $$d\vec{r}= {\left(1-\frac{2M}{r}\right)}^{1/2} dt\hat{t} - {\left(1-\frac{2M}{r}\right)}^{-1/2} dr \hat{r}$$ Solving the energy expression for $d\tau$, we set both expressions equal to eachother:

$$\begin{aligned}
  1 &= \left(1-\frac{2M}{r}\right)\frac{dt}{d\tau}\\
  d\tau^2 &= \left(1-\frac{2M}{r}\right)^2 dt^2
\end{aligned} \qquad \begin{aligned}
  d\tau^2 &= -ds^2 = d\vec{r}\cdot d\vec{r} \\
    &= \left(1-\frac{2M}{r}\right)dt^2 - {\left(1-\frac{2M}{r}\right)}^{-1} dr^2
\end{aligned}$$

We then solve for $dr/dt$:

$$\begin{aligned}
  \left(1-\frac{2M}{r}\right)^2 dt^2 &= \left(1-\frac{2M}{r}\right)dt^2 - {\left(1-\frac{2M}{r}\right)}^{-1} dr^2 \\
  \left(1-\frac{2M}{r}\right) &= 1 - {\left(1-\frac{2M}{r}\right)}^{-2} \frac{dr^2}{dt^2} \\
  -\frac{2M}{r} &= - {\left(1-\frac{2M}{r}\right)}^{-2} \frac{dr^2}{dt^2} \\
  \frac{dr^2}{dt^2} &= \left(1-\frac{2M}{r}\right)^2 \frac{2M}{r} \\
  \frac{dr}{dt} &= -\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}
\end{aligned}$$

We have taken the negative sign for the expression, as a decreasing change corresponds to a radial in-fall (positive describes outward motion). This is the description of the Bookkeeper's measurements as the stone falls in. Note that, with *Exploring Black Holes*, all instances of $c$ have been surpressed, so this relation is giving speeds as factors of $c$. Now, if we want to examine what the speed is measured by a shell observer, we can substitute the relations for $dr_{shell}$ and $dt_{shell}$ into this expression:

$$\begin{aligned}
  \frac{dr_{bk}}{dt_{bk}} &= -\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}\\
  \frac{\frac{dr_{shell}}{\sqrt{1-\frac{2M}{r}}}}{\frac{dt_{shell}}{\sqrt{1-\frac{2M}{r}}}} &= -\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}\\
  \frac{dr_{shell}}{dt_{shell}} &= -\sqrt{\frac{2M}{r}}
\end{aligned}$$

This can then be plotted as a function of $r$, where the value of $dr/dt_{shell}$ corresponds to the measured speed at the $r$-coordinate for that shell. Translating into code, this is fairly straight forward (and fast, given our optimizations!):

```py
def get_bookkeeper_speed_of_infalling_stone():
  return np.multiply(
      np.ones(np.shape(ALMOST_CURVATURE_FACTOR)) - ALMOST_CURVATURE_FACTOR,
      - np.sqrt(ALMOST_CURVATURE_FACTOR)
    )
    
def get_shell_speed_of_infalling_stone():
  return (- np.sqrt(ALMOST_CURVATURE_FACTOR))
```

And with this, we get the characteristic diverging behaviour: The Bookkeeper see's the stone's speed drop to 0 as it reaches the horizon while the shell observers near the horizon see the stone accelerating towards $-c$! 

#### Changing Perspective

The tricky bit is now to describe what a specific shell observer measures throughout the stone's entire journey. Previously, we've been using the value of $dr_{bk}$ to determine the basis for all measurements, but for a specific shell, that needs to be scaled by their view of things.

1. Redefine how we measure: everything should be based off of the observation shell's meter stick and light clock. Using Equations 21 and 24:

$$\begin{aligned}
dr_{obs\ shell} &= \frac{dr_{bk}}{\sqrt{1-\frac{2M}{r_{obs\ shell}}}} \\
dr_{bk} &= \sqrt{1-\frac{2M}{r_{obs\ shell}}} dr_{obs\ shell}
\end{aligned} \qquad
\begin{aligned}
dt_{obs\ shell} &= \sqrt{1-\frac{2M}{r_{obs\ shell}}} dt_{bk}\\
dt_{bk} &= \frac{dt_{obs\ shell}}{\sqrt{1-\frac{2M}{r_{obs\ shell}}}}
\end{aligned}$$

2. Change expression for speed to be scaled by these new measurements:

$$\begin{aligned}
\frac{dr}{dt} &= - \left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}\\
\frac{\sqrt{1-\frac{2M}{r_{obs\ shell}}} dr_{obs\ shell}}{\frac{dt_{obs\ shell}}{\sqrt{1-\frac{2M}{r_{obs\ shell}}}}} &= - \left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}\\
\frac{dr_{obs\ shell}}{dt_{obs\ shell}} &= - \left(\frac{1-\frac{2M}{r}}{1-\frac{2M}{r_{obs\ shell}}}\right)\sqrt{\frac{2M}{r}}\\
\end{aligned}$$

But this relation doesn't behave nicely. The curvature factor term sets the point of inflection for $dr/dt_{bk}$ at $6M$: until this $r$-coordinate, the Bookkeeper measures the stone to fall inwards at an increasing velocity and any $r$-coordinate beyond this decays towards $0$. This expression will behave nicely for shell observers at or above $6M$, but will lead to unphysical results below this threshold. For $r<6M$, the *vertex* stops translating to the left, but the function still needs to reach the value as described by $\sqrt{2M/r_{obs}}$ and this corresponds to the vertex translating *downward*, giving speed measurements greater than or equal to $-1$ for $r>2M$. This is a problem two-fold: not only is a massive object obtaining the speed of light, it will exceed it!

So, this expression is invalid, but it does still have some characteristic behavior that we need. Let's layout everything we know and what behavior the expression needs to have for it to be a physically admissible solution:

> TODO: Finish write up of work

\pagebreak

## Analysis of Differential Scattering for low-mass particles

### Simple case: Rain frame

### Increasing complexity

\pagebreak

# Conclusions

> TODO: Did Cartographer do what it set out to?

\pagebreak

# Acknowledgements

## People

- Tevian Dray
- Kathy Hadley
- Christopher Magone
- Greg Moulder
- Liz Gire
- Corrine Manouge

## Software

### Open-source

- Python 3.10
- Numpy
- Matplotlib
- PyYaml

- Desmos

### Corporations

- Microsoft
  - GitHub
  - VSCode (is an IDE too far? I guess its free, so might as well?)
- Wolfram
  - Mathematica
  - WolframAlpha

\pagebreak

# References

[1] E.F Taylor and J. A. Wheeler, *Exploring Black Holes: Introduction to General Relativity*. 

<br />

[2] J. R. Taylor, *Classical Mechanics*. 

<br />

[3] C. W. Misner, K. S. Thorne, and J. A. Wheeler, *Gravitation*. 

<br />

[4] C. Bambi, *Introduction to General Relativity: A Course for Undergraduate Students of Physics.* 

<br />

[5] J. R. Taylor, *Classical Mechanics*. 
<br />

> TODO: Add Hartle, *Black Holes*,

\pagebreak

# Appendices

## Glossary and Notation

> Everyone uses different signatures and mathematical notation, here's a list that compares common bits and attempts to map them in a unifying way.

## Special Relativity

> If you've completely forgotten 335, this is the base of what you need to know

## General Relativity

> Omit sub-sections, depending on the extent of Cartographer

### Schwarzschild

### Riessner-Nordstroem

### Kerr

## Cartographer

> TODO: To what extent should the code base be added?