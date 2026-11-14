# Circumstellar and Circumbinary Discs in Multiple Stellar Systems

`2025Symm...17..344C` | Symmetry 2025 | first author: Cuello, Nicolás | arXiv: 2501.19249 | DOI: 10.3390/sym17030344

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation, exoplanets
- Question: How do multiple stellar systems shape protoplanetary disc structure, dynamics and evolution, and what does this imply for planet formation (review of circumstellar and circumbinary discs)  
  > "focusing on their distinct formation pathways, dynamical interactions, and implications for planet formation" (Introduction)
- Target **HT Lup**: coordinates _not stated_; z/distance 154 +/- 2 pc  
  > "Located at a distance of $154\pm2$ pc" (3.4 CSDs of interest); "the HT Lup system comprises three stars, all detected in millimetre wavelengths through both continuum and CO emission." (3.4 CSDs of interest); distance from Gaia (cite: Gaia+2016)  
  > "Located at a distance of $154\pm2$ pc" (3.4 CSDs of interest); "the HT Lup system comprises three stars, all detected in millimetre wavelengths through both continuum and CO emission." (3.4 CSDs of interest)
- Target **S CrA**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **UY Aur**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **T Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 100453**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **UZ Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **GG Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **GW Ori**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 142527**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 98800**: coordinates _not stated_; z/distance 45 pc  
  > "Located $45$ pc away in the TW Hya association" (4.4 CBDs of interest); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01678.S, 2019.1.00703.S, 2016.1.00484.L, 2016.1.01164.S, 2019.1.01792.S, 2015.1.01353.S, 2018.1.00532.S, 2018.1.00813.S, 2017.1.00350.S
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
- pi or archival as stated: ALMA "quality assurance" products downloaded from the ALMA archive  
  > "The ALMA images displayed in the galleries below are "quality assurance" products that were downloaded from the ALMA archive" (3.4 CSDs of interest)
- Line: CO not stated (not stated)
- Other facility **VLT/SPHERE (ESO archive)**: Polarimetric scattered-light images shown alongside ALMA images in the galleries  
  > "The SPHERE polarimetric data were downloaded from the ESO archive" (3.4 CSDs of interest); "The images shown are in polarized intensity with the contribution of the central star removed" (3.4 CSDs of interest)
- External data: Distance of HT Lup, 154 +/- 2 pc  
  > "Located at a distance of $154\pm2$ pc" (3.4 CSDs of interest) [from (cite: Gaia+2016)]
- External data: Table of systems with coordinates, number of stars and disc types compiled from literature references  
  > "We list these systems in Table" (3.4 CSDs of interest) [from references listed per row of the systems table, e.g. (cite: Ghez+1997; Andrews+2018)]
- Simulation/model as data: Hydrodynamical model of a circumstellar disc with an inner gas giant planet at about 20 au, shown in Figure 5 (HD 100453)  
  > "illustrates how hydrodynamical models of circumstellar discs replicate observed features such as spirals and precession while testing new dynamical scenarios" (6 Open questions in the field)
- Simulation/model as data: Hydrodynamical simulations of accretion in binary versus triple systems, shown in Figure 6 (Ceppi+2022)  
  > "recent hydrodynamical simulations demonstrate how stellar multiplicity affects accretion by comparing a pure binary case against two similar configurations of triple systems" (6 Open questions in the field)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA quality assurance products used as downloaded  
  > "used as they are" (3.4 CSDs of interest)
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

- Handling of polarimetric observations of discs in multiple systems, where nearby stars contaminate the signal, is referred to Weber+2023 for details  
  > "Polarimetric observations of discs in multiple stellar systems are challenging due to the contamination of the signal by nearby stars" (Footnote 6) [from (cite: Weber+2023)]

### Not stated but needed to reproduce (our reading)

- Which ALMA project code corresponds to which system or gallery panel
- Which ALMA QA product (band, array, line or continuum, beam, rms) is shown in each gallery panel
- Which SPHERE programme/observations and IRDAP settings were used for each system
- Names in the systems table were lost, so row-to-system mapping of coordinates is not given in the text

## Analysis recipe

1. **retrieve ALMA images for gallery**: ALMA quality assurance products downloaded from the ALMA archive and used as they are  
  > "quality assurance" products that were downloaded from the ALMA archive" (3.4 CSDs of interest)
   - fitting: _not stated_
   - validation: _not stated_
