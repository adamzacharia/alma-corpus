# The Peculiar Debris Disk of HD 111520 as Resolved by the Gemini Planet Imager

`2016ApJ...826..147D` | The Astrophysical Journal 2016 | first author: Draper, Zachary H. | arXiv: 1605.02771 | DOI: 10.3847/0004-637X/826/2/147

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: What is the near-IR scattered-light morphology, brightness asymmetry and polarization of the HD 111520 debris disk, with archival far-IR/mm photometry (incl. ALMA) used for SED context?  
  > "We therefore present GPI data which resolves the disk inside 1 ″ to better probe the structure of the disk." (1. INTRODUCTION)
- Target **HD 111520**: coordinates _not stated_; z/distance 108 ± 12 pc  
  > "The distance to the system was measured to be 108 ± 12 pc (van Leeuwen 2007), which we adopt throughout this study." (1. INTRODUCTION); distance from van Leeuwen 2007  
  > "The distance to the system was measured to be 108 ± 12 pc (van Leeuwen 2007), which we adopt throughout this study." (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2012.1.00688.S
- bands: Band 6 (1.3 mm), Cycle 1  
  > "ALMA Cycle 1 Band 6 (1.3 mm) continuum observations" (6. SPECTRAL ENERGY DISTRIBUTION)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public archival data, PI J. Carpenter  
  > "Public archival Herschel PACS (Poglitsch et al. 2010) observations (Obs. ID 1342227022-23; PI D. Padgett) and ALMA Cycle 1 Band 6 (1.3 mm) continuum" (6. SPECTRAL ENERGY DISTRIBUTION)
- Other facility **Gemini Planet Imager (Gemini South)**: H-band spectral and polarimetric imaging of the disk  
  > "A total of forty-one 60 s exposures were taken in H -band spectral mode (R ∼ 45)" (2. OBSERVATIONS AND DATA REDUCTION)
- Other facility **Herschel PACS**: 70 and 160 µm photometry  
  > "Herschel PACS 70 205 ± 4" (Table 1)
- Other facility **Spitzer, 2MASS, Tycho-2**: Archival SED photometry  
  > "Photometry included the optical Tycho-2 survey (Høg et al. 2000) and infrared surveys from 2MASS (Cutri et al. 2003) and Spitzer (Chen et al. 2014)." (6. SPECTRAL ENERGY DISTRIBUTION)
- External data: Spitzer photometry used in the SED  
  > "infrared surveys from 2MASS (Cutri et al. 2003) and Spitzer (Chen et al. 2014)" (6. SPECTRAL ENERGY DISTRIBUTION) [from Chen et al. 2014]

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

- SED scaling relations for disk radii from blackbody temperatures  
  > "we find implied disk radii of 11 and 54 AU, respectively, from simple scaling relations (Wyatt 2008)" (6. SPECTRAL ENERGY DISTRIBUTION) [from Wyatt 2008]

### Not stated but needed to reproduce (our reading)

- ALMA array configuration, beam, rms and imaging parameters
- CASA version or whether archive products were used
- aperture center and position for ALMA photometry
- Kurucz model details and fit initial values
- flux scale uncertainty

## Analysis recipe

1. **ALMA continuum aperture photometry**: Archived ALMA continuum maps measured with a 2.5 arcsec aperture; RMS from random apertures of same size  
  > "ALMA continuum maps were retrieved from the ALMA Science Archive and was measured with an 2 ″. 5 aperture." (6. SPECTRAL ENERGY DISTRIBUTION)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit two-component SED**: Kurucz stellar model plus two modified blackbodies, least-squares weighted by photometric uncertainties  
  > "The star subtracted flux densities were then least-squares fit with two modified blackbody SEDs using the photometric uncertainties as weights." (6. SPECTRAL ENERGY DISTRIBUTION)
   - parameter: Kurucz Teff 6750 K; knee 173 µm, beta 0.8  
  > "The modified slope parameters include a knee at 173 µm with a β index of 0.8" (6. SPECTRAL ENERGY DISTRIBUTION)
   - assumption: Blackbody dust temperatures, stellar luminosity 2.9 Lsun for radii  
  > "Given a stellar luminosity 2.9 L ⊙ and assuming blackbody temperatures for the dust" (6. SPECTRAL ENERGY DISTRIBUTION)
   - fitting: Least squares; uncertainties from diagonal of covariance matrix  
  > "Uncertainties were determined using the diagonal of the covariance matrix" (6. SPECTRAL ENERGY DISTRIBUTION)
   - validation: _not stated_

## Software

- **pyKLIP** : PSF subtraction of GPI data  
  > "The spectral mode cubes were combined with pyKLIP (Wang et al. 2015) using ADI-only mode" (3. PSF SUBTRACTION)
- **GPI Data Reduction Pipeline** : GPI reduction  
  > "The data were reduced using primitives in the GPI Data Reduction Pipeline" (2. OBSERVATIONS AND DATA REDUCTION)
- **HIPE** : Herschel PACS reduction  
  > "Herschel PACS data was reduced with standard HIPE pipeline (Ott 2010)" (6. SPECTRAL ENERGY DISTRIBUTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 6 (1252 µm) flux | 1.17 | 0.08 | mJy | 1 | ALMA Band 6 1252 1 . 17 ± 0 . 08 |
| Warm and cold dust temperatures | 111 and 49 | 2 K each | K | 2 | The temperatures of the warm and cold components in the SED are measured to be 111 ± 2 K and 49 ± 2 K, respectively. |
| Second ALMA source flux density | 0.5 | not stated | mJy | 1 | A second
point source is detected in the ALMA map at a PA of
329 _[◦]_, 11 _[′′]_ _._ 9 away from the peak emission of HD 111520
with a flux density of 0.5 mJy. |

## Qualitative findings

- ALMA 1.3 mm emission is a point source; a second source lies 11.9 arcsec away  
  > "At PACS 70 µm and ALMA 1252 µm the emission is seen as a point source" (Figure 8 caption)

## Claim tuples

- H: What is the disk asymmetry and its cause? | E: GPI imaging with three PSF subtraction methods | R: 2:1 NW/SE brightness asymmetry; polarization fraction similar on both sides | F: Azimuthal dust density variation likely causes the asymmetry | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties do not include systematic biases such as non-blackbody grains; knee and beta uncertain  
  > "given the lack of photometric coverage near the knee, both parameters remain uncertain" (6. SPECTRAL ENERGY DISTRIBUTION)
- Caveat (inferred, ours): ALMA used only as one photometric point from an unresolved source
- Caveat (inferred, ours): Little ALMA processing detail given

## Reproducibility

- Data public (paper): Public archival data  
  > "Public archival Herschel PACS (Poglitsch et al. 2010) observations" (6. SPECTRAL ENERGY DISTRIBUTION)
- Products in archive: _not stated_
- Missing: ALMA imaging details
- Missing: SED fitting code
- Data volume (inferred): ~1-5 GB for the ALMA continuum
- Score (inferred): 3/5, The ALMA part is a single aperture flux; the GPI data are not ALMA, and the recipe lacks detail.
- Rediscovery candidate: no, ALMA role is minor and the recipe is incomplete.

## Links

- Companion: Padgett & Stapelfeldt 2015 (HST discovery of the disk)
- Related: GPI Exoplanet Survey

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 21,
  "rate": 0.344
 },
 "evidence_ok": true
}
```
