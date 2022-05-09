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

We conclude this brief overview of \gls{gr} with a disucssion on the equations of motion in Schwarzschild geometry. Since gravity is curvature, objects in free fall follow geodesics. Adopting the nomenclature from Taylor and Wheeler, we refer to these free falling objects as **stones**. As mentioned with Equation \ref{eqn:minkowskiTimelike}, stones will move through Schwarzschild spacetime on time-like geodesics, and the line element from which the equations of motion will be derived changes from Equation \ref{eqn:schwarzLine} to \begin{equation}\label{eqn:schwarzTimelike} {d\tau}^2 = \left(1-\frac{2M}{r}\right)(dt)^2 - \frac{dr^2}{1-\frac{2M}{r}} - r^2{d\phi}^2, \end{equation} where we use spherical symmetry to simplify the disucssion to the equitorial plane ($\theta=\pi/2$). Two important properties of the stone encoded in Equation \ref{eqn:schwarzTimelike}, energy per unit mass and angular momentum per unit mass, come from dividing both sides of Equation \ref{eqn:schwarzTimelike} by $d\tau$. The first, energy per unit mass, is defined by \begin{equation}\label{eqn:energyPerUnitMass} \frac{E}{m} = \left(1-\frac{2M}{r}\right) \frac{dt}{d\tau}, \end{equation} and comes from the notion of \gls{sr}. For a stone far away ($r\rightarrow\infty$), this quantity reduces to unity for a stone at rest, or scaled by $\gamma$[^-212] for a stone with initial velocity. As featured previously, angular momentum per unit mass, \begin{equation}\label{eqn:angularMomentumPerUnitMass} \frac{L}{m} = r^2 \frac{d\phi}{d\tau}, \end{equation} arises from the conservation of angular momentum in a spherically symmetric model.

[^-212]: Recall that $\gamma$ is defined as $\left(1-\frac{v^2}{c^2}\right)^{-1/2}$, where $v$ is the relative speed of the object.

In cases where the motion is only radial, the convention is to set the azimuthal angle of $\phi$ to zero. With that, we only need to solve Equation \ref{eqn:schwarzTimelike} for $dr/d\tau$ and this motion is examined in Section \ref{radialMotion}. For paths with non-zero angular momentum, there is an effective potential which describes the orbit the stone will take. This effective potential takes the form \begin{equation}\label{eqn:veffective} \left( \frac{V}{m} \right)^2 = \left(1-\frac{2M}{r}\right)\left(1+\frac{(L/m)^2}{r^2}\right), \end{equation} where $L/m$ is the angular momentum per unit mass of the stone. Figure \ref{fig:veffective_vs_r} highlights the dependence on $L/m$ with $V/m$ plotted versus $r$-coordinate for notable possible paths due to the magnitude of $L/m$.

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

To offer a more intuitive representation of effective potential versus $r$-coordinate, we rotate the plots of Figure \ref{fig:veffective_vs_r} about the azimuthal axis and create a similar representation to the embedding diagrams of Figure \ref{fig:Embedding} with Figure \ref{fig:vEff3d}. However, with non-zero angular momentum, a stone has two potential barriers it must cross as $V_{eff}$ adopts a valley-like shape for $r$-coordinates in the interval of $(6M, 25M)$. If the stone doesn't have enough energy, it will have a hyperbolic path and perform a partial orbit before escaping to infinity. If the stone starts at rest in this valley, $E/m > V_{eff}$ for $r\in (6M, 25M)$, the stone will orbit between the two extreme $r$-coordinates bound where $E/m = V/m$. If the stone has energy greater than the peak $V/m$, it will perform a parabolic orbit and be captured by the event horizon.

\begin{figure}[H]
    \begin{subfigure}{.5\textwidth}
      \centering
      \includegraphics[width=7.5cm,keepaspectratio,]{effective_potential_L0.png}
      \caption{$L/m=0$}
      \label{fig:vEff3d_noL}
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

\pagebreak

## Cartographer: Implementation and Design Philosophy {#design}

