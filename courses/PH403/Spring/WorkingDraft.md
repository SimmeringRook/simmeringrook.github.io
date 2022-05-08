---
title: "Cartographer: Using Python to Animate the Motion of Low-Mass Objects about a Schwarzschild Blackhole"
author:
  - Thomas Knudson `\\\\`{=latex} Advised by Dr. Kathryn Hadley
subtitle: "Department of Physics, OSU"
date: "May 6, 2022"
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
    \usetikzlibrary{arrows, automata}
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
    \usepackage{indentfirst}
---

\newacronym{gr}{GR}{general relativity}
\newacronym{sr}{SR}{special relativity}
\newacronym{gps}{GPS}{Global Position System}
\newacronym{bh}{BH}{black hole}
\captionsetup{format=hang,indention=-0.5cm}
\onehalfspacing
\setlength{\parindent}{4em}
\setlength{\parskip}{1.5em}

\pagebreak

# Abstract {-}

The computational framework, Cartographer, created and examined in this study focused on two key aspects: (1) visualizing exact and simulated motion in general relativity and (2) creating a framework that can be easily extended to describe more complex geometries of general relativity. Even the simplest geometric model of general relativity, the Schwarzschild geometry, requires a mathematical representation that is very complex for most undergraduate physics students. The main method for developing intuition of a object's geodesic (path) is either through examining the equation in detail and reasoning about the described behaviour (radius of orbit, is there an orbit, eccentricity, etc) or by cross comparing various 2-D graphs of coordinates/attributes. The latter involves reasoning through energy versus r-coordinate plots combined with spacetime diagrams showing time vs r-coordinate, time vs phi, or even phi versus r-coordinate.

The spacetime geometry is discretized into a lattice of nodes. The theoretical geodesics are represented in the three (4?) dimensional plots through numeric integration using the Verlet velocity method. The computational framework then finds the path the object should take, based off initial conditions, by extending the lattice into a weighted graph. The framework then uses the $A^*$ pathfinding algorithm to find the next step the object will take by calculating the action for each possible neighboring node.

The accuracy of the simulate path is directly related to the resolution of the discreteness of the underlying spacetime but has a minimum error threshold proportional to the theoretical path. While it is impossible to remove all error from both the theory and simulated paths, this error can be minimized to a requested precision, allowing for quicker run times and reducing hardware requirements for the computational framework. This framework offers an interface for undergraduate students to approach motion in general relativity in an easier method, requiring only the basic familiarity with python taught in the PH 36X courses. These visualizations also surpass the equivalent representations provided in various texts by allowing a third dimension to be represented: 2-dimensions of space and 1-dimension of time via rotatable animations.

\glsresetall

\pagebreak

\listoffigures

\pagebreak

# Introduction

Galilean relativity is the model we use to describe relative velocities in everyday life and is fairly robust, requiring extremes to find the breaking points. Einstein’s famous thought experiment about light moving on a train is the perfect analog for describing problem involving \gls{gps} Satellites and their transmissions to Earth. Using Galilean relativity, we can illustrate the physical situation like in Figure \ref{fig:gpsDemonstration}, however, it fails to provide a consistent description of physics for both the satellite and Earth.

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

In short, each \gls{gps} satellite periodically transmits location data alongside a time-code [1]. Using \gls{sr}, we find a scaling factor, $\gamma$, that represents the strength of length contraction and time dilation caused by the relative velocity of the satellite to Earth. To calculate this factor, we must transition from the Galilean model of treating space and time distances separately to \gls{sr}’s spacetime. However, measurement and theory would still disagree on the time elapsed between ticks of both the Earth’s and the \gls{gps}’s light-clocks and that is because we have failed to consider the effects of gravity. These results are illustrated in Figure \ref{fig:timeDilationSum}.

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

### Old

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

### New

Before introducing the concepts and geometric model of \gls{gr} examined in this project, we first briefly recap the flat spacetime of \gls{sr}. As mentioned in the introduction, when we  attempt to model the physics of objects moving at significant fractions of the speed of light, Galilean relativity is insufficient. This problem is typically motivated to students by recounting Dr. Albert Einstein's thought experiment regarding two light clocks: one on a train platform, the other aboard a moving train.

Supposing two general assumptions: (1) the physical laws are consistent everywhere in the universe and (2) the speed of light is constant, we are forced to conclude that the Galilean method of measuring distance with the Pythagorean Theorem is no longer applicable. The "Surveyor's Parable" offers further motivation to measure time and space using the same dimensions: length. Time is multiplied by the speed of light, $c$, and we move from using the Euclidean geometric model which measures distance with \begin{equation}\label{eqn:pythagTheoremDistance} s = \sqrt{x^2 + y^2} \end{equation} to a non-Euclidean model. In this formalism, the hyperbolic distance formula, \begin{equation}\label{eqn:hyperbolicDistance} s^2 = x^2 - (ct)^2, \end{equation} is used. The two dimensional model described by Equation \ref{eqn:hyperbolicDistance} is called Minkowski spacetime. Equation \ref{eqn:hyperbolicDistance} is constructed from basis differentials and is called the **line element**:

