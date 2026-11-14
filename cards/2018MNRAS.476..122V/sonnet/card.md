# An ALMA view of star formation efficiency suppression in early-type galaxies after gas-rich minor mergers

`2018MNRAS.476..122V` | Monthly Notices of the Royal Astronomical Society 2018 | first author: van de Voort, Freeke | arXiv: 1801.08140 | DOI: 10.1093/mnras/sty228

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Is the strongly suppressed star formation efficiency in ETGs after gas-rich minor mergers caused by dynamically unrelaxed molecular gas stabilizing against collapse?  
  > "It is possible that star formation is suppressed due to the fact that the gas brought in by the minor merger is not dynamically relaxed." (4 Discussion and conclusions)
- Target **Six dust lane ETGs (2MASXJ0903, 2MASXJ1416, NGC4797, 2MASXJ1301, 2MASXJ1333, CGCG013-092)**: coordinates _not stated_; z/distance z = 0.026-0.082; D_L = 106-315 Mpc  
  > "The properties of our target galaxies are taken from (cite: Davis2015) and presented in Table" (Table 1 (galaxy properties)); distance from Davis2015 (cite), H0=71 cosmology  
  > "The properties of our target galaxies are taken from (cite: Davis2015) and presented in Table" (Table 1 (galaxy properties))

## Data provenance

