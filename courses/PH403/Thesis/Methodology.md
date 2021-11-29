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
    \usepackage{float}
---

# Methodology

## Design Principles

> TODO: Guidelines and idealize criteria to inform decision making during synthesis and refactoring.

- MVP styled iteration
- Easy to use (goal: one year of experience, e.g. PH 36X)
- Performant (to a degree?)
    - Home/Personal PC use for non-extreme examples
    - Cache calcuations where possible
    - Optimize function calls to allow compiler optimizations
- Extendability
    - Remove implicit assumptions from code
    - SOLID

> TODO: Ripped from Proposal: "Plan of Work", Refine Later

We will study the equations of motion for massive and massless particles in the presence of curved spacetime. A Schwarzschild black hole will serve as the source of curvature for analysis of limiting cases that will be used as the foundation for sense making and error checking in computational runtimes. The project itself has been subdivided into three major phases: Scaffolding, Curving, and Refinement.
The core of the toolset depends on a series of key design and implementation decisions about the underlying framework. One of the key features is to have an intuitive code base for physicists to use, which implies a latticework of grid points mapping out the space. Ideally, this latticework will be agnostic with respect to the active geometry and type of curvature. This stage will focus on the creation of the latticework, its documentation and the manifestation of key mathematical tools such as differential scattering and the representation and parameterization of a geodesic. Examples of this design process are shown on the following page with Figure 1 and Figure 2.

> TODO: Replace if final implementation is no longer OOP.

\begin{figure}[H]
    \centering
    \caption{Latticework design implementation document detailing desired behaviour and properties. }
\end{figure}

\begin{figure}[H]
    \centering
    \caption{SpacetimeGeometry design implementation document outlining the use of object-oriented class inheritance to allow modularity for future different descriptions of curvature in spacetime and to ensure the framework does not implicitly assume any behaviour of the geometry: “Spacetime agnostic”. }
\end{figure}

The differential scattering cross-section has a general form that can be parameterized based off the impact parameter, $\sigma\left(b\right)=\int{\frac{d\sigma\left(b\right)}{d\Omega}\left(\theta,\ \phi\right)d\Omega}$ [5], but we will need to still solve the EOM, Equation 4, and mesh the two together. Care will need to be taken to avoid any implicit assumptions about the object traversing the spacetime to avoid unphysical geodesics and cross-sections: e.g., the impact parameter has a different form for massive versus massless particles [1,3]. Below, in Figure 3, the general user story has been mapped out to provide insight into the conceptual process of the toolset.

> TODO: Replace with final version's flow system. Maybe keep original for comparision

\begin{figure}[H]
    \centering
    \caption{Flow chart detailing the typical user story for interacting with the toolset. }
\end{figure}

\pagebreak

## The Core Design Process

> TODO: This is true at this stage, Refine as progress continues.

The underlying theme of iterating on and releasing a minimal viable product was chosen to facilitate efficent paritioning of the desired feature set along with fast implementation and iteration. By necessity, this required a simple core design process. In the early stages of synthesis, the algorithm was defined by five steps:

1. Find/Choose an Equation
2. Translate Equation to Python
3. Plot results of Equation
4. Verify results and implement changes as necessary
5. Refactor

### 1. Choose an Equation

> TODO: Move following paragraph to *Introduction: A Primer on Spacetime and Relativity*?

As mentioned in previous sections, each equation in GR very quickly increases in both mathematical and congnitive complexity. Therefore, it was paramount to start with the simplest descriptions in Schwarzschild: proper time and proper distance. Recall that we can simplify the line element (Equation $\ref{SchwarzschildWithC}$) by dictating what coordinates can change. Each corresponding invariant measurement is performed by finding the set of *rest* frames in which the change in spatial (or temporal) coordinates is minimized (typically zero)[^-21]. The corresponding invariant measurements for the stationary observers in Schwarzschild are then given as:

[^-21]: For proper distance, this is done be measuring the spacetime separation between two events that occur simultaneously; $t_{e1}=t_{e2}$, $dt=0$. Proper time is measured similarly: ${space}_{e1} = {space}_{e2}$, $d{space} = 0$.

