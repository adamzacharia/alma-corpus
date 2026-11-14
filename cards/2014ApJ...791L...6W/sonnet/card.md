# ALMA Hints at the Presence of two Companions in the Disk around HD 100546

`2014ApJ...791L...6W` | The Astrophysical Journal Letters 2014 | first author: Walsh, Catherine | arXiv: 1405.6542 | DOI: 10.1088/2041-8205/791/1/L6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the gas and dust structures of the HD 100546 disk at (sub)mm wavelengths, and do they indicate companions or a protoplanet?  
  > "We present ALMA observations of the HD 100546 disk which resolve the gas and dust structure at (sub)mm wavelengths." (abstract)
- Target **HD 100546**: coordinates RA 11h33m25.44058s, Dec -70d11m41.2363s (J2000)  
  > "HD 100546 is a 2.4$\mathrm{M}_\odot$ B9V Herbig Be star located at 103$\pm$6 pc" (HD 100546); "$\alpha_{2000}$ = 11$^\mathrm{h}$ 33$^\mathrm{m}$ 25.44058s" (4 OBSERVATIONS); z/distance 103±6 pc  
  > "HD 100546 is a 2.4$\mathrm{M}_\odot$ B9V Herbig Be star located at 103$\pm$6 pc" (HD 100546); "$\alpha_{2000}$ = 11$^\mathrm{h}$ 33$^\mathrm{m}$ 25.44058s" (4 OBSERVATIONS); distance from van den Ancker et al. 1998; Grady et al. 2001  
  > "HD 100546 is a 2.4$\mathrm{M}_\odot$ B9V Herbig Be star located at 103$\pm$6 pc" (HD 100546); "$\alpha_{2000}$ = 11$^\mathrm{h}$ 33$^\mathrm{m}$ 25.44058s" (4 OBSERVATIONS)

## Data provenance

- ALMA projects: 2011.0.00863.S
- bands: Band 7  
  > "The source was observed in seven spectral windows in Band 7" (OBSERVATIONS)
- frequencies and spectral setup: 7 spws, 469 MHz bandwidth each, 0.122 MHz channels; centres 300.506, 301.286, 303.927 GHz (execution 1) and 344.311, 345.798, 346.998, 347.331 GHz (execution 2)  
  > "The central frequencies in each spectral window are 300.506, 301.286, and 303.927 GHz for the first execution, and 344.311, 345.798, 346.998, and 347.331 GHz for the second execution." (OBSERVATIONS)
- continuum bandwidth: 1.48 and 1.83 GHz at 302 and 346 GHz  
  > "The continuum bandwidth amounted to 1.48 and 1.83 GHz averaged at 302 and 346 GHz." (OBSERVATIONS)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21-375 m, 24 antennas  
  > "using 24 antennas with baseline lengths between 21 and 375 m" (OBSERVATIONS)
- angular resolution: 1.0" x 0.48" (302 GHz), 0.95" x 0.42" (346 GHz)  
  > "synthetic beam sizes of $1.0\ensuremath{''} \times 0.48\ensuremath{''}$ (23°) and $0.95\ensuremath{''} \times 0.42\ensuremath{''}$ (38°) at 302 and 346 GHz" (OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.4 and 0.5 mJy/beam; 19 mJy/beam/channel for CO  
  > "The achieved rms for the continuum was 0.4 and 0.5 mJy beam$^{-1}$ at 302 and 346 GHz, respectively" (OBSERVATIONS)
- time on source: 13 and 14 min  
  > "The total on-source observation time was 13 and 14 mins, respectively." (OBSERVATIONS)
- observing dates: 2012 November 18  
  > "on 2012 November 18" (OBSERVATIONS)
- pi or archival as stated: Cycle 0, PI C. Walsh; same data previously published by Pineda et al. 2014  
  > "(cite: pineda14) have already published these data; however, we reach different conclusions based on more thorough data processing." (INTRODUCTION)
- Line: CO J=3-2 (345.795 GHz)
- External data: 1.3 and 3.4 mm total flux densities 465±20 and 36±3 mJy (SEST, ATCA)  
  > "yielding a total flux density of 465$\pm$20 and 36$\pm$3 mJy, respectively" (HD 100546) [from (cite: henning94; wilner03)]
- External data: APEX CO flux for comparison  
  > "which is around 92% of the flux measured with APEX (cite: panic10)" (RESULTS) [from (cite: panic10)]
- External data: Disk model, companion mass limit and dust mass used for dust evolution simulations  
  > "a dust mass, $5.0 \times 10^{-4}$ $\mathrm{M}_\odot$ (cite: mulders13)" (DISCUSSION) [from (cite: mulders13)]
- Simulation/model as data: Dust growth and migration models with 20 MJup companion at 10 AU, with and without 15 MJup protoplanet at 68 AU injected at 1 Myr  
  > "(a) a 20 M$_\mathrm{Jup}$ companion at 10 AU only, and (b) both a 20 M$_\mathrm{Jup}$ companion and a protoplanet (15 M$_\mathrm{Jup}$) at 68 AU." (DISCUSSION)

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA 3.4; self-calibration with CASA 4.1  
  > "The data were calibrated using the Common Astronomy Software Package (CASA), version 3.4." (OBSERVATIONS)
- casa version: 3.4 (calibration), 4.1 (self-cal and imaging)  
  > "Self-calibration and imaging were performed using CASA version 4.1." (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan flux; 3C 297 bandpass; J1147-6753 phase  
  > "The quasar, 3C 297, was used as bandpass calibrator with Titan and a quasar, J1147-6753, used for amplitude and phase calibration, respectively." (OBSERVATIONS)
- flux scale uncertainty: ≈10%  
  > "The estimated absolute flux calibration uncertainties are $\approx$ 10%." (RESULTS)
- self calibration: Self-calibration with mask on strong continuum component only; peak S/N at 346 GHz 150 to 1320  
  > "The self-calibration procedure (using a mask containing only the strong continuum component) significantly increased the dynamic range" (RESULTS)

### Imaging

- task: CLEAN, fixvis to correct phase center for proper motion  
  > "The phase center of the observations was subsequently corrected using the CASA task, `fixvis`." (OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Continuum and line imaging were performed using the CLEAN algorithm with Briggs weighting (robust = 0.5)" (OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "The continuum was subtracted from line-containing channels using the CASA task, `uvcontsub`, in advance of imaging the CO emission." (OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.0"x0.48" (302 GHz); 0.95"x0.42" (346 GHz)  
  > "synthetic beam sizes of $1.0\ensuremath{''} \times 0.48\ensuremath{''}$ (23°)" (OBSERVATIONS)
- final rms: 0.4/0.5 mJy/beam continuum; 19 mJy/beam/channel CO  
  > "with an rms of 19 mJy beam$^{-1}$ channel$^{-1}$ attained for the CO-containing channels" (OBSERVATIONS)

### Inherited from earlier work

- Gaussian ring brightness profile  
  > "a compact ring with a gaussian brightness distribution," (RESULTS) [from (cite: perez14)]
- Dust temperature and dust opacity assumptions  
  > "assuming $\kappa_\nu = 10$ cm$^2$ g$^{-1}$ at 300 GHz, and $T_\mathrm{dust} = 60$ K (cite: andrews11; bruderer12)." (RESULTS) [from (cite: andrews11; bruderer12)]
- Dust evolution model  
  > "we model the dust growth and migration for two scenarios (cite: birnstiel10; pinilla12)" (DISCUSSION) [from (cite: birnstiel10; pinilla12)]

### Not stated but needed to reproduce (our reading)

- CLEAN masks, number of iterations and thresholds, cell and image size
- Line-free channels used for uvcontsub
- Self-calibration solution intervals and number of rounds
- Exact visibility-fitting chi2 and Bayesian error procedure
- Dust evolution code and numerical set-up (grid, gas surface density profile)
- Which execution calibrators apply to which spectral windows

## Analysis recipe

1. **Image continuum and CO**: CLEAN with Briggs weighting after fixvis, self-cal and uvcontsub; moment maps of CO  
  > "Continuum and line imaging were performed using the CLEAN algorithm with Briggs weighting (robust = 0.5)" (OBSERVATIONS)
   - software: CASA
   - parameter: CO integrated between -12 and +12 km/s of source velocity 5.7 km/s  
  > "The integrated intensity was determined between $-12$ and $+12$ km s$^{-1}$ relative to the source velocity" (RESULTS)
   - fitting: _not stated_
   - validation: CO flux compared to APEX (92%)  
  > "the total integrated CO flux in these data is 151 Jy km s$^{-1}$ which is around 92% of the flux measured with APEX" (RESULTS)
2. **Fit disk geometry**: uvmodelfit elliptical disk to continuum visibilities  
  > "the CASA task `uvmodelfit` was used to fit the continuum visibilities assuming the emission arises from a elliptical disk." (RESULTS)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: agreement with previous observations  
  > "in excellent agreement with previous observations" (RESULTS)
3. **Fit radial structure in visibility domain**: Bin deprojected visibilities (10 kλ); grid fit of power-law ring, then Gaussian compact ring plus flat extended ring; chi2 grid with Bayesian errors  
  > "A small step size of 0.5 AU was chosen to allow quantification of the errors via Bayesian inference." (RESULTS)
   - parameter: fluxes fixed at 0.962 and 0.024 Jy (302 GHz), 1.190 and 0.048 Jy (346 GHz)  
  > "the total flux contribution from the compact and extended components were fixed at 0.962 and 0.024 Jy at 302 GHz" (RESULTS)
   - assumption: Circular symmetry  
  > "Without any further knowledge on the structure we assume a circular-symmetric surface-brightness distribution." (RESULTS)
   - fitting: chi2 grid search  
  > "A low-resolution grid was run (5 AU) to determine the location of the global minimum in the $\chi^2$ value." (RESULTS)
   - validation: Residual images with identical uv coverage  
  > "The model residuals were imaged using an identical $uv$ coverage as the observations" (RESULTS)
4. **Estimate dust masses**: Optically thin Mdust = D^2 F / (kappa B(T))  
  > "The total dust mass, M$_\mathrm{dust}$ $\approx$ $D^2 F_\nu / \kappa_\nu B_\nu(T_\mathrm{dust})$" (RESULTS)
   - assumption: kappa=10 cm2/g at 300 GHz, Tdust=60 K; 80 K and 40 K for inner/outer rings  
  > "assuming disk temperatures of 80 and 40 K at $\approx$ 30 and $\approx$ 190 AU" (RESULTS)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dust evolution simulations with companions**: Dust growth/migration models for companion only and companion+protoplanet, compared qualitatively to ALMA  
  > "The younger protoplanet is injected into the simulations at 1 Myr." (DISCUSSION)
   - parameter: initial size 1 μm, alpha=2e-3, M*=2.4 Msun, dust mass 5e-4 Msun  
  > "We assume an initial particle size, 1$\mu$m, a disk viscosity, $\alpha_\mathrm{turb} = 2\times 10^{-3}$" (DISCUSSION)
   - assumption: gas-to-dust 100; model extrapolated to 400 AU by power law  
  > "assuming a gas-to-dust mass ratio of 100" (DISCUSSION)
   - fitting: _not stated_
   - validation: Qualitative agreement, contrast ~100 between rings  
  > "These results are qualitatively in agreement with the ALMA observations which also show a contrast of $\sim$ 100 between emission from the inner and outer ring." (DISCUSSION)

## Software

- **CASA** 3.4 (calibration); 4.1 (self-cal, imaging): Calibration, self-calibration, imaging, fixvis, uvcontsub, uvmodelfit  
  > "The data were calibrated using the Common Astronomy Software Package (CASA), version 3.4." (OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO disk radius | 390 | 20 | AU | 1 | extensive molecular disk (390$\pm$20 AU in radius) |
| Continuum disk radius | 230 | 20 | AU | 1 | continuum emission is more compact (230$\pm$20 AU in radius) |
| Continuum total flux 302 GHz / 346 GHz | 0.980 / 1.240 | ~10% absolute | Jy | 1 | a total flux density of 0.980 and 1.240 Jy (summing over all flux $\gtrsim$ 3 $\sigma$) at 302 and 346 GHz |
| Inclination | 44 | 3 | deg | 2 | inclination of 44$\pm$3°and a position angle |
| Position angle | 146 | 4 | deg | 2 | position angle (measured East from North) of 146$\pm$4° |
| Visibility null | 290 | not stated | kλ | 3 | there is a zero crossing (null) at 290 k$\lambda$ |
| Outer ring centre | 190 | 3 | AU | 3 | an outer ring with a width of 75$\pm$3 AU centered at 190$\pm$3 AU |
| Inner ring peak / FWHM | 26 / 21 | not stated | AU | 3 | a compact ring with a peak brightness at 26 AU and a FWHM of 21 AU |
| Total dust mass | 0.035 | not stated | MJup | 4 | is $\approx$ 0.035 M$_\mathrm{Jup}$ |
| Inner/outer ring dust mass | 2.5e-2 / 1.4e-3 | not stated | MJup | 4 | $\approx$ 2.5 $\times$ 10$^{-2}$ and $\approx$ 1.4 $\times$ 10$^{-3}$ M$_\mathrm{Jup}$ |
| Total CO flux | 151 | not stated | Jy km/s | 1 | the total integrated CO flux in these data is 151 Jy km s$^{-1}$ |

## Qualitative findings

- CO is similar in extent to scattered light, indicating well-mixed gas and micron-sized grains; mm continuum is more compact, suggesting radial drift  
  > "suggesting radial drift of the mm-sized grains." (abstract)

## Claim tuples

- H: Is the continuum a single power-law disk? | E: Fit single power-law ring to visibilities | R: Best fit 16-51 AU gamma=2 leaves large residuals | F: Single component cannot reproduce visibilities; two rings needed | **supported**
- H: Do companions explain the ring structure? | E: Dust evolution simulations with one or two companions | R: Two companions reproduce inner ring and weaker outer ring; one alone cannot explain outer ring | F: Evidence for close-in companion and protoplanet in outer disk | **partially**
- H: Are gas and small grains mixed? | E: Compare CO extent with scattered light | R: Similar extent | F: Well-mixed in disk atmosphere | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Overlapping rings excluded in favour of two distinct rings  
  > "The data exclude overlapping rings in favour of two distinct rings of emission." (RESULTS)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk size near largest recoverable scale; imaginary scatter at long baselines may indicate asymmetry needing higher resolution  
  > "Higher spatial resolution observations are needed to confirm any asymmetry at small spatial scales." (RESULTS)
- Caveat (inferred, ours): Two-ring fit fixes component fluxes and assumes axisymmetry
- Caveat (inferred, ours): Dust-evolution comparison is only qualitative with no fit
- Caveat (inferred, ours): Single short Cycle 0 dataset limits resolution of inner ring
- Caveat (inferred, ours): Dust mass depends on assumed opacity and temperature

## Reproducibility

- Data public (paper): ALMA Cycle 0 program 2011.0.00863.S, previously published by Pineda et al.  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00863.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Self-calibration settings
- Missing: Dust evolution code and inputs
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Public data and a clear visibility-fitting approach, but imaging/self-cal details and simulation code are missing.
- Rediscovery candidate: yes, Public Cycle 0 data, numeric ring radii and fluxes can be redone via visibility fitting.

## Links

- Method: (cite: berger07) (Visibility of ring models and deprojection)
- Method: (cite: perez14) (Gaussian ring model)
- Companion: (cite: pineda14) (Earlier publication of the same ALMA data)
- Companion: (cite: quanz13) (Protoplanet candidate at 68 AU)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 51,
  "rate": 0.68
 },
 "evidence_ok": true
}
```
