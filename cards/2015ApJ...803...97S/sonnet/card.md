# An ALMA Imaging Study of Methyl Formate (HCOOCH<SUB>3</SUB>) in Torsionally Excited States toward Orion KL

`2015ApJ...803...97S` | The Astrophysical Journal 2015 | first author: Sakai, Yusuke | arXiv: 1503.07397 | DOI: 10.1088/0004-637X/803/2/97

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Do rotational and vibrational (torsional) temperatures of methyl formate differ in Orion KL Compact Ridge and Hot Core when resolved with ALMA, unlike the earlier single-dish result?  
  > "In this study, high spatial resolution analysis by using Atacama Large Millimeter/Submillimeter Array (ALMA) science verification data was carried out to verify and understand this difference." (abstract)
- Target **Orion KL (Compact Ridge and Hot Core)**: coordinates Tracking center 05h35m14.35s, -05d22m35.0s (J2000)  
  > "The tracking center position of Orion KL was set to be R.A. = 05$^{h}$35$^{m}$14.35s and decl.=-05$^\circ$22$'$35.$''$ 0 (J2000)." (Observations); "The center coordinates of the Compact Ridge and Hot Core are (R.A.(J2000), decl.(J2000))= (05h35m14s.10, -05$^{\circ}$22$'$36$''$.7) and (05h35m14s.45, -05$^{\circ}$22$'$34$''$.8), respectively." (Spatial Distribution and Channel Maps); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (215-245 GHz)  
  > "The band 6 (215-245 GHz) covers the 1 mm wavelength region." (Observations)
- frequencies and spectral setup: 20 spectral settings; correlator resolution 488 kHz (0.60-0.65 km/s)  
  > "The data consist of 20 spectral settings and the net on-source time for each setting was about 20 minutes." (Observations); "The spectral resolution of the ALMA correlator was 488 kHz, which corresponds to the velocity resolution of 0.60-0.65 km s$^{-1}$ at the observed frequency range." (Observations)
- continuum bandwidth: _not stated_
- arrays: 16 x 12 m antennas  
  > "The baseline lengths ranged from 17 to 265 m and consisted of 16 $\times$ 12 m antennas." (Observations)
- configurations: _not stated_
- baselines: 17 to 265 m  
  > "The baseline lengths ranged from 17 to 265 m and consisted of 16 $\times$ 12 m antennas." (Observations)
- angular resolution: 1.7" x 1.4", PA 171 deg (natural weighting)  
  > "The natural-weighted beam size was 1.7$''$ $\times$ 1.4$''$ with the position angle of 171$^\circ$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.01-0.05 Jy/beam per channel  
  > "The resultant typical rms (root-mean square) noise level is 0.01-0.05 Jy beam$^{-1}$ for each channel map." (Observations)
- time on source: about 20 min per setting  
  > "The data consist of 20 spectral settings and the net on-source time for each setting was about 20 minutes." (Observations)
- observing dates: _not stated_
- pi or archival as stated: Public ALMA science verification data  
  > "The public spectral line survey data, ALMA SV toward the Orion KL, was used in this study." (Observations)
- Line: HCOOCH3 v_t=0,1,2 rotational lines (e.g. 18_2,16-17_2,15 E) (216830.129 MHz (example))
- External data: Rest frequencies of v_t=0,1 (lab data set)  
  > "The data set is from (cite: ily09) which includes the data by (cite: bro75), (cite: bau79)" (Analysis of the spectral lines) [from (cite: ily09)]
- External data: Rest frequencies in v_t=2  
  > "The rest frequencies in $v_{t}$=2 were taken from (cite: mae08) and (cite: kob13)." (Analysis of the spectral lines) [from (cite: mae08); (cite: kob13)]
- External data: Torsional energies 132 cm-1 (v_t=1) and 250 cm-1 (v_t=2)  
  > "$\Delta E$=132 cm$^{-1}$ (cite: tud12) and $\Delta E$=250 cm$^{-1}$ (cite: sen05) were assumed for $v_{t}=$1 and 2, respectively" (Partition Functions) [from (cite: tud12); (cite: sen05)]
- External data: A-sublevel rotational constants  
  > "The A sublevel rotational constants given by (cite: bau79) were used to calculate Equation (1)." (Partition Functions) [from (cite: bau79)]

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

- task: CASA  
  > "The data were analyzed by using the Common Astronomy Software Applications (CASA) package." (Observations)
- deconvolver: Hogbom  
  > "The Hogbom algorithm was used for the clean." (Observations)
- weighting robust: natural weighting  
  > "The natural-weighted beam size was 1.7$''$ $\times$ 1.4$''$ with the position angle of 171$^\circ$." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: first-order fit to line-free channels  
  > "A first order fit to the line-free channels was used to estimate the continuum emission removal." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.7" x 1.4", PA 171 deg  
  > "The natural-weighted beam size was 1.7$''$ $\times$ 1.4$''$ with the position angle of 171$^\circ$." (Observations)
