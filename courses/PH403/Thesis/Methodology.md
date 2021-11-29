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

# Methodology

## Design Principles

> TODO: Guidelines and idealize criteria to inform decision making during synthesis and refactoring.

- Easy to use (goal: one year of experience, e.g. PH 36X)
- Performant (to a degree?)
    - Home/Personal PC use for non-extreme examples
    - Cache calcuations where possible
    - Optimize function calls to allow compiler optimizations
- Extendability
    - Remove implicit assumptions from code
    - SOLID

> TODO: Ripped from Proposal: "Plan of Work", Refine Later

We will study the equations of motion for massive and massless particles in the presence of curved spacetime. A Schwarzschild black hole will serve as the source of curvature for analysis of limiting cases that will be used as the foundation for sense making and error checking in computational runtimes. The project itself has been subdivided into three major phases: Scaffolding, Curving, and Refinement.
The core of the toolset depends on a series of key design and implementation decisions about the underlying framework. One of the key features is to have an intuitive code base for physicists to use, which implies a latticework of grid points mapping out the space. Ideally, this latticework will be agnostic with respect to the active geometry and type of curvature. This stage will focus on the creation of the latticework, its documentation and the manifestation of key mathematical tools such as differential scattering and the representation and parameterization of a geodesic. Examples of this design process are shown on the following page with Figure 1 and Figure 2.

> TODO: Replace if final implementation is no longer OOP.

\begin{figure}
    \caption{Latticework design implementation document detailing desired behaviour and properties. }
\end{figure}

\begin{figure}
    \caption{SpacetimeGeometry design implementation document outlining the use of object-oriented class inheritance to allow modularity for future different descriptions of curvature in spacetime and to ensure the framework does not implicitly assume any behaviour of the geometry: “Spacetime agnostic”. }
\end{figure}

The differential scattering cross-section has a general form that can be parameterized based off the impact parameter, $\sigma\left(b\right)=\int{\frac{d\sigma\left(b\right)}{d\Omega}\left(\theta,\ \phi\right)d\Omega}$ [5], but we will need to still solve the EOM, Equation 4, and mesh the two together. Care will need to be taken to avoid any implicit assumptions about the object traversing the spacetime to avoid unphysical geodesics and cross-sections: e.g., the impact parameter has a different form for massive versus massless particles [1,3]. Below, in Figure 3, the general user story has been mapped out to provide insight into the conceptual process of the toolset.

> TODO: Replace with final version's flow system. Maybe keep original for comparision

\begin{figure}
    \caption{Flow chart detailing the typical user story for interacting with the toolset. }
\end{figure}

## The Core Design Process

> TODO: This is the design process of Cartographer

1. Find Equation
2. Represent Equation in Python
3. Plot
4. Compare results and implement changes as necessary for correct representation
5. Refactor

