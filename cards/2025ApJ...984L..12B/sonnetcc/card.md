# exoALMA. VII. Benchmarking Hydrodynamics and Radiative Transfer Codes

`2025ApJ...984L..12B` | The Astrophysical Journal Letters 2025 | first author: Bae, Jaehan | arXiv: 2504.18643 | DOI: 10.3847/2041-8213/adc436

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Do widely used hydrodynamics (FARGO3D, Idefix, Athena++, PLUTO, Phantom) and radiative transfer (mcfost, RADMC-3D) codes give consistent planet-driven kinematic perturbations, temperatures and synthetic 12CO cubes, and consistent planet-location retrieval with DISCMINER?  
  > "in this paper we tested if various hydrodynamics and radiative transfer codes produce consistent results." (Introduction)
- Target **Synthetic benchmark disk with an embedded Jupiter-mass planet (no real source)**: coordinates _not stated_; z/distance 140 pc (assumed)  
  > "we placed the planet at 100 au from the solar-mass central star." (Radiative Transfer Calculation Setup); "The star was placed at 140 parsecs from the observer." (Radiative Transfer Calculation Setup); distance from assumed in the benchmark setup  
  > "we placed the planet at 100 au from the solar-mass central star." (Radiative Transfer Calculation Setup); "The star was placed at 140 parsecs from the observer." (Radiative Transfer Calculation Setup)

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15 arcsec Gaussian beam applied to synthetic cubes (fiducial exoALMA beam size)  
  > "these are the beamsize and level of noise of fiducial exoALMA molecular line images" (Retrieval of Planet Location using DISCMINER)
- max recoverable scale: _not stated_
- sensitivity: 1.5 K noise (std) per 100 m/s channel added to synthetic cubes (fiducial exoALMA level)  
  > "and added random noises with a standard deviation of 1.5 K in each" (Retrieval of Planet Location using DISCMINER)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (synthetic) (not stated)
- External data: Fiducial exoALMA molecular-line beam (0.15 arcsec) and noise level (1.5 K per 100 m/s channel)  
  > "these are the beamsize and level of noise of fiducial exoALMA molecular line images" (Retrieval of Planet Location using DISCMINER) [from (cite: Teague_exoALMA)]
- External data: Typical noise in exoALMA molecular line images, about 1.5 K  
  > "the typical level of noise in the exoALMA molecular line images is about 1.5 K" (Channel Maps) [from (cite: Teague_exoALMA)]
- External data: Disk aspect ratio 0.1 motivated by exoALMA planet candidate locations and the inferred disk temperature profile  
  > "when we adopt the temperature profile inferred in (cite: Galloway_exoALMA)." (Initial Disk Setup) [from (cite: Pinte_exoALMA); (cite: Galloway_exoALMA)]
- External data: Gas surface density at planet location (0.52 g cm^-2) checked against values inferred for exoALMA disks  
  > "which is broadly consistent with the gas surface density inferred for exoALMA disks (cite: Rosotti_exoALMA)" (Radiative Transfer Calculation Setup) [from (cite: Rosotti_exoALMA)]
- Simulation/model as data: Five 3D hydrodynamic planet-disk simulations (FARGO3D, Idefix, Athena++, PLUTO, Phantom), Mp = 1e-3 Mstar, output at 500 planetary orbits  
  > "we simulated a protoplanetary disk with an embedded giant planet" (abstract); "using the outputs at 500 planetary orbits from the hydrodynamic simulations introduced in the previous Section." (Radiative Transfer Calculations)
- Simulation/model as data: Nine hydro + radiative transfer combinations (mcfost on all five, RADMC-3D on four grid codes) producing synthetic 12CO cubes  
  > "This results in nine total combinations." (Radiative Transfer Calculations)

## Processing

### Calibration

- pipeline or manual: _not stated_
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
- smoothing: raw synthetic cubes convolved with 0.15 arcsec Gaussian beam  
  > "To do so, we convolved the raw synthetic cubes with a" (Retrieval of Planet Location using DISCMINER)
- final beam: _not stated_
- final rms: 1.5 K per 100 m/s channel (added random noise)  
  > "and added random noises with a standard deviation of 1.5 K in each" (Retrieval of Planet Location using DISCMINER)

### Inherited from earlier work

- Detailed DISCMINER retrieval workflow  
  > "For the detailed workflow of the retrieval, we refer the reader to (cite: discminer; izquierdo2023)." (Retrieval of Planet Location using DISCMINER) [from (cite: discminer; izquierdo2023)]
