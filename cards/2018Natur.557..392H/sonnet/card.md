# The onset of star formation 250 million years after the Big Bang

`2018Natur.557..392H` | Nature 2018 | first author: Hashimoto, Takuya | arXiv: 1805.05966 | DOI: 10.1038/s41586-018-0117-z

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Determine the spectroscopic redshift of the lensed z~9 galaxy MACS1149-JD1 via ALMA [OIII] 88um and test whether its IRAC 4.5um excess implies an early (z~15) star formation episode  
  > "We detect an emission line of doubly ionized oxygen at a redshift of 9.1096 ± 0.0006, with an uncertainty of one standard deviation." (abstract)
- Target **MACS1149-JD1**: coordinates RA 11:49:33.58, Dec +22:24:45.7  
  > "RA 11 : 49 : 33 . 58" (Table 1); "The adopted cosmological parameters are H 0 = 70 . 4 km s − 1 Mpc − 1, Ω m = 0 . 272" (Methods, Cosmological model); z/distance z = 9.1096 ± 0.0006 ([OIII])  
  > "RA 11 : 49 : 33 . 58" (Table 1); "The adopted cosmological parameters are H 0 = 70 . 4 km s − 1 Mpc − 1, Ω m = 0 . 272" (Methods, Cosmological model); distance from ALMA [OIII] 88um line (this work)  
  > "RA 11 : 49 : 33 . 58" (Table 1); "The adopted cosmological parameters are H 0 = 70 . 4 km s − 1 Mpc − 1, Ω m = 0 . 272" (Methods, Cosmological model)

## Data provenance

- ALMA projects: 2015.1.00428.S
- bands: Band 7  
  > "We observed MACS1149-JD1 with ALMA in Band 7" (Methods, ALMA observations and data reduction)
