---
header-includes: |
    \usepackage{pgfplots}
    \usepackage{tikz-3dplot}
---

Template: https://latexdraw.com/draw-a-sphere-in-latex-using-tikz/

```
TeX
\tdplotsetmaincoords{60}{115}
\pgfplotsset{compat=newest}

\begin{tikzpicture}[tdplot_main_coords, scale = 2.5]

% Create a point (SpacePoint)
\coordinate (SpacePoint) at (0,0,1.5);

% Create a point (SourcePoint)
\coordinate (SourcePoint) at ({1/sqrt(3)},{1/sqrt(3)},{1/sqrt(3)});

% Draw shaded circle
\shade[ball color = lightgray,
    opacity = 0.25
] (0,0,0) circle (1cm);

% draw arcs
\tdplotsetrotatedcoords{0}{0}{0};
\draw[dashed,
    tdplot_rotated_coords,
    gray
] (0,0,0) circle (1);

\tdplotsetrotatedcoords{90}{90}{90};
\draw[dashed,
    tdplot_rotated_coords,
    gray
] (1,0,0) arc (0:180:1);

\tdplotsetrotatedcoords{0}{90}{90};
\draw[dashed,
    tdplot_rotated_coords,
    gray
] (1,0,0) arc (0:180:1);

% Projection of the SourcePoint on X and y axes
\draw[thin, dashed] (SourcePoint) --++ (0,0,{-1/sqrt(3)});
\draw[thin, dashed] ({1/sqrt(3)},{1/sqrt(3)},0) --++
(0,{-1/sqrt(3)},0);
\draw[thin, dashed] ({1/sqrt(3)},{1/sqrt(3)},0) --++
({-1/sqrt(3)},0,0);

% Axes in 3 d coordinate system
\draw[-stealth] (0,0,0) -- (2,0,0)
    node[below left] {$\hat{x}$};

\draw[-stealth] (0,0,0) -- (0,1.5,0)
    node[below right] {$\hat{y}$};

\draw[-stealth] (0,0,0) -- (0,0,2)
    node[above] {$\hat{z}$};

\draw[dashed, gray] (0,0,0) -- (-1,0,0);
\draw[dashed, gray] (0,0,0) -- (0,-1,0);

% Line from the origin to (SpacePoint)
\draw[thick, -stealth] (0,0,0) -- (SpacePoint) node[midway, left] {$\vec{r}$};

% Line from the origin to (SpacePoint)
\node at (SpacePoint) [above, left]  {$z$};

% Line from the origin to (SourcePoint)
\node at (SourcePoint) [right]  {$dq$};

% Line from the origin to (SourcePoint)
\draw[thick, -stealth] (0,0,0) -- (SourcePoint) node[midway, below] {$\vec{r'}$};

% Line from the SourcePoint to (SpacePoint)
\draw[thick, -stealth] (SourcePoint) -- (SpacePoint) node[midway, right] {$\vec{r} - \vec{r'}$};

\end{tikzpicture}
```
