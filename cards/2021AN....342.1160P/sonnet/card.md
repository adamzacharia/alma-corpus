# CO kinematics unveil outflows plausibly driven by a young jet in the gigahertz peaked radio core of NGC 6328

`2021AN....342.1160P` | Astronomische Nachrichten 2021 | first author: Papachristou, Michalis | arXiv: 2111.00453 | DOI: 10.1002/asna.20210063

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is the high velocity dispersion of molecular gas in NGC 6328 due to projection effects of regularly rotating, non-coplanar disks, or to dynamically unsettled gas from inflows or outflows?  
  > "could the observed velocity dispersion be due to projection effects of regularly rotating, non-coplanar disks or to dynamically unsettled gas due to inflows or outflows?" (2 ALMA data analysis and Modeling)
- Target **NGC 6328 (PKS 1718-649)**: coordinates _not stated_; z/distance 62 Mpc (z=0.014313)  
  > "The host galaxy, NGC 6328, is an early type galaxy at a distance of 62 $\rm{Mpc}$ $(z=0.014313)$" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01359.S, 2017.1.01638.S
- bands: Band 6 (CO 2-1) and Band 7 (CO 3-2)  
  > "archival ALMA observations of Band 6 CO(2-1) (PID 2015.1.01359.S) and Band 7 CO(3-2) (PID 2017.1.01638.S)" (2 ALMA data analysis and Modeling)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.27x0.19 arcsec (CO 2-1); 0.35x0.29 arcsec (CO 3-2)  
  > "synthesized beams of 0$\,\!^{\prime\prime}$27 $\times$0$\,\!^{\prime\prime}$19 and 0$\,\!^{\prime\prime}$35$\times$0$\,\!^{\prime\prime}$29 for CO(2-1) and CO(3-2), respectively" (2 ALMA data analysis and Modeling)
- max recoverable scale: _not stated_
- sensitivity: rms 0.24 mJy/beam (CO 2-1), 0.297 mJy/beam (CO 3-2) in 20 km/s channels  
  > "resulting in root-mean-square (rms) noise levels of 0.24 and 0.297 mJy/beam" (2 ALMA data analysis and Modeling)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "We present the analysis of archival ALMA observations" (2 ALMA data analysis and Modeling)
- Line: CO 2-1 (not stated)
- Line: CO 3-2 (not stated)
- External data: HI velocity data at the outskirts of the galaxy and HI disk geometry used as priors/likelihood  
  > "the observed HI velocity data at the outskirts of the galaxy ((cite: maccagni_what_2014; veron-cetty_pks_1995))" (2 ALMA data analysis and Modeling) [from (cite: maccagni_what_2014; veron-cetty_pks_1995)]
