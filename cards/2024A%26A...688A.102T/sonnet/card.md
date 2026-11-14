# Orbital dynamics in the GG Tau A system: Investigating its enigmatic disc

`2024A&A...688A.102T` | Astronomy and Astrophysics 2024 | first author: Toci, Claudia | arXiv: 2404.07565 | DOI: 10.1051/0004-6361/202348470

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the most likely orbital configuration (coplanar vs misaligned) of the GG Tau A triple and its circumtriple disc, tested via new astrometry and SPH gas+dust simulations compared with ALMA 1.3 mm and SPHERE 1.67 micron images?  
  > "To determine the best orbital configuration of the GG Tau A system and its circumtriple disc, we provide new astrometric measures of the system and we run a set of hydrodynamical simulations" (abstract)
- Target **GG Tau A**: coordinates _not stated_; z/distance 145 pc  
  > "GG Tau is a hierarchical quintuple system located in the Taurus-Auriga star-forming region at a distance of 145 pc (cite: Galli19)" (GG Tau Aa/b); distance from Galli19  
  > "GG Tau is a hierarchical quintuple system located in the Taurus-Auriga star-forming region at a distance of 145 pc (cite: Galli19)" (GG Tau Aa/b)

## Data provenance

- ALMA projects: 2018.1.00532.S
- bands: Band 6 (1300 micron continuum)  
  > "archival ALMA Band 6 observations from project Project 2018.1.00532.S" (Observed features)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.31" x 0.25", PA=27 deg (beam used for convolution, as in Phuong 2020a)  
  > "0.31” $\times$ 0.25”, PA=27$^\circ$ for the 1300 $\mu$m emission (as in (cite: phuong2020b))" (Radiative transfer and synthetic observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival; PI Denis Alpizar, Otoniel  
  > "we use as reference the archival ALMA Band 6 observations from project Project 2018.1.00532.S (P.I. Denis Alpizar, Otoniel)" (Observed features)
- Other facility **Keck/NIRC2 and VLT/NaCo archives**: 2 micron imaging for six new astrometric epochs  
  > "we identified six new epochs of 2 $\mu$m imaging observations with Keck/NIRC2 and VLT/NaCo" (Archival observations and orbit analysis)
- Other facility **VLT/SPHERE (IRDIS) H band**: 1.67 micron scattered-light image from Keppler et al. 2020 used as comparison  
  > "1.67 $\mu$m image from (cite: keppler2020gap) (SPHERE/IRDIS observation, guaranteed-time observations GTO time, project 198.C-0209)" (Observed features)
- External data: ALMA Band 6 continuum image of GG Tau A (imaged and analysed in Phuong et al. 2020)  
  > "recently imaged and analysed in (cite: phuong2020b), calibrated using the ALMA pipeline reduction scripts provided with the raw data from the ALMA archive" (Observed features) [from (cite: phuong2020b)]
- External data: Total dynamical mass 1.41 +/- 0.08 Msun  
  > "The total dynamical mass of the system has been estimated in (cite: phuong2020b), and corresponds to $1.41 \pm 0.08$ M$_\odot$" (GG Tau Aa/b) [from (cite: phuong2020b)]
- Simulation/model as data: 4 PHANTOM SPH gas+dust simulations (coplanar 1/2, misaligned 1/2) post-processed with MCFOST  
  > "We run 4 SPH simulations with the `PHANTOM` code, two for the most probable coplanar configuration and two for the most probable misaligned one." (Simulations set)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline reduction scripts provided with archive raw data (as in Phuong et al. 2020a)  
  > "calibrated using the ALMA pipeline reduction scripts provided with the raw data from the ALMA archive" (Observed features)
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
- final beam: 0.31" x 0.25", PA=27 deg  
  > "0.31” $\times$ 0.25”, PA=27$^\circ$ for the 1300 $\mu$m emission (as in (cite: phuong2020b))" (Radiative transfer and synthetic observations)
- final rms: _not stated_

### Inherited from earlier work

- ALMA imaging/analysis of the 2018.1.00532.S data  
  > "recently imaged and analysed in (cite: phuong2020b)" (Observed features) [from (cite: phuong2020b)]
- Initial conditions following earlier simulations  
  > "following the parameters choice of (cite: cazzoletti2017) and (cite: aly2018secular)" (Methods) [from (cite: cazzoletti2017); (cite: aly2018secular)]

### Not stated but needed to reproduce (our reading)

- ALMA imaging parameters (weighting, robust, cleaning, rms) are not given; must be taken from Phuong et al. 2020
- How the observed ALMA image was registered and compared quantitatively (comparison is visual only)
- MCFOST wavelength/image grid settings and Voronoi cell numbers
- SPH snapshot output times and CaSh annulus width
- Observed continuum flux/rms values

## Analysis recipe

1. **Derive binary orbit from archival astrometry**: Relative astrometry by least-squares PSF fitting; orbit fit with orbitize! (ptemcee) and orbfit_lib  
  > "we employed the `orbitize!` package (cite: Blunt20) in combination with the parallel-tempered package `ptemcee` (cite: Vousden16)" (Archival observations and orbit analysis)
   - software: orbitize!, ptemcee, orbfit_lib
   - parameter: 10 temperatures, 100 walkers, 80000 steps, first half burn-in  
  > "We performed each fit with 10 temperatures and 100 walkers per temperature, advanced the chains 80000 steps, cut the first half as an extended burn-in" (Archival observations and orbit analysis)
   - assumption: Parallax fixed to 6.91 mas (L1551 mean)  
  > "We therefore fixed the parallax of the system to 6.91 mas, which is the mean estimate for the L1551 cloud (cite: Galli19)." (Archival observations and orbit analysis)
   - fitting: Uniform priors on e, omega, Omega, tau0; log-uniform a; sine-uniform i; Gaussian prior on total mass  
  > "we employ uniform ($e$, $\omega$, $\Omega$ and $\tau_0$), log-uniform ($a$) and sine-uniform ($i$) priors." (Archival observations and orbit analysis)
   - validation: Compared MCMC and least-squares results; chain inspection for convergence  
  > "Inspection of the chain evolution confirms that they have reached convergence." (Archival observations and orbit analysis)
2. **Run SPH gas+dust simulations**: 3D SPH with PHANTOM, one-fluid dust, sink-particle stars, coplanar and 30 deg misaligned orbits, evolved up to 3000/1500 orbits  
  > "We perform two sets of gas and dust 3D hydrodynamic simulations using the SPH (Smoothed Particle Hydrodynamics) code `PHANTOM`" (Numerical simulations)
   - software: PHANTOM
   - parameter: 1e6 SPH particles, Rout=800 au, disc mass 0.12 Msun, dust-to-gas 0.01, 1 mm grains, alpha_SS=0.005  
  > "The system is surrounded by a disc of 1$\times 10^6$ SPH particles" (Initial Conditions)
   - assumption: Locally isothermal, T=20 K (R/300 au)^-0.9; no disc self-gravity; no circumstellar discs  
  > "We neglect the disc self-gravity, as our disc mass results in a gravitationally stable disc." (Initial Conditions)
   - fitting: _not stated_
   - validation: Benchmarked against earlier gas-only results (Cazzoletti 2017, Aly 2018)  
  > "We summarise here previous findings for bench-marking our gas dynamics results in the overlapping parameter space" (Previous results)
3. **Measure cavity size and eccentricity**: CaSh computes cavity eccentricity and semi-major axis; cavity edge at 50% of peak surface density  
  > "the semi-major axis of the inner cavity is defined as the radius $R_{\textrm{mid}}$, at which the surface density becomes half its maximum value" (Long-term evolution)
   - software: CaSh
   - fitting: _not stated_
   - validation: _not stated_
4. **Synthetic images and comparison with ALMA/SPHERE**: MCFOST Monte Carlo RT at 1300 and 1.67 micron, convolved with observed beam, visually compared with ALMA Band 6 and SPHERE images  
  > "We post-process the selected snapshots of all the simulations using `MCFOST`" (Radiative transfer and synthetic observations)
   - software: MCFOST
   - parameter: 1.3e8 photon packets; d=145 pc; i=37 deg; PA=97 deg; dust mass fixed to 1e-3 Msun  
  > "we compute the temperature of our models by using $1.3 \times 10^8$ photon packets" (Radiative transfer and synthetic observations)
   - assumption: DIANA dust: 60% silicates, 15% amorphous carbon, 25% porosity; dn/da ∝ a^-3.5, amin 0.03 um, amax 3.5 mm; Mie+EMT  
  > "We assume a chemical composition of 60% silicates, 15% amorphous carbon, and 25% porosity (in volume ratios)" (Radiative transfer and synthetic observations)
   - fitting: _not stated_
   - validation: Visual comparison of cavity size, ring size, star position and streams  
  > "We conclude that the misaligned configuration on short times is the best match of GG Tau A." (What is the most likely configuration for GG Tau A?)

## Software

- **orbitize!** : MCMC orbit fit  
  > "we employed the `orbitize!` package (cite: Blunt20)" (Archival observations and orbit analysis)
- **ptemcee** : parallel-tempered sampler  
  > "parallel-tempered package `ptemcee` (cite: Vousden16)" (Archival observations and orbit analysis)
- **orbfit_lib** : least-squares orbit fit  
  > "we use the `orbfit_lib` procedure (cite: schaefer2006)" (Archival observations and orbit analysis)
- **PHANTOM** : SPH hydrodynamics  
  > "SPH (Smoothed Particle Hydrodynamics) code `PHANTOM` (cite: price2018phantom)" (Numerical simulations)
- **MCFOST** : radiative transfer synthetic images  
  > "`MCFOST` (cite: pinte2006monte), a Monte Carlo radiative transfer code" (Radiative transfer and synthetic observations)
- **CaSh** : cavity semi-major axis and eccentricity  
  > "using the numerical tool CaSh" (Long-term evolution)
- **pymcfost, plonk** : visualization  
  > "the following visualization tools: `pymcfost, plonk`" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Orbital period (orbitize!, 68%) | 199 | +67/-28 | yr | 1 | $P$ (yr)                  / 199 $^{+67}_{-28}$ |
| Eccentricity (orbitize!) | 0.22 | +0.06/-0.05 | dimensionless | 1 | $e$                       / 0.22 $^{+0.06}_{-0.05}$ |
| Semi-major axis (orbitize!) | 38 | +8/-3 | au | 1 | $a$ (au)                  / 38 $^{+8}_{-3}$ |
| Misalignment angle (orbitize!) | 12 | +11/-7 | deg | 1 | $\Delta\theta$ ($^\circ$) / 12 $^{+11}_{-7}$ |
| Coplanar cavity eccentricity at end of simulation (3500 orbits) | ~0.4 | not stated | dimensionless | 3 | At the end of our simulations, after 3500 orbits, the cavity eccentricity has grown up to $\sim 0.4$ |
| Misaligned short-timescale cavity size | ~180 | not stated | au | 3 | almost circular cavity of the size of 3 $a_{\rm{mis}}$, corresponding to $\sim 180$ au |

## Qualitative findings

- Astrometry alone cannot break degeneracy between coplanar and misaligned orbits, but modest misalignment is probable  
  > "are not capable of fully breaking the degeneracy between families of coplanar and misaligned orbits, but obtaining that a modest misalignment is probable" (abstract)

## Claim tuples

- H: Is the GG Tau A orbit coplanar or misaligned with the circumtriple ring? | E: Orbit fits to extended astrometry | R: Delta theta ~12 deg preferred by MCMC, but degeneracy remains | F: Modest misalignment likely, not conclusive | **partially**
- H: Which simulated configuration matches the ALMA and SPHERE morphology? | E: Compare synthetic MCFOST images of coplanar and misaligned snapshots with data | R: Misaligned on short timescales matches; coplanar fails at both times | F: Misaligned configuration (shorter than tau_ecc) is best match | **supported**
- H: Does disc eccentricity growth occur and conflict with observation? | E: Long-term evolution of both configurations | R: Cavity grows and becomes eccentric beyond tau_ecc, no longer matching | F: Either system younger than tau_ecc or growth suppressed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Astrometry does not constrain orbit, so simulation morphology compared to observations is used  
  > "As our new astrometric data points do not completely constrain the orbits of the system, we rely on the comparison between the morphology of the outcomes of numerical simulations and observations" (Numerical simulations)
- How they decided it was enough: _not stated_
- Limitation (authors): Models do not fully reproduce SPHERE morphology; comparison is qualitative, deferred to future work  
  > "We therefore defer to a future work a more quantitative characterisation of the observed features." (Observed features)
- Caveat (inferred, ours): Comparison with ALMA is visual, no quantitative metric
- Caveat (inferred, ours): Only one grain size and two orbits tested; a small parameter space
- Caveat (inferred, ours): Viscosity and tau_ecc dependence not explored
- Caveat (inferred, ours): Astrometric systematics from unresolved Ab1/Ab2

## Reproducibility

- Data public (paper): ALMA data archival, Keck and ESO archives  
  > "we use as reference the archival ALMA Band 6 observations from project Project 2018.1.00532.S" (Observed features)
- Products in archive: _not stated_
- Code: CaSh available on GitHub  
  > "CaSh is available at the following Github repository <https://github.com/si-mon-jinn/CaSh>." (footnote 7)
- Missing: ALMA imaging details
- Missing: Quantitative comparison metric
- Missing: Simulation snapshots/inputs
- Data volume (inferred): ALMA ~ tens of GB raw; simulations compute-heavy
- Score (inferred): 3/5, Simulation and orbit setup is well specified and public codes are used, but the ALMA part is minor and comparison is visual.
- Rediscovery candidate: no, Main results are simulations and visual comparisons; ALMA use is minor.

## Links

- Method: (cite: phuong2020b) (ALMA imaging of the data used)
- Method: (cite: cazzoletti2017) (simulation setup replicated)
- Companion: (cite: keppler2020gap) (SPHERE image and prior simulations)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 41,
  "rate": 0.526
 },
 "evidence_ok": true
}
```
