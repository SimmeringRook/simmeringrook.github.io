---
title: "Cartographer: Using Python to Create Maps of Curved Spacetime and Differential Scattering Cross-sections of Low-Mass Objects about a Schwarzschild Black Hole"
author:
  - Thomas Knudson `\\\\`{=latex} Advised by Dr. Kathryn Hadley
subtitle: "Department of Physics, OSU"
date: December 6, 2021
geometry:
 - a4paper
 - margin=2cm
toc: true
toc_depth: 2
graphics: yes
header-includes: |
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usepackage{fancyhdr}
    \usepackage{float}
    \usepackage{subcaption}
    \pagestyle{fancy}
---

$$\ $$

\pagebreak

\listoffigures

\pagebreak

\listoftables

> TODO: Add tables? Will I have any tables?

\pagebreak

# Abstract {-}

> TODO: Figure out how modify pandoc's template to move about table of contents.

\pagebreak

# Introduction

Galilean relativity is the model we use to describe relative velocities in everyday life and is fairly robust, requiring extremes to find the breaking points. Einstein’s famous thought experiment about light moving on a train is the perfect analog for describing problem involving Global Positioning System (GPS) Satellites and thier transmissions to Earth. Using Galilean relativity, we can illustrate the physical situation like in Figure 1, however, anything beyond simple kinematics fails.

