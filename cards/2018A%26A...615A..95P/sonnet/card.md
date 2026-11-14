# Resolved millimeter-dust continuum cavity around the very low mass young star CIDA 1

`2018A&A...615A..95P` | Astronomy and Astrophysics 2018 | first author: Pinilla, Paola | arXiv: 1805.00960 | DOI: 10.1051/0004-6361/201832690

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the disk around the very low mass star CIDA 1 have a resolved mm-dust cavity, and what could cause it?  
  > "We report the discovery of a large inner dust-empty region in the disk around the very low mass star CIDA 1" (abstract)
- Target **CIDA 1**: coordinates 04:14:17.62 +28:06:09.28 (J2000)  
  > "Eventually we adopted as disk center position α2000 =04:14:17.62, δ2000 =+28:06:09.28." (3. Observations); "a distance of 140 pc (typical for young stars in the Taurus association)" (2.); z/distance 140 pc  
  > "Eventually we adopted as disk center position α2000 =04:14:17.62, δ2000 =+28:06:09.28." (3. Observations); "a distance of 140 pc (typical for young stars in the Taurus association)" (2.); distance from typical for young stars in the Taurus association  
  > "Eventually we adopted as disk center position α2000 =04:14:17.62, δ2000 =+28:06:09.28." (3. Observations); "a distance of 140 pc (typical for young stars in the Taurus association)" (2.)

## Data provenance

