# Exploring the survivability of higher-order multiple protostellar systems - the case of VLA1623

`2026MNRAS.551g1639M` | Monthly Notices of the Royal Astronomical Society 2026 | first author: Murillo, N. M. | arXiv: 2608.27294 | DOI: 10.1093/mnras/stag1639

Card schema 1.0 | model gemini-4-argon | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation
- Question: Whether higher-order protostellar systems survive as gravitationally bound systems or dissolve into binaries over time, tested via a case study of the embedded quadruple protostellar system VLA1623.  
  > "A persistent question in star formation and evolution is whether these higher-order protostellar systems survive as gravitationally bound systems or dissolve into binaries over time." (Abstract); "We explore this question with a case study of the embedded quadruple protostellar system VLA1623 and its observational constraints, assuming that the components A1, A2, B, and W are gravitationally bound." (Abstract)
- Target **VLA 1623-2417**: coordinates _not stated_; z/distance 138 ± 2.6 pc  
  > "VLA 1623-2417 (hereafter VLA1623), located in L1688 at a distance of 138 $\pm$ 2.6 pc (cite: ortiz2018), is one of the most widely studied embedded quadruple protostellar systems (A1+A2, B, and W) with three rotationally-supported gas disks" (Introduction); distance from (cite: ortiz2018)  
  > "VLA 1623-2417 (hereafter VLA1623), located in L1688 at a distance of 138 $\pm$ 2.6 pc (cite: ortiz2018), is one of the most widely studied embedded quadruple protostellar systems (A1+A2, B, and W) with three rotationally-supported gas disks" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: 864 um dust continuum  
  > "An 864 $\mu$m dust continuum image of VLA1623 (ALMA project ID 2018.1.01089, image processing carried out via the NRAO ALMA pipeline (cite: alma2023)) is shown in Figure 1." (VLA1623 observational constraints)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Protostellar masses, gas disk masses, orbital inclinations, and component separations for VLA1623 A1, A2, B, and W  
  > "For our simulations, we adopt the protostar $M_{*}$, gas disk masses $M_{d}$ and gas disk inclination $i$ as the orbital inclination, along with the corresponding uncertainties, for A, B, and W from (cite: sadavoy2024vla1623masses)." (Masses and inclinations); "The adopted A1-A2 separation is 0.1$\ensuremath{''}$, considering the projected separation (14 AU) reported in (cite: sadavoy2024vla1623masses) which was based on (cite: harris2018A)." (Component separations) [from (cite: sadavoy2024vla1623masses), (cite: harris2018A)]
- External data: Outflow mass loss rate of 2.3 x 10^-6 M_sun yr^-1  
  > "We include this effect as a single, constant mass loss rate adopted from (cite: andre1990)." (Outflows and accretion); "| Outflow mass loss rate | $\dot{M}_{\mathrm{loss}}$ | 2.3 | 10$^{-6}$ M$_{\odot}$ yr$^{-1}$ | \(3\) |" (Table 1) [from (cite: andre1990)]
- External data: Cloud core density profile parameters (R_in, R_out, R_ref, n_ref, alpha)  
  > "The cloud core density profile is adopted from (cite: jorgensen2002), which used single-dish observations of protostellar cloud cores together with 1D radiative transfer modeling." (Cloud core) [from (cite: jorgensen2002)]
- External data: Bolometric luminosities for each protostellar component  
  > "where $L_{\mathrm{bol,}p}$ is the bolometric luminosity of protostar $p$, adopted from (cite: murillo2018SED), $R_{*}$ is the protostellar radius set to 2$R_{\odot}$ (cite: codella2024), $G$ is the universal gravitational constant, and $M_{*,p}$ is the protostellar mass of component $p$." (Outflows and accretion) [from (cite: murillo2018SED)]
- Simulation/model as data: REBOUND and REBOUNDx N-body simulations of VLA1623 across 3 simulation sets (Gravity Only, Cloud Core t_life, and Cloud Core t_life x 0.5) with 1000 Monte Carlo input conditions integrated over 8 Myr  
  > "We made use of the REBOUND $N$-body code (cite: rebound) to perform our simulations." (Set-up); "We generate three simulation sets: i) Gravity Only; ii) Cloud Core $t_{\mathrm{life}}$; and iii) Cloud Core $t_{\mathrm{life}}$ $\times$ 0.5 ($t_{\mathrm{life}}$ reduced by half)." (Set-up); "We use a Monte Carlo (MC) algorithm with a uniform distribution (numpy `random.uniform`) to randomly generate 1000 input conditions for each simulation set based on the observational uncertainties of VLA1623" (Parameter space)