\begin{figure}
  \centering
  \begin{tikzpicture}

  % create coordinates
  \coordinate (O) at (0,0);
  \coordinate (P) at (8,0);
  \coordinate (V) at (8,2);

  % Earth
  \node[circle,draw,text=white,fill=gray,minimum size = 3cm] (c1) at (O) {Earth};

  % Satellite
  \node[circle, draw] (c2) at (P) {};
  \node at (c2) [below, right] {$\ $ GPS Satellite};

  % Label the radius
  \draw[dashed] (c1) -- (c2) node [midway, below] {$2.02\times 10^7\ m$};

  % Show velocity
  \draw[stealth-] (V) --++ (c2) node [midway, right] {$3.861\times 10^3\ m/s$};

  \end{tikzpicture}
  \caption{Galilean description of the relative velocities between Earth and a GPS Satellite. Source: https://earthobservatory.nasa.gov/features/OrbitsCatalog.}
  \label{gpsGalileo}
\end{figure}

> TODO: Reference figure 2 to highlight $\gamma$

In short, each GPS satellite periodically transmits location data alongside a timecode (TODO: Source). Using special relativity (SR), we find a scaling factor—typically $\gamma$—that represents the strength of length contraction and time dilation caused by the relative velocity. To calculate this factor, we must transition from the Galilean model (treating space and time distances  separately) to SR’s spacetime. However, measurement and theory would still disagree on the time between ticks of Earth’s and the GPS’s light-clocks: we have failed to consider the effect of gravity.

\begin{figure}
  \centering
  \begin{tikzpicture}

  % create coordinates
  \coordinate (O) at (0,0);
  \coordinate (P) at (8,0);
  \coordinate (V) at (8,2);

  % Earth
  \node[circle,draw,text=white,fill=gray,minimum size = 3cm] (c1) at (O) {Earth};

  % Satellite
  \node[circle, draw] (c2) at (P) {};
  \node at (c2) [below, right] {$\ $ GPS Satellite};

  % Label the radius
  \draw[dashed] (c1) -- (c2) node [midway, below] {$2.02\times 10^7\ m$};

  % Show velocity
  \draw[stealth-] (V) --++ (c2) node [midway, right] {$3.861\times 10^3\ m/s$};

  \end{tikzpicture}
  \caption{TODO: Update figure.}
  \label{gpsSR}
\end{figure}

By expressing the intensity of a massive body’s gravitational field as curvature, we discover and are able to correct for an additional set of length contraction and time dilation. This geometric model is called Schwarzschild Geometry and is the simplest solution to Einstein’s field equations involving a single massive object that is non-rotating. 

While we now have a theory that provides extremely accurate predictions, we subtly sacrificed a lot along the way. In Galilean relativity, we could easily switch from reference frame to reference frame and agree on what all observers measured: distance, time, relative velocities, and order of events. As the relative speed of objects increased, we had to switch to special relativity, but lost: observers agreeing on the order of events (see the “barn and pole” paradox). Finally, in using general relativity (GR) to correctly unify observers’ measurements in the presence of a gravitational field, we lost the notion of relative velocity.

We will first review the notions of proper time, proper distance, and geodesics in GR and how to use the line element to measure separation in spacetime and how to represent it computationally (Sections 2.1-2.2). Then we will refresh on differential scattering cross-sections of light about an object (Section 2.3) in preparation for examining the scattering caused by the curvature of spacetime. Section 3 focuses on the generation and analysis of visualizations depicting simple and complex geodesics in the Schwarzschild geometry.

\pagebreak

# Background

## Motivation {#motivation}

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

$$\ $$

## A Primer on Spacetime and Relativity

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

$$\ $$

## The Core Design Process

> Notes: I'm planning on having introduced concepts of SR and GR in the introduction as well as some computational things. That is, a reader going in order will know the context of a "geodesic" and "geodesic equation" by reaching this section.

> TODO: Possibly move the following paragraph to the preceding section $\rightarrow$ Define/introduce minimal viable product (MVP) there?

To facilitate periodic testing and quick implementation, the desired functionality of Cartographer was divided into a series of milestones. Each milestone was chosen such that it gradually increased in complexity and laid the groundwork for subsequent milestones. This iterative design process is often referred to the minimal viable product: at the conclusion of each milestone, all corresponding functionality has been implemented and the code has been cleaned up and reorganized (refactored).

This design process can be distilled into a series of five steps:

1. Choose an Equation
2. Translate Equation to Python
3. Generate Visualization for Equation
4. Verify Results and Change as Necessary
5. Refactor

The end goal of Cartographer is to generate visualizations corresponding to light and low-mass particles moving through Schwarzschild spacetime. As mentioned in $\ref{motivation}$, these geodesic equations are complex but we can leverage that they are the result of algebraic compositions from simpler expressions. This naturally allows us to work backwards from the end goal of visualizing something like Equation $(\ref{GeneralSchwarzschildEOM})$ to the building blocks of describing the curvature of spacetime.

> TODO: Simple Illustration? Scattering -> GeneralSchwarzschildEOM (general motion in schwarz) -> motion with angular momentum -> orbits -> just radial motion -> just curvature
> Also callout sections/subsections?

| GeneralSchwarzschildEOM -> motion with angular momentum -> orbits | radial motion | curvature factors |
| -- | -- | -- |
| 3.3 Angular Momentum, Effective Potential, and Orbits | 3.2 Gaining Speed and Radial Geodesics | 3.1 Distance, Time, and Embedding Diagrams |

The following subsections provide additional context for each step by detailing the process of implementing the building blocks. These subsections focus primarily on the computational implementation whereas *3.1 Distance, Time, and Embedding Diagrams* offers an analysis of the resulting visualizations and the physics behind them.

### Choose an Equation

> TODO: Move derivation to background section for GR in the Intro? Or have conceptual introduction there and leave this more mathematical approach here?

We begin by isolating the descriptions of proper time and proper distance as measured by a shell observer using the line element (Equation $\ref{SchwarzschildWithC}$). Recall from *1.2.3 Space into Spacetime* that proper time and distance are invariant with respect to changing reference frames. We can introduce the shorthand of $f(r)= \sqrt{1 - \frac{2M}{r}}$ and $d^2\Omega=\sin^2{\theta}d^2\varphi + d^2\theta$ to simplify the expression.

\begin{equation}
ds^2= - f(r)^2 (dt^2) + \frac{dr^2}{f(r)^2} + r^2 d^2\Omega
\end{equation}

Then by setting $d^2\Omega=0$, we simplify the description of the line element to be changes in $r$ or $t$. Examining just a change in $r$ or $t$, we derive proper distance and time for the shell observer as Equations $\ref{ShellDistance}$ and $\ref{ShellTime}$:

\begin{equation}\label{ShellDistance}
    dr_{shell} = \left(1-\frac{2M}{r}\right)^{-\frac{1}{2}} dr
\end{equation}
\begin{equation}\label{ShellTime}
    dt_{shell} = \left(1-\frac{2M}{r}\right)^{\frac{1}{2}} dt
\end{equation}

$$\ $$

### Translate to Python

The next step is to represent the two equations in Python. Given the relative simplicity of Equations $\ref{ShellDistance}$ and $\ref{ShellTime}$, they naturally lend themselves to being represented as Python functions:

``` python
def dr_shell(r, M, dr):
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

def dt_shell(r, M, dt):
  from math import sqrt
  return sqrt(1-(2*M)/r)*dt
```

Like the functional form of Equations $\ref{ShellDistance}$ and $\ref{ShellTime}$, these functions evaluate $dr_{shell}$ and $dt_{shell}$ for a specific $r$-coordinate (corresponding to the shell's location).

$$\ $$

### Generate Visualization for Equation

This portion requires only basic familiarity with Matplotlib and NumPy. Using the distance function, `dr_shell(...)`, with convenient values for `M` and `dr` are choosen allow for easy inspection for uncharacteristic behaviour. Specific values of `M` and `dr` will be used in $\ref{distanceTimeAndEmbedding}$ to verify the expected results from literature.

``` python
import numpy as np
import matplotlib.pyplot as plt

def dr_shell(r, M, dr):
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

M = 5
dr = 1
```

Since there is a coordinate singularity at $r=2M$ and shell observers only exist outside the event horizon (see $\ref{massIsCurvature}$), we need to adjust the interval of possible $r$-coordinates accordingly. We also need the size of the interval to be in a nice middle ground: just far enough away to display the shape of the plot and close enough to avoid suppressing the desired behaviour.

``` python
r_coordinates = np.arange(2*M+dr, 15*M, dr)
proper_distance = np.zeros(r_coordinates.shape)
```

We accomplish this by making the interval exclusive, $(2M,15M)$, and adding $dr$ to $2M$. Trial and error is used to find that $15M$ works as desired for the chosen values of `M=5` and `dr=1`. The figure generated by this implementation is Figure $\ref{DesignProcessVerify_Python}$.

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

### Verify Results and Change as Necessary

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
  \caption{a Python representation of Equation \ref{ShellDistance}. b Mathematica's interpretation. Note that both visualizations have the same behaviour: monotonically decreasing and asympotically approaching $f(x)=1$ as $x\rightarrow\infty$.}
\end{figure}

> TODO: Attempt to align formatting between Mathematica and Python plots? The difference is definitely detracting, but they are different software visualizations. I would like to unify them, but it comes at a cost (besides time). If one of my intents is to have code present that can be ripped out and thrown into someone else's computer for reproducibility, then I have to include all the extra formatting line as well. This'll increase the size of each codeblock along with intensity. Maybe have the full Mathematica code in the appendix then?

As more complex expressions are represented and interpreted by Cartographer, this stage becomes more time consuming due to the increased chance for mistakes in derivation and/or implementation. This stage is also when direct comparisons to any existing visualizations from literature are conducted.

$$\ $$

### Refactor

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

While the two representations are almost identical, especially for those used to representing math equations in LaTeX, the names of the functions and variables are not *self-narrating*. Therefore, comments denoting the intention and use of each variable are expected.

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

This, however, is treated as the bare minimum in being a good custodian of the code. Very often comments are not kept up-to-date with the changes to a function[^-21]. Instead, the programming community recommends that the code be self documenting: variable names should be descriptive and offer insight into the type of object they represented and that explicit programming statements are easier to understand than their elegant and brief counter-parts. These *best practices* are recommendations agreed upon by the larger software development community. The Python organization takes this a step further by formally representing their community's best practices in the style guide released as [PEP 8](https://www.python.org/dev/peps/pep-0008/) [6]. By explicitly naming each variable (and function), we can free up the comments to provide a summary of the function's behaviour and reference the derivation of the expression.

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

# The Mapping of Schwarzschild

$$\ $$

## Distance, Time, and Embedding Diagrams {#distanceTimeAndEmbedding}

> TODO: This sets the stage for more complex plots and visualizations to come.

> TODO: Figure plotting proper time/distance as measured by each shell.

\begin{figure}[H]
    \centering
    \caption{\label{ProperDistanceShell} TODO: I've created this figure and added it to the paper earlier than intended. Need to check if I need to add it again or if I just reference. Will there be any significant change? Probably $M$? Maybe this is a series of plots, showing how different values of $dr$ effect the result? }
\end{figure}

\begin{figure}[H]
    \centering
    \caption{\label{ProperTimeShell} Cartographer's visualization for Equation \ref{ShellTime}, exhibiting time dilation from the pressence of a gravitational potential. }
\end{figure}

> TODO: This is also the place to call out what appears to be the standard formatting for these type of plots.

\pagebreak

## Gaining Speed and Radial Geodesics

> TODO: Embedding diagram with geodesic plotted and corresponding callout.

\begin{figure}[H]
    \centering
    \caption{\label{EmptyEmbedding} Using the results of Figure \ref{ProperDistanceShell}, we can rotate this function about the axis of symmetry and highlight specific shells to give a geometric representation of the curvature of spacetime in Schwarzschild. These types of visualizations are called "Embedding diagrams". }
\end{figure}

> TODO: Speed as measured from different observers.

\begin{figure}[H]
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Bookkeeper}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r\rightarrow 2M$}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=3M$}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=6M$}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=10M$}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=20M$}
      \label{fig:sub-first}
    \end{subfigure}

  \caption{Speed of in-falling object as measured from a series of different reference frames.}
  \label{RainSpeed}