- Technical details of the hydrodynamics codes  
  > "While we refer the reader to the relevant papers listed above for technical details of these codes" (Grid-based Hydrodynamics Simulation Setup) [from (cite: fargo3d; idefix; athena; pluto; Phantom)]
- Further details of the Phantom code  
  > "We refer the reader to (cite: Phantom) for further details on the code." (Smoothed Particle Hydrodynamics Simulation Setup) [from (cite: Phantom)]
- Wave-killing damping zones at radial boundaries  
  > "we implemented a wave-killing zone at the radial boundaries (cite: devalborro2006)" (Boundary Conditions) [from (cite: devalborro2006)]
- Phantom viscosity formulation ('two first derivatives')  
  > "following the ‘two first derivatives’ formulation of the Navier Stokes terms outlined in Section 3.2.4 of (cite: lodato2010)" (Smoothed Particle Hydrodynamics Simulation Setup) [from (cite: lodato2010)]
- Beam size and noise level for synthetic observations taken from exoALMA fiducial images  
  > "these are the beamsize and level of noise of fiducial exoALMA molecular line images" (Retrieval of Planet Location using DISCMINER) [from (cite: Teague_exoALMA)]

### Not stated but needed to reproduce (our reading)

- DISCMINER model setup: model components, fixed vs free parameters, priors, initial guesses, masks and fitting region used for each synthetic cube
- How the folded velocity residual map, the peak residual and its significance (3.64 sigma) are computed (smoothing, azimuthal/radial binning, noise estimate)
- Random seed or realization of the added noise (retrieved values depend on it)
- Line radiative transfer setup: 12CO rest frequency, velocity channel grid, number of channels, image size/pixel scale and viewing grid for mcfost and RADMC-3D
- Number of photon packages and wavelength grid beyond the stated 1e9 photons, and convergence criteria for mcfost vs RADMC-3D temperature runs
- Hydrodynamic code numerical choices (reconstruction, Riemann solver, CFL number, time integrator) per code
- Phantom smoothing-length settings, particle placement recipe, and how Voronoi cells map to mcfost cells
- Inputs and scripts used to compute the grid-by-grid temperature and brightness-temperature comparisons

## Analysis recipe

1. **run planet-disk hydrodynamic simulations with five codes**: 3D spherical-coordinate simulations of a vertically isothermal disk with a prescribed-potential planet on a fixed circular orbit, evolved for 500 planetary orbits, in four grid codes and one SPH code  
  > "we simulated a protoplanetary disk with an embedded giant planet" (abstract); "We fixed the planet on a circular orbit and did not allow orbital migration." (Planet Potential)
   - software: FARGO3D, Idefix, Athena++, PLUTO, Phantom
   - parameter: Grid: 288 log cells in r (0.3 to 3.0), 128 in theta, 784 in phi; about 12 cells per scale height  
  > "We used 288 logarithmically-spaced grid cells in $r$, 128 linear grid cells in $\theta$, and 784 linear grid cells in $\phi$, respectively." (Simulation Domain & Numerical Resolution); "a numerical resolution allowing about 12 grid cells per scale height" (Simulation Domain & Numerical Resolution)
   - parameter: Phantom: 10 million SPH particles  
  > "We used 10 million SPH particles" (Smoothed Particle Hydrodynamics Simulation Setup)
   - parameter: Planet mass ramped up over 100 orbits (sin^2 ramp), final Mp = 1e-3 Mstar  
  > "The potential of the planet was ramped up over the initial 100 orbits" (Smoothed Particle Hydrodynamics Simulation Setup)
   - parameter: Kinematic viscosity nu = 1e-5 (alpha = 1e-3 at planet location)  
  > "We adopted kinematic viscosity characterized by $\nu = 10^{-5}$." (Initial Disk Setup)
   - assumption: Temperature power law with q = -0.5, H/R = 0.1 at planet; vertically isothermal, isothermal equation of state  
  > "We assumed that the disk is vertically isothermal and adopted an isothermal equation of state." (Initial Disk Setup)
   - assumption: Initial total disk mass 0.01 Msun, surface density proportional to R^-1 (outcome scalable)  
  > "We chose $\rho_p$ such that the total initial disk mass is $0.01~M_\odot$." (Initial Disk Setup)
   - fitting: _not stated_
   - validation: Additional simulations without FARGO orbital advection confirmed the outcome does not depend on it; resolution cited as sufficient for convergence  
  > "although we ran additional simulations without implementing FARGO and confirmed that the outcome of the simulations do not depend on the use of the FARGO algorithm" (Grid-based Hydrodynamics Simulation Setup)
