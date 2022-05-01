---
title: "Cartographer: Using Python to Animate Motion of Low-Mass Objects in Curved Spacetime"
subtitle: "Assignment 5, Conclusion Draft"
author:
  - Thomas Knudson
geometry:
 - a4paper
 - margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 403, HW 5}
    \fancyhead[CO,CE]{ }
    \usepackage{setspace}
---

\setlength{\parskip}{2em}

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