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

$$\ $$

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

The core of the toolset depends on a series of key design and implementation decisions about the underlying framework. One of the key features is to have an intuitive code base for physicists to use, which implies a latticework of grid points mapping out the space. Ideally, this latticework will be agnostic with respect to the active geometry and type of curvature. This stage will focus on the creation of the latticework, its documentation and the manifestation of key mathematical tools such as differential scattering and the representation and parameterization of a geodesic. Examples of this design process are shown on the following page with Figure $\ref{DesignProcess1}$ and Figure $\ref{DesignProcess2}$.

> TODO: Replace if final implementation is no longer OOP.

\begin{figure}[H]
    \centering
    \caption{\label{DesignProcess1}Latticework design implementation document detailing desired behaviour and properties. }
\end{figure}

\begin{figure}[H]
    \centering
    \caption{\label{DesignProcess2}SpacetimeGeometry design implementation document outlining the use of object-oriented class inheritance to allow modularity for future different descriptions of curvature in spacetime and to ensure the framework does not implicitly assume any behaviour of the geometry: “Spacetime agnostic”. }
\end{figure}

The differential scattering cross-section has a general form that can be parameterized based off the impact parameter, $\sigma\left(b\right)=\int{\frac{d\sigma\left(b\right)}{d\Omega}\left(\theta,\ \phi\right)d\Omega}$ [5], but we will need to still solve the EOM, Equation 4, and mesh the two together. Care will need to be taken to avoid any implicit assumptions about the object traversing the spacetime to avoid unphysical geodesics and cross-sections: e.g., the impact parameter has a different form for massive versus massless particles [1,3]. Below, in Figure $\ref{FlowChart}$, the general user story has been mapped out to provide insight into the conceptual process of the toolset.

> TODO: Replace with final version's flow system. Maybe keep original for comparision

\begin{figure}[H]
    \centering
    \caption{\label{FlowChart}Flow chart detailing the typical user story for interacting with the toolset. }
\end{figure}

\pagebreak

## The Core Design Process

> Notes: I'm planning on having introduced concepts of SR and GR in the introduction as well as some computational things. That is, a reader going in order will know the context of a "geodesic" and "geodesic equation" by reaching this section.

> TODO: Possibly move the following paragraph to the preceeding section $\rightarrow$ Define/introduce minimal viable product (MVP) there?

To facilitate periodic testing and quick implementation, the desired functionality of Cartographer was divided into a series of milestones. Each milestone was choosen such that it gradually increased in complexity and laid the groundwork for subsequent milestones. This iterative design process is often referred to the minimal viable product: at the conclusion of each milestone, all corresponding functionality has been implemented and the code has been cleaned up and reorganized (refactored). 

This design process can be distilled into a series of five steps:

1. Choose an Equation
2. Translate Equation to Python
3. Generate Visualization for Equation
4. Verify Results and Change as Necessary
5. Refactor

The end goal of Cartographer is to generate visualizations correspoding to light and low-mass particles moving through Schwarzschild spacetime. As mentioned previously in *1.1 Motivation*, these geodesic equations are complex but we can leverage that they are the result of algebraic compositions from simpler expressions. This naturally allows us to work backwards from the end goal of visualizating something like Equation $(\ref{GeneralSchwarzschildEOM})$ to the building blocks of describing the curvature of spacetime. 

> TODO: Simple Illiustration? Scattering -> GeneralSchwarzschildEOM (general motion in schwarz) -> motion with angular momentum -> orbits -> just radial motion -> just curvature
> Also callout sections/subsections?

| GeneralSchwarzschildEOM -> motion with angular momentum -> orbits | radial motion | curvature factors |
| -- | -- | -- |
| 3.3 Angular Momentum, Effective Potential, and Orbits | 3.2 Gaining Speed and Radial Geodesics | 3.1 Distance, Time, and Embedding Diagrams |

The following subsections provide additional context for each step by detailing the process of implementing the building blocks. These subsections focus primarly on the computational implementation whereas *3.1 Distance, Time, and Embedding Diagrams* offers an analysis of the resulting visualizations and the physics behind them. 

### 1. Choose an Equation

> TODO: Move derivation to background section for GR in the Intro? Or have conceptual introduction there and leave this more mathematical approach here?