\begin{equation}\label{eqn:hyperbolicDistance}
{ds}^2 = {dx}^2 - c^2(dt)^2.
\end{equation}

For the purposes of this paper and the code in Cartographer, we have adopted the common approach of using natural units, where we have set $c$ to be unity such that the equations can be represented in a less cluttered form. Previously, we only considered the positive sign for $ds^2$, but in cases where the separation in time coordinates is greater than spatial, a negative sign is used to keep all spacetime distances real numbers. The sign used on $ds^2$ signifies whether the path is space-like or time-like. In equations, this is more often represented by replacing $s$ with $\sigma$ or $\tau$, which represent **proper distance** and **proper time** respectively.

When the line element is altered to describe the motion of non-accelerating object, the path is then referred to as a **geodesic**. All objects that have mass follow time-like geodesics and as such, the equations of motion will use the time-like version of the line element, \begin{equation}\label{eqn:minkowskiTimelike} {d\tau}^2 = dt^2 - {dx}^2. \end{equation}

The geometric model for flat spacetime is not constrained to only describe one spatial dimension and one temporal. The line element for $\mathbb{M}^3$ using polar coordinates adds the azimuthal angle $\phi$, \begin{equation}\label{eqn:minkowskiPolar} {ds}^2 = - dt^2 + {dr}^2 + r^2{d\phi}^2 , \end{equation} and spherical coordinates follows the same expected form with $\theta$ corresponding to the polar angle: \begin{equation}\label{eqn:minkowskiSpherical} {ds}^2 =  - dt^2 + {dr}^2 + r^2(\sin^2{(\theta)}{d\phi}^2 + {d\theta}^2). \end{equation}

With Equation \ref{eqn:minkowskiSpherical}, we are only one step away from discussing \gls{gr}. Performing a similar thought experiment as with the trains, we place one light clock on the surface of the Earth and one in geostationary orbit. The observer on Earth will measure the light clock in orbit as ticking faster than the one on the surface, as mentioned in the Introduction. In \gls{sr}, we noted time dilation was a consequence do to motion, but the relative velocities between the satellite and Earth are zero. Considering this effect was absent in flat spacetime, we conclude that gravity must be the cause.

For the case of a single massive non-rotating and spherically symmetric object, we model gravity's influence by adding curvature to spacetime. This model is called the Schwarzschild geometric model and only requires a slight adjustment to the spherical Minkowski ($\mathbb{M}^4$) line element with two scaling factors: \begin{equation}\label{eqn:schwarzLine} {ds}^2 = - \left(1-\frac{2M}{r}\right)(dt)^2 + \frac{dr^2}{1-\frac{2M}{r}} + r^2(\sin^2{(\theta)}{d\phi}^2 + {d\theta}^2), \end{equation} where $M$ is the mass of the object measured in meters[^-211]. Only the $r$ and $t$ coordinates obtain this scaling factor as they represent gravitational length contraction and time dilation. If we use Equation \ref{eqn:schwarzLine} to find the path of an object very far away from the massive object, $r\rightarrow\infty$, the line element simplifies back to Equation \ref{eqn:minkowskiSpherical} and we regain the description of \gls{sr}.

[^-211]: When using the explicit formulation (not natural units), the mass term is $\frac{GM}{c^2}$, where $G$ is Newton's gravitational constant and $M$ is the mass in kilograms.

One important distinction between \gls{sr} and \gls{gr} is the classification of inertial reference frames. In \gls{sr}, there is no preferred frame and all frames using the line element will measure the same spacetime separation between events. \gls{gr} requires a slight change and creates three categories of inertial reference frames: the **bookkeeper**, **shell observers**, and **rain** frames. The bookkeeper is an observer very far away ($r\rightarrow\infty$) from the massive object and performs their measurements in flat spacetime ($\mathbb{M}^4$). These are the geometric coordinates of the Schwarzschild model and whose basis differentials appear in Equation \ref{eqn:schwarzLine}.

Shell observers are surfaces of a constant coordinate, typically $r$ or $t$, in proximity to the massive object. As a result, their measurements are affected by the curvature and they measure contracted length and dilated time when compared to the bookkeeper. Figure \ref{fig:schwarzTriangle} visually represents their relations using hyperbolic triangles.

