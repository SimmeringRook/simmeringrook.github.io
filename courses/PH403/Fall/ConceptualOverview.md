Last Updated: 10/16/2021 11:10 AM

# Key Concepts:

- Create visualizations for:
  - differential scattering cross-sections for particles
  - vector field representation of particle trajectories
  - view of process with different coordinates:
    - geometric
    - local
    - shell
- Use time as additional dimension for visualizations ?

<!-- tabs:start -->

<!-- tab:Computational -->

## Computational

Lattice $\rightarrow$ Node

  - [`Latticework`](/courses/PH401/Computational/Latticework.md)
    - 3-D (4D?) representation of [spacetime](/courses/PH401/Physics/Spacetime.md)
    - 2D (3D?) collection of `Nodes`
    - [`SpacetimeGeometry`](/courses/PH401/Computational/SpacetimeGeometry.md)
  - [`Node`](/courses/PH401/Computational/Node.md)
    - coordinate location in `Latticework`
      - x,y,z,t
    - Nearest Neighbors:
      - geometric,
      - local,
      - shell

- Helper Math functions:
  - Differential Scattering Cross-Section
  - [Metric](/courses/PH401/Physics/Metric.md)
    - Euclidean
    - Minkowski
    - Schwarzschild
  - Geodesic Equations of Motion
    - Null
    - Particle
  - Convert Coordinate Systems
    - x,y,z
    - r,phi,theta
    - s,phi,z
  - Vectors
  - Euler's Method?

- Helper Control Functions:
  - Read In data set?
    - Allow for configuration to be set by files and not require terminal input?
  - Output data set?
    - CSV?
    - save plots with file names based off parameters?

- Visualization:
  - Internal Plots
    - Vector Field of trajectories
    - Differential Scattering Cross-section heat map
  - Animations?

<!-- tab:Physics -->

## Physics

- General Relativity
  - Measurements
    - time and space
    - Proper Time
    - Proper Distance
  - Curved Spacetime
    - Coordinate Systems
      - geometric vs physical
      - physical latticework is effected by length contraction and time dilation
      - geometric is unaffected
  - Geodesic
    - path traveled by free fall object
    - Null
      - only light
    - Killing Vectors
      - representation/manifestation of conserved quantities in the geometry
    - Geodesic Equations
      - Equations of Motion

- Differential Scattering Cross-section
  - method for discussing how much an object is deflected from original trajectory
  - Rutherford's alpha particles and gold foil for determining the nucleus of an atom

<!-- tabs:end -->
