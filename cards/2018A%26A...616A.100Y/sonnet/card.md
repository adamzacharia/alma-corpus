# Stellar masses and disk properties of Lupus young stellar objects traced by velocity-aligned stacked ALMA <SUP>13</SUP>CO and C<SUP>18</SUP>O spectra

`2018A&A...616A.100Y` | Astronomy and Astrophysics 2018 | first author: Yen, Hsi-Wei | arXiv: 1804.06272 | DOI: 10.1051/0004-6361/201732196

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Can velocity-aligned stacking of 13CO and C18O (3-2) data from the ALMA Lupus survey yield more detections, dynamical stellar masses, disk orientations and gas masses, and how do gas masses relate to dust masses and accretion rates?  
  > "we apply the velocity-aligned stacking method to extract more information from molecular-line data of these ALMA surveys and to study the kinematics and disk properties traced by molecular lines." (abstract)
- Target **88 Class II/flat-spectrum YSOs in Lupus (e.g. RY Lup, Sz 83, J16083070-3828268)**: coordinates not stated (obtained from Ansdell16)  
  > "The distance is adopted to be 200 pc for the sources in the Lupus III cloud and to be 150 pc for the sources in the Lupus I, II, and IV clouds" (Method); z/distance 200 pc (Lupus III); 150 pc (Lupus I, II, IV)  
  > "The distance is adopted to be 200 pc for the sources in the Lupus III cloud and to be 150 pc for the sources in the Lupus I, II, and IV clouds" (Method); distance from Comeron08  
  > "The distance is adopted to be 200 pc for the sources in the Lupus III cloud and to be 150 pc for the sources in the Lupus I, II, and IV clouds" (Method)

## Data provenance

- ALMA projects: 2013.1.00220.S
- bands: 0.9 mm continuum (Band 7), simultaneous with 13CO and C18O (3-2)  
  > "0.9 mm continuum, $^{13}$CO (3–2; 330.587965 GHz), and C$^{18}$O (3–2; 329.330552 GHz) were observed simultaneously." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.34 arcsec typical  
  > "The typical angular resolution achieved is $\sim$0.34$''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 70 and 67 mJy/beam per channel for 13CO and C18O  
  > "the typical noise levels per channel are 70 and 67 mJy beam$^{-1}$ for the $^{13}$CO (3–2) and C$^{18}$O (3–2) emission, respectively." (Observations)
