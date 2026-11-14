# The HH 212 Interstellar Laboratory: Astrochemistry as a Tool To Reveal Protostellar Disks on Solar System Scales around a Rising Sun

`2019ESC.....3.2110C` | ACS Earth and Space Chemistry 2019 | first author: Codella, Claudio | arXiv: 1910.04442 | DOI: 10.1021/acsearthspacechem.9b00136

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, protoplanetary_disks
- Question: Can iCOM emission (CH3CHO, CH3OH) reveal the disk and centrifugal barrier of the Class 0 protostar HH 212-mm on Solar System scales, where simple tracers (CO, CS, SiO) fail?  
  > "the observation of iCOMs emission, observed to infer the chemical composition of star forming regions, can be used also as unique tracer to image protostellar disks on Solar System scales" (abstract)
- Target **HH 212-mm**: coordinates RA(J2000) 05h43m51.41s, Dec -01d02'53.17" (MM1 continuum peak)  
  > "located at a distance 405(15) pc [20] in the L1630 cloud in Orion B" (3. HH 212: AN ILLUSTRATIVE CASE OF THE SOLAR TYPE STAR FORMATION PROCESS COMPLEXITY); "R.A.(J2000) = 05 [h] 43 [m ] 51.41 [s]," (Appendix 1: Technical details of the new ALMA observations presented in this review); z/distance 405(15) pc  
  > "located at a distance 405(15) pc [20] in the L1630 cloud in Orion B" (3. HH 212: AN ILLUSTRATIVE CASE OF THE SOLAR TYPE STAR FORMATION PROCESS COMPLEXITY); "R.A.(J2000) = 05 [h] 43 [m ] 51.41 [s]," (Appendix 1: Technical details of the new ALMA observations presented in this review); distance from Kounkel et al. 2017 (GOBELINS)  
  > "located at a distance 405(15) pc [20] in the L1630 cloud in Orion B" (3. HH 212: AN ILLUSTRATIVE CASE OF THE SOLAR TYPE STAR FORMATION PROCESS COMPLEXITY); "R.A.(J2000) = 05 [h] 43 [m ] 51.41 [s]," (Appendix 1: Technical details of the new ALMA observations presented in this review)

## Data provenance

- ALMA projects: 2016.1.01475.S
- bands: Band 7  
  > "The new observations of HH 212 analyzed here were obtained with ALMA Band 7 using" (Appendix 1: Technical details of the new ALMA observations presented in this review)
- frequencies and spectral setup: Cycle 1: 337.1-338.9 and 348.4-350.7 GHz, 488 kHz units; Cycle 4: 335.0-337.4 GHz, 122 kHz (0.1 km/s) units  
  > "For Cycle 4 spectral units of 122 kHz" (Appendix 1: Technical details of the new ALMA observations presented in this review)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas: 34 (Cycle 1), 44 (Cycle 4)  
  > "using 44 12-m antennas between 6 October and 26 November 2016" (Appendix 1: Technical details of the new ALMA observations presented in this review)
- configurations: _not stated_
- baselines: Maximum baselines 650 m (Cycle 1) and 3 km (Cycle 4)  
  > "The maximum baselines for Cycle 1 and 4 were 650 m and 3 km," (Appendix 1: Technical details of the new ALMA observations presented in this review)
- angular resolution: Cycle 4: 0.15" x 0.12" (~60 au); Cycle 1: 0.41"x0.33" to 0.52"x0.34" (~160 au)  
  > "The continuum-subtracted images have a typical clean-beam FWHM of 0.15” x 0.12” (PA = -88 [o] )," (Appendix 1: Technical details of the new ALMA observations presented in this review)
- max recoverable scale: _not stated_
- sensitivity: rms ~30 mJy/beam (Cycle 1); 4-5 mJy/beam (Cycle 4)  
  > "rms noise level of 4–5 mJy beam [-1] ." (Appendix 1: Technical details of the new ALMA observations presented in this review)
- time on source: _not stated_
- observing dates: Cycle 1: 15 June-19 July 2014 (30SiO); Cycle 4: 6 October-26 November 2016 (HDCO, CH3OH, CH3OD)  
  > "between 6 October and 26 November 2016 during the Cycle 4 phase (HDCO," (Appendix 1: Technical details of the new ALMA observations presented in this review)
- pi or archival as stated: _not stated_
- Line: HDCO 5(1,4)-4(1,3) (335.0968 GHz)
- Line: CH3OH 7(1,7)-6(1,6) A (335.5820 GHz)
- Line: 30SiO 8-7 (338.9300 GHz)
- Line: CH3CHO 18(0,18)-17(0,17) A (335.3587 GHz)
- External data: C17O(3-2) and C34S(7-6) ALMA data  
  > "c. Tabone et al. [14] ; d. Bianchi et al. [15] ; e. Codella et al. [16] ." (Table 1) [from Tabone et al. [14]]
- External data: CH3CHO column densities and maps  
  > "column densities of CH 3 CHO [16] and [13] CH 3 OH" (Figure 8) [from Codella et al. [16]]
- External data: 12C/13C = 50 for Orion  
  > "We then assumed a" (4.3 Acetaldehyde and methanol abundance ratios: feeding astrochemical models) [from Kahane et al. (cite: 61)]

## Processing

### Calibration

