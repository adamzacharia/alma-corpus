# The inhomogeneous submillimeter atmosphere of Betelgeuse

`2017A&A...602L..10O` | Astronomy and Astrophysics 2017 | first author: O'Gorman, E. | arXiv: 1706.06021 | DOI: 10.1051/0004-6361/201731171

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the thermal structure of Betelgeuse's extended atmosphere at ~1.3 R_star, and is it spherically symmetric or does it show localized heating?  
  > "The mechanisms responsible for heating the extended atmospheres of early-M spectral-type supergiants are poorly understood." (abstract)
- Target **Betelgeuse (alpha Ori, M2Iab)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00206.S
- bands: Band 7 (275-373 GHz), continuum at 338 GHz (0.89 mm)  
  > "during Cycle 3 in Band 7 ($275 - 373\,$GHz)" (Observations and analysis)
- frequencies and spectral setup: Five spws centered at 330.65, 332.55, 343.19, 345.15, 345.80 GHz  
  > "The observations were performed using five spectral windows (spws)." (Observations and analysis)
- continuum bandwidth: 4.1 GHz at 338 GHz  
  > "The total continuum bandwidth amounted to 4.1 GHz at a center frequency of 338 GHz" (Observations and analysis)
- arrays: 47 antennas  
  > "A total of 47 antennas were used to make the final calibrated visibility dataset." (Observations and analysis)
- configurations: _not stated_
- baselines: 0.078 to 16.076 km projected  
  > "projected baselines ranging from 0.078 to 16.076 km" (Observations and analysis)
- angular resolution: 15 x 13 mas beam (robust 0)  
  > "The restoring beam FWHM of $15\,\times\,13\,$mas" (Results)
- max recoverable scale: _not stated_
- sensitivity: 85 uJy/beam (robust 0)  
  > "85 $\mu$Jy beam$^{-1}$ (robust 0 images)" (Continuum imaging)
- time on source: 75 min total, 61 min on source  
  > "The observations lasted for 75 min with 61 min spent on source." (Observations and analysis)
- observing dates: 9 November 2015  
  > "on 9 November 2015 during Cycle 3" (Observations and analysis)
- pi or archival as stated: _not stated_
- External data: Photospheric effective temperature 3690 +/- 54 K  
  > "photospheric effective temperature of $3690\,\pm\,54\,$K (cite: ohnaka_2011)" (Discussion) [from (cite: ohnaka_2011)]
