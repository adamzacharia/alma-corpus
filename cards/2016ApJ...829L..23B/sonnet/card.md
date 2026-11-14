# ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe

`2016ApJ...829L..23B` | The Astrophysical Journal Letters 2016 | first author: Basu, K. | arXiv: 1608.05413 | DOI: 10.3847/2041-8205/829/2/L23

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: Can ALMA SZ measurements detect the pressure discontinuity of a merger shock at the NW radio relic of El Gordo, and what Mach number and relic magnetic field result when combined with Chandra and ATCA data?  
  > "Multi-wavelength analysis in combination with the archival *Chandra *data and a high-resolution radio image provides a consistent picture of the thermal and non-thermal signal variation across the shock front" (abstract)
- Target **El Gordo (ACT-CL J0102-4915) NW relic**: coordinates R.A., decl. = [15.723°, -49.264°] (shock model center)  
  > "The galaxy cluster ACT-CL J0102$-$4915 at $z=0.87$, nicknamed “El Gordo,” is the most massive high-redshift cluster known" (1 Introduction); "We take the midpoint of these arcs, at R.A., decl. $=[15.723{^{\circ}},-49.264{^{\circ}}]$, as the center of our spherical shock model" (2 Data and Analysis Methods); z/distance z = 0.87  
  > "The galaxy cluster ACT-CL J0102$-$4915 at $z=0.87$, nicknamed “El Gordo,” is the most massive high-redshift cluster known" (1 Introduction); "We take the midpoint of these arcs, at R.A., decl. $=[15.723{^{\circ}},-49.264{^{\circ}}]$, as the center of our spherical shock model" (2 Data and Analysis Methods); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01187.S