We begin by isolating the descriptions of proper time and proper distance as measured by a shell observer using the line element (Equation $\ref{SchwarzschildWithC}$). Recall from *1.2.3 Space into Spacetime* that proper time and distance are invariant with respect to changing reference frames. We can introduce the shorthand of $f(r)= \sqrt{1 - \frac{2M}{r}}$ and $d^2\Omega=\sin^2{\theta}d^2\varphi + d^2\theta$ to simplify the expression. other than $dr$ or $dt$, equal to $0$ we can obtain the expressions which allow us to discuss proper time and distance with respect to any stationary observer:

$$ds^2= - f(r)^2 (dt^2) + \frac{dr^2}{f(r)^2} + r^2 d^2\Omega$$

Then by setting $d^2\Omega=0$, we simplify the description of the line element to be changes in $r$ or $t$. Examining just a change in $r$ or $t$, we derive proper distance and time for the shell observer as Equations $\ref{ShellDistance}$ and $\ref{ShellTime}$:

\begin{equation}\label{ShellDistance}
    dr_{shell} = \left(1-\frac{2M}{r}\right)^{-\frac{1}{2}} dr
\end{equation}
\begin{equation}\label{ShellTime}
    dt_{shell} = \left(1-\frac{2M}{r}\right)^{\frac{1}{2}} dt
\end{equation}

$$\ $$

### 2. Translate to Python

Having obtained our two equations to implement, the next step is to represent them in Python. Given the relative simplicty of Equations $\ref{ShellDistance}$ and $\ref{ShellTime}$, they naturally lend themselves to being respresented as Python functions:

``` python
def dr_shell(r, M, dr):
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

def dt_shell(r, M, dt):
  from math import sqrt
  return sqrt(1-(2*M)/r)*dt
```

