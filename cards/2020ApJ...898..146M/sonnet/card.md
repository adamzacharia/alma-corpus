# Dust Populations in the Iconic Vega Planetary System Resolved by ALMA

`2020ApJ...898..146M` | The Astrophysical Journal 2020 | first author: Matrà, Luca | arXiv: 2006.16257 | DOI: 10.3847/1538-4357/aba0a4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, exoplanets
- Question: What is the mm-wavelength structure of Vega's outer dust belt, is there warm inner dust emission, and what planetary architecture explains it?  
  > "motivated to resolve the previous mysteries surrounding Vega’s outer belt structure, and to attempt resolved detection of the warm dust component" (Introduction)
- Target **Vega (HD 172167)**: coordinates _not stated_; z/distance 7.8 pc  
  > "Vega (HD 172167) is an A0V (cite: GrayGarrison1987) star at a distance of 7.8 pc (cite: vanLeeuwen2007)" (Introduction); distance from van Leeuwen 2007  
  > "Vega (HD 172167) is an A0V (cite: GrayGarrison1987) star at a distance of 7.8 pc (cite: vanLeeuwen2007)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00182.S
- bands: Band 6, mean 225.2 GHz (1.34 mm)  
  > "The observations were carried out in ALMA band 6 at a mean frequency of 225.2 GHz (project 2015.1.00182.S)." (2 Observations)
- frequencies and spectral setup: 7.5 GHz total bandwidth; three TDM low-resolution SPWs and one SPW covering 12CO J=2-1 at 1.3 km/s resolution  
  > "The total bandwidth was 7.5GHz, with three spectral windows set for low resolution TDM mode, and one covering the region of the $^{12}$CO line at 230.538 GHz with a resolution of 1.3 km s$^{-1}$." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array (most compact configuration) and ACA  
  > "Executions were carried out on both the ACA and the 12m array in the most compact configuration." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.8'' x 0.9'' (natural, no taper); 8.5'' x 7.9'' (10'' taper)  
  > "This image has an RMS sensitivity of 13 $\mu$Jy/beam for a synthesized beam of 1.8$\ensuremath{''}$ $\times$ 0.9$\ensuremath{''}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 70 uJy/beam (10'' taper); 13 uJy/beam (natural, no taper); CO cube 1 mJy/beam per 0.64 km/s channel  
  > "This image achieves an RMS sensitivity of 70 $\mu$Jy/beam for a synthesized beam of 8.5$\ensuremath{''}$ $\times$ 7.9$\ensuremath{''}$" (2 Observations)
