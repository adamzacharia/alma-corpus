# First detection of cyanamide (NH<SUB>2</SUB>CN) towards solar-type protostars

`2018A&A...612A.107C` | Astronomy and Astrophysics 2018 | first author: Coutens, A. | arXiv: 1712.09548 | DOI: 10.1051/0004-6361/201732346

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is cyanamide (NH2CN) and its isotopologues present in the warm gas around solar-type protostars, what are its abundance and deuteration, and can grain-surface NH2 + CN chemistry explain it?  
  > "We here present the first detection of this species in the warm gas surrounding two solar-type protostars" (abstract)
- Target **IRAS 16293-2422 B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1333 IRAS2A**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: _not stated_
- frequencies and spectral setup: 329.1-362.9 GHz, ~0.2 km/s resolution (ALMA PILS); PdBI IRAS2A: 223.5-227.1, 240.2-243.8, 315.5-319.1 GHz, 1.95 MHz resolution (WIDEX)  
  > "observed in Cycle 2 between 329.1 and 362.9 GHz at a spatial resolution of about 0.5$\ensuremath{''}$ and a spectral resolution of $\sim$0.2 km s$^{-1}$" (Observations); "They cover the spectral ranges 223.5–227.1, 240.2–243.8, and 315.5–319.1 GHz with a spectral resolution of 1.95 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5'' (ALMA); about 1.2x1.0'' at 225 GHz, 1.4x1.0'' at 242 GHz, 0.9x0.8'' at 317 GHz (PdBI)  
  > "The angular resolution is about 1.2$\ensuremath{''}$ $\times$ 1.0$\ensuremath{''}$ at 225 GHz" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 4-5 mJy/beam km/s (ALMA); ~5-6 mJy/beam km/s or lower (PdBI)  
  > "The data reach a sensitivity of about 4–5 mJy beam$^{-1}$ km s$^{-1}$." (Observations)
- time on source: _not stated_
- observing dates: ALMA Cycle 2  
  > "observed in Cycle 2 between 329.1 and 362.9 GHz" (Observations)
- pi or archival as stated: _not stated_
- Line: NH2CN e.g. 18 1 17 0 - 17 1 16 0 (eleven unblended lines) (362143.5 MHz)
- Line: NHDCN eight unblended lines (336337.6-358488.3 MHz)
- Line: NH2(13)CN three lines (361997.1 MHz)
- Line: HNCNH not detected (223.7918 GHz)
- Other facility **IRAM PdBI**: WIDEX spectra of NGC1333 IRAS2A  
  > "The PdBI data of the low-mass protostar IRAS2A were obtained with the WIDEX correlator" (Observations)
- Other facility **CALYPSO**: 216.8-220.4 GHz line list used to confirm IRAS2A detection  
  > "list of lines observed in the spectral range 216.8–220.4 GHz covered by the CALYPSO program" (3.1)
- External data: H2 column density lower limit for IRAS16293 B  
  > "the lower limit of the H$_2$ column density derived by (cite: Jorgensen2016)" (3.3) [from (cite: Jorgensen2016)]
- External data: H2 column density for IRAS2A, and NH2CHO column density  
  > "Using the H$_2$ column density derived by (cite: Taquet2015) for IRAS2A" (3.3) [from (cite: Taquet2015)]
- External data: 12C/13C ratio of 68  
  > "assuming a standard $^{12}$C/$^{13}$C ratio of 68 (cite: Milam2005)" (3.2) [from (cite: Milam2005)]
- External data: Tex ~130 K and source size ~0.5'' for IRAS2A  
  > "An excitation temperature of $\sim$130 K and a source size of $\sim$0.5$\ensuremath{''}$ were derived from the analysis of other complex organics towards this source by (cite: Coutens2015)." (3.1) [from (cite: Coutens2015)]
- External data: Unidentified lines of CALYPSO  
  > "Unidentified lines from (cite: Maury2014) (their Table 1) that can be assigned to NH$_2$CN." (Table 5) [from (cite: Maury2014)]
- Simulation/model as data: MAGICKAL three-phase chemical model with final densities 6e10 and 1.6e7 cm-3, warm-up to 400 K  
  > "we ran a three-phase chemical kinetics model MAGICKAL (cite: Garrod2013), modified with the grain-surface back-diffusion correction of (cite: Willis2017)." (Discussion)

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

- ALMA PILS observations and reduction  
  > "The observations and their reduction are presented in (cite: Jorgensen2016)." (Observations) [from (cite: Jorgensen2016)]
