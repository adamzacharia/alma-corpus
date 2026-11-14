# Recent Progress in High-Mass Star-Formation Studies with ALMA

`2018PKAS...33...21H` | Publication of Korean Astronomical Society 2018 | first author: Hirota, Tomoya | arXiv: 1806.10837 | DOI: 10.5303/PKAS.2018.33.2.021

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: What has ALMA contributed to high-mass star-formation studies (filaments/clumps/cores, disks and outflows, chemistry, masers and accretion bursts)?  
  > "It should be noted that only representative observational results from ALMA are presented in this review." (Summary of ALMA Outcomes)
- Target **Orion KL / Source I**: coordinates _not stated_; z/distance 420 pc (Orion Molecular Cloud)  
  > "even the nearest site of high-mass star-formation, i.e. Orion Molecular Cloud, is located three times larger distance of 420 pc." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV, 2011.0.00199.S, 2013.1.00048.S, 2015.1.00669.S
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
- Line: Si18O not stated (484 GHz)
- External data: Enclosed mass of Orion Source I 8.7±0.6 Msun and centrifugal radii 21-47 AU from Si18O position-velocity diagram  
  > "The position-velocity diagram suggests an enclosed mass of 8.7$\pm$0.6$M_{\odot}$ and centrifugal radii of 21-47 AU." (Disks and Outflows) [from (cite: Hirota2017)]

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

- This is a review; no data reduction or analysis recipe is given. Reproduction would require the original papers.

## Analysis recipe


## Software


## Numeric results


## Qualitative findings

- ALMA resolves 100-1000 AU disks and outflows around high-mass YSOs, with evidence of disk accretion and magnetically driven outflows analogous to low-mass star formation.  
  > "These results show strong evidences of the accretion through disks and magnetically driven outflows which are analogous to low-mass star-formation." (Summary)

## Claim tuples

- H: Does ALMA provide evidence on high-mass star-formation scenarios (turbulent core vs competitive accretion)? | E: Literature review of ALMA studies of IRDC cores, protoclusters, disks, outflows, chemistry, masers | R: Observations give mixed results favoring either model; few high-mass starless cores are confirmed | F: More statistical, uniform datasets are needed to decide the dominant process | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Observations are limited to case studies; resolution insufficient for innermost regions.  
  > "observations are still limited for case studies of well know sources, and spatial resolutions are insufficient to resolve the innermost regions" (Summary)
- Caveat (inferred, ours): Review: selective coverage, no quantitative synthesis.

## Reproducibility

- Data public (paper): Archive data listed in acknowledgments  
  > "This paper makes use of the following ALMA archive data" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Entire methods; the review presents no processing or analysis.
- Data volume (inferred): not applicable
- Score (inferred): 1/5, Review paper with no reproducible recipe.
- Rediscovery candidate: no, No methods or numeric results of its own.

## Links

- Companion: (cite: Hirota2017) (Orion Source I Si18O disk/outflow result discussed)
- Related: ALMA large program 2017.1.01355.L

## Checks

```json
{
 "quotes": 13,
 "quotes_ok": 13,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.1.01355.L"
 ],
 "numeric_results": 0,
 "numeric_problems": 0,
 "fill": {
  "facts": 46,
  "stated": 6,
  "rate": 0.13
 },
 "evidence_ok": true
}
```