- frequencies and spectral setup: Four setups T3-T6, 314.4-340.5 GHz; each 7.5 GHz in four 1.875 GHz SPWs, FDM, 7.8125 MHz resolution (~7 km/s)  
  > "we used four setups with contiguous frequencies labeled as T3, T4, T5, and T6 encompassing the frequency range 314 . 4 − 340 . 5 GHz" (Methods, ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3  
  > "with a configuration C40-3" (Methods, ALMA observations and data reduction)
- baselines: _not stated_
- angular resolution: 0.62" x 0.52", PA = -8.9 deg  
  > "The spatial resolution is 0 ′′ . 62 × 0 ′′ . 52 (FWHM)" (Methods, ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 17.7 uJy/beam  
  > "the rms noise level for the continuum image is 17 . 7 µ Jy beam − 1" (Methods, Upper limits on dust continuum)
- time on source: 75.6, 35.3, 119.4, 42.3 min for T3-T6  
  > "The total observation times are 75 . 6, 35 . 3, 119 . 4, and 42 . 3 minutes, for T3, T4, T5, and T6, respectively." (Methods, ALMA observations and data reduction)
- observing dates: March 2016 to April 2017  
  > "Between March 2016 and April 2017 we performed observations of MACS1149-JD1" (main text)
- pi or archival as stated: PI A. K. Inoue; data in ALMA archive  
  > "ID 2015.1.00428.S, PI: A. K. Inoue" (Methods, ALMA observations and data reduction)
- Line: [OIII] 88 um (3P1-3P0) (3393.006244 GHz)
- Other facility **VLT/X-Shooter**: Tentative Lya detection, z=9.0942±0.0019  
  > "We performed the X-Shooter observations in February and April 2017 (098.A-0534, PI: N. Laporte)" (Methods, VLT/X-Shooter)
- Other facility **HST, Spitzer/IRAC, VLT/HAWK-I**: Photometry for SED fitting (from Zheng+17, Hoag+18)  
  > "combining data from the 3 deep HST images obtained within the framework of the Frontier Fields survey [7]" (Methods, SED modeling)
- External data: HST, Spitzer/IRAC photometry  
  > "HST and Spitzer as well as VLT/HAWK-I photometry data that support our finding are available in the IOPscience repository" (Data availability) [from Zheng et al. 2017 (cite: 7)]
- External data: Lensing magnification from Frontier Fields mass models  
  > "using all the mass models released in the framework of the Frontier Fields survey" (Methods, Magnification factor) [from (cite: 40-46)]
- External data: Dust mass absorption coefficient kappa0 = 10 cm2/g at 250 um  
  > "κ 0 = 10 cm 2 g − 1 at 250 µ m" (Methods, Upper limits on dust continuum) [from Hildebrand 1983 (cite: 12)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline with standard calibration script  
  > "with a standard calibration script provided by the ALMA observatory" (Methods, ALMA observations and data reduction)
- casa version: 4.7.0, 4.5.2, 4.7.2, 4.6.0 for T3, T4, T5, T6  
  > "The T3, T4, T5, and T6 data were reduced using the CASA pipeline version 4.7.0, 4.5.2, 4.7.2, and 4.6.0, respectively" (Methods, ALMA observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1229+0203 (also bandpass)  
  > "A quasar, J1229+0203, was used for bandpass and flux calibrations" (Methods, ALMA observations and data reduction)
- flux scale uncertainty: ≲10%  
  > "for which a flux uncertainty is estimated to be ≲ 10%" (Methods, ALMA observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "We then produced final images and cubes with the CLEAN task using natural weighting" (Methods, ALMA observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting to maximize point-source sensitivity" (Methods, ALMA observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum image excludes ±3×FWHM around [OIII]  
  > "we excluded the frequency around the [O III ] line, ± 3 × FWHM [OIII]" (Methods, Upper limits on dust continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: six native channels binned, ~42 km/s  
  > "we created a data cube, six native channels of which are binned, resulting in a velocity resolution of ∼ 42 km s − 1" (Methods, [OIII] 88 um line)
- final beam: 0.62" x 0.52"  
  > "The spatial resolution is 0 ′′ . 62 × 0 ′′ . 52 (FWHM)" (Methods, ALMA observations and data reduction)
- final rms: 17.7 uJy/beam continuum; 17.5 mJy km/s/beam line  
  > "where σ = 17 . 7 µ Jy beam − 1" (Extended Data Figure 1)

### Inherited from earlier work

- Dynamical mass method follows z~2 analyses  
  > "We derive the dynamical mass, M dyn, of MACS1149-JD1 following analyses at z ∼ 2 [55]." (Methods, Dynamical mass) [from Förster Schreiber et al. 2009 (cite: 55)]
- Total IR luminosity via modified blackbody similar to previous studies  
  > "similarly to previous studies [27–30]" (Methods, Upper limits on dust continuum) [from (cite: 27-30)]
- Dust region size of a single beam following high-z null detections  
  > "following other high- z null detection cases [10,31–33]" (Methods, Upper limits on dust continuum) [from (cite: 10, 31-33)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, image size and cell size
- Which of the SPWs/channels were used for continuum and their weighting
- Exact spectral extraction region and Gaussian fit procedure details
- Velocity-integrated map channel selection beyond 335.5-335.8 GHz
- SED fitting grid details beyond tables, MC procedure
- Lens model choice for magnification beyond fiducial mu=10

## Analysis recipe

1. **Image cubes and search for line**: CLEAN with natural weighting; bin six channels to ~42 km/s; search for >3σ signal in five consecutive channels  
  > "signal in five continuous binned-channels" (Methods, [O III] 88 um line)
   - software: CASA
   - fitting: _not stated_
   - validation: Frequency region free from atmospheric absorption  
  > "This frequency region is free from atmospheric absorption features." (Methods, [OIII] 88 um line)
2. **Measure line flux, redshift, width, size**: Integrated flux with imfit; 1D spectrum from >3σ region fit with Gaussian; imfit deconvolved size  
  > "Applying a Gaussian fit to the line, and with a rest-frame [O III ] frequency 3393.006244 GHz, we obtain a redshift" (Methods, [OIII] 88 um line)
   - software: CASA imfit
   - assumption: Lensing effects equal for major and minor axes  
  > "Assuming that lensing effects are equal for the major and minor axes, the intrinsic size is" (Methods, [OIII] 88 um line)
   - fitting: Gaussian line fit  
  > "Applying a Gaussian fit to the line, and with a rest-frame" (Methods, [O III] 88 um line)
   - validation: _not stated_
3. **Dust continuum upper limit, LIR and dust mass**: Collapse all four setups, exclude line; 3σ limit; modified blackbody over 8-1000 um with CMB correction  
  > "We estimate the total infrared luminosity by integrating the modified-black body radiation over 8 − 1,000 µ m" (Methods, Upper limits on dust continuum)
   - software: CASA imstat
   - assumption: Td=30-60 K (fiducial 40 K), beta_d=1.5, kappa0=10 cm2/g at 250um, emitting region one beam, mu=10  
  > "We assume dust temperature T d = 40 K, spectral index β d = 1 . 5, and the dust emitting region of a single beam size" (Table 1)
   - fitting: _not stated_
   - validation: Astrometry check with CLASH 2882 continuum: ALMA-HST centroids consistent within 0.1"  
  > "The centroids of ALMA and HST are consistent within 0 ′′ . 1." (Methods, Astrometry)
4. **SED fitting for star formation history**: Custom SED code with GALAXEV, nebular emission, [OIII] flux and dust upper limit; compare single and two-component SFHs (tau=10-400 Myr)  
  > "We next considered a two stellar component SED comprising a young starburst and an old population." (Methods, SED modeling)
   - software: KENSFIT
   - parameter: Fiducial tau=100 Myr; Chabrier IMF 0.1-100 Msun; Calzetti law; escape fraction 0  
  > "we select the τ = 100 Myr model as our fiducial case" (Methods, SED modeling)
   - assumption: mu=10 fiducial  
  > "For simplicity we assume a fiducial value for the magnification" (Methods, Magnification factor)
   - fitting: Least chi-square with analytic treatment of upper limits; Monte Carlo uncertainties  
  > "we use the least χ 2 formula [54] including an analytic treatment of upper limits for the non-detection" (Methods, SED modeling)
   - validation: Single-component models rejected (chi2nu 6.9, 11.4); two-component chi2nu 2.8-3.0  
  > "we can reproduce the observations with χ 2 ν ∼ 2 . 8 − 3 . 0" (Methods, SED modeling)
5. **Dynamical mass**: Dispersion-dominated Mdyn = 6.7 sigma^2 r_1/2 / G  
  > "we assume that MACS1149-JD1 is dispersion-dominated" (Methods, Dynamical mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.2, 4.6.0, 4.7.0, 4.7.2: Pipeline reduction, CLEAN, imstat, imfit  
  > "The ALMA data were reduced using the CASA pipeline versions 4.7.0, 4.5.2, 4.7.2, and 4.6.0" (Code availability)
- **KENSFIT (custom SED code)** : SED fitting  
  > "Our SED fitting code is our custom one" (Code availability)
- **ESO Reflex / X-Shooter pipeline** v2.8 / v2.9.3: X-Shooter reduction  
  > "The data were reduced using ESO Reflex tool [34] (v2.8) with the latest version of the X Shooter pipeline (v 2.9.3)." (Methods, VLT/X-Shooter)
- **IRAF imcombine** : Combine X-Shooter exposures  
  > "the IRAF imcombine task on the individual observing blocks" (Methods, VLT/X-Shooter)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [OIII] redshift | 9.1096 | 0.0006 | dimensionless | 2 | Redshift z [OIII] 9 . 1096 ± 0 . 0006 |
| [OIII] peak intensity | 129.8 | 17.5 | mJy km/s/beam | 1 | The peak intensity of MACS1149-JD1 is 129 . 8 ± 17 . 5 mJy km s − 1 beam − 1 |
| [OIII] integrated flux | 0.229 | 0.048 | Jy km/s | 2 | 0 . 229 ± 0 . 048 Jy km s − 1 |
| [OIII] FWHM | 154 | 39 | km/s | 2 | 154 ± 39 |
| [OIII] luminosity | 7.4e7 x (10/mu) | 1.6e7 | Lsun | 2 | (7 . 4 ± 1 . 6) × (10 /µ ) |
| Dust continuum 3σ upper limit | <5.3 x (10/mu) | not stated | uJy/beam | 3 | < 5 . 3 × (10 /µ ) a (3 σ ) |
| Dust mass 3σ upper limit (Td=40K) | <5.3e5 x (10/mu) | not stated | Msun | 3 | we obtain the 3 σ dust mass upper limit of 5 . 3 × 10 5 × (10 /µ ) M ⊙ |
| Dynamical mass | 4e9 x (10/mu)^0.5 | 3e9 | Msun | 5 | M dyn = (4 ± 3) × (10 /µ ) 0 . 5 × 10 9 M ⊙ |
| Formation redshift of old component | 15.4 | +2.7/-2.0 | dimensionless | 4 | z f , old 15 . 4 |
| Stellar mass | 1.08e9 x (10/mu) | +0.53/-0.18 | Msun | 4 | Stellar mass (10 9 M ⊙ ) 1 . 08 |
| Lya redshift | 9.0942 | 0.0019 | dimensionless | 0 | corresponding to Ly α at a redshift of 9 . 0942 ± 0 . 0019 |

## Qualitative findings

- [OIII]5007 cannot explain IRAC excess; excess arises from Balmer break of an older stellar population  
  > "We conclude therefore, that the IRAC excess can only arise from the stellar continuum around the Balmer break at ∼ 4000 A." (main text)

## Claim tuples

- H: Can ALMA spectroscopically confirm MACS1149-JD1 at z>9? | E: Band 7 scan of 314-340 GHz for [OIII] 88um | R: 7.4σ line at z=9.1096±0.0006 | F: Redshift precisely determined | **supported**
- H: Does the IRAC excess imply an earlier star formation episode? | E: Two-component SED fits with [OIII] and dust limits | R: Old component age ~290 Myr, formation z~15.4 | F: Dominant stellar population formed ~250 Myr after the Big Bang | **supported**
- H: Is there dust emission? | E: Continuum stack of all setups | R: No 3σ detection, <5.3 uJy/beam x (10/mu) | F: Low dust mass limit | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Four contiguous setups cover the photometric redshift range  
  > "To cover the uncertainty derived from the photometric redshift analysis" (Methods, ALMA observations and data reduction)
- Alternative: Single exponential/constant SFH and tau=300/400 Myr two-component models rejected  
  > "which we consider physically unacceptable" (Methods, SED modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Detailed parameters of the two components not uniquely determined; Lya detection tentative  
  > "Although the detailed parameters of these two components cannot be uniquely determined with the current data" (main text)
- Caveat (inferred, ours): Magnification mu=10 is fiducial with a wide model range (4.9-89)
- Caveat (inferred, ours): SED conclusions depend on assumed SFH shapes and fixed escape fraction
- Caveat (inferred, ours): Lya redshift offset tentative at 4σ

## Reproducibility

- Data public (paper): ALMA and X-Shooter data via archives  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00428.S" (Data availability)
- Products in archive: _not stated_
- Code: SED code KENSFIT available online  
  > "Our SED fitting code is our custom one, which is available at" (Code availability)
- Missing: CLEAN parameters
- Missing: Line/continuum channel selection details
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Public data and code, key numbers given, but imaging parameters missing and SED analysis model-dependent.
- Rediscovery candidate: yes, Public data, numeric line results, simple recipe for line detection.

## Links

- Method: Inoue et al. 2014 (cite: 19) ([OIII] 88um as redshift/SFR indicator)
- Companion: Zheng et al. 2017 (cite: 7) (HST/Spitzer photometry of MACS1149-JD1)
- Related: Hubble Frontier Fields

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 54,
  "rate": 0.692
 },
 "evidence_ok": true
}
```
