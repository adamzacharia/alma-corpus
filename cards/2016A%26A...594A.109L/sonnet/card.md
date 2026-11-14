# ALMA's view of the nearest neighbors to the Sun. The submm/mm SEDs of the α Centauri binary and a new source

`2016A&A...594A.109L` | Astronomy and Astrophysics 2016 | first author: Liseau, R. | arXiv: 1608.02384 | DOI: 10.1051/0004-6361/201629135

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, solar_system
- Question: What are the submm/mm SEDs and chromospheric temperature structures of alpha Cen A and B, and what is a new point source detected in Band 8?  
  > "The comparison of the observed spectral energy distributions with theoretical model computations provides the chromospheric structure in terms of temperature and density above the stellar photosphere" (abstract)
- Target **alpha Cen A and B**: coordinates A: 14 39 28.893 -60 49 57.86 (Band 3 epoch, Table pos)  
  > "Outside the solar system, Alpha Centauri ($\alpha \, {\rm Cen}$) is our nearest neighbour, only a little more than a parsec away ($\pi=\,$0$\stackrel {\prime \prime}{_{\bf \cdot}}$742)." (Introduction); z/distance parallax 0.742 arcsec  
  > "Outside the solar system, Alpha Centauri ($\alpha \, {\rm Cen}$) is our nearest neighbour, only a little more than a parsec away ($\pi=\,$0$\stackrel {\prime \prime}{_{\bf \cdot}}$742)." (Introduction); distance from _not stated_
