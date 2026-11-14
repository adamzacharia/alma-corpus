# ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). II. Vertical stratification of CO, CS, CN, H<SUB>2</SUB>CO, and CH<SUB>3</SUB>OH in a Class I disk

`2020A&A...642L...7P` | Astronomy and Astrophysics 2020 | first author: Podio, L. | arXiv: 2008.12648 | DOI: 10.1051/0004-6361/202038952

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How are CO, CS, H2CO, CN and CH3OH distributed vertically in the edge-on Class I disk of IRAS 04302, and what is the CH3OH/H2CO abundance ratio?  
  > "We report the first tentative detection of methanol (CH$_3$OH) in a Class I disk and resolve, for the first time, the vertical structure of a disk with multiple molecular tracers." (abstract)
- Target **IRAS 04302+2247**: coordinates _not stated_; z/distance 161±3 pc  
  > "located in Taurus ($d=161\pm3$ pc, (cite: galli19))" (Introduction); "edge-on disk ($i = 90\pm3\degree$[^1], (cite: wolf03))" (Introduction); distance from galli19  
  > "located in Taurus ($d=161\pm3$ pc, (cite: galli19))" (Introduction); "edge-on disk ($i = 90\pm3\degree$[^1], (cite: wolf03))" (Introduction)

## Data provenance

- ALMA projects: 2018.1.01037.S
- bands: Band 6 (1.3 mm)  
  > "Observations were taken with ALMA-Band 6 on October 28, 2018" (2 Observations and data reduction)
- frequencies and spectral setup: High-resolution (0.141 MHz) SPWs covering CO 2-1, CN 2-1, o-H2CO, CS 5-4, CH3OH; CS in broad continuum SPW (1.129 MHz)  
  > "The correlator set-up consists of high-resolution (0.141 MHz) spectral windows (SPWs)" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1.4 km  
  > "with baselines ranging from 15 m to 1.4 km" (2 Observations and data reduction)
- angular resolution: ~0.3" (~48 au); beams 0.31x0.26 to 0.41x0.32 arcsec  
  > "The clean beam of the self-calibrated maps ranges from 0.31$''$$\times$0.26$''$ to 0.41$''$$\times$0.32$''$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms per channel ~0.8-2.3 mJy/beam  
  > "the root mean square (r.m.s.) noise per channel is $\simeq 0.8-2.3$ mJy beam$^{-1}$" (2 Observations and data reduction)
- time on source: ~113 minutes  
  > "The integration time sums up to $\sim 113$ minutes." (2 Observations and data reduction)
- observing dates: October 28, 2018  
  > "Observations were taken with ALMA-Band 6 on October 28, 2018" (2 Observations and data reduction)
- pi or archival as stated: PI L. Podio  
  > "(PI L. Podio)" (Acknowledgements)
- Line: CO 2-1 (230538.000 MHz)
- Line: CN 2-1 hyperfine (226874.7813 MHz (central))
- Line: CS 5-4 (244935.557 MHz)
- Line: o-H2CO 3_{1,2}-2_{1,1} (225697.775 MHz)
- Line: CH3OH-A 5_{0,5}-4_{0,4} (241791.352 MHz)
- External data: Molecular line parameters (spectroscopy) for column densities  
  > "converted into column densities through the molecular parameters in Table [\[tab:lines\]](#tab:lines) (cite: Mueller2005)" (3.3) [from Mueller2005]
- External data: Comparison CH3OH/H2CO ratios for TW Hya, HD 163296, hot corinos, comets  
  > "$\sim 1.27 - 1.73$ for T$_{\rm ex} \sim 25-75$ K, (cite: walsh16; carney19)" (4 Discussion) [from walsh16; carney19; jorgensen18; taquet15; biver15; rubin19]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2  
  > "Data reduction was carried out using CASA 4.7.2." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on continuum, applied to line-free continuum and continuum-subtracted line; continuum S/N improved by 3.4  
  > "The signal-to-noise ratio (S/N) of the continuum improved by a factor of 3.4 after the self-calibration." (2 Observations and data reduction)

### Imaging

