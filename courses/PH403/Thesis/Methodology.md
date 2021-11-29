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

