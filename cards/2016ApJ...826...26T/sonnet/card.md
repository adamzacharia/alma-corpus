# Revealing a Detailed Mass Distribution of a High-density Core MC27/L1521F in Taurus with ALMA

`2016ApJ...826...26T` | The Astrophysical Journal 2016 | first author: Tokuda, Kazuki | arXiv: 1604.04954 | DOI: 10.3847/0004-637X/826/1/26

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the detailed dust/gas mass and column density distribution of the dense core MC27/L1521F from ~100 AU to ~10,000 AU, obtained by combining ALMA 12 m and 7 m data with single-dish data?  
  > "The detailed column density distribution on size scales from a few tens AU to ∼10,000 AU scale are revealed by combining the ALMA (12 m array + 7 m array) data" (abstract)
- Target **MC27/L1521F**: coordinates 4h28m39.00s, +26d51m35.0s (J2000)  
  > "at the center position of (α J2000.0, δ J2000.0 ) = (4 [h] 28 [m] 39 [s] .00, +26 [◦] 51 [′] 35 [′′] .0)" (2. Observations); "where F ν is the integrated flux of the continuum emission at frequency ν and d is the" (3.1); z/distance 140 pc  
  > "at the center position of (α J2000.0, δ J2000.0 ) = (4 [h] 28 [m] 39 [s] .00, +26 [◦] 51 [′] 35 [′′] .0)" (2. Observations); "where F ν is the integrated flux of the continuum emission at frequency ν and d is the" (3.1); distance from Elias 1978 (Taurus distance)  
  > "at the center position of (α J2000.0, δ J2000.0 ) = (4 [h] 28 [m] 39 [s] .00, +26 [◦] 51 [′] 35 [′′] .0)" (2. Observations); "where F ν is the integrated flux of the continuum emission at frequency ν and d is the" (3.1)

## Data provenance

- ALMA projects: 2011.0.00611.S, 2012.1.00239.S
- bands: Band 6 (1.2 mm) and Band 7 (0.87 mm), Cycle 1  
  > "We carried out ALMA Cycle 1 Band 6 (1.2 mm) and Band 7 (0.87 mm) continuum" (2. Observations)
