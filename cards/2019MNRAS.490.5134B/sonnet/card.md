# Detecting the halo heating from AGN feedback with ALMA

`2019MNRAS.490.5134B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Brownson, S. | arXiv: 1910.02088 | DOI: 10.1093/mnras/stz2945

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Can the SZ decrement from AGN-heated halo gas around quasar HE0515-4414 be detected in the ALMA visibility plane after subtracting compact positive sources?  
  > "We use a deep ALMA observation of HE0515-4414 in band 4, the most luminous quasar known at the peak of cosmic star formation (z=1.7), to search for the SZ signal tracing the heating of the galaxy’s halo." (abstract)
- Target **HE0515-4414**: coordinates RA = 05:17:07.63, Dec = -44.10.55.5  
  > "with the phase centred at the location of the quasar (RA = 05:17:07.63, Dec = -44.10.55.5)" (2 ALMA observations and data reduction); z/distance z=1.7  
  > "with the phase centred at the location of the quasar (RA = 05:17:07.63, Dec = -44.10.55.5)" (2 ALMA observations and data reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00309.S
- bands: Band 4, 12m array  
  > "HE0515-4414 was observed during ALMA cycle 4 in band 4 using the 12m array" (2 ALMA observations and data reduction)
- frequencies and spectral setup: 4 SPWs centred at 133, 135, 145, 147 GHz, 128 channels each, 2 GHz each, 8 GHz total  
  > "The SPWs are centred at 133, 135, 145 and 147 GHz, each with 128 channels covering a 2 GHz band." (2 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 384 m  
  > "a minimum baseline length of 15m and maximum of 384m" (2 ALMA observations and data reduction)
- angular resolution: 3.2x2.3 arcsec2, ~20 kpc  
  > "producing a synthesised beam with size 3.2$\times$2.3 arcsec$^{2}$" (2 ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: RMS 3.8 uJy/beam achieved; proposed 4.7 uJy/beam  
  > "an RMS noise level of 3.8 $\mu$Jy beam$^{-1}$ is reached" (2.1 Identification of emission sources)
- time on source: 11.6 hours, 14 execution blocks  
  > "with a total on-source time of 11.6 hours" (2 ALMA observations and data reduction)
- observing dates: January-March 2017  
  > "The quasar was observed between January and March 2017 across 14 execution blocks" (2 ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- External data: FABLE simulation SZ y-parameter maps and halo properties of a similar object  
  > "we use the results of the FABLE simulations (Feedback Acting on Baryons in Large-scale Environments) (cite: Henden2018) to simulate observations of the SZ emission with ALMA." (Comparison with Simulations) [from (cite: Henden2018)]
- External data: Black hole mass of HE0515-4414 ~4.3e10 Msun  
  > "${M}_{BH}\approx4.3\times{10}^{10}{M}_{\odot}$ (cite: Lacy2018)" (Comparison with Simulations) [from (cite: Lacy2018)]
- Simulation/model as data: FABLE SZ map of a similar object (M_BH 2.0e10 Msun, z=1.4) observed with CASA simobserve, 10 h, config C40-1  
  > "We simulate observations of the object using the CASA task *simobserve* with 10 hours of on-source time and the same spectral setup as in the real observation." (Comparison with Simulations)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated using the ALMA pipeline in CASA 4.7.2" (2 ALMA observations and data reduction)
- casa version: CASA 4.7.2  
  > "The data were calibrated using the ALMA pipeline in CASA 4.7.2" (2 ALMA observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0538-4405 and Mars (phase cal J0519-4546)  
  > "J0519-4546 was used as the phase calibrator, and J0538-4405 and Mars were used as flux calibrators." (2 ALMA observations and data reduction)
- flux scale uncertainty: ~5 per cent  
  > "The calibration yields an absolute flux uncertainty of $\sim$5 per cent at the observed frequency" (2 ALMA observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "we have also produced an image of the continuum emission using the CASA task *tclean* with the the Högbom deconvolving algorithm" (2.1 Identification of emission sources)
- deconvolver: Högbom, single Taylor term  
  > "We also chose to use a single Taylor coefficient in the spectral model" (2.1 Identification of emission sources)
- weighting robust: natural  
  > "A natural weighting was employed to maximise the sensitivity" (2.1 Identification of emission sources)
- uv taper: 10 arcsec taper for tapered residual map  
  > "a second with a 10 arcsec taper" (3.1 Image Plane)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel and time averaging: 128 channels per SPW, 30 s  
  > "We channel averaged the data across the 128 channels in each of the four SPWs and time averaged the data into 30 second intervals." (2.1 Identification of emission sources)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Cell size and image size for tclean
- Mask and clean threshold/iterations
- MCMC sampler type, priors, number of walkers/steps for GALARIO fits
- Exact visibility binning/weighting and which data columns were used
- Procedure for inferring the 3.35 sigma with dof=1 details and per-bin values
- Model for correction factor beyond FABLE comparison; noise realisation details of simulations

## Analysis recipe

1. **average data and image continuum**: Channel/time average to 30 s, then tclean natural weighting to identify five sources  
  > "Five sources are observed with SNR larger than three, with the central emission coming from HE0515-4414." (2.1 Identification of emission sources)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
2. **rescale visibility weights**: Compute weights as reciprocal variance in uvdist bins; default weights ~2x too large, rescaled  
  > "On average, the default ALMA weights are roughly twice as large as the statistically correct weights." (2.2.2 Noise determination and weights scaling)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **fit positive-emission sources in uv plane**: Fit 3 symmetric Gaussians (A,B,C) and 2 point sources (D,E) to visibilities  
  > "We therefore use a brightness model with the three resolved sources described as extended Gaussian profiles and the remaining two sources as point sources." (2.2.3 Model Parameter Estimation)
   - software: GALARIO
   - fitting: Bayesian MCMC sampler; median and 16th/84th percentiles of posteriors  
  > "GALARIO allows users to choose the fitting procedure - in our case, a Bayesian MCMC sampler." (2.2.1 Modelling in the Fourier Plane)
   - validation: _not stated_
4. **inspect residuals for SZ**: Subtract model from visibilities; bin residuals in 1 klambda bins; tclean residual images  
  > "The residuals were found by subtracting the model presented in Fig. 4 from the observed visibilities." (3 Results)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: Checked >50 uv tracks and >20 antenna pairs in shortest bin  
  > "We plotted the uv coordinates of the visibilities inside that bin and observed over 50 uv-tracks." (3.2 Visibility Plane)
5. **quantify significance**: Reduced chi2 of shortest-baseline bin and chi2 CDF probability converted to sigma  
  > "We find a 99.960 per cent probability of a ${\chi}_{red}^{2}$ smaller than the smallest baseline bin ${\chi}_{red}^{2}$, corresponding to a 3.35 $\sigma$ detection." (3.3 Significance)
   - fitting: _not stated_
   - validation: _not stated_
6. **compare with FABLE simulation**: simobserve of FABLE SZ map, same pipeline; derive correction factor 2.5  
  > "This suggests a total SZ flux of 0.5 mJy from HE0515-4414 after correcting for the primary beam attenuation and the flux resolved out by the array (i.e. a correction factor of 2.5)." (4.2 Comparison with Simulations)
   - software: CASA, simobserve
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Calibration, tclean imaging, simobserve, plotms  
  > "The data were calibrated using the ALMA pipeline in CASA 4.7.2" (2 ALMA observations and data reduction)
- **GALARIO** : Fitting visibility models of positive sources via MCMC  
  > "GALARIO (cite: Tazzari2017) is a new code that makes use of GPUs and multiple CPU cores to compute synthetic visibilities quickly." (2.2.1 Modelling in the Fourier Plane)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SZ detection significance (visibility plane) | 3.35 | not stated | sigma | 5 | The significance of the SZ detection is 3.35$\sigma$. |
| Flux of source C | 387.1 | +9.5/-9.2 | uJy | 3 | C / $387.1^{\mathrm{+9.5}}_{\mathrm{-9.2}}$ |
| SZ flux (uncorrected) | ~0.2 | not stated | mJy | 4 | We report a SZ flux of $\sim$ 0.2 mJy |
| Corrected SZ flux | ~0.5 | not stated | mJy | 6 | $\sim$ 0.5 mJy after applying a correction factor |
| SW bowl significance | 3.2 | not stated | sigma | 4 | In our analysis this feature has a slightly lower significance, 3.2$\sigma$. |
| Image RMS | 3.8 | not stated | uJy/beam | 1 | an RMS noise level of 3.8 $\mu$Jy beam$^{-1}$ is reached |

## Qualitative findings

- Band 3 and ACA observations are predicted to detect SZ more effectively; ~40 h band 4 or ~10 h band 3 needed  
  > "a total of $\sim$40 hours and $\sim$10 hours of on-source time are required for a clear detection in bands 4 and 3 respectively." (Conclusion)

## Claim tuples

- H: SZ decrement from halo heating is detectable at short baselines | E: GALARIO source subtraction and residual visibility analysis | R: Negative residual at 5-6 klambda, chi2red~12, 3.35 sigma, ~0.2 mJy | F: Marginal SZ detection on ~300 kpc scales | **partially**
- H: Observation consistent with FABLE predictions | E: simobserve of FABLE SZ map | R: Shortest-baseline point consistent within error | F: Simulation consistent with data | **supported**
- H: Band 3 is better for SZ detection | E: Simulate band 3 and ACA | R: Decrement visible without amplification, ~10 h | F: Band 3 twice as sensitive | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-plane fitting gives direct uncertainties and separates compact from extended emission  
  > "Working in the visibility plane (i.e. fitting the visibilities) is a straightforward operation on the interferometric measurements which allows a direct computation of uncertainties." (2.2.1 Modelling in the Fourier Plane)
- Alternative: Direct fit of a broad negative Gaussian for SZ was unsuccessful  
  > "We attempted to directly model the SZ absorption by fitting a negative, very broad Gaussian. Unfortunately, this modelling does not provide well constrained results" (2.2.3 Model Parameter Estimation)
- How they decided it was enough: _not stated_
- Limitation (authors): Only dof=1 for short baselines; limited SNR prevents 2D fitting  
  > "Our positive emission model, however, has 17 parameters, leaving dof=1." (3.3 Significance)
- Caveat (inferred, ours): Significance from dof=1 chi2 is fragile and no look-elsewhere/systematics assessment
- Caveat (inferred, ours): Correction factor depends on a single FABLE object
- Caveat (inferred, ours): Residual could arise from imperfect source modelling or symmetric Gaussian assumption
- Caveat (inferred, ours): Shortest bin may be affected by missing short-spacing coverage

## Reproducibility

- Data public (paper): Archival ALMA data, project 2016.1.00309.S  
  > "We analyse an archival ALMA band 4 observation" (Introduction)
- Products in archive: _not stated_
- Missing: MCMC settings and priors
- Missing: FABLE simulation maps
- Missing: Exact binning and chi2 calculation details
- Data volume (inferred): ~100 GB raw for 14 EBs; ~10s GB calibrated
- Score (inferred): 3/5, Public data and clear approach, but fit settings, priors and simulation inputs are missing.
- Rediscovery candidate: no, Simulation inputs and fitting details are missing and the significance is fragile.

## Links

- Method: (cite: Tazzari2017) (GALARIO visibility modelling code)
- Companion: (cite: Lacy2018) (Independent image-plane analysis of same data)
- Related: FABLE simulations

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 69,
  "stated": 37,
  "rate": 0.536
 },
 "evidence_ok": true
}
```