- External data: Jet power ~2e43 erg/s  
  > "the jet power of $\sim 2\times 10^{43}\,\mathrm{ergs/s}$ (cite: wojtowiczJetProductionEfficiency2020)" (3 Discussion) [from (cite: wojtowiczJetProductionEfficiency2020)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were calibrated using the Common Astronomy Software Application (CASA) pipeline" (2 ALMA data analysis and Modeling)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: continuum maps improved with phase and amplitude self-calibration  
  > "have improved through phase and amplitude self-calibration" (2 ALMA data analysis and Modeling)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The imaging was performed using natural weighting and channel widths of 20 km s$^{-1}$" (2 ALMA data analysis and Modeling)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: subtracted in line-free channels  
  > "The CO line cubes were obtained after subtraction of the continuum in the line-free channels." (2 ALMA data analysis and Modeling)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- line-free channel ranges
- image size and cell size
- self-calibration solution intervals
- cleaning threshold and masking
- MCMC priors, walkers, steps and likelihood form
- free-ring radii in spline parameterization and potential parameters (bulge mass, halo)
- how residuals were isolated and outflow mass/rate/energetics computed (geometry, velocity, radius)
- CO(3-2) to CO(2-1) conversion for luminosity

## Analysis recipe

1. **calibrate and image CO cubes**: CASA pipeline calibration, continuum subtraction, natural-weighted imaging with 20 km/s channels  
  > "The imaging was performed using natural weighting and channel widths of 20 km s$^{-1}$" (2 ALMA data analysis and Modeling)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **CO luminosity and molecular gas mass**: L'CO(2-1) computed following Solomon & Vanden Bout; gas mass with Milky Way conversion factor  
  > "giving a total molecular gas mass of $1.8\times 10^{9} \,\mathrm{M}_\odot$ for a Milky Way conversion factor of 4.6" (2 ALMA data analysis and Modeling)
   - assumption: Milky Way conversion factor 4.6 Msun/(K km/s pc^2)  
  > "Milky Way conversion factor of 4.6" (2 ALMA data analysis and Modeling)
   - fitting: _not stated_
   - validation: _not stated_
3. **3D tilted-ring kinematic model**: New 3D tilted-ring code in sky+velocity space; rings with PA, i and velocity as monotonic cubic splines; potential of SMBH (Keplerian), Hernquist bulge, NFW halo  
  > "we developed a new 3D model (in the sky+velocity space) code that uses the tilted rings approximation" (2 ALMA data analysis and Modeling)
   - software: emcee
   - assumption: Disk potential neglected; contribution comparable to error bar of 20 km/s  
  > "We do not add the potential of the disk, as its contribution to the rotation curve is comparable to the error bar" (2 ALMA data analysis and Modeling)
   - fitting: emcee MCMC sampling of posterior = likelihood of data cube and HI velocities times joint prior; MAP best fit  
  > "The parameter estimation is done by sampling, with the Markov Chain Monte Carlo sampler *emcee*" (2 ALMA data analysis and Modeling)
   - validation: Best fit explains most high dispersion regions via projection; residuals remain near center  
  > "can explain most of the high velocity dispersion regions of the molecular gas through projection effects" (2 ALMA data analysis and Modeling)
4. **excitation and outflow energetics from residuals**: Compare T_CO(3-2)/T_CO(2-1) to LTE value 9/4; estimate outflow mass from residual intensity with alpha_CO 0.8; derive rate, power, momentum  
  > "From the intensity of the high-velocity residuals, we conservatively estimate the mass of the outflow to be 3-4$\times10^6\,\mathrm{M}_\odot$" (3 Discussion)
   - assumption: alpha_CO = 0.8 Msun/(K km/s pc^2) for outflow  
  > "using an $a_\mathrm{CO}$ conversion factor of 0.8" (3 Discussion)
   - fitting: _not stated_
   - validation: Compared to SN, stellar radiation and AGN radiation pressure budgets  
  > "A central star forming region would be unable to drive the outflow" (3 Discussion)

## Software

- **CASA** : pipeline calibration  
  > "The data were calibrated using the Common Astronomy Software Application (CASA) pipeline" (2 ALMA data analysis and Modeling)
- **emcee** : MCMC sampling of kinematic model parameters  
  > "the Markov Chain Monte Carlo sampler *emcee*" (2 ALMA data analysis and Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L'CO(2-1) | 3.8e8 | not stated | K km/s pc^2 | 2 | The $L'_\mathrm{CO(2-1)}$ luminosity calculated is 3.8$\times10^{8}\,\mathrm{K}\,\mathrm{kms^{-1}}\,\mathrm{pc}^2$ |
| Total molecular gas mass | 1.8e9 | not stated | Msun | 2 | giving a total molecular gas mass of $1.8\times 10^{9} \,\mathrm{M}_\odot$ |
| L'CO(3-2) | 8.4e7 | not stated | K km/s pc^2 | 2 | has a luminosity of $L'_\text{CO(3-2)}$=8.4$\times10^{7}\,\mathrm{K}\, \mathrm{km s^{-1}}\, \mathrm{pc}^2$ |
| Outflow mass | 3-4e6 | not stated | Msun | 4 | we conservatively estimate the mass of the outflow to be 3-4$\times10^6\,\mathrm{M}_\odot$ |
| Mass outflow rate | 3-8 | not stated | Msun/yr | 4 | a mass outflow rate of 3-8 $\mathrm{M}_\odot/\mathrm{yr}$ |
| Outflow kinetic power | 2-7e40 | not stated | erg/s | 4 | This leads to an outflow kinetic power between $2-7\times10^{40}\,\mathrm{ergs/s}$ |
| Outflow momentum rate | 1-7e33 | not stated | dyn | 4 | a momentum rate of $1-7\times 10^{33}\,\mathrm{dyn}$ |

## Qualitative findings

- Central disk (650 pc) has i~65 deg, PA~72 deg; larger disk appears warped with PA from 140 to 180 deg  
  > "The first one is a central disk extending up to 650 pc from the center with $i\approx$65$^{\circ}$ and PA$\approx$72$^{\circ}$." (2 ALMA data analysis and Modeling)
- Regularly rotating gas is sub-thermally excited in contrast with the unsettled gas  
  > "The regularly rotating, well-modeled gas is sub-thermally excited in contrast with the unsettled one." (3 Discussion)

## Claim tuples

- H: High velocity dispersion regions are explained by projection effects of a warped rotating disk | E: 3D tilted-ring model fit with emcee to CO(2-1) cube | R: Most high dispersion regions reproduced, but residuals remain at 100-300 pc with velocities 0 to -250 km/s and CO(3-2) clump at 200 km/s | F: Unsettled non-rotating gas is present beyond projection effects | **supported**
- H: The residual gas is an outflow driven by a young jet | E: Energetics compared to star formation, AGN radiation and jet power; excitation ratio | R: Outflow power 2-7e40 erg/s well below jet power ~2e43 erg/s; star formation and AGN insufficient | F: Outflow plausibly jet-driven | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Shredding of an infalling structure rejected given high dispersion and -250 to 250 km/s range  
  > "we argue that the non-rotating gas in emission cannot be attributed to the shredding of an individual infalling structure" (3 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 7 data not optimized for CO(3-2) and only partially covers the field/velocity range  
  > "Band 7 observations were not optimized for the CO(3-2) transition and are only partially visible in the field-of-view" (2 ALMA data analysis and Modeling)
- Caveat (inferred, ours): Outflow mass depends on alpha_CO choice of 0.8 and residual definition
- Caveat (inferred, ours): Model code is new and unreleased; model degeneracies not shown
- Caveat (inferred, ours): Jet-driving inferred from power budget only

## Reproducibility

- Data public (paper): archival ALMA data  
  > "We present the analysis of archival ALMA observations" (2 ALMA data analysis and Modeling)
- Products in archive: _not stated_
- Missing: Kinematic modeling code and priors
- Missing: CASA version and imaging parameters
- Missing: Residual extraction and outflow energetics details
- Data volume (inferred): ~50-100 GB for two projects
- Score (inferred): 3/5, Public data but the short proceedings omit modeling priors, code and many processing details.
- Rediscovery candidate: no, Custom unreleased model code and incomplete recipe.

## Links

- Companion: (cite: maccagniALMAObservationsAGN2018) (Earlier ALMA CO absorption observations of the same source)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 29,
  "rate": 0.439
 },
 "evidence_ok": true
}
```