- frequencies and spectral setup: 4 spectral windows per band, 1875 MHz each, 3840 channels; 7.5 GHz total per band  
  > "The total bandwidth is thus 7.5 GHz in each Band." (2. Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array and 7 m array (ACA)  
  > "with the 12 m array and the 7 m array (ACA)" (2. Observations)
- configurations: _not stated_
- baselines: 12 m uv: 10.9–239 kλ (B6), 16.2–699 kλ (B7); 7 m: 8.1–27.7 kλ (B6), 8.9–43.9 kλ (B7)  
  > "The 7 m array data of the Band 6 and the band 7 cover the baseline ranges of 8.1–27.7 kλ and 8.9–43.9 kλ, respectively." (2. Observations)
- angular resolution: B6 12 m ~1.3x0.8 arcsec; B7 12 m ~0.74x0.32 arcsec; 7 m ~6.6x5.5 (B6), 5.1x4.2 arcsec (B7)  
  > "Synthesized beam size ∼1 [′′] . 3 × 0 [′′] . 8 ∼6 [′′] . 6 × 5 [′′] . 5 ∼0 [′′] . 74 × 0 [′′] . 32 ∼5 [′′] . 1 × 4 [′′] . 2" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms ~0.1 mJy/beam (12 m, both bands), 1.2 (B6 7 m), 2.4 (B7 7 m) mJy/beam  
  > "Sensitivity of continuum observation (r.m.s.) ∼0.1 mJy beam [−][1] ∼1.2 mJy beam [−][1] ∼0.1 mJy beam [−][1] ∼2.4 mJy beam [−][1]" (Table 1)
- time on source: _not stated_
- observing dates: 2013 October to 2015 June  
  > "The observations have been carried out between 2013 October and 2015 June." (2. Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: H13CO+ J=4-3 (not stated)
- Line: C17O J=3-2 (not stated)
- Other facility **IRAM 30 m / MAMBO-2**: 1.2 mm single-dish continuum map for combining with ALMA  
  > "as part of project 109–02 (P.I.: Ph. Andr´e), using the 117-channel MAMBO-2" (2. Observations)
- Other facility **JCMT/SCUBA**: 0.87 mm single-dish data from literature  
  > "We used the JCMT/SCUBA data obtained by Shinnaga et al. (2004) and" (3.2)
- External data: JCMT/SCUBA 0.87 mm single-dish maps  
  > "We used the JCMT/SCUBA data obtained by Shinnaga et al. (2004) and" (3.2) [from Shinnaga et al. 2004; Kirk et al. 2005]
- External data: Dust opacity kappa(231 GHz)=1.0e-2 cm2/g  
  > "is the emissivity of the dust" (3.1) [from Ossenkopf & Henning 1994; Kauffmann et al. 2008]
- External data: Dust temperature 10 K consistent with Herschel SED  
  > "We assumed T d = 10 K, which is consistent" (3.1) [from André et al. 2010; Palmeirim 2014 private communication]

## Processing

### Calibration

- pipeline or manual: Data reduced with CASA; version not given  
  > "The data were reduced using the Common Astronomy Software Application package [2] and the visibility imaged." (2. Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Uranus and quasar J0510+1800; Butler-JPL-Horizons 2012 model  
  > "we used the" (2. Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for both bands  
  > "We used the natural weighting for both the Band 6 and the Band 7 data." (2. Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m and 7 m cleaned separately, then combined with single-dish map by feathering in Fourier space  
  > "we cleaned the 7 m and 12 m data sets individually and combined the cleaned maps and the single-dish map in Fourier space." (3.2)
- smoothing: _not stated_
- final beam: 1.3x0.8 arcsec for combined 1.2 mm image  
  > "The synthesized beam size is 1 [′′] .3 ×" (3.2)
- final rms: _not stated_

### Inherited from earlier work

- Feathering following CASA instructions from ALMA  
  > "by using the feathering technique in an accordance with the CASA instruction obtained by ALMA" (3.2) [from CASA feathering guide]
- MAMBO-2 signal-loss simulation similar to Motte & André 2001 Appendix  
  > "A simulation, similar to that described in the Appendix of Motte & Andr´e (2001)," (3.2) [from Motte & André 2001]

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean parameters (cell, image size, masks, niter, thresholds)
- feathering parameters (SD scaling, uvrange, beam of single dish)
- how MAMBO-2 map was reduced and how its 14 arcsec resolution relates to the 11 arcsec beam
- details of the MAMBO-2 signal-loss simulation
- radial profile annuli and binning
- phase/bandpass calibrator assignment per execution block
- line-free channels and continuum subtraction method

## Analysis recipe

1. **Image ALMA 12 m and 7 m data**: Calibrate and image with CASA, natural weighting  
  > "We used the natural weighting for both the Band 6 and the Band 7 data." (2. Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive masses and column densities of compact sources**: Optically thin dust emission, uniform T_d; Eqs. 1-3  
  > "with the assumption of optically thin emission and uniform dust temperature." (3.1)
   - parameter: T_d = 10 K; beta = 1.9; kappa(0.87mm)=2.1e-2 cm2/g; d = 140 pc  
  > "β was assumed to be 1.9" (3.1)
   - assumption: Optically thin, uniform dust temperature  
  > "with the assumption of optically thin emission and uniform dust temperature." (3.1)
   - fitting: _not stated_
   - validation: Compared with Cycle 0 1.1 mm results (~10-20% for MMS-2)  
  > "within ∼10–20% for MMS-2." (3.1)
3. **Combine interferometer and single-dish data**: Feather 12 m, 7 m and IRAM 30 m (1.2 mm) or JCMT/SCUBA (0.87 mm) images  
  > "we combined the three different datasets by using the feathering technique" (3.2)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Mean radial column density profile and slopes**: Azimuthally averaged profile around MMS-2; power-law slopes; MAMBO-2 signal-loss simulation  
  > "Figure 5 shows the mean radial profile of the H 2 column densities centered at MMS-2" (3.2)
   - parameter: T_d = 10 K, kappa = 1.2e-2 cm2/g for column density map  
  > "κ ν = 1.2 × 10 [−][2] cm [2] g [−][1]" (3.2)
   - assumption: Uniform T_d, spherical symmetry, optically thin  
  > "if we assume a uniform dust temperature, spherically symmetric geometry, and optically thin dust" (3.2)
   - fitting: _not stated_
   - validation: Change of center to MMS-1 changes profile little  
  > "Even if we change the center to MMS-1, the change" (3.2)
5. **Density diagnostics from line ratios**: Non-LTE RADEX on H13CO+ 4-3/3-2 ratio, T_kin=10 K  
  > "(RADEX; van der Tak et al. 2007) under the assumption of the kinematic temperature of" (3.1)
   - software: RADEX
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction, imaging, feathering  
  > "The data were reduced using the Common Astronomy Software Application package [2] and the visibility imaged." (2. Observations)
- **RADEX** : non-LTE density estimate from H13CO+ ratio  
  > "(RADEX; van der Tak et al. 2007)" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MMS-2 integrated flux (0.87 mm) | 11.8 | not stated | mJy | 2 | MMS-2 4 [h] 28 [m] 38 [s] .89 +26 [◦] 51 [′] 33 [′′] . 9 11.8 360 1.1 1.3 × 10 [23] 3.9 × 10 [−][3] |
| MMS-2 total mass | 3.9e-3 | not stated | Msun | 2 | 3.9 × 10 [−][3] |
| MMS-3 total mass | 1.8e-4 | not stated | Msun | 2 | 1.8 × 10 [−][4] |
| Gas mass within r<3000 AU | 0.49 | not stated | Msun | 4 | M gas = 0.49 M ⊙ |
| Inner column density slope (r<3000 AU) | -0.4 | not stated | dimensionless | 4 | N H 2 ∼r [−][0][.][4], clearly flatter than |
| Outer intrinsic column density slope | -1.0 | 0.2 | dimensionless | 4 | ∼ r [−][1][.][0][±][0][.][2] beyond ∼3000 AU |
| Flux of MMS-1 deconvolved size | 0.28x0.13 arcsec (40x18 AU) | ±0.1, ±0.06 arcsec | arcsec | 2 | (40±14 AU) × (18±8 |

## Qualitative findings

- MMS-1 is unresolved and lacks associated line emission; MMS-2 resolves into two peaks at 0.87 mm  
  > "The 0.87 mm continuum observation revealed that MMS-2 could be further resolved" (3.1)

## Claim tuples

- H: Does the radial column density flatten inside ~3000 AU? | E: Combine 12 m, 7 m and IRAM 30 m 1.2 mm data and make radial profile | R: Inner slope ~r^-0.4, outer ~r^-1.0 after correcting for MAMBO-2 loss | F: Inner region is flatter, coincident with complex velocity structure | **supported**
- H: Are MMS-1 and MMS-2 resolved? | E: 0.87 mm 12 m array imaging | R: MMS-1 unresolved, MMS-2 two peaks | F: MMS-2 may be fragmenting | **partially**
- H: Do SMA CO(2-1) components represent outflow? | E: Compare ALMA CO(3-2) with Takahashi et al. 2013 | R: Components match dense filaments/cores | F: They are not outflowing gas | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Combining single-dish and ACA data fills the spatial frequency gap  
  > "ALMA has the capability to" (1. Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Assumed beta and T_d differ from Herschel FTS values; MAMBO-2 loses signal at large radii; MMS-3 only 3 sigma  
  > "which is different from" (3.1)
- Caveat (inferred, ours): Uniform T_d=10 K likely underestimates temperature in the inner region
- Caveat (inferred, ours): Slope error not given for inner profile
- Caveat (inferred, ours): Feathering details unspecified

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; IRAM data from project 109-02  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00611.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: IRAM MAMBO-2 map not obviously public
- Missing: imaging and feathering parameters
- Missing: Herschel temperature from private communication
- Data volume (inferred): ~100-300 GB raw for Cycle 1 12 m + ACA, two bands
- Score (inferred): 4/5, ALMA data identified, but imaging parameters and single-dish data are not specified.
- Rediscovery candidate: no, Key single-dish data and feathering details are unavailable or unstated.

## Links

- Method: Motte & André 2001 (MAMBO-2 signal-loss simulation)
- Companion: Tokuda et al. 2014 (Cycle 0 ALMA observations of the same core)
- Related: Herschel Gould Belt survey

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 40,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
