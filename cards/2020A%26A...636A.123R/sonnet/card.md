# Discovery of a complex spiral-shell structure around the oxygen-rich AGB star GX Monocerotis

`2020A&A...636A.123R` | Astronomy and Astrophysics 2020 | first author: Randall, S. K. | arXiv: - | DOI: 10.1051/0004-6361/201935787

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What is the circumstellar envelope morphology of the O-rich AGB star GX Mon in CO(2-1) and other lines, and is it consistent with a binary-induced spiral?  
  > "The resulting CO (2–1) map reveals an intricate, complex circumstellar spiral-arc structure consistent with hydrodynamical models for an AGB experiencing mass loss in a highly eccentric, close binary" (abstract)
- Target **GX Mon**: coordinates _not stated_; z/distance ~650 pc  
  > "a Mira-type variable at an approximate distance of around 650 pc" (1. Introduction); distance from average of Karovicova et al. 2013 and Danilovich et al. 2015  
  > "we assumed an average of the values quoted by Karovicova et al. 2013; Danilovich et al. 2015" (1. Introduction)

## Data provenance

- ALMA projects: 2016.1.00652.S
- bands: Band 6  
  > "The spectral setup used in the ALMA Band 6 covers the 215.13−218.88 and 230.14−232.98 GHz frequency ranges" (2. Data acquisition and processing)
- frequencies and spectral setup: 0.6 km/s resolution for CO window, ~1.3 km/s for other windows  
  > "a spectral velocity resolution of 0.6 km s −1 for the spectral window containing the 12 CO (2−1) line and ∼1.3 km s −1 for the other spectral windows" (2. Data acquisition and processing)
- continuum bandwidth: _not stated_
- arrays: extended 12-m (C40-6), compact 12-m (C40-3), 7-m ACA  
  > "Data from three different arrays were combined: C40-6 (our extended 12-m configuration), C40-3 (compact 12-m configuration), and the 7-m Atacama Compact Array (ACA)." (2. Data acquisition and processing)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.16 arcsec (CO); 0.19 x 0.13 arcsec, PA -69.4 deg  
  > "This yields an angular resolution of ∼0.16 ′′ (for the CO image)" (2. Data acquisition and processing)
- max recoverable scale: 30 arcsec  
  > "the inclusion of the 7-m array data allows us to recover structures as large as 30 ′′" (2. Data acquisition and processing)
- sensitivity: 1.0 mJy/beam per 1.3 km/s  
  > "with a typical sensitivity of 1.0 mJy beam −1 per 1.3 km s −1" (2. Data acquisition and processing)
- time on source: 2994 s, 907 s, 1210 s (extended 12-m, compact 12-m, 7-m); total 1.4 h  
  > "the on-source times were 2994 s, 907 s, and 1210 s, for the extended 12-m, compact 12-m, and 7-m array, respectively" (2. Data acquisition and processing)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: SO 3Σ J=5-4 (215.221 GHz)
- Line: SiO v=0 J=5-4 (217.105 GHz)
- Other facility **HST/ACS**: archival F606W and F814W image compared to SO  
  > "composite ACS/HST image of GX Mon in the F606W and F814W bands" (Figure 2 caption)
- External data: mass-loss rate 8.5e-6 Msun/yr and systemic velocity -9 km/s  
  > "a relatively high mass-loss rate of 8.5 × 10 −6 M ⊙ yr −1 and a systemic velocity of −9 km s −1 (Danilovich et al. 2015)" (1. Introduction) [from Danilovich et al. 2015]
- External data: stellar mass 1 Msun and radius 2.7 AU  
  > "mass of GX Mon M 1 = 1 M ⊙ (Justtanont et al. 1994)" (4. Discussion) [from Justtanont et al. 1994]