2. **compare hydrodynamic outputs between codes**: Compare 2D phi-r maps of density and velocity components at Z/R = 0, 0.1, 0.3 and azimuthally averaged radial profiles after 500 orbits  
  > "at three different heights after 500 planetary orbits of evolution" (Results); "in Figure [5](#fig:radial_profiles) we present azimuthally averaged radial profiles of the surface density and azimuthal velocity." (Results)
   - parameter: Heights Z/R = 0, 0.1, 0.3  
  > "These heights are chosen to cover a range of vertical layers which various molecular lines having different optical depths probe" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **compute dust temperature with Monte Carlo radiative transfer**: Monte Carlo dust radiative transfer on the hydrodynamic grid (Voronoi cells per SPH particle for Phantom) with identical dust opacities in both codes  
  > "we first determined the dust temperature by running Monte Carlo simulations." (Radiative Transfer Calculation Setup); "The same opacities were used for both `mcfost` and `RADMC-3D` Monte Carlo simulations." (Radiative Transfer Calculation Setup)
   - software: mcfost, RADMC-3D
   - parameter: Star: 1 Msun, radius 2 Rsun, 4000 K; 1e9 photons  
  > "We placed a solar-mass star having a radius of $2~R_\odot$ and a temperature of 4000 K at the center of the domain" (Radiative Transfer Calculation Setup)
   - parameter: Dust size distribution dn/da proportional to a^-3.5 from 0.03 micron to 1 mm; dust mass 1% of gas mass  
  > "Dust opacities were calculated assuming a power-law grain size distribution" (Radiative Transfer Calculation Setup); "The total dust mass was assumed to be $1\%$ of the gas mass in each grid cell." (Radiative Transfer Calculation Setup)
   - parameter: Physical scaling: planet at 100 au, solar-mass star, total gas mass 0.01 Msun, source at 140 pc  
  > "we placed the planet at 100 au from the solar-mass central star." (Radiative Transfer Calculation Setup)
   - assumption: Astrosilicate grains, Mie theory, isotropic scattering only  
  > "We computed the dust optical properties using the Mie theory, considering isotropic scattering only." (Radiative Transfer Calculation Setup); "Grain composition was assumed to be astrosilicates (cite: Weingartner2001)." (Radiative Transfer Calculation Setup)
   - assumption: Gas and dust in LTE sharing the same temperature  
  > "We assumed that the gas and dust are in local thermodynamic equilibrium, sharing the same temperature." (Radiative Transfer Calculation Setup)
   - fitting: _not stated_
   - validation: Cross-check between mcfost and RADMC-3D temperatures  
  > "When `mcfost` models are compared with `RADMC-3D` models, we found a strong consistency between the models." (Temperature)
4. **generate synthetic 12CO line cubes**: Line radiative transfer of 12CO J=3-2 with prescribed abundance, freeze-out below 20 K, thermal broadening only, disk inclined 45 deg, PA 90 deg, planet 45 deg west of south  
  > "The disk inclination was set to 45 degrees, with a position angle of 90 degree (from north to east)." (Radiative Transfer Calculation Setup); "The disk was placed at 140 pc and positioned such that the planet is located 45 degrees west of south." (Radiative Transfer Calculation Setup)
   - software: mcfost, RADMC-3D
   - parameter: 12CO abundance 1e-4 relative to total gas for T > 20 K  
  > "We adopted a $^{12}$CO abundance of $10^{-4}$ relative to the total gas (by number) when the temperature is higher than 20 K." (Radiative Transfer Calculation Setup)
   - assumption: All CO frozen onto grains below 20 K  
  > "Below 20 K, we assumed that all CO molecules are frozen onto grains and no gas phase CO is present." (Radiative Transfer Calculation Setup)
   - assumption: Line width from thermal broadening only  
  > "We made an assumption that the local line width is set by thermal broadening only and ignored any non-thermal broadening." (Radiative Transfer Calculation Setup)
   - fitting: _not stated_
   - validation: _not stated_
