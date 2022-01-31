---
title: "Method Draft, Process Memo"
author:
  - Thomas Knudson `\\\\`{=latex} Department of Physics, OSU
geometry:
 - a4paper
 - margin=2cm
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{PH 403, HW 3}
    \fancyhead[CO,CE]{Knudson}
---

There's still some cosmetic things that I haven't changed from the fleshed out skeleton feedback (chapter/section numbers).

I think this section does a good job at explaining *how* I went about implementing things computationally, but I don't know if this should be a section or an appendix. I've been looking at a few different theses that have a similar structure, and while this is great for explaining what I did, I don't know if it is directly useful. I think last term I was approaching the thesis write up more from the point of view of documenting the project and a project summary than from a more.. experiment view?

Below is an example of some research that I've written, and stands as a possible alternative to having the explicit methods situation. Most of the time, I can't separate each thing from a physical situation, and so I might need to just do mini thought-experiments/problem statments (like below) to set up the math before the resulting visualization.

## Possible Alternative

To find out how a particlar shell in Schwarzschild measures speed, we can't just directly manipulate the line element to obtain a simple equation. Recall that for the case of a stone falling in from infinity, we can obtain two relations from $ds^2 = -\left(1-\frac{2M}{r}\right)dt^2 + \left(1-\frac{2M}{r}\right)^{-1}dr^2 + r^2 (d\theta^2 + \sin^2{\theta}d\phi^2)$:

$$\underbrace{\frac{dr_{bk}}{dt_{bk}}=-\left(1-\frac{2M}{r}\right)\sqrt{\frac{2M}{r}}}_{\text{bookkeeper}}, \quad \underbrace{\frac{dr_{shell}}{dt_{shell}}=-\sqrt{\frac{2M}{r_{shell}}}}_{\text{'all shells'}}$$

However, if we try to manipulate the line element to pick a specific shell for our reference frame (setting the meterstick and clock tickrate), the resulting expression leads to unphysical results -- namely the stone can surpass the speed of light if the observation shell is less than $r=6M$. Instead, we must construct a thought experiment:

> Consider a lightblub emitting a known wavelength of light, $\lambda_{emitted}$ (as measured in its rest frame). An observer, situated on a shell ($r_{measured}$), then measures the redshifted wavelength as $\lambda_{measured}$. If the information of which $r$-coordinate is transmitted alongside each $\lambda_{emitted}$, how fast is the lightblub moving towards the event horizon along a radial path?

Noting that the redshift has contributions from both gravity (curvature of spacetime) and the speed (relativistic Doppler effect), we can build an expression to describe this:

$$\lambda_{measured} = \sqrt{\frac{1-\frac{2M}{r_{measured}}}{1-\frac{2M}{r_{emitted}}}}\sqrt{\frac{c+v}{c-v}} \lambda_{emitted}$$

Solving for speed, we then obtain the function:

$$v(\lambda_{measured}, r_{measured}, \lambda_{emitted}, r_{emitted}) = c \frac{\left(\frac{\lambda_{measured}}{\lambda_{emitted}}\right)^2 \left(\frac{1-\frac{2M}{r_{emitted}}}{1-\frac{2M}{r_{measured}}}\right) - 1}{\left(\frac{\lambda_{measured}}{\lambda_{emitted}}\right)^2 \left(\frac{1-\frac{2M}{r_{emitted}}}{1-\frac{2M}{r_{measured}}}\right) + 1}$$