## Processing

### Calibration

- pipeline or manual: NRAO ALMA pipeline  
  > "An 864 $\mu$m dust continuum image of VLA1623 (ALMA project ID 2018.1.01089, image processing carried out via the NRAO ALMA pipeline (cite: alma2023)) is shown in Figure 1." (VLA1623 observational constraints)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Assumption that bolometric luminosity equals accretion luminosity and protostellar radius R_* = 2 R_sun for accretion rate calculations  
  > "Mass accretion rates for each component in VLA1623 are calculated with the assumption used in (cite: codella2024), where the bolometric luminosity is assumed to equal the accretion luminosity (i.e., $L_{\mathrm{bol}}$ = $L_{\mathrm{acc}}$)." (Outflows and accretion); "where $L_{\mathrm{bol,}p}$ is the bolometric luminosity of protostar $p$, adopted from (cite: murillo2018SED), $R_{*}$ is the protostellar radius set to 2$R_{\odot}$ (cite: codella2024), $G$ is the universal gravitational constant, and $M_{*,p}$ is the protostellar mass of component $p$." (Outflows and accretion) [from (cite: codella2024)]
- Disk truncation radius limit relation used to constrain the A1-B separation range  
  > "Hence, the disk truncation radius limit presented in (cite: winter2018) is used to constrain the range of separations that can produce the observed disks of A (150–316 au) and B (43 au)." (Component separations) [from (cite: winter2018)]
- Cloud core density profile  
  > "The cloud core density profile is adopted from (cite: jorgensen2002), which used single-dish observations of protostellar cloud cores together with 1D radiative transfer modeling." (Cloud core) [from (cite: jorgensen2002)]

### Not stated but needed to reproduce (our reading)

- Initial orbital phase angles (true anomaly, argument of periapsis, longitude of ascending node) used when initializing the 3D orbits in REBOUND
- Exact individual bolometric luminosity values adopted from Murillo et al. (2018) for each component
- Random number generator seed for the 1000 Monte Carlo realizations

## Analysis recipe

1. **Derive A1-B separation range and component mass accretion rates from observational constraints**: Calculate minimum separation between A and B from disk truncation radius formula; calculate mass accretion rates from bolometric luminosity and protostellar mass.  
  > "Hence, the disk truncation radius limit presented in (cite: winter2018) is used to constrain the range of separations that can produce the observed disks of A (150–316 au) and B (43 au)." (Component separations); "Mass accretion rates for each component in VLA1623 are calculated with the assumption used in (cite: codella2024), where the bolometric luminosity is assumed to equal the accretion luminosity (i.e., $L_{\mathrm{bol}}$ = $L_{\mathrm{acc}}$)." (Outflows and accretion)
   - parameter: R_* = 2 R_sun, d = 138 +/- 2.6 pc  
  > "VLA 1623-2417 (hereafter VLA1623), located in L1688 at a distance of 138 $\pm$ 2.6 pc (cite: ortiz2018), is one of the most widely studied embedded quadruple protostellar systems (A1+A2, B, and W) with three rotationally-supported gas disks" (Introduction); "where $L_{\mathrm{bol,}p}$ is the bolometric luminosity of protostar $p$, adopted from (cite: murillo2018SED), $R_{*}$ is the protostellar radius set to 2$R_{\odot}$ (cite: codella2024), $G$ is the universal gravitational constant, and $M_{*,p}$ is the protostellar mass of component $p$." (Outflows and accretion)
   - assumption: L_bol = L_acc, M_A1 / M_A2 = 1, protostellar mass in simulation M_p is the sum of disk mass M_d,p and protostellar mass M_*,p  
  > "As a simplification, the mass for each protostar in the simulation $M_{p}$ is the sum of the corresponding disk mass $M_{d,p}$ and the protostellar mass $M_{*,p}$ for each source in the simulation." (Masses and inclinations); "We assume $M_{A1}$/$M_{A2}$ = 1, hence distributing the protostellar and disk gas-mass of A evenly among the A1 and A2 components." (Masses and inclinations); "Mass accretion rates for each component in VLA1623 are calculated with the assumption used in (cite: codella2024), where the bolometric luminosity is assumed to equal the accretion luminosity (i.e., $L_{\mathrm{bol}}$ = $L_{\mathrm{acc}}$)." (Outflows and accretion)
   - fitting: _not stated_
   - validation: _not stated_