5. **compare temperatures and channel-map brightness temperatures across models**: Grid-by-grid comparison of azimuthally averaged 2D temperature distributions (absolute and fractional), and brightness temperature along an iso-velocity contour relative to the FARGO3D + mcfost reference model  
  > "When the azimuthally averaged two-dimensional temperature distributions are compared grid by grid" (Temperature); "we present the brightness temperature of each model relative to the reference model (`FARGO3D` + `mcfost`), along the iso-velocity contour" (Channel Maps)
   - software: mcfost, RADMC-3D
   - fitting: _not stated_
   - validation: Differences compared against the typical exoALMA line noise of about 1.5 K  
  > "Given that the typical level of noise in the exoALMA molecular line images is about 1.5 K" (Channel Maps)
6. **retrieve planet location from synthetic cubes**: Convolve cubes with 0.15 arcsec beam, add 1.5 K noise per 100 m/s channel, run DISCMINER to build a folded velocity residual map and locate its peak (radius, azimuth, peak residual velocity)  
  > "to retrieve the planet location in synthetic cubes" (Retrieval of Planet Location using DISCMINER); "we present a folded velocity residual map for the" (Retrieval of Planet Location using DISCMINER)
   - software: DISCMINER
   - parameter: Beam 0.15 arcsec; noise 1.5 K per 100 m/s channel  
  > "and added random noises with a standard deviation of 1.5 K in each" (Retrieval of Planet Location using DISCMINER)
   - fitting: _not stated_
   - validation: Retrieved radius and azimuth compared with the true planet location (100 au, -45 deg)  
  > "which are in a good agreement with the true planet location: 100 au and" (Retrieval of Planet Location using DISCMINER)
7. **compare retrieved planet location and peak residual across models**: Plot retrieved radial and azimuthal location and peak residual velocity for all nine hydro + RT combinations and compare with the true location  
  > "To compare the inferred location of the planet and the associated peak velocity residual, we plot these quantities in Figure" (Retrieval of Planet Location using DISCMINER)
   - software: DISCMINER
   - fitting: _not stated_
   - validation: Mean retrieved radius compared with one beam (0.15 arcsec, 21 au at 140 pc)  
  > "Note, however, that the mean retrieved radial location is within one beam" (Retrieval of Planet Location using DISCMINER)

## Software

- **FARGO3D** 2.01: Grid-based (finite-difference) hydrodynamic planet-disk simulation  
  > "Among the grid-based codes, `FARGO3D` employs a finite-difference scheme" (Grid-based Hydrodynamics Simulation Setup)
- **Idefix** 1.1.0: Grid-based (finite-volume) hydrodynamic simulation  
  > "The other three codes, namely `Idefix`, `Athena++`, and `PLUTO`, utilize a finite-volume scheme" (Grid-based Hydrodynamics Simulation Setup)
- **Athena++** 21.0: Grid-based (finite-volume) hydrodynamic simulation  
  > "The other three codes, namely `Idefix`, `Athena++`, and `PLUTO`, utilize a finite-volume scheme" (Grid-based Hydrodynamics Simulation Setup)
- **PLUTO** 4.3: Grid-based (finite-volume) hydrodynamic simulation  
  > "The other three codes, namely `Idefix`, `Athena++`, and `PLUTO`, utilize a finite-volume scheme" (Grid-based Hydrodynamics Simulation Setup)
- **Phantom** 2022.0.1: Smoothed particle hydrodynamics planet-disk simulation  
  > "`Phantom` solves the equations of hydrodynamics in Lagrangian form." (Smoothed Particle Hydrodynamics Simulation Setup)
- **mcfost** 4.1.08: Monte Carlo dust temperature and synthetic 12CO line cubes for all five hydro models  
  > "The same opacities were used for both `mcfost` and `RADMC-3D` Monte Carlo simulations." (Radiative Transfer Calculation Setup)
- **RADMC-3D** 2.0: Monte Carlo dust temperature and synthetic 12CO line cubes for the four grid-based hydro models  
  > "The same opacities were used for both `mcfost` and `RADMC-3D` Monte Carlo simulations." (Radiative Transfer Calculation Setup)
- **DISCMINER** : Retrieving planet location and peak velocity residual from synthetic cubes  
  > "to retrieve the planet location in synthetic cubes" (Retrieval of Planet Location using DISCMINER)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Max grid-by-grid temperature difference among the four grid-based mcfost models | 0.84 | not stated | K | 5 | no two models have a temperature difference greater than 0.84 K |
