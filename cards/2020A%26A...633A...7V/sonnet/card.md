# Temperature profiles of young disk-like structures. The case of IRAS 16293A

`2020A&A...633A...7V` | Astronomy and Astrophysics 2020 | first author: van 't Hoff, Merel L. R. | arXiv: 1911.03495 | DOI: 10.1051/0004-6361/201936839

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What is the gas temperature structure of the young disk-like structure around the Class 0 protostar IRAS 16293-2422A, as probed by H2CS line ratios?  
  > "We set out to determine the gas temperature of the young disk-like structure around the Class 0 protostar IRAS 16293–2422A." (abstract)
- Target **IRAS 16293-2422A**: coordinates RA(J2000) 16h32m22.873s, Dec -24d28m36.54s  
  > "In this work we focus on the A source ($\alpha$(J2000) = 16$^{\rm{h}}$32$^{\rm{m}}$22.873s; $\delta$(J2000) =  $-$24$\ensuremath{^\circ}$28$\ensuremath{'}$36.54$''$)." (2 Observations); "($d \sim$140 pc; (cite: Dzib2018))" (Introduction); z/distance d ~140 pc  
  > "In this work we focus on the A source ($\alpha$(J2000) = 16$^{\rm{h}}$32$^{\rm{m}}$22.873s; $\delta$(J2000) =  $-$24$\ensuremath{^\circ}$28$\ensuremath{'}$36.54$''$)." (2 Observations); "($d \sim$140 pc; (cite: Dzib2018))" (Introduction); distance from Dzib2018  
  > "In this work we focus on the A source ($\alpha$(J2000) = 16$^{\rm{h}}$32$^{\rm{m}}$22.873s; $\delta$(J2000) =  $-$24$\ensuremath{^\circ}$28$\ensuremath{'}$36.54$''$)." (2 Observations); "($d \sim$140 pc; (cite: Dzib2018))" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00278.S, 2012.1.00712.S, 2016.1.01150.S
- bands: Band 7 (329-363 GHz) and Band 6 (~230 GHz)  
  > "The PILS program also contains eight selected windows in Band 6 ($\sim$230 GHz)" (2 Observations)
