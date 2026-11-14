# Radio emission and mass loss rate limits of four young solar-type stars

`2017A&A...599A.127F` | Astronomy and Astrophysics 2017 | first author: Fichtinger, Bibiana | arXiv: 1702.08393 | DOI: 10.1051/0004-6361/201629886

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: stellar_physics, solar_system
- Question: Can radio free-free emission of young solar-type stars reveal or limit their wind mass loss, and was the young Sun massive enough to solve the faint young Sun paradox?  
  > "Our aim is to re-examine the faint young Sun paradox by assuming that the young Sun was more massive in its past" (abstract)
- Target **chi1 Ori**: coordinates 05h 54m 22.78s, +20d 16' 33.58" (observed)  
  > "A G1V star with a rotation period of about 5.2 days (cite: Messina2001), a distance of 8.7 pc and an age of  300 Myr (cite: Ribas2005)." (2.1 Target sample); z/distance 8.7 pc  
  > "A G1V star with a rotation period of about 5.2 days (cite: Messina2001), a distance of 8.7 pc and an age of  300 Myr (cite: Ribas2005)." (2.1 Target sample); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.01234.S
- bands: Band 3, 100 GHz (84-116 GHz)  
  > "was used to observe in band 3 (with a bandwidth of 84-116 GHz) at 100 GHz in December 2013 within Cycle 1." (2.2 VLA and ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.23" x 2.00" clean beam  
  > "| 3 (ALMA) | 2.5 | 1 | Dec 2013 | 8 | 2.$''$ 23 $\times$ 2.$''$ 00 | J0604+2429, | Ganymede |" (Table 1 (observations))
- max recoverable scale: _not stated_
- sensitivity: rms 8 uJy  
  > "| 3 (ALMA) | 2.5 | 1 | Dec 2013 | 8 | 2.$''$ 23 $\times$ 2.$''$ 00 | J0604+2429, | Ganymede |" (Table 1 (observations))
- time on source: 2.5 h  
  > "| 3 (ALMA) | 2.5 | 1 | Dec 2013 | 8 | 2.$''$ 23 $\times$ 2.$''$ 00 | J0604+2429, | Ganymede |" (Table 1 (observations))
- observing dates: December 2013 (Cycle 1)  
  > "at 100 GHz in December 2013 within Cycle 1." (2.2 VLA and ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLA**: C-band (4-8 GHz) and Ku-band (12-18 GHz) continuum of all four stars  
  > "We use C-band (4 - 8 GHz, 6 cm) and Ku-band (12 - 18 GHz, 2 cm) receivers." (2.2 VLA and ALMA)
- External data: Stellar properties (distance, Teff, mass, radius, Lx, Prot, age) of targets  
  > "(cite: Ribas2005) adopted an age of about 100 Myr for this near-ZAMS star." (2.1 Target sample) [from (cite: Ribas2005)]

## Processing

### Calibration

- pipeline or manual: NRAO-provided scripts / ALMA pipeline, with extra flagging and a second pipeline run  
  > "For our data analysis, we used these pipelines, but some extra flagging and a second run through the pipeline calibration were necessary." (2.2 VLA and ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (ALMA); phase calibrators J0604+2429, J0538-4405  
  > "| 3 (ALMA) | 2.5 | 1 | Dec 2013 | 8 | 2.$''$ 23 $\times$ 2.$''$ 00 | J0604+2429, | Ganymede |" (Table 1 (observations))
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

- ALMA CASA/pipeline version
- ALMA imaging parameters (weighting, cell, deconvolver, masking)
- how the 103 uJy flux and uncertainty were measured
- continuum channel selection and flux scale uncertainty
- project code discrepancy: text prints 2011.0.01234.S, archive links 2012.1.00268.S

## Analysis recipe

1. **measure ALMA 100 GHz flux of chi1 Ori**: Stokes I flux density measured on the calibrated image; no Stokes V available for Cycle 1  
  > "The flux density at 100 GHz measured with ALMA is 103 $\pm$ 4.9 $\rm \mu Jy$ in Stokes I." (3.2.3 chi1 Ori)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **estimate chromospheric contribution**: blackbody flux of whole stellar disk at 100 GHz with T = 10000 K  
  > "At 100 GHz we expect a lower temperature of typically 10 000 K, although it can be even lower." (3.3 Chromospheric emission)
   - assumption: entire stellar surface covered by optically thick chromosphere  
  > "Furthermore, we assume that the entire surface of the star is covered by chromospheric emission." (3.3 Chromospheric emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : inspecting, flagging, calibrating and imaging data  
  > "has been used for inspecting, editing (including flagging), calibrating, and imaging the data sets." (2.2 VLA and ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| chi1 Ori ALMA 100 GHz Stokes I flux density | 103 | 4.9 | uJy | 1 | The flux density at 100 GHz measured with ALMA is 103 $\pm$ 4.9 $\rm \mu Jy$ in Stokes I. |
| predicted chromospheric flux of chi1 Ori at 100 GHz | 65 | not stated | uJy | 2 | For $\rm \chi^{1} \ Ori$ at the distance of *d* = 8.7 pc the flux density is 65 $\mu$Jy for ALMA (100 GHz). |

## Qualitative findings

- The radio emission of chi1 Ori likely comes from its M-dwarf companion and is non-thermal/flaring  
  > "The emission of $\rm \chi^{1}\  Ori$ does not come from the main target itself, but from its M-dwarf companion." (abstract)

## Claim tuples

- H: Enhanced early wind mass loss could solve the faint young Sun paradox | E: VLA/ALMA radio limits converted to mass loss rate limits and integrated over time | R: Initial solar mass at most 1.02 Msun (spherical), 1.004 (conical) | F: Increased wind mass loss cannot solve the paradox | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No Stokes V available for ALMA Cycle 1 data  
  > "For ALMA, no Stokes V measurements were available for Cycle 1 data sets." (3.2.3 chi1 Ori)
- Caveat (inferred, ours): ALMA is a single minor detection; chromospheric vs. companion origin not separated
- Caveat (inferred, ours): mass loss limits depend on assumed T and v

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging settings
- Missing: software versions
- Data volume (inferred): ~10-50 GB
- Score (inferred): 2/5, ALMA part is a single flux with few processing details.
- Rediscovery candidate: no, ALMA recipe incomplete and minor.

## Links

- Related: The Sun in Time programme

## Checks

```json
{
 "quotes": 23,
 "quotes_ok": 23,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.01234.S"
 ],
 "obscore_codes_not_in_card": [
  "2012.1.00268.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 55,
  "stated": 18,
  "rate": 0.327
 },
 "evidence_ok": true
}
```
