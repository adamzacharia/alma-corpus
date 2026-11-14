# Magnetic field at a jet base: extreme Faraday rotation in 3C 273 revealed by ALMA

`2019A&A...623A.111H` | Astronomy and Astrophysics 2019 | first author: Hovatta, T. | arXiv: 1803.09982 | DOI: 10.1051/0004-6361/201832587

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: What is the Faraday rotation measure and magnetic field structure at the jet base of 3C 273, probed by full-polarization ALMA 1 mm observations?  
  > "With these observations we were able to probe the optically thin polarized emission close to the jet base, and constrain the magnetic field structure." (abstract)
- Target **3C 273**: coordinates _not stated_; z/distance z = 0.158  
  > "the nearest high-power quasar 3C 273 ( z = 0.158; Strauss et al. 1992)" (1. Introduction); distance from Strauss et al. 1992  
  > "the nearest high-power quasar 3C 273 ( z = 0.158; Strauss et al. 1992)" (1. Introduction)

## Data provenance

- ALMA projects: 2016.1.01073.S
- bands: Band 6 (1.3 mm), full polarization  
  > "The Cycle 4 ALMA observations at band 6 (1.3 mm) were taken on December 20, 2016, using 44 of the 12m antennas." (2. ALMA observations and data reduction)
- frequencies and spectral setup: four 1.875 GHz spws, 64 channels of 31.25 MHz, at 224, 226, 240, 242 GHz; total 7.5 GHz  
  > "the four 1.875 GHz spectral windows (spw), each consisting of 64 channels that are 31.25 MHz wide, are placed at 224, 226, 240, and 242 GHz" (2. ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 44 12m antennas  
  > "using 44 of the 12m antennas" (2. ALMA observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.8 arcsec  
  > "The angular resolution (size of the synthesized beam) was 0.8 ′′ ." (2. ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 73 min on 3C 273  
  > "with a total integration time of about 73 min on 3C 273" (2. ALMA observations and data reduction)
- observing dates: December 20, 2016  
  > "were taken on December 20, 2016" (2. ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- External data: Near-core RM values at 4.7-8 GHz (250-450 rad m^-2) used for RM vs frequency fit  
  > "We used the range RM = 250 − 450 rad m −2 in the frequency range 4.7 − 8 GHz from Asada et al. (2002)." (4.1 RM as a function of frequency) [from Asada et al. 2002]
- External data: Near-core RM 1000-3000 rad m^-2 at 8-15 GHz  
  > "For the frequency range 8 − 15 GHz we use the range of near-core RM values of RM = 1000 − 3000 rad m −2" (4.1 RM as a function of frequency) [from Zavala & Taylor 2005; Hovatta et al. 2012]
- External data: RM lower limits 2.1-2.4e4 rad m^-2 at 43-86 GHz  
  > "For the 43 − 86 GHz range we use the range of lower limits 2.1 − 2.4 × 10 4 rad m −2 from Attridge et al. (2005) and Hada et al. (2016)." (4.1 RM as a function of frequency) [from Attridge et al. 2005; Hada et al. 2016]

## Processing

### Calibration

- pipeline or manual: Standard CASA calibration plus extra T-mode self-calibration and target bandpass calibration  
  > "we have self-calibrated the visibilities of our target using the CASA task gaincal in the so-called “T” mode" (2. ALMA observations and data reduction)
- casa version: CASA 4.7.0  
  > "The data reduction was done using Common Astronomical Software Applications (CASA) version 4.7.0." (2. ALMA observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C279, 5.86 Jy at 233 GHz, spectral index -0.63  
  > "assuming a flux density of 5.86 Jy at 233 GHz with a spectral index of −0.63" (2. ALMA observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: gaincal in T mode, then bandpass on target with solutions averaged in T mode  
  > "Afterwards, we run a bandpass calibration using the target’s visibilities, averaging also the solutions to “T” mode" (2. ALMA observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final rms: _not stated_

### Inherited from earlier work

- Standard data reduction and polarization calibration steps  
  > "For details of the standard data reduction and polarization calibration steps, see Nagai et al. (2016)." (2. ALMA observations and data reduction) [from Nagai et al. (2016)]
- Monte Carlo uncertainty assessment procedure  
  > "Following Vlemmings et al. (2017), we perform Monte Carlo (MC) simulations to assess the uncertainties in the Stokes parameters." (2. ALMA observations and data reduction) [from Vlemmings et al. (2017)]

### Not stated but needed to reproduce (our reading)

- Solution intervals for gaincal self-calibration and bandpass
- Initial and final bandpass/polarization calibrator details beyond 3C279
- Fitting priors/sampler and initial values for qu-fitting; multi-component fits are non-unique
- RM synthesis weighting settings
- Exact data used for lower-frequency RM fit and fit weighting

## Analysis recipe

1. **Extract Stokes I,Q,U,V per channel**: Fit a centered delta component to visibilities of each 31.25 MHz channel  
  > "We fit a centered delta component to each channel individually to obtain the Stokes I, Q, U, and V values." (2. ALMA observations and data reduction)
   - software: UVMULTIFIT, CASA
   - assumption: Emission dominated by central point source at phase center  
  > "we assume that the emission in 3C 273 is dominated by the central point source at the phase center of the image" (2. ALMA observations and data reduction)
   - fitting: _not stated_
   - validation: Cross-check with independent calibration by S. Kameno  
  > "We thank Prof. Seiji Kameno for providing us with independently calibrated polarization measurements for cross-checking our results." (Acknowledgements)
2. **Estimate systematic uncertainties**: 100 Monte Carlo realizations perturbing gain terms with Gaussian noise (Table A.1)  
  > "We report the standard deviation of the 100 MC simulations as the uncertainty for each parameter in Table 1." (2. ALMA observations and data reduction)
   - parameter: D-terms 1%, X-Y phase 2 deg, X-Y bandpass 0.1% and 0.5 deg, thermal 8.5e-5 Jy  
  > "D-terms (real and imag) 0 1%" (Table A.1)
   - assumption: Noise parameters are educated guesses  
  > "The noise parameters given in Table A.1 are based on an educated guess" (Appendix A)
   - fitting: _not stated_
   - validation: Sinusoidal Stokes V vs parallactic angle amplitude consistent with MC uncertainty  
  > "which indicates that our Monte Carlo estimates of polarimetric uncertainties are realistic" (Appendix A.2)
3. **Linear fit of EVPA vs lambda^2**: Fit EVPA vs λ² for RM and intrinsic EVPA, manually adjusting nπ ambiguities  
  > "we need to manually adjust for any possible n π ambiguities in the EVPAs" (3.1 RM determination)
   - assumption: Single external Faraday screen  
  > "The underlying assumption is that the RM is caused by a single external Faraday screen" (3.1 RM determination)
   - fitting: _not stated_
   - validation: _not stated_
4. **RM synthesis and RM CLEAN**: Faraday rotation measure synthesis on full dataset, then RM CLEAN  
  > "We also apply RM CLEAN (Heald et al. 2009) to deconvolve the RM spectrum" (3.1 RM determination)
   - software: RM synthesis, RM CLEAN
   - parameter: Faraday depth -2e8 to +2e8 rad m^-2 in steps of 1e4  
  > "The Faraday depth (φ) varies from −2 × 10 8 to +2 × 10 8 rad m −2 sampled at intervals of 10 4 rad m −2 ." (Figure 2 caption)
   - fitting: _not stated_
   - validation: No additional RM CLEAN peaks above noise  
  > "find no additional peaks in the RM spectrum significantly above the band-averaged noise level of ∼0.3 mJy beam −1" (3.1 RM determination)
5. **qu-fitting of depolarization models**: Fit Stokes q,u with single-component, two-component and internal Faraday rotation models  
  > "In order to investigate the Faraday depolarization properties of the data in a quantitative manner, we used the qu-fitting technique." (3.2 Polarization modeling)
   - fitting: _not stated_
   - validation: Acknowledged non-unique solutions  
  > "This is again one plausible set of parameters that fit the data, but it is not necessarily a unique solution." (3.2 Polarization modeling)
6. **RM vs frequency power-law**: Linear fit of RM vs frequency using literature core RMs and the ALMA RM, range used as uncertainty  
  > "we take their mean as the RM value and use the range as an uncertainty in the calculation of the slope" (4.1 RM as a function of frequency)
   - assumption: Conical jet in equipartition, |RM| ∝ ν^a  
  > "in a conical jet under equipartition the RM is expected to follow a relation |RM| ∝ ν a" (4.1 RM as a function of frequency)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: Data reduction, calibration, gaincal self-calibration  
  > "The data reduction was done using Common Astronomical Software Applications (CASA) version 4.7.0." (2. ALMA observations and data reduction)
- **UVMULTIFIT** : Fitting visibilities to get per-channel Stokes parameters  
  > "we use the external CASA library UVMULTIFIT (Martí-Vidal et al. 2014) to fit the visibility data" (2. ALMA observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| RM from linear EVPA fit | 5.01e5 | 0.04e5 | rad m^-2 | 3 | RM= (5.01 ± 0.04) × 10 5 rad m −2 |
| RM from RM synthesis | 4.8e5 | 0.2e5 | rad m^-2 | 4 | we find an RM of (+4.8 ± 0.2) × 10 5 rad m −2 |
| Linear polarization fraction (RM synthesis) | 1.81 | 0.01 | % | 4 | degree of polarization of (1.81±0.01)% |
| RM from simple qu-fit | 4.95e5 | 0.25e5 | rad m^-2 | 5 | RM=4.95 ± 0.25 × 10 5 rad m −2 |
| Intrinsic EVPA chi_0 (qu-fit) | -107.1 | 2.3 | deg | 5 | χ 0 = −107.1 ± 2.3 deg |
| RM-frequency power-law index a | 2.0 | 0.2 | dimensionless | 6 | We obtain a = 2.0 ± 0.2 |
| Fractional circular polarization | ~0.2 | not stated | % | 0 | This would indicate a fractional circular polarization of ∼ 0.2%. |
| Rest-frame RM | 6.7e5 | not stated | rad m^-2 | 0 | RM int = RM obs (1 + z ) 2 = 6.7 × 10 5 rad m −2 |

## Qualitative findings

- Polarization fraction increases with wavelength (inverse depolarization), requiring multiple components or internal Faraday rotation.  
  > "The polarization fraction increases as a function of wavelength" (abstract)

## Claim tuples

- H: Is there a very high RM in 3C 273 at 1 mm? | E: Linear EVPA fit, RM synthesis and qu-fitting of ALMA band 6 data | R: RM ~5e5 rad m^-2 | F: Faraday rotation exceeds 40 deg and cannot be ignored at mm wavelengths | **supported**
- H: Can a single component with external screen explain the polarization? | E: qu-fitting of three models | R: Polarization fraction rises with wavelength | F: Need two or more components or internal Faraday rotation; models are not distinguishable | **partially**
- H: Does RM scale with frequency consistent with a conical jet sheath? | E: Fit of RM vs frequency with literature values | R: a = 2.0 ± 0.2 | F: Consistent with sheath around conical jet (upper limit) | **partially**
- H: Is circular polarization detectable in the ALMA data? | E: MC assessment of Stokes V | R: ~10 mJy intrinsic V, ~0.2% | F: Tentative detection needing confirmation | **partially**

## Reasoning

- Why this data: 3C 273 selected as pilot because lower-frequency data suggested |RM| > 2e4 rad m^-2  
  > "We selected 3C 273 for our pilot study because earlier observations of it in the 7mm to 3mm range have shown indications of" (1. Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Limited wavelength coverage and angular resolution prevent distinguishing models  
  > "because of the limited wavelength coverage and angular resolution, our observations cannot distinguish between the two cases" (4. Discussion)
- Caveat (inferred, ours): MC noise parameters are educated guesses
- Caveat (inferred, ours): Extra self-calibration on the polarized target may bias polarization
- Caveat (inferred, ours): Single epoch; variability
- Caveat (inferred, ours): RM-frequency fit uses lower limits and ranges from different epochs

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Solution intervals for extra calibration
- Missing: qu-fitting fitting setup
- Missing: RM synthesis code and weights
- Data volume (inferred): ~10-30 GB raw for one 73 min Band 6 polarization track
- Score (inferred): 5/5, Data identified by project code and Table 1 gives per-channel results, but extra calibration and fitting details are incomplete.
- Rediscovery candidate: yes, Project code given and results numeric (RM, polarization fraction), though recipe has gaps.

## Links

- Method: Martí-Vidal et al. 2014 (UVMULTIFIT)
- Method: Nagai et al. 2016 (Standard polarization calibration)
- Method: Vlemmings et al. 2017 (Monte Carlo uncertainty approach)
- Method: Brentjens & de Bruyn 2005 (RM synthesis)
- Method: O'Sullivan et al. 2012 (qu-fitting)
- Companion: Martí-Vidal et al. 2015 (High RM in PKS 1830-211 with ALMA)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 39,
  "rate": 0.513
 },
 "evidence_ok": true
}
```