| Max fractional temperature difference among grid-based mcfost models (Idefix vs Athena++) | 2.7 | not stated | % | 5 | no two models have a difference greater than $2.7~\%$ |
| Max grid-by-grid temperature difference among RADMC-3D models | 0.51 | not stated | K | 5 | we found no two models have a difference greater than 0.51 K |
| Max fractional temperature difference among RADMC-3D models | 1.8 | not stated | % | 5 | no two models have a difference greater than $1.8~\%$ |
| Fractional temperature difference mcfost vs RADMC-3D, Athena++ models (largest), everywhere in domain | < 3 | not stated | % | 5 | the fractional temperature difference is smaller than $3~\%$ everywhere in the domain |
| Phantom + mcfost temperature difference from other mcfost models, individual cells and domain-averaged mean | up to +/-15 in cells; about 5 domain-averaged | not stated | % | 5 | up to $\pm 15~\%$ in individual grid cells, with a domain-averaged mean difference of about $5~\%$ |
| Brightness temperature difference among all models along iso-velocity contour | within +/-1.5 | not stated | K | 5 | all models agree with each other within $\pm 1.5$ K |
| Brightness temperature difference among models at planet location | < 0.5 | not stated | K | 5 | the difference among the models is $<0.5$ K |
| Gap-center surface density suppression, grid-based codes | about 70 | not stated | % | 2 | is suppressed by $\simeq 70~\%$ |
| Gap-center surface density decrease, Phantom | about 10 | not stated | % | 2 | the surface density is decreased by only $\simeq 10~\%$ |
| Fraction of initial disk mass lost through inner boundary in Phantom after 500 orbits | about 30 | not stated | % | 1 | We found that about 30% of the initial disk mass is lost through the inner boundary after 500 orbits. |
| DISCMINER peak significance in folded velocity residual map, FARGO3D + mcfost cube | 3.64 | not stated | sigma | 6 | found a peak in the folded velocity residual map with a $3.64\sigma$ significance |
| Retrieved planet radius, FARGO3D + mcfost cube (true 100 au) | 107.8 | not stated | au | 6 | inferred the planet to be at 107.8 au in radius |
| Retrieved planet azimuth, FARGO3D + mcfost cube (true -45 deg) | -45.25 | not stated | degrees | 6 | and $-45.25$ degrees in azimuth |
| Mean retrieved planet radius across models (min 105.0 au Idefix+RADMC-3D, max 116.2 au Phantom+mcfost) | 109.0 | not stated | au | 7 | with a mean distance of 109.0 au, a minimum distance of 105.0 au; and a maximum distance of 116.2 au |
| Mean retrieved planet azimuth across models (min -48.97 PLUTO+mcfost, max -41.49 PLUTO+RADMC-3D) | -45.92 | not stated | degrees | 7 | with a mean azimuthal angle of $-45.92$ degrees, a minimum azimuthal angle of $-48.97$ degrees |
| Mean peak residual velocity across models (min 0.054 Idefix+RADMC-3D, max 0.088 Athena++ + mcfost) | 0.074 | not stated | km/s | 7 | with a mean of $0.074~{\rm km~s}^{-1}$ |

## Qualitative findings

- Retrieved planet radii are systematically biased to larger radii, possibly because the peak residual is more sensitive to the outer spiral arm  
  > "we speculate that this bias is because the peak residual is generally more sensitive to the outer spiral arm" (Retrieval of Planet Location using DISCMINER)
- Phantom gap is shallower (boundary conditions, numerical viscosity), so gap-shape planet mass inference from Phantom may overestimate mass, but spiral morphology and perturbation level agree  
  > "the overall morphology of the spirals driven by the planet and the level of density perturbation associated with the spirals seen in the `Phantom` simulation agree well with those seen in grid-based simulations" (Results)

## Claim tuples

