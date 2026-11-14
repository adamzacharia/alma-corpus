# VLA Overview of the Bursting H2O Maser Source G25.65+1.05

`2019ApJ...884..140B` | The Astrophysical Journal 2019 | first author: Bayandina, O. S. | arXiv: 1812.11353 | DOI: 10.3847/1538-4357/ab3fa4

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: Where is the bursting 22 GHz H2O maser in G25.65+1.05 relative to continuum sources and other masers, and what caused the burst?  
  > "For the first time, maps of 22 GHz H$_2$O and 44 GHz CH$_3$OH maser spots are obtained and the absolute position of the 22 GHz H$_2$O bursting feature is determined with milliarcsecond precision." (abstract)
- Target **G25.65+1.05 (RAFGL7009S, IRAS 18316-0602)**: coordinates pointing RA(J2000)=18h34m21s, Dec(J2000)=-05d59m42s  
  > "The pointing coordinates used were RA(J2000)=18$^h$34$^m$21$^s$, DEC(J2000)=-05$^{\circ}$59$\ensuremath{'}$42$\ensuremath{''}$ and the central velocity was 42 km s$^{-1}$." (2 Observations); "indicates a distance of 2.08$\pm$0.37 kpc with a probability of 64%. In our calculations below we will use this value." (1 Introduction); z/distance 2.08±0.37 kpc  
  > "The pointing coordinates used were RA(J2000)=18$^h$34$^m$21$^s$, DEC(J2000)=-05$^{\circ}$59$\ensuremath{'}$42$\ensuremath{''}$ and the central velocity was 42 km s$^{-1}$." (2 Observations); "indicates a distance of 2.08$\pm$0.37 kpc with a probability of 64%. In our calculations below we will use this value." (1 Introduction); distance from BeSSeL probability density function (Reid et al. 2016)  
  > "The pointing coordinates used were RA(J2000)=18$^h$34$^m$21$^s$, DEC(J2000)=-05$^{\circ}$59$\ensuremath{'}$42$\ensuremath{''}$ and the central velocity was 42 km s$^{-1}$." (2 Observations); "indicates a distance of 2.08$\pm$0.37 kpc with a probability of 64%. In our calculations below we will use this value." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00826.S
- bands: ALMA: 350 GHz image from archive (JVLA main data)  
  > "ALMA archive data (Project Code 2012.1.00826.S) provide a 350 GHz image showing a point source at the position of JVLA 2." (5.1 Nature of the Continuum Sources)
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
- Other facility **JVLA**: B-configuration C, Ku, K, Q band continuum and maser line data (project 17B-408)  
  > "in the B-configuration as a Target of Opportunity program (project code 17B-408)" (2 Observations)
- External data: Distance 2.08±0.37 kpc from BeSSeL  
  > "indicates a distance of 2.08$\pm$0.37 kpc with a probability of 64%." (1 Introduction) [from (cite: 2016ApJ...823...77R)]

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

### Not stated but needed to reproduce (our reading)

- ALMA 350 GHz data reduction, flux and position of the point source are not given
- ALMA band, array and resolution not given

## Analysis recipe


## Software


## Numeric results


## Qualitative findings

- The archival ALMA 350 GHz image shows a point source at JVLA 2, supporting it being a massive accreting protostar.  
  > "Based on the presence of 6.7 GHz masers and the ALMA detection at 350 GHz, we propose that JVLA 2 is a massive, accreting protostar." (8. Conclusions)

## Claim tuples

- H: Is JVLA 2 an embedded massive YSO? | E: Compared JVLA continuum and 6.7 GHz masers with archival ALMA 350 GHz image and IR source | R: ALMA point source and K-band IR source coincide with JVLA 2 | F: JVLA 2 is a massive accreting protostar | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA used only qualitatively, with no processing details

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data details and measurements
- Data volume (inferred): Not applicable for ALMA part; likely tens of GB if reprocessed
- Score (inferred): 1/5, ALMA contribution is a single qualitative statement without any methods.
- Rediscovery candidate: no, ALMA role is minor and not numeric.

## Links

- Related: BeSSeL

## Checks

```json
{
 "quotes": 14,
 "quotes_ok": 14,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 0,
 "numeric_problems": 0,
 "fill": {
  "facts": 46,
  "stated": 8,
  "rate": 0.174
 },
 "evidence_ok": true
}
```