- ALMA projects: 2015.1.00934.S
- bands: Band 7 (~338 GHz, 887 µm)  
  > "at Band 7 (frequency of about 338 GHz" (3. Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: two spectral windows of 2 GHz at 332.0 and 344.0 GHz  
  > "Two spectral windows were dedicated to the continuum (bandwidth of 2 GHz), and have central frequencies of 332.0 and 344.0 GHz" (3. Observations)
- arrays: 38 antennas  
  > "During the observations 38 antennas were available." (3. Observations)
- configurations: _not stated_
- baselines: 15 to 1462 m  
  > "observations covered unprojected baselines between about 15 and 1462 m" (3. Observations)
- angular resolution: 0.21" x 0.12"  
  > "a synthesized beam of 0.′′21 × 0.′′12 (FWHM)" (3. Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.15 mJy/beam  
  > "has an rms of 0.15 mJy beam−1" (3. Observations)
- time on source: about 50 minutes  
  > "The total time on-source was about 50 minutes" (3. Observations)
- observing dates: August 12, 2016  
  > "CIDA 1 was observed with ALMA on August 12, 2016" (3. Observations)
- pi or archival as stated: _not stated_
- External data: Line fluxes (Hα etc.) used for extinction and accretion luminosity  
  > "measured by Herczeg & Hillenbrand (2008)" (2. CIDA 1) [from Herczeg & Hillenbrand (2008)]
- External data: Taurus Class II dust masses and mm fluxes for comparison  
  > "the millimeter fluxes and dust masses obtained in Andrews et al. (2013)" (6. Discussion) [from Andrews et al. (2013)]

## Processing

### Calibration

- pipeline or manual: Calibrated by NRAO staff with CASA; then two rounds of self-calibration  
  > "The ALMA data were calibrated by National Radio Astronomy Observatory (NRAO) staff using the CASA software package" (3. Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800; Butler-JPL-Horizons 2012 models  
  > "The frequency-dependent bandpass and absolute flux scale were calibrated using J0510+1800." (3. Observations)
- flux scale uncertainty: about 10%  
  > "resulting in an accuracy of about 10%" (3. Observations)
- self calibration: phase-only (20 s) then amplitude and phase (200 s)  
  > "we performed two rounds of self-calibration on phase only (20s solution intervals) and amplitude and phase (200s solution intervals)" (3. Observations)

### Imaging

- task: clean in CASA  
  > "Imaging was performed with the clean algorithm in CASA using uniform weighting." (3. Observations)
- deconvolver: _not stated_
- weighting robust: uniform  
  > "Imaging was performed with the clean algorithm in CASA using uniform weighting." (3. Observations)
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
- final rms: 0.15 mJy/beam  
  > "has an rms of 0.15 mJy beam−1" (3. Observations)

### Inherited from earlier work

- MCMC fitting procedure  
  > "We follow the procedure as in Pinilla et al. (2017a)." (5. Data Analysis) [from Pinilla et al. 2017a]
- Dust mass calculation for comparison sample  
  > "we follow the same procedure as in Andrews et al. (2013)" (6. Discussion) [from Andrews et al. (2013)]

### Not stated but needed to reproduce (our reading)

- clean threshold, niter, mask, cell and image size
- how channels were averaged and uv-weights
- MCMC priors form, likelihood and binning of visibilities
- likelihood details for BIC
- reference image phase-center handling
- exact uvmodelfit settings

## Analysis recipe

1. **Phase-center, PA and inclination**: fixvis offset from uvmodelfit with Gaussian or disk model  
  > "the phase center of the data was corrected by an offset of [0.′′13, −0.′′42] using the algorithm fixvis in CASA." (3. Observations)
   - software: CASA
   - parameter: PA=12.0±0.9 deg, i=37.3±0.6 deg  
  > "PA=12.0◦ ±0.9◦, and i = 37.3◦ ±0.6◦" (3. Observations)
   - fitting: _not stated_
   - validation: Fits to short baselines (≤200 or ≤400 kλ) give similar results  
  > "These tests give similar results as using the entire dataset." (3. Observations)
2. **Dust mass from total flux**: optically thin Hildebrand formula  
  > "we calculate the disk dust mass assuming optically thin emission, as Hildebrand (1983)" (4. Results)
   - parameter: d=140 pc; T_dust 20 K, or 25(L/Lsun)^0.25 K  
  > "the prescription Tdust ≈25 ×(L⋆/L⊙)0.25 K derived by Andrews et al. (2013)" (4. Results)
   - assumption: kappa = 2.3 cm2/g (nu/230 GHz)^0.4  
  > "κν = 2.3 cm2 g−1 ×(ν/230 GHz)0.4 (Andrews et al. 2013)" (4. Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit ring model to visibilities**: Deprojected real visibilities fit with Gaussian ring (symmetric and asymmetric) via Bessel transform  
  > "we only fit the real part of the visibilities." (5. Data Analysis)
   - software: emcee
   - parameter: 200 walkers, 1000 steps; r_peak in [1,150] au, sigma in [1,50] au, F in [0,0.1] Jy; radial grid 0-500 au step 0.25 au  
  > "We allow the Markov chain to sample the parameter space for one thousand steps, with two hundred walkers." (5. Data Analysis)
   - assumption: axisymmetric disk  
  > "We assume an axisymmetric disk since the image in Fig. 2 does not show significant asymmetries." (5. Data Analysis)
   - fitting: emcee MCMC, three free parameters  
  > "using a Markov chain Monte Carlo (MCMC) method with three free parameters" (5. Data Analysis)
   - validation: Autocorrelation time ~100; last 100 steps checked; BIC compares models  
  > "The maximum autocorrelation time is ∼100 for all cases, and we examine the last 100 steps to check the convergence of the fit." (5. Data Analysis)

## Software

- **CASA** : calibration, fixvis, uvmodelfit, clean imaging  
  > "using the algorithm fixvis in CASA" (3. Observations)
- **emcee** : MCMC fit of ring models  
  > "we use emcee (Foreman-Mackey et al. 2013)" (5. Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ring peak radius (symmetric) | 20.7 | +0.1/-0.1 | au | 3 | rpeak = 20.7 −+00..11 au |
| ring width sigma (symmetric) | 5.8 | +0.2/-0.2 | au | 3 | σwidth = 5.8 −+00..22 au |
| total flux from fit | 35.4 | +0.2/-0.2 | mJy | 3 | Ftotal = 35.4 −+00..22 mJy |
| dust mass (adopted) | 5.2e-5 | 1.7e-5 | Msun | 2 | we will adopt the value of 5.2 ×10−5 ±1.7 ×10−5 M⊙ |
| BIC difference | 11.7 | not stated | dimensionless | 3 | the difference between the two BICs is 11.7 |
| asymmetric ring r_peak | 28.8 | +0.5/-0.9 | au | 3 | rpeak = 28.8 −+00..59 au |

## Qualitative findings

- Disk is compact (~30 au outer radius), smaller than inferred from Cycle 0 data  
  > "is more compact (∼30 au) than previously inferred from ALMA Cycle 0 data" (5. Data Analysis)

## Claim tuples

- H: CIDA 1 hosts a resolved mm cavity | E: ALMA 887 µm imaging and visibility ring fit | R: ring peaks at 20.7 au with clear cavity | F: CIDA 1 is a transition disk around a very low mass star | **supported**
- H: Origin of the cavity | E: Compare photoevaporation, dead zones, planets, binary with observed properties | R: photoevaporation and dead zones disfavoured | F: Saturn-mass planet or close binary most likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporation and dead zones judged unlikely  
  > "photoevaporation and dead zones are unlikely explanations" (7. Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Binary separations of a few au not yet probed  
  > "but separations of a few au have not been probed yet" (6. Discussion)
- Caveat (inferred, ours): Dust mass depends strongly on assumed T_dust and opacity
- Caveat (inferred, ours): Distance of 140 pc assumed, not measured
- Caveat (inferred, ours): Planet mass estimates are model-dependent

## Reproducibility

- Data public (paper): ALMA project data cited with project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00934.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: visibility binning
- Missing: MCMC likelihood details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and a clear model fit, but imaging and fit details are sparse.
- Rediscovery candidate: yes, Data are public, the fit is simple and results are numeric.

## Links

- Method: Pinilla et al. 2017a (MCMC visibility fitting procedure)
- Companion: Ricci et al. 2014 (Earlier Cycle 0 ALMA data of CIDA 1)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 66,
  "stated": 40,
  "rate": 0.606
 },
 "evidence_ok": true
}
```
