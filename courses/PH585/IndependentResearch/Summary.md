!> **Author's Note:** Links which redirect to Wikipedia are placeholders for pages that have not yet been created on this site (to avoid dead links and to visually denote *required future work*).

# Review of 'Observables of spheroidal magnetized Strange Stars'

Article title: *Observables of spheroidal magnetized Strange Stars* ([arXiv](https://arxiv.org/abs/2010.06514v1))

> Why did I choose this article?

I choose this article because I am doing my undergrad Physics research in the context of General Relativity and wanted to try to find a paper that touches on content relevant to AMO and Astrophysics/General Relativity. Luckily, this paper was at the top of my search results and the title and abstract just immediately sold me on the concept of reading and trying to share this content with other people.

Neutron Stars are as fascinating, if not more so, than black holes in that they mix together high densities, degeneracy pressures battling massive gravitational forces, and the interaction between those forces in a *compact* scale.

> Notes taken while reading the article can be located [here](/courses/PH585/IndependentResearch/Notes.md).

## Summary

The main focus of this paper is on the area of expanding our description and understanding of Neutron stars (NSs) and their cores. Neutron stars are primarily composed of their namesake: neutrons. Not only is a star comprised mainly of subatomic particles interesting, but this extreme system requires the combination of some intense$^{1}$ fields of Physics :

- **General Relativity**: because while extremely small and compact, the star has enough mass to curve spacetime.
- **Statistical Mechanics**: [degenerate neutron matter](https://en.wikipedia.org/wiki/Degenerate_matter#Neutron_degeneracy) and [strange quark matter](https://en.wikipedia.org/wiki/QCD_matter) can't be reasonably described by Classical Thermodynamics (in comparison to Main Sequence stars).
- **Quantum Mechanics** (and Quantum Chromodynamics): to model and begin to describe the energy of a system comprised of [quarks](https://en.wikipedia.org/wiki/Quark) (elementary particles that make up the three subatomic particles: electrons, protons, and neutrons).

> $^{1}$ By *intense*, I refer to need for something beyond Classical Mechanics. Normally, we can still approximate other features of a system with Newtonian Mechanics, but in this case, we need to replace each major portion of a Classical description for the problem with its corresponding modern counterpart.  

### Background

Astrophysicists have a good understanding of the overview for the life of a star. Areas of interest and uncertainty currently focus on the formation of a star and their exotic end stages. The main stages of [stellar evolution](https://en.wikipedia.org/wiki/Stellar_evolution) are divided (loosely) into the following sections:

1. Early
    - This covers the time period from the condensing of gas, most likely from a [nebulae](https://en.wikipedia.org/wiki/Molecular_cloud), into the formation of a [protostar](https://en.wikipedia.org/wiki/Protostar) and ultimately into a [Main Sequence Star](https://en.wikipedia.org/wiki/Main_sequence). The central discriminating feature of Main sequence stars are that they are primarily using Hydrogen to fuel the [nuclear fusion](https://en.wikipedia.org/wiki/Nuclear_fusion#Nuclear_fusion_in_stars) occurring in the core. The Sun is still well within the hydrogen stage and is our local main sequence star.
2. Post-Main Sequence
    - As the hydrogen fuel begins to run out, this is the period where the mass (size) of the star starts to dramatically differentiate its life from the paths of others. As the hydrogen core is exhausted, these stars expand as the hydrogen above the now helium core feeds the fusion and the star transitions into a [Red giant](https://en.wikipedia.org/wiki/Red_giant).
3. Late
    - There are a few branching paths that more massive stars can take as they either switch to different fuel sources for fusion. Stars that are not primarily convective can experience periods of instability as easier to fuse material is cycled internally causing the star to flare and flash, [ejecting some of its stellar material](https://en.wikipedia.org/wiki/Stellar_mass_loss) (one form of creating a nebula).
    - Other stars that live through this process ultimately run into the problem where silicon is fused into iron (called the ["Iron peak"](https://en.wikipedia.org/wiki/Iron_peak)). Iron is a big problem for stars as the process requires energy, instead of producing energy. As the iron core grows, the star will eventually collapse producing a [supernova](https://en.wikipedia.org/wiki/Supernova). The explosion ejects the outer layers of the star and reveals the remnant of the core which is either a form of [Neutron star](https://en.wikipedia.org/wiki/Neutron_star) or a [Black Hole](https://en.wikipedia.org/wiki/Black_hole).

The following figure offers a qualitative guide to the aforementioned stages of a star's life (before stellar collapse) through the use of a Hertzsprung–Russell diagram ([HR diagram](https://en.wikipedia.org/wiki/Hertzsprung%E2%80%93Russell_diagram)):

?> ![By User:Rursus - Self made diagram, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=2047079](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7a/HR-diag-w-text.svg/1024px-HR-diag-w-text.svg.png "By User:Rursus - Self made diagram, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=2047079") <br /> Image courtesy of Wikipedia user: *Rursus*. [Source](https://commons.wikimedia.org/w/index.php?curid=2047079).

?> This second figure, from Page 337 of Charles Keeton's *Principles of Astrophysics: Using Gravity and Stellar Physics to Explore the Cosmos*, demonstrates the quantitative uses of an HR diagram to visualize the corresponding Luminosity and Temperature as a function of mass (and as a prediction for the path of stellar evolution for a given star). <br /> ![This is a HR (Hertzsprung–Russell) diagram which is used to visualize the corresponding Luminosity and Temperature as a function of mass (and as a prediction for the path of stellar evolution for a given star). Keeton, Page 337](HRDiagram.png "This is a HR (Hertzsprung–Russell) diagram which is used to visualize the corresponding Luminosity and Temperature as a function of mass (and as a prediction for the path of stellar evolution for a given star). Keeton, Page 337")

<br />

### Why do we care about 'Strange Stars'?

Strange Stars are a sub-classification on Neutron Stars. Under the extreme pressures and intensities that exist inside Neutron Stars, we suppose that the core consists not of subatomic particles, but Strange Matter (SM or SQM for 'Strange Quark Matter'): quarks that come from the decomposed [hadronic](https://en.wikipedia.org/wiki/Hadron) matter (neutrons). The study of quarks are of great interest in our path to understanding the minute building blocks that combine in masses to create the grand structures of life and the properties of our Universe.

The study of Neutron Stars has renewed with increased interest over the past decade, as another sub-classification has promisingly offered an alternative (and concurrent) method of visualizing and recording Gravitational Waves: Pulsars. A prime example of this research can be seen by [NANOGrav's](http://nanograv.org/) work with the [Pulsar Timing Array](http://www.ipta4gw.org/), which has a local presence at Oregon State University through the work done by Dr. Xavier Siemens.

<br />

### What's so interesting about this paper?

The authors of this paper make tremendous effort forward in deriving Equations of State (EoS) for these Strange Stars (SSs). What is notable about this physical system is that there are no solutions that provide the EoS for these SSs: either using exact calculations or perturbation theory in [Quantum Chromodynamics](https://en.wikipedia.org/wiki/Quantum_chromodynamics).

Previous attempts to derive equations of state for magnetized Strange Stars arrive at two independent pressure equations. The independence of these equations prevent a coherent description of the macroscopic star and are highly dependent on the model. This attempt uses the same concept as a launching point but derives a variation of the [Tolman-Oppenhimer-Volkoff](https://en.wikipedia.org/wiki/Tolman%E2%80%93Oppenheimer%E2%80%93Volkoff_equation) (TOV) equations by starting with an axially symmetric metric in spherical coordinates. From this, the Equations of State and Structure equations combine coherently to more accurately describe observed properties of highly magnetized Neutron stars.

The results of this can be seen in the figure below, as the authors plot possible (highly magnetized) Strange star candidates versus the allowed theoretical models. While the results are promising, they are not a complete description of the systems in question: the structure equations and equations of state are still very model dependent and the confining energy for the quark matter is still described as an external parameter (versus a property of the system).

?> ![Figure 7, Page 14, Terrero et al. (2010)](Figure7.png "This is Figure 7, Page 14 of Terrero et al. (2010)") <br /> Figure 7, Page 14, Terrero et al. (2010).

<br />

---

# The Physics of this Paper

There are three major topics of Physics present in this paper (excluding Astrophysics):

1. Thermodynamics (and Statistical Mechanics)
    - (Stable) Stars need to be in stellar equilibrium: if they are not, they will evolve to reach what will be the new equilibrium.
    - Equations of State let us discuss how changes of properties change the rest of the system
    - We need Statistical Mechanics to describe the Microscopic contributions to the two separate pressure differentials.
2. Quantum Mechanics
    - We describe (and limit) the energy of the quarks by using a model similar to *particle in a box*
    - [MIT-Bag Model](http://hyperphysics.phy-astr.gsu.edu/hbase/Particles/qbag.html)
    - quasi-free particles but with binding energy
3. General Relativity
    - Need a metric that describes the physical situation more than the idealization
      - accounts for deformation and separate pressure gradients
    - Axial symmetry, not spherical

What follows below is only a survey of the concepts and models involved in this paper and not an exhaustive derivation or explanation.

<br />

## Thermodynamics: Equations of State

The setup for this physical model for pressure and energy densities assumes:

- a uniform and constant magnetic field oriented in the z direction,
- that quarks can be treated as quasi-free particles confined to a "bag" by a binding energy $B_{Bag}$,
- the star must be in stellar equilibrium
  - charge neutrality
    - $\sum_{f}{e_f N_f} = 0$
  - baryon number conservation
    - $\sum_{i=u,d,s}{N_i} = 3N_B$
  - chemical potentials
    - $\mu_u +\mu_e - \mu_d = 0$, $\mu_d - \mu_s = 0$
  - $\beta$ equilibrium

With these constraints, we obtain the following Equations of State (EoS) for the magnetized Strange Star (SSs):

$$\begin{aligned}
E &= \sum_{f}{[\Omega_f+\mu_fN_f]} + B_{bag} + \frac{B^2}{8\pi} \\
P_\parallel &= - \sum_{f}{\Omega_f} - B_{bag} - \frac{B^2}{8\pi} \\
P_\perp &= -\sum_{f}{[\Omega_f+ B\mathcal{M}_f]} + B_{bag} + \frac{B^2}{8\pi}
\end{aligned}$$

- $\mathcal{M}_f = -\partial\Omega_f/\partial B$ is the magnetization

Notably, there are only three main contributions to the EoSs:

1. the thermodynamic quantities for each species (of quark)
2. the binding energy ($\pm B_{bag}$)
3. the magnetic field pressures and energy density

<br />

### Thermodynamic Potential

The thermodynamic potential is then given in its most general form as

$$\Omega_f (B, \mu_f, T) = - e_f d_f BT \int_{-\infty}^{\infty}{\frac{dp_3}{4\pi^2} \sum_{\ell=0}^{\infty}{\left(g_{\ell} \times \sum_{p_4}{\ln{\bigg[(p_4+i\mu_f)^2+{\mathcal{E}_{\ell f}}^2\bigg]}}\right)}}$$

- $\ell$ denotes the Landau levels
- $f$ denotes a different type of particle (for relevant properties and variables)
    - $e$ for electrons
    - $u$, $d$, $s$ for quark flavor
      - $u\mapsto$ up
      - $d\mapsto$ down
      - $s\mapsto$ strange
    - $\mu_f$ denotes chemical potential
    - $m_f$ denotes mass
    - $e_f$ denotes the charge
- $d_f$ denotes flavour degeneracy factor
  - $d_e=1$
  - $d_{u,d,s}=3$
- $g_\ell$ denotes spin degeneracy of fermions for $\ell \neq 0$
  - $g_\ell = 2-\delta_{\ell 0}$
- $T$ is the absolute temperature
- $\mathcal{E}_{\ell f}$ denotes the spectrum of charged fermions coupled to a magnetic field
  - $\mathcal{E}_{\ell f} = \sqrt{p_3^2+2\vert e_f B\vert\ell + m_f^2}$

This potential can be divided into two contributions: Vacuum, $\Omega_f^{vac}(B, 0, 0)$, and Statistical, $\Omega_f^{st}(B,\mu_f, T)$. The vacuum contribution notably does not depend on temperature or the chemical potential, but must be renormalized to avoid an ultraviolet divergence; however, due to the density of fermions being so high, $\Omega_f^{vac}(B, 0, 0)\ll\Omega_f^{st}(B,\mu_f, T)$ and we can approximate the thermodynamic potential as the degenerate fermion system. The [degenerate limit](https://physics.stackexchange.com/a/242796), $T\rightarrow 0$, can be taken of the Statistical contribution as the temperature of the Neutron Star is much less than the Fermi Temperature of the composing gas. With these simplifications, the thermodynamic potential becomes:

$$\begin{aligned}
\Omega_f &\approx \Omega_f^{st} (B, \mu_f, 0) = - \frac{e_f d_f B}{4\pi^2} \sum_{\ell=0}^{\ell_{max}}{g_\ell \bigg[\mu_f {p^\ell}_f - ({\mathcal{E}^\ell}_f)^2 \ln{\left(\frac{\mu_f + {p^\ell}_f}{{\mathcal{E}^\ell}_f}\right)}} \bigg]
\end{aligned}$$

- ${p^\ell}_f$ is the Fermi momentum (of the particles)
  - ${p^\ell}_f = \sqrt{\mu_f^2 - ({\mathcal{E}^\ell}_f)^2}$
- ${\mathcal{E}^\ell}_f$ is (their) the ground state energy
  - ${\mathcal{E}^\ell}_f = \sqrt{m_f^2+2qB\ell}$
- $\ell_{max}$ is the maximum number of occupied Landau levels for fixed magnetic field and chemical potentials
  - $I[z]$ denotes the integer part of $z$
  - $\ell_{max} = I \left[ \frac{\mu_f^2 - m_f^2}{2e_f B} \right]$

<br />

## Quantum Mechanics: Binding Energy

As the Neutron star is a bound system, we want the total energy of the star to be negative. This means that the confining energy, $B_{bag}$, must be greater than the magnetic field, as we can see from the first Equation of state (described above)

$$E = \sum_{f}{[\Omega_f+\mu_fN_f]} + B_{bag} + \frac{B^2}{8\pi}$$

The researchers discuss limiting the magnitude of the magnetic field, $\vec{B}$, through ensuring the Strange Star is stable. This stability (and derivation of the limiting value) is discussed in further detail on page 12 of the paper (Section 3, Subsection A), as it requires the use of the structure equations derived from the axially symmetric metric.

?> The following figure, Figure 1 from Page 7 of Terrero et al. (2010), shows how the required confinement energy from the Bag must scale with the magnetic field's strength to ensure a stable star. The corresponding plot on the right then illustrates how the perpendicular pressure increases and causes the star to deform more (as $P_\perp > P_\parallel$) <br /> ![Figure 1, Page 7, Terrero et al. (2010)](Figure1.png "This is Figure 1 from Page 7 of Terrero et al. (2010)")

In short, we can use these relations to constrain the upper limit for the strength of a magnetic field inside a Strange Star that allows it to deform, but remain stable as resist tearing itself apart from rotations about its axis of symmetry (as angular momentum is conserved from the progenitor star).

<br />

### MIT-Bag Model ("Quark in a Bag")

The description for the energy of the quarks in the core of the star is done with Quantum Chromodynamics using what is intermittently referred to as the "MIT-Bag Model". In brief, this model is an extension of the *Infinite Square Well* (or "Particle in a box") quantum system from undergraduate QM courses. The main difference is that the particle is located inside a (generally spherical) cavity, with the cavity located inside the potential well.

The particle is allowed to asymptotically move through out the cavity, but with increasing potential as the distance between quarks increases. A more complete description can be found in graduate (or advanced undergraduate) texts such as *Quantum Mechanics* by K.T. Hecht or on websites such as [HyperPhysics](http://hyperphysics.phy-astr.gsu.edu/hbase/Particles/qbag.html).

<br />

## General Relativity: TOV-like equations and Axially Symmetric Metric

The structure equations for a star are typically derived by modeling the star as a spherically symmetric body in static gravitational equilibrium. The result is the [Tolman-Oppenheimer-Volkoff (TOV)](https://en.wikipedia.org/wiki/Tolman%E2%80%93Oppenheimer%E2%80%93Volkoff_equation) equation.

The problem, as Terrero et al. (2010) discuss in the paper, is that the models strictly disagree with each other: The equations of state describe a non-spherically symmetric system (different pressure gradients), while TOV requires that extra level of symmetry. To resolve this, the researchers derive a metric that finds a middle ground between absolute spherical symmetry and just axial symmetry. Their resulting metric takes the following form$^2$:

$$ds^2 = - \left( 1 - \frac{2M(r)}{r} \right)^{\gamma} dt^2 + \left( 1 - \frac{2M(r)}{r} \right)^{-\gamma} dr^2 + r^2\sin{\theta}d\phi^2 + r^2 d\theta^2$$

> $^2$ This is given as Equation 11 on Page 8 of the paper, where $\gamma$ is the ratio of polar radius $z$ to equatorial radius $r$: $\gamma \equiv z/r$. I also note that there appears to be a typo: If we take the limiting case where $z=r$ and we should regain the [Schwarzschild metric](https://en.wikipedia.org/wiki/Schwarzschild_metric), which leads me to assume that $\sin{\theta}$ really should be $\sin^2{\theta}$.

Using this metric to describe [curvature](https://en.wikipedia.org/wiki/Curvature) and the [stress-energy tensor](https://en.wikipedia.org/wiki/Stress%E2%80%93energy_tensor) for the magnetized star, Einstein's equations can be solved to find the following structure equations:

$$\begin{aligned}
\frac{dM}{dr} &= 4\pi r^2 \frac{E_\parallel + E_\perp}{2}\gamma\\
\frac{dP_\parallel}{dz} &= - \frac{(E_\parallel + P_\parallel) \left(\frac{r}{2} + 4\pi r^3 P_\parallel - \frac{r}{2}\left( 1 - \frac{2M(r)}{r} \right)^{\gamma}\right) }{r^2 \left( 1 - \frac{2M(r)}{r} \right)^{\gamma}}\\
\frac{dP_\perp}{dr} &= - \frac{(E_\perp + P_\perp) \left(\frac{r}{2} + 4\pi r^3 P_\perp - \frac{r}{2}\left( 1 - \frac{2M(r)}{r} \right)^{\gamma}\right) }{r^2 \left( 1 - \frac{2M(r)}{r} \right)^{\gamma}}
\end{aligned}$$

$\gamma$ is constrained to be $1>\gamma>0.8$ for the structure equations to still be valid. This constraint then reveals the upper limit for the magnetic field to be approximately $10^{18} G$, as shown in the comparison plot below of $\gamma$ vs energy density:

?> ![Figure 4, Page 11, Terrero et al. (2010)](Figure4.png "This is Figure 4 from Page 11 of Terrero et al. (2010)") <br /> Note that both ( $B_{bag} = 65 Mev/fm^3$ and $B_{bag}=75 Mev/fm^3$) families of solutions (with a magnetic field of $B\simeq10^{18} G$) fail to even reach valid values of $\gamma$ before reaching the upper limit of energy density for the system of $930 Mev/fm^3$.

The researchers also point out that having invalid solutions for $B\simeq10^{18}$ is consistent with results of other models and the limit established from the [Virial theorem](https://en.wikipedia.org/wiki/Virial_theorem).