The Cartographer framework works by discretizing curved spacetime into a lattice of vertices. Cartographer is written in version 3.10 of the Python programming language using the object-oriented programming methodolgy with the assistance of the NumPy and Matplotlib libraries. The `Latticework` class is initialized by specifying the interval and resolution for each spatial dimension. These parameters are independent of each other and allow for optimization with respect to computational runtime versus accuracy of the simulation. The `Latticework` object then instantiates two NumPy arrays as a mesh to represent the spacetime geometry.

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

The algorithm walks through the graph by visiting each node and recording the cost to reach each neighboring node. Once the target node has been reached, the algorithm then sorts through all possible paths by the smallest total cost. Figure \ref{fig:WeightGraph2} represents the same structure but with numeric values for the costs, which allows for a definitive answer to "what is the shortest path from $x_1$ to $x_5$?"

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

While the example shown in Figure \ref{fig:weightedGraph} is simplistic, the underlying procedure of $A^*$ will not increase in complexity as the weighted graph increases. Figure \ref{fig:cartographerGraph} provides an example of how $A^*$ treats navigating through the graph constructed by the `Latticework` object for a stone travelling counter-clockwise.

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

            \node[state] (R0P0) {$r_0, \phi_0$};
            \node[state] (R0P11) [right of=R0P0] {$r_0, \phi_{-1}$};
            \node[state] (R0P1) [left of=R0P0] {$r_0, \phi_{1}$};
            \node[state] (R1P0) [above of=R0P0] {$r_1, \phi_0$};
            \node[state] (R1P11) [right of=R1P0] {$r_1, \phi_{-1}$};
            \node[state] (R1P1) [left of=R1P0] {$r_1, \phi_{1}$};
            \node[state] (R11P0) [below of=R0P0] {$r_{-1}, \phi_0$};
            \node[state] (R11P11) [right of=R11P0] {$r_{-1}, \phi_{-1}$};
            \node[state] (R11P1) [left of=R11P0] {$r_{-1}, \phi_{1}$};
            
            \node (L0) [below of=R11P11] {$\ $};
            \node (L1) [below of=R11P1] {$\ $};

            \draw[-stealth] (R0P0) -- (R0P11);
            \draw[-stealth] (R0P0) -- (R0P1);
            \draw[-stealth] (R0P0) -- (R1P11);
            \draw[-stealth] (R0P0) -- (R1P1);
            \draw[-stealth] (R0P0) -- (R11P11);
            \draw[-stealth] (R0P0) -- (R11P1);
            \draw[-stealth] (R0P0) -- (R1P0);
            \draw[-stealth] (R0P0) -- (R11P0);

            \draw[-stealth] (L0) -- (L1) node[midway, below]{$\frac{L}{m}>0$};
        \end{tikzpicture}
    }
    \caption{In this example, the stone's current position would be at the center node: $(r_0, \phi_0)$. Each of the other nodes represent possible neighbors of the current position. The graph does not explicitly disallow travel in the clockwise direction (to the right). The edge costs are calculated and used to determine which of the possible neighbors the stone is permitted to actually travel to. }
    \label{fig:cartographerGraph}
\end{figure}

In Cartographer, the edge cost for radial neighbors (same $\phi$, different $r$) is given by the action, which is found by solving Equation \ref{eqn:schwarzTimelike} for $d\tau$. For $\phi$ neighbors, the cost of change in angular momentum is used. This allows the underlying graph to only be generated once, and only requires a recalculation of the edges if the stone's properties are changed. For the free fall motion examined in this project, the stone's properties of $E/m$ and $L/m$ are constant. Therefore, in the example shown in Figure \ref{fig:cartographerGraph}, the nodes with $\phi_0$ and $\phi_{-1}$ will have total edge costs that rule them out.

\pagebreak

# Motion about a Schwarzschild Blackhole

## Gaining Speed and Radial Geodesics {#radialMotion}

As overviewed in Section \ref{primer}, the equations of motion for an object in free-fall in spacetime are given from manipulations to Equation \ref{eqn:schwarzTimelike}. We begin by examining the simplest case of motion in the Schwarzschild geometry: radial timelike geodesics. For this case, we go a step further and examine how the speed of the stone is observed by different refernce frames by changing the basis differentials used in the line element. The two paths shown in Figure \ref{fig:RainSpeed} correspond to the bookkeeper and to shell observers.

\begin{figure}[H]
  \centering
  \includegraphics[width=15cm,keepaspectratio,]{rain_speed.png}
  \caption{Speed of in-falling object as measured from a series of different reference frames. Note the diverging observations from the Bookkeeper and the Shell Observer as $r_{shell}$ approachs $2M$. The Bookkeeper measures the speed of the stone to be increasing in the region of $r>6M$ before its deceleration to $v=0c$ at the event horizon.}
  \label{fig:RainSpeed}
\end{figure}

Since we are using natural units, $c$ will not be visible in this radial equation of motion, and so any numeric result must be scaled by $c$ to obtain a dimensionful answer. To obtain the speed of the stone as a function of $r$-coordinate, we substitute the $E/m$ from Equation \ref{eqn:energyPerUnitMass} for $d\tau$ and solve for $dr/dt$. The result is \begin{equation}\label{eqn:radialBK}\frac{dr_{bk}}{dt_{bk}}=-\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}. \end{equation} Since Equation \ref{eqn:radialBK} is initially squared, we must add back in the formation of direction by choosing the corresponding sign for the right-hand side. A negative value describes inward motion and a positive describes an escaping stone. As the stone reaches $r=2M$, the first quantity approaches zero, which corresponds to far-away observers observing in-falling objects slowing down as they approach the event horizon and never crossing, as shown in Figure \ref{fig:RainSpeed}.