- final rms: 0.01-0.05 Jy/beam per channel  
  > "The resultant typical rms (root-mean square) noise level is 0.01-0.05 Jy beam$^{-1}$ for each channel map." (Observations)

### Inherited from earlier work

- Rotation diagram method  
  > "the conventional rotation diagram method is employed (cite: tur91)" (Rotation Diagrams) [from (cite: tur91)]
- Intensity convention in rotation diagram same as Favre et al.  
  > "which is the same as that of (cite: fav14)" (Partition Functions) [from (cite: fav14)]
- Analytic rotational partition function  
  > "The rotational partition function was calculated by using the analytical rotational partition function, which is shown below (cite: tur91)." (Partition Functions) [from (cite: tur91)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration (SV data products used?) details
- Line-free channel ranges and continuum fit per setting
- Clean mask, image size, cell size, number of iterations/threshold
- Spectrum extraction aperture (green circle size) for Compact Ridge and Hot Core
- Gaussian fitting procedure and uncertainty derivation for line parameters
- Rotation diagram fitting method (weights, treatment of errors, beam filling)
- Flux calibration uncertainty
- Source distance/column density equation details and whether continuum was corrected for optical depth

## Analysis recipe

1. **Image cubes and remove continuum**: CASA imaging with Hogbom clean, natural weighting; linear continuum fit to line-free channels  
  > "A first order fit to the line-free channels was used to estimate the continuum emission removal. The Hogbom algorithm was used for the clean." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify methyl formate lines and check blending**: Match to lab rest frequencies; check overlap using Splatalogue; classify B/NB/ND  
  > "Any possible overlap of other lines was examined based on the molecular line database, Splatalogue (cite: rem07)." (Analysis of the spectral lines)
   - software: Splatalogue, JPL catalogue
   - parameter: NB if contaminant weaker than ~10% of methyl formate line  
  > "When the intensity of the contaminated line is weaker than about 10% of the methyl formate line, it was considered to be no blend." (Analysis of the spectral lines)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map distributions and extract line parameters**: Integrated intensity maps 4-12 km/s; Gaussian fits to spectra of Compact Ridge and Hot Core giving T, FWHM, VLSR, W  
  > "The spectra of the Hot Core can be fitted by a single Gaussian and the center of velocity is about 7.3  km s$^{-1}$." (Spatial Distribution and Channel Maps)
   - fitting: Single Gaussian for Hot Core; two components for Compact Ridge  
  > "there are two velocity components at the Compact Ridge corresponding to $V_{LSR}$ of about 7.3 km s$^{-1}$ and 9.1 km s$^{-1}$" (Spatial Distribution and Channel Maps)
   - validation: Compared with MF1/MF2 of Favre et al. 2011  
  > "In the paper by (cite: fav11), the Compact Ridge corresponds to MF1 and the Hot Core corresponds to MF2." (Spatial Distribution and Channel Maps)
4. **Compute partition function**: Q = Q_rot Q_tor with analytic Q_rot and sum over torsional states up to v_t=2  
  > "The partition function used in this study was $Q=Q_{rot}Q_{tor}$." (Partition Functions)
   - assumption: Same torsional energies for A and E sublevels  
  > "for Equation (2), $\Delta E$=132 cm$^{-1}$ (cite: tud12) and $\Delta E$=250 cm$^{-1}$ (cite: sen05) were assumed for $v_{t}=$1 and 2, respectively, for both the A and E sublevels." (Partition Functions)
   - fitting: _not stated_
   - validation: Compared with JPL direct sum and Favre et al. 2014; within 1% at 9.375 K  
  > "our adopted simple and easy-to-calculate model is within a 1$\%$ error even at 9.375 K." (Partition Functions)
5. **Rotation diagrams: temperatures and column densities**: Rotation diagrams per component, per torsional state (T_rot) and all states combined (T_eff = T_vib); LTE; optically thick lines excluded  
  > "We set the criteria to exclude lines with $S\mu^{2} \geq 35$ in $v_{t}$=0 for the 7.3 km s$^{-1}$ component in the Compact Ridge and Hot Core to avoid the optically thick transitions." (Rotation Diagrams)
   - parameter: Blended lines also removed  
  > "Therefore, optically thick transitions and contaminated transitions were removed to determine the rotational temperature and vibrational temperature." (Rotation Diagrams)
   - assumption: LTE, optically thin after exclusion; tau~2 at Smu2~35 assuming 150 K  
  > "Assuming a temperature of 150 K, which may be a little higher for the Compact Ridge but reasonable for the Hot Core, optical depths $\tau$ of a few lines were calculated and they were about two." (Rotation Diagrams)
   - fitting: _not stated_
   - validation: Removal of optically thick lines improved fit; compared with Favre 2011/2014 and Takano 2012  
  > "Removal of the optically thick transitions improved the quality of the fit." (Rotation Diagrams)

## Software

- **CASA** : Data analysis and imaging  
  > "The data were analyzed by using the Common Astronomy Software Applications (CASA) package." (Observations)
- **Splatalogue** : Checking line overlap  
  > "Any possible overlap of other lines was examined based on the molecular line database, Splatalogue (cite: rem07)." (Analysis of the spectral lines)
- **JPL catalogue** : Line assignment and partition function comparison  
  > "the assignment was done based on the JPL catalogue (cite: pik98)" (Analysis of the spectral lines)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Effective temperature, Compact Ridge, 7.3 km/s component | 99.6 | 8.1 | K | 5 | 7.3 km s$^{-1}$ component / 146$\pm$17 / 153$\pm$20 / 219$\pm$56 / 99.6$\pm$8.1 / 1.11$\pm$0.31$\times10^{18}$ |
| Rotational temperature v_t=0, Compact Ridge 7.3 km/s | 146 | 17 | K | 5 | 7.3 km s$^{-1}$ component / 146$\pm$17 / 153$\pm$20 / 219$\pm$56 |
| Effective temperature, Compact Ridge 9.1 km/s | 86.8 | 4.1 | K | 5 | 9.1 km s$^{-1}$ component / 82.9$\pm$3.7 / 93$\pm$14 / 97$\pm$28 / 86.8$\pm$4.1 / 3.42$\pm$0.79$\times10^{17}$ |
| Effective temperature, Hot Core | 119.9 | 9.2 | K | 5 | Hot Core / 162$\pm$26 / 153$\pm$24 / \- / 119.9$\pm$9.2 / 6.0$\pm$1.6$\times10^{17}$ |
| Column density, Compact Ridge 7.3 km/s | 1.11e18 | 0.31e18 | cm-2 | 5 | 99.6$\pm$8.1 / 1.11$\pm$0.31$\times10^{18}$ |
| Column density, Compact Ridge 9.1 km/s | 3.42e17 | 0.79e17 | cm-2 | 5 | 86.8$\pm$4.1 / 3.42$\pm$0.79$\times10^{17}$ |
| Column density, Hot Core | 6.0e17 | 1.6e17 | cm-2 | 5 | 119.9$\pm$9.2 / 6.0$\pm$1.6$\times10^{17}$ |
| Number of methyl formate transitions found in v_t=0,1,2 | 84, 68, 62 | not stated | dimensionless | 2 | Briefly, 84, 68, and 62 transitions were found to be due to the transitions of methyl formate in $v_{t} =$0, 1 and 2, respectively. |

## Qualitative findings

- Intensity maps of v_t=0,1,2 have similar distributions with peaks on Compact Ridge and Hot Core  
  > "The intensity maps in the ground, first, and second torsional excited states have quite similar distributions." (abstract)

## Claim tuples

- H: Do Compact Ridge and Hot Core show distinct velocity structure in methyl formate? | E: Gaussian fits of ALMA SV spectra | R: Compact Ridge has 7.3 and 9.1 km/s components; Hot Core only 7.3 | F: Velocity components confirmed | **supported**
- H: Is T_vib higher than T_rot as found with single dish? | E: Rotation diagrams with ALMA lines | R: T_rot and T_vib agree for Hot Core and CR 9.1; T_rot > T_vib for CR 7.3 | F: Single-dish difference not reproduced; likely beam dilution/narrow Eu range | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Conventional rotation diagram with partition function including v_t up to 2  
  > "Therefore, we calculated the partition function up to $v_{t} =$2 as discussed above." (Partition Functions)
- How they decided it was enough: _not stated_
- Limitation (authors): Many lines blended; Hot Core v_t=2 T_rot not determinable  
  > "It was not possible to determine the realistic rotational temperature of HCOOCH$_{3}$ in $v_{t} =$2 for the Hot Core." (Rotation Diagrams)
- Caveat (inferred, ours): LTE and single-temperature assumption with beam size ~1.7" comparable to source separation
- Caveat (inferred, ours): Uncertainties from Gaussian fits and blending not fully described
- Caveat (inferred, ours): No continuum/optical-depth correction beyond line exclusion

## Reproducibility

- Data public (paper): Public ALMA SV data  
  > "The public spectral line survey data, ALMA SV toward the Orion KL, was used in this study." (Observations)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Extraction regions
- Missing: Fitting method details for rotation diagrams
- Data volume (inferred): Tens of GB (20 spectral settings of SV data)
- Score (inferred): 3/5, Public data and line tables given, but imaging and fitting details sparse.
- Rediscovery candidate: yes, Public data, line tables with measured values, and numeric temperatures/column densities; recipe moderately complete.

## Links

- Method: (cite: tur91) (Rotation diagram method and rotational partition function)
- Method: (cite: kob13) (v_t=2 laboratory spectroscopy and partition function)
- Companion: (cite: tak12) (Single-dish detection of v_t=2 with Nobeyama)
- Companion: (cite: fav14) (ALMA SV survey of methyl formate)
- Related: ALMA Science Verification Orion KL

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