- time on source: 80 min (3 executions, 12m, April 2016); 400 min (12 executions, ACA, Aug-Sept 2016)  
  > "The total on-source time was 80 minutes over three executions using the 12m array in April 2016, and 400 minutes in 12 executions with the ACA in Aug-Sept 2016." (2 Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- External data: Warm dust asteroid belt model (170 K, 7e-6 fractional luminosity); predicted 240 uJy at 1.34 mm  
  > "predicted flux density of 240 $\mu$Jy at 1.34 mm extrapolated from the asteroid belt model of (cite: Su2013)" (3.4 Searching for the inner belt) [from (cite: Su2013)]
- External data: Galaxy number counts used to assess the background-source hypothesis  
  > "Taking the galaxy number counts from (cite: Carniani2015), we expect 3.5 galaxies as bright or brighter than this source" (3.3 Modelling results) [from (cite: Carniani2015)]
- External data: Vega equatorial spectrum used for CO fluorescence and photodissociation  
  > "we use the Vega spectrum provided by (cite: Aufdenberg2006) as would be seen along the star’s equatorial plane" (3.5 CO emission) [from (cite: Aufdenberg2006)]

## Processing

### Calibration

- pipeline or manual: ALMA data reduction pipeline flagging (incl. shadowing); additional self-calibration of 12m data  
  > "this was taken into account by flagging in the data reduction pipeline" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939 (bandpass and flux); J1848+3219 phase calibrator  
  > "J1751+0939 was used for bandpass and flux calibration and J1848+3219 was the phase calibrator." (2 Observations)
- flux scale uncertainty: 5-10% expected in Band 6; 15% adopted in total flux estimate  
  > "given the expected 5-10% flux calibration accuracy in Band 6" (2 Observations)
- self calibration: 12m only, per execution: 3 phase-only rounds (~370, 132, 99 s) then one amplitude round (~370 s), using stellar point-source model  
  > "We executed 3 rounds of phase-only self-calibration, combining visibilities from all 4 SPWs." (2 Observations); "we applied one round of amplitude self-calibration with a $\sim$370 s solution interval" (2 Observations)

### Imaging

- task: tclean in CASA v5.4.0, multi-frequency synthesis  
  > "We imaged the continuum from the combined 12m+ACA phase-shifted and amplitude-rescaled visibility dataset using the *tclean* task within CASA v5.4.0." (2 Observations)
- deconvolver: multiscale  
  > "We employed multi-frequency synthesis with multiscale deconvolution to best recover emission on extended scales from the outer belt" (2 Observations)
- weighting robust: natural weighting  
  > "we image the combined 12m+ACA data with natural visibility weighting" (2 Observations)
- uv taper: 10'' taper for large-scale image  
  > "we produce an image of the combined 12m+ACA data with natural weighting, but with a 10$\ensuremath{''}$ *u-v* taper applied" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 1, 3, 9 times synthesized beam size  
  > "we used scales of 0 (point source), 1, 3, and 9 times the expected synthesized beam size of the image" (2 Observations)
- continuum subtraction: uvcontsub, excluding ±50 km/s around the CO line  
  > "avoiding a region $\pm$50 km/s from the line frequency in the rest frame of Vega" (2 Observations)
- line free channels: _not stated_
- primary beam correction: Airy-disk primary beams; A-Projection for joint 12m+ACA  
  > "we use the A-Projection algorithm as implemented in CASA" (3.1 Image analysis)
- array combination: 12m+ACA visibilities concatenated and imaged jointly  
  > "We imaged the continuum from the combined 12m+ACA phase-shifted and amplitude-rescaled visibility dataset" (2 Observations)
- smoothing: _not stated_
- final beam: 8.5''x7.9'' (PA -60.7) tapered; 1.8''x0.9'' (PA -20.8) natural  
  > "with a position angle (PA) of -20.8$^{\circ}$" (2 Observations)
- final rms: 70 uJy/beam tapered; 13 uJy/beam natural  
  > "This image has an RMS sensitivity of 13 $\mu$Jy/beam" (2 Observations)

### Inherited from earlier work

- Vertical Gaussian belt model parameterization  
  > "following Sect. 4.2 of (cite: Matra2019b)" (3.3.1 Modelling framework) [from (cite: Matra2019b)]
- Weight scaling factor in visibility fits  
  > "has been shown to be necessary to ensure that the visibility uncertainties are correct in an absolute sense (cite: Marino2018b; Matra2019b)" (3.2 Modelling the star) [from (cite: Marino2018b; Matra2019b)]
- CO spectro-spatial filtering and non-LTE excitation analysis  
  > "we searched for CO emission using the spectro-spatial filtering technique described in (cite: Matra2015; Matra2017b)" (3.5 CO emission) [from (cite: Matra2015; Matra2017b)]
- Visibility deprojection procedure  
  > "following the commonly adopted procedure of e.g. (cite: Hughes2007)" (3.3.2 Modelling results) [from (cite: Hughes2007)]

### Not stated but needed to reproduce (our reading)

- CLEAN thresholds, masks, cell and image sizes
- Priors ranges and starting positions of belt MCMC
- Exact line-free channel selection beyond +-50 km/s and CO imaging details
- Pipeline version and ALMA flagging details
- Temperature grid details for RADMC-3D
- Phase-center coordinates of Vega

## Analysis recipe

1. **Self-calibrate and align 12m data**: Phase-only (3 rounds) and amplitude self-cal on stellar point-source model per execution; shift phase centre to fitted stellar position  
  > "we self-calibrated the data separately for each of the three executions using the bright, unresolved emission from the central star." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: 40-50% increase in peak stellar SNR  
  > "this procedure successfully led to a $\sim$40-50% increase in the peak SNR of the star." (2 Observations)
2. **Fit stellar flux and offsets**: Point-source fit to 12m visibilities beyond 50 klambda per execution; mean flux adopted for rescaling  
  > "We first model the star as a point source and fit the long baseline ($>50 k\lambda$) visibilities of each of the 12-m datasets independently." (3.2 Modelling the star)
   - software: emcee
   - parameter: 2000 steps, 40 walkers, uniform priors, likelihood exp(-chi2/2), free weight scaling  
  > "We ran the MCMC for 2000 steps using 40 walkers, ensuring convergence." (3.2 Modelling the star)
   - fitting: emcee affine-invariant sampler  
  > "using the affine-invariant sampler from (cite: GoodmanWeare2010), starting from uniform priors on all parameters" (3.2 Modelling the star)
   - validation: Residual maps noise-like at stellar location  
  > "produced noise-like maps, free of significant residual emission at the stellar location" (3.2 Modelling the star)
3. **Fit outer belt models to visibilities**: Gaussian, single power-law, double power-law radial models; RADMC-3D ray-trace, primary-beam multiply, GALARIO Fourier transform, star added, MCMC; ACA fit first for ACA stellar parameters, then joint ACA+12m  
  > "we first ray-trace the belt’s emission at 1.34 mm using RADMC-3D" (3.3.1 Modelling framework)
   - software: RADMC-3D, GALARIO, emcee
   - parameter: aspect ratio h fixed to 0.03; walkers = 10 x free parameters; 2000 steps  
  > "For all models, we fixed the aspect ratio $h$ to 0.03" (3.3.1 Modelling framework)
   - assumption: Optically thin; r^-0.5 temperature profile; constant dust opacity  
  > "we assume the dust to follow a $r^{-0.5}$ radial temperature profile" (3.3.1 Modelling framework)
   - fitting: MCMC as for stellar fits  
  > "We fit this star+belt model to the observed visibilities with MCMC as done for the star-only fits" (3.3.1 Modelling framework)
   - validation: Residual images and AIC/BIC model comparison  
  > "Statistical tests such as the Akaike Information Criterion (AIC) and the Bayesian Information Criterion (BIC) confirm" (3.3.2 Modelling results)
4. **Search for warm inner belt**: Inspect residual visibilities and residual radial profile; derive 3 sigma upper limits via annulus noise  
  > "the best way to look for the warm belt is to analyse the visibility residuals after subtraction of the best-fit star+outer belt model visibilities" (3.4 Searching for the inner belt)
   - software: CASA
   - assumption: Narrow unresolved Gaussian belt at 14-40 au  
  > "Assuming a warm belt with a Gaussian radial profile and an unresolved width" (3.4 Searching for the inner belt)
   - fitting: _not stated_
   - validation: _not stated_
5. **CO gas mass upper limit**: Spectro-spatial filtering within 130 au; non-LTE excitation with UV fluorescence to convert flux limit to mass  
  > "we employ a non-LTE excitation analysis (cite: Matra2015) including fluorescence due to CO excitation by UV photons (cite: Matra2018a)" (3.5 CO emission)
   - parameter: kinetic temperatures 10-250 K, full range of electron densities  
  > "kinetic temperatures between 10 and 250 K" (3.5 CO emission)
   - assumption: Optically thin, electron collisions dominate, little H2, CO co-located with dust at 118 au  
  > "We assume that emission is optically thin and that collisions with electrons dominate the excitation" (3.5 CO emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v5.4.0: Imaging (tclean), uvcontsub, A-Projection  
  > "using the *tclean* task within CASA v5.4.0" (2 Observations)
- **emcee** v3: MCMC visibility fitting  
  > "implemented using the EMCEE v3 package" (3.2 Modelling the star)
- **RADMC-3D** : Ray-tracing belt model images  
  > "we first ray-trace the belt’s emission at 1.34 mm using RADMC-3D" (3.3.1 Modelling framework)
- **GALARIO** : Fourier transform of model to uv points  
  > "we use the GALARIO package (cite: Tazzari2018) to compute its Fourier transform" (3.3.1 Modelling framework)
- **PHOENIX** : Extrapolating stellar spectrum to 0.09 um  
  > "rescaling the flux of a PHOENIX (cite: Allard2014) spectrum" (3.5 CO emission)
- **Matplotlib** : Plotting  
  > "CASA (cite: McMullin2007), Matplotlib (cite: Hunter2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar peak flux density in tapered map | 2580 | SNR ~37 | uJy | 0 | The star itself is strongly detected with a peak flux density of 2580 $\mu$Jy (SNR$\sim$37) in the tapered map. |
| Mean stellar flux density at 1.34 mm (12m) | 2495 | not stated | uJy | 2 | mean of the best-fit values obtained from the separate 12m datasets (2495 $\mu$Jy) |
| Gaussian belt radius r_c | 118 | +4/-3 | au | 3 | $118^{+4}_{-3}$ ($15.3^{+0.5}_{-0.4}$) |
| Gaussian belt FWHM | 67 | +9/-7 | au | 3 | $67^{+9}_{-7}$ ($8.7^{+1.2}_{-0.9}$) |
| Power-law inner edge r_in | 74 | +3/-3 | au | 3 | $74^{+3}_{-3}$ ($9.6^{+0.4}_{-0.4}$) |
| Double power-law inner slope gamma | 10 | +5/-3 | dimensionless | 3 | $10^{+5}_{-3}$ |
| Belt flux density (Gaussian) | 8.5 | +1.3/-1.1 | mJy | 3 | $8.5^{+1.3}_{-1.1}$ |
| Warm belt 3 sigma upper limit (narrow, 14-40 au) | 120-223 | not stated | uJy | 4 | this yields 3$\sigma$ upper limits of $120-223$ $\mu$Jy on the 1.34 mm flux density of a narrow warm belt |
| Warm dust 3 sigma upper limit (broad, <40 au) | <324 | not stated | uJy | 4 | we measure a 3$\sigma$ upper limit of $<$324 $\mu$Jy on the total residual 1.34 mm flux density interior to 40 au |
| CO integrated line flux 3 sigma upper limit | 250 | not stated | mJy km/s | 5 | we obtain a 3$\sigma$ upper limit on the integrated line flux of 250 mJy km/s |
| CO mass upper limits | 3.4-19e-7 | not stated | Earth masses | 5 | obtaining mass upper limits in the range 3.4-19$\times10^{-7}$ M$_{\oplus}$ |
| CO photodissociation timescale at 118 au | 12 | not stated | years | 5 | we calculate a CO photodissociation timescale of 12 years |
| Total 1.34 mm flux density of Vega system | 9.9-16.9 | 1 sigma range | mJy | 3 | ranging between $9.9-16.9$ mJy (1$\sigma$ range, including the star) |

## Qualitative findings

- No significant clumps in residuals; belt is smooth and axisymmetric  
  > "we find no significant evidence of clumps at all scales" (3.3.2 Modelling results)
- Compact ~4 sigma residual south of star likely a background galaxy  
  > "we conclude that this source is most likely a background galaxy" (3.3.2 Modelling results)

## Claim tuples

- H: Is Vega's outer belt detectable and resolved by ALMA+ACA? | E: Visibility modelling of combined 12m+ACA 1.34 mm data | R: Belt resolved with inner hole; Gaussian r_c=118 au, FWHM 67 au; steep inner edge at 60-80 au | F: Belt is very broad (to at least 150-200 au) with a steep inner edge | **supported**
- H: Is warm dust emission detectable at mm wavelengths? | E: Residual visibility/image analysis after subtracting star+belt | R: 3 sigma limits 120-223 uJy (narrow) and <324 uJy (broad) | F: Limits are close to predictions; cannot confirm or rule out the warm belt | **partially**
- H: Can unperturbed collisional evolution of an extended planetesimal disk explain the inner edge? | E: Compare fitted gamma with predicted gamma~2-2.3 | R: gamma=10 (+5/-3), 3 sigma lower limit 4.4 | F: Inconsistent unless belt was born truncated; a planet likely truncates it | **supported**
- H: Is CO gas detectable around Vega? | E: Spectro-spatial filtering and non-LTE excitation | R: No detection; mass limit 3.4-19e-7 Mearth | F: Limit does not constrain exocomet CO ice fraction | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Model visibilities directly to avoid CLEAN and missing-short-spacing artifacts for extended low-level emission  
  > "to robustly derive the mm continuum structure of the Vega planetary system and avoid imaging biases, in the following subsections, we opt to model the visibilities directly." (3.1 Image analysis)
- Alternative: Gaussian, single and double power-law models fit equally well; no strong AIC/BIC preference  
  > "there is no strong evidence in the data that the single and double power law models (which have an extra free parameter) are significantly better" (3.3.2 Modelling results)
- How they decided it was enough: _not stated_
- Limitation (authors): Total belt flux is model-dependent due to extrapolation to zero uv distance; position angle and inclination unconstrained  
  > "The best-fit total belt flux at 1.34 mm varies depending on the model employed" (3.3.2 Modelling results)
- Limitation (authors): Low target elevation and antenna shadowing  
  > "The high source declination means that the elevations of the Vega scans were low - in the range 21-28$^{\circ}$." (2 Observations)
- Caveat (inferred, ours): Outer extent poorly constrained because of primary beam limits (20% power level)
- Caveat (inferred, ours): Stellar flux rescaling by 12m mean and ACA fit may bias the belt flux
- Caveat (inferred, ours): Planet mass limits rely on assumed circular orbit and r_c as inner edge
- Caveat (inferred, ours): h fixed and temperature profile assumed

## Reproducibility

- Data public (paper): ALMA project given; public status not explicitly stated  
  > "This paper makes use of ALMA data ADS/JAO.ALMA#2015.1.00182." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Priors bounds and walker initialization
- Missing: CLEAN parameters (threshold, mask, cell/image size)
- Missing: RADMC-3D grid and temperature setup
- Missing: Pipeline version
- Data volume (inferred): ~10-50 GB raw (15 executions, 12m+ACA)
- Score (inferred): 3/5, Data and modelling recipe described with software, but many numerical settings and priors are missing.
- Rediscovery candidate: yes, Data are archival ALMA project, recipe fairly complete, and main results (belt radius, width, upper limits) are numeric.

## Links

- Method: (cite: Matra2019b) (Belt model parameterization and weight scaling)
- Method: (cite: Matra2015) (CO non-LTE excitation analysis)
- Method: (cite: Tazzari2018) (GALARIO visibility computation)
- Companion: (cite: Su2013) (Warm dust asteroid belt model for Vega)
- Companion: (cite: Hughes2012) (Previous interferometric non-detections)

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 59,
  "rate": 0.72
 },
 "evidence_ok": true
}
```