- Simulation/model as data: 3D hydrodynamical eccentric-binary model (e=0.8, P=138 yr, inclination 45 deg), same code as Kim et al. 2019  
  > "we constructed our own threedimensional hydrodynamical simulations designed to be more representative of GX Mon, based on the same code as those presented by Kim et al. (2019)" (4. Discussion)

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline, each array calibrated independently  
  > "The data for the different arrays were independently calibrated using the ALMA Pipeline." (2. Data acquisition and processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231 (7-m, compact 12-m), J0510+1800 (extended 12-m)  
  > "the flux calibrators were J0750+1231, J0750+1231, and J0510+1800 for the 7-m, compact 12-m, and extended 12-m configurations, respectively" (2. Data acquisition and processing)
- flux scale uncertainty: ~10%  
  > "the error achieved for the flux calibration is approximately 10%" (2. Data acquisition and processing)
- self calibration: _not stated_

### Imaging

- task: CASA TCLEAN on merged uv data  
  > "All the images presented here were then produced using the TCLEAN algorithm in CASA." (2. Data acquisition and processing)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "a standard Briggs weighting scheme with a robust parameter of 0.5" (2. Data acquisition and processing)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual channel-by-channel masks plus automated masking for complex lines; single elliptical mask for compact lines  
  > "For molecular transitions that show only compact and/or non-complex emission, a single elliptical mask was used." (2. Data acquisition and processing)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: merged in uv domain, no extra weighting between 12-m and 7-m  
  > "No additional weighting was applied between the 12- and 7-m data" (2. Data acquisition and processing)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- details of hydrodynamical model and parameter effects  
  > "We invite the reader to refer to this publication as well as Kim & Taam (2012) and Kim et al. (2017) for details on the models" (4. Discussion) [from Kim et al. 2019; Kim & Taam 2012; Kim et al. 2017]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- cell size, image size, clean threshold, niter
- continuum subtraction and line-free channels
- multiscale scales used
- how the angle-radius diagram was built (center, deprojection)
- hydrodynamic code and setup details such as resolution and rendering of model images
- phase calibrator names and observing dates

## Analysis recipe

1. **combine arrays and image**: merge calibrated 12-m extended, compact and 7-m data in uv and image with tclean  
  > "we merged all the calibrated data from the extended and compact 12-m, and 7-m arrays in the visibility ( u v) domain." (2. Data acquisition and processing)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "a robust parameter of 0.5" (2. Data acquisition and processing)
   - fitting: _not stated_
   - validation: _not stated_
2. **identify spiral features**: angle-radius diagram of systemic-velocity CO channel, features marked by eye  
  > "We used this plot to identify the following features by eye" (4. Discussion)
   - fitting: _not stated_
   - validation: compared qualitatively to Kim et al. 2019 models  
  > "A first comparison with the models recently published by Kim et al. (2019) reveals that the best compatibility of the features observed lies with the eccentric binary models" (4. Discussion)
3. **run representative binary hydrodynamic model**: 3D hydro simulation with M1=1, M2=1 Msun, e=0.8, wind 22 km/s, P=138 yr, inclination 45 deg; compare qualitatively with CO  
  > "orbital period P orb = 138 yr (determined by the pattern spacing in the CO emission image divided by the wind speed)" (4. Discussion)
   - parameter: adiabatic index 1.4, domain 4000 AU  
  > "We employed an adiabatic index γ = 1.4 and a computation domain size of 4000 AU" (4. Discussion)
   - assumption: companion mass 1 Msun and e=0.8 assumed; distance 650 pc  
  > "companion mass M 2 = 1 M ⊙ (assumption), orbital eccentricity e = 0.8 (assumption)" (4. Discussion)
   - fitting: no quantitative fit  
  > "Although the observed morphology is too messy and noisy for a quantitative model fit" (5. Conclusion)
   - validation: qualitative overlay of observed features on model  
  > "The spiral structure extracted from the observations is over-plotted and shows a good agreement with the model." (4. Discussion)

## Software

- **CASA** : merging data and tclean imaging  
  > "we created our own final multi-scale images manually using CASA" (2. Data acquisition and processing)
- **ALMA Pipeline** : calibration  
  > "independently calibrated using the ALMA Pipeline" (2. Data acquisition and processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) line peak | 132 | not stated | mJy/beam | 1 | CO J = (2−1) 230.538 0.93 0.19 × 0.13 –34.2, +11.3 132 |
| continuum integrated flux | 9 | not stated | mJy | 1 | with an integrated flux of 9 mJy based on a 2D Gaussian fitting |
| model orbital period | 138 | not stated | yr | 3 | orbital period P orb = 138 yr |
| binary separation range for M2 0.3-3 Msun | 30-43 | not stated | AU | 3 | Varying M 2 between 0.3 and 3 M ⊙ gives a binary separation between 30 and 43 AU |
| CO envelope radius | ~6 arcsec (4000 AU) | not stated | arcsec | 1 | extending out to a radius of ∼6 ′′, or 4000 AU from the star |

## Qualitative findings

- SO(5-4) shows a weaker arc/ring structure similar to CO, with an asymmetric ridge to the south/south-east  
  > "the SO (5–4) transition appears to show a similar morphology" (3.2 SO (5–4))

## Claim tuples

- H: Is the GX Mon CSE shaped by an eccentric binary companion? | E: Compare CO systemic-velocity channel features with a 3D hydrodynamical model | R: Spiral with bifurcations and wiggles matched qualitatively by e=0.8, P~138 yr model | F: Consistent with close, highly eccentric binary | **partially**
- H: Does SO trace the CO structure? | E: Image SO(5-4) and compare PV diagrams | R: Weak arc/ring matches CO outer arc at ~5 arcsec | F: Similar distribution, needs more sensitivity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: variable mass loss, third stellar component, or ISM interaction as extra factors  
  > "such as variable mass loss, a third stellar component, or interactions of the CSE with the interstellar medium" (5. Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): morphology too messy for quantitative fit; model units not comparable to observed flux  
  > "the units of column density per projected velocity unit in the model image cannot be directly translated to the observed flux per beam on an absolute scale" (4. Discussion)
- Caveat (inferred, ours): Feature identification by eye, subjective
- Caveat (inferred, ours): Model parameters (M2, e, inclination) assumed, not fitted; degeneracies
- Caveat (inferred, ours): Distance uncertain (Gaia unusable)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Hydrodynamic code not released
- Missing: CASA version and clean parameters
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Imaging recipe fairly given, but analysis is qualitative and model code and several parameters are missing.
- Rediscovery candidate: no, Main result is qualitative morphology and the modelling is not reproducible from the text.

## Links

- Method: Kim et al. 2019, ApJS, 243, 35 (hydrodynamical models and code)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 36,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
