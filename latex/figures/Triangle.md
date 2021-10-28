\begin{figure}
    \centering
    \begin{tikzpicture}

    % create coordinates
    \coordinate (O) at (0,0);
    \coordinate (A) at (0,1.25);
    \coordinate (P) at (4,0);

    % Create the cylinder on it's side
    % Start with the top
    \draw (0,0) ellipse (0.5 and 1.25);

    % Now we'll add in the sides, and sweep across the bottom
    \draw (0,1.25) -- (-0.5,1.25) node [above] {$dz$};
    \draw (-0.5,-1.25) -- (0,-1.25);

    % If you want a full cylinder, replace this with another ellipse
    \draw (-0.5,1.25) arc (90:270: 0.5 and 1.25);
    % Or for a more fancy illustration, we can do a dashed arc for the side we can't see
    %\draw[dashed] (-0.5,-1.25) arc (-90:90: 0.5 and 1.25);

    % Label the radius
    \draw[dashed] (0,0) -- (0,1.25) node [midway, right] {$a$};

    % Draw z axis and label
    \draw[-stealth, gray] (0,0) --++ (5,0);
    \node at (5,0) [below] {$+\hat{z}$};

    % Label the point
    \node at (P) [below] {$P$};

    % Construct triangle
    \draw[dashed] (0,1.25) -- (4,0) node[midway, above] {$\vec{\mathfrak{r}}$};
    \draw (0,0) -- (4,0) node[midway, below] {$z$};
    \tkzFillAngle[fill=orange, opacity=0.4](A,P,O);
    \tkzLabelAngle[pos=1.2](A,P,O){$\theta$};

    \end{tikzpicture}
    \caption{A visual representation of the angle, $\theta$, from the edge of the solenoid (approximated as ring of current $\vec{I}=I\hat{\phi}$ with thickness $dz$) to the point $P$ located on the axis of symmetry.}
\end{figure}