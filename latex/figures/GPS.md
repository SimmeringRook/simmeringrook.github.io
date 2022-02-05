---
geometry:
 - a4paper
 - margin=2cm
graphics: yes
header-includes: |
    \usepackage{pgfplots}
    \usepackage{tikz,tikz-3dplot} 
    \usepackage{tkz-euclide}
    \usetikzlibrary{shapes.geometric}
    \usetikzlibrary{calc}
    \usetikzlibrary{angles}
---

```TeX
\begin{tikzpicture}

  % create coordinates
  \coordinate (O) at (0,-1.25);
  \coordinate (gps) at (8,0);
  \coordinate (V) at (8,2);

  % Earth
  \node[circle,draw,text=white,fill=gray,minimum size = 50, outer sep = 2] (c1) at (O) {Earth};
  \draw[blue, dashed] (c1) ellipse (0.85 and 0.25);
  \node at (c1.west) [left] {$\Delta t$};
  \node at (c1.south) [below=10pt, blue] {$dt_{Earth}=\sqrt{1-\frac{2M}{r_{Earth}}}dt$};

  % Satellite
  \node[circle, draw, outer sep = 2] (c2) at (gps) {$\ $};
  \node at (c2.east) [right] {$\Delta t^\prime = \gamma\Delta t$};
  \node at (c2.south) [below] {GPS Satellite};

  %\clip (-2,-4) rectangle (12,4);

  % Add curvature
  \tikzstyle{shell}=[ellipse,dash pattern=on \pgflinewidth off 2pt, outer sep=12pt]

  \node[shell, minimum width=450, minimum height=150] (gpsShell) at (0,0) {};
  \node at (gpsShell.south east) [below, right, sloped, red] {$dt_{GPS}=\sqrt{1-\frac{2M}{r_{GPS}}}dt$};
  \draw[red, dashed] (gpsShell) ellipse (8 and 2.6);

  \draw[dotted] (0,-0.55) ellipse (5.75 and 1.5);
  \draw[dotted] (0,-0.8) ellipse (3.5 and 1);
  \draw[dotted] (0,-1) ellipse (2 and 0.5);

  % Label the radius
  \draw[dashed] (c1.east) -- (c2) node [midway, below, sloped] {$2.02\times 10^7\ m$};

  % Show velocity
  \draw[stealth-] (V) --++ (c2) node [midway, right] {$3.861\times 10^3\frac{m}{s}$};

\end{tikzpicture}
```

\begin{tikzpicture}

  \coordinate (gpsTOrigin) at (-4,0);
  \coordinate (gpsSROrigin) at (0,0);
  \coordinate (gpsGROrigin) at (4,0);

  % GPS Total
  \node[circle,draw,text=white,fill=white,minimum size = 100] (GPST) at (gpsTOrigin) {};
  \node at (GPST.south) [below] {Total time between clock ticks};
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
  \node[circle,draw,text=white,fill=white,minimum size = 100] (GPSSR) at (gpsSROrigin) {};
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
  \node[circle,draw,text=white,fill=white,minimum size = 100] (GPSGR) at (gpsGROrigin) {};
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


\begin{tikzpicture}

  \tikzstyle{clock}=[circle,draw,minimum size=100,inner sep=0pt]
  \tikzstyle{sign}=[rectangle,minimum width=50,inner sep=0pt]

  \node[sign]  (equals) at (0,0)                     {=};
  \node[clock] (GPST)   at (-3,0)   {};
  \node[clock] (GPSSR)  at (3,0)  {};
  \node[sign]  (plus)   at (6,0)   {+};
  \node[clock] (GPSGR)  at (9,0)    {};

  \coordinate (gpsTOrigin) at (GPST);
  \coordinate (gpsSROrigin) at (GPSSR);
  \coordinate (gpsGROrigin) at (GPSGR);

  % GPS Total
  \node at (GPST.south) [below] {GPS Clock tick};
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