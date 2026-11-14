# ALMA discovery of a rotating SO/SO<SUB>2</SUB> flow in HH212. A possible MHD disk wind?

`2017A&A...607L...6T` | Astronomy and Astrophysics 2017 | first author: Tabone, B. | arXiv: 1710.01401 | DOI: 10.1051/0004-6361/201731691

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Do SO and SO2 around the HH212 SiO jet show rotation consistent with an MHD disk wind, and what launch radii and magnetic lever arm does this imply?  
  > "We compare the observations with synthetic predictions for extended DWs to constrain the possible range of launch radii and magnetic lever arm" (Introduction)
- Target **HH212**: coordinates RA(J2000)=05h43m51.41s, Dec=-01d02m53.17s (continuum peak)  
  > "Positions are given with respect to the continuum peak at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17 (Lee et al. 2014)" (2 Observations); "(for $d$ = 450 pc)" (Introduction); z/distance d = 450 pc  
  > "Positions are given with respect to the continuum peak at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17 (Lee et al. 2014)" (2 Observations); "(for $d$ = 450 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01475.S
- bands: Band 7  
  > "HH212 was observed in Band 7 with ALMA between 6 October and 26 November 2016 (Cycle 4)" (2 Observations)
- frequencies and spectral setup: SO2 at 1 km/s resolution; other lines 0.1 km/s rebinned to 0.44 km/s  
  > "The SO$_2$($8_{2,6}-7_{1,7}$) line at 334.67335GHz was observed with a spectral resolution of 1km s$^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 44 antennas  
  > "using 44 antennas of the 12-m array with a maximum baseline of 3 km" (2 Observations)
- configurations: _not stated_
- baselines: maximum 3 km  
  > "using 44 antennas of the 12-m array with a maximum baseline of 3 km" (2 Observations)
- angular resolution: 0.19x0.17 arcsec (C34S, natural); 0.15x0.13 arcsec (others)  
  > "resulting in a beam of 0.15” $\times$ 0.13” (PA $\sim$ -89$^{\circ}$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 1 mJy/beam in SO2 (1 km/s channels); 1.5 mJy/beam in 0.44 km/s channels for other lines  
  > "The rms noise level is $\sigma \sim$ 1 mJy/beam in SO$_2$ in 1 km s$^{-1}$ channels" (2 Observations)
- time on source: _not stated_
- observing dates: 6 October to 26 November 2016  
  > "HH212 was observed in Band 7 with ALMA between 6 October and 26 November 2016 (Cycle 4)" (2 Observations)
- pi or archival as stated: PI: C. Codella (ALMA 2016.1.01475.S)  
  > "This paper makes use of the ALMA 2016.1.01475.S data (PI: C. Codella)." (Acknowledgements)
- Line: SO2 8(2,6)-7(1,7) (334.67335 GHz)
- Line: SO 9(8)-8(7) (346.52848 GHz)
- Line: SiO 8-7 (347.33063 GHz)
- Line: C34S 7-6 (337.39669 GHz)
- Line: C17O 3-2 (337.06113 GHz)
- External data: ALMA SiO data of HH212 jet knots, used for comparison with models  
  > "compared with the ALMA SiO data of (cite: 2017NatAs...1E.152L)" (3.2 Comparison with MHD disk wind models) [from (cite: 2017NatAs...1E.152L)]
- External data: Inclination i ~ 87 deg and stellar mass 0.2 Msun  
  > "we kept a fixed inclination $i = 87\ensuremath{^\circ}$ and stellar mass $M_\star = 0.2M_\odot$ (cite: 2017ApJ...843...27L)" (3.2 Comparison with MHD disk wind models) [from (cite: 2017ApJ...843...27L)]
- External data: Keplerian disk radius of 40 au  
  > "the expected radius of the Keplerian disk, namely 40 au (cite: 2017ApJ...843...27L)" (3.2 Comparison with MHD disk wind models) [from (cite: 2017ApJ...843...27L)]

## Processing

### Calibration

- pipeline or manual: standard procedures in CASA  
  > "Calibration was carried out following standard procedures under the CASA environment" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural for C34S; robust 0.5 for other lines  
  > "natural weighting for C$^{34}$S to increase sensitivity" (2 Observations)
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