- frequencies and spectral setup: Band 7 resolution 0.2 km/s (244 kHz); Band 6 and 2016 data 0.15 km/s (122 kHz)  
  > "The data have a spectral resolution of 0.2 km s$^{-1}$ (244 kHz)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5" (~70 AU)  
  > "a restoring beam of 0.5$\ensuremath{''}$ ($\sim$70 AU)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 7: 7-10 mJy/beam/channel; Band 6: ~4; 2016.1.01150.S: ~1.3  
  > "a sensitivity of 7–10 mJy beam$^{-1}$ channel$^{-1}$, or $\sim$5 mJy beam$^{-1}$ km s$^{-1}$ across the entire frequency range" (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H2CS 7(K)-6(K) and 10(K)-9(K) multiple Ka lines (236.7-240.5 GHz and 338.1-348.5 GHz)
- External data: H2CS collisional rate coefficients (in LAMDA)  
  > "which contains collisional rate coefficients for H$_2$CS from (cite: Wiesenfeld2013))" (3.3 Temperature) [from Wiesenfeld2013; Schoier2005]
- External data: Spectroscopic line data from CDMS  
  > "The transition frequencies and other line data were taken from the CDMS database (cite: Muller2001; Muller2005)." (2 Observations) [from Muller2001; Muller2005]
- External data: H2CS column density toward IRAS 16293B of 1.3e15 cm-2  
  > "Toward IRAS 16293B, a H$_2$CS column density of $1.3 \times 10^{15}$ cm$^{-2}$ was found (cite: Drozdovskaya2018)." (3.3 Temperature) [from Drozdovskaya2018]

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
- continuum subtraction: described in Jorgensen2016  
  > "A detailed description of the data reduction and continuum subtraction can be found in (cite: Jorgensen2016)." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and continuum subtraction of PILS Band 7 and Band 6 data  
  > "The data reduction proceeded in the same manner as the Band 7 data (cite: Jorgensen2016)." (2 Observations) [from Jorgensen2016]
- Data reduction of program 2016.1.01150.S  
  > "The data reduction is described in (cite: Taquet2018)." (2 Observations) [from Taquet2018]
- Line isolation via methanol peak-velocity map and VINE maps  
  > "we make use of the method outlined in (cite: Calcutt2018) to isolate the formaldehyde and thioformaldehyde lines" (3.1 Kinematics) [from Calcutt2018]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details
- Imaging parameters (robust, cell, image size, deconvolver)
- Whether Band 6/7 images were smoothed to a common beam
- Pixel-by-pixel blending exclusion criteria
- Line-free channels for continuum subtraction
- Exact RADEX grid ranges and the LTE calculation details
- Fitting method for rotation diagrams

## Analysis recipe

1. **Isolate lines and build velocity-corrected maps**: Peak velocity per pixel from bright methanol line used to identify target lines; VINE moment-0 maps  
  > "the peak velocity in each pixel is determined using a bright methanol transition (7$_{3,5}$ – 6$_{4,4}$ at 337.519 GHz)" (3.1 Kinematics)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract peak flux maps**: Moment 8 (peak flux per pixel); pixels with too much blending excluded  
  > "we extract the peak flux per pixel in order to make spatial maps of the line ratios and hence temperature structure" (3.2 Peak fluxes)
   - fitting: _not stated_
   - validation: _not stated_
3. **Convert H2CS line ratios to temperature**: Grid of RADEX non-LTE models; LTE where no collision rates  
  > "converted into temperature maps using a grid of RADEX non-LTE radiative transfer models" (3.3 Temperature)
   - software: RADEX
   - parameter: n(H2)=1e10 cm-3, N(H2CS)=1e14 cm-2, line width 2 km/s  
  > "A column density of $10^{14}$ cm$^{-2}$ is adopted in the temperature calculations." (3.3 Temperature)
   - assumption: Densities >1e7 cm-3 make ratios density independent  
  > "the exact value adopted for the density does not influence the derived temperatures and we use a value of $10^{10}$ cm$^{-3}$" (3.3 Temperature)
   - fitting: _not stated_
   - validation: Error bars from image rms propagated through RADEX; compared with LTE results  
  > "Error bars on the line ratios are calculated from the image rms, and converted into error bars on the temperature using the RADEX calculations" (3.3 Temperature)
4. **Rotation diagrams per pixel as cross-check**: Rotation diagrams for every pixel in 2"x2" region; fits to all, para, ortho, or Eup<200 K lines  
  > "rotation diagrams are made for every pixel in a $2^{\prime\prime} \times 2^{\prime\prime}$ region surrounding the continuum position" (3.3 Temperature)
   - assumption: Ortho-to-para ratio 2 (1-3 changes T by <~30 K)  
  > "An ortho-to-para ratio of 2 is assumed, but varying this between 1 and 3 changes the derived temperature by $\lesssim$30 K." (3.3 Temperature)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RADEX** : Non-LTE radiative transfer grid to convert line ratios to temperature  
  > "a grid of RADEX non-LTE radiative transfer models (cite: vanderTak2007)" (3.3 Temperature)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gas temperature in inner ~150 AU | ~100-175 | not stated | K | 3 | the temperature is between $\sim$100–175 K in the inner $\sim$150 AU, and drops to $\sim$75 K at $\sim$200 AU |
| Gas temperature at ~200 AU | ~75 | not stated | K | 3 | drops to $\sim$75 K at $\sim$200 AU |
| Rotation-diagram temperature at 200 AU / center | ~60 at 200 AU rising to ~150 at center | not stated | K | 4 | The first three cases result in temperatures of $\sim$60 K at 200 AU rising up to $\sim$150 at source center. |
| Non-LTE minus LTE temperature offset | ~20-50 | not stated | K | 3 | The non-LTE RADEX results give temperatures higher by $\sim$20–50 K than the LTE results |

## Qualitative findings

- High-velocity wings of H2CS 7(0,7)-6(0,6) arise from line blending, not Keplerian rotation  
  > "The large velocity gradient thus seems the result of line blending and not Keplerian rotation." (3.1 Kinematics)

## Claim tuples

- H: Is the disk-like structure warm and does temperature rise steeply inside 100 AU as in envelope models? | E: H2CS line ratios converted to temperature with RADEX, plus rotation diagrams | R: 100-175 K within 150 AU, ~75 K at 200 AU, no steep rise at <100 AU | F: Consistent with envelope profiles down to ~100 AU but flatter inside | **supported**
- H: Is there a temperature jump at the disk-envelope interface? | E: Radial temperature profiles at 0.5" resolution | R: No jump seen | F: No evidence for centrifugal-barrier heating at current resolution | **supported**
- H: Does IRAS 16293A's disk-like structure differ in temperature from L1527? | E: Compare with literature L1527 profile | R: ~75 K higher | F: Consistent with higher luminosity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Ratios of H2CS lines across Ka ladders trace kinetic temperature independent of pointing, beam and calibration  
  > "can provide a measure of the kinetic temperature unaffected by relative pointing uncertainties, beam-size differences and absolute calibration uncertainties" (Introduction)
- Alternative: H2CO, H2(13)CO and D2CO rejected: too few unblended lines, optically thick, or continuum oversubtraction  
  > "However, all these ratios are near unity, suggesting that the emission is optically thick" (3.3 Temperature)
- How they decided it was enough: _not stated_
- Limitation (authors): Line blending and limited 0.5" resolution; optically thin higher-resolution tracers are needed  
  > "High resolution observations of optically thin lines are required to establish the details of the temperature profile in the inner $\sim$100 AU." (5 Conclusions)
- Caveat (inferred, ours): Peak-flux ratios in the blended central pixels may be biased
- Caveat (inferred, ours): Assumed column density of 1e14 cm-2 and single density are not fitted
- Caveat (inferred, ours): Unresolved binary A1/A2 and dust optical depth not modeled
- Caveat (inferred, ours): No formal temperature fitting or uncertainty budget beyond rms

## Reproducibility

- Data public (paper): Data are ALMA programs with listed project codes; PILS is a public survey  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00712.S, ADS/JAO.ALMA#2013.1.00278.S and ADS/JAO.ALMA#2016.1.01150.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduced PILS cubes details/imaging parameters (in Jorgensen2016)
- Missing: Pixel selection and blending masks
- Missing: Exact RADEX setup and LTE procedure
- Data volume (inferred): Hundreds of GB for the three programs' raw data; PILS reduced cubes tens of GB
- Score (inferred): 3/5, Methodology is clear and simple, but reduction/imaging is deferred to other papers and pixel selection is not specified.
- Rediscovery candidate: no, Main numbers are approximate ranges and depend on unspecified blending-based pixel selection and inherited reductions.

## Links

- Method: Jorgensen2016 (PILS survey and data reduction)
- Method: Calcutt2018 (Line isolation / VINE method)
- Method: Taquet2018 (Reduction of 2016.1.01150.S)
- Companion: Oya2016 (Earlier H2CS temperature and kinematics of IRAS 16293A)
- Companion: vantHoff2018b (L1527 temperature profile comparison)
- Related: PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 29,
  "rate": 0.426
 },
 "evidence_ok": true
}
```