- PdBI data reduction  
  > "The data reduction of each dataset is described in (cite: Coutens2014; Coutens2015) and (cite: Persson2014)." (Observations) [from (cite: Coutens2014; Coutens2015; Persson2014)]
- Analysis position for IRAS16293 B (full-beam offset)  
  > "at the full-beam offset position analyzed in previous studies (cite: Coutens2016; Lykke2017; Ligterink2017)" (3.1) [from (cite: Coutens2016; Lykke2017; Ligterink2017)]
- Chemical network based on Belloche et al. 2017  
  > "The model uses a network based on that of (cite: Belloche2017)" (Discussion) [from (cite: Belloche2017)]

### Not stated but needed to reproduce (our reading)

- Exact offset coordinates of the full-beam and half-beam positions
- Calibration and imaging details (in Jorgensen2016)
- Line widths/FWHM and vlsr used in the LTE models
- Fit procedure and uncertainties for column densities (by eye?)
- Source coordinates and distances
- Model parameters for MAGICKAL (warm-up timescale, reaction rates, binding energies)

## Analysis recipe

1. **Identify NH2CN lines with LTE synthetic spectra**: Compare synthetic LTE spectra with observed spectra, check blending with CDMS/JPL  
  > "Synthetic spectra were produced and compared with the observations to identify the lines." (3 Results)
   - software: CASSIS
   - parameter: IRAS16293 B: Tex 300 K, source size 0.5''; IRAS2A: Tex 130 K, size 0.5''  
  > "for an excitation temperature of 300 K ($\geq$ 5 $\times$ 10$^{13}$ cm$^{-2}$ for 100 K) and a source size of 0.5$\ensuremath{''}$" (3.1)
   - assumption: LTE valid owing to densities >~1e10 cm-3  
  > "Column densities were determined assuming local thermodynamic equilibrium (LTE)" (3 Results)
   - fitting: _not stated_
   - validation: Half-beam position checked; IRAS2A predictions compared with CALYPSO U-lines  
  > "Among the six brightest lines, five of them are in agreement with the presence of unidentified lines detected by (cite: Maury2014)" (3.1)
2. **Isotopologue column densities and D/H**: LTE models of NHDCN and NH2 13CN; D/H divided by 2 for statistics, 12C/13C=68  
  > "The D/H ratio of NH$_2$CN (corrected for statistics, i.e. divided by 2) is 1.7%" (3.2)
   - software: CASSIS
   - assumption: 12C/13C = 68  
  > "assuming a standard $^{12}$C/$^{13}$C ratio of 68 (cite: Milam2005)" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Abundances relative to H2 and NH2CHO**: Divide column densities by literature H2 column densities; NH2CHO column from optically thin lines  
  > "A simple analysis of the most optically thin NH$_2$CHO lines covered by our data suggests a column density of about 1.2 $\times$ 10$^{16}$ cm$^{-2}$" (3.3)
   - software: CASSIS
   - fitting: _not stated_
   - validation: _not stated_
4. **Grain-surface chemical modelling**: MAGICKAL run with NH2+CN added, cold collapse then warm-up to 400 K, two final densities  
  > "The reaction NH$_2$ + CN $\rightarrow$ NH$_2$CN was added to the grain/ice chemical network" (Discussion)
   - software: MAGICKAL
   - parameter: nH final = 6e10 and 1.6e7 cm-3  
  > "here, a final density $n_{\mathrm{H}}=6\times10^{10}$ cm$^{-3}$ was assumed" (Discussion)
   - fitting: _not stated_
   - validation: Compared with observed abundances and NH2CN/NH2CHO ratios  
  > "However, the resulting NH$_2$CN:NH$_2$CHO peak abundance ratio of 0.0011 is still lower than the observed values in both IRAS2A ($\sim$0.02), and IRAS 16293 ($\sim$0.2)." (Discussion)

## Software

- **CASSIS** : line identification and LTE column densities  
  > "The CASSIS$\footnote{CASSIS has been developed by IRAP-UPS/CNRS (\url{http://cassis.irap.omp.eu/}).}$ software was used to search for and identify the lines of NH$_2$CN and its isotopologues" (Results)
- **MAGICKAL** : three-phase chemical kinetics modelling  
  > "we ran a three-phase chemical kinetics model MAGICKAL (cite: Garrod2013)" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NH2CN column density, IRAS16293 B (300 K) | >= 7e13 | lower limit | cm-2 | 1 | a column density of $\geq$ 7 $\times$ 10$^{13}$ cm$^{-2}$ is derived for an excitation temperature of 300 K |