- ALMA projects: 2015.1.00320.S
- bands: _not stated_
- frequencies and spectral setup: 1850 MHz window on CO(1-0), ~1600 km/s coverage, ~1.0 km/s raw resolution; three 2 GHz continuum windows  
  > "A 1850 MHz correlator window was placed over the CO(1–0) line, yielding a continuous velocity coverage of about $1600$ km s$^{-1}$ with a raw velocity resolution of $\approx1.0$ km s$^{-1}$." (2.2 ALMA data)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, compact configuration  
  > "ALMA’s 12 m antennas were used in a compact configuration, resulting in an approximately 1$''$ beam" (2.2 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: ≈30-40″  
  > "sensitivity to emission on scales up to $\approx30-40\ensuremath{''}$" (2.2 ALMA data)
- sensitivity: _not stated_
- time on source: 27-63 min per source  
  > "2MASXJ13333299+2616190 | 2016-05-04 | 27.15" (Table 2)
- observing dates: 2016-03-19 to 2016-05-04  
  > "2016-03-19" (Table 2)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **IRAM 30m**: Previous CO(1-0) fluxes used for selection and comparison  
  > "we selected the six galaxies with the lowest SFEs based on previous Institut de Radioastronomie Millimétrique (IRAM) 30 m data (cite: Davis2015)." (2.1 Sample)
- Other facility **DECaLS/SDSS**: Optical images  
  > "using the Dark Energy Camera Legacy Survey (DECaLS; (cite: DECaLS2016); in bands $grz$), when available" (2.1 Sample)
- External data: Redshift, distance, stellar mass, SFR (MAGPHYS), M_H2, SFE  
  > "The properties of our target galaxies are taken from (cite: Davis2015) and presented in Table" (2.1 Sample) [from Davis2015]
- External data: ATLAS3D relaxed ETG R_CO/R25=0.16 and KS data  
  > "the radius of the molecular gas disc normalized by the radius of the 25 mag arcsec$^{−2}$ isophote in the $B$ band is $R_\mathrm{CO}/R_{25}=0.16$ (cite: Davis2013)" (3 Results) [from Davis2013; Davis2014]
- External data: Far-infrared fluxes for continuum interpretation  
  > "By comparing to the far-infrared fluxes from (cite: Rowlands2012)" (2.4 Continuum) [from Rowlands2012]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline by regional centre staff  
  > "The raw ALMA data were calibrated using the standard ALMA pipeline, provided by the ALMA regional centre staff." (2.2 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA; cubes binned to 10 km/s  
  > "In this work we bin the raw data to a channel width of 10 km s$^{-1}$ and use pixels of 0.3$''$" (2.2 ALMA data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "The data presented here were produced using Briggs weighting with a robust parameter of 0.5." (2.2 ALMA data)
- uv taper: _not stated_
- cell size: 0.3″  
  > "use pixels of 0.3$''$" (2.2 ALMA data)
- image size: _not stated_
- masking: Interactive masks on source emission; clean to RMS of dirty channels  
  > "cleaned in regions of source emission (identified interactively) to a threshold equal to the root-mean-square (RMS) noise of the dirty channels." (2.2 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB in uv plane if continuum present  
  > "we subtracted the continuum from the line data in the $uv$ plane using the CASA task UVCONTSUB." (2.2 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ≈1.0-2.35″ (e.g. 1.91×1.32″ to 2.35×1.03″)  
  > "1.62$\times$1.31" (Table 2)
- final rms: 0.8-1.5 mJy/beam in 10 km/s channels  
  > "the RMS noise reached in 10 km s$^{-1}$ channels" (2.3 Line detections)

### Inherited from earlier work

- Galaxy properties and Galactic X_CO molecular masses  
  > "The properties of our target galaxies are taken from (cite: Davis2015)" (2.1 Sample) [from (cite: Davis2015)]
- 10 Msun/pc^2 surface brightness limit for disc radius  
  > "which is the surface brightness limit used by (cite: Davis2013)" (3 Results) [from (cite: Davis2013)]

### Not stated but needed to reproduce (our reading)

- Continuum-free channel ranges and CASA version
- Number of clean iterations/beam handling details
- MCMC priors, sampler settings, and convergence criteria in KinMS_MCMC
- Method for computing Q uncertainties and dynamical time
- Exact area definition for KS surface densities

## Analysis recipe

1. **Image CO(1-0) cubes**: CASA imaging, Briggs robust 0.5, 10 km/s channels, 0.3″ pixels, uvcontsub, clean to dirty RMS  
  > "The data presented here were produced using Briggs weighting with a robust parameter of 0.5." (2.2 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared ALMA spectra with IRAM 30m fluxes; consistent  
  > "The total flux is consistent within uncertainties, which indicates that we are likely not resolving out any structure on large scales." (3 Results)
2. **Kinematic modelling of gas discs**: Forward model data cubes with KinMS coupled to MCMC; arctangent rotation curve; exponential surface brightness profile; constant dispersion  
  > "We used the KINematic Molecular Simulation (KinMS) tool (cite: Davis2013), with which we produce mock observations of a theoretical gas distribution" (3.1 Kinematic modelling)
   - software: KinMS, KinMS_MCMC
   - parameter: Fit v_circ,flat, r_norm, flux, centre, systemic velocity, PA, inclination, profile, dispersion  
  > "We furthermore fit the total flux, kinematic centre, systemic velocity, position angle, and inclination of the gas disc." (3.1 Kinematic modelling)
   - assumption: Circularly symmetric disc  
  > "We assume that the gas is in a circularly symmetric disc" (3.1 Kinematic modelling)
   - fitting: MCMC giving full Bayesian posterior; priors not stated  
  > "explore the parameter range with the Markov Chain Monte Carlo (MCMC) code KinMS_MCMC" (3.1 Kinematic modelling)
   - validation: Repeated with SDSS/Spitzer-based rotation curves; similar best fits  
  > "found best fit values similar to those using the arctangent model" (3.1 Kinematic modelling)
3. **Toomre Q and merger ages**: Q=κσ/(πGΣ) with κ from arctangent model; t_merge=5 t_dyn at undisturbed/disturbed transition  
  > "we therefore assume $t_\mathrm{merge}\approx5t_\mathrm{dyn}$" (3.1 Kinematic modelling)
   - assumption: Canonical σ=8 km/s alternative; eccentricity 0.2  
  > "a canonical $\sigma_\mathrm{gas}=8$ km s$^{-1}$" (3.1 Kinematic modelling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Kennicutt-Schmidt comparison**: Divide SFR and M_H2 by area of relaxed disc (3×RMS) or total gas, assuming axisymmetry  
  > "This is calculated by dividing the SFR and $M_\mathrm{H_2}$ by the area of the molecular gas disc." (3.2 Kennicutt-Schmidt relation)
   - assumption: Galactic X_CO  
  > "The molecular masses used here assume a Galactic $X_\mathrm{CO}$ factor" (2.2 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging and UVCONTSUB  
  > "We then used the Common Astronomy Software Applications (CASA) package to image the resulting visibility files" (2.2 ALMA data)
- **KinMS** : Mock cube kinematic modelling  
  > "We used the KINematic Molecular Simulation (KinMS) tool" (3.1 Kinematic modelling)
- **KinMS_MCMC** : MCMC fitting of data cubes  
  > "explore the parameter range with the Markov Chain Monte Carlo (MCMC) code KinMS_MCMC that couples to the KinMS routines in order to get the full Bayesian posterior probability distribution." (Kinematic modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity dispersion range (upper limits) | 6-40 | upper limits | km/s | 2 | The resulting velocity dispersions of the molecular gas are relatively high ($16-40$ km s$^{-1}$), except in galaxy 2MASXJ1333 (6 km s$^{-1}$ |
| Merger ages | 39-171 | not stated | Myr | 3 | we derive (minor) merger ages between 39 and 171 Myr |
| Mean R_CO/R25 undisturbed | 0.28 | not stated | dimensionless | 2 | we find an average $R_\mathrm{CO}/R_{25}=0.28$ |
| Mean R_CO/R25 including disturbed gas | 0.53 | not stated | dimensionless | 2 | this increases to $R_\mathrm{CO}/R_{25}=0.53$ |

## Qualitative findings

- Five of six galaxies show detached clouds, warps or asymmetries; only 2MASXJ1333 appears relaxed  
  > "Only galaxy 2MASXJ1333 shows no sign of asymmetries." (3 Results)

## Claim tuples

- H: Gas from minor mergers is dynamically unrelaxed | E: Resolved CO(1-0) imaging and kinematic modelling | R: Most galaxies show disturbances | F: Supports dynamical suppression of SFE | **supported**
- H: Galaxies lie below KS relation | E: Compute Σ_SFR vs Σ_gas | R: Much lower Σ_SFR at fixed Σ_gas | F: Strong suppression vs spirals and relaxed ETGs | **supported**
- H: Toomre Q discriminates stability | E: Kinematic Q | R: Q>1 mostly, similar to spirals | F: Q not discriminating; edge-on degeneracies | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: AGN/supernova feedback disfavoured  
  > "We therefore disfavour the explanation that AGN feedback (or supernova feedback) could be responsible for the abnormally low SFEs." (4 Discussion and conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Edge-on geometry gives degenerate, upper-limit velocity dispersions  
  > "We therefore consider our values upper limits to the true velocity dispersion of the gas." (3.1 Kinematic modelling)
- Caveat (inferred, ours): Galactic X_CO assumed; SFR timescale of ~100 Myr comparable to merger ages
- Caveat (inferred, ours): Merger age scaling 5 t_dyn is rough
- Caveat (inferred, ours): Axisymmetric models ignore disturbed gas

## Reproducibility

- Data public (paper): Programme code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00320.S" (Acknowledgements)
- Products in archive: _not stated_
- Code: KinMS on GitHub  
  > "https://github.com/TimothyADavis/KinMS" (footnote)
- Missing: MCMC priors/settings
- Missing: CASA version
- Missing: Line-free channels
- Missing: Rotation-curve and Q computation details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data and main settings are given but fitting details and some processing are missing.
- Rediscovery candidate: no, Fitting priors and processing details are missing.

## Links

- Method: Davis2013 (KinMS code)
- Companion: Davis2015 (Source sample, IRAM data and galaxy properties)
- Related: ATLAS3D
- Related: Galaxy Zoo

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