- External data: Mean gas temperature declining from ~3600 K at 2 R_star to 1400 K at 6 R_star  
  > "declines from approximately $3600\,$K at 2 R$_{\star}$ to 1400 K at 6 R$_{\star}$" (Discussion) [from (cite: lim_1998); (cite: ogorman_2015a)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline, manually inspected  
  > "The data were calibrated with the ALMA calibration pipeline and manually inspected and imaged using CASA 4.5.0." (Observations and analysis)
- casa version: CASA 4.5.0  
  > "imaged using CASA 4.5.0" (Observations and analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800, 3.0 Jy at 339.5 GHz, alpha = -0.25  
  > "assuming a flux density at 339.5 GHz of 3.0 Jy and a spectral index of $\alpha = -0.25$" (Observations and analysis)
- flux scale uncertainty: 5%  
  > "We estimate an absolute flux density uncertainty of 5%" (Observations and analysis)
- self calibration: Three phase-only iterations (15 s solint) then one amplitude+phase iteration  
  > "three iterations of phase-only self-calibration were performed on the continuum emission until a S/N convergence was reached with a solution interval of 15 sec." (Continuum imaging)

### Imaging

- task: _not stated_
- deconvolver: Multi-frequency synthesis CLEAN, nterms=2, multiscale  
  > "Two Taylor coefficients were used to model the linear frequency dependence of the continuum emission." (Continuum imaging)
- weighting robust: Briggs robust 0 (also robust -1 and uniform tested)  
  > "Briggs weighting and a robust parameter of 0" (Continuum imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 1, 3 x synthesized beam  
  > "scales approximately corresponding to 0, 1, and $3\,\times$ the synthesized beam" (Continuum imaging)
- continuum subtraction: Continuum split from line emission; channels averaged to 125 MHz  
  > "the continuum channel widths were averaged to 125 MHz" (Observations and analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 15 x 13 mas  
  > "synthetic beam size of $15\,\times \,13\,$mas at 338 GHz" (Continuum imaging)
- final rms: 85 uJy/beam (robust 0); 138 (robust -1); 255 (uniform)  
  > "138 $\mu$Jy beam$^{-1}$ (robust -1 images), and 255 $\mu$Jy beam$^{-1}$ (uniform images)" (Continuum imaging)

### Inherited from earlier work

- Absolute position check of Betelgeuse with J0605+0939  
  > "was used to check the absolute position of Betelgeuse (see (cite: harper_2017))" (Observations and analysis) [from (cite: harper_2017)]

### Not stated but needed to reproduce (our reading)

- Which spw channels were flagged as line-contaminated for the continuum
- Image size and cell size
- Initial uv-fit starting parameters and the fitting procedure details for UVMULTIFIT
- Stellar distance and R_star value used to convert 1.3 R_star
- Clean threshold and masks

## Analysis recipe

1. **Calibrate and image continuum with self-calibration**: ALMA pipeline calibration, continuum split, target shifted to phase center, multiscale MFS CLEAN with self-cal  
  > "A Gaussian profile was then fitted to the target in the initial continuum image to allow the target to be shifted to phase center." (Observations and analysis)
   - software: CASA
   - parameter: robust 0, nterms=2, scales 0,1,3 beams, solint 15 s  
  > "Briggs weighting and a robust parameter of 0" (Continuum imaging)
   - fitting: _not stated_
   - validation: Self-cal reduced rms by about an order of magnitude  
  > "self-calibrating the continuum data reduced the rms noise by approximately an order of magnitude" (Continuum imaging)
2. **Fit visibility models to quantify emission components**: Fit uniform elliptical disk plus Gaussians and thin ring to complex visibilities; residual images inspected after each fit; best model chosen by lowest reduced chi-squared and residuals  
  > "The model that produced the lowest reduced chi-squared statistic value as well as the lowest remaining residuals in the residual images is described in Table" (Results)
   - software: UVMULTIFIT, CASA uvsub
   - fitting: Least-squares visibility fitting with UVMULTIFIT; sampler/priors not stated  
  > "we used the UVMULTIFIT task version 2.2.0-r3" (Observations and analysis)
   - validation: Circular disk gave larger chi-squared; negative-flux Gaussians rejected  
  > "replacing the elliptical uniform intensity disk with a circular uniform intensity disk in the multi-component fits described previously produced larger chi-squared statistic values" (Residual images from uv-fitting)
3. **Derive brightness temperatures and spectral index**: Brightness temperature from fitted flux and size (Rayleigh-Jeans); spectral index from integrated flux in lower (331.86 GHz) and upper (344.09 GHz) band images; Eddington-Barbier Tb ~ Tgas  
  > "by separately imaging the lower (at 331.86 GHz) and upper (at 344.09 GHz) portions of the bandpass and calculating the integrated flux density in each image" (Results)
   - software: CASA
   - assumption: Tb ~ Tgas(tau=1) for slowly varying temperature; free-free H- opacity  
  > "Eddington-Barbier relations show that for temperatures varying slowly with optical depth $T_\textrm{b}\simeq T_\textrm{gas}(\tau=1)$" (Discussion)
   - fitting: _not stated_
   - validation: Compared with previous unresolved mm and cm spectral indices  
  > "This is slightly larger than the $\alpha = 1.57 \pm 0.05$ that can be derived from previous unresolved millimeter observations" (Results)

## Software

- **CASA** 4.5.0: Imaging, uvsub, self-calibration, clean  
  > "imaged using CASA 4.5.0" (Observations and analysis)
- **UVMULTIFIT** 2.2.0-r3: Direct fitting of visibilities  
  > "we used the UVMULTIFIT task version 2.2.0-r3" (Observations and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Uniform elliptical disk brightness temperature | 2760 | 140 | K | 2 | 2760$\pm$140 |
| Uniform disk major axis | 57.8 | 0.1 | mas | 2 | 57.8$\pm$0.1 |
| NE-peak total brightness temperature | 3815 | 165 | K | 3 | The total brightness temperature of the NE-peak was $3815\pm165$ K. |
| NE-peak axis ratio | 2.38 | 0.02 | dimensionless | 2 | 2.38$\pm$0.02 |
| East-extension brightness temperature | 2260 | 135 | K | 2 | its brightness temperature was $2260\pm 135$ K |
| Global spectral index | 1.67 | 0.09 | dimensionless | 3 | We find the global spectral index to be $\alpha = 1.67\,\pm 0.09$ |
| Disk flux density | 544.7 | 0.5 | mJy | 2 | 544.7$\pm$0.5 |

## Qualitative findings

- Emission is not spherically symmetric; localized heating likely tied to magnetic activity from convection  
  > "We suggest that the detected localized heating is related to magnetic activity generated by large-scale photospheric convection." (abstract)

## Claim tuples

- H: Is the mean temperature at ~1.3 R_star below the effective temperature (inversion)? | E: Fit uniform disk to 338 GHz visibilities and derive Tb | R: Tb = 2760 +/- 140 K vs Teff 3690 K | F: Temperature inversion exists in the atmosphere of a red supergiant | **supported**
- H: Is the sub-mm emission spherically symmetric? | E: Images and visibility model fitting with residual inspection | R: NE-peak (axis ratio 2.38, 3815 K) and east-extension detected | F: Localized heating asymmetries are present | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Circular uniform disk and negative-flux Gaussians were rejected  
  > "We also attempted fits by forcing the Gaussian components to have negative flux density values, but the fitted values were smaller than the fitting errors." (Residual images from uv-fitting)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited resolution smears fine structures and reduces contrast; spectral index errors may be underestimated  
  > "our limited spatial resolution would smear out these fine structures and would reduce the contrast in the brightness temperatures" (Discussion)
- Caveat (inferred, ours): Magnetic-activity interpretation is speculative and untested
- Caveat (inferred, ours): Single epoch, single band
- Caveat (inferred, ours): Model choice (thin ring) is ad hoc
- Caveat (inferred, ours): Brightness-temperature conversion for resolved components is not detailed

## Reproducibility

- Data public (paper): Project code and PI given; data from ALMA archive implied  
  > "(project code: 2015.1.00206.S, PI: P. Kervella)" (Observations and analysis)
- Products in archive: _not stated_
- Missing: Image/cell size
- Missing: Flagging and line-free channel selection
- Missing: UVMULTIFIT starting parameters
- Missing: R_star and distance
- Data volume (inferred): ~50-100 GB raw; one long-baseline Band 7 execution
- Score (inferred): 3/5, Public data and standard tools, but imaging details and fit setup are sparse.
- Rediscovery candidate: yes, Data are public, recipe is mostly clear, and results are numeric (Table 1).

## Links

- Method: (cite: marti_vidal_2014) (UVMULTIFIT visibility fitting)
- Companion: (cite: harper_2017) (Companion ALMA Betelgeuse paper; position check)
- Companion: (cite: ogorman_2015a) (Previous radio temperature profile of Betelgeuse)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 62,
  "stated": 39,
  "rate": 0.629
 },
 "evidence_ok": true
}
```