- H: Different hydrodynamics codes produce consistent planet-driven density and velocity perturbations | E: Four grid codes and Phantom run with matched setup, compared in 2D maps and 1D profiles after 500 orbits | R: Grid-based codes agree closely; Phantom agrees on spirals but has a shallower gap | F: Excellent agreement among grid-based codes; Phantom consistent for spiral perturbations only | **supported**
- H: Phantom reproduces the same gap and azimuthal velocity structure as the grid codes | E: Compared azimuthally averaged surface density and azimuthal velocity profiles | R: Gap suppression about 10% vs about 70% in grid codes; azimuthal velocity variation about 1% vs about 6% | F: Planet-opened gap is shallower in Phantom, attributed to boundary conditions | **partially**
- H: mcfost and RADMC-3D give consistent disk temperature and 12CO channel maps | E: Nine hydro + RT combinations compared grid-by-grid in temperature and along an iso-velocity contour in brightness temperature | R: Temperature within about 3% (grid-based hydro) and brightness temperature within +/-1.5 K for all models | F: Differences are below typical exoALMA noise | **supported**
- H: Planet location retrieval from synthetic cubes is robust to the choice of hydro and RT code | E: DISCMINER retrieval on all nine cubes after beam convolution and noise addition | R: Mean radius 109.0 au and azimuth -45.92 deg versus true 100 au and -45 deg; peak residual 0.054 to 0.088 km/s | F: Any combination of tested codes gives consistent retrieval | **supported**

## Reasoning

- Why this data: No prior systematic benchmark of hydro and RT codes for planet-induced kinematic perturbations  
  > "no systematic hydrodynamics or radiative transfer benchmark tests comparing kinematic perturbations induced by planets embedded in their birth protoplanetary disks have been carried out" (Introduction)
- Why this method: Hydrodynamic simulations plus radiative transfer forward modeling used to infer planet location and mass behind observed substructures  
  > "Hydrodynamic planet-disk interaction simulations, combined with radiative transfer calculations, can give us deeper understanding of the nature of observed substructures." (Introduction)
- Alternative: Runs without FARGO orbital advection were done and gave the same outcome  
  > "although we ran additional simulations without implementing FARGO and confirmed that the outcome of the simulations do not depend on the use of the FARGO algorithm" (Grid-based Hydrodynamics Simulation Setup)
- How they decided it was enough: _not stated_
- Limitation (authors): Only a single base hydrodynamic model; planet mass, eccentricity/migration, temperature stratification, cooling time, viscosity and magnetic fields not varied  
  > "Admittedly, we only considered a single base hydrodynamics model." (Conclusion)
- Limitation (authors): Phantom + RADMC-3D not tested because no module reads Phantom outputs  
  > "This results in nine total combinations." (Radiative Transfer Calculations)
- Limitation (authors): Origin of larger Athena++ temperature differences left for future study  
  > "It is certainly worthwhile further investigating why `Athena++` models show larger differences" (Temperature)
- Caveat (inferred, ours): No real ALMA data are used; the exoALMA data only motivate beam size and noise, so the work is a code benchmark on synthetic data
- Caveat (inferred, ours): Single noise realization and single planet location; the scatter in retrieved location may not capture noise-driven variance
- Caveat (inferred, ours): Isothermal hydro setup differs from the RT temperature structure used afterwards (temperatures are not fed back)
- Caveat (inferred, ours): Retrieved radius is biased about 9 au high with only 3.64 sigma significance in the fiducial case

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: _not stated_
- Missing: DISCMINER configuration and fit settings for the synthetic cubes
- Missing: Exact simulation input/parameter files for each hydrodynamics code and RT code
- Missing: Noise realization seed and image/channel grid details for the cubes
- Missing: Scripts used for the temperature and brightness-temperature comparisons
- Data volume (inferred): No ALMA data needed; simulation outputs and synthetic cubes only (compute-heavy: five 3D hydro runs to 500 orbits and nine RT runs)
- Score (inferred): 3/5, On an assumed 1-5 scale: codes and versions are public and setup parameters are largely given, but DISCMINER settings and RT numerical details are missing and the compute is heavy.
- Rediscovery candidate: no, No ALMA data are used; the results come from simulations and synthetic cubes, so there is no archive data to redo.

## Links

- Method: (cite: discminer; izquierdo2023) (DISCMINER workflow for planet location retrieval)
- Method: (cite: Phantom) (Phantom SPH code details)
- Method: (cite: Pinte2006; Pinte2009) (mcfost code)
- Companion: (cite: Teague_exoALMA) (Fiducial exoALMA beam and noise level)
- Companion: (cite: Pinte_exoALMA) (exoALMA planet candidates and detectable planet mass)
- Companion: (cite: Galloway_exoALMA) (Temperature structure inferred for exoALMA disks)
- Companion: (cite: Rosotti_exoALMA) (Gas surface density inferred for exoALMA disks)
- Related: exoALMA (ALMA large program 2021.1.01123.L)

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 63,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
