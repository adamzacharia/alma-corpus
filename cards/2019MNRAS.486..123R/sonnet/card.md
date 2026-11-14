# MUSE observations of a changing-look AGN - I. The reappearance of the broad emission lines

`2019MNRAS.486..123R` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Raimundo, S. I. | arXiv: 1903.08696 | DOI: 10.1093/mnras/stz852

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the host galaxy gas and stellar properties and nuclear dynamics of the changing-look AGN Mrk 590, and have its optical broad lines reappeared?  
  > "In this work we study in detail and for the first time the host galaxy of Mrk 590, a changing-look AGN, using optical and near-infrared integral field spectroscopy." (Introduction)
- Target **Mrk 590**: coordinates _not stated_; z/distance z = 0.026385 (493 pc/arcsec)  
  > "Mrk 590 is an Sa galaxy at z $=$ 0.026385 (493 pc/$''$)" (Mrk 590); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00534.S, 2015.1.00770.S
- bands: _not stated_
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
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Line: CO 1-0 (not stated)
- Other facility **VLT/MUSE**: Optical IFU cube, 4750-9350 A, 2h27min on source  
  > "for a total on-source exposure time of 2h27min" (2.1 MUSE observations)
- Other facility **VLT/SINFONI**: Archival K-band IFU data (programme 080.B-0239), H2 2.12 um  
  > "We have processed and analysed archival SINFONI/VLT observations of Mrk 590." (2.2 SINFONI observations)
- External data: ALMA CO(3-2) flux maps of Mrk 590  
  > "The CO(3-2) flux maps were presented by (cite: koay16a)" (4.5 Molecular gas distribution) [from Koay et al. (cite: koay16a)]
- External data: ALMA CO(1-0) maps  
  > "The detailed analysis of the CO(1-0) maps will be presented by Koay et al. (in prep)." (4.5 Molecular gas distribution) [from Koay et al. in prep]

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

- ALMA CO(3-2) and CO(1-0) maps and sub-mm continuum taken from other works; no ALMA processing described  
  > "The CO(3-2) flux maps were presented by (cite: koay16a)" (4.5 Molecular gas distribution) [from (cite: koay16a); Koay et al. in prep]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging, beam and rms of the CO maps
- Contour levels used in the ALMA overlays
- Observing setup of the ALMA data

## Analysis recipe

1. **Overlay ALMA CO and continuum contours on the Halpha map**: Contour maps of CO(1-0), CO(3-2) and sub-mm continuum overlaid on the Halpha flux map for comparison  
  > "we show contour maps of CO(1-0), CO(3-2) and sub-mm continuum emission overlaid on the H$\alpha$ flux map" (4.5 Molecular gas distribution)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ESOREX** 3.12.3: MUSE and SINFONI pipeline reduction  
  > "The data were processed using the command line tool ESOREX (version 3.12.3)" (2.1 MUSE observations)
- **pPXF** : Stellar kinematics  
  > "we use the Penalized Pixel-Fitting (pPXF) method" (3.1.2 Stellar kinematics)
- **GANDALF** : Emission line fitting  
  > "we use GANDALF, a Gas AND Absorption Line Fitting algorithm" (3.1.3 Gas dynamics)
- **STARLIGHT** : Stellar population synthesis  
  > "We use the stellar population synthesis code STARLIGHT" (4.6 Stellar population)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar kinematic position angle | 118.0 | 1.2 | degrees | 0 | PA = 118.0$\pm 1.2$ degrees |
| [O III] broad component mean velocity | -400 | not stated | km/s | 0 | mean velocity of V$_{\rm [O III]\,broad}$ $\sim$ -400 km s$^{-1}$ |

## Qualitative findings

- CO(1-0) traces the inner edge of the Halpha ring and is not detected in the nucleus, while H2 2.12 um is detected there  
  > "There is no significant detection of CO(1-0) in the nucleus or the nuclear spiral." (4.5 Molecular gas distribution)

## Claim tuples

- H: Do the optical broad lines of Mrk 590 reappear? | E: MUSE spectra in 2017 | R: Broad Halpha and Hbeta present, continuum ~10x below 1990s | F: Broad lines reappeared without large continuum rise | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA data are only used from other papers for comparison; no independent analysis

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data processing not described
- Data volume (inferred): not applicable for ALMA part
- Score (inferred): 2/5, ALMA role is minor and processing is not described.
- Rediscovery candidate: no, ALMA part not reproducible from this paper.

## Links

- Companion: Koay et al. (cite: koay16a) (Presents ALMA CO(3-2) maps)

## Checks

```json
{
 "quotes": 21,
 "quotes_ok": 21,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 56,
  "stated": 13,
  "rate": 0.232
 },
 "evidence_ok": true
}
```
