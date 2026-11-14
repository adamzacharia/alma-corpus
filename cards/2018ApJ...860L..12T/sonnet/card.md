# A Kinematical Detection of Two Embedded Jupiter-mass Planets in HD 163296

`2018ApJ...860L..12T` | The Astrophysical Journal Letters 2018 | first author: Teague, Richard | arXiv: 1805.10290 | DOI: 10.3847/2041-8213/aac6d7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Can precise rotation curves of CO isotopologue emission reveal pressure-gradient perturbations from embedded planets in the HD 163296 disk?  
  > "In this Letter we present a new method to precisely measure $v_{\rm rot}$ which is used to make the first kinematical detection of embedded planets in the disk of HD 163296" (Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance 101.5 pc  
  > "a A1 star at 101.5 pc (cite: Bailer-Jones_ea_2018)" (Introduction); distance from Bailer-Jones et al. 2018 (Gaia)  
  > "a A1 star at 101.5 pc (cite: Bailer-Jones_ea_2018)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00601.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.26'' x 0.18'' beam for all three lines  
  > "resulting in a beam size of $0.26\ensuremath{''} \times 0.18\ensuremath{''}$ for all three lines" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, PI Isella  
  > "We use archival data of the $J = 2-1$ transitions" (2 Observations)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Stellar mass 2.3 Msun and inclination 47.7 deg for Keplerian reference  
  > "assuming $2.3~M_{\rm sun}$ and $i = 47.7\ensuremath{^\circ}$, appropriate for HD 163296 (cite: Flaherty_ea_2015; Flaherty_ea_2017)" (3 Precise Measurement of Rotation) [from Flaherty_ea_2015; Flaherty_ea_2017]
- External data: Distance 101.5 pc  
  > "a A1 star at 101.5 pc (cite: Bailer-Jones_ea_2018)" (Introduction) [from Bailer-Jones_ea_2018]
- Simulation/model as data: 2D FARGO3D hydrodynamic simulations of embedded planets, post-processed with LIME to C18O cubes  
  > "we ran hydrodynamical simulations of embedded protoplanets using `FARGO 3D` (cite: Benitez_ea_2016)" (4 Hydrodynamic Models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.4.0 for calibration; CASA 4.7.2 for self-calibration and imaging  
  > "The data were initially calibrated with `CASA v4.4.0` before transferring to `CASA v4.7.2` for self-calibration and imaging." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal on combined continuum spws, applied to whole dataset; no amplitude self-cal  
  > "Phase self-calibration was performed on the continuum by combining the three continuum spectral windows before being applied to the whole dataset. No amplitude self-calibration was performed." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "the lines imaged using Briggs weighting and a robust value of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "Continuum emission was subtracted from the line data using the task `uvcontsub`" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channel spacing averaged to 50 m/s  
  > "The channel spacing was averaged down to $50~{\rm m\,s^{-1}}$ in order to improve signal to noise." (2 Observations)
- final beam: 0.26'' x 0.18''  
  > "resulting in a beam size of $0.26\ensuremath{''} \times 0.18\ensuremath{''}$ for all three lines" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction procedure follows earlier work  
  > "Our reduction closely follows the procedure outlined in ." (2 Observations) [from reference not given in text (original data paper)]
- Emission height method  
  > "For this we follow the method presented in (cite: Pinte_ea_2018)" (3 Precise Measurement of Rotation) [from Pinte_ea_2018]
- Underlying physical structure of hydro models from best-fit model  
  > "The underlying physical structure was taken from the best-fit model of (cite: Flaherty_ea_2017)." (4 Hydrodynamic Models) [from Flaherty_ea_2017]

### Not stated but needed to reproduce (our reading)

- Spectral windows, channel/velocity range and imaging parameters (cell, image size, masks, line-free channels for uvcontsub)
- Self-calibration solution intervals
- GP kernel, hyperparameters and priors for the emission surface
- Details of the width-minimization (stacked line profile, line model) and bin radii
- Planet-disk setup: disk mass, scale height, planet accretion/smoothing, temperature model for LIME
- Exact inner-planet fit procedure and parameter grid

## Analysis recipe

1. **Measure emission surface height**: Follow Pinte et al. 2018 with emission surface modelled as a Gaussian Process  
  > "The emission surface is modelled as a Gaussian Process (GP) which assumes that the observations are drawn from a smoothly varying function." (3 Precise Measurement of Rotation)
   - software: celerite
   - parameter: position angle 132 deg from Keplerian fit to first moment map  
  > "using a position angle of 132$^\circ$ which we obtained from fitting a Keplerian rotation pattern to the first moment map" (3 Precise Measurement of Rotation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive rotation velocity profile by stacking deprojected spectra**: Annuli ~2 pixels wide (~9 au); shift spectra by v_rot cos(theta), stack; the correct v_rot minimizes stacked line width  
  > "We assert that the correct $v_{\rm rot}$ is the value which minimizes this width." (3 Precise Measurement of Rotation); "we first binned the data into annuli roughly two pixels wide ($\sim 9$ au)" (3 Precise Measurement of Rotation)
   - software: scipy.optimize
   - assumption: Keplerian reference: 2.3 Msun, i = 47.7 deg  
  > "assuming $2.3~M_{\rm sun}$ and $i = 47.7\ensuremath{^\circ}$" (3 Precise Measurement of Rotation)
   - fitting: L-BFGS-B minimization  
  > "we use the `L-BFGS-B` method implemented in the `scipy.optimize` package" (3 Precise Measurement of Rotation)
   - validation: Forward models with known v_rot; precision of 2 m/s recovered for SNR >~ 10  
  > "For a SNR of $\gtrsim 10$, as with the observations, we could recover $v_{\rm rot}$ accurately to a precision of $2~{\rm m\,s^{-1}}$." (3 Precise Measurement of Rotation)
3. **Run hydrodynamic simulations and synthetic C18O observations**: 2D FARGO3D runs with planets, inflate surface density by hydrostatic equilibrium, LIME non-LTE radiative transfer, convolve with beam, apply same method  
  > "we generate C$^{18}$O image cubes, simulate the observations and apply the methodology outline in Section [3](#sec:methodology) to the simulated observations." (4 Hydrodynamic Models)
   - software: FARGO3D, LIME
   - parameter: 1024 log radial cells 16-480 au, 1920 azimuthal cells  
  > "1024 logarithmically spaced radial cells between 16 and 480 au and 1920 uniformly spaced azimuthal cells covering $2\pi$ radians" (4 Hydrodynamic Models)
   - parameter: alpha = 1e-3, isothermal  
  > "An isothermal equation of state was assumed and a uniform viscosity of $\alpha = 10^{-3}$ was adopted" (4 Hydrodynamic Models)
   - assumption: C18O abundance 8.67e-8 above 19 K isotherm and below shielding column 1.2e21 H2 cm^-2  
  > "Above the 19 K isotherm and below a shielding column of $1.2 \times 10^{21}~{\rm H_2~cm^{-2}}$ (cite: Visser_ea_2009) a molecular abundance of $8.67\times10^{-8}$ was assumed for C$^{18}$O." (4 Hydrodynamic Models)
   - fitting: _not stated_
   - validation: Disk mass x5 test shows delta v_rot minimally affected  
  > "The derived $\delta v_{\rm rot}$ profile is minimally affected other than a slight shift to lower values" (5 Discussion)

## Software

- **CASA** 4.4.0 / 4.7.2: Calibration, self-calibration, imaging, uvcontsub  
  > "The data were initially calibrated with `CASA v4.4.0` before transferring to `CASA v4.7.2` for self-calibration and imaging." (2 Observations)
- **celerite** : Gaussian Process model of emission surface  
  > "`celerite` (cite: Foreman-Mackey_ea_2017)" (Software)
- **scipy** : L-BFGS-B optimisation of v_rot  
  > "we use the `L-BFGS-B` method implemented in the `scipy.optimize` package" (3 Precise Measurement of Rotation)
- **FARGO3D** : 2D hydrodynamic simulations  
  > "we ran hydrodynamical simulations of embedded protoplanets using `FARGO 3D` (cite: Benitez_ea_2016)" (4 Hydrodynamic Models)
- **LIME** : Non-LTE radiative transfer for C18O cubes  
  > "Radiative transfer was performed with the non-LTE code `LIME` (cite: Brinch_ea_2010)" (4 Hydrodynamic Models)
- **emcee** : listed in software; use not described  
  > "`emcee` (cite: emcee)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| v_rot precision on individual bins | 2 | not stated | m/s | 2 | The uncertainties on individual bins are roughly $2~{\rm m\,s^{-1}}$ between 50 and $250~{\rm m\,s^{-1}}$ |
| GP model uncertainty | 8 | not stated | m/s | 1 | is larger at $8~{\rm m\,s^{-1}}$ |
| Outer planet mass and location (122 pc) | 1.3 MJup at 165 au | mass within 50%, location within 10% | MJup, au | 3 | We find an excellent match to the observations with a $1~M_{\rm Jup}$ planet at 100 au, and $1.3~M_{\rm Jup}$ planet at 165 au |
| Inner planet (best fit, poor) | 0.6 MJup at 65 au | not stated | MJup, au | 3 | A planet of $0.6~M_{\rm Jup}$ at 65 au provided the best fit |
| Planet locations at 101.5 pc | 83 and 137 | not stated | au | 3 | (83 au and 137 au at the new distance of 101.5 pc) |

## Qualitative findings

- Rotation curves show deviations centred on continuum gaps, consistent with pressure-gradient perturbations; density changes dominate over temperature or height  
  > "the dominant source of the perturbation is changes in the density profile, consistent with the previously proposed embedded planet scenario" (4 Hydrodynamic Models)

## Claim tuples

- H: Embedded planets cause detectable velocity deviations in the gas rotation | E: Measured C18O rotation curve and compared with 2D hydro+LIME models | R: 1 MJup at 100 au and 1.3 MJup at 165 au match observed delta v_rot | F: Kinematical detection of two Jupiter-mass planets | **supported**
- H: The inner perturbation is explained by a single planet | E: Hydro model fits | R: No convincing fit | F: Inner feature unresolved; alternatives such as pressure confinement possible | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Vertical shear instability, ambipolar diffusion and magnetic reconnection rejected or unsupported for outer gaps  
  > "For the outer two perturbations, only the embedded planet scenario is able to succinctly account for all the observations." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): No gap cooling included, so planet masses are upper limits; planet not directly detected  
  > "our planet masses should be seen as an upper limit" (5 Discussion); "without the detection of a point source, we cannot unambiguously dismiss scenarios without a planet" (5 Discussion)
- Caveat (inferred, ours): Temperature perturbations neglected in the hydro models
- Caveat (inferred, ours): Only 2D isothermal models; fit by eye with no stated parameter grid or formal uncertainties
- Caveat (inferred, ours): Beam-scale resolution limits inner-region rotation

## Reproducibility

- Data public (paper): Archival ALMA data 2013.1.00601.S  
  > "We use archival data of the $J = 2-1$ transitions" (2 Observations)
- Products in archive: _not stated_
- Missing: GP and stacking implementation details
- Missing: Hydro model/LIME input files
- Missing: Full imaging parameters
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data, key method described, but many setup details inherited or unstated and no code released.
- Rediscovery candidate: no, Recipe depends on unreleased code and models and unspecified hydro fit details.

## Links

- Method: Pinte_ea_2018 (Emission surface height method)
- Method: Foreman-Mackey_ea_2017 (Gaussian Process (celerite))
- Companion: Isella_ea_2016 (Original presentation of the data and three-planet model)
- Companion: Flaherty_ea_2017 (Disk physical structure)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 38,
  "rate": 0.528
 },
 "evidence_ok": true
}
```
