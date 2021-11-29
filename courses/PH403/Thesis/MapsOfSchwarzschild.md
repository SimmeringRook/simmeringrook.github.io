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


# The Mapping of Schwarzschild

$$\ $$

## Distance, Time, and Embedding Diagrams

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

