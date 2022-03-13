---
title: "Cartographer: Using Python to Create Maps of Curved Spacetime and Differential Scattering Cross-sections of Low-Mass Objects about a Schwarzschild Black Hole"
author:
  - Thomas Knudson `\\\\`{=latex} Advised by Dr. Kathryn Hadley
subtitle: "Department of Physics, OSU"
date: "February 21, 2022"
geometry:
 - a4paper
 - margin=2cm
toc: true
toc_depth: 2
graphics: yes
header-includes: |
    \usepackage{graphicx}
    \usepackage{pgfplots}
    \usepackage{hyperref}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usepackage{fancyhdr}
    \usepackage{float}
    \usepackage{subcaption}
    \pagestyle{fancy}
    \usetikzlibrary{shapes.geometric}
    \usetikzlibrary{calc}
    \usetikzlibrary{angles}
    \usepackage{setspace}
    \usepackage[acronym]{glossaries-extra}
    \setabbreviationstyle[acronym]{long-short}
    \makeglossaries
---

\newacronym{gr}{GR}{general relativity}
\newacronym{sr}{SR}{special relativity}
\newacronym{gps}{GPS}{Global Positition System}
\newacronym{bh}{BH}{black hole}
\newacronym{embedding}{embedding diagram}{embedding diagram}
\captionsetup{format=hang,indention=-0.5cm}
\onehalfspacing
\setlength{\parindent}{4em}
\setlength{\parskip}{1.5em}

$$\ $$

\pagebreak

\listoffigures

\pagebreak

\listoftables

> TODO: Add tables? Will I have any tables?

\pagebreak

# Abstract {-}

> TODO: Figure out how modify pandoc's template to move about table of contents.

<!-- \renewcommand{\baselinestretch}{1.5}\selectfont -->

> This thesis was written with a OSU physics major starting their capstone courses in mind. While not uniformly true for all physics students, base concepts of astrophysics and relativity, as would be covered in PH 455: Astrophysics and PH 335: Theoretical Mechanics, are treated as prior knowledge. Advanced concepts from general relativity or programming & optimization (beyond PH 36X: Computational Lab) will be explained or given an explicit appendix reference. $$\ $$

\glsresetall

\pagebreak

# Introduction

Galilean relativity is the model we use to describe relative velocities in everyday life and is fairly robust, requiring extremes to find the breaking points. Einstein’s famous thought experiment about light moving on a train is the perfect analog for describing problem involving \gls{gps} Satellites and thier transmissions to Earth. Using Galilean relativity, we can illustrate the physical situation like in Figure \ref{fig:gpsDemonstration}, however, it fails to provide a consistent description of physics for both the satellite and Earth.