- bands: ~100 GHz continuum; four bands centered at 93, 95, 105 and 107 GHz  
  > "Four continuum bands were centered at 93, 95, 105 and 107, GHz, covering a total 7.5 GHz bandwidth." (2.3 ALMA-SZ data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz total  
  > "Four continuum bands were centered at 93, 95, 105 and 107, GHz, covering a total 7.5 GHz bandwidth." (2.3 ALMA-SZ data)
- arrays: ALMA main array, thirty-five 12-m antennas  
  > "The relic was observed by the ALMA main array in Cycle 3 during 2015 December, employing thirty-five 12-meter antennas" (2.3 ALMA-SZ data)
- configurations: most compact configuration  
  > "employing thirty-five 12-meter antennas in the most compact configuration" (2.3 ALMA-SZ data)
- baselines: _not stated_
- angular resolution: 3.6"x2.7" (P.A. 88°) synthesized beam  
  > "for a synthesized beam size of $3.6{^{\prime\prime}}\times 2.7{^{\prime\prime}}$ (P.A. $88{^{\circ}}$)" (2.3 ALMA-SZ data)
- max recoverable scale: _not stated_
- sensitivity: 6 µJy/beam rms at phase center  
  > "resulted in a noise rms of $6~ \mu$Jy/beam at the phase center" (2.3 ALMA-SZ data)
- time on source: 5.2 hr total, ~3 hr on-source  
  > "Total duration of the observation was 5.2 hr, which after calibration yielded roughly 3 hr of on-source data." (2.3 ALMA-SZ data)
- observing dates: 2015 December (Cycle 3)  
  > "The relic was observed by the ALMA main array in Cycle 3 during 2015 December" (2.3 ALMA-SZ data)
- pi or archival as stated: PI: K. Basu (own program)  
  > "(2015.1.01187.S; PI: K. Basu)" (2.3 ALMA-SZ data)
- Other facility **Chandra**: Archival 360 ks X-ray data (ObsID 12258, 14022, 14023)  
  > "We use archival *Chandra *data for El Gordo totaling 360 ks of observation (ObsID: 12258, 14022, 14023)." (2.2 Chandra X-Ray data)
- Other facility **ATCA**: 2.1 GHz high-resolution total intensity radio image, 6.1"x3.1"  
  > "The effective resolution is $6.1{^{\prime\prime}}\times 3.1{^{\prime\prime}}$" (2.1 ATCA 2.1 GHz radio data)
- Other facility **HST**: RGB color image for overview figure  
  > "The left panel shows an RGB-color image made from two *Hubble Space Telescope* (HST) pointings" (2 Data and Analysis Methods)
- External data: Weak-lensing total mass M500,c = 1.80±0.34e15 Msun used as prior  
  > "Putting a weak-lensing prior on the total mass ($M_{500,c}=1.80\pm 0.34 \times 10^{15}$ M$_{\odot}$; (cite: Jee14))" (3.1 SZ shock modeling) [from (cite: Jee14)]
- External data: ATCA 2.1 GHz radio image, analysis described in Lindner et al. 2014  
  > "we use a high-resolution total intensity image made from the ATCA 2.1 GHz observation" (2.1 ATCA 2.1 GHz radio data) [from Lindner et al. 2014 (L14)]
- Simulation/model as data: Mock ALMA observations of M=1, 2, 4 shock models on a massive El Gordo-like cluster, noise from randomized phases  
  > "simulating a ${\cal M}=1$, 2, or 4 shock model on a massive El Gordo-like cluster. The noise is obtained from randomizing the phases in individual scans." (2.3 ALMA-SZ data)

## Processing

### Calibration

- pipeline or manual: ALMA-provided calibrated products with a few additional flaggings  
  > "We used the calibrated data products obtained with the CASA software as provided by the ALMA project, with a few additional flaggings." (2.3 ALMA-SZ data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: yes, apart from extra flagging  
  > "We used the calibrated data products obtained with the CASA software as provided by the ALMA project, with a few additional flaggings." (2.3 ALMA-SZ data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN (illustration only); modeling fit directly to uv-data  
  > "we *do not* use any imaging product for the shock modeling, rather fit our model directly to the ALMA $uv$-data" (2.3 ALMA-SZ data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Imaging using CLEAN with natural weighting resulted in a noise rms of $6~ \mu$Jy/beam at the phase center" (2.3 ALMA-SZ data)
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
- final beam: 3.6"x2.7", P.A. 88°  
  > "for a synthesized beam size of $3.6{^{\prime\prime}}\times 2.7{^{\prime\prime}}$ (P.A. $88{^{\circ}}$)" (2.3 ALMA-SZ data)
- final rms: 6 µJy/beam  
  > "resulted in a noise rms of $6~ \mu$Jy/beam at the phase center" (2.3 ALMA-SZ data)

### Inherited from earlier work

- Radio data analysis of ATCA image  
  > "The radio data analysis is described in , we use a high-resolution total intensity image" (2.1 ATCA 2.1 GHz radio data) [from Lindner et al. 2014 (L14)]
- Lognormal emissivity model for relic  
  > "We use a lognormal emissivity model ((cite: szrelic)) that is projected from a 3D cone and smoothed to the ATCA resolution." (2.1 ATCA 2.1 GHz radio data) [from (cite: szrelic)]
- Broken power-law density model for X-ray  
  > "The X-ray brightness is modeled with a standard broken power law in density (cite: Eck16)" (2.2 Chandra X-Ray data) [from (cite: Eck16)]
- GNFW pressure model with shallow outer slope  
  > "we choose GNFW model parameters with a shallow outer pressure slope (cite: Say13) and marginalize its value within 30% uncertainty" (2.3 ALMA-SZ data) [from (cite: Say13)]
- Relativistic SZ spectrum corrections  
  > "The $93-107$ GHz SZ spectrum is computed with relativistic corrections ((cite: Ito04))" (2.3 ALMA-SZ data) [from (cite: Ito04)]

### Not stated but needed to reproduce (our reading)

- Additional flagging details for the ALMA data
- Specifics of the MCMC-in-CASA uv-fitting code, sampler and priors
- CASA and CIAO versions (only CALDB 4.7.1 given)
- CLEAN parameters (cell, size, masking, threshold)
- GNFW parameter values and priors on amplitude, shock radius, Mach number
- Binning of Chandra profile and X-ray temperature fitting details
- Priors for the radio/B-field calculation and cooling assumptions
- Exact upstream-temperature scaling chain

## Analysis recipe

1. **Fit radio relic profile**: Fit lognormal emissivity model projected from 3D cone, smoothed to ATCA beam, to radial brightness profile  
  > "We use a lognormal emissivity model ((cite: szrelic)) that is projected from a 3D cone and smoothed to the ATCA resolution." (2.1 ATCA 2.1 GHz radio data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Model Chandra X-ray brightness for shock**: Broken power-law density, spherical projection, fit to 0.5-2 keV brightness with MCMC; Rankine-Hugoniot density jump  
  > "This model is projected assuming a spherical geometry and fit to the $0.5-2$ keV brightness profile using a Markov Chain Monte Carlo (MCMC) method." (2.2 Chandra X-Ray data)
   - software: CIAO
   - parameter: Fit limited to 400 kpc downstream; shock cone 26°-94°; background marginalized over 5%  
  > "we limit the fit to 400 kpc downstream" (2.2 Chandra X-Ray data)
   - assumption: Adiabatic index 5/3, spherical geometry  
  > "The shock density jump is derived from the standard Rankine-Hugoniot (R-H) condition (with adiabatic index 5/3)" (2.2 Chandra X-Ray data)
   - fitting: MCMC  
  > "fit to the $0.5-2$ keV brightness profile using a Markov Chain Monte Carlo (MCMC) method" (2.2 Chandra X-Ray data)
   - validation: _not stated_
3. **Fit SZ shock model to ALMA uv-data**: GNFW pressure plus R-H pressure boost at shock radius, fit directly to visibilities by MCMC within CASA  
  > "This is done using an MCMC method within CASA and is computationally expensive, due to the large data volume." (2.3 ALMA-SZ data)
   - software: CASA
   - parameter: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30%  
  > "leaving the pressure amplitude, shock radius and the Mach number as free parameters" (2.3 ALMA-SZ data)
   - assumption: p_down/p_up = (5M^2-1)/4  
  > "$p_{\mathrm{down}}/p_{\mathrm{up (GNFW)}} = (5{\cal M}^2 -1)/4$" (2.3 ALMA-SZ data)
   - fitting: MCMC  
  > "This is done using an MCMC method within CASA" (2.3 ALMA-SZ data)
   - validation: Mock ALMA observations with M=1, 2, 4 shocks  
  > "We make extensive simulations for mock ALMA observations" (2.3 ALMA-SZ data)
4. **Joint SZ/X-ray Mach number**: Derive pre-shock pressure prior from X-ray density and temperature (upstream T scaled from downstream T via R-H) and apply to SZ fit  
  > "we scale from the downstream $T_\mathrm{X}$ value using the Mach number in a chain, from the R-H condition for temperature jump." (3.3 Joint SZ/X-Ray modeling)
   - parameter: Post-shock T_X from 1' region = 16.8 keV  
  > "The post-shock temperature is measured from a wider $1{^{\prime}}$ region ($T_\mathrm{X} = 16.8^{+2.4}_{-1.8}$ keV)" (3.3 Joint SZ/X-Ray modeling)
   - assumption: Upstream X-ray density and temperature measurements independent  
  > "we use a pressure prior assuming the upstream X-ray density and temperature measurements are independent" (3.3 Joint SZ/X-Ray modeling)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate relic magnetic field**: Relic width = velocity x radiative lifetime of electrons, using Mach number and upstream temperature  
  > "assuming the relic’s width to be roughly equal to the product of the velocity and the radiative lifetime of the non-thermal electrons" (3.4 Radio modeling and the relic $B$-field)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibrated data products, CLEAN imaging, MCMC uv-fitting  
  > "This is done using an MCMC method within CASA and is computationally expensive" (2.3 ALMA-SZ data)
- **CIAO** CALDB 4.7.1: Chandra data reduction  
  > "The data are reduced with the CIAO software (CALDB 4.7.1)" (2.2 Chandra X-Ray data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SZ shock radius | 870 | +14/-13 | kpc | 3 | $r_{\mathrm{sh}}=870^{+14}_{-13}$ kpc |
| Mach number from SZ alone | 1.4 | +1.2/-0.2 | dimensionless | 3 | ${\cal M}= 1.4^{+1.2}_{-0.2}$, supporting ${\cal M}> 1$ at more than $98\%$ confidence |
| Mach number SZ with weak-lensing mass prior | 1.5 | +0.5/-0.2 | dimensionless | 3 | reduces the errors to ${\cal M}= 1.5^{+0.5}_{-0.2}$ |
| X-ray shock radius | 854 | +11/-13 | kpc | 2 | at $854^{+11}_{-13}$ kpc |
| X-ray Mach number (with SZ radius prior) | 3.5 | +6.4/-1.3 | dimensionless | 2 | we obtain a Mach number $3.5^{+6.4}_{-1.3}$ |
| Joint SZ/X-ray Mach number | 2.4 | +1.3/-0.6 | dimensionless | 4 | ${\cal M}= 2.4^{+1.3}_{-0.6}$ |
| Post-shock temperature | 16.8 | +2.4/-1.8 | keV | 4 | $T_\mathrm{X} = 16.8^{+2.4}_{-1.8}$ keV |
| Relic magnetic field | 4-10 | not stated | µG | 5 | of the order of $4-10~\mu$G |
| Radio-fit shock radius | 882 | not stated | kpc | 1 | a shock radius 882 kpc that is consistent with the SZ measurement |

## Qualitative findings

- ALMA SZ data alone show a pressure discontinuity (shock) at >98% confidence; Mach number degenerate with pressure normalization due to short-spacing limitation  
  > "This is an inherent limitation of the current ALMA observation (‘short-spacing’ problem)." (2.3 ALMA-SZ data)

## Claim tuples

- H: Does ALMA detect a pressure discontinuity at El Gordo's NW relic? | E: uv-plane MCMC fit of GNFW+shock model to ALMA 100 GHz data | R: M=1.4 +1.2/-0.2, M>1 at >98% | F: Shock detected via SZ at z=0.87 | **supported**
- H: What is the shock Mach number combining SZ and X-ray? | E: Pressure prior from Chandra applied to SZ fit | R: M=2.4 +1.3/-0.6 | F: Stronger shock preferred, consistent with radio | **supported**
- H: What magnetic field does the relic width imply? | E: Lognormal emissivity fit and width-lifetime argument | R: 3D width ~15 kpc requires 4-10 µG | F: Unexpectedly high field for this redshift | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-fitting avoids biases from imaging a diffuse low S/N negative signal  
  > "The $uv$-fitting method safeguards against possible biases that can occur when imaging a diffuse, low S/N negative signal like a cluster shock in SZ." (2.3 ALMA-SZ data)
- Alternative: Global weak-lensing mass prior rejected as inaccurate for a disturbed sector, replaced by X-ray pressure prior  
  > "for a merging cluster like El Gordo a global mass prior will be inaccurate for modeling the pressure in a disturbed sector, so we derive a pressure prior from the X-ray data." (3.1 SZ shock modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Short-spacing problem makes Mach number anti-correlated with pressure normalization  
  > "its amplitude is anti-correlated with the pressure normalization. This is an inherent limitation of the current ALMA observation" (2.3 ALMA-SZ data)
- Limitation (authors): Pre-shock temperature unconstrained in Chandra data  
  > "the pre-shock temperature in this high-$z$ object remains unconstrained due to the high background-to-cluster photon ratio" (3 Results and Discussion)
- Caveat (inferred, ours): Spherical shock geometry in a disturbed merger
- Caveat (inferred, ours): Wide Mach uncertainties; joint result driven by X-ray prior
- Caveat (inferred, ours): B-field depends on width-lifetime assumption
- Caveat (inferred, ours): Short-spacing filtering without ACA data

## Reproducibility

- Data public (paper): Chandra archival; ALMA project code given  
  > "We use archival *Chandra *data for El Gordo totaling 360 ks of observation" (2.2 Chandra X-Ray data)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: uv-fitting MCMC code and priors
- Missing: ATCA image
- Missing: additional flagging list
- Missing: GNFW parameters
- Data volume (inferred): ~50-100 GB for ALMA plus ~few GB Chandra
- Score (inferred): 3/5, Data public and numeric results, but custom uv-MCMC code and priors not given.
- Rediscovery candidate: no, Custom uv-plane MCMC and unstated priors prevent a complete recipe.

## Links

- Method: (cite: szrelic) Basu et al. 2016 (Lognormal relic emissivity model)
- Method: (cite: Eck16) (Broken power-law X-ray density model)
- Companion: (cite: Lind14) (ATCA radio data and relics of El Gordo)
- Companion: (cite: Men12) (Multiwavelength analysis of El Gordo merger)
- Related: ACT survey

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 82,
  "stated": 51,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