To obtain the speed measured by shell observes as the stone passes, we change the basis diferentials from the bookkeeper to a shell observer by substituting in the division of \begin{equation}\label{eqn:ShellDistance} dt_{shell} = \sqrt{1-\frac{2M}{r}} dt \end{equation} by \begin{equation}\label{eqn:ShellTime} dt_{shell} = \sqrt{1-\frac{2M}{r}} dt \end{equation} into the left-hand side of Equation \ref{radialBK}, and obtain \begin{equation}\label{eqn:radialShell}\frac{dr_{shell}}{dt_{shell}}=-\sqrt{\frac{2M}{r_{shell}}}. \end{equation}

As shown in Figure \ref{fig:RainSpeed}, this diverging behaviour has physical consequences. If we give the Bookkeeper the most senstive equipment, they measure any in-falling stone to stop as it reaches the event horizon and would never observe it pass through. In practice, if we model light being emitted by the stone towards the Bookkeeper as continous, the wavelength of light that informs any outside observer that the stone has crossed the horizon will be gravitationally redshifted to an infinite wavelength.

Figures \ref{fig:cartographerRadialTheory} and \ref{fig:cartographerRadialSimulated} show the respective visualizations of the numerical integration and $A^*$ simulated path from Cartographer. The surface underneath both lines is the effective potential for a stone with no angular momentum (Figure \ref{fig:vEff3d_noL}) and agree completely. For this type of motion, the resolution of $r$ and $\phi$ set for the `lattice` only affects how smooth the $A^*$ path and effective potential surface are.

\begin{figure}[H]
  \centering
  \includegraphics[width=15cm,keepaspectratio,]{rain_speed.png}
  \caption{Speed of in-falling object as measured from a series of different reference frames. Note the diverging observations from the Bookkeeper and the Shell Observer as $r_{shell}$ approachs $2M$. The Bookkeeper measures the speed of the stone to be increasing in the region of $r>6M$ before its deceleration to $v=0c$ at the event horizon.}
  \label{fig:cartographerRadialTheory}
\end{figure}

\begin{figure}[H]
  \centering
  \includegraphics[width=15cm,keepaspectratio,]{rain_speed.png}
  \caption{Speed of in-falling object as measured from a series of different reference frames. Note the diverging observations from the Bookkeeper and the Shell Observer as $r_{shell}$ approachs $2M$. The Bookkeeper measures the speed of the stone to be increasing in the region of $r>6M$ before its deceleration to $v=0c$ at the event horizon.}
  \label{fig:cartographerRadialSimulated}
\end{figure}

$$\ $$

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