2. **Generate Monte Carlo initial conditions and run N-body simulations**: Generate 1000 input conditions via uniform Monte Carlo sampling within +/- 3 sigma of observational constraints; integrate 3 sets of N-body simulations (Gravity Only, Cloud Core t_life, Cloud Core t_life x 0.5) over 8 Myr using IAS15.  
  > "The simulations were integrated using IAS15, a 15th order Gauss-Radau integrator (cite: reboundias15)." (Set-up); "We use a Monte Carlo (MC) algorithm with a uniform distribution (numpy `random.uniform`) to randomly generate 1000 input conditions for each simulation set based on the observational uncertainties of VLA1623" (Parameter space); "we set our integration time to 8 Myr, in 2 $\times$ 10$^{5}$ timesteps linearly spaced, distributed approximately as 1 Myr for the embedded protostellar phase (Class 0 and I), 2–3 Myr for the pre-main sequence phase (Class II+III), and an additional 4–5 Myr for the main sequence phase." (Integration time)
   - software: REBOUND, REBOUNDx, numpy
   - parameter: 1000 input conditions, +/- 3 sigma spread, 8 Myr integration time in 2 x 10^5 linearly spaced timesteps, e_A2 = 0, maximum eccentricity e = 0.75 for B and W, cloud core removed when M_core <= 0.1 M_sun  
  > "The cloud core mass, protostellar mass accretion and outflow mass loss rates are then set to zero when $M_{\mathrm{core}}$ $\leq$ 0.1 M$_{\odot}$." (Set-up); "we have adopted a $\pm$3$\sigma$ spread from the mean values listed in" (Parameter space); "Considering all the above observational constraints, we adopt a maximum eccentricity of $e=0.75$ in our simulations." (Parameter space)
   - assumption: Components A1, A2, B, and W are initially gravitationally bound; cloud core is centered on VLA1623 B; circular orbit (e = 0) for A2 around A1; gas drag, magnetic fields, and disk torques are neglected.  
  > "For our case study, we center the cloud core on VLA1623 B, which means that the acceleration vector of B is not modified." (Set-up); "We assume an eccentricity of $e$ = 0 (i.e., circular orbit) for A2 around A1 since the disk does not show indications of internal asymmetries (cite: radley2025; maureira2025)." (Parameter space); "In our simulations, we assume as an initial condition that the components A1, A2, B, and W are gravitationally bound." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
3. **Classify simulation outcomes by degree of multiplicity**: Calculate pairwise total energies and total energy of B wrt the COM at each timestep; evaluate minimum total energies in 0.08 Myr (2000 timestep) intervals to classify systems into quadruples, triples, pair binaries, one binary, or unclassified.  
  > "To classify the results of the simulations, we use the total energy ($E$) as the main diagnostic tool." (Simulation Diagnostics); "The first criterion used to classify the outcome of systems is the minimum total energy of B wrt the COM, $E_\mathrm{min,B}$, in 8 $\times$ 10$^{4}$ yr (0.08 Myr, 2000 timesteps) intervals." (Simulation Diagnostics); "To determine the temporal evolution of the degree of multiplicity, the minimum value $E_{\mathrm{min}}$ for each pair in 0.08 Myr intervals is obtained." (Simulation Diagnostics)
   - parameter: Time interval bin = 8 x 10^4 yr (0.08 Myr, 2000 timesteps); bound criterion E_min < 0  
  > "The first criterion used to classify the outcome of systems is the minimum total energy of B wrt the COM, $E_\mathrm{min,B}$, in 8 $\times$ 10$^{4}$ yr (0.08 Myr, 2000 timesteps) intervals." (Simulation Diagnostics); "When $E_{\mathrm{min}}$ < 0, the pair is bound. Instead, when $E_{\mathrm{min}}$ $\geq$ 0, one of the components in the pair has been ejected." (Simulation Diagnostics)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **NRAO ALMA pipeline** : Image processing of the 864 um dust continuum image of VLA1623  
  > "An 864 $\mu$m dust continuum image of VLA1623 (ALMA project ID 2018.1.01089, image processing carried out via the NRAO ALMA pipeline (cite: alma2023)) is shown in Figure 1." (VLA1623 observational constraints)
- **REBOUND** : Running N-body dynamical simulations integrated with IAS15  
  > "We made use of the REBOUND $N$-body code (cite: rebound) to perform our simulations. The simulations were integrated using IAS15, a 15th order Gauss-Radau integrator (cite: reboundias15)." (Set-up)