- Target **U (unidentified Band 8 point source)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00170.S
- bands: Bands 3, 4, 6, 7, 8, 9 (97.5-679 GHz)  
  > "The binary $\alpha \, {\rm Cen\,A}$B was observed in all six ALMA continuum bands during the period July 2014 to May 2015" (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 8 GHz effective bandwidth over four spectral windows (Bands 4, 6, 8)  
  > "8 GHz effective bandwidth spread over four spectral windows in each of the bands" (2 Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.2 to 1.5 arcsec  
  > "the angular resolution (synthesized half power beam width) ranged from 0$\stackrel {\prime \prime}{_{\bf \cdot}}$2 to 1$\stackrel {\prime \prime}{_{\bf \cdot}}$5" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 4 5.5 min; Band 6 ~2 min; Band 8 ~7 min  
  > "with $\sim$ 24 min of observing time with 5.5 min on-source" (2 Observations and data reduction)
- observing dates: 2014-07-03 to 2015-05-02  
  > "2015-05-02" (Table pos)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: only proposed/privately communicated 17 GHz detections; S/N estimates computed by authors  
  > "C. Trigilio privately communicated to us that both stars were recently detected at 17 GHz." (3.2 Spectral slopes of the SEDs)
- External data: Stellar angular diameters/radii of A and B  
  > "With angular diameters of 0$\stackrel {\prime \prime}{_{\bf \cdot}}$008 and 0$\stackrel {\prime \prime}{_{\bf \cdot}}$006 for A and B at 2 $\mu$m (cite: kervella2003)" (2 Observations and data reduction) [from (cite: kervella2003)]
- External data: Quiet Sun brightness temperatures for comparison  
  > "is compared with observed values for the Quiet Sun (cite: loukitcheva2004)." (4.1 The stellar brightness temperatures) [from (cite: loukitcheva2004)]
- Simulation/model as data: Semi-empirical non-LTE chromosphere model based on modified solar C7 model  
  > "based on a modified hydrostatic equilibrium model (C7) of the solar chromosphere (cite: avrett2008; delaluz2014)" (4.2 Theoretical model chromospheres)

## Processing

### Calibration

- pipeline or manual: standard flagging and calibration in CASA  
  > "The visibilities were flagged and calibrated following standard procedures using the CASA package" (2 Observations and data reduction)
- casa version: v4.2.2 (Bands 4, 6); v4.3.1 (Band 8)  
  > "v4.2.2 for Band 4 and 6, and v4.3.1 for Band 8" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (B4), quasar 1427-421 (B6), Titan (B8)  
  > "while Titan was used in Band 8 when it was at 50$^{\circ}$ elevation" (2 Observations and data reduction)
- flux scale uncertainty: goals: <5% B3/B4, <10% B6/B7, ~20% B8/B9  
  > "better than 5% for bands B 3 and B 4, better than 10% for B 6 and B 7, and at best about 20% for B 8 and B 9" (3 Results)
- self calibration: one round of phase-only self-cal in Bands 4, 6, 8  
  > "one round of phase-only self-calibration was carried out on all three images to improve the rms noise" (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (Bands 4, 6, 8)  
  > "Imaging was performed using natural weighting in Band 4, 6, and 8" (2 Observations and data reduction)
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

- Band 3, 7 and 9 observations and reduction  
  > "the observations in Band 3, 7 and 9 have already been described in detail by (cite: liseau2015) and will not be repeated here." (2 Observations and data reduction) [from (cite: liseau2015)]
- Chromosphere non-LTE model details  
  > "both the ionization-excitation and the radiative transfer are treated in non-LTE (De la Luz & Tapia, in preparation)" (4.2 Theoretical model chromospheres) [from De la Luz & Tapia, in preparation]

### Not stated but needed to reproduce (our reading)

- Imaging task, cell and image size, and masking
- Method of flux extraction (point-source fit vs. aperture)
- Band 3, 7, 9 calibration and imaging parameters
- Model code and inputs for the chromosphere model (in preparation)
- Details of position/flux fit and error budget for U
- Self-calibration solution interval

## Analysis recipe

1. **Calibrate and image Bands 4, 6, 8**: CASA calibration, natural weighting imaging, one round of phase-only self-cal  
  > "Imaging was performed using natural weighting in Band 4, 6, and 8 with one round of phase-only self-calibration" (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure flux densities and spectral indices**: Linear regression of log S vs log nu; separate spw imaging for in-band indices  
  > "linear regression (cite: press1986) to the Band 3 to 9 data results in a spectral index" (3.2 Spectral slopes of the SEDs)
   - fitting: chi2 linear fit; goodness-of-fit Q  
  > "The goodness-of-fit is $Q=0.9999$ for both." (3.2 Spectral slopes of the SEDs)
   - validation: _not stated_
3. **Convert flux to brightness temperature**: Planck-based Eq. 1 with stellar radii, h/R ~ 1e-4 assumed  
  > "We assume similar $h/R$-values for the $\alpha \, {\rm Cen}$ stars and use their photospheric radii" (4.1 The stellar brightness temperatures)
   - assumption: Photospheric radii from Kervella et al. 2003; optically thick free-free in RJ regime  
  > "We assume similar $h/R$-values for the $\alpha \, {\rm Cen}$ stars and use their photospheric radii, i.e. $R_{\rm star}+h \sim R_{\rm star}$, where $R_{\rm star}$ refers to the values determined by (cite: kervella2003)." (Discussion, The stellar brightness temperatures)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model chromosphere**: Modified solar C7 semi-empirical non-LTE model fitted to T_B(lambda)  
  > "The temperature profile is computed iteratively from the modified density/pressure structure, ionization balance and opacity (lines and continua)." (4.2 Theoretical model chromospheres)
   - fitting: _not stated_
   - validation: Compared with Quiet Sun and model fit to data  
  > "In Fig. [3](#a_sun), $T_{\rm B}(\lambda)$ for the disk integrated $\alpha \, {\rm Cen\,A}$ is compared with observed values for the Quiet Sun (cite: loukitcheva2004)." (Discussion, The stellar brightness temperatures)

## Software

- **CASA** v4.2.2, v4.3.1: calibration and imaging  
  > "using the CASA package[^1] v4.2.2 for Band 4 and 6, and v4.3.1 for Band 8" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average flux ratio S(B)/S(A), Bands 3-9 | 0.464 | 0.051 | dimensionless | 2 | $[S_{\!\nu}({\rm B})/S_{\!\nu}({\rm A})]_{\rm ave}=0.464 \pm 0.051$ |
| Spectral index alpha_A, Bands 3-9 | 1.92 | 1.06 | dimensionless | 2 | $\alpha_{\rm A,\,3-9}=1.92 \pm 1.06$ |
| Spectral index alpha_B, Bands 3-9 | 1.97 | 1.50 | dimensionless | 2 | $\alpha_{\rm B,\,3-9}=1.97 \pm1.50$ |
| alpha Cen A Band 8 flux | 35.32 | 0.21 | mJy | 2 | $35.32\pm 0.21$1 \[168\] |
| alpha Cen A T_min | 3548 at h=615 km | not stated | K | 4 | $T_{\rm min}=3548$ K at $h=615$ km |
| alpha Cen B T_min | 3407 at 560 km | not stated | K | 4 | The corresponding model parameters for $\alpha \, {\rm Cen\,B}$ are 3407 K, 560 km |
| Source U Band 8 flux | 4.24 | 0.49 | mJy | 2 | $4.24\pm 0.49$ |

## Qualitative findings

- SEDs flatten at long wavelengths, likely optically thin free-free beyond 1.5 mm  
  > "likely because the free-free emission is turning from optically thick to thin beyond 1.5 mm" (4.2)

## Claim tuples

- H: Do modified solar chromosphere models reproduce alpha Cen submm/mm SEDs? | E: Compared Band 3-9 brightness temperatures with modified C7 model | R: T_min/T_eff=0.61 for A; good fit except Band 3 | F: Solar-like non-radiative heating operates in alpha Cen | **supported**
- H: What is source U? | E: Single Band 8 detection with upper limits elsewhere; solar system object search | R: 4.24 mJy at 740 um; no known object to V=26 | F: Likely a distant solar system object (ETNO), but uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Companion star, planet at alpha Cen, and Pluto-like body for U rejected  
  > "A companion star of the $\alpha \, {\rm Cen}$ system does not present a viable explanation" (4.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Single epoch, single detection for U  
  > "With only one epoch and only one detection, we are left with little information regarding that object’s nature" (abstract)
- Caveat (inferred, ours): Model details unpublished so not reproducible
- Caveat (inferred, ours): Spectral index errors very large (about 1)
- Caveat (inferred, ours): Flux calibration with Titan/Ceres at different elevation from target
- Caveat (inferred, ours): Band 3 flux not fit by model

## Reproducibility

- Data public (paper): Project 2013.1.00170.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00170.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Chromosphere model code and inputs
- Missing: Flux extraction method
- Missing: Imaging parameters
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple flux measurements, but model is unpublished and imaging details are sparse.
- Rediscovery candidate: no, Flux measurements are reproducible, but the chromosphere modelling relies on unpublished code.

## Links

- Method: (cite: marti-vidal2014) (Simultaneous visibility fitting of point sources)
- Companion: (cite: liseau2015) (Earlier Band 3, 7, 9 alpha Cen ALMA observations)
- Companion: (cite: liseau2013) (Herschel detection of temperature minimum)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 32,
  "rate": 0.464
 },
 "evidence_ok": true
}
```