\end{figure}

$$\ $$

> TODO: Ripped from *Progress Report 11/22*, Refine Later

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

$$\ $$

### Changing Perspective

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

> Before fixing E/m to be from shell

We're changing perspective: so, $d\vec{r}$ from the observation shell is actually $$d\vec{r}= {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{1/2} dt\hat{t} - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{-1/2} dr \hat{r}$$

Therefore:

$$\begin{aligned}
  1 &= \left(1-\frac{2M}{r}\right)\frac{dt_{bk}}{d\tau}\\
  d\tau^2 &= \left(1-\frac{2M}{r}\right)^2 {dt_{bk}}^2 
\end{aligned} \qquad \begin{aligned}
  d\tau^2 &= -ds^2 = d\vec{r}\cdot d\vec{r} \\
    &= \left(1-\frac{2M}{r_{obs\ shell}}\right)dt^2 - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{-1} dr^2
\end{aligned}$$

We then solve for $dr/dt$:

$$\begin{aligned}
  \left(1-\frac{2M}{r}\right)^2 dt^2 &= \left(1-\frac{2M}{r_{obs\ shell}}\right)dt^2 - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{-1} dr^2 \\
  \frac{\left(1-\frac{2M}{r}\right)^2}{\left(1-\frac{2M}{r_{obs\ shell}}\right)} &= 1 - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{-2} \frac{dr^2}{dt^2} \\
  \frac{\left(1-\frac{2M}{r}\right)^2}{\left(1-\frac{2M}{r_{obs\ shell}}\right)} -1 &= - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{-2} \frac{dr^2}{dt^2} \\
  \frac{\left(1-\frac{2M}{r}\right)^2}{\left(1-\frac{2M}{r_{obs\ shell}}\right)} -1 &= -  \frac{dr^2}{dt^2} \\
  \frac{dr^2}{dt^2} &= {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{2} - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}\left(1-\frac{2M}{r}\right)\\
  \frac{dr}{dt} &= -\sqrt{{\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{2} - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}\left(1-\frac{2M}{r}\right)}