- time on source: approximately one minute per source  
  > "were observed with an on-source integration time of approximately one minute per source." (Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 13CO 3-2 (330.587965 GHz)
- Line: C18O 3-2 (329.330552 GHz)
- External data: Spectroscopic stellar masses and mass accretion rates  
  > "$M_{\star,{\rm spec}}$ is the spectroscopically determined stellar mass from (cite: Alcala14; Alcala17)." (Table notes) [from (cite: Alcala14; Alcala17)]
- External data: Continuum fluxes, source coordinates, continuum PA and inclinations  
  > "The coordinates are obtained from (cite: Ansdell16)." (Method) [from (cite: Ansdell16; Tazzari17)]
- External data: Grids of physical-chemical disk models for gas mass  
  > "our measurements and the expected $^{13}$CO and C$^{18}$O line luminosities of protoplanetary disks with different masses from models by (cite: Williams14) and (cite: Miotello16)." (Measured Stellar Mass and Disk Properties) [from (cite: Williams14; Miotello16; Miotello17)]
- Simulation/model as data: 24 synthetic model disks (uniform/Gaussian, 0.2/0.5 Msun, 30/60 deg, 400-800 mJy km/s) simulated with CASA at C34-5, 1 min  
  > "Then, we used CASA to simulate ALMA observations with the array configuration of C34-5 and a one-minute integration time on our model image cubes" (Simple disk models)

## Processing

### Calibration

- pipeline or manual: standard reduction script for cycle-2 data  
  > "The raw visibility data were calibrated using the standard reduction script for the cycle-2 data" (Observations)
- casa version: CASA 4.2.2  
  > "(cite: McMullin07) of version 4.2.2" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "cleaned with the CASA task “clean” at a spectral resolution of 122 kHz" (Observations)
- deconvolver: _not stated_
- weighting robust: briggs, robust = +0.5  
  > "generated with the briggs weighting with a robust parameter of +0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectral resolution 122 kHz (0.11 km/s)  
  > "corresponding to a velocity resolution of 0.11 km s$^{-1}$" (Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Velocity-aligned stacking method and formulation  
  > "A detailed formulation is given in (cite: Yen16)." (Method) [from (cite: Yen16)]
- Observation details  
  > "The details of the observations have been described in (cite: Ansdell16)." (Observations) [from (cite: Ansdell16)]
- Gas mass estimation by comparing line luminosities with model grids  
  > "we followed the method in (cite: Ansdell16) and (cite: Miotello17)" (Measured Stellar Mass and Disk Properties) [from (cite: Ansdell16; Miotello17)]
- PV peak measurement method  
  > "following the method described in (cite: Yen13)" (Demonstration with observational data) [from (cite: Yen13)]

### Not stated but needed to reproduce (our reading)

- Code for the stacking/alignment and S/N search (not released)
- Exact clean parameters (image size, cell, threshold, masks)
- Continuum subtraction and line-free channels
- Exact outlier-trimming rule for S/N distribution
- Model-grid details for the luminosity-weighted gas mass averaging
- Dust mass conversion details (taken from Ansdell16/Miotello17)

## Analysis recipe

1. **Image 13CO and C18O cubes**: Calibrate with standard cycle-2 script and clean with Briggs weighting  
  > "cleaned with the CASA task “clean” at a spectral resolution of 122 kHz" (Observations)
   - software: CASA
   - parameter: robust +0.5; 0.11 km/s channels  
  > "robust parameter of +0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Grid search with velocity-aligned stacking for M*, PA, i, Vsys**: Shift spectra by projected Keplerian velocities, integrate within 1 arcsec de-projected radius, maximize S/N of Gaussian-weighted integrated intensity; uncertainties from parameter ranges giving consistent line profiles  
  > "we searched for the parameter set that maximized the S/N ratios of the aligned stacked spectra" (Method)
   - parameter: M* 0.1-3 Msun (0.1 steps); PA 0-355 deg (5); i 5-85 deg (5); Vsys 1.7-6.3 km/s (0.1)  
  > "$5\ensuremath{^\circ} \leq i \leq 85\ensuremath{^\circ}$ in steps of 5$\ensuremath{^\circ}$" (Method)
   - parameter: detection: peak >4 sigma and >=3 channels above 3 sigma within 2 sigma Gaussian width  
  > "the peak intensity of the best-aligned stacked spectrum is above 4$\sigma$ and (2) there are at least three channels above 3$\sigma$ within the 2$\sigma$ Gaussian line width." (Method)
   - assumption: geometrically thin Keplerian disk; stellar position at continuum center; distances 150/200 pc  
  > "the assumption that its disk traced by the $^{13}$CO and C$^{18}$O (3–2) lines is geometrically thin" (Method)
   - fitting: S/N-maximization grid search; Gaussian fits to stacked spectra  
  > "Then, we searched for the parameter set that maximized the S/N ratios of the aligned stacked spectra, and adopted this parameter set as our measurements of $M_\star$, PA, $i$, and $V_{\rm sys}$ of that source." (Method)
   - validation: Tested on 30 blank-field synthetic images (no detections), 3 bright sources vs PV diagram analysis, and 24 model disks  
  > "We have tested the method on 30 synthetic ALMA images of a blank field" (Method)
3. **Measure fluxes**: Apply best parameters; stack in radial bins (half-beam steps) to find detected radius (2 sigma); integrate within twice the FWHM line width; apply same to C18O  
  > "we measured the total integrated flux within twice of the FWHM line widths in the aligned stacked spectra." (Measured Stellar Mass and Disk Properties)
   - parameter: C18O detection above 4 sigma; 20% systematic flux uncertainty  
  > "We define that the C$^{18}$O emission is detected when the integrated flux is above the 4$\sigma$ threshold." (Measured Stellar Mass and Disk Properties)
   - assumption: 13CO and C18O trace the same regions  
  > "we assume that the $^{13}$CO and C$^{18}$O lines trace the same regions" (Measured Stellar Mass and Disk Properties)
   - fitting: _not stated_
   - validation: Compared with Ansdell16 fluxes  
  > "the mean difference is 10%" (Measured Stellar Mass and Disk Properties)
4. **Estimate disk gas masses**: Compare 13CO and C18O luminosities with Williams & Best 2014 and Miotello+16 grids (luminosity-weighted mean mass); Miotello+17 fitting function for 13CO-only disks  
  > "The estimated disk mass is then adopted to be the mean mass of those model disks weighted by the difference between the model and observed line luminosities." (Measured Stellar Mass and Disk Properties)
   - parameter: face-on vs edge-on fit function split at i=70 deg  
  > "whether $i$ is smaller or larger than 70$\ensuremath{^\circ}$" (Measured Stellar Mass and Disk Properties)
   - assumption: No volatile carbon depletion in the models  
  > "are based on the assumption that there is no depletion of volatile carbon and oxygen" (Gas-to-Dust Ratio and Disk Mass)
   - fitting: _not stated_
   - validation: Two grids consistent within uncertainties where both apply  
  > "As shown in Fig. [9](#mass2), the estimated gas masses with the two models are consistent within the uncertainties, when the observed line luminosities can be reproduced by both models." (Gas-to-Dust Ratio and Disk Mass)
5. **Gas-dust mass correlation**: Bayesian linear fit in log space with errors on both axes, using log of upper limit/measurement as 1 sigma  
  > "by using the routine of a Bayesian approach with errors of both axes written by (cite: Kelly07), *linmix_err*." (Gas-to-Dust Ratio and Disk Mass)
   - software: linmix_err
   - parameter: disks with dust mass <1e-6 Msun excluded  
  > "we exclude those disks in the following discussion." (Gas-to-Dust Ratio and Disk Mass)
   - fitting: linmix_err Bayesian regression  
  > "We performed a linear fit to the logarithms of the disk gas and dust masses by using the routine of a Bayesian approach with errors of both axes written by (cite: Kelly07), *linmix_err*." (Gas-to-Dust Ratio and Disk Mass)
   - validation: Robust to including upper limits for non-detections, dust mass source, 10% flux calibration uncertainty  
  > "our results do not depend on whether the disk dust masses are adopted from (cite: Ansdell16) or from (cite: Miotello17)" (Gas-to-Dust Ratio and Disk Mass)

## Software

- **CASA** 4.2.2: calibration, clean imaging, simulating ALMA observations  
  > "(cite: McMullin07) of version 4.2.2" (Observations)
- **Miriad** : imgen, velmodel, velimage to generate model disk cubes  
  > "We first used the *Mirad* tasks, *imgen* and *velmodel*, to generate intensity distributions and velocity patterns of model disks" (Simple disk models)
- **linmix_err** : Bayesian linear fit of gas vs dust mass  
  > "*linmix_err*" (Gas-to-Dust Ratio and Disk Mass)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 13CO detections | 41 of 88 | not stated | disks | 2 | We obtain $^{13}$CO detections in 41 disks and C$^{18}$O detections in 18 disks |
| Mean dynamical vs spectroscopic mass difference (16 sources) | 0.15 | not stated | Msun | 2 | The mean difference between the dynamical and spectroscopic stellar masses in this subsample is 0.15 $M_\ensuremath{\odot}$. |
| Slope of log gas vs log dust mass | 1.1 | 0.5 | dimensionless | 5 | with a slope of 1.1$\pm$0.5 and a correlation coefficient of 0.8$\pm$0.2 |
| Scatter of residual gas masses | 0.9 | not stated | dex | 5 | measured the standard deviation of the residual gas masses to be 0.9 dex |
| Median gas-to-dust ratio (dust mass >1e-6 Msun) | 12 | not stated | dimensionless | 5 | is relatively flat and has a median of 12 |
| Mean inclination difference vs continuum (23 disks) | 15 | not stated | deg | 2 | The mean difference of the disk inclination, $i$, measured from our method and from the continuum emission is 15$^\circ$ |

## Qualitative findings

- Disk gas mass shows no correlation with accretion rate, expected given large gas mass uncertainties  
  > "we still find no significant correlation between the mass accretion rate and the disk gas mass" (Discussion)

## Claim tuples

- H: Velocity-aligned stacking increases 13CO/C18O detections in Lupus | E: Stack 88 disks | R: 41 13CO and 18 C18O detections, 11 and 9 new | F: Method enhances S/N and gives more detections | **supported**
- H: Dynamical masses from stacking agree with spectroscopic masses | E: Compare for 37 sources and 16 with fixed continuum PA and i | R: Agree within 2 sigma for all 16; mean difference 0.15 Msun | F: Method is robust for stellar masses where inclination is constrained | **supported**
- H: Disk gas mass correlates with dust mass | E: linmix_err fit | R: slope 1.1±0.5, scatter 0.9 dex | F: Possible correlation but large scatter; depends on Miotello+17 fitting function | **partially**
- H: Gas mass correlates with accretion rate | E: Compare with new gas masses and simulations | R: No significant correlation | F: Not expected to be seen given the uncertainties | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar mass can be overestimated for fluxes ≲400 mJy km/s; inclination poorly constrained  
  > "when the total flux is as low as 400 mJy km s$^{-1}$, $M_\star$ can be overestimated" (Demonstration with models)
- Caveat (inferred, ours): Gas mass relation depends on model choice for 13CO-only disks
- Caveat (inferred, ours): Fixed distances of 150/200 pc for all sources
- Caveat (inferred, ours): Error bars treated as Gaussian in linmix_err though they are not

## Reproducibility

- Data public (paper): Data retrieved from ALMA archive  
  > "The data analyzed here were retrieved from the ALMA archive (project code: 2013.1.00220.S)." (Observations)
- Products in archive: _not stated_
- Missing: Stacking code
- Missing: Detailed clean settings and masks
- Missing: Dust mass conversion
- Data volume (inferred): ~50-100 GB raw for 88 short-integration sources
- Score (inferred): 6/5, Public data and a clear algorithm with parameter grids, but code and some imaging and conversion details are missing.
- Rediscovery candidate: yes, Public data and a clearly described method with numeric results, though code is needed to be rewritten.

## Links

- Method: (cite: Yen16) (velocity-aligned stacking method)
- Method: (cite: Miotello17) (gas mass fitting functions)
- Companion: (cite: Ansdell16) (original Lupus ALMA survey)
- Related: ALMA Lupus disk survey

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 80,
  "stated": 47,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
