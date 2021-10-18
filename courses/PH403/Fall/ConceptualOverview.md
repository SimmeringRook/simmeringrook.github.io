Last Updated: 10/18/2021 12:50 PM

## Goals

Create a visualization toolset for increasing the accessibility and understandability for trajectories moving through spacetime. This toolset will be able to produce vector field plots for trajectories of objects moving throughout non-Euclidian space through solved geodesic equations of motion. Also, the toolset will be able to generate the corresponding differential scattering cross section for a particle with specified parameters of Energy and (Orbital) angular momentum.

Time permitting, the codebase will be refined to be modular and well documented, with a particular addition focus on extendibility. This framework is intended to be integrated into similar codebases, such as either the Stardisk or Chimera projects. The underlying latticework of grid points will be implemented without assumptions of the underlying properties for the geometry of spacetime to facilitate straightforward modular extension for more complicated spacetimes such as the Reissner-Nordström or Kerr geometries.

![Implementation Timeline](Combined_Gnatt.png)

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