- **REBOUNDx** : Implementing protostellar mass accretion onto each component and adjusting component accelerations due to the cloud core  
  > "In order to implement additional astrophysical effects for the simulations with the cloud core, we wrote two routines in REBOUNDx (cite: tamayo2020reboundx) to implement protostellar mass accretion onto each component, and adjust the component accelerations due to the presence of the cloud core." (Set-up)
- **numpy** : Generating 1000 Monte Carlo input conditions using a uniform distribution (random.uniform)  
  > "We use a Monte Carlo (MC) algorithm with a uniform distribution (numpy `random.uniform`) to randomly generate 1000 input conditions for each simulation set based on the observational uncertainties of VLA1623" (Parameter space)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Separation A1-B range | 1 - 4 | not stated | arcsec | 1 | / Separation A1-B / $S_{\mathrm{A1-B}}$ / 1 – 4 / $\ensuremath{''}$ / This work /; Considering either A or B as a perturber of the other, we find a range of 1$\ensuremath{''}$–4$\ensuremath{''}$, equivalent to 138–552 AU at $d\sim$138 pc for eccentricities smaller than 0.75. |
| Accretion rate of A1 | 1.43 | ±0.45 | 10^-8 M_sun yr^-1 | 1 | / Accretion rate of A1 / $\dot{M}_{\mathrm{A1}}$ / 1.43$\pm$0.45 / 10$^{-8}$ M$_{\odot}$ yr$^{-1}$ / This work (Sect. [2.4](#subsec:vla1623-in-out)) / |
| Accretion rate of A2 | 1.43 | ±0.45 | 10^-8 M_sun yr^-1 | 1 | / Accretion rate of A2 / $\dot{M}_{\mathrm{A2}}$ / 1.43$\pm$0.45 / 10$^{-8}$ M$_{\odot}$ yr$^{-1}$ / This work / |
| Accretion rate of B | 2.26 | ±0.54 | 10^-9 M_sun yr^-1 | 1 | / Accretion rate of B / $\dot{M}_{\mathrm{B}}$ / 2.26$\pm$0.54 / 10$^{-9}$ M$_{\odot}$ yr$^{-1}$ / This work / |
| Accretion rate of W | 3.49 | ±0.42 | 10^-9 M_sun yr^-1 | 1 | / Accretion rate of W / $\dot{M}_{\mathrm{W}}$ / 3.49$\pm$0.42 / 10$^{-9}$ M$_{\odot}$ yr$^{-1}$ / This work / |
| Quadruple survival fraction (Gravity only) | 30.0 | not stated | % | 3 | / Gravity only / 30.0 / 34.9 / 18.7 / 3.5 / 12.9 / 70.0 / |
| Triple fraction (Gravity only) | 34.9 | not stated | % | 3 | / Gravity only / 30.0 / 34.9 / 18.7 / 3.5 / 12.9 / 70.0 / |
| Pair Binaries fraction (Gravity only) | 18.7 | not stated | % | 3 | / Gravity only / 30.0 / 34.9 / 18.7 / 3.5 / 12.9 / 70.0 / |
| One Binary fraction (Gravity only) | 3.5 | not stated | % | 3 | / Gravity only / 30.0 / 34.9 / 18.7 / 3.5 / 12.9 / 70.0 / |
| Quadruple survival fraction (Cloud Core t_life) | 30.0 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ / 30.0 / 25.4 / 16.6 / 13.0 / 15.0 / 70.0 / |
| Triple fraction (Cloud Core t_life) | 25.4 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ / 30.0 / 25.4 / 16.6 / 13.0 / 15.0 / 70.0 / |
| Pair Binaries fraction (Cloud Core t_life) | 16.6 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ / 30.0 / 25.4 / 16.6 / 13.0 / 15.0 / 70.0 / |
| One Binary fraction (Cloud Core t_life) | 13.0 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ / 30.0 / 25.4 / 16.6 / 13.0 / 15.0 / 70.0 / |
| Quadruple survival fraction (Cloud Core t_life x 0.5) | 29.1 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ $\times$ 0.5 / 29.1 / 30.9 / 17.6 / 7.5 / 14.9 / 70.9 / |
| Triple fraction (Cloud Core t_life x 0.5) | 30.9 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ $\times$ 0.5 / 29.1 / 30.9 / 17.6 / 7.5 / 14.9 / 70.9 / |
| Pair Binaries fraction (Cloud Core t_life x 0.5) | 17.6 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ $\times$ 0.5 / 29.1 / 30.9 / 17.6 / 7.5 / 14.9 / 70.9 / |
| One Binary fraction (Cloud Core t_life x 0.5) | 7.5 | not stated | % | 3 | / Cloud Core $t_{\mathrm{life}}$ $\times$ 0.5 / 29.1 / 30.9 / 17.6 / 7.5 / 14.9 / 70.9 / |

## Qualitative findings

- VLA1623 has a ~30% probability of surviving as a gravitationally-bound quadruple system up to 8 Myr across all three simulation sets.  
  > "The probability of VLA1623 surviving into the main sequence as a gravitationally-bound quadruple system is 30%. This probability is consistent in all the simulation sets." (Conclusions)
- VLA1623 has a 25–35% probability of dissolving into a triple system, indicating that quadruple dissolution contributes to the formation of stable triple systems.  
  > "The probability of VLA1623 dissolving into a triple system (i.e., ejection of one component) is between 25 and 35%. This outcome suggests that quadruple protostellar systems can contribute significantly to the production of stable triple (proto)stellar systems." (Conclusions)
- Component W is the least likely to be ejected, whereas the lowest-mass components A1 or A2 are the most commonly ejected.  
  > "Component VLA1623 W is the least likely to be ejected. In contrast, A1 or A2 are the most commonly ejected components." (Conclusions)

## Claim tuples

- H: The embedded quadruple protostellar system VLA1623 can survive as a gravitationally-bound quadruple system into the main sequence. | E: Integrate 3 sets of N-body simulations (1000 Monte Carlo realizations each) over 8 Myr incorporating observational constraints, protostellar mass accretion, and cloud core potential and dispersal. | R: Approximately 30% (29.1% to 30.0%) of simulated systems remain gravitationally-bound quadruples at 8 Myr across all three simulation sets. | F: VLA1623 has a 30% probability of surviving into the main sequence as a gravitationally-bound quadruple system, depending on a combination of mass ratios, separations, and eccentricities. | **supported**
- H: Dissolution of quadruple protostellar systems contributes to the formation of stable triple stellar systems. | E: Classify the multiplicity outcomes of the 8 Myr N-body simulation ensembles using pairwise minimum total energies. | R: Between 25.4% and 34.9% of simulations dissolve into a bound triple system with one ejected component. | F: Quadruple protostellar systems provide a significant pathway to form stable triple systems that survive into the main sequence, with longer cloud core lifetimes reducing triple formation in favor of single binaries with two ejections. | **supported**
- H: Wide-separation component W is the most susceptible to ejection from the VLA1623 quadruple system. | E: Track which individual components (A1, A2, B, W) become gravitationally unbound in simulations that form triples or binaries. | R: Components A1 and A2 are most frequently ejected between 0.1 and 3 Myr, whereas W is the least likely component to be ejected when a triple forms. | F: Despite its wide separation (~10^3 AU), component W is less likely to be ejected than the lower-mass close binary components A1 and A2. | **refuted**

## Reasoning

- Why this data: VLA1623 is a well-studied embedded quadruple protostellar system with three rotationally-supported gas disks that allow protostellar masses to be derived for components A1+A2, B, and W, making it an ideal case study.  
  > "Analysis of the rotationally-supported disks enabled protostellar masses to be derived for components A1+A2, B and W (cite: ohashi2022; sadavoy2024vla1623masses), making VLA1623 an ideal case study." (Introduction)
- Why this method: Hydrodynamical simulations are too computationally expensive to explore a broad parameter space over the long integration times (8 Myr) needed from the protostellar to main sequence stages, whereas N-body simulations allow this exploration.  
  > "However, the computational cost of these simulations limits the exploration of a broad parameter space and the long integration times needed to study the survivability of higher-order systems from the protostellar phase to the main sequence stage." (Introduction); "This method allows for the exploration of the dynamical evolution of higher-order protostellar systems, although it sacrifices a detailed treatment of gas, dust, and magnetic fields." (Introduction)
- Alternative: Adopting literature proper motion constraints into the simulations was rejected due to limitations in epoch coverage and missing constraints for either W or A1+A2.  
  > "Due to the limitations of the available proper motion analysis we did not adopt these constraints into our simulations." (Proper motion information)
- Alternative: Non-ideal magnetohydrodynamical (MHD) simulations were not used due to high computational cost limiting parameter space exploration and long integration times.  
  > "However, the computational cost of these simulations limits the exploration of a broad parameter space and the long integration times needed to study the survivability of higher-order systems from the protostellar phase to the main sequence stage." (Introduction)
- How they decided it was enough: An integration time of 8 Myr was chosen based on literature lifetimes for Class 0/I (~1 Myr), Class II/III (2-3 Myr), and main sequence (4-5 Myr) stages.  
  > "Combining all these constraints from observations and models, and considering our objective is to explore which systems reach the main sequence as gravitationally-bound systems, we set our integration time to 8 Myr, in 2 $\times$ 10$^{5}$ timesteps linearly spaced" (Integration time)
- Limitation (authors): Physical processes such as gas dynamical friction (drag), accretion angle, outflow position angle, magnetic fields, rotationally-supported disk torques, and other gas/dust structures are not included.  
  > "Consequently, physical processes that can impact the evolution of multiple protostellar systems such as gas dynamical friction (drag), accretion angle, outflow position angle, magnetic fields, rotationally-supported disks, and other gas and dust structures (e.g., (cite: offner2023)) were not included" (Set-up); "The directions of the outflows, direction of mass accretion from the cloud core or the disk, and the torques produced by the rotationally-supported disks are also not being factored into the simulations presented here." (Discussion)
- Limitation (authors): The simulations model VLA1623 as an isolated system, neglecting its clustered environment.  
  > "Finally, our simulations are modeling an isolated higher-order protostellar system, when in fact VLA1623 is located in a clustered environment (e.g., (cite: nakamura2025))." (Discussion)
- Limitation (authors): About 15% of simulated systems remain unclassified by the energy pair criteria due to energy oscillations in complex configurations.  
  > "About 15% of the systems are unclassified from their total energies due to the complexity of the configurations." (Conclusions)
- Caveat (inferred, ours): Neglecting gas dynamical friction (drag) from the dense envelope and hydrodynamic interactions with the massive circumbinary disk around A1+A2 may significantly alter orbital migration and ejection statistics during the first 1 Myr.
- Caveat (inferred, ours): Centering the static cloud core potential purely on component B (leaving B's acceleration unmodified by the core) introduces an artificial asymmetry in the gravitational potential.
- Caveat (inferred, ours): Initial 3D orbital angles (longitude of ascending node, argument of periapsis, true anomaly) are not specified in the text, which affects exact reproducibility of the 3D orbital hierarchy.

## Reproducibility

- Data public (paper): Model grids are available upon request to the authors.  
  > "The model grids are available upon request to the authors." (Data Availability)
- Products in archive: _not stated_
- Missing: Custom REBOUNDx routines written for cloud core acceleration and mass accretion
- Missing: Exact distribution or fixed values assumed for orbital angles (omega, Omega, true anomaly/mean anomaly) when initializing particles in REBOUND
- Missing: Individual component bolometric luminosities adopted from Murillo et al. (2018) to compute accretion rates
- Missing: Random seed for the 1000 Monte Carlo initial condition realizations
- Data volume (inferred): A few GB (3000 N-body runs with 2e5 timesteps each, plus one archival ALMA continuum FITS image)
- Score (inferred): 65/5, The N-body simulation equations, software (REBOUND/REBOUNDx), integrator (IAS15), timestepping, and input parameter distributions (Table 1) are clearly documented, and only statistical ensemble outcomes need to be matched; however, custom REBOUNDx scripts are not released, model grids are only available upon request, and initial orbital phase angle assumptions are not explicitly stated.
- Rediscovery candidate: no, This is primarily an N-body dynamical modeling paper using literature constraints rather than an observational ALMA data analysis paper (ALMA data is only used for an illustrative continuum figure), and the custom simulation code is not publicly released.

## Links

- Method: (cite: winter2018) (Disk truncation radius limit equation used to constrain the A1-B separation range)
- Method: (cite: codella2024) (Accretion rate calculation method assuming bolometric luminosity equals accretion luminosity and R_* = 2 R_sun)
- Method: (cite: rebound) (REBOUND N-body simulation code)
- Method: (cite: reboundias15) (IAS15 15th-order Gauss-Radau integrator)
- Method: (cite: tamayo2020reboundx) (REBOUNDx library used to implement custom mass accretion and cloud core potential routines)
- Companion: (cite: sadavoy2024vla1623masses) (Primary source of observational constraints (protostellar masses, disk masses, inclinations, separations) for VLA1623)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 2,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2018.1.01089.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 37,
  "rate": 0.481
 },
 "evidence_ok": true
}
```