\end{aligned}$$

> Fixing E/m to be from shell and $d\vec{r}$:

$$d\vec{r}= {\left(1-\frac{2M}{r}\right)}^{1/2} dt_{bk}\hat{t} - {\left(1-\frac{2M}{r}\right)}^{-1/2} dr_{bk} \hat{r}$$

becomes

$$d\vec{r}= {\left(1-\frac{2M}{r}\right)}^{1/2}{\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{1/2} dt_{obs\ shell}\hat{t} - {\left(1-\frac{2M}{r}\right)}^{-1/2}{\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{-1/2} dr_{obs\ shell} \hat{r}$$

Therefore:

$$\begin{aligned}
  1 &= \left(1-\frac{2M}{r}\right)\frac{dt_{bk}}{d\tau}\\
  d\tau^2 &= \left(1-\frac{2M}{r}\right)^2 {dt_{bk}}^2 \\
  d\tau^2 &= \frac{\left(1-\frac{2M}{r}\right)^2}{1-\frac{2M}{r_{obs\ shell}}}{dt_{obs\ shell}}^2
\end{aligned} \qquad \qquad \begin{aligned}
  d\tau^2 &= -ds^2 = d\vec{r}\cdot d\vec{r} \\
    &= \left(1-\frac{2M}{r_{obs\ shell}}\right)\left(1-\frac{2M}{r}\right)dt^2 - {\left(1-\frac{2M}{r_{obs\ shell}}\right)}^{-1}{\left(1-\frac{2M}{r}\right)}^{-1} dr^2
\end{aligned}$$

Since the shell curvature factor is a constant, let's clean this up by using $k\equiv 1 - \frac{2M}{r_{obs\ shell}}$ and then solve for $dr/dt$:

$$\begin{aligned}
  \frac{\left(1-\frac{2M}{r}\right)^2}{k}{dt_{obs\ shell}}^2 &= \left(1-\frac{2M}{r}\right)k{dt_{obs\ shell}}^2 - \frac{{dr_{obs\ shell}}^2}{\left(1-\frac{2M}{r}\right)k}\\
  \left(1-\frac{2M}{r}\right)^2 &= \left(1-\frac{2M}{r}\right)k^2 - \frac{1}{\left(1-\frac{2M}{r}\right)}\frac{{dr_{obs\ shell}}^2}{{dt_{obs\ shell}}^2}\\
  \left(1-\frac{2M}{r}\right)^3 &= \left(1-\frac{2M}{r}\right)^2 k^2 - \frac{{dr_{obs\ shell}}^2}{{dt_{obs\ shell}}^2}\\
  \frac{{dr_{obs\ shell}}^2}{{dt_{obs\ shell}}^2} &= \left(1-\frac{2M}{r}\right)^2 \left(k^2 - \left(1-\frac{2M}{r}\right)\right)\\
  \frac{{dr_{obs\ shell}}}{{dt_{obs\ shell}}} &= -\left(1-\frac{2M}{r}\right)\sqrt{k^2 - \left(1-\frac{2M}{r}\right)} \\
\end{aligned}$$

Without constant:

$$\begin{aligned}
  \frac{\left(1-\frac{2M}{r}\right)^2}{1-\frac{2M}{r_{obs\ shell}}}{dt_{obs\ shell}}^2 &= \left(1-\frac{2M}{r}\right)\left(1-\frac{2M}{r_{obs\ shell}}\right){dt_{obs\ shell}}^2 - \frac{{dr_{obs\ shell}}^2}{\left(1-\frac{2M}{r}\right)\left(1-\frac{2M}{r_{obs\ shell}}\right)}\\
  \frac{\left(1-\frac{2M}{r}\right)^2}{1-\frac{2M}{r_{obs\ shell}}} &= \left(1-\frac{2M}{r}\right)\left(1-\frac{2M}{r_{obs\ shell}}\right) - \frac{1}{\left(1-\frac{2M}{r}\right)\left(1-\frac{2M}{r_{obs\ shell}}\right)}\frac{{dr_{obs\ shell}}^2}{{dt_{obs\ shell}}^2}\\
  \left(1-\frac{2M}{r}\right)^2 &= \left(1-\frac{2M}{r}\right)\left(1-\frac{2M}{r_{obs\ shell}}\right)^2 - \frac{1}{\left(1-\frac{2M}{r}\right)}\frac{{dr_{obs\ shell}}^2}{{dt_{obs\ shell}}^2}\\
  \frac{{dr_{obs\ shell}}^2}{{dt_{obs\ shell}}^2} &= \left(1-\frac{2M}{r}\right)^3 \left(\left(1-\frac{2M}{r_{obs\ shell}}\right)^2 - 1\right)\\
  \frac{{dr_{obs\ shell}}}{{dt_{obs\ shell}}} &= -\left(1-\frac{2M}{r}\right)\sqrt{\left(1-\frac{2M}{r}\right)\left(\left(1-\frac{2M}{r_{obs\ shell}}\right)^2 - 1\right)} \\
\end{aligned}$$

> TODO: Finish write up of work

\pagebreak


### Rain versus Hail

> TODO: Rain frame (rest at infinity) versus Hail frame (initial speed) as measured from different observers.

\begin{figure}[H]
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Bookkeeper}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r\rightarrow 2M$}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=3M$}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=6M$}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=10M$}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.3\textwidth}
      \centering
      \caption{Shell at $r=20M$}
      \label{fig:sub-first}
    \end{subfigure}

  \caption{Speed of in-falling object as measured from a series of different reference frames (same as for Figure \ref{RainSpeed}). The in-falling object, however, starts with a non-zero initial radial velocity.}
  \label{HailSpeed}
