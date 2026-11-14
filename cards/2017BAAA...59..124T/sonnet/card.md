# The role of major mergers in (obscured) black hole growth and galaxy evolution

`2017BAAA...59..124T` | Boletin de la Asociacion Argentina de Astronomia La Plata Argentina 2017 | first author: Treister, E. | arXiv: - | DOI: -

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: How do major mergers connect to SMBH growth and galaxy evolution in the dual AGN Mrk 463, using IFU and ALMA data?  
  > "We present here the first results from our MODA program, aim to study the properties of the gas in all its phases in nearby major galaxy mergers undergoing simultaneous SMBH growth episodes." (4. Conclusions)
- Target **Mrk 463**: coordinates _not stated_; z/distance z=0.0504, d~210 Mpc  
  > "Mrk 463 is a nearby, _z_ =0.0504 (Falco et al., 1999) or _d≃_ 210 Mpc, ultraluminous Infrared Galaxy" (1. Introduction); distance from Falco et al., 1999 (redshift)  
  > "Mrk 463 is a nearby, _z_ =0.0504 (Falco et al., 1999) or _d≃_ 210 Mpc, ultraluminous Infrared Galaxy" (1. Introduction)

## Data provenance

- ALMA projects: 2013.1.00525.S
- bands: Band 6, ~220 GHz (1.3 mm continuum)  
  > "The observations were done in band 6, covering both the [12] CO(21) molecular transition and the mm continuum at _∼_ 220" (2.2. ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 35 antennae (first observation), 39 antennae (second)  
  > "For the second observation, 39 antennae were used and similar baselines." (2.2. ALMA)
- configurations: _not stated_
- baselines: 41 m to 4.5 km  
  > "minimum and maximum baselines of 41m and 4.5 kms kms" (2.2. ALMA)
- angular resolution: 0.15 arcsec  
  > "which resulted on a spatial resolution of 0.15 _[′′]_ ." (2.2. ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: August 16, 2015 and September 16, 2015  
  > "on August 16, 2015 and September 16, 2015" (2.2. ALMA)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT/MUSE**: Optical IFU maps, [OIII] velocity field  
  > "Mrk 463 was observed by the VLT/MUSE as part of program 095.B-0482" (2.1. VLT Optical and Near-IR IFU)
- Other facility **VLT/SINFONI**: K-band near-IR IFU, Paα map  
  > "The observations were carried out using the K-band grating, centered at _∼_ 2.2 _µ_ m." (2.1. VLT Optical and Near-IR IFU)
- Other facility **Chandra**: X-ray luminosities and column densities of nuclei (from literature)  
  > "It was a classified as a dual AGN thanks to the Chandra X-ray observations reported by Bianchi et al." (1. Introduction)
- External data: Chandra X-ray luminosities and NH of the two nuclei  
  > "Both nuclei are heavily obscured, at _N_ _H_ =7.1 _×_ 10 [23] cm _[−]_ [2] and" (1. Introduction) [from Bianchi et al. (2008)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Preliminary analysis based on NRAO ARC processing delivered to PI  
  > "The preliminary analysis reported here is based only on the processing done by the NRAO ARC and delivered to the PI." (2.2. ALMA)
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

### Not stated but needed to reproduce (our reading)

- CASA version
- imaging parameters (weighting, cell, masking)
- continuum subtraction and line-free channels
- spectral setup
- CO(2-1) moment map construction
- time on source
- beam and rms

## Analysis recipe


## Software

- **CASA** : Further analysis of ALMA data  
  > "Further analysis was carried out using Common Astronomy Software" (2.2. ALMA)
- **ESO MUSE pipeline** 1.6.2: MUSE data reduction in ESO Reflex  
  > "Data reduction was carried out using the ESO MUSE pipeline version 1.6.2" (2.1. VLT Optical and Near-IR IFU)
- **ESO SINFONI pipeline** 2.9.0: SINFONI data reduction  
  > "the standard ESO SINFONI pipeline version 2.9.0" (2.1. VLT Optical and Near-IR IFU)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity gradient on east nucleus ([OIII]) | ~400 | not stated | km/s | 0 | a velocity gradient of _∼_ 400 km/s can be observed on the east nucleus |
| Outflow velocity of northern ionized region | ~650 | not stated | km/s | 0 | moving at a velocity of _∼_ 650 km/s and thus clearly outflowing |

## Qualitative findings

- CO(2-1) and continuum are associated with the east nucleus; none significant at the west nucleus, with CO found ~0.5-1 kpc west and between nuclei  
  > "no significant emission can be observed in the west nucleus." (3.1. Morphology)

## Claim tuples

- H: Does the extended [OIII] cloud south of the east galaxy arise from AGN ionization? | E: MUSE line ratios and ionizing flux estimate | R: cloud consistent with AGN ionization; AGN luminosity roughly constant to a factor ~10 over ~10^4 yr | F: Mrk 463 hosts a voorwerp-like AGN-ionized cloud | **supported**
- H: Is gas transferring from the east to the west component? | E: ALMA CO(2-1) mapping | R: CO between the nuclei and west of the west nucleus | F: Possible ongoing mass transfer | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: A disk model fails to fit the east nucleus velocity profile, so a biconical ionization cone is preferred  
  > "A disk model fails to fit to this observed velocity profile." (3.2. Kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Preliminary analysis; cycle 2 program unfinished  
  > "obtained as part of our unfinished cycle 2 program" (Figure 1)
- Caveat (inferred, ours): No quantitative ALMA measurements (fluxes, masses) given
- Caveat (inferred, ours): Mass transfer interpretation is speculative
- Caveat (inferred, ours): Qualitative ALMA analysis only

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA processing details
- Missing: CO moment maps and fluxes
- Missing: MUSE line-ratio analysis details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 1/5, Conference proceeding with qualitative ALMA use and almost no processing detail.
- Rediscovery candidate: no, No numeric ALMA results or recipe.

## Links

- Related: MODA (Multiwavelength Observations of Dual AGN)

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 53,
  "stated": 19,
  "rate": 0.358
 },
 "evidence_ok": true
}
```