2. **process SPHERE polarimetric images**: SPHERE polarimetric data downloaded from ESO archive and processed with IRDAP; shown in polarized intensity with central star contribution removed  
  > "processed using the IRDAP open-access pipeline" (3.4 CSDs of interest); "The images shown are in polarized intensity with the contribution of the central star removed" (3.4 CSDs of interest)
   - software: IRDAP
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **IRDAP** : Processing of SPHERE polarimetric data  
  > "processed using the IRDAP open-access pipeline" (3.4 CSDs of interest)

## Numeric results


## Qualitative findings

- Circumstellar discs in multiple systems are typically smaller than those around isolated stars (tidal truncation)  
  > "circumstellar discs in these systems are typically smaller than those around isolated stars" (3.1 Tidal truncation of CSDs)
- Larger samples are needed to assess the influence of stellar multiplicity on dust growth  
  > "Overall, a larger sample is required to be able to assess the influence of stellar multiplicity on dust growth." (6 Open questions in the field)

## Claim tuples

- H: Does stellar multiplicity change protoplanetary disc structure and planet formation? | E: Literature review supplemented by gallery of ALMA and SPHERE archive images of multiple systems | R: Review concludes multiple stars alter disc dynamics and morphology | F: Stellar multiplicity shapes disc structures and planet formation | **supported**
- H: Are circumstellar discs in multiple systems smaller than around single stars? | E: Review of tidal truncation theory and observations | R: Discs in multiples are typically smaller | F: Tidal truncation limits circumstellar disc size | **supported**
- H: Do misaligned and polar circumbinary discs yield unconventional planetary orbits? | E: Review of simulations and observations | R: Simulations and observations suggest such planets could exist | F: Misaligned and polar discs produce unique planetary architectures | **partially**
- H: Does stellar multiplicity affect dust growth? | E: Review of SED and resolved studies of grain properties | R: No correlation found between multiplicity and maximum grain size in one sample | F: A larger sample is required | **partially**

## Reasoning

- Why this data: ALMA and SPHERE observations illustrate disc-companion interactions  
  > "in an attempt to illustrate the interactions between a disc and an external companion" (3.4 CSDs of interest)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Selection of systems is limited, not exhaustive  
  > "present a limited but representative selection of circumstellar discs in such systems" (3 Circumstellar discs (CSDs) in multiple stellar systems); "an extensive (although not exhaustive) list of multiple stellar systems of interest" (Appendix: List of young multiple stellar systems)
- Caveat (inferred, ours): Gallery images are archive QA products shown without stated band, beam or noise, so they cannot be used quantitatively
- Caveat (inferred, ours): Review: no new measurements or analysis of ALMA data

## Reproducibility

- Data public (paper): ALMA images downloaded from the public ALMA archive; SPHERE data from the ESO archive  
  > "The SPHERE polarimetric data were downloaded from the ESO archive" (3.4 CSDs of interest); "products that were downloaded from the ALMA archive" (3.4 CSDs of interest)
- Products in archive: ALMA quality assurance products used as they are  
  > "used as they are" (3.4 CSDs of interest)
- Code: IRDAP described as an open-access pipeline  
  > "processed using the IRDAP open-access pipeline" (3.4 CSDs of interest)
- Missing: Mapping of ALMA project codes to systems and panels
- Missing: Band, array, line and beam of each QA image
- Missing: SPHERE observation IDs and IRDAP settings
- Data volume (inferred): Small: only archive QA image products for about ten systems
- Score (inferred): 1/5, Review with a gallery of archive images; no measurements, recipe or numeric results to reproduce
- Rediscovery candidate: no, No ALMA measurements or analysis recipe; the paper is a literature review

## Links

- Method: (cite: Weber+2023) (Cited for details on polarimetric observations of discs in multiple systems)
- Companion: (cite: Andrews+2018) (DSHARP survey that first resolved the HT Lup discs)
- Companion: (cite: Kurtovic+2018) (DSHARP analysis of HT Lup and AS 205 spirals)
- Related: DSHARP

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.01678.S",
  "2019.1.00703.S",
  "2016.1.00484.L",
  "2016.1.01164.S",
  "2019.1.01792.S",
  "2015.1.01353.S",
  "2018.1.00532.S",
  "2018.1.00813.S",
  "2017.1.00350.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 0,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 22,
  "rate": 0.253
 },
 "evidence_ok": true
}
```
