# ALMA Discovery of Solar Umbral Brightness Enhancement at λ = 3 mm

`2017ApJ...841L..20I` | The Astrophysical Journal Letters 2017 | first author: Iwai, Kazumasa | arXiv: 1705.03147 | DOI: 10.3847/2041-8213/aa71b5

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: sun
- Question: What is the 3 mm brightness structure of a large sunspot umbra at high resolution, and how does it compare with UV/EUV/visible images?  
  > "The purpose of this study is to explore the structure of a sunspot at λ=3 mm in high-resolution ALMA images and to compare it" (1. Introduction)
- Target **Sunspot in AR12470**: coordinates N13E30 (heliographic)  
  > "The observed sunspot was part of the active region AR12470, located in the eastern hemisphere (N13E30) on December 16." (2. Observation); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 3 (λ=3 mm, 100 GHz)  
  > "The Band 3 (λ=3 mm, i.e. 100 GHz)" (2. Observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: twenty-two 12m antennas and nine 7m antennas, plus single-dish fast-scanning  
  > "which includes twenty-two 12m antennas and nine 7m antennas." (2. Observation)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 4.9"×2.2" synthesized beam  
  > "4".9×2".2 spatial resolution" (abstract)
- max recoverable scale: _not stated_
- sensitivity: noise about 3.7 K  
  > "The noise level of this map is about 3.7 K (Shimojo et al., 2017)" (3. Data Analysis and Results)
- time on source: _not stated_
- observing dates: 18:01-18:48 on 2015 December 16  
  > "between 18:01 and 18:48 on 2015 December 16" (2. Observation)
- pi or archival as stated: ALMA Science Verification data released early 2017  
  > "released as ALMA Science Verification data in early 2017" (2. Observation)
- Other facility **IRIS**: Slit-jaw images at 1330, 1400, 2796, 2832 Å  
  > "slit-jaw images at 1330 Å (C II), 1400 Å (Si IV), 2796 Å (Mg II line core) and 2832 Å" (3. Data Analysis and Results)
- Other facility **SDO/AIA**: 1700, 1600, 304, 171 Å images  
  > "at 1700 (lower photosphere), 304 (transition region), and 171 Å (cool corona) observed by AIA" (3. Data Analysis and Results)
- Other facility **SDO/HMI**: Visible continuum and line-of-sight magnetograms  
  > "Figure 1(d) displays the corresponding visible continuum image observed by the Helioseismic and Magnetic Imager (HMI: Scherrer et al. 2012), with temperature contours from the ALMA data overlaid." (3. Data Analysis and Results)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Quiet-Sun disk-centre temperature of single-dish image ~7500 K, 200 K above recommended; not corrected (2.7% offset)  
  > "we choose not to correct the absolute temperatures for the 2.7% offset represented by 200 K." (3. Data Analysis and Results)
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
- array combination: Single dish and interferometric data combined in the U-V plane (feathering), default parameters  
  > "The single dish and interferometric data were combined in the U-V plane (feathering)" (2. Observation)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details, calibration and imaging/feathering  
  > "Details of the observation and analysis are provided by Shimojo et al. (2017)." (2. Observation) [from Shimojo et al. 2017]
- Single-dish observations and temperature scale  
  > "Single dish, fast-scanning observations covering the full solar disk were carried out simultaneously (see White et al., 2017)." (2. Observation) [from White et al. 2017]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging software and versions
- Feathering parameters
- Method for aligning ALMA with IRIS/AIA/HMI
- Definition of inner/outer umbra ellipses
- Tool used for the analysis

## Analysis recipe

1. **Compare 3 mm brightness with multiwavelength images**: Overlay ALMA brightness temperature contours on AIA, HMI and IRIS images and compare  
  > "The overlaid contours indicate the radio brightness temperature at λ=3 mm observed by ALMA" (Figure 2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Histogram regional statistics**: Histograms of brightness temperature, continuum and field in inner and outer umbra regions  
  > "Histograms from the images of (b) brightness temperature at λ=3 mm" (Figure 5)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Umbral brightness enhancement average temperature | about 8000 K | not stated | K | 1 | The average temperature of this “umbral brightness enhancement” is about 8000 K |
| Inner penumbra temperature | 7200 | not stated | K | 1 | The inner penumbra (7200 K) and the outer part of the umbra (7300 K) |
| Plage temperature | about 7800 | not stated | K | 1 | The plage region neighboring the sunspot is about 7800 K at 3 mm. |

## Qualitative findings

- The 3 mm map shows a dark ring around a bright inner umbra, adjacent to a partial lightbridge; origin is ambiguous (intrinsic, umbral flashes, or coronal plume).  
  > "The present observations cannot distinguish between different" (4.3 Origin of the umbral brightness enhancement)

## Claim tuples

- H: Does the sunspot umbra show a 3 mm brightness enhancement at high resolution? | E: Analysis of ALMA Band 3 mosaic of AR12470 compared with IRIS, AIA, HMI | R: Inner umbra ~8000 K, ~800 K above inner penumbra | F: A previously unreported umbral brightness enhancement exists | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Origin may be intrinsic (penumbral darkening), umbral flashes, or coronal plume; cannot be distinguished  
  > "Another possibility is that the λ=3 mm umbral brightness enhancement is related to a" (4.3 Origin of the umbral brightness enhancement)
- How they decided it was enough: _not stated_
- Limitation (authors): Single snapshot, limited resolution, cannot distinguish scenarios  
  > "so that additional millimeter observations" (4.3 Origin of the umbral brightness enhancement)
- Caveat (inferred, ours): Single epoch; no uncertainty on regional means beyond std
- Caveat (inferred, ours): Absolute scale offset and feathering may bias values

## Reproducibility

- Data public (paper): Released as ALMA Science Verification data  
  > "released as ALMA Science Verification data in early 2017" (2. Observation)
- Products in archive: _not stated_
- Missing: Reduction details are in Shimojo et al. 2017
- Missing: Region definitions
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data, but processing deferred to companion papers.
- Rediscovery candidate: no, Recipe incomplete here and processing is external.

## Links

- Method: Shimojo et al. 2017 (Observation and analysis details)
- Method: White et al. 2017 (Single-dish data and scaling)
- Related: ALMA Science Verification solar data

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
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 57,
  "stated": 21,
  "rate": 0.368
 },
 "evidence_ok": true
}
```
