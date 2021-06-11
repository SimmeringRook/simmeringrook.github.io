## Abstract

Strange Stars

  - Strange Quark Matter
    - MIT-Bag model
  - Properties:
    - mass
      - mass quadrupole moment
    - radius
    - eccentricity
      - orbit?
    - redshift


Axially symmetric metric

  - spherical coordinates

Equation of State

  - Anisotropy (gamma parameter)
    - links deformation of star to magnetic field

TOV?

Spheroidal model

  - observables depend directly on deformation
  - deviate from corresponding spherical configurations
    - mass quadrupole moment might allow discrimination between models


## Intro

Neutron Stars (NSs)

- core:
  - "densities beyond that of nuclear saturation"
- hadronic to Strange Quark Matter (SQM)
  - hadronic -> hydrogenic?
    - https://en.wikipedia.org/wiki/Hadron
  - SQM is the true ground state of strong-interacting matter
    - Bodmer-Witten's conjecture
- subclasses
  - differentiated by how strong interaction and phases of SQM
  1. Strange Stars (SSs)
      - SQM
      - describe compact objects with maximum mass 1.5 Solar Mass
      - 4-8km radius
      - could account from observations of cold, dense, and small Compact Objects (COs)
  2. Hybrid Stars (HSs)
      - core of SQM, layer of hadrons
      - mass can reach 2 Solar Masses
        - 2 Solar Mass is a constraint on NS mass
      - recent theoretical and experimental support for models
        - Eemeli Annala et al. (13)
        - combines Equations of State from particle and nuclear physics and results from Gravitational Wave measurements of NSs collisions
        - a star with ~2 Solar Mass and radius of ~ 12 km is *more likely* to have a quark core of approximately 6.5 km *than to be* formed exclusively by baryons

SQM

- Quark-gluon plasma
  - high temperature, low density
  - Relativistic Heavy Ion Collider (RHIC) at Brookhaven National Laboratory (BNL)
  - Large Hadron Collider (LHC) at CERN
- opposite regime
  - low temperature, high densities
    - Facility for Antiproton and Ion Research (FAIR) at GSI
    - Nuclotron-based Ion Collider Facility (NICA) at JINR
  - NS cores might be the natural habitat for SQM in this regime
    - properties could be inferred through astronomical observations
- Equation of State (EoS)
  - quarks might be unpaired or paired
    - color superconductor state
  - No *ab initio* or perturbative Quantum Chromodynamic (QCD) calculations for the desired EoS in the regime of high densities and zero temperature.
  - SQM inside of COs is usually described through models that mimic main features of QCD
    - MIT-Bag model
      - quarks are considered as quasi-free particles confined into a "bag" with fixed masses.
      - reproduces confinement and asymptotic freedom using one external parameter, the bag energy $B_{Bag}$

COs

- extreme magnetic fields
  - observed surface fields are in the range of $10^9 - 10^{15}\ G$
    - internal fields estimated to be $5\times 10^{18}\ G$
  - energy momentum tensor of matter is **anisotropic**
    - gas exerting different pressures (parallel and perpendicular with respect to magnetic axis)
    - leads to non-spherical stars

Previous Models

- use TOV equations for each pressure (parallel vs perpendicular)
  - Tolman-Oppenhimer-Volkoff (TOV)
- approximate solution to Einstein's equations for an axially symmetric metric in cylindrical coordinates
- two different stellar sequences
  - one for each pressure
  - prevents a calculation of the total mass of the star

This Model

- derived TOV-like structure equations ($\gamma$ equations)
  - axially symmetric metric
  - spherical coordinates
- describe spheroidal objects
  - as long as shape is "nearly spherical"
- used on
  - White Dwarfs
  - (hypothetical) magnetized BEC (Bose-Einstein Condensate) stars
  - Strange Stars (SSs)

This Paper

- analyze stability of magnetized SQM
  - dependence on
    - density
    - bag energy
    - magnetic field
- uses new model to calculate and compare to observed data
  - mass
  - eccentricity
  - redshift
- revisit magnetized EoS for SSs
  - magnetic field effects on energy density and pressures

## Equation of State

Physical Situation

- Uniform and constant magnetic field oriented in the z direction
- quarks are assumed as quasi-free particles
  - confined to a "bag"
  - binding energy $B_{Bag}$

$$\Omega_f (B, \mu_f, T) = - e_f d_f BT \int_{-\infty}^{\infty}{\frac{dp_3}{4\pi^2} \sum_{\ell=0}^{\infty}{\left(g_{\ell} \times \sum_{p_4}{\ln{\bigg[(p_4+i\mu_f)^2+{\mathcal{E}_{\ell f}}^2\bigg]}}\right)}}$$

- Pressure and Energy density
  - Thermodynamic potential
  - $\ell$ denotes the Landau levels
  - particle properties and variables
    - $f$
      - $e$ for electrons
      - $u$, $d$, $s$ for quark flavor
        - $u\mapsto$ up
        - $d\mapsto$ down
        - $s\mapsto$ strange
    - $d_f$ denotes flavour degeneracy factor
      - $d_e=1$
      - $d_{u,d,s}=3$
    - $g_\ell$ denotes spin degeneracy of fermions for $\ell \neq 0$
      - $g_\ell = 2-\delta_{\ell 0}$
    - $\mu_f$ denotes chemical potential
    - $m_f$ denotes mass
    - $e_f$ denotes the charge
  - $T$ is the absolute temperature
  - $\mathcal{E}_{\ell f}$ denotes the spectrum of charged fermions coupled to a magnetic field
    - $\mathcal{E}_{\ell f} = \sqrt{p_3^2+2\vert e_f B\vert\ell + m_f^2}$