Like the funcitonal form of Equations $\ref{ShellDistance}$ and $\ref{ShellTime}$, these functions evaluate $dr_{shell}$ and $dt_{shell}$ for a specific $r$-coordinate (coresponding to the shell's location).

$$\ $$

### 3. Generate Visualization for Equation

> TODO: Keep/remove first sentence?

This portion falls within the realm of an in-class assignment that can be given to a student in the PH 36X series, as it requires only basic familarity with Matplotlib and NumPy. Using the distance function as defined in the previous subsection (`dr_shell(...)`), we choose convient values for `M` and `dr` initially to be able to easily inspect the resulting plot for uncharacteristic behaviour.. Specific values of `M` and `dr` will be used in *3.1 Distance, Time, and Embedding Diagrams* to verify the expected results from literature.

``` python
import numpy as np
import matplotlib.pyplot as plt

def dr_shell(r, M, dr):
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

M = 5
dr = 1
```

Since there is a coordinate singularity at $r=2M$ and shell observers only exist outside the event horizon (see *1.2.4 Mass is Curvature*), we need to adjust the interval of possible $r$-coordinates accordingly. We also need the size of the interval to be in a nice middle ground: just far enough away to display the shape of the plot and close enough to avoid supressing the desired behaviour. ; programmatically, 

``` python
r_coordinates = np.arange(2*M+dr, 15*M, dr)
proper_distance = np.zeros(r_coordinates.shape)
```

We accomplish this by making the interval exclusive, $(2M,15M)$, and adding $dr$ to $2M$. Trial and error is used to find that $15M$ works as desired for the choosen values of `M=5` and `dr=1`. The figure generated by this implementation is shown in the following subsection, *2.2.4 Verify Results and Change as Necessary*, as Figure $\ref{DesignProcessVerify_Python}$.

``` python
for r in r_coordinates:
  proper_distance[r-(2*M+dr)] = dr_shell(r, M, dr)

plt.plot(r_coordinates, proper_distance)
plt.title(f"Proper distance of {dr=} meters as measured by each shell\n observer with a
 blackhole of {M=} meters")
plt.xlabel("r-coordinate of shell")
plt.ylabel("Distance measured by shell")
plt.savefig(fname="CoreDesign_Plot.png")
```

$$\ $$

### 4. Verify Results and Change as Necessary

Recall that for distance, we are plotting a function that takes the general form of 

$$f(x) = \frac{1}{\sqrt{1-\frac{1}{x}}}$$

With this in mind, it is very easy to compare the general shapes between the output generated by Cartographer and any other plotting software. Using the following Mathematica code, we compare the two functions by considering their concavity, shape, and behaviour as $x\rightarrow\infty$.

```Mathematica
dr = 1; M = 5;
f[x_] := dr/Sqrt[1 - (2*M)/x]
Plot[f[x], {x, 2*M + dr, 15*M}, PlotRange -> {{2*M, 15*M}, {1, 3.5}}, 
 AxesLabel -> {"x", "f(x)"}, 
 PlotLabel -> 
  "Mathematica Plot for Comparision of Cartographer Output", 
 ImageSize -> Large]
```

\begin{figure}[H]
  \begin{subfigure}[b]{0.5\textwidth}
      \centering
      \includegraphics{CoreDesign_Plot.png}
      \caption{Cartographer}
      \label{DesignProcessVerify_Python}
  \end{subfigure}
  \hfill
  \begin{subfigure}[b]{0.5\textwidth}
      \centering
      \includegraphics{CoreDesign_PlotMathematica.png}
      \caption{Mathematica}
      \label{DesignProcessVerify_Mathematica}
  \end{subfigure}
  \caption{Displayed on the left, \ref{DesignProcessVerify_Python} is the plot produced by the Python representation of Equation \ref{ShellDistance}. On the right, \ref{DesignProcessVerify_Mathematica} demonstrates Mathematica's interpretation. Note that both visualizations have the same behaviour: monotonically decreasing and asympotically approaching $f(x)=1$ as $x\rightarrow\infty$.}
\end{figure}

> TODO: Attempt to align formatting between Mathematica and Python plots? The difference is definitely detracting, but they are different software visualizations. I would like to unify them, but it comes at a cost (besides time). If one of my intents is to have code present that can be ripped out and thrown into someone else's computer for reproducibility, then I have to include all the extra formatting line as well. This'll increase the size of each codeblock along with intensity. Maybe have the full Mathematica code in the appendix then?

As more complex expressions are represented and interpreted by Cartographer, this stage becomes more time consuming due to the increased chance for mistakes in derivation and/or implementation. This stage is also when direct comparisions to any exisiting visualizations from literature are conducted. 

$$\ $$

### 5. Refactor

Refactoring is a catch-all term for:

- finding and fixing bugs from the result of adding new code or using existing code differently
- reorganizing code into logical divisions
- renaming variables to more clearly denote their purpose

The following is an example of refactoring the code written in the previous subsections. Recall that the functions and variables were given the same names as their mathematical counterparts:

``` python
        def dr_shell(r, M, dr):                   def dt_shell(r, M, dt):
          from math import sqrt                     from math import sqrt
          return dr/sqrt(1-(2*M)/r)                 return sqrt(1-(2*M)/r)*dt
```

$$dr_{shell} = \left(1-\frac{2M}{r}\right)^{-\frac{1}{2}} dr, \qquad dt_{shell} = \left(1-\frac{2M}{r}\right)^{\frac{1}{2}} dt$$

While the two representations are almost identitcal, especially for those used to representing math equations in LaTeX, the names of the functions and variables are not *self-narrating*. Therefore, comments denoting the intention and use of each variable are expected. 

``` python
def dr_shell(r, M, dr):
  """Returns the proper distance for 'dr' as measured by the shell located at 'r' from a 
   blackhole of mass 'M'. Only valid for r>2M.
  
  'M' is the mass of the blackhole in meters
  'r' is the r-coordinate of the shell
  'dr' is the length measured by the bookkeeper
  """
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

def dt_shell(r, M, dt):
  """Returns the proper time for 'dt' as measured by the shell located at 'r' from a
   blackhole of mass 'M'. Only valid for r>2M.
  
  'M' is the mass of the blackhole in meters
  'r' is the r-coordinate of the shell
  'dt' is the time measured by the bookkeeper
  """
  from math import sqrt
  return sqrt(1-(2*M)/r)*dt
```

This, however, is treated as the bare minimum in being a good custodian of the code. Very often comments are not kept up-to-date with the changes to a function[^-21]. Instead, the programming communtity recommends that the code be self documenting: variable names should be descriptive and offer insight into the type of object they represented and that explicit programming statements are easier to understand than their elegant and brief counter-parts. These *best practices* are recommendations agreeded upon by the larger software development community. The Python organization takes this a step further by formally representing their community's best practices in the style guide released as [PEP 8](https://www.python.org/dev/peps/pep-0008/) [6]. By explicitly naming each variable (and function), we can free up the comments to provide a summary of the function's behaviour and reference the derivation of the expression.

[^-21]: An equivalent analogy are the pictures or diagrams included with many problem statements in math and physics. If they are not outright wrong, they end up being deceiving by misrepresenting angles, relative sizes, or trajectories.

``` python
def get_corresponding_proper_distance_for_shell(
    shell_r_coordinate, 
    blackhole_mass_in_meters, 
    bookkeeper_distance_measured
  ):
  """Returns the proper distance of `bookkeeper_distance_measured` as measured by
   the shell at `shell_r_coordinate` in Schwarzschild. Only valid for r>2M.

  This is the implementation of Equation $\ref{ShellDistance}$ from the Thesis. 
  Alternatively, this is derived and given in 'Exploring Black Holes' by E.F Taylor 
  and J. A. Wheeler as Equation 12 from Page 2-22. Reference: [1].
  """
  from math import sqrt
  return bookkeeper_distance_measured/sqrt(
      1 - (2*blackhole_mass_in_meters)/shell_r_coordinate
    )

def get_corresponding_proper_time_for_shell(
    shell_r_coordinate, 
    blackhole_mass_in_meters, 
    bookkeeper_time_measured
  ):
  """Returns the proper time of `bk_time_measured` as measured by the shell at 
  `shell_r_coordinate` in Schwarzschild. Only valid for r>2M.

  This is the implementation of Equation $\ref{ShellTime}$ from the Thesis. 
  Alternatively, this is derived and given in 'Exploring Black Holes' by E.F Taylor 
  and J. A. Wheeler as Equation 19 from Page 2-23. Reference: [1].
  """
  from math import sqrt
  return sqrt(1 - (2*blackhole_mass_in_meters)/shell_r_coordinate) 
    * bookkeeper_time_measured
```

> TODO: Add further example where we use lessons learned/introduced from *1.3.2 Variables, Dimensions, and their Representation*? `shell_r_coordinate` $\rightarrow$ `dimensionless_shell_r_coordinate`; make the `r_coordinates` array dimensionless and introduce the `r_coordinate_resolution` scaling factor?

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
    speed[(r - r_coord.domain[0]) * r_coord.iteration_direction] = - (1 - (2*M)/
      (r*r_coord.step_resolution)) * np.sqrt((2*M)/(r*r_coord.step_resolution))
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

So, we're already at almost 2 seconds of runtime per function call, and these are the two simplest equations I can numerically evaluate in the entirety of General Relativity. As mentioned above, after reading some more detail about the `NumPy` documentation, I noticed that `np.multiply` and the other maths functions can *operate in place*. Essentially, the way the following statement would evaluate `proper_distance[ ... ] = __r_step_resolution / np.sqrt(1 - (2*M)/(r*__r_step_resolution))` is that this calculation would occur for each `r`. On its face, this isn't a ground breaking statement, but during the runtime, `__r_step_resolution` is constant, as well as `r_coord`. So, at the very least, we're doubling the amount of calculations that need to occur. Caching the results in a global `CURVATURE_FACTORS` variable that calculates $1-\frac{2M}{r}$ for each `r` at the start of the program can almost cut the total elapsed time in half.

$$1-\frac{2M}{r}$$

The only thing that is not constant in this expression (in code) is the `r` from `r_coord`, but this is where we can actually start to leverage the power of `NumPy`. They have gone through great lengths to optimize operations like scalar multiplication, and by sacrificing some readability:

```py
__r_step_resolution / np.sqrt(1 - (2*M)/(r*__r_step_resolution))
```

We can let the compiler optimize and reduce computation time by being very explict that each operation needs to occur to the entire array:

```py
ALMOST_CURVATURE_FACTOR = np.reciprocal(np.true_divide(np.multiply(
    r_coord_local.domain, 
    r_coord_local.step_resolution
  ), 2*M))
CURVATURE_FACTORS = np.sqrt(np.ones(np.shape(r_coord_local.domain))
   - ALMOST_CURVATURE_FACTOR
  )
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
