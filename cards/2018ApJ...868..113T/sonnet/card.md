# Evidence for a Vertical Dependence on the Pressure Structure in AS 209

`2018ApJ...868..113T` | The Astrophysical Journal 2018 | first author: Teague, Richard | arXiv: 1810.04961 | DOI: 10.3847/1538-4357/aae836

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Can an improved Gaussian-Process rotation-velocity method applied to archival 12CO data of AS 209 reveal pressure perturbations and their relation to mm and NIR rings?  
  > "We present an improved method to measure the rotation curves for disks with non-axisymmetric brightness profiles initially published in (cite: Teague_ea_2018a)." (abstract)
- Target **AS 209**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00486.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12CO natural weighting: 0.23'' x 0.19'' at PA -79.3 deg; continuum uniform: 0.15'' x 0.13''  
  > "yielding beam sizes of $0.23\ensuremath{''} \times 0.19\ensuremath{''}$ at a position angle of $-79.3\ensuremath{^\circ}$" (3.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: 12CO rms 3.3 mJy/beam per channel; continuum rms 65 uJy/beam  
  > "The RMS noise in a line free channel was $3.3~{\rm mJy~beam^{-1}}$" (3.1 Observations); "A RMS noise of $\sigma = 65~\mu {\rm Jy~beam^{-1}}$ was measured in continuum free regions of the continuum map" (3.1 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, PI Fedele  
  > "we use archival data of AS 209 (2015.1.00486.S, PI Fedele, D.)" (3 The Rotation Curve of AS 209)
- Line: 12CO not stated (not stated)
- Other facility **VLT/SPHERE scattered light**: NIR scattered light data of AS 209 from Avenhaus et al. 2018, shared by H. Avenhaus  
  > "Henning Avenhaus for sharing the scattered light data" (Acknowledgments)
- External data: Model structure parameters (surface density, CO abundance) taken from Huang et al. 2016  
  > "with specific values taken from (cite: Huang_ea_2016)" (4.1 The Toy Model) [from (cite: Huang_ea_2016)]
- External data: Scattered-light radial profile and preferred disk orientation  
  > "the $r^2$-scaled scattered light intensity from (cite: Avenhaus_ea_2018)" (4.3 Pressure Profile) [from (cite: Avenhaus_ea_2018)]

## Processing

### Calibration

- pipeline or manual: Provided scripts in CASA 4.4, then CASA 5.2 for imaging and self-calibration  
  > "The data were calibrated using the provided scripts in `casa v4.4` before moving to `casa v5.2` for the imaging and self-calibration." (3.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase gains from continuum window applied to the three 12CO windows  
  > "Phase gain tables were calculated on the continuum window then applied to the three spectral line windows containing $^{12}$CO emission." (3.1 Observations)

### Imaging

- task: tclean  
  > "Using the `tclean` task, we first image the emission with natural weighting" (3.1 Observations)
- deconvolver: _not stated_
- weighting robust: natural for 12CO; uniform for continuum  
  > "Therefore we use natural weighting for the imaging" (3.1 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask from first-moment fit, convolved with beam  
  > "The data were then imaged and CLEANed again using this Keplerian mask." (3.1 Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, linear interpolation from line-free channels; also case without subtraction  
  > "The continuum is removed using the task `uvcontsub` which linearly interpolates the the continuum from line-free channels in the $uv$-plane." (3.1 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.23'' x 0.19'', PA -79.3 deg, ~160 m/s channels  
  > "The data were imaged at a velocity resolution of $\approx 160~{\rm m\,s^{-1}}$ ($\approx 244~{\rm kHz}$)." (3.1 Observations)
- final rms: 3.3 mJy/beam per channel  
  > "The RMS noise in a line free channel was $3.3~{\rm mJy~beam^{-1}}$" (3.1 Observations)

### Inherited from earlier work

- Data reduction process  
  > "Data reduction followed the same process as outlined in (cite: Fedele_ea_2018)." (3.1 Observations) [from (cite: Fedele_ea_2018)]
- Rotation velocity measurement method (modified here)  
  > "Following the method in (cite: Teague_ea_2018a) and with the modification described in Section [2](#sec:methodology) we measure an azimuthally averaged rotation profile." (3.2 Measuring Rotation Curves) [from (cite: Teague_ea_2018a)]
- Inclination fixed at 35.3 deg  
  > "holding the inclination constant at $i = 35.3\ensuremath{^\circ}$ (cite: Fedele_ea_2018)" (3.1 Observations) [from (cite: Fedele_ea_2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Self-calibration solution intervals
- Clean threshold, cell and image size, and number of iterations
- Priors and walker/step settings for the emcee Keplerian fit
- Gaussian-Process kernel and hyperparameters in celerite
- Rest frequency/transition of 12CO and distance to AS 209
- Details of the six-Gaussian perturbation fit (priors, parametrisation)
- Source of the continuum profile used in Fig. 6

## Analysis recipe

1. **Image continuum and 12CO**: tclean with Keplerian mask from moment-map fit; natural weighting for 12CO  
  > "The data were then imaged and CLEANed again using this Keplerian mask." (3.1 Observations)
   - software: CASA
   - parameter: 160 m/s channels  
  > "The data were imaged at a velocity resolution of $\approx 160~{\rm m\,s^{-1}}$ ($\approx 244~{\rm kHz}$)." (3.1 Observations)
   - assumption: i = 35.3 deg fixed  
  > "holding the inclination constant at $i = 35.3\ensuremath{^\circ}$ (cite: Fedele_ea_2018)" (3.1 Observations)
   - fitting: _not stated_
   - validation: Mask checked to encompass whole emission  
  > "checked to encompass the whole emission" (3.1 Observations)
2. **Fit Keplerian pattern and emission surface**: Fit line-of-sight velocity map (parabola fit to peak pixel) with conical emission surface, convolved with beam  
  > "we fit a Keplerian pattern, including a conical emission surface (cite: Rosenfeld_ea_2013) using the MCMC ensemble sampler `emcee`" (3.2 Measuring Rotation Curves)
   - software: emcee, bettermoments
   - assumption: i = 35.3 deg fixed; z = r tan psi  
  > "The emission surface is calculated as $z = r \cdot \tan \psi$" (3.2 Measuring Rotation Curves)
   - fitting: emcee; uncertainties are posterior standard deviations  
  > "The uncertainties are the standard deviation of the posterior distribution." (3.2 Measuring Rotation Curves)
   - validation: Emission height cross-checked with Pinte et al. 2018 method, psi ~13 deg  
  > "we find good agreement with a conical model with $\psi \approx 13\ensuremath{^\circ}$" (3.2 Measuring Rotation Curves)
3. **Measure azimuthally averaged rotation curve**: Deproject spectra into annuli, shift by v_rot cos(theta), stack, model stack as Gaussian Process and minimise residual variance; annuli of quarter beam  
  > "we then bin the data into annuli with a width of a quarter of the beam ($\approx 0.05\ensuremath{''}$) and derive a $v_{\rm rot}$ value." (3.2 Measuring Rotation Curves)
   - software: eddy, celerite
   - parameter: three cases: flared, thin, flared without continuum subtraction  
  > "firstly we deproject the sky-plane coordinates into disk coordinates to correctly account for the flaring, secondly we consider a geometrically thin disk, and finally we consider the flared disk with no continuum subtraction." (3.2 Measuring Rotation Curves)
   - fitting: Gaussian Process via celerite; radial profile also modelled as GP  
  > "We further model the radial profile as a Gaussian Process, requiring the profile to be smoothly varying" (3.2 Measuring Rotation Curves)
   - validation: Simulated spectra tests (Appendix); three cases consistent within 3 sigma  
  > "All three scenarios yield comparable radial $v_{\rm rot}$ profiles which are consistent within $3\sigma$ of one another." (3.2 Measuring Rotation Curves)
4. **Model perturbed physical structure to reproduce rotation residuals**: Toy disk model; power laws for T, n, z of 12CO layer; multiply one property by a sum of six Gaussians, fix others, compute v_rot and fit to observed  
  > "we model a perturbation vector as a sum of six Gaussian curves and multiply the power-law describing that property by this to create a perturbed profile" (4.2 Perturbations)
   - software: emcee
   - parameter: 30 au <= r <= 320 au  
  > "$30~{\rm au} \leq r \leq 320~{\rm au}$" (4.2 Perturbations)
   - assumption: Disk mass 0.035 Msun, CO abundance 1.7e-6, Dartois temperature structure  
  > "we chose a relative abundance of $x({\rm CO}) = 1.7 \times 10^{-6}$" (4.1 The Toy Model)
   - fitting: MCMC; scatter of 200 draws shown  
  > "The error bars on the perturbed model represents the scatter of 200 draws from the MCMC fitting." (4.2 Perturbations)
   - validation: Compared with brightness temperature and emission surface  
  > "Large changes in temperature as shown in panel (b) can be ruled out by the line emission as $T_B \leq T_{\rm gas}$" (4.2 Perturbations)
5. **Compute pressure profile and compare with rings**: Pressure from perturbed T and n; compare maxima with mm continuum and scattered-light rings  
  > "From the perturbed radial profiles of $T_{^{12}\rm CO}$ and $n_{^{12}\rm CO}$ we can calculate the pressure profile traced by the $^{12}$CO emission." (4.3 Pressure Profile)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4 (calibration), 5.2 (imaging): calibration, self-calibration, imaging, uvcontsub, tclean  
  > "The data were calibrated using the provided scripts in `casa v4.4` before moving to `casa v5.2` for the imaging and self-calibration." (3.1 Observations)
- **eddy** 1.0: rotation velocity measurement  
  > "Version 1.0 of the code used for this paper can be obtained from <https://doi.org/10.5281/zenodo.1440051>." (2 Measuring The Rotation Velocity)
- **celerite** : Gaussian Process modelling of stacked spectra  
  > "In practice this is performed using the Python package `celerite`" (2 Measuring The Rotation Velocity)
- **emcee** : MCMC fit of Keplerian pattern  
  > "using the MCMC ensemble sampler `emcee`" (3.2 Measuring Rotation Curves)
- **bettermoments** : line-of-sight velocity map via parabola fit  
  > "which fits a parabola to the pixel of peak intensity and its two neighbouring pixels" (3.2 Measuring Rotation Curves)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass from Keplerian fit (i=35.3 deg) | 1.16 | 0.01 | Msun | 2 | $M_{\star} = 1.16 \pm 0.01~M_{\rm sun}$ |
| Position angle | 86.7 | 0.1 | deg | 2 | ${\rm PA} = 86.7\ensuremath{^\circ} \pm 0.1\ensuremath{^\circ}$ |
| v_LSR | 4670 | 5 | m/s | 2 | $v_{\rm LSR} = 4670 \pm 5~{\rm m\,s^{-1}}$ |
| Emission surface angle psi | 13.1 | 0.3 | deg | 2 | $\psi = 13.1\ensuremath{^\circ} \pm 0.3\ensuremath{^\circ}$ |
| 12CO integrated flux | 7.99 | not stated | Jy km/s | 1 | we measure an integrated flux of 7.99 Jy km s$^{-1}$ |
| Continuum integrated intensity | 251 | not stated | mJy | 1 | an integrated intensity of 251 mJy was measured |
| Thin-disk reference Keplerian stellar mass (i=35.7 deg) | 1.25 | not stated | Msun | 3 | resulting in $M_{\rm star} = 1.25~M_{\rm sun}$ |
| Cloud absorption of 12CO on western side | ~30 | not stated | percent | 1 | the cloud absorbs $\approx 30\%$ of the $^{12}$CO emission on the Western side of the disk |
| Max deviation from Keplerian rotation | up to 5 | not stated | percent | 3 | shows substantial deviations from Keplerian rotation of up to $\pm 5\%$ |

## Qualitative findings

- Inner two mm and NIR rings lie at pressure maxima; outer scattered-light ring at ~250 au sits at the edge of a pressure minimum  
  > "The outer ring in scattered light, however, appears at the outer edge of a large pressure minimum centred at $\approx 250$ au." (3.2 Measuring Rotation Curves)

## Claim tuples

- H: Does AS 209's rotation curve deviate from Keplerian due to pressure perturbations? | E: GP-based rotation curve of 12CO, residuals vs thin Keplerian | R: Deviations up to ±5%, including a feature at ~250 au | F: Pressure perturbations are present, including one detected only kinematically | **supported**
- H: Are rings in NIR and mm emission coincident with pressure maxima? | E: Compare inferred pressure profile with continuum and scattered light profiles | R: Better match with micron-sized grains than mm | F: Vertical dependence of pressure maxima location | **partially**
- H: Is continuum subtraction affecting the rotation profile? | E: Compare profiles with and without subtraction | R: Consistent within 3 sigma | F: No significant effect | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Sensitivity matters more than resolution for precise v_rot, so natural weighting used  
  > "For precise measurements of $v_{\rm rot}$, sensitivity is more important than spatial resolution." (3.1 Observations)
- Alternative: Emission height perturbations rejected as they require larger deviations than allowed  
  > "Changes in the emission height, shown in panel (c), require larger deviations, particularly between 150 and 250 au, than are allowed from observations." (4.2 Perturbations)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution (~29 au) leaves velocity features unresolved, underestimating depth  
  > "the velocity features are not resolved and so will underestimate the true depth" (4.3 Pressure Profile)
- Limitation (authors): Cannot disentangle pressure gradient from stellar mass; pressure scaling depends on assumed density  
  > "we are unable to disentangle large scale effects of the pressure gradient from the stellar mass" (3.2 Measuring Rotation Curves)
- Caveat (inferred, ours): Toy model degenerate: temperature, density and height changes are treated one at a time
- Caveat (inferred, ours): Cloud absorption strongly affects western side
- Caveat (inferred, ours): Pressure offsets between mm and NIR rings are small relative to resolution
- Caveat (inferred, ours): Distance and ring positions rely on external data

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "we use archival data of AS 209 (2015.1.00486.S, PI Fedele, D.)" (3 The Rotation Curve of AS 209)
- Products in archive: _not stated_
- Code: eddy on GitHub and Zenodo v1.0  
  > "Examples of the code used for this and Jupyter Notebooks containing guides on how to use them can be found at <https://github.com/richteague/eddy>." (2 Measuring The Rotation Velocity)
- Missing: Exact imaging parameters (cell, size, threshold)
- Missing: MCMC priors and GP settings
- Missing: Scattered-light and continuum profile data
- Missing: Perturbation fit details
- Data volume (inferred): tens of GB (calibrated multi-EB band 6 CO line data)
- Score (inferred): 3/5, Public data and released code, but many imaging and fitting settings are unstated and the model fit is under-specified.
- Rediscovery candidate: no, Rotation curve is reproducible with eddy, but the perturbation modelling and external data are incompletely specified.

## Links

- Method: (cite: Teague_ea_2018a) (Original rotation-curve method)
- Method: (cite: Foreman-Mackey_ea_2017) (celerite Gaussian Process)
- Method: (cite: Teague_Foreman-Mackey_2018) (bettermoments velocity map method)
- Companion: (cite: Fedele_ea_2018) (Continuum data and reduction of the same project)
- Companion: (cite: Huang_ea_2016) (CO isotopologue ring structure and model parameters)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 48,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