\end{figure}

$$\ $$

A direct comparision between frames where the measured values are notably different are shown below in Figure $\ref{RainVSHail}$:

$$\ $$

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{Bookkeeper, Rain}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{Bookkeeper, Hail}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$r\rightarrow 2M$, Rain}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$r\rightarrow 2M$, Hail}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$r=6M$, Rain}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$r=6M$, Hail}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
  \caption{Comparision of the different observed speed measurements from the same shell reference frames used in both Figures \ref{RainSpeed} and \ref{HailSpeed}.}
  \label{RainVSHail}
\end{figure}

\pagebreak

## Angular Momentum, Effective Potential, and Orbits

> TODO: Potential vs r-coordinate

\begin{figure}[H]
    \centering
    \caption{\label{EffectivePotential} The plot of $V_{eff}$ as a function of $r$-coordinate. The dashed function is the Newtonian description of the gravitational potential with the notable behaviour that an in-falling object with non-zero angular momentum cannot reach the horizon ($r=2M$). }
\end{figure}

$$\ $$

### Circular

> TODO: Limiting cases

\begin{figure}[H]
    \centering
    \caption{\label{EffectivePotentialCircular} $V_{eff}$ versus ${L_z}/m$, highlighting that only a specifc set of angular momentum values correspond to a circular orbit. Note that $r=6M$ is the "Inner-most stable orbit" for any object with mass and that $r=3M$ can only be acheived by a massless particle. $r=3M$ is called the "Light Sphere". }