\begin{equation}\label{ShellDistance}
    dr_{shell} = \left(1-\frac{2M}{r}\right)^{-\frac{1}{2}} dr
\end{equation}
\begin{equation}\label{ShellTime}
    dt_{shell} = \left(1-\frac{2M}{r}\right)^{\frac{1}{2}} dt
\end{equation}

### 2. Translate to Python

Given the relative simplicty of Equations $\ref{ShellDistance}$ and $\ref{ShellTime}$, the conversion to Python is straightfoward:

``` python
def get_proper_distance_for_shell(shell_r_coordinate, blackhole_mass_in_meters, dr):
  from math import sqrt
  return dr/sqrt(1-(2*blackhole_mass_in_meters)/shell_r_coordinate)

def get_proper_time_for_shell(shell_r_coordinate, blackhole_mass_in_meters, dt):
  from math import sqrt
  return sqrt(1-(2*blackhole_mass_in_meters)/shell_r_coordinate)*dt
```

While the translation from a mathematical expression to a functional call is easy, due note that the readability has already decreased by a factor. This can be mitigated by trying to write the functions with Physicists in mind: 

``` python
def get_proper_distance_for_shell(r, M, dr):
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

def get_proper_time_for_shell(r, M, dt):
  from math import sqrt
  return sqrt(1-(2*M)/r)*dt
```

However, the shorthand of using mathematical variable names does come at a cost. Recall, as noted in *Introduction: Computational Physics Background: "Variables, Dimensions, and their Representation"*, that the accepted design practices for *clean* code require variable names to be specific. "But why is using the variable names that allow a direct map between mathematical expression and progomatic representation not the *easiest* implementation?" At this stage, it most certaintly is, but we are also in the process of implementing the two simplest expressions in the simplest geometry for curved spacetime. Recall Equation $(\ref{GeneralSchwarzschildEOM})$ from *Introduction: Motivation*:

$$\frac{1}{2}\dot{r}^2 = \frac{E^2-kc^4}{2c^2} +k \frac{GM}{r} - \frac{ {L_z}^2 }{2r^2} + \frac{GM {L_z}^2}{c^2 r^3}$$

In the later parts of this thesis, my hope is that this equation will have lost some of its confounding nature, but that will be accomplished through plots and descriptions of objects interacting with the curvature, not through piece by piece deconstruction of the variables (at least, directly). A computational model of a system should be able to be parsed by someone who is fluent in the language of the program, iregardless if they have the model's domain knowledge, just as a mathematican should be able to parse a series of equations describing physical phenoma.

### 3. Plot

This portion definitely falls within the realm of an in-class assignment that can be given to a student in the PH 36X series with a simple implementation using Matplotlib:

``` python
import numpy as np
import matplotlib.pyplot as plt

def get_proper_distance_for_shell(r, M, dr):
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

M = 50
dr = 1

r_coordinates = np.arrange(2*M+dr, 15*M, dr)
proper_distance = np.zeros(r_coordiantes.shape)

for r in r_coordinates:
    proper_distance[r-2*M+dr] = get_proper_distance_for_shell(r, M, dr)

plt.plot(r_coordinates, proper_distance)
plt.show()
```

### 4. Verify Results

Remembering that we are fundamently ploting a function that takes the form of $$f(x) = \frac{1}{\sqrt{1-\frac{1}{x}}}$$ It is very easy to compare the general shapes between the output generated by Cartographer and any other various plotting software. As more complex expressions are represented and interpreted by Cartographer, this stage will become more time consuming as the chance for mistakes increases in greater proportion than complexity. Also, more literature research will need to be conducting in conjuction to ensure that the results are comparable or reproducible to already existing figures.

> TODO: Figure comparision of above code versus Mathematica (or Desmos?)

### 5. Refactor

\pagebreak

## Measuring Performance and Optimizations

> TODO: Ripped from *Progress Report 11/22*, Refine Later

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

## SOLID, KISS, and DRY: Breaking Monoliths

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