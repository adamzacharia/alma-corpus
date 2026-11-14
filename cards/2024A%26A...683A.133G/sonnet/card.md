# TIPSY: Trajectory of Infalling Particles in Streamers around Young stars. Dynamical analysis of the streamers around S CrA and HL Tau

`2024A&A...683A.133G` | Astronomy and Astrophysics 2024 | first author: Gupta, Aashish | arXiv: 2401.10403 | DOI: 10.1051/0004-6361/202348007

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Are observed streamer-like structures around S CrA and HL Tau consistent with infalling motion, and what are their dynamical parameters (energy, angular momentum, infall time, mass infall rate)?  
  > "In order to ascertain the infalling nature of observed streamer-like structures and then systematically characterize their dynamics, we developed the code TIPSY" (abstract)
- Target **S CrA**: coordinates _not stated_; z/distance 160 pc  
  > "| Distance \[pc\]               | 160   | 147    |" (Table 1); "Distance estimate for S CrA is based on *Gaia* DR3 parallax value (cite: gaiadr3)." (Stellar parameters for S CrA and HL Tau); distance from Gaia DR3 parallax  
  > "| Distance \[pc\]               | 160   | 147    |" (Table 1); "Distance estimate for S CrA is based on *Gaia* DR3 parallax value (cite: gaiadr3)." (Stellar parameters for S CrA and HL Tau)
- Target **HL Tau**: coordinates _not stated_; z/distance 147 pc  
  > "*Gaia* measurements were unavailable for HL Tau, so we used the estimate of the distance to its surrounding cloud, Lynds 155 (cite: Galli2018)." (Stellar parameters for S CrA and HL Tau); distance from distance to Lynds 155 cloud (Galli2018)  
  > "*Gaia* measurements were unavailable for HL Tau, so we used the estimate of the distance to its surrounding cloud, Lynds 155 (cite: Galli2018)." (Stellar parameters for S CrA and HL Tau)

## Data provenance

- ALMA projects: 2019.1.01792.S, 2016.1.00366.S
- bands: 13CO (2–1) for S CrA; HCO+ (3–2) for HL Tau  
  > "We present the fitting results for $^{13}$CO (2–1) data of S CrA and HCO$^{+}$ (3–2) data of HL Tau" (3 Applications)
- frequencies and spectral setup: channel width ~0.1 km/s for both datasets  
  > "The channel width (velocity resolution) for both the S CrA and HL Tau observations is $\sim0.1$ km s$^{-1}$" (4.1 Data requirements)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: HL Tau data reveal only ~300 au of streamer, limited by largest recoverable scale  
  > "limited by the largest recoverable scale, reveal only a $\sim300$ au part of streamer" (4.1 Data requirements)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 13CO 2–1 (not stated)
- Line: HCO+ 3–2 (not stated)
- Line: C18O 2–1 (not stated)
- External data: S CrA stellar mass (2 Msun total, 1 Msun each)  
  > "Stellar mass estimates for S CrA and HL Tau were taken from (cite: Gahm2018) and (cite: Yen2019), respectively." (Stellar parameters for S CrA and HL Tau) [from (cite: Gahm2018)]
- External data: HL Tau stellar mass and systemic velocity  
  > "For HL Tau, the systemic velocity derived by (cite: Yen2019) was used." (Stellar parameters for S CrA and HL Tau) [from (cite: Yen2019)]
- External data: Einstein A and Eu from LAMDA; partition function from CDMS  
  > "from the Leiden Atomic and Molecular Database (cite: lamda)" (4.2 Physical parameters) [from (cite: lamda); (cite: cdms)]
- External data: 13CO abundance 1.45e-6; HCO+ abundance 1e-9  
  > "$1.45\times10^{-6}$ for $^{13}$CO (cite: Huang2020) and $10^{-9}$ for HCO$^{+}$ (cite: jorgensen04)" (4.2 Physical parameters) [from (cite: Huang2020); (cite: jorgensen04)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: S CrA: standard pipeline calibrated data; HL Tau: self-calibrated data as in Yen2019  
  > "We used the standard pipeline calibrated data" (3.1 S CrA); "we used the same self-calibrated HCO$^{+}$ (3–2) ALMA observations" (3.2 HL Tau)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5 (S CrA)  
  > "the imaging was done using "Briggs" weighting with robust=0.5" (3.1 S CrA)
- uv taper: _not stated_
- cell size: 0.05 arcsec (S CrA)  
  > "a cell size of 0.05$''$" (3.1 S CrA)
- image size: _not stated_
- masking: auto-multithresh with default parameters (S CrA)  
  > ""auto-multithresh" masking with default parameters" (3.1 S CrA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HL Tau HCO+ (3–2) data reduction and self-calibration as in Yen2019  
  > "we used the same self-calibrated HCO$^{+}$ (3–2) ALMA observations (Project Id.: 2016.1.00366.S) of HL Tau as described in (cite: Yen2019)" (3.2 HL Tau) [from (cite: Yen2019)]
- Infall trajectory model  
  > "TIPSY fits theoretical trajectories expected for infalling gas, following the model given in (cite: Mendoza2009)" (2 Fitting methodology) [from (cite: Mendoza2009)]

### Not stated but needed to reproduce (our reading)

- Imaging details for HL Tau (beam, robust, cell, rms) and for S CrA beam/rms/image size
- Observing configurations, dates, integration times, beams
- Exact OPTICS parameters (min_samples, xi) and the default distance bin definition
- Parameter grid ranges and resolutions for LOS distance, POS speed, direction
- Continuum subtraction and line-free channels
- Streamer region definition beyond Table 1 limits
- CASA version

## Analysis recipe

1. **Isolate streamer emission**: Visually define sub-cube in RA, Decl., RV; remove pixels below sigma threshold; OPTICS clustering keeps biggest cluster  
  > "we visually examine the emission maps and define a boundary for a sub-cube that encompasses the streamer emission using RA, Decl., and RV limits." (2.2 Fitting procedure); "The biggest coherent cluster of emission in the selected sub-cube is identified as the streamer" (2.2 Fitting procedure)
   - software: TIPSY, scikit-learn
   - parameter: Significance level 3 sigma (S CrA), 4 sigma (HL Tau); limits in Table 1  
  > "| Significance ($\sigma$) level | 3     | 4      |" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reduce point cloud to curve**: Bin points by distance metric d=sqrt(r^2+(w r theta)^2) into ten bins; intensity-weighted means and standard deviations of RA, Decl., RV  
  > "we first divide the streamer points into several bins, set to ten by default, based on a distance metric." (2.2 Fitting procedure)
   - software: TIPSY
   - parameter: w=1 by default, 10 bins  
  > "is by default equal to one" (2.2 Fitting procedure)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit infall trajectories**: Grid over 3 free parameters (LOS separation, POS speed, POS direction) with Mendoza2009 trajectories; spline interpolation at distance metric; best fit = highest fraction within error bars, tie broken by lowest chi-squared  
  > "We consider the best-fit trajectory as the one that can accommodate the highest fraction of mean values representing the observed streamer, within their error bars." (2.2 Fitting procedure)
   - software: TIPSY, scipy
   - assumption: Only point-mass gravity of the protostar; stellar mass, distance, systemic velocity fixed  
  > "we consider only one force acting on the infalling material: the gravitational force of a point mass (protostar)." (2.4 Caveats)
   - assumption: Line intensity traces gas density  
  > "we also assume that the observed intensity of molecular-line emission represents the actual density distribution of gas." (2.4 Caveats)
   - fitting: Grid search, no sampler; goodness = fitting fraction and chi-squared  
  > "We consider the best-fit trajectory as the one that can accommodate the highest fraction of mean values representing the observed streamer, within their error bars. In cases where multiple trajectories fit the same fraction of values, we choose the trajectory with the lowest chi-squared deviation" (Fitting procedure)
   - validation: Implementation compared with two-body REBOUND simulations  
  > "were also validated through two-body simulations using the REBOUND framework" (2.1 Physical model)
4. **Estimate uncertainties**: Std of parameters among trajectories with fitting fraction >=0.9, floored at grid resolution; propagated to derived quantities  
  > "the errors are estimated as the standard deviations of each parameter for these parameter combinations with sufficiently good fits (fitting fraction greater $\geq 0.9$)." (2.3 Error estimation)
   - software: TIPSY
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive energies, angular momentum, infall time**: Specific kinetic and potential energy, r0 x v0, infall time to closest approach from best-fit trajectory  
  > "specific (per unit mass) kinetic energy can be estimated as $0.5\times(v_{RA}^{2}+v_{Decl.}^{2}+v_{LOS}^{2})$." (4.2 Physical parameters)
   - software: TIPSY
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate streamer mass and infall rate**: Optically thin lower-limit mass from integrated flux (Bergin2013 formula); Mdot = M_streamer / T_inf  
  > "estimate mass infall rates as $\dot{M}_{inf}=M_{streamer}/T_{inf}$" (4.2 Physical parameters)
   - parameter: A=6.038e-7 s^-1, Eu=15.87 K (13CO); A=1.453e-3 s^-1, Eu=25.68 K (HCO+); Q=19.6, 12.0 at 25 K  
  > "were 19.6 and 12.0 for $^{13}$CO and HCO$^{+}$, respectively" (4.2 Physical parameters)
   - assumption: T=25 K, abundances 1.45e-6 (13CO), 1e-9 (HCO+), optically thin  
  > "For both sources, we assumed a representative temperature of 25 K" (4.2 Physical parameters)
   - fitting: _not stated_
   - validation: Treated as order-of-magnitude estimates  
  > "these values should be treated as an order of magnitude estimates" (4.2 Physical parameters)

## Software

- **TIPSY** : fit infall trajectories to streamers  
  > "we have developed the code Trajectory of Infalling Particles in Streamers around Young Stars (TIPSY)" (1 Introduction)
- **scikit-learn (OPTICS)** : cluster removal of unrelated emission  
  > "we use the sklearn (cite: scikit-learn) implementation of the Ordering Points To Identify the Clustering Structure" (2.2 Fitting procedure)
- **scipy** : first-order spline interpolation  
  > "We use the first-order spline interpolation, as implemented in scipy (cite: scipy)" (2.2 Fitting procedure)
- **REBOUND** : two-body validation of trajectories  
  > "validated through two-body simulations using the REBOUND framework" (2.1 Physical model)
- **CASA tclean (auto-multithresh)** : imaging of S CrA with auto-multithresh masking  
  > ""auto-multithresh" masking with default parameters" (3.1 S CrA)
- **Astropy** : general analysis  
  > "This work made use of Astropy" (Acknowledgements)
- **TRIVIA and Plotly** : 3D plots  
  > "The three-dimensional plots were made using TRIVIA" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S CrA specific total energy | -1.1 | 0.1 | km^2 s^-2 | 5 | of $-1.1\pm0.1$ km$^{2}$ s$^{-2}$ |
| S CrA specific angular momentum | 791 | 218 | AU km/s | 5 | / Specific angular momentum \[AU km / s\] / 791$\pm$218 / 606$\pm$1803 / |
| HL Tau specific angular momentum | 606 | 1803 | AU km/s | 5 | / Specific angular momentum \[AU km / s\] / 791$\pm$218 / 606$\pm$1803 / |
| Infall time S CrA | 8301 | 1358 | yr | 5 | We found infall timescales of $8301\pm1358$ yr and $2724\pm1237$ yr |
| Infall time HL Tau | 2724 | 1237 | yr | 5 | We found infall timescales of $8301\pm1358$ yr and $2724\pm1237$ yr |
| Streamer mass S CrA (lower limit) | >=2.1e-4 | not stated | Msun | 6 | $\gtrsim2.1\times10^{-4}$ M$_{\odot}$ and $\gtrsim1.2\times10^{-5}$ M$_{\odot}$ for S CrA and HL Tau |
| Streamer mass HL Tau (lower limit) | >=1.2e-5 | not stated | Msun | 6 | $\gtrsim2.1\times10^{-4}$ M$_{\odot}$ and $\gtrsim1.2\times10^{-5}$ M$_{\odot}$ for S CrA and HL Tau |
| Mass infall rate S CrA | >=2.5e-8 (>=27 MJup/Myr) | not stated | Msun/yr | 6 | $\gtrsim2.5\times10^{-8}$ M$_{\odot}$ yr$^{-1}$ (or $\gtrsim27$ M$_{jupiter}$ Myr$^{-1}$) for S CrA |
| Mass infall rate HL Tau | >=4.5e-9 (>=4.7 MJup/Myr) | not stated | Msun/yr | 6 | $\gtrsim4.5\times10^{-9}$ M$_{\odot}$ yr$^{-1}$ (or $\gtrsim4.7$ M$_{jupiter}$ Myr$^{-1}$) for HL Tau |
| Integrated streamer flux S CrA | 1.3e-20 | not stated | W m^-2 | 6 | $1.3\times10^{-20}$ W m$^{-2}$ for S CrA and $4.2\times10^{-21}$ W m$^{-2}$ for HL Tau |

## Qualitative findings

- HL Tau fit is poorly constrained because only ~300 au of streamer is covered; recoverable scales >~1000 au are better  
  > "This suggests that observations with higher recoverable scales ($\gtrsim$1000 au) are better for constraining streamer dynamics." (4.1 Data requirements)

## Claim tuples

- H: S CrA streamer is infalling gas on a bound trajectory | E: TIPSY fit to 13CO (2–1) PPV streamer | R: All ten curve points fit; total energy -1.1±0.1 km^2/s^2 | F: Bound elliptical infall, not ejection or disk spiral | **supported**
- H: HL Tau streamer is consistent with infall | E: TIPSY fit to HCO+ (3–2) | R: All points fit; kinetic ≈ potential energy but large uncertainties | F: Consistent with roughly parabolic infall, poorly constrained | **partially**
- H: Streamers can add significantly to planet-forming mass budget | E: Lower-limit streamer masses divided by infall times | R: ≳27 and ≳5 MJup/Myr | F: Could increase mass budget significantly if sustained | **partially**

## Reasoning

- Why this data: 13CO chosen over 12CO because 12CO suffers cloud absorption and contamination  
  > "most of the streamers have been serendipitously observed in bright $^{12}$CO emission and generally suffer from significant cloud absorption and contamination." (3 Applications)
- Why this method: _not stated_
- Alternative: Ejection and gravitational-instability spiral rejected for S CrA via negative energy and large size  
  > "further indicate that this is not a spiral arm induced by gravitationally unstable disk." (3.1 S CrA)
- How they decided it was enough: _not stated_
- Limitation (authors): Errors in fixed parameters not propagated; mass estimates are lower limits and order of magnitude  
  > "TIPSY does not currently propagate errors in the fixed parameters to the errors of fitted parameters." (2.3 Error estimation)
- Caveat (inferred, ours): Uncertainties from the std of good-fit grid points are not formal confidence intervals
- Caveat (inferred, ours): S CrA binary tidal forces ignored although the inner velocity profile is not reproduced
- Caveat (inferred, ours): Fixed mass and distance errors not propagated; mass rate relies on assumed T and abundances

## Reproducibility

- Data public (paper): Project codes given; code on GitHub  
  > "https://github.com/AashishGpta/TIPSY" (footnote)
- Products in archive: _not stated_
- Code: TIPSY at https://github.com/AashishGpta/TIPSY  
  > "https://github.com/AashishGpta/TIPSY" (footnote)
- Missing: Grid ranges/resolution and OPTICS settings
- Missing: HL Tau imaging/self-cal products from Yen2019
- Missing: Beam and rms values
- Data volume (inferred): ~50-200 GB raw for two projects; small if using calibrated cubes
- Score (inferred): 3/5, Code is public and method well described, but imaging details and grid settings are partly missing, and HL Tau data are self-calibrated products from another paper.
- Rediscovery candidate: no, HL Tau data depend on Yen2019 self-calibration, and the grid parameters are unstated.

## Links

- Method: (cite: Mendoza2009) (Infall trajectory equations)
- Method: (cite: Ulrich1976) (UCM model basis)
- Companion: (cite: Gupta2023) (Original S CrA streamer detection in 12CO)
- Companion: (cite: Yen2019) (HL Tau streamer analysis and data)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 46,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