\end{figure}

$$\ $$

### Eliptical 

> TODO: Precession of Mercury

\begin{figure}[H]
    \centering
    \caption{\label{Mercury} Note that by removing the restriction of a circular orbit, we obtain the family of stable orbits that are almost elliptical in shape. This is one method in which the claims of GR were verified experimentally, as it correctly described Mercury's precision about the Sun. }
\end{figure}

\pagebreak

# Scattering

> TODO: For each section: geodesic on embedding diagram

\begin{figure}[H]
    \centering
    \caption{\label{EmptyEmbedding} Using the results of Figure \ref{ProperDistanceShell}, we can rotate this function about the axis of symmetry and highlight specific shells to give a geometric representation of the curvature of spacetime in Schwarzschild. These types of visualizations are called "Embedding diagrams". }
\end{figure}

$$\ $$

## Light

$$\ $$

### On axis

> TODO: Does this do anything other than the Light sphere?

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
    \caption{\label{ScatteringLightOnAxis} The null-geodesics followed by light moving towards the Schwarzschild Black Hole with inital parameters: ... }
\end{figure}

\begin{figure}[H]
    \centering
    \caption{\label{ScatteringLightOnAxisHeatMap} A 'heat-map' / velocity vector field plot overlayed on an embedding diagram showing the distortion and effects to radially traveling light. }
\end{figure}

$$\ $$

### Off axis

> TODO: At this stage, I'm assuming there'll be more to show, but I don't know how interesting this set will be. It could be trivial and just a few chosen geodesics to demonstrate the behaviour or it could be as intense as the On-Axis paths.

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
  \caption{The null-geodesics followed by light moving towards the Schwarzschild Black Hole with inital parameters: ... }
  \label{ScatteringLightOffAxis}
\end{figure}


\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \caption{A 'heat-map' / velocity vector field plot overlayed on an embedding diagram showing the distortion and effects to off-radial-axis traveling light.}
    \label{ScatteringLightOffAxisHeatMap}
\end{figure}

$$\ $$

## Low-mass particles

$$\ $$

> TODO: I don't really know how many plots will be created and how to represent them. Light will be done first but I don't have any meaningly different captions at this stage. Will replace in the future when visualizations begin to be generated.

$$\ $$

### On axis

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??}
      \label{fig:sub-first}
    \end{subfigure}
    \caption{\label{ScatteringLowMassOnAxis} The null-geodesics followed by a low mass particle moving towards the Schwarzschild Black Hole with inital parameters: ... }
