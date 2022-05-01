---
title: "Cartographer: Using Python to Animate Motion of Low-Mass Objects in Curved Spacetime"
subtitle: "Assignment 4, Abstract Draft"
author:
  - Thomas Knudson
geometry:
 - a4paper
 - margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 403, HW 4}
    \fancyhead[CO,CE]{ }
    \usepackage{setspace}
---

\doublespacing

\setlength{\parskip}{2em}

\setlength{\parindent}{4em}

The computational framework, Cartographer, created and examined in this study focused on two key aspects: (1) visualizing exact and simulated motion in general relativity and (2) creating a framework that can be easily extended to describe more complex geometries of general relativity. Even the simplest geometric model of general relativity, the Schwarzschild geometry, requires a mathematical representation that is very complex for most undergraduate physics students. The main method for developing intuition of a object's geodesic (path) is either through examining the equation in detail and reasoning about the described behaviour (radius of orbit, is there an orbit, eccentricity, etc) or by cross comparing various 2-D graphs of coordinates/attributes. The latter involves reasoning through energy versus r-coordinate plots combined with spacetime diagrams showing time vs r-coordinate, time vs phi, or even phi versus r-coordinate.

The spacetime geometry is discretized into a lattice of nodes. The theoretical geodesics are represented in the three (4?) dimensional plots through numeric integration using the Verlet velocity method. The computational framework then finds the path the object should take, based off initial conditions, by extending the lattice into a weighted graph. The framework then uses the $A^*$ pathfinding algorithm to find the next step the object will take by calculating the action for each possible neighboring node.

The accuracy of the simulate path is directly related to the resolution of the discreteness of the underlying spacetime but has a minimum error threshold proportional to the theoretical path. While it is impossible to remove all error from both the theory and simulated paths, this error can be minimized to a requested precision, allowing for quicker run times and reducing hardware requirements for the computational framework. This framework offers an interface for undergraduate students to approach motion in general relativity in an easier method, requiring only the basic familiarity with python taught in the PH 36X courses. These visualizations also surpass the equivalent representations provided in various texts by allowing a third dimension to be represented: 2-dimensions of space and 1-dimension of time via rotatable animations.

\pagebreak

### What?

I am creating visualizations to achieve two goals:

1. better visualize motion in the Schwarzschild geometry of general relativity
2. simulate this motion in a way that can be easily expanded for more complex (accurate) geometries of general relativity

### Why?

The mathematical language of general relativity is very complex in comparision to what most undergraduate physics students are familiar with. The main method for developing intuition of a object's geodesic is either through examining the equation in detail and reasoning about the described behaviour (radius of orbit, is there an orbit, eccentricity, etc) or by cross comparing various 2-D graphs of coordinates/attributes. The latter involves reasoning through energy versus r-coordinate plots combined with spacetime diagrams showing time vs r-coordinate, time vs phi, or even phi versus r-coordinate.

### How?

The spacetime geometry is discretized into a lattice of nodes. The theoretical geodesics are represented in the three (4?) dimensional plots through numeric integration using the Verlet velocity method. The computational framework then finds the path the object should take, based off initial conditions, by extending the lattice into a weighted graph. The framework then uses the $A^*$ pathfinding algorithm to find the next step the object will take by calculating the action for each possible neighboring node.

### Result?

The accuracy of the simulate path is directly related to the resolution of the discreteness of the underlying spacetime but has a minimum error threshold proportional to the theoretical path. While it is impossible to remove all error from both the theory and simulated paths, this error can be minimized to a requested precision, allowing for quicker run times and reducing hardware requirements for the computational framework.

### Implication?

This framework offers an interface for undergraduate students to approach motion in general relativity in an easier method, requiring only the basic familiarity with python taught in the PH 36X courses. These visualizations also surpass the equivalent representations provided in various texts by allowing a third dimension to be represented: 2 dimensions of space and 1 dimension of time (via animation).
