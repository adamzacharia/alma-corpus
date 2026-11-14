# First M87 Event Horizon Telescope Results. V. Physical Origin of the Asymmetric Ring

`2019ApJ...875L...5E` | The Astrophysical Journal Letters 2019 | first author: Event Horizon Telescope Collaboration | arXiv: 1906.11242 | DOI: 10.3847/2041-8213/ab0f43

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is the EHT2017 1.3 mm asymmetric ring in M87 consistent with a Kerr black hole with a GRMHD accretion flow, and what do the data imply for black hole spin, magnetic flux and jet power?  
  > "we test whether or not the results of the 2017 EHT observing campaign (hereafter EHT2017) are consistent with the black hole hypothesis." (1. Introduction)
- Target **M87**: coordinates _not stated_; z/distance 16.9 Mpc  
  > "Models of the stellar velocity distribution imply a mass for the central core" (1. Introduction); "a distance of 16.9 Mpc (see also EHT Collaboration et al. 2019e, (hereafter Paper VI; Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018)" (2. Review and Estimates); distance from Paper VI; Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018  
  > "Models of the stellar velocity distribution imply a mass for the central core" (1. Introduction); "a distance of 16.9 Mpc (see also EHT Collaboration et al. 2019e, (hereafter Paper VI; Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018)" (2. Review and Estimates)

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: 1.3 mm (230 GHz) VLBI; high-band data of 2017 April 6  
  > "we focus on comparisons with a single data set, the 2017 April 6 high-band data (Paper III)." (4. Procedure for Comparison of Models with Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: EHT2017 campaign; 2017 April 6 data set used  
  > "The 2017 April 6 data set has the largest number of scans, 284 detections in 25 scans (see Paper III)" (4. Procedure for Comparison of Models with Data)
- pi or archival as stated: _not stated_
- Other facility **Chandra and NuSTAR**: Simultaneous X-ray observations giving 2-10 keV luminosity used to reject overluminous models  
  > "we simultaneously observed M87 with the Chandra X-ray observatory and the Nuclear Spectroscopic Telescope Array (NuSTAR)." (6.2. X-Ray Constraints)
- External data: M87 black hole mass 6.2e9 Msun from stellar dynamics  
  > "Models of the stellar velocity distribution imply a" (1. Introduction) [from Gebhardt et al. 2011]
- External data: Large-scale jet PA ~288 deg and jet angle to line of sight 17 deg  
  > "Walker et al. (2018) estimated that the angle between the approaching jet and the line of sight is 17°." (2. Review and Estimates) [from Walker et al. (2018)]
- Simulation/model as data: Simulation Library of 43 GRMHD simulations (SANE and MAD, spins -0.94 to 0.98), 23 TB, ray-traced into an Image Library of ~60,000 images  
  > "The Simulation Library occupies 23 TB of disk space and contains a total of 43 GRMHD simulations" (3.1. Simulation Library); "The Image Library contains of order 60,000 images." (3.3. Image Library Summary)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

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

- EHT2017 array, observing campaign, correlation and calibration  
  > "for details on the array, 2017 observing campaign, correlation, and calibration, see Paper II and Paper III" (2. Review and Estimates) [from Paper II and Paper III (EHT Collaboration 2019b, 2019c)]
- Image-model fitting and Average Image Scoring details  
  > "see also Section 4 of Paper VI for details" (4. Procedure for Comparison of Models with Data) [from Paper VI (EHT Collaboration 2019e)]
- Flux normalization of ~0.5 Jy for model images  
  > "We use this freedom to adjust M so that the average image from a GRMHD model has a 1.3 mm flux density ≈0.5 Jy (see Paper IV)." (3.2. Image Library Generation) [from Paper IV]

### Not stated but needed to reproduce (our reading)

- Public EHT2017 visibility data and closure-quantity data products (not given here)
- THEMIS and GENA fitting settings, priors and chain configuration (deferred to Paper VI and in-prep papers)
- GRMHD and GRRT code versions and run parameters
- Exact snapshot selection and ISCO/time sampling per model

## Analysis recipe

1. **Generate GRMHD Simulation Library**: _not stated_
   - software: BHAC, H-AMR, iharm, KORAL
   - parameter: _not stated_
   - assumption: Untilted disks, thermal electron distribution  
  > "We have assumed that the disk angular momentum vector and black hole spin vector are (anti-) aligned." (7.3. Other Models and Analysis Limitations)
   - fitting: _not stated_
   - validation: Multiple codes and resolutions give consistent results  
  > "with some repeated at multiple resolutions with multiple codes, with consistent results" (3.1. Simulation Library)
2. **Produce synthetic image library**: GRRT with Rhigh electron temperature prescription, mass scaled so flux is ~0.5 Jy  
  > "were produced using the general relativistic ray-tracing (GRRT)" (Section 3)
   - software: ipole, RAPTOR, BHOSS
   - parameter: Rhigh = 1, 10, 20, 40, 80, 160; i = 12, 17, 22, 158, 163, 168 deg; 160x160 microarcsec FOV, 1 microarcsec pixels  
  > "The model images are generated with a 160 ´ 160 _m_ as field of view and 1 _m_ as pixels" (3.2. Image Library Generation)
   - assumption: M = 6.2e9 Msun, D = 16.9 Mpc, M/D = 3.62 microarcsec  
  > "The ratio _GM_ ( _c_ 2 _D_ ) = 3.62 _m_ as" (3.2. Image Library Generation)
   - fitting: _not stated_
   - validation: Tests with M=3.5e9 Msun, different resolution and flux show insensitivity  
  > "The comparisons with the data are also insensitive to image resolution." (3.3. Image Library Summary)
3. **Fit snapshots to EHT visibilities**: Reduced chi-square fits varying M/D, flux, PA and station gains, by two pipelines  
  > "The best-fit parameters ( _M_ _D_, _F_ _n_, PA) for each snapshot are found by two pipelines independently" (4. Procedure for Comparison of Models with Data)
   - software: THEMIS, GENA
   - fitting: _not stated_
   - validation: Two independent pipelines give qualitatively similar results  
  > "with qualitatively similar results" (Figure 7)
4. **Average Image Scoring**: THEMIS-AIS tests whether data chi-square distance to model average image is drawn from model distribution; models rejected if mean p <= 0.01  
  > "we can assign a probability p that the data is drawn from a specific model’s distribution." (4. Procedure for Comparison of Models with Data)
   - software: THEMIS
   - fitting: _not stated_
   - validation: _not stated_
5. **Apply radiative, X-ray and jet power constraints**: Compute efficiency and L_X with Monte Carlo radiative transfer; measure Pjet in simulations; reject models failing thresholds  
  > "with the Monte Carlo code grmonty" (Section 6)
   - software: grmonty
   - parameter: Pjet,min = 1e42 erg/s; L_X obs = 4.4e40 erg/s; (beta gamma)cut = 1  
  > "adopt a very conservative lower limit on jet power º _P_ jet,min = 10 42 erg s - 1 ." (6.3. Jet Power)
   - fitting: _not stated_
   - validation: Sensitivity to the jet definition tested using Pout and varied cutoff  
  > "This conclusion is not sensitive to the definition of P jet" (6.3. Jet Power)

## Software

- **THEMIS** : _not stated_
- **GENA** : _not stated_
- **grmonty** : Monte Carlo radiative transfer for L_bol and L_X  
  > "We calculate _L_ bol with the Monte Carlo code grmonty" (6.1. Radiative Equilibrium)
- **ipole** : General relativistic ray tracing of snapshots  
  > "schemes ipole" (Section 3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit M/D peak for best snapshots | ~3.6 | width about 0.5 | microarcsec | 3 | the distribution narrows and peaks close to _M_ _D_ ~ 3.6 _m_ as with a width of about 0.5 _m_ as . |
| Mean best-fit PA, spin-away models (THEMIS/GENA) | 209 / 203 | sigma_PA = 54 / 55 | degrees | 3 | mean 209 (203) and _s_ PA = 54 (55) |
| Minimum reduced chi-square over image library | 1.79 | not stated | dimensionless | 3 | the minimum _c_ _n_ 2 = 1.79 over the entire set of the more than 60,000 individual images |
| Mean AIS p for MAD a*=-0.94 | 0.01 | all models p <= 0.04 | dimensionless | 4 | On average this group has p = 0.01 |
| Spindown time, a*=0.94 MAD Rhigh=160 | 7.3e12 | not stated | yr | 5 | t = 7.3 ´ 10 12 yr, which is long compared to a Hubble time |

## Qualitative findings

- All a*=0 models are rejected by the jet power constraint; spin vector points away from Earth if aligned with the large-scale jet.  
  > "Models in our library of non-spinning black holes are inconsistent with the observations as they do not produce sufficiently powerful jets." (abstract)

## Claim tuples

- H: EHT2017 M87 image is consistent with a Kerr black hole with a GRMHD accretion flow | E: Compare ~60,000 synthetic images to 2017 April 6 data with THEMIS and GENA | R: M/D peaks near 3.6 microarcsec and most models pass average image scoring | F: Data consistent with lensed synchrotron emission near a Kerr black hole | **supported**
- H: Black hole spin orientation can be inferred from ring asymmetry | E: Compare best-fit PA distributions to the large-scale jet PA of ~288 deg | R: Jet PA consistent with spin-away models, off the shoulder of spin-toward | F: Spin points away from Earth if aligned with the jet | **supported**
- H: Non-spinning black holes can power the M87 jet | E: Measure Pjet in models against Pjet,min = 1e42 erg/s | R: All a*=0 models fall below the threshold | F: a*=0 models ruled out; jet powered by Blandford-Znajek extraction | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Superspinars and naked singularity models ruled out qualitatively; boson stars and gravastars considered in another paper  
  > "the EHT2017 observations rule out any superspinar model for M87." (7.4. Alternatives to Kerr Black Holes)
- How they decided it was enough: _not stated_
- Limitation (authors): Thermal single-parameter electron model, untilted disks, nonradiative GRMHD, fast-light approximation  
  > "We have interpreted the EHT2017 data using a limited library of models with attendant limitations." (7. Discussion)
- Caveat (inferred, ours): Conclusions depend on the Rhigh thermal electron prescription and the conservative Pjet threshold
- Caveat (inferred, ours): Single-day data set with correlated epochs; fit variability handled only through model snapshots
- Caveat (inferred, ours): ALMA is only one station in the EHT array; no ALMA-specific processing is given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Visibility data and Paper III/VI calibrated products
- Missing: THEMIS/GENA configuration
- Missing: GRMHD simulation outputs (23 TB)
- Missing: Several referenced codes marked in preparation
- Data volume (inferred): Simulation Library 23 TB; EHT visibility data small (GB scale)
- Score (inferred): 2/5, Large unreleased simulation library and companion-paper pipelines make full reproduction impractical.
- Rediscovery candidate: no, The recipe depends on a 23 TB simulation library and in-preparation pipelines; ALMA's role is as a VLBI station.

## Links

- Method: EHT Collaboration et al. 2019e (Paper VI) (Model comparison, THEMIS-AIS and GENA details)
- Companion: EHT Collaboration et al. 2019a-d (Papers I-IV) (Array, calibration and imaging of M87)
- Related: Event Horizon Telescope 2017 campaign

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
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
  "facts": 77,
  "stated": 29,
  "rate": 0.377
 },
 "evidence_ok": true
}
```
