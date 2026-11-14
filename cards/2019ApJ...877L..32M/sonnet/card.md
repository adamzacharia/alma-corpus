# Multiple Rings of Millimeter Dust Emission in the HD 15115 Debris Disk

`2019ApJ...877L..32M` | The Astrophysical Journal Letters 2019 | first author: MacGregor, Meredith A. | arXiv: 1905.08258 | DOI: 10.3847/2041-8213/ab21c2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Does the HD 15115 debris disk show multiple rings and a gap at 1.3 mm, and does the millimeter emission show the east-west asymmetry seen in scattered light?  
  > "This new ALMA image shows evidence for two rings in the disk separated by a cleared gap." (abstract); "Since we do not see any evidence at millimeter wavelengths for the dramatic east-west asymmetry seen in scattered light" (abstract)
- Target **HD 15115**: coordinates _not stated_; z/distance 49.0±0.1 pc  
  > "at a GAIA DR2 distance of $49.0\pm0.1$ pc" (Introduction); distance from GAIA DR2  
  > "at a GAIA DR2 distance of $49.0\pm0.1$ pc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00633.S
- bands: Band 6 (1.3 mm, 230 GHz)  
  > "We observed the HD 15115 debris disk with ALMA in Cycle 3 using Band 6 (1.3 mm, 230 GHz)." (2 Observations)
- frequencies and spectral setup: 4 spectral windows at 230.538 (12CO 2-1), 232.538, 215.5, 217.5 GHz; three continuum windows with 2 GHz and 128 channels; line window 1.875 GHz with 3840 channels  
  > "The three continuum-only spectral windows had a bandwidth of 2 GHz with 128 channels, while the final spectral window had a reduced bandwidth of 1.875 GHz with 3840 channels." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact (15–310 m) and extended (15–704 m), 36 antennas  
  > "Two scheduling blocks (SBs) were executed in both a compact (baselines of 15–310 m) and more extended (baselines of 15–704 m) configuration with 36 antennas" (2 Observations)
- baselines: _not stated_
- angular resolution: 0.58"×0.55" (28×27 AU), robust=0.5  
  > "The synthesized beam is $0.58\ensuremath{''}\times0.55\ensuremath{''}$ ($28\times27$ AU) with robust $=0.5$ weighting" (3 Results and Analysis)
- max recoverable scale: _not stated_
- sensitivity: 15 µJy/beam rms  
  > "the rms noise in the image is $15$ $\mu$Jy beam$^{-1}$" (3 Results and Analysis)
- time on source: 15.1 min (compact) and 30.2 min (extended)  
  > "with an on-source time of 15.1 min, and 48.5 min with 30.2 min on-source for the compact and extended configurations, respectively" (2 Observations)
- observing dates: 2016 January 1 and 2016 June 9  
  > "on 2016 January 1 and 2016 June 9, respectively" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST STIS**: scattered light image for comparison  
  > "over the previous HST STIS scattered light image" (3 Results and Analysis)
- External data: Previous SMA millimeter inner/outer radii  
  > "Low-resolution millimeter imaging with the Submillimeter Array (SMA) gave comparable values" (4.1 Comparison to Previous Observations) [from (cite: MacGregor:2015a)]