\begin{figure}[H]
  \begin{subfigure}{.5\textwidth}
    \centering
    \scalebox{1.5}{
      \begin{tikzpicture}

      % create coordinates
      \coordinate (O) at (0,0);
      \coordinate (L) at (0,5);
      \coordinate (P) at (-2,0);

      % Construct triangle
      \draw (P) -- (L) node [midway, above, sloped] {$dr_{shell} = \frac{dr_{BK}}{\sqrt{1-\frac{2M}{r_{shell}}}}$};
      \draw (O) -- (L) node [midway, right] {$\sqrt{1-\frac{2M}{r_{shell}}}$};
      \draw (O) -- (P) node [midway, below] {$dr_{BK}$};

      \end{tikzpicture}
    }
    \caption{Distance}
    \label{fig:schwarzDistanceTriangle}
  \end{subfigure}
  \hfill
  \begin{subfigure}{.5\textwidth}
    \centering
    \scalebox{1.5}{
      \begin{tikzpicture}

      % create coordinates
      \coordinate (O) at (0,0);
      \coordinate (L) at (0,-5);
      \coordinate (P) at (-2,0);

      % Construct triangle
      \draw (P) -- (L) node [midway, below, sloped] {$dt_{shell} = \sqrt{1-\frac{2M}{r_{shell}}} dt_{BK}$};
      \draw (O) -- (L) node [midway, right] {$\sqrt{1-\frac{2M}{r_{shell}}}$};
      \draw (O) -- (P) node [midway, below] {$dt_{BK}$};

    \end{tikzpicture}
    }
    \caption{Time}
    \label{fig:schwarzTimeTriangle}
  \end{subfigure}
  \caption{The two hyperbolic triangles represent the difference between physical quantities and their geometric coordinates. Extending a latticework of these constructions for each coordinate allows for the creation of embedding diagrams like Figure \ref{fig:Embedding}, which offer a direct visual representation of the underlying curvature.}
  \label{fig:schwarzTriangle}
\end{figure}

By constructing concentric hypersurfaces of constant $r$ and setting each shell's vertical axis value equal to $\sqrt{1-\frac{2M}{r}}$, we can construct an embedding diagram, which helps visualize the increasing curvature as $r$ approaches $2M$. Figure \ref{fig:Embedding} shows the result of this process using Cartographer for shells where $\theta$ has been set to $\pi/2$ and the other coordinate suppressed ($t$ and $r$ respectively for Figures \ref{fig:Embedding-Distance} and \ref{fig:Embedding-Time}). These diagrams omit the shells of $r=2M$, as that hypersurface represents the event horizon, where there is infinite curvature and no stationary reference frame can exist.

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{embedding_diagram_distance.png}
      \caption{Distance}
      \label{fig:Embedding-Distance}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{embedding_diagram_time.png}
      \caption{Time}
      \label{fig:Embedding-Time}
    \end{subfigure}
  \caption{The two-dimensional projection of the three-dimensional surfaces describe by revolving Equations \ref{eqn:ShellTime} and \ref{eqn:ShellDist} about the origin. Each embedding diagram shows cross-sections for surfaces of constant $t$ and $r$ by using height to represent the strength of curvature at each surface. The $\theta$ coordinate is surpressed through spherical symmetry by taking cross-sections in the equitorial plane($\theta=\pi/2$).}
  \label{fig:Embedding}
\end{figure}

We conclude this brief overview of \gls{gr} with a disucssion on the equations of motion in Schwarzschild geometry. Since gravity is curvature, objects in free fall follow geodesics. Adopting the nomenclature from Taylor and Wheeler, we refer to these free falling objects as **stones**. As mentioned with Equation \ref{eqn:minkowskiTimelike}, stones will move through Schwarzschild spacetime on time-like geodesics, and the line element from which the equations of motion will be derived changes from Equation \ref{eqn:schwarzLine} to \begin{equation}\label{eqn:schwarzTimelike} {d\tau}^2 = \left(1-\frac{2M}{r}\right)(dt)^2 - \frac{dr^2}{1-\frac{2M}{r}} - r^2{d\phi}^2, \end{equation} where we use spherical symmetry to simplify the disucssion to the equitorial plane ($\theta=\pi/2$).