| NH2CN column density, IRAS2A (130 K) | 2.5e14 | not stated | cm-2 | 1 | a LTE model with a column density of 2.5 $\times$ 10$^{14}$ cm$^{-2}$ is in very good agreement |
| NHDCN column density, IRAS16293 B | 7e13 | not stated | cm-2 | 2 | A column density of 7 $\times$ 10$^{13}$ cm$^{-2}$ is obtained for an excitation temperature of 300 K. |
| NH2 13CN column density, IRAS16293 B | 3e13 | not stated | cm-2 | 2 | a column density of 3 $\times$ 10$^{13}$ cm$^{-2}$ is derived |
| D/H of NH2CN | 1.7 | not stated | % | 2 | is 1.7%, assuming a standard $^{12}$C/$^{13}$C ratio of 68 |
| NH2CN/NH2CHO, IRAS16293 B | ~0.2 | not stated | dimensionless | 3 | The NH$_2$CN/NH$_2$CHO abundance ratio is about 0.2. |
| NH2CN/NH2CHO, IRAS2A | ~0.02 | not stated | dimensionless | 3 | The NH$_2$CN/NH$_2$CHO ratio is consequently about 0.02 |
| NH2CN/H2 IRAS16293 B | <~2e-10 | upper limit | dimensionless | 3 | an abundance of NH$_2$CN with respect to H$_2$ of $\lesssim$ 2 $\times$ 10$^{-10}$ at 60 AU |
| Model NH2CN abundance, low-density | 3.7e-10 | not stated | dimensionless | 4 | This model produces an NH$_2$CN fractional abundance of 3.7 $\times$ 10$^{-10}$ |

## Qualitative findings

- NH2CN emission arises from warm inner regions of source B and shows deep absorption against continuum like formamide  
  > "This species also appears to be strongly affected by absorption against the strong continuum similarly to formamide" (3.1)

## Claim tuples

- H: Cyanamide is present around solar-type protostars | E: LTE line search in ALMA PILS and PdBI data | R: 11 lines toward IRAS16293 B, 3 toward IRAS2A | F: First detection of NH2CN in solar-type protostars; NHDCN first ISM detection | **supported**
- H: NH2CN and NH2CHO share a precursor | E: Compare D/H | R: D/H ~1.7% similar to formamide | F: May suggest common NH2 precursor | **partially**
- H: Grain-surface NH2 + CN forms NH2CN | E: MAGICKAL models | R: Underproduces at high density; 3.7e-10 at low density | F: Capable with correct physical parameters, but NH2CN/NH2CHO ratio underpredicted | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gas-phase CN + NH3 rejected; proceeds to HCN + NH2  
  > "An experimental study by (cite: Blitz2009) confirms that this reaction proceeds exclusively to HCN + NH$_2$." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): NH2CN column density in IRAS16293 B is a lower limit due to absorption  
  > "this column density can only be considered as a lower limit, because of the absorption components" (3.1)
- Caveat (inferred, ours): No fit uncertainties given; LTE columns by eye
- Caveat (inferred, ours): Absorption makes column densities uncertain
- Caveat (inferred, ours): Model with one network and single warm-up timescale
- Caveat (inferred, ours): IRAS2A PdBI resolution coarse, beam dilution assumed

## Reproducibility

- Data public (paper): ALMA PILS data cited by project code; PdBI project codes given  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA$\#$2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated PILS cubes details and exact extraction positions
- Missing: Line widths and velocities
- Missing: MAGICKAL network and parameters
- Data volume (inferred): Large: PILS full spectral survey, hundreds of GB raw
- Score (inferred): 3/5, Public data and tabulated lines, but LTE fits are by eye with few stated parameters and the data reduction is deferred to other papers.
- Rediscovery candidate: no, Recipe incomplete (position, line widths, fitting) and the reduction is inherited.

## Links

- Method: (cite: Jorgensen2016) (PILS observations and reduction)
- Method: (cite: Garrod2013) (MAGICKAL model)
- Companion: (cite: Coutens2016) (Formamide in IRAS16293 B)
- Companion: (cite: Coutens2015) (IRAS2A complex organics)
- Related: PILS
- Related: CALYPSO

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 33,
  "rate": 0.418
 },
 "evidence_ok": true
}
```