\begin{figure}
  \centering
  \scalebox{0.95}{
  \begin{tikzpicture}

  % create coordinates
  \coordinate (O) at (0,-1.25);
  \coordinate (gps) at (8,-0.4);
  \coordinate (V) at (7.4,1);

  % Earth
  \node[circle,draw,text=white,fill=gray,minimum size = 50, outer sep = 2] (c1) at (O) {Earth};
  \draw[blue, dashed, thick] (c1) ellipse (0.85 and 0.25);
  \node at (c1.160) [left] {$\Delta t$};
  \node at (c1.south) [below=10pt, blue] {$\left(1-\frac{2M}{r_{Earth}}\right)^{-1/2}$};

  % Add curvature
  \tikzstyle{shell}=[ellipse,dash pattern=on \pgflinewidth off 2pt, outer sep=12pt]

  \node[shell, minimum width=450, minimum height=150] (gpsShell) at (0,0) {};
  \node at (gpsShell.south east) [below, right, sloped, red] {$\left(1-\frac{2M}{r_{GPS}}\right)^{-1/2}$};
  \draw[red, dashed, thick] (0,-0.4) ellipse (8 and 1.8);

  \draw[dotted] (0,-0.55) ellipse (5.75 and 1.5);
  \draw[dotted] (0,-0.8) ellipse (3.5 and 1);
  \draw[dotted] (0,-1) ellipse (2 and 0.5);

  % Satellite
  \node[circle, draw, outer sep = 2, fill=white] (c2) at (gps) {$\ $};
  \node at (c2.east) [right] {$\Delta t^\prime = \gamma\Delta t$};
  \node[fill=white] at (c2.south) [below] {GPS Satellite};

  % Label the radius
  % \draw[dashed] (c1.east) -- (c2) node [midway, below, sloped] {$2\times 10^7\ m$};

  % Show velocity
  \draw[stealth-] (V) --++ (c2) node [midway, right] {$\vec{v}$};

  \end{tikzpicture}
  }
  \caption{The Galilean description of the relative velocities between Earth and a \gls{gps} Satellite is given by the velocity vector from the satellite [1]. $\gamma$ represents the scale factor for time-dilation to unify observer's measurements in the context of special relativity and the ellipses represent stationary observers in general relativity. $M$ is the mass of the Earth (in meters) and the time dilation factors with their corresponding observers (at \textcolor{blue}{$r_{Earth}$} and \textcolor{red}{$r_{GPS}$}) are colored in blue and red, respectively.}
  \label{fig:gpsDemonstration}
\end{figure}

In short, each \gls{gps} satellite periodically transmits location data alongside a timecode [1]. Using \gls{sr}, we find a scaling factor, $\gamma$, that represents the strength of length contraction and time dilation caused by the relative velocity of the satellite to Earth. To calculate this factor, we must transition from the Galilean model of treating space and time distances separately to \gls{sr}’s spacetime. However, measurement and theory would still disagree on the time elapsed between ticks of both the Earth’s and the \gls{gps}’s light-clocks and that is because we have failed to consider the effects of gravity. These results are illustrated in Figure \ref{fig:timeDilationSum}.

\begin{figure}[H]
  \begin{subfigure}{\textwidth}
  \centering
  \scalebox{0.75}{
    \begin{tikzpicture}

      \tikzstyle{clock}=[circle,draw,minimum size=100,inner sep=0pt]
      \tikzstyle{sign}=[rectangle,minimum width=50,inner sep=0pt]

      \node[sign, scale=3]  (equals) at (0,0)  {=};
      \node[clock]          (GPST)   at (-3,0) {};
      \node[clock]          (GPSSR)  at (3,0)  {};
      \node[sign, scale=3]  (plus)   at (6,0)  {+};
      \node[clock]          (GPSGR)  at (9,0)  {};

      \coordinate (gpsTOrigin) at (GPST);
      \coordinate (gpsSROrigin) at (GPSSR);
      \coordinate (gpsGROrigin) at (GPSGR);

      % GPS Total
      \node at (GPST.west) [left] {GPS};
      \node at (GPST.south) [below] {Clock tick};
      \draw[dashed] (GPST.90) -- (GPST.center);
      \draw[dashed] (GPST.60) -- (GPST.center);

      %hour markings
      \foreach \j in {0,30,60,...,360}{
        \draw ($(GPST.center)!0.85! \j:(GPST.west)$) -- ($(GPST.center)!0.95! \j:(GPST.west)$);
      }

      \coordinate (GPST90) at (GPST.90);
      \coordinate (GPSTC) at (gpsTOrigin);
      \coordinate (GPST60) at (GPST.60);

      \node at (GPST.75) [above, sloped] {${\Delta t^\prime}_{net}$};
      \tkzFillAngle[fill=gray, opacity=0.4, size = 1.5](GPST60,GPSTC,GPST90){};

      % GPS SR
      \node at (GPSSR.south) [below] {Time dilation from relative velocity};
      \draw[dashed] (GPSSR.90) -- (GPSSR.center);
      \draw[dashed] (GPSSR.45) -- (GPSSR.center);

      %hour markings
      \foreach \j in {0,30,60,...,360}{
        \draw ($(GPSSR.center)!0.85! \j:(GPSSR.west)$) -- ($(GPSSR.center)!0.95! \j:(GPSSR.west)$);
      }

      \coordinate (GPSSR90) at (GPSSR.90);
      \coordinate (GPSSRC) at (gpsSROrigin);
      \coordinate (GPSSR45) at (GPSSR.45);

      \node at (GPSSR.68) [above] {\color{red}$\gamma\Delta t$};
      \tkzFillAngle[fill=red, opacity=0.4, size = 1.5](GPSSR45,GPSSRC,GPSSR90){};

      % GPS GR
      \node at (GPSGR.south) [below] {Time dilaton from graviational field};
      \draw[dashed] (GPSGR.90) -- (GPSGR.center);
      \draw[dashed] (GPSGR.105) -- (GPSGR.center);

      %hour markings
      \foreach \j in {0,30,60,...,360}{
        \draw ($(GPSGR.center)!0.85! \j:(GPSGR.west)$) -- ($(GPSGR.center)!0.95! \j:(GPSGR.west)$);
      }

      \coordinate (GPSGR90) at (GPSGR.90);
      \coordinate (GPSGRC) at (gpsGROrigin);
      \coordinate (GPSGR105) at (GPSGR.105);

      \node[color=black!50!green] at (GPSGR.100) [above] {$1-\frac{2M}{r_{GPS}}$};
      \tkzFillAngle[fill=black!50!green, opacity=0.4, size = 1.5](GPSGR90,GPSGRC,GPSGR105){};

    \end{tikzpicture}
  }
  \end{subfigure}
  \newline
  \begin{subfigure}{\textwidth}
  \centering
  \scalebox{0.75}{
    \begin{tikzpicture}

      \tikzstyle{clock}=[circle,draw,minimum size=100,inner sep=0pt]
      \tikzstyle{sign}=[rectangle,minimum width=50,inner sep=0pt]

      \node[sign, scale=3]  (equals)  at (0,0)  {=};
      \node[clock]          (EarthT)  at (-3,0) {};
      \node[clock]          (EarthSR) at (3,0)  {};
      \node[sign, scale=3]  (plus)    at (6,0)  {+};
      \node[clock]          (EarthGR) at (9,0)  {};

      \coordinate (earthTOrigin) at (EarthT);
      \coordinate (earthSROrigin) at (EarthSR);
      \coordinate (earthGROrigin) at (EarthGR);

      % Earth Total
      \node at (EarthT.west) [left] {Earth};
      \node at (EarthT.south) [below] {Clock tick};
      \draw[dashed] (EarthT.90) -- (EarthT.center);
      %\draw[dashed] (EarthT.60) -- (EarthT.center);
      \draw[dashed] (EarthT.15) -- (EarthT.center);

      %hour markings
      \foreach \j in {0,30,60,...,360}{
        \draw ($(EarthT.center)!0.85! \j:(EarthT.west)$) -- ($(EarthT.center)!0.95! \j:(EarthT.west)$);
      }

      \coordinate (EarthT90) at (EarthT.90);
      \coordinate (EarthTC) at (earthTOrigin);
      \coordinate (EarthT60) at (EarthT.60);
      \coordinate (EarthT15) at (EarthT.15);

      \node at (EarthT.75) [above, sloped] {${\Delta t}_{net}$};
      \tkzFillAngle[fill=gray, opacity=0.4, size = 1.5](EarthT15,EarthTC,EarthT90){};
      %\tkzFillAngle[fill=red, opacity=0.4, size = 1.5](EarthT15,EarthTC,EarthT90){};

      % Earth SR
      \node at (EarthSR.south) [below] {Time dilation from relative velocity};

      %hour markings
      \foreach \j in {0,30,60,...,360}{
        \draw ($(EarthSR.center)!0.85! \j:(EarthSR.west)$) -- ($(EarthSR.center)!0.95! \j:(EarthSR.west)$);
      }

      % Earth GR
      \node at (EarthGR.south) [below] {Time dilaton from graviational field};
      \draw[dashed] (EarthGR.90) -- (EarthGR.center);
      \draw[dashed] (EarthGR.15) -- (EarthGR.center);

      %hour markings
      \foreach \j in {0,30,60,...,360}{
        \draw ($(EarthGR.center)!0.85! \j:(EarthGR.west)$) -- ($(EarthGR.center)!0.95! \j:(EarthGR.west)$);
      }

      \coordinate (EarthGR90) at (EarthGR.90);
      \coordinate (EarthGRC) at (earthGROrigin);
      \coordinate (EarthGR15) at (EarthGR.15);

      \node[color=red] at (EarthGR.65) [right, above] {$1-\frac{2M}{r_{E}}$};
      \tkzFillAngle[fill=red, opacity=0.4, size = 1.5](EarthGR15,EarthGRC,EarthGR90){};

    \end{tikzpicture}
  }
  \end{subfigure}
  \caption{A first order approximation demonstrating how the each consideration of relativity effects the accuracy in the time elapsed between ticks on a clock. \textcolor{red}{Red} slices of the clock denote more elapsed time between ticks, while \textcolor{black!50!green}{green} denotes less (quicker clock-ticks). Note that Earth is at rest in its own frame and therefore experiences no dilation due to SR and that the result is the net elapsed time between clock-ticks for Earth, ${\Delta t}_{net}$, is greater than the \gls{gps}'s elapsed time, ${\Delta t^\prime}_{net}$.}
  \label{fig:timeDilationSum}
\end{figure}

By expressing the intensity of a massive body’s gravitational field as curvature to spacetime (alluded to by the ellipses in Figure \ref{fig:gpsDemonstration}), we discover and are able to correct for an additional set of length contraction and time dilation (Section \ref{primer}). This geometric model is called Schwarzschild Geometry and is the simplest solution to Einstein’s field equations involving a single massive object that is spherically symmetric, uncharged, and non-rotating.

While we now have a theory that provides extremely accurate predictions, we subtly sacrificed a lot along the way. In Galilean relativity, we could easily switch reference frames and agree on what all observers measured: distance, time, relative velocities, and order of events. As the relative speed of objects increased, we had to switch to special relativity, but lost: observers agreeing on the order of events (see the “barn and pole” paradox). Finally, in using \gls{gr} to correctly unify observers’ measurements in the presence of a gravitational field, we lose the ability to easily measure the relative velocity between reference frames.

To facilitate the exploration of Schwarzschild geometry, the computational framework, dubbed Cartographer, generates visualizations of particular physical situations of interest. While the \gls{gps} example is only concerned with introductory implications of relativity, a particular topic of focus for Cartographer is to map out the differential scattering caused by a \gls{bh} as massless and low-mass particles traverse the curved spacetime. Differential scattering is modeled using minor adjustments to Rutherford scattering [6].

We first review the concepts of proper time, proper distance, and geodesics in \gls{gr} and how to use the line element to measure separation in spacetime and how to represent it computationally (Sections \ref{primer}-\ref{design}). Then we will refresh on differential scattering cross-sections of light about an object (Section \ref{diffScatt}) in preparation for examining the scattering caused by the curvature of spacetime in Section \ref{scattering}. Section \ref{schwarzMaps} focuses on the generation and analysis of visualizations depicting simple and complex geodesics in the Schwarzschild geometry.

\pagebreak

# Background

## A Primer on Spacetime and Relativity {#primer}

As we move into more complex but accurate formulations of relativity, we lose properties that can be taken for granted in the more intuitive (but less accurate) descriptions. Asking simple questions like "how much time elapsed between when they threw the ball and it hit the ground?" or "how far did the ball fly?" become increasingly difficult to answer. In special relativity, we measure the spacetime separation between events, not space and time separately. Mathematically, this corresponds to a transition from measurements using the Pythagorean theorem,

\begin{equation}\label{eqn:pythag}
z = \sqrt{x^2 + y^2},
\end{equation}

within an Euclidean geometric model to the hyperbolic distance formula, 

\begin{equation}\label{eqn:hyperDistance}
z = \sqrt{x^2 - y^2},
\end{equation}

in a non-Euclidean space, where $x$, $y$, and $z$ are positive real numbers representing physical lengths.

From this, the spacetime separation measured by any reference frame--between two events to be only temporal or only spatial--is given the respective label of proper time or proper distance. In the two dimensional Minkowski geometric model for flat spacetime, $\mathbb{M}^2$, the **line element**--how spacetime separation is measured--takes the form of 

\begin{equation}\label{eqn:m2LineElement}
  ds^2 = - c^2dt^2 + dx^2.
\end{equation}

In informal language, Equation \ref{eqn:m2LineElement}, is sometimes reffered to as the *metric* [3]. More specifically, the metric, denoted by $g$, is the tool that describes how to resolve the inner product between basis 1-forms. While we generally avoid disucssing operations from different geometry in this paper, it is worth the brief detour to note where the differences in signs of the line element come from. Misner, Thorne, and Wheeler devote the inside cover of *Gravitation* [4] to display the most common set of choices for how $g$ resolves the product of basis 1-forms. In this paper, we will adopt the practice of E.F Taylor and J. A. Wheeler by using the $-+++$ signature, such that the time direction carries the negative sign. In more detail, Equation \ref{eqn:m2LineElement} is given by

\begin{equation}\label{eqn:m2LineElementExplicit}
ds^2 = g(d\vec{r},d\vec{r}) = c^2 dt^2 g(\hat{t},\hat{t}) + dx^2 g(\hat{x},\hat{x}) = -c^2 dt^2 + dx^2.
\end{equation}

We also adopt the shorthand of $\tau$ and $\sigma$ to signify proper time and distance, respectively, as well as natural units[^-1]. Therefore, in $\mathbb{M}^2$, **proper time** is where 

\begin{equation}\label{eqn:minkowsiProperTime}
  d\tau^2 = -ds^2 = dt^2
\end{equation}

and **proper distance** is

\begin{equation}\label{eqn:minkowsiProperDistance}
  d\sigma^2 = ds^2 = dx^2.
\end{equation}

[^-1]: This corresponds to setting the magntiude of various physical constants, such as the speed of light, to unity in order to simplify the visual appearance of equations.

Notably, there exists a scaling factor, $\gamma$, that corresponds to a length contraction and/or a time dilation between reference frames such that the measurements of proper time and proper distance can be measured by everyone. The behaviour of this property is called invariance and is crucial to determining what other observers in spacetime see. While \gls{gr} does introduce another set of length contraction and time dilation, the notions of proper time and distance remain the same, but take on a different mathematical representation. The fact that we can express both (\gls{sr} and \gls{gr}) sets of simultaneously and independently is crucial and explored more in-depth in Section \ref{radialShellSpeed}.

In the Schwarzschild geometric model, we consider spacetime to be curved due to the presence of a massive object with spherical symmetry. The gravitional field exerted by this object can be fully described by this curvature in an analogous fashion as to how electrostatic potential, $V(\vec{r})$, can describe the electric field $\vec{E}$. Unlike potential, it is very difficult to visually represent the features of the curved four dimensional spacetime in two dimensional projections and before we can introduce some attempts to visualize these properties, some additional notation is required.

As mentioned previously, \gls{sr} requires we treat all reference frames[^-2] equally: any frame moving with the same relative velocity as another will measure the same spacetime seperation between events (without corrections). With the introduction of curvature, not all reference frames agree on what they measure. Notably, we have three major *families* of frames now: shell observers, the bookkeeper, and the rain frame. While Section \ref{rainAndHail} will elaborate on the **rain frame**, for now we treat it synonmously with the intertial reference frame of an object free falling radially inward. **Shell observers** represent reference frames of constant distance, $r$-coordinate, or time, $t$. Finally, the **Bookkeeper** (BK), represents the set of frames infintely far away from the influence of the gravitational source and conduct their measurements as if in flat space.

[^-2]: Recall that an intertial reference frame describes a region of space that follows Newton's First Law of Motion [6].  

Due to Schwarzschild's spherical symmetry, we naturally adopt a version of spherical coordinates. The important difference is in how we measure distance from the origin. For example, consider the hyperbolic triangles in Figure \label{fig:schwarzTriangle} which show how the *radial* distance from the massive object, $M$, changes how we measure things versus someone at a different $r$-coordinate.

\begin{figure}[H]
  \begin{subfigure}{.5\textwidth}
    \centering
    \scalebox{1.15}{
      \begin{tikzpicture}

      % create coordinates
      \coordinate (O) at (0,0);
      \coordinate (L) at (5,0);
      \coordinate (P) at (0,-2);

      % Construct triangle
      \draw (P) -- (L) node [midway, below, sloped] {$dr_{shell} = \frac{dr_{BK}}{\sqrt{1-\frac{2M}{r_{shell}}}}$};
      \draw (O) -- (L) node [midway, above] {$dr_{BK}$};
      \draw (O) -- (P) node [midway, left] {$\sqrt{1-\frac{2M}{r_{shell}}}$};

      \end{tikzpicture}
    }
    \caption{Distance}
    \label{fig:schwarzDistanceTriangle}
  \end{subfigure}
  \hfill
  \begin{subfigure}{.5\textwidth}
    \centering
    \scalebox{1.15}{
      \begin{tikzpicture}

      % create coordinates
      \coordinate (O) at (0,0);
      \coordinate (L) at (5,0);
      \coordinate (P) at (0,-2);

      % Construct triangle
      \draw (P) -- (L) node [midway, below, sloped] {$dt_{BK}$};
      \draw (O) -- (L) node [midway, above] {$dt_{shell} = \sqrt{1-\frac{2M}{r_{shell}}}dt_{BK}$};
      \draw (O) -- (P) node [midway, left] {$\sqrt{1-\frac{2M}{r_{shell}}}$};

    \end{tikzpicture}
    }
    \caption{Time}
    \label{fig:schwarzTimeTriangle}
  \end{subfigure}
  \caption{The two hyperbolic triangles represent the difference between physical quantites and their geometric coordinates. Extending a latticework of these constructions for each coordinate allows for the creation of embedding diagrams like Figure \ref{fig:Embedding}, which offer a direct visual representation of the underlying curvature.}
  \label{fig:schwarzTriangle}
\end{figure}

Since the physical distance, denoted as $dr_{shell}$, increases as we approach $M$, we must exercise caution in how we define our geometric location[^-3]. As a result, we measure the circumference of our concentric shell and divide by $2\pi$ to obtain the **$\mathbf{r}$-coordinate**. This process is analogous to tracing out great circles on a sphere which leads us to the next important geometric object useful in describing paths: **geodesics** are the lines of spacetime. Mathematically, these are *straight* lines (constant speed) in this non-Euclidean geometry[8]. Physically, these lines correspond to paths through spacetime of objects moving at constant velocity. It is very important to note that the gravitational field is a description of the curvature of spacetime, and that gravity is not treated as an external force in \gls{gr}.

[^-3]: Consider how far (radially) away a neighboring shell would be if $r$ was very close to $2M$. The use of physical distance to be synonymous with our geometric location works perfectly fine in Euclidean geometries, but here in Schwarzschild, having points that are almost infinitely far away when they are neighbors is not useful to describe positions.

$$\ $$

## The Design Process {#design}

To facilitate periodic testing and quick implementation, the desired functionality of Cartographer was divided into a series of milestones. Each milestone was chosen such that it gradually increased in complexity and laid the groundwork for subsequent milestones. This iterative design process is often referred to the minimal viable product: at the conclusion of each milestone, all corresponding functionality has been implemented and the code has been cleaned up and reorganized (refactored).

This design process can be distilled into a series of five steps:

1. Choose an Equation
2. Translate Equation to Python
3. Generate Visualization for Equation
4. Verify Results and Change as Necessary
5. Refactor

The goal of Cartographer is to generate visualizations corresponding to light and low-mass particles moving through Schwarzschild spacetime. As mentioned in \ref{motivation}, these geodesic equations are complex but we can leverage that they are the result of algebraic compositions from simpler expressions. This allows us to work backwards from the end goal of visualizing something like Equation (\ref{GeneralSchwarzschildEOM}) to the building blocks of describing the curvature of spacetime.

The following subsections provide additional context for each step by detailing the process of implementing the building blocks. These subsections focus primarily on the computational implementation whereas Section 3.1 offers an analysis of the resulting visualizations and the physics behind them.

### Choose an Equation

We begin by isolating the descriptions of proper time and proper distance as measured by a shell observer using the line element (Equation $\ref{SchwarzschildWithC}$). Recall from Section \ref{primer} that proper time and distance are invariant with respect to changing reference frames. We can introduce the shorthand of $f(r)= \sqrt{1 - \frac{2M}{r}}$ and $d^2\Omega=\sin^2{\theta}d^2\varphi + d^2\theta$ to simplify the expression.

\begin{equation}
ds^2= - f(r)^2 (dt^2) + \frac{dr^2}{f(r)^2} + r^2 d^2\Omega
\end{equation}

Then by setting $d^2\Omega=0$, we simplify the description of the line element to be changes in $r$ or $t$. Examining just a change in $r$ or $t$, we derive proper distance and time for the shell observer as Equations \ref{ShellDistance} and \ref{ShellTime}:

\begin{equation}\label{ShellDistance}
    dr_{shell} = \left(1-\frac{2M}{r}\right)^{-\frac{1}{2}} dr
\end{equation}
\begin{equation}\label{ShellTime}
    dt_{shell} = \left(1-\frac{2M}{r}\right)^{\frac{1}{2}} dt
\end{equation}

$$\ $$

### Translate to Python

The next step is to represent the two equations in Python.

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

Using the distance function, `dr_shell(...)`, with convenient values for `M` and `dr` are choosen allow for easy identification of uncharacteristic behaviour. Specific values of `M` and `dr` will be used in $\ref{distanceTimeAndEmbedding}$ to verify the expected results from literature.

``` python
import numpy as np
import matplotlib.pyplot as plt

def dr_shell(r, M, dr):
  from math import sqrt
  return dr/sqrt(1-(2*M)/r)

M = 5
dr = 1
```

Since there is a coordinate singularity at $r=2M$ and shell observers only exist outside the event horizon, we need to adjust the interval of possible $r$-coordinates accordingly. We also need the size of the interval to be in a nice middle ground: just far enough away from $2M$ to display the shape of the plot and close enough to avoid suppressing the shape of the function.

``` python
r_coordinates = np.arange(2*M+dr, 15*M, dr)
proper_distance = np.zeros(r_coordinates.shape)
```

We choose the interval of $(2M,15M)$ to show the characteristic fall-off of the function as it quickly approaches the asmyptote of $1$. This *locally intense* and *weak at a distance* behaviour is crucial in demonstrating why Euclidean geometric models have previously described physical phenoma so well for so long. The figure generated by this implementation is Figure $\ref{DesignProcessVerify_Python}$.

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

Recall that for distance, we are plotting Equation (\ref{ShellDistance}) which has the general form of

\begin{equation}
f(x) = \frac{1}{\sqrt{1-\frac{1}{x}}}.
\end{equation}

With this in mind, it is very easy to construct comparisions for the shape of the output generated by Cartographer to any plotting software. Using the following Mathematica code, we compare the two functions by considering their concavity, shape, and behaviour as $x\rightarrow\infty$.

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
  \label{fig:designProcessVerify}
\end{figure}

As expected, Figure \ref{fig:designProcessVerify} shows a strong agreement between representations. Comparing the output generated by Cartographer to the results from other plotting software, where applicable, is a key step in sense making and verifing the results agree with the already established predictions of \gls{gr}. As more complex expressions are represented and interpreted by Cartographer, this stage becomes more time consuming due to the increased chance for mistakes in derivation and/or implementation.

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

$$\ $$

## Differential Scattering {#diffScatt}

> TODO: Add description once Cartographer is generating content for Section \ref{scattering} and I understand it better.

\pagebreak

# The Mapping of Schwarzschild {#schwarzMaps}

## Distance, Time, and Embedding Diagrams {#distanceTimeAndEmbedding}

The simplest visualizations to help generate intuition about curved spacetime come from plotting how measurements of space and time are affected by radial proximity ($r$-coordinate) to the massive object ($M$) in question. This is done by taking the line element of Schwarzschild geometry, 

\begin{equation}\label{eqn:SchwarzLine}
ds^2 = -f(r)^2 dt^2 + \frac{dr^2}{f(r)^2},
\end{equation}

and solving for spacetime measurements conducted by shell observers of constant $r$ or $t$. Note that we have introduced the shorthand of $f(r)$ to represent the scale factor of

\begin{equation}\label{eqn:SchwarzScale}
\sqrt{1-\frac{2M}{r}}
\end{equation}

for ease of presentation. Shell observers of constant $r$, $dr=0$, measure the proper time by 

\begin{equation}\label{eqn:ShellTime}
d\tau = dt_{shell} = \sqrt{1-\frac{2M}{r_{shell}}} dt_{BK}.
\end{equation}

By plotting Equation \ref{eqn:ShellTime} as a function of $r$, we can graphically represent the effects of time dilation due to proximity of $M$. However, plotting Equation \ref{eqn:ShellTime} in its current form does not immediately answer the question posed in Figure \ref{fig:gpsDemonstration}. To answer the question of "How much slower is a clock tick at the radius of the Earth versus a clock at the orbital height of a \gls{gps}?", it is best to solve Equation \ref{eqn:ShellTime} for $dt_{BK}$ and the plot of that result is shown in Figure \ref{fig:ShellTime}.

\begin{figure}[H]
    \centering
    \includegraphics[width=10cm,keepaspectratio,]{curvature_diagram_time.jpg}
    \caption{ Equation \ref{eqn:ShellTime} solved for $dt_{BK}$ and plotted with the domain of $r\in$[$3M$,$10M$]. Note as $r$ approaches the event horizon, the gravitational time dilation approaches infinity.}
    \label{fig:ShellTime}
\end{figure}

An equivalent description for gravitational length contraction can also be derived from the line element by considering surfaces of constant time. These shell observers of constant $t$ measure proper distance by 

\begin{equation}\label{eqn:ShellDist}
d\sigma = dr_{shell} =  \frac{dr_{BK}}{f(r_{shell})},
\end{equation}

which can be used to create the complmentary plot of Figure \ref{fig:ShellTime} as shown in Figure \ref{fig:ShellDist}. These functions, given by Equations \ref{eqn:ShellTime} and \ref{eqn:ShellDist}, are then often revolved about the origin to create embedding diagrams. These three-dimensional surfaces are used to help construct an intuition about what it means for spacetime to be curved, as Figures \ref{fig:Embedding-Time} and \ref{fig:Embedding-Distance} demonstrate.

\begin{figure}[H]
    \centering
    \includegraphics[width=10cm,keepaspectratio,]{curvature_diagram_length.jpg}
    \caption{Equation \ref{eqn:ShellDist} solved for $dr_{BK}$ and plotted with the domain of $r\in$[$3M$,$10M$]. Note as $r$ approaches the event horizon, the length of an object must approach infinity to be finite from the Bookkeeper's view.}
    \label{fig:ShellDist}
\end{figure}

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{embedding_diagram_time.png}
      \caption{Time}
      \label{fig:Embedding-Time}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{embedding_diagram_distance.png}
      \caption{Distance}
      \label{fig:Embedding-Distance}
    \end{subfigure}
  \caption{The two-dimensional projection of the three-dimensional surfaces describe by revolving Equations \ref{eqn:ShellTime} and \ref{eqn:ShellDist} about the origin. Each embedding diagram shows cross-sections for surfaces of constant $t$ and $r$ by using height to represent the strength of curvature at each surface. The $\theta$ coordinate is surpressed through spherical symmetry by taking cross-sections in the equitorial plane($\theta=\pi/2$).}
  \label{fig:Embedding}
\end{figure}

\pagebreak

## Gaining Speed and Radial Geodesics

> TODO: Embedding diagram with geodesic plotted and corresponding callout?

\begin{figure}[H]
  \centering
  \includegraphics[width=15cm,keepaspectratio,]{rain_speed.png}
  \caption{Speed of in-falling object as measured from a series of different reference frames. Note the diverging observations from the Bookkeeper and the Shell Observer as $r_{shell}$ approachs $2M$. The Bookkeeper measures the speed of the stone to be increasing in the region of $r>6M$ before its deceleration to $v=0c$ at the event horizon.}
  \label{fig:RainSpeed}
\end{figure}

For a stone (some arbitrary low-mass object), the simplest path it can traverse in this geometric model is to free-fall radially towards the black hole. Figure \ref{fig:RainSpeed} provides a visual representation of how different frames measure the stone's radial speed. To explore the most general case first, consider the stone to be collocated with the Bookkeeper ($r\rightarrow\infty$). Out at $r\ggg 2M$, the energy (per unit mass) of the stone is just its rest mass and we describe this property with Equation 12 from [2]:

\begin{equation}\label{eqn:SchwarzEnergy}
\frac{E}{m} = \left(1-\frac{2M}{r}\right)\frac{dt}{d\tau}.
\end{equation}

From the Bookkeeper's measurements, the stone moves along a path described by

\begin{equation}\label{eqn:RadialDR}
d\vec{r}= f(r) dt\hat{t} - \frac{dr}{f(r)} \hat{r}.
\end{equation}

Multiplying Equation \ref{eqn:RadialDR} with itself gives us the simplified line element from before (Equation \ref{eqn:SchwarzLine}). We then combine Equations \ref{eqn:SchwarzEnergy} and \ref{eqn:SchwarzLine} by equating them after solving each for proper time. The result is speed (as a multiple of $c$) as a function of $r$-coordinate for the stone, as measured by the Bookkeeper:

\begin{equation}\label{eqn:SchwarzRadBK}
\frac{dr_{bk}}{dt_{bk}}=-\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}.
\end{equation}

The sign of Equation \ref{eqn:SchwarzRadBK} describes an in-falling (when negative) or an escaping (when postive) object. Substituing in the division of Equation \ref{eqn:ShellDist} by Equation \ref{eqn:ShellTime} into the left-hand side of Equation \ref{SchwarzRadBK}, we obtain what a shell observer would measure when the stone reaches $r_{shell}$. This expression is given as

\begin{equation}\label{eqn:SchwarzRadShells}
\frac{dr_{shell}}{dt_{shell}}=-\sqrt{\frac{2M}{r_{shell}}},
\end{equation}

where we have applied the same notion of sign to represent direction.

As shown in Figure \ref{fig:RainSpeed}, this diverging behaviour has physical consequences. If we give the Bookkeeper the most senstive equipment, they measure any in-falling object to stop as it reaches the event horizon and would never observe any object passing through. In practice, if we model light being emitted by the stone towards the Bookkeeper as continous, the wavelength of light that informs any outside observer that the stone has crossed the horizon will be gravitationally redshifted to an infinite wavelength. In re-examinating of Figures \ref{fig:ShellTime} and \ref{fig:ShellDist}, if we consider the extreme case as the contraction scaling factor, $\zeta$, approaches $0$, the un-contracted length, $\lambda$, must approach infinity such that the length measured at $r\rightarrow BK$ remains unity as described below:

\begin{equation}\label{eqn:ExampleRedshift}
\lim_{\zeta\rightarrow 0 ,\ \lambda\rightarrow\infty} \zeta \times \lambda= 1.
\end{equation}

$$\ $$

### Changing Perspective {#radialShellSpeed}

> TODO Flesh out more/refine stone's view

Both Equations \ref{eqn:SchwarzRadBK} and \ref{eqn:SchwarzRadShells} were able to be derived from the line element, but they only describe the stone's speed from two very different frames. The natural step to complete the description of the stone's journey would be to consider what the stone measures and what one specific Shell observer measures (not the aggregate). The former proves easier than the latter.

To measure things in the stone's frame, we perform a change of basis on the differentials, as detailed in [3, 4]. Since the stone is in a free-fall, there is no test the stone can perform that informs it of its motion. This is consistent with the findings of \gls{sr}.

To find out how a particlar shell in Schwarzschild measures speed, we can't just directly manipulate the line element to obtain a simple equation. If we try (to manipulate the line element) to pick a specific shell for our reference frame, the resulting expression leads to unphysical results -- namely the stone can surpass the speed of light if the observation shell is less than $r=6M$. Instead, we must construct a thought experiment:

> Consider a lightblub emitting a continous known wavelength of light, $\lambda_{emitted}$ (as measured in its rest frame), as it falls inward to the \gls{bh}. An observer, situated on a specific shell, $r_{measured}$, measures the redshifted wavelength as $\lambda_{measured}$. If $r_{emitted}$ is transmitted alongside each instance of $\lambda_{emitted}$, how fast is the lightblub moving towards the event horizon along a radial path, as measured by the shell observer?

Noting that the redshift has contributions from both gravity (curvature of spacetime) and the speed (relativistic Doppler effect), we can build an expression to describe this:

\begin{equation}\label{eqn:DopplerAndGravShift}
\lambda_{measured} = \sqrt{\frac{1-\frac{2M}{r_{measured}}}{1-\frac{2M}{r_{emitted}}}}\sqrt{\frac{c+v}{c-v}} \lambda_{emitted}
\end{equation}

Solving for speed, we then obtain the function:

\begin{equation}\label{eqn:RainSpeedObsShell}
v(\lambda_{measured}, r_{measured}, \lambda_{emitted}, r_{emitted}) = c \frac{\left(\frac{\lambda_{measured}}{\lambda_{emitted}}\right)^2 \left(\frac{1-\frac{2M}{r_{emitted}}}{1-\frac{2M}{r_{measured}}}\right) - 1}{\left(\frac{\lambda_{measured}}{\lambda_{emitted}}\right)^2 \left(\frac{1-\frac{2M}{r_{emitted}}}{1-\frac{2M}{r_{measured}}}\right) + 1}.
\end{equation}

Since $r_{measured}$ and $\lambda_{emitted}$ are constants, Equation \ref{eqn:RainSpeedObsShell} becomes a function of two independent variables: $v(\lambda_{m}, r_{e})$. By considering the case where $r_m = r_e$, the gravitational redshiftting terms simplifly to unity and we are left with only the \gls{sr} description of redshift. This expression can then be equated to the result of Equation \ref{eqn:SchwarzRadShells} in an effort to specify the initial condition of the lightbulb starting at rest for $r\rightarrow\infty$. This result is displayed in Figure \ref{fig:RainSpeed_OBS} by plotting $v(r_e)$ versus $r/M$.

\begin{figure}[H]
  \centering
  \includegraphics[width=15cm,keepaspectratio,]{rain_speed_obs_shell.png}
  \caption{Speed of the stone as measured from a shell observer at $r=10M$. **TODO:** Replace with Cartographer plot and not the placeholder from Mathematica with faulty formatting.}
  \label{fig:RainSpeed_OBS}
\end{figure}

As mentioned in the introduction, in moving from the realm of \gls{sr} to \gls{gr}, we lost the notion of a *global* velocity. This is an underdetermined system of equations and can only provide insight into the radial speed and direction of the lightbulb observed by $r_m$ for a given ratio of doppler redshifting, $\lambda_e / \lambda_m$. Since this ratio is non-constant, as the shell frames observe increasing speed, it is impossible to provide a complete answer to the prompt.

\pagebreak

### Rain versus Hail {#rainAndHail}

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
    \caption{\label{Mercury} Note that by removing the restriction of a circular orbit, we obtain the family of stable orbits that are almost elliptical in shape. This is one method in which the claims of \gls{gr} were verified experimentally, as it correctly described Mercury's precision about the Sun. }
\end{figure}

\pagebreak

# Scattering {#scattering}

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
- Corinne Manogue

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

<!-- \setlength{\parindent}{0em} -->

<br />

[1] Riebeek, Holli. "Catalog of Earth Satellite Orbits." NASA Earth Observatory. https://earthobservatory.nasa.gov/
features/OrbitsCatalog (accessed January 30, 2022).

<br />

[2] E.F Taylor and J. A. Wheeler, *Exploring Black Holes: Introduction to General Relativity*. 2000, Addison Wesley Longman, Inc.

<br />

[3] T. Dray, *Differential Forms and the Geometry of General Relativity*. 2015, Taylor & Franics Group, LLC.

<br />

[4] C. W. Misner, K. S. Thorne, and J. A. Wheeler, *Gravitation*. 2017, Princeton University Press.

<br />

[5] C. Bambi, *Introduction to General Relativity: A Course for Undergraduate Students of Physics*.  2018, Springer.

<br />

[6] J. R. Taylor, *Classical Mechanics*. 2005, University Science Books.
<br />

[7] G. van Rossum, Guido; Warsaw, Barry; Coghlan, Nick. "PEP 8 -- Style Guide for Python Code." pythong.org. https://www.python.org/dev/peps/pep-0008/ (accessed December 1, 2021)

<br />


\pagebreak

# Appendices

<!--\setlength{\parindent}{4em}-->

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