Spilt the Thermodynamic potential into two contributions:
$$\begin{aligned}\Omega_f (B, \mu_f, T) &= \Omega_f^{vac}(B, 0, 0) + \Omega_f^{st}(B,\mu_f, T) \\
&\Omega_f^{vac}(B, 0, 0) \equiv -\frac{e_f d_f B}{2\pi^2}\int_{0}^{\infty}{dp_3 \sum_{\ell=0}^{\infty}{g_\ell\mathcal{E}_{\ell f}}} \\
&\Omega_f^{st}(B, \mu_f, T) \equiv -\frac{e_f d_f BT}{2\pi^2}\int_{0}^{\infty}{dp_3 \sum_{\ell=0}^{\infty}{g_\ell\ln{\big[1+e^{-\beta(\mathcal{E}_{\ell f}\pm\mu_f)}\big]}}}
\end{aligned}$$

- Vacuum contribution does not depend on chemical potential or $T$
  - must be renormalized
    - avoid ultraviolet divergence
  - $\Omega_f^{vac}(B, 0, 0) = \frac{d_f m_f^4}{24\pi^2} \left(\frac{B}{B^c_f}\right)^2 \ln{\frac{B}{B^c_f}}$
    - $B^c_f = m_f^2/e_f$, critical magnetic field
      - cyclotron energy of particles is comparable to their rest mass
      - Schwinger field
      - $B^c_e \backsim 10^{13}\ G$
      - $B^c_u \backsim 10^{15}\ G$
      - $B^c_d \backsim 10^{16}\ G$
      - $B^c_s \backsim 10^{19}\ G$

- Statistical contribution
  - COs have temperatures much less than the Fermi temperature of gases that compose them
    - https://physics.stackexchange.com/questions/216207/what-is-the-significance-of-fermi-temperature
  - compute Thermodynamic potential in the degenerate limit $(T\rightarrow 0)$
    - $\Omega_f^{st} (B, \mu_f, 0) = - \frac{e_f d_f B}{2\pi^2} \int_{0}^{\infty}{dp_3 \sum_{\ell=0}^{\infty}{g_\ell \Theta(\mu_f - \mathcal{E}_{\ell f})}}$
      - $\Theta(\zeta)$ is the unit step function
    - $\Omega_f^{st} (B, \mu_f, 0) = - \frac{e_f d_f B}{4\pi^2} \sum_{\ell=0}^{\ell_{max}}{g_\ell \bigg[\mu_f {p^\ell}_f - ({\mathcal{E}^\ell}_f)^2 \ln{\left(\frac{\mu_f + {p^\ell}_f}{{\mathcal{E}^\ell}_f}\right)}} \bigg]$
      - ${p^\ell}_f$ is the Fermi momentum (of the particles)
        - ${p^\ell}_f = \sqrt{\mu_f^2 - ({\mathcal{E}^\ell}_f)^2}$
      - ${\mathcal{E}^\ell}_f$ is (their) the ground state energy
        - ${\mathcal{E}^\ell}_f = \sqrt{m_f^2+2qB\ell}$
      - $\ell_{max}$ is the maximum number of occupied Landau levels for fixed magnetic field and chemical potentials
        - $I[z]$ denotes the integer part of $z$
        - $\ell_{max} = I \left[ \frac{\mu_f^2 - m_f^2}{2e_f B} \right]$

- high fermionic densities $\Rightarrow$ $\Omega_f^{vac}$ is negligible with respect to $\Omega_f^{st}$
  - we can approximate Thermodynamic potential of the degenerate fermion system as $\Omega_f \approx \Omega_f^{st}$
- star must be in stellar equilibrium
  - particle densities: $N_f = -\partial\Omega_f / \partial \mu_f$
  - charge neutrality
    - $\sum_{f}{e_f N_f} = 0$
  - baryon number conservation
    - $\sum_{i=u,d,s}{N_i} = 3N_B$
  - chemical potentials
    - $\mu_u +\mu_e - \mu_d = 0$, $\mu_d - \mu_s = 0$
  - $\beta$ equilibrium

With these constraints, we obtain the following EoS for the magnetized SSs:

$$\begin{aligned}
E &= \sum_{f}{[\Omega_f+\mu_fN_f]} + B_{bag} + \frac{B^2}{8\pi} \\
P_\parallel &= - \sum_{f}{\Omega_f} - B_{bag} - \frac{B^2}{8\pi} \\
P_\perp &= -\sum_{f}{[\Omega_f+ B\mathcal{M}_f]} + B_{bag} + \frac{B^2}{8\pi}
\end{aligned}$$

- $\mathcal{M}_f] = -\partial\Omega_f/\partial B$ is the magnetization
- there are three main contributions to the EoS
  1. thermodynamic quantities for each species
  2. $\pm B_{bag}$
  3. magnetic field pressures and energy density