\end{figure}

\begin{figure}[H]
    \centering
    \caption{\label{ScatteringLowMassOnAxisHeatMap} A 'heat-map' / velocity vector field plot overlayed on an embedding diagram showing the distortion and effects to a radially traveling low mass particle. }
\end{figure}

$$\ $$

### Off axis

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
  \caption{The geodesics followed by a low-mass object moving towards the Schwarzschild Black Hole with inital parameters: ... }
  \label{ScatteringLowMassOffAxis}
\end{figure}


\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
  \newline
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \caption{$b=$??, offset = ??}
      \label{fig:sub-first}
    \end{subfigure}
    \caption{A 'heat-map' / velocity vector field plot overlayed on an embedding diagram showing the distortion and effects to off-radial-axis low mass particles.}
    \label{ScatteringLowMassOffAxisHeatMap}
\end{figure}

$$\ $$

\pagebreak

# Conclusions

> TODO: Did Cartographer do what it set out to?

$$\ $$

## Effectiveness in Visualizing GR

> TODO: Any failures? Pros/Cons? Delibrate sacrifices?

$$\ $$

## Effectiveness in Design

> TODO: Any failures? Pros/Cons? Delibrate sacrifices?

\pagebreak

# Acknowledgements

$$\ $$

## People

- Tevian Dray
- Kathy Hadley
- Christopher Magone
- Greg Moulder
- Liz Gire
- Corrine Manouge

$$\ $$

## Software

**Open-source**

- Python 3.10
- NumPy
- Matplotlib
- PyYaml

- Desmos

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

[6] G. van Rossum, Guido; Warsaw, Barry; Coghlan, Nick. "PEP 8 -- Style Guide for Python Code." pythong.org. https://www.python.org/dev/peps/pep-0008/ (accessed December 1, 2021)

> TODO: Add Hartle, *Black Holes*,

\pagebreak

# Appendices

$$\ $$

## Glossary and Notation

> Everyone uses different signatures and mathematical notation, here's a list that compares common bits and attempts to map them in a unifying way.

$$\ $$

## Special Relativity

> If you've completely forgotten 335, this is the base of what you need to know

$$\ $$

## General Relativity

> Omit sub-sections, depending on the extent of Cartographer

$$\ $$

### Schwarzschild

$$\ $$

### Riessner-Nordstroem

$$\ $$

### Kerr

$$\ $$

## Cartographer

> TODO: To what extent should the code base be added?
