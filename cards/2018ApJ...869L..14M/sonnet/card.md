# Discovery of <SUP>14</SUP>NH<SUB>3</SUB> (2,2) Maser Emission in Sgr B2 Main

`2018ApJ...869L..14M` | The Astrophysical Journal Letters 2018 | first author: Mills, E. A. C. | arXiv: 1810.09567 | DOI: 10.3847/2041-8213/aaf237

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Is there 14NH3 (2,2) maser emission in Sgr B2 Main, and what are its properties and relation to other masers and continuum sources?  
  > "We report the discovery of a new, strong para-$^{14}$NH$_{3}$ maser in the metastable (2,2) transition toward the Galactic center star forming region Sgr B2 Main" (Introduction)
- Target **Sgr B2 Main (Sgr B2 (M))**: coordinates maser spots near 17h47m20s, -28d23m05s  
  > "which corresponds to a spatial resolution of 0.1 pc at the adopted distance to Sgr B2 of 8 kpc (cite: Reid09; Gravity18)" (Data); z/distance 8 kpc  
  > "which corresponds to a spatial resolution of 0.1 pc at the adopted distance to Sgr B2 of 8 kpc (cite: Reid09; Gravity18)" (Data); distance from Reid09; Gravity18  
  > "which corresponds to a spatial resolution of 0.1 pc at the adopted distance to Sgr B2 of 8 kpc (cite: Reid09; Gravity18)" (Data)

## Data provenance

- ALMA projects: 2016.1.00550.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA reference map 0.2 arcsec (3 mm continuum); VLA A-config 0.17x0.08 arcsec  
  > "a high-resolution (0$\ensuremath{''}$.2), 3 mm ALMA continuum map" (Absolute positional reference frame)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLA**: K-band 14NH3 observations: DnC (project 11B-210, Jan 2012) and A configuration (project 18A-229, Mar-Apr 2018)  
  > "made using the A configuration of the VLA in March-April 2018 (project 18A-229, PI: A. Ginsburg)" (High-resolution observations)
- External data: Published positions of OH, H2O, H2CO, SiO masers used for comparison  
  > "We have used published figures of the masers and the simultaneously observed continuum emission to align the maser positions with our continuum maps." (Results) [from Gaume90; McGrath04; Mehringer94; Morita92]

## Processing

### Calibration

- pipeline or manual: VLA pipeline with automated RFI flagging step removed; phase-only self-calibration  
  > "The data were pipeline processed using the VLA pipeline after removing the automated RFI flagging step." (High-resolution observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: three iterations of phase-only self-calibration on brightest (2,2) maser peak  
  > "We then performed three iterations of phase-only self-calibration using the brightest $^{14}$NH$_{3}$ (2,2) maser peak." (High-resolution observations)

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

- Calibration and imaging of the 2012 DnC data described elsewhere  
  > "additional description of these observations, including details on the data calibration and imaging, is given in (cite: Mills15)." (Low-resolution observations) [from Mills15]
- ALMA map positional accuracy tied to larger mosaic  
  > "which should have good absolute positional accuracy as it is tied to a larger mosaic of the region (cite: Ginsburg18)" (Absolute positional reference frame) [from Ginsburg18]

### Not stated but needed to reproduce (our reading)

- CASA/pipeline versions
- imaging parameters (weighting, cell, deconvolver)
- how maser positions/widths were fitted
- continuum subtraction details
- ALMA map processing

## Analysis recipe

1. **align VLA A-config frame to ALMA**: cross-correlate ALMA 3 mm image with A-config continuum image and shift  
  > "to perform cross correlations between the ALMA image and our A-configuration continuum image" (Absolute positional reference frame)
   - software: scikit-image
   - parameter: shift 0.05" in RA and 0.48" in Dec; uncertainty ±0.03"  
  > "shift our A-configuration images by $0\ensuremath{''}.05$ in Right Ascension and $0\ensuremath{''}.48$ in Declination" (Absolute positional reference frame)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **scikit-image** : register_translation cross-correlation for image alignment  
  > "We use the task ‘register_translation’ from the python package scikit-image (cite: scikit14)" (Absolute positional reference frame)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M1 peak brightness temperature | 90900 | ±1000 | K | 0 | 90900 $\pm$ 1000 |
| M1 FWHM linewidth | 1.64 | ±0.02 | km/s | 0 | 1.64 $\pm$ 0.02 |

## Qualitative findings

- Maser spots are not coincident with other masers or continuum peaks  
  > "The maser spots are not spatially or kinematically coincident with any other masers in this region" (abstract)

## Claim tuples

- H: Is there NH3 (2,2) maser emission in Sgr B2 Main? | E: VLA DnC and A-config observations of 13 NH3 transitions | R: (2,2) only line masing; 5 spots in A config, widths 1.6-3.9 km/s | F: First 14NH3 (2,2) maser discovered | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA used only for astrometry
- Caveat (inferred, ours): Tb are lower limits since spots unresolved

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: VLA imaging parameters
- Missing: fit procedure
- Data volume (inferred): ~100s GB (VLA) plus ALMA continuum image
- Score (inferred): 3/5, VLA data central; ALMA minor; few processing details.
- Rediscovery candidate: no, Main data are VLA and imaging recipe incomplete.

## Links

- Companion: Mills15 (VLA data calibration and imaging for 2012 data)
- Companion: Ginsburg18 (ALMA mosaic of Sgr B2)

## Checks

```json
{
 "quotes": 21,
 "quotes_ok": 21,
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
  "stated": 15,
  "rate": 0.283
 },
 "evidence_ok": true
}
```