- pipeline or manual: standard procedures  
  > "Calibration was carried out" (Appendix 1: Technical details of the new ALMA observations presented in this review)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA used for line imaging  
  > "The CASA package was used to" (Appendix 1: Technical details of the new ALMA observations presented in this review)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: images are continuum-subtracted  
  > "The continuum-subtracted Cycle 1 images have clean-beam FWHMs" (Appendix 1: Technical details of the new ALMA observations presented in this review)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 13CH3OH and CH3CHO data/analysis from earlier papers  
  > "which are published in Tabone et al. 14, Codella et al. 16, and" (Appendix 1: Technical details of the new ALMA observations presented in this review) [from Tabone et al. 2017; Codella et al. 2018; Bianchi et al. 2017]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell and image size for each image
- Line-free channels for continuum subtraction
- CASA version and flux calibrator details
- Rotational diagram lines and fit details for N(CH3CHO), N(13CH3OH)
- Beam-filling factor and Trot adopted

## Analysis recipe

1. **Image lines and make channel maps**: CASA line imaging of continuum-subtracted data, integrated in velocity channels  
  > "The CASA package was used to" (Appendix 1: Technical details of the new ALMA observations presented in this review)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Position-velocity diagrams and uv-fit centroids**: PV cuts along equatorial plane; uv-plane fit of two gas components for CH3OH centroids per channel  
  > "The fit has been performed assuming two gas components associated with the northern and southern outer disk." (4.2 The hamburger shape of methanol emission: disk atmosphere or accretion shock?)
   - fitting: _not stated_
   - validation: _not stated_
3. **CH3CHO/CH3OH abundance ratio**: Rotational diagram under LTE; CH3OH from 13CH3OH x 50  
  > "We used the rotational diagram analysis to determine the temperature and the column" (4.3 Acetaldehyde and methanol abundance ratios: feeding astrochemical models)
   - assumption: LTE, optically thin 13CH3OH, 12C/13C = 50  
  > "The column densities have been" (4.3 Acetaldehyde and methanol abundance ratios: feeding astrochemical models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : spectral line imaging  
  > "The CASA package was used to" (Appendix 1: Technical details of the new ALMA observations presented in this review)
- **GILDAS** : data analysis  
  > "while data analysis was performed using GILDAS" (Appendix 1: Technical details of the new ALMA observations presented in this review)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CHO/CH3OH abundance ratio | 3-4 x 10^-3 | not stated | dimensionless | 3 | The ratio looks pretty constant, lying in the 3-4 x 10 [-3] range. |
| N(CH3CHO) | 8 x 10^15 | 3 x 10^15 | cm-2 | 3 | N(CH 3 CHO) = 8(3) x 10 [15 ] cm [-2] |
| N(13CH3OH) | 7 x 10^16 | 2 x 10^16 | cm-2 | 3 | column density is 7(2) x 10 [16 ] cm [-2] |
| N(CH3OH) | 4 x 10^18 | 1 x 10^18 | cm-2 | 3 | N(CH 3 OH) = 4(1) x 10 [18 ] cm [-2] |

## Qualitative findings

- CH3CHO PV shows a rigidly rotating ring (v ∝ R) of radius ~40 au, unlike C17O.  
  > "this line is emitted in a ring of gas, which rotates around the center as a rigid" (4.1 Acetaldehyde: a rotating ring of warm gas)
- CH3OH peaks above and below the equatorial plane (hamburger shape).  
  > "peaks above and below it, i.e. towards the South" (4.2 The hamburger shape of methanol emission: disk atmosphere or accretion shock?)

## Claim tuples

- H: Can iCOMs trace the disk/centrifugal barrier where simple molecules cannot? | E: Compared C17O PV with CH3CHO and CH3OH PV and maps | R: C17O PV cannot distinguish Keplerian from infall; CH3CHO shows a rotating ring at ~40 au | F: iCOMs trace the centrifugal barrier/disk atmosphere | **supported**
- H: Is the CH3CHO/CH3OH ratio in HH 212 similar to other hot corinos? | E: Rotational diagram column density ratio vs literature | R: 3-4e-3 in HH 212, in 1e-3 to 1e-2 range, lower than comets | F: Similar to hot corinos, lower than comets | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disk atmosphere vs. optically thick dust obscuring midplane methanol; accretion shock vs. thermal sublimation; disk wind  
  > "In principle, all these findings have two explanations" (4.2 The hamburger shape of methanol emission: disk atmosphere or accretion shock?)
- How they decided it was enough: _not stated_
- Limitation (authors): Edge-on geometry and optically thick continuum prevent midplane detection; lower-frequency observations needed.  
  > "high spatial resolution observations are needed at much" (4.2 The hamburger shape of methanol emission: disk atmosphere or accretion shock?)
- Caveat (inferred, ours): Review paper: new data only briefly described, no uncertainty analysis of rotational diagram
- Caveat (inferred, ours): Abundance ratio relies on 12C/13C=50 and LTE
- Caveat (inferred, ours): Ratio quoted as 3-4e-3 in text but 1-3e-3 in Table 2

## Reproducibility

- Data public (paper): Project 2016.1.01475.S acknowledged  
  > "This paper makes use of the ADS/JAO.ALMA#2016.1.01475.S data (PI: C. Codella)." (ACKNOWLEDGMENT)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Rotational diagram details and line lists used
- Missing: Cycle 1 project code
- Data volume (inferred): ~50-200 GB
- Score (inferred): 3/5, Data public but imaging and fitting details are sparse; mostly review.
- Rediscovery candidate: no, Recipe incomplete; results mostly drawn from prior papers.

## Links

- Method: Codella et al. 2018 (cite: 16) (CH3CHO observations and analysis)
- Companion: Lee et al. 2017b (cite: 24) (CH3OH disk atmosphere)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 29,
  "rate": 0.46
 },
 "evidence_ok": true
}
```