In cases where the motion is only radial, the convention is to set the azimuthal angle of $\phi$ to zero. With that, we only need to solve Equation \ref{eqn:schwarzTimelike} for $dr/d\tau$ and this motion is examined in Section \ref{radialMotion}. For paths with non-zero angular momentum, there is an effective potential which describes the orbit the stone will take. This effective potential takes the form \begin{equation}\label{eqn:veffective} \left( \frac{V}{m} \right)^2 = \left(1-\frac{2M}{r}\right)\left(1+\frac{(L/m)^2}{r^2}\right), \end{equation} where $L/m$ is the angular momentum per unit mass of the stone. Figure \ref{fig:veffective_vs_r} highlights the dependence on $L/m$ with $V/m$ plotted versus $r$-coordinate for significant values of $L/m$.

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{veff_vs_r_L0.jpg}
      \caption{$L/m=0$}
      \label{fig:veffective_vs_r_L0}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{veff_vs_r_Lsqrt(12).jpg}
      \caption{$L/m=\sqrt{12}$}
      \label{fig:veffective_vs_r_Lsqrt(12)}
    \end{subfigure}
    \newline
    \vspace{0.5cm}
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{veff_vs_r_L4.jpg}
      \caption{$L/m=4$}
      \label{fig:veffective_vs_r_L4}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics{veff_vs_r_L45.jpg}
      \caption{$L/m>4$}
      \label{fig:veffective_vs_r_L45}
    \end{subfigure}
  \caption{Effective potential versus $r$-coordinate. For the case of zero angular momentum, a stone following a radial geodesic with any energy value will travel directly towards event horizon. The dotted red lines for Figures \ref{fig:veffective_vs_r_Lsqrt(12)}, \ref{fig:veffective_vs_r_L4}, and \ref{fig:veffective_vs_r_L45} denote the $r$-coordinate for a circular orbit, if the stone's energy per unit mass is equal to the effect potential.}
  \label{fig:veffective_vs_r}
\end{figure}

The first value of angular momentum that supports a circle orbit is $L/m=\sqrt{12}$, located at $r=6M$ and is unstable: any change to the energy of the stone will cause its orbit to decay towards the event horizon. For stones with angular momentum greater than or equal to $4$, the effective potential has a prominent peak. If the stone's energy per unit mass, $E/m$, is less than the value of this local maximum for the effective potential, the stone will orbit the massive object with the corresponding minimum radius and not be captured by the event horizon. At $L/m=4$, the stone can maintain a stable circular orbit at $r=12M$. If the stone has an energy value greater than the local minimum of the effective potential (but less than the peak), the stone will have an eliptical orbit. Finally, in the case where the peak of $V/m$ is greater than unity, and the stone starts with $E/m=1$ (free fall starting at rest, collocated with the bookkeeper), the stone's orbit will be hyperbolic: coming in from $r\rightarrow\infty$, partially rotating about the massive object, and then escaping back out to the bookkeeper.

\pagebreak

## Cartographer: Implementation and Design Philosophy {#design}

The Cartographer framework works by discretizing curved spacetime into a lattice of vertices. The `Latticework` class is initialized by specifying the interval and resolution for each spatial dimension. These parameters are independent of each other and allow for optimization with respect to computational runtime versus accuracy of the simulation. The `Latticework` object then instantiates two NumPy arrays as a mesh to represent the spacetime geometry.

At this stage, the lattice can be used to explore the underlying geometry through the embedding diagrams in Section \ref{distanceTimeAndEmbedding}. To visualize motion, two `Stone` objects are created with the initial conditions to be explored: energy per unit mass, $E/m$, and orbital angular momentum[^-221] per unit mass, $L/m$. These objects are used as parameters for calculating both their theoretical and simulated paths.

The `VerletPathfinding` class uses numerical integration with the Verlet Velocity method (Section \ref{verletAlgo}) to calculate the theoretical geodesic and uses a time step size parameter for controlling the accuracy of the path. The `Latticework` class uses the $A^*$ ("A star") pathfinding algorithm (Section \ref{astarAlgo}) and the principle of least action to determine how the stone should move about the given geometry. A selection of helper data classes created to aid in the readability and verbosity of the code are featured in Appendix \ref{helperClasses}.

[^-221]: Future references to angular momentum will omit the *orbital* clarifier as spin angular momentum is not discussed or explored in this paper.

$$\ $$

### Verlet Velocity Algorithm {#verletAlgo}

The Verlet Velocity Algorithm approximates future position, velocity, and acceleration by using two time steps of data to calculate the next time step. This algorithm, like Euler's method, uses a Taylor series expansion of the position function around a time $t$ describing the future position as

\begin{equation}\label{eqn:TaylorPosition}
x(t + \Delta t) = x(t) + \Delta t x^\prime (t) + \frac{(\Delta t)^2 x^{\prime\prime} (t)}{2} + \mathcal{O}(\Delta t^3).
\end{equation}

A simple Python implementation of Equation \ref{eqn:TaylorPosition} typically looks like

```py
dt, t, total_time = ...
while t < total_time:
    current_acceleration = net_force / mass
    current_velocity = current_velocity + current_acceleration * dt
    current_position = current_position + current_velocity*dt
    t = t + dt
```

While both the Verlet Velocity and Euler's methods use the forward difference definition for derivatives,

\begin{equation}
x^\prime (t) \approx \frac{x(t + \Delta t) - x(t)}{\Delta t},
\end{equation}

Euler's method only considers the derivatives and the position function at $t$ to inform the output for $t+\Delta t$. The Verlet Velocity method improves the accuracy by considering both expansions for $x(t+\Delta t)$ and $x(t-\Delta t)$. $x(t+\Delta t)$ is then reexpressed as the sum of the two expansions,

\begin{equation}
x(t+\Delta t) = 2x(t) - x(t-\Delta t) + \frac{(\Delta t)^2 a(t)}{2} + \mathcal{O}(\Delta t^4) .
\end{equation}

$$\ $$

### $A^*$ Pathfinding Algorithm {#astarAlgo}

The $A^*$ search algorithm is a heuristic method for navigating graphs. Two common applications for this type of algorithm are the movement of units in a strategy computer game and a mobile \gls{gps} providing directions. The problem is classified by considering a weighted graph of nodes, such as in Figure \ref{fig:weightedGraph}. Each node represents some intermediate destination along the way from a *source* to the desired *target*. Each edge then has a real valued number corresponding to the *cost* of moving to the next node.

\begin{figure}[H]
\centering
    \scalebox{0.75}{
        \begin{tikzpicture}[
                    > = stealth, % arrow head style
                    shorten > = 1pt, % don't touch arrow head to node
                    auto,
                    node distance = 3cm, % distance between nodes
                    semithick % line style
            ]

            \tikzstyle{every state}=[
                draw = black,
                thick,
                fill = white,
                minimum size = 4mm
            ]

            \node[state] (X1) {$x_1$};
            \node[state] (X4) [right of=X1] {$x_4$};
            \node[state] (X2) [above of=X4] {$x_2$};
            \node[state] (X3) [below of=X4] {$x_3$};
            \node[state] (X5) [right of=X4] {$x_5$};
            
            \draw[-stealth] (X1) -- (X2) node[midway] {$y_{12}$};
            \draw[-stealth] (X1) -- (X3) node[left, midway ] {$y_{13}$};
            \draw[-stealth] (X2) -- (X5) node[midway] {$y_{25}$};
            \draw[-stealth] (X3) -- (X4) node[midway] {$y_{34}$};
            \draw[-stealth] (X4) -- (X5) node[midway] {$y_{45}$};
        \end{tikzpicture}
    }
    \caption{In this directed graph, each $x_i$ is a node and each $y_{ij}$ represents the cost to traverse from $x_i$ to $x_j$. For this example, there are two possible paths from the source node $x_1$ to $x_5$: (1) $x_1 \rightarrow x_2 \rightarrow x_5$ and (2) $x_1 \rightarrow x_3 \rightarrow x_4 \rightarrow x_5$ with total respective costs of $y_{12}+y_{25}$ and $y_{13}+y_{34}+y_{45}$. }
    \label{fig:weightedGraph}
\end{figure}

While the example shown in Figure \ref{fig:weightedGraph} is simplistic, the underlying heuristic of $A^*$ will not increase in complexity as the weight graph increases. The algorithm walks through the graph by visiting each node and recording the cost to reach each neighboring node. Once the target node has been reached, the algorithm then sorts through all possible paths by the smallest total cost. Figure \ref{fig:WeightGraph2} represents the same structure but with numeric values for the costs, which allows for a definitive answer to "what is the shortest path from $x_1$ to $x_5$?"

\begin{figure}[H]
    \begin{subfigure}{0.9\textwidth}
    \centering
    \scalebox{0.75}{
        \begin{tikzpicture}[
                > = stealth, % arrow head style
                shorten > = 1pt, % don't touch arrow head to node
                auto,
                node distance = 3cm, % distance between nodes
                semithick % line style
        ]

        \tikzstyle{every state}=[
            draw = black,
            thick,
            fill = white,
            minimum size = 4mm
        ]

        \node[state] (X1) {$x_1$};
        \node[state] (X4) [right of=X1] {$x_4$};
        \node[state] (X2) [above of=X4] {$x_2$};
        \node[state] (X3) [below of=X4] {$x_3$};
        \node[state] (X5) [right of=X4] {$x_5$};
        
        \draw[-stealth] (X1) -- (X2) node[midway] {$10$};
        \draw[-stealth] (X1) -- (X3) node[midway] {$2$};
        \draw[-stealth] (X2) -- (X5) node[midway] {$7$};
        \draw[-stealth] (X3) -- (X4) node[midway] {$3$};
        \draw[-stealth] (X4) -- (X5) node[midway] {$5$};

        \end{tikzpicture}
    }
    \end{subfigure}
    \newline
    \begin{subfigure}{0.45\textwidth}
    \centering
    \scalebox{0.75}{
        \begin{tikzpicture}[
                > = stealth, % arrow head style
                shorten > = 1pt, % don't touch arrow head to node
                auto,
                node distance = 3cm, % distance between nodes
                semithick % line style
        ]

        \tikzstyle{every state}=[
            draw = black,
            thick,
            fill = white,
            minimum size = 4mm
        ]

        \node[state] (X2) {$x_2$};
        \node[state] (X1) [below left of=X2] {$x_1$};
        \node[state] (X5) [below right of=X2] {$x_5$};
        
        \draw[-stealth] (X1) -- (X2) node[midway] {$10$};
        \draw[-stealth] (X2) -- (X5) node[midway] {$7$};

        \end{tikzpicture}
    }
    \caption{Path 1: $x_1 \rightarrow x_2 \rightarrow x_5$}
    \label{fig:2wgb}
    \end{subfigure}
    \hfill
    \begin{subfigure}{0.45\textwidth}
    \centering
    \scalebox{0.75}{
        \begin{tikzpicture}[
                > = stealth, % arrow head style
                shorten > = 1pt, % don't touch arrow head to node
                auto,
                node distance = 3cm, % distance between nodes
                semithick % line style
        ]

        \tikzstyle{every state}=[
            draw = black,
            thick,
            fill = white,
            minimum size = 4mm
        ]

        \node[state] (X1) {$x_1$};
        \node[state] (X4) [right of=X1] {$x_4$};
        \node[state] (X3) [below of=X4] {$x_3$};
        \node[state] (X5) [right of=X4] {$x_5$};
        
        \draw[-stealth] (X1) -- (X3) node[midway] {$2$};
        \draw[-stealth] (X3) -- (X4) node[midway] {$3$};
        \draw[-stealth] (X4) -- (X5) node[midway] {$5$};

        \end{tikzpicture}   
    }
    \caption{Path 2: $x_1 \rightarrow x_3 \rightarrow x_4 \rightarrow x_5$}
    \label{fig:2wgc}
    \end{subfigure}
    \caption{While the first path (Figure \ref{fig:2wgb}) has fewer edges traversed, the total cost is higher than the second path (Figure \ref{fig:2wgc}).}
    \label{fig:WeightGraph2}
\end{figure}

In Cartographer, the edge cost for radial neighbors (same $\phi$, different $r$) is given by the action, whereas for $\phi$ neighbors, the cost of change in angular momentum is used. While the specific implementation of $A^*$ is discussed in Section \ref{pathfinding}, the underlying concept is unchanged.

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

## Angular Momentum, Effective Potential, and Paths {#vEff}

> TODO: Potential vs r-coordinate

\begin{figure}[H]
    \centering
    \includegraphics[width=15cm,keepaspectratio,]{veff.png}
    \caption{The plot of $V_{eff}$ as a function of $r$-coordinate. The dashed function is the Newtonian description of the gravitational potential with the notable behaviour that an in-falling object with non-zero angular momentum cannot reach the horizon ($r=2M$). }
    \label{fig:EffectivePotential}
\end{figure}

Figure \ref{fig:vEff3d} shows what the effective potential looks like rotated about the azimutal axis (demonstrating symmetery in $phi$). With no angular momentum, the effective potential plot resembles an embedding diagram, telling all stones to fall radially inward. However, with non-zero angular momentum, a stone has two potential barriers it must cross as $V_{eff}$ adopts a valley-like shape for $r$-coordinates in the interval of $(6M, 25M)$. If the stone doesn't have enough energy, it will have a hyperbolic path and perform a partial orbit before escaping to infinity. If the stone starts at rest in this valley, $E/m > V_{eff}$ for $r\in (6M, 25M)$, the stone will orbit between the two extreme $r$-coordinates bound where $E/m = V/m$. If the stone has energy greater than the peak $V/m$, it will perform a parabolic orbit and be captured by the event horizon.

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics[width=7.5cm,keepaspectratio,]{effective_potential_L0.png}
      \caption{$L/m=0$}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics[width=7.5cm,keepaspectratio,]{effective_potential_L4.png}
      \caption{$L/m=4$}
      \label{fig:sub-first}
    \end{subfigure}
  \caption{Comparision of how the effective potential changes as the stone's angular momentum increases. }
  \label{fig:vEff3d}
\end{figure}

$$\ $$

### Pathfinding in Schwarzschild {#pathfinding}

> TODO: discuss how the algorithm operates

\pagebreak

# Motion about a Schwarzschild Blackhole

## Gaining Speed and Radial Geodesics {#radialMotion}

As overviewed in Section \ref{primer}, the equations of motion for an object in free-fall in spacetime are given from the line element. We begin by examining the simplest case of motion in the Schwarzschild geometry: radial timelike geodesics. For this case, we go a step further and examine how motion is observed by different refernce frames by changing the basis differentials used in the line element. The two paths shown in Figure \ref{fig:RainSpeed} correspond to the bookkeeper and to shell observers.

\begin{figure}[H]
  \centering
  \includegraphics[width=15cm,keepaspectratio,]{rain_speed.png}
  \caption{Speed of in-falling object as measured from a series of different reference frames. Note the diverging observations from the Bookkeeper and the Shell Observer as $r_{shell}$ approachs $2M$. The Bookkeeper measures the speed of the stone to be increasing in the region of $r>6M$ before its deceleration to $v=0c$ at the event horizon.}
  \label{fig:RainSpeed}
\end{figure}

Since we are considering a timelike geodesic with only change in the $r$ and $t$ coordinates, the line element (Equation \ref{eqn:SchwarzLineElement}) simplifies to

\begin{equation}\label{eqn:timelikeRadial}
{d\tau}^2 = \left(1-\frac{2M}{r}\right) {dt_{BK}}^2 - \frac{{dr_{BK}}^2}{\left(1-\frac{2M}{r}\right)}.
\end{equation}

To obtain the speed of the stone as a function of $r$-coordinate, $dr_{BK}/dt_BK$, we must substitute an equivalent definition for $d\tau$. This other relation is the energy per unit mass of the stone \cite{EBH} and takes the form of

\begin{equation}\label{eqn:SchwarzEnergy}
\frac{E}{m} = \left(1-\frac{2M}{r}\right)\frac{dt}{d\tau}.
\end{equation}

We then combine Equations \ref{eqn:SchwarzEnergy} and \ref{eqn:SchwarzLine} by equating them after solving each for proper time. The result is speed (as a multiple of $c$) as a function of $r$-coordinate for the stone, as measured by the Bookkeeper:

\begin{equation}\label{eqn:SchwarzRadBK}
\frac{dr_{bk}}{dt_{bk}}=-\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}.
\end{equation}

The sign of Equation \ref{eqn:SchwarzRadBK} describes an in-falling (when negative) or an escaping (when postive) object. As the stone reaches $r=2M$, the first quantity approaches zero, which corresponds to far-away observers observing in-falling objects slowing down as they approach the event horizon and never crossing. To obtain the speed measured by shell observes as the stone passes, we substitute in the division of Equation \ref{eqn:ShellDist} by Equation \ref{eqn:ShellTime} into the left-hand side of Equation \ref{SchwarzRadBK}, and obtain

\begin{equation}\label{eqn:SchwarzRadShells}
\frac{dr_{shell}}{dt_{shell}}=-\sqrt{\frac{2M}{r_{shell}}}.
\end{equation}

Now that the $1-\frac{2M}{r}$ term is absent, we discover the first disagreement of observations between the different families of observers.

As shown in Figure \ref{fig:RainSpeed}, this diverging behaviour has physical consequences. If we give the Bookkeeper the most senstive equipment, they measure any in-falling object to stop as it reaches the event horizon and would never observe any object passing through. In practice, if we model light being emitted by the stone towards the Bookkeeper as continous, the wavelength of light that informs any outside observer that the stone has crossed the horizon will be gravitationally redshifted to an infinite wavelength. In re-examinating of Figures \ref{fig:ShellTime} and \ref{fig:ShellDist}, if we consider the extreme case as the contraction scaling factor, $\zeta$, approaches $0$, the un-contracted length, $\lambda$, must approach infinity such that the length measured at $r\rightarrow BK$ remains unity as described below:

\begin{equation}\label{eqn:ExampleRedshift}
\lim_{\zeta\rightarrow 0 ,\ \lambda\rightarrow\infty} \zeta \times \lambda= 1.
\end{equation}

$$\ $$

### Rain versus Hail {#rainAndHail}

> TODO: Rain frame (rest at infinity) versus Hail frame (initial speed)

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics[width=7.5cm,keepaspectratio,]{theory_and_simulated_L0_V20_elapsed_time.png}
      \caption{Elapsed proper time}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics[width=7.5cm,keepaspectratio,]{theory_and_simulated_L0_V20_effective_potential.png}
      \caption{Effective Potential}
      \label{fig:sub-first}
    \end{subfigure}
  \caption{Comparision of the simulated path (purple) versus the exact path (brown) for a stone starting at rest at $r/M = 20$ with no angular momentum.Both paths use the geodesic equation from the stone's reference frame such that all time coordinates are measure in proper time.}
  \label{HailSpeed}
\end{figure}

> TODO: Introduce geodesic equation and discuss purple's funnel in (a)

$$\ $$

> TODO: Hail frame

\pagebreak

## Non-zero Angular Momentum

$$\ $$

### Hyperbolic and Parabolic

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

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics[width=7.5cm,keepaspectratio,]{theory_and_simulated_L4_V20_elapsed_time.png}
      \caption{Elapsed proper time}
      \label{fig:sub-first}
    \end{subfigure}
    \hfill
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics[width=7.5cm,keepaspectratio,]{theory_and_simulated_L4_V20_effective_potential.png}
      \caption{Effective Potential}
      \label{fig:sub-first}
    \end{subfigure}
  \caption{Comparision of the simulated path (purple) versus the exact path (brown) for a stone starting at rest at $r/M = 20$ with and angular momentum per unit mass of $4$. Both paths use the geodesic equation from the stone's reference frame such that all time coordinates are measure in proper time.}
  \label{fig:angular}
\end{figure}

\pagebreak

# Conclusions

> TODO: Take inspiration from answering brother's questions and use it to help structure concepts for conclusion

My Brother - 04/21/2022
I missed why there's a difference in the first place.  Is it just to see the spirals?  I assume even with a different algorithm they'd start at the same point

Me — 04/21/2022
they start at the same point, but purple is constrained to move only to nearest neighbors at each step, which can lead to extra orbits that shouldn't be there
like in this case, where the lattice's resolution doesn't allow for smaller steps

My Brother — 04/21/2022
oh, Aster is A*, I thought it was some physicist's name
Astar and Verlet, the famous astronomer duo 
what was the thesis proposal again?  trying to find a performant and efficient approximation?

Me — 04/21/2022
if I switch to Dijkstra's, I can probably remove some of that inaccuracy due to resolution
the goal was to create a framework that created visualizations of motion in curved spacetime
it didn't need to do the pathfinding side of things, but I wanted to use the lattice that was being created to see if the geometry would be able to tell an object how it should move
overall, it does goes physical answers (as long as the resolution isn't too awkward), but does at the very least exclude the extreme unphysical ones such as moving into the horizon and back out, or escaping when it shouldn't
an example of the lattice's resolution giving an unphysical path - its supposed to be elliptical, not helical
Image

Me — 04/21/2022
its more of a pedagogical venture than trying to discover new stuff
with the design and language, future undergrads can take this and specify initial conditions and get a view of:
- how specifying different resolutions in r and phi can lead to things that aren't outright wrong, but not be descriptive of what should happen
- how varying initial conditions can give expected or unexpected paths for motion
basically, a much more approachable and easier to tinker with version than trying to cross compare various 2-d plots and interpret what will happen for various quantities

My Brother — 04/21/2022
so you're intentionally trying to say "this graph is somewhat incorrect so keep that in mind when simplifying your math"?

Me — 04/21/2022
I think its something I'll mention; we typically expect the model to do something crazy if we ask it to do something that isn't physical. More often than not, the model doesn't explode but more like fail silently
Image
this is basically all that's given to talk about different orbits
after sufficient time, you can develop an intuition on what's going to happen for an initial energy, but what makes part of this worse is that V/m depends on the object's angular momentum, and so its shape changes as well. This isn't enough, as is, to truly inform you about what the motion looks like in Schwarzschild
and, as far as I know, these plots don't exist for an object without angular momentum but approaching the black hole with some offset such that its not a direct radial path inwards (think of gravitational sling shot maneuver from Far Scape)
not super novel, just helping pave the way for others in the future (and deepen my understanding of the concepts)

My Brother — 04/21/2022
no, I get that part.  I just am stuck on the part where you have two paths and one seems more accurate because it uses detailed math while the other was an approximation
i.e. was there some reason behind looking and displaying A* or other pathfinding algorithms?
versus simply showing the brown path

Me — 04/21/2022
I guess you could have done the numeric integration as a standalone, since it is essentially external to the discretized spacetime. So you'd have to generate a visualization of the black hole in some variation to get additional context.
there was a stretch goal in the proposal to take this underlying framework and add it to the protostar generation models, and in that case you'd need the pathfinding bit

My Brother — 04/21/2022
I see

Me — 04/21/2022
its not perfectly setup up such that you can swap things out with inheritance, but its fairly close
and i'll most likely tinker with this for fun in the future with getting that to work; so you can see how changing the geometry of spacetime alters the paths
oh, thats the other thing: the numeric integration (brown) only describes paths for objects in free fall; so if we move to the slightly more complicated curved spacetime where the blackhole has a charge and you wanted to ask about the path a charged particle would take - brown no longer applies

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

- Python 3.10
- NumPy
- Matplotlib

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

### Changing Perspective {#radialShellSpeed}

> **TODO:** Scrap; salvage some description for use in other sections

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

## Cartographer

> TODO: To what extent should the code base be added?