- External data: Gap-clearing mass ratio relation mu=(δa/1.5a)^(7/2)  
  > "define the mass ratio of the planet to the star ($\mu$) given the gap size to be" (4.3 Constraints on a Planet in the Gap) [from (cite: Quillen:2006)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "All data processing and calibration was done with the ALMA pipeline in `CASA` (version 4.7.2)." (2 Observations)
- casa version: 4.7.2  
  > "ALMA pipeline in `CASA` (version 4.7.2)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636  
  > "was used for both bandpass and flux calibration, as well as pointing" (2 Observations)
- flux scale uncertainty: <10%  
  > "We estimate that the absolute flux calibration uncertainty is $<10\%$." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN task in CASA  
  > "All images were generated using the `CLEAN` task in `CASA`." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with robust $=0.5$ weighting" (3 Results and Analysis)
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
- final rms: 15 µJy/beam  
  > "the rms noise in the image is $15$ $\mu$Jy beam$^{-1}$" (3 Results and Analysis)

### Inherited from earlier work

- MCMC visibility-fitting procedure  
  > "we adopt the modeling procedure initially described in (cite: MacGregor:2013) and most recently in (cite: MacGregor:2018b)" (3.1 Modeling Approach) [from (cite: MacGregor:2013); (cite: MacGregor:2018b)]

### Not stated but needed to reproduce (our reading)

- Imaging details: cell size, image size, mask, niter/threshold
- Time-averaged visibility handling and any channel averaging or weights rescaling for fitting
- Whether continuum windows only were used for fitting
- Initial walker positions and burn-in length
- Stellar photosphere flux value
- Details of the CO upper-limit calculation (excitation temperature, line width)
- REBOUND setup details (integration time step, particle initial distributions)

## Analysis recipe

1. **Image continuum and CO**: CLEAN imaging of calibrated, 30 s time-averaged visibilities; CO non-detection upper limit  
  > "the calibrated visibilities were time-averaged in 30 sec intervals" (2 Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "with robust $=0.5$ weighting" (3 Results and Analysis)
   - assumption: CO mass upper limit assumes LTE  
  > "upper limit on the total CO mass of $<1.4\times10^{-9}$ $M_\oplus$ assuming Local Thermodynamic Equilibrium (LTE)" (3 Results and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit disk models to visibilities**: Single ring, two power-law rings, and power-law ring with Gaussian gap fit directly to visibilities in MCMC  
  > "We fit three different models to the HD 15115 ALMA data– a single ring model and two different double ring models." (3.1 Modeling Approach)
   - software: emcee, vis_sample
   - parameter: ~10^6 iterations (100 walkers, 10,000 steps each)  
  > "We use $\sim10^6$ iterations (100 walkers, 10,000 steps each) to fully explore parameter space" (3.1 Modeling Approach)
   - assumption: Axisymmetric surface brightness I∝r^α with T∝r^-0.5  
  > "we assume that the surface brightness is an axisymmetric function, $I_\nu\propto r^\alpha$" (3.1 Modeling Approach)
   - fitting: emcee, uniform priors with F_disk>0 and 0<R_in<R_out, chi2 likelihood lnL=-chi2/2  
  > "We assume uniform priors for all parameters and only introduce limits to ensure that each model is physical" (3.1 Modeling Approach)
   - validation: Gelman-Rubin R-hat<1.1; residual maps ≤3σ; reduced chi2 ~1.1  
  > "requiring $\hat{R}<1.1$ for all model parameters" (3.1 Modeling Approach)
3. **Estimate planet mass and test with N-body**: Quillen & Faber gap-width relation with 1.4 Msun star; REBOUND N-body with 10000 particles  
  > "we performed N-body simulations using REBOUND (cite: Rein:2012)" (4.3 Constraints on a Planet in the Gap)
   - software: REBOUND
   - assumption: F4 star with mass ~1.4 Msun  
  > "Assuming the central star is an F4 spectral type with mass $\sim1.4$ $M_\odot$" (4.3 Constraints on a Planet in the Gap)
   - fitting: _not stated_
   - validation: N-body gap FWHM ~15 AU compared to observed  
  > "The planet quickly opens a gap with FWHM $\sim15$ AU in both models" (4.3 Constraints on a Planet in the Gap)

## Software

- **CASA** 4.7.2: pipeline calibration and CLEAN imaging  
  > "All data processing and calibration was done with the ALMA pipeline in `CASA` (version 4.7.2)." (2 Observations)
- **emcee** : MCMC sampling  
  > "We make use of both the `emcee` (cite: Foreman-Mackey:2013) and `vis_sample`" (3.1 Modeling Approach)
- **vis_sample** : sampling model images at visibility locations  
  > "We make use of both the `emcee` (cite: Foreman-Mackey:2013) and `vis_sample`" (3.1 Modeling Approach)
- **REBOUND** : N-body gap-opening simulations  
  > "we performed N-body simulations using REBOUND (cite: Rein:2012)" (4.3 Constraints on a Planet in the Gap)
- **BANYAN Σ** : moving group membership of HIP 12545  
  > "`BANYAN` $\Sigma$ does not find a high probability that HIP 12545 is in Tuc-Hor" (4.2 Possible Sculpting Mechanisms)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inner edge (Gaussian gap model) | 43.9 | ±5.8 | AU | 2 | $43.9\pm5.8$ ($0.89\ensuremath{''}\pm0.12\ensuremath{''}$) |
| Disk outer edge (Gaussian gap model) | 92.2 | ±2.4 | AU | 2 | $92.2\pm2.4$ ($1.88\ensuremath{''}\pm0.49\ensuremath{''}$) |
| Gap location | 58.9 | ±4.5 | AU | 2 | $58.9\pm4.5$ ($1.20\ensuremath{''}\pm0.10\ensuremath{''}$) |
| Gap FWHM | 13.8 | ±5.6 | AU | 2 | $13.8\pm5.6$ ($0.28\ensuremath{''}\pm0.11\ensuremath{''}$) |
| Gap fractional depth | 0.88 | ±0.10 | dimensionless | 2 | $0.88\pm0.10$ |
| Inclination (Gaussian gap model) | 86.2 | ±0.5 | deg | 2 | $86.2\pm0.5$ |
| Total disk flux density (Gaussian gap model) | 1.98 | ±0.03 | mJy | 2 | $1.98\pm0.03$ |
| 12CO integrated flux 3σ upper limit | <0.022 | not stated | Jy km/s | 1 | upper limit on the integrated flux density of the line of $<0.022$ Jy km s$^{-1}$ |
| CO mass upper limit | <1.4e-9 | not stated | Earth masses | 1 | upper limit on the total CO mass of $<1.4\times10^{-9}$ $M_\oplus$ |
| Planet mass | 0.16 | ±0.06 | M_Jup | 3 | yields an estimate for the planet mass of $0.16\pm0.06$ $M_\text{Jup}$ |

## Qualitative findings

- The millimeter disk shows no significant east-west asymmetry (>3σ), unlike scattered light.  
  > "the ALMA image does not show any asymmetry $>3\sigma$ between the eastern and western sides of the disk" (4.2 Possible Sculpting Mechanisms)

## Claim tuples

- H: The disk contains two rings separated by a gap | E: MCMC visibility fits of single-ring, two-ring and Gaussian-gap models | R: Single ring leaves 6σ residuals; two-ring and gap models give reduced chi2 ~1.1 with a nearly empty gap | F: Disk has two rings with a gap at ~59 AU | **supported**
- H: Scattered-light asymmetry is also present in large grains | E: Compare ALMA image with scattered light | R: No asymmetry >3σ | F: The mechanism affects only small grains, likely ISM ram pressure | **supported**
- H: A planet carved the gap | E: Gap-width mass relation and REBOUND simulations | R: 0.16±0.06 MJup planet; ~0.2 MJup opens FWHM ~15 AU gap in 1 Myr | F: A sub-Jupiter planet plausibly sculpts the gap | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Eccentric non-aligned particles piling at edges rejected: brightness difference ~40-50% too small  
  > "the maximum brightness difference between the two apparent peaks is $\sim40-50\%$, not large enough to match our observations" (4.3 Constraints on a Planet in the Gap)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution cannot distinguish the two-ring from the Gaussian gap model  
  > "Given the current resolution of these observations, we cannot distinguish between the two ring and Gaussian gap models." (3.2 Modeling Results)
- Caveat (inferred, ours): Planet mass relies on a simple gap-width scaling and assumed stellar mass
- Caveat (inferred, ours): Surface density gradients are poorly constrained and degenerate with edge radii
- Caveat (inferred, ours): Edge-on geometry limits radial profile recovery

## Reproducibility

- Data public (paper): ALMA data cited with project code; vis_sample publicly available  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00633.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: vis_sample is public on GitHub  
  > "`vis_sample` is publicly available at <https://github.com/AstroChem/vis_sample>" (footnote)
- Missing: Imaging parameters beyond robust
- Missing: MCMC model code and initialisation
- Missing: REBOUND setup details
- Data volume (inferred): ~5-20 GB raw for two Cycle 3 execution blocks
- Score (inferred): 6/5, Public data and a clear modeling approach with parameter table, but model code and several imaging/setup details are not given.
- Rediscovery candidate: yes, Public data, a stated modeling recipe, and numeric results in Table 1.

## Links

- Method: (cite: MacGregor:2013) (MCMC visibility modeling procedure)
- Method: (cite: MacGregor:2018b) (most recent description of modeling procedure)
- Companion: (cite: MacGregor:2015a) (previous SMA millimeter observations of HD 15115)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 42,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