- Disk wind model computed following the equations of Casse & Ferreira  
  > "calculated following the equations described in (cite: 2000A&A...353.1115C)" (3.2 Comparison with MHD disk wind models) [from (cite: 2000A&A...353.1115C)]
- Continuum peak position and systemic velocity 1.7 km/s  
  > "velocities are with respect to a systemic velocity $V_{\rm sys}$ = 1.7 km s$^{-1}$(cite: 2014ApJ...786..114L)" (2 Observations) [from (cite: 2014ApJ...786..114L)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Spectral windows and line-free channels / continuum subtraction
- Imaging parameters (cell, size, masks, deconvolver)
- Flux calibrator choice and flux scale uncertainty
- Self-calibration
- Model grid details (alpha values, abundance normalization, line-of-sight integration, how best fit chosen)
- Distance source for 450 pc
- PV cut widths and extraction details in GILDAS
- Number of executions and time on source

## Analysis recipe

1. **Image the lines and inspect morphology and rotation**: Channel maps, transverse shifts of redshifted vs blueshifted emission, PV cuts and line profiles at +-70 au from midplane  
  > "Figure [2](#fig:pv) shows transverse position-velocity (PV) cuts and line profiles of SO$_2$ and SO at $\pm 70$ au from the midplane" (3.1 Evidence for a rotating wide-angle flow)
   - software: CASA, GILDAS
   - assumption: Inclination i ~ 87 deg for deprojecting speeds  
  > "yields a mean deprojected speed of $V_p \simeq 20-40$km s$^{-1}$ for an inclination $i \simeq 87\ensuremath{^\circ}$" (3.1 Evidence for a rotating wide-angle flow)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare with self-similar MHD disk wind models**: Synthetic cubes from steady-state, axisymmetric, self-similar DW with power-law emissivity r^alpha, convolved with clean beam, compared to PV cuts and line profiles  
  > "Synthetic data cubes were then computed assuming optically thin emission and a velocity dispersion of $0.6$ km s$^{-1}$" (3.2 Comparison with MHD disk wind models)
   - parameter: lambda and W=r_max/r0; r_in, r_out; alpha  
  > "The minimum and maximum launch radii, $r_{\rm in}$ and $r_{\rm out}$, then determine the range of velocities in the wind" (3.2 Comparison with MHD disk wind models)
   - assumption: Fixed i=87 deg, M*=0.2 Msun, optically thin, 0.6 km/s dispersion, power-law emissivity  
  > "we kept a fixed inclination $i = 87\ensuremath{^\circ}$ and stellar mass $M_\star = 0.2M_\odot$" (3.2 Comparison with MHD disk wind models)
   - fitting: Visual comparison; alpha constrained by slope of line wings; no formal fit stated  
  > "For a given MHD solution, the value of $\alpha$ is well constrained by the slope of the line profile wings." (3.2 Comparison with MHD disk wind models)
   - validation: Same solution also reproduces SiO knot rotation from Lee et al. 2017a  
  > "the same DW solution that fits the SO and SO$_2$ PV cuts can also reproduce the rotation signatures across axial SiO knots" (3.2 Comparison with MHD disk wind models)

## Software

- **CASA** : Calibration and spectral line imaging  
  > "Spectral line imaging was performed in CASA with natural weighting for C$^{34}$S" (2 Observations)
- **GILDAS** : Further data analysis  
  > "Further data analysis was performed using the GILDAS[^1] package." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Transverse shift between red and blue SO2 emission at +-2 km/s | ~0.05 | not stated | arcsec | 1 | a transverse shift $\simeq \pm 0.05\ensuremath{''}$ between redshifted and blueshifted emission at $\pm$ 2km s$^{-1}$ from systemic |
| Mean deprojected speed | 20-40 | not stated | km/s | 1 | yields a mean deprojected speed of $V_p \simeq 20-40$km s$^{-1}$ |
| Best-fit lever arm lambda | 5.5 | not stated | dimensionless | 2 | we could obtain a good fit for a slower MHD solution with $\lambda = 5.5$ and ${\mathcal{W}}$ = 30 |
| Best-fit r_out | 40 | not stated | au | 2 | the more extended emission is better reproduced if we increase $r_{\rm out}$ to the expected radius of the Keplerian disk, namely 40 au |
| r_in from blue wing | <=0.1 | not stated | au | 2 | the extent of the blue wing suggests $r_{\rm in} \leq 0.1$ au |
| SiO knot launch radii r_out | 0.2-0.3 | not stated | au | 2 | our best fitting $r_{\rm out} \simeq 0.2-0.3$ au for SiO knots |
| Mass ejection fraction of accretion flow | 50% | not stated | percent | 2 | it would be ejecting 50% of the incoming accretion flow |

## Qualitative findings

- Chemical stratification: SiO traces the jet, C34S the cavity walls, C17O the rotating envelope and disk  
  > "SiO traces the narrow high-velocity jet, while C$^{34}$S outlines the dense walls of a broad outflow cavity, and C$^{17}$O traces the rotating equatorial envelope and disk." (3.1 Evidence for a rotating wide-angle flow)
- Apparent velocity gradient underestimates r_out via the Anderson formula, due to superposed flow surfaces  
  > "the superposition of many flow surfaces along the line of sight creates a shallower velocity gradient leading to strongly underestimate $r_{\rm out}$" (3.3 Biases in analytical estimates of DW outer launch radius)

## Claim tuples

- H: Is there a rotating wide-angle outflow in SO/SO2 around the SiO jet in HH212? | E: Cycle 4 ALMA imaging of SO, SO2, PV cuts | R: Transverse shifts ~0.05 arcsec, tilted PV cuts, deprojected speed 20-40 km/s | F: A rotating slower wide-angle flow carves the cavity rather than a fast wind | **supported**
- H: Can an MHD disk wind reproduce the kinematics? | E: Self-similar DW synthetic PV cuts compared to data | R: Good fit with lambda=5.5, W=30, r_out=40 au; lambda=13 too fast | F: lambda <~ 5 and launch radii 0.05 to ~40 au | **partially**
- H: Does the Anderson formula recover r_out? | E: Compare model r_out to formula estimate | R: Formula gives ~1 au vs 40 au | F: Apparent rotation gradient strongly underestimates r_out | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: DG Tau lambda=13 solution rejected as too fast for HH212  
  > "the DW solution with $\lambda = 13$ used to fit the DG Tau jet in (cite: 2004A&A...416L...9P) is too fast to reproduce the HH212 data" (3.2 Comparison with MHD disk wind models)
- How they decided it was enough: _not stated_
- Limitation (authors): Modeling is idealized, illustrative and probably not unique  
  > "We nevertheless caution that our modeling is very idealized and probably not unique." (Conclusions)
- Limitation (authors): Self-similarity cannot treat outer truncation  
  > "Notably, self-similarity cannot properly treat the effect of outer truncation." (3.5 Further model tests and limitations)
- Caveat (inferred, ours): Model fits are by eye with no formal uncertainties
- Caveat (inferred, ours): Power-law emissivity replaces chemistry
- Caveat (inferred, ours): Red lobe fit poor
- Caveat (inferred, ours): Rotation signature is a 0.05 arcsec shift, below the beam

## Reproducibility

- Data public (paper): Project code given with PI; public status not stated  
  > "This paper makes use of the ALMA 2016.1.01475.S data (PI: C. Codella)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Disk wind synthetic cube code not released
- Missing: Model grid and fit details
- Missing: CASA version and imaging details
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 3/5, Data identified, but imaging details are sparse and model code and fitting are not described in reproducible detail.
- Rediscovery candidate: no, Model-comparison results are by-eye and the model code is not available.

## Links

- Method: (cite: 2000A&A...353.1115C) (Equations for the self-similar MHD disk wind solutions)
- Companion: (cite: 2017NatAs...1E.152L) (SiO jet rotation in HH212, data compared here)
- Companion: (cite: 2017ApJ...843...27L) (HH212 disk and infall properties)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 33,
  "rate": 0.516
 },
 "evidence_ok": true
}
```