- task: TCLEAN  
  > "The final maps were produced with TCLEAN" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: robust=0.0 for CO, H2CO, CS, CN; robust=2.0 for CH3OH  
  > "We used Briggs weighting with robust=0.0 for the bright CO, H$_2$CO, CS, and CN lines" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manually selected mask  
  > "by applying a manually selected mask on the visible signal" (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.31x0.26 to 0.41x0.32 arcsec  
  > "ranges from 0.31$''$$\times$0.26$''$ to 0.41$''$$\times$0.32$''$" (2 Observations and data reduction)
- final rms: 0.8-2.3 mJy/beam per channel  
  > "$\simeq 0.8-2.3$ mJy beam$^{-1}$" (2 Observations and data reduction)

### Inherited from earlier work

- Validity of LTE and optically thin assumptions  
  > "The validity of these assumptions is discussed by (cite: podio19)." (3.3) [from (cite: podio19)]
- Excitation temperature ranges  
  > "the excitation temperature is assumed to be 20$-$100 K in the molecular layer and 10$-$30 K in the outer midplane (cite: walsh10)" (3.3) [from (cite: walsh10)]

### Not stated but needed to reproduce (our reading)

- Continuum-subtraction channels / line-free channels
- Self-calibration solution intervals and number of rounds
- Image size, cell size (pixel apparently 0.06 arcsec)
- Clean threshold and mask details
- Exact integration regions for molecular layer and midplane
- Flux calibrator and flux scale uncertainty

## Analysis recipe

1. **Image continuum and line cubes, moment maps**: Self-calibration, tclean, moment 0 and 1 maps  
  > "Moment 0 and 1 maps were produced over the velocity range \[$+1.2, +10$\] km s$^{-1}$, except for CO" (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Vertical intensity profiles and z/r**: Profiles across disk height from moment 0 maps, averaged over three pixels (0.18")  
  > "by averaging the emission radially over three pixels (0.18$''$, corresponding to $\sim 29$ au)" (3.1)
   - fitting: _not stated_
   - validation: Errors as standard deviation over a nine-pixel box  
  > "The errors in the figure correspond to the standard deviation obtained over a nine-pixel box." (3.1)
3. **Column densities and CH3OH/H2CO ratio**: Integrate over molecular layer (A=4.3 arcsec2) and outer midplane (A=0.41 arcsec2); convert to N  
  > "The column densities of the detected molecular species were inferred by assuming local thermodynamic equilibrium and optically thin lines." (3.3)
   - parameter: Noise = sigma0*sqrt(A/theta_beam); upper limits at 3 sigma  
  > "The noise on the line integrated emission is $\sigma_0 \times \sqrt{A/\theta_{\rm beam}}$" (Footnote 2)
   - assumption: Tex 20-100 K (layer), 10-30 K (midplane); OPR 1.8-2.8; A/E=1  
  > "The total H$_2$CO and CH$_3$OH column densities were derived assuming an ortho-to-para ratio of $1.8-2.8$" (3.3)
   - fitting: _not stated_
   - validation: A posteriori check that CH3OH intensity is consistent with expected abundance ratio  
  > "the integrated line intensity is consistent with the expectations for the \[CH$_3$OH\]/\[H$_2$CO\] abundance ratio" (3.2)

## Software

- **CASA** 4.7.2: Data reduction, self-calibration, tclean imaging  
  > "Data reduction was carried out using CASA 4.7.2." (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH integrated intensity, molecular layer | 42 | 13 | mJy km/s | 3 | / CH$_3$OH / Molecular layer / 42 (13) |
| z/r for CO | 0.41-0.45 | not stated | dimensionless | 2 | $z/r$ spans from 0.41$-$0.45 for CO |
| [CH3OH]/[H2CO] in molecular layer | 0.5-0.6 | not stated | dimensionless | 3 | the abundance ratio between CH$_3$OH and H$_2$CO is $\sim 0.5-0.6$ in the molecular layer |
| CS column density, molecular layer | 3.4-5.0e13 | not stated | cm^-2 | 3 | 3.4$-$5.0 |
| H2CO column density, molecular layer | 7.2-25e13 | not stated | cm^-2 | 3 | 7.2$-$25 |

## Qualitative findings

- CN does not show an X-shape and is detected at constant height above the midplane  
  > "the CN $2-1$ emission does not show an X-shape and is instead detected at a constant height above the midplane" (3.1)

## Claim tuples

- H: Molecules are vertically stratified in the disk | E: Vertical profiles from moment 0 maps | R: z/r 0.41-0.45 for CO vs ~0.2-0.28 for CS and H2CO | F: CO traces higher layer; CS and H2CO cospatial | **supported**
- H: CH3OH is present in a Class I disk | E: Integrated moment 0 over molecular layer | R: 42 mJy km/s at 3 sigma | F: Tentative detection | **partially**
- H: H2CO is released from icy grains in the midplane | E: Midplane vs peak intensity | R: H2CO drops only a factor ~2 vs >100 for CO and 15 for CS | F: Consistent with formation on ice and nonthermal release | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No estimates of disk temperature, so Tex assumed  
  > "As there are no estimates of the disk temperature, the excitation temperature is assumed to be 20$-$100 K" (3.3)
- Caveat (inferred, ours): CH3OH detection only 3 sigma
- Caveat (inferred, ours): Tex assumed, large column density ranges
- Caveat (inferred, ours): LTE and optically thin assumed for CS, H2CO
- Caveat (inferred, ours): Inclination uncertain (76 vs 90 deg)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Continuum and line-free channel selection
- Missing: Self-cal parameters
- Missing: Region definitions for integration
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified and imaging parameters partly given, but several processing and region details missing.
- Rediscovery candidate: no, Key CH3OH result is marginal and region definitions are incomplete.

## Links

- Method: podio19 (validity of LTE/optically thin assumptions)
- Companion: garufi20b (ALMA-DOT survey paper)
- Related: ALMA-DOT

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 32,
  "rate": 0.525
 },
 "evidence_ok": true
}
```
