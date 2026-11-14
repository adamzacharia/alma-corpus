# The formation of peptide-like molecules on interstellar dust grains

`2018MNRAS.480.3628L` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Ligterink, N. F. W. | arXiv: 1808.00742 | DOI: 10.1093/mnras/sty2066

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: How do small amides form in interstellar ice analogues, and is acetamide or N-methylformamide detectable towards IRAS 16293B?  
  > "the solid state formation of some of the smallest amides is investigated in the laboratory." (abstract)
- Target **IRAS 16293-2422B**: coordinates _not stated_; z/distance 120 pc  
  > "Due to its relative close proximity at 120 pc and high luminosity of 21 $L_{\rm \odot}$ (cite: jorgensen2016)" (4 Interstellar observations); distance from (cite: jorgensen2016)  
  > "Due to its relative close proximity at 120 pc and high luminosity of 21 $L_{\rm \odot}$ (cite: jorgensen2016)" (4 Interstellar observations)

## Data provenance

- ALMA projects: 2016.1.01150.S, 2012.1.00712.S, 2013.1.00278.S
- bands: Bands 6 and 7  
  > "these data cover large parts of the spectral ranges in ALMA Bands 6 and 7 at a spectral resolution of 0.2 km s$^{-1}$" (4.1 Observations and analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: circular restoring beam of 0.5"  
  > "The observations have a circular restoring beam of 0$.\!\!^{\prime\prime}$5" (4.1 Observations and analysis)
- max recoverable scale: _not stated_
- sensitivity: rms 0.5–5 mJy beam-1 km s-1  
  > "high rms sensitivity of 0.5–5 mJy beam$^{-1}$ km s$^{-1}$" (4.1 Observations and analysis)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS survey plus Taquet et al. (subm.) data  
  > "data from the Protostellar Interferometric Line Survey (cite: jorgensen2016), supplemented by data from Taquet et al. (subm., project-id: 2016.1.01150.S)" (4.1 Observations and analysis)
- External data: Rotational spectroscopy of acetamide (lowest three vibrational states)  
  > "The rotational spectroscopic data of the lowest three vibrational states of CH$_{3}$C(O)NH$_{2}$ are provided by (cite: ilyushin2004)" (4.1 Observations and analysis) [from (cite: ilyushin2004)]
- External data: Rotational spectroscopy of CH3NHCHO  
  > "the rotational spectroscopy of CH$_{3}$NHCHO is given by (cite: belloche2017), respectively" (4.1 Observations and analysis) [from (cite: belloche2017)]
- External data: NH2CHO and CH3NCO column densities towards IRAS 16293B  
  > "Comparisons are made with HNCO (3$\times$10$^{16}$ cm$^{-2}$), NH$_{2}$CHO (cite: coutens2016), CH$_{3}$NCO (cite: ligterink2017a) and H$_{2}$ (cite: jorgensen2016)." (4.2 Results) [from (cite: coutens2016; ligterink2017a; jorgensen2016)]

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

- Fixed Tex of 100 and 300 K for the column density grid  
  > "We therefore run our grid of synthetic spectra at fixed temperatures of 100 and 300 K, similar to (cite: coutens2016) and (cite: ligterink2017a)." (4.2 Results) [from (cite: coutens2016; ligterink2017a)]
- ALMA data from the PILS survey  
  > "data from the Protostellar Interferometric Line Survey (cite: jorgensen2016)" (4.1 Observations and analysis) [from (cite: jorgensen2016)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (delegated to PILS paper)
- Line-free channels used for the CH3NHCHO upper limit
- Exact transitions and frequencies used
- Source size or beam filling assumed in the LTE models
- Coordinates of the offset position

## Analysis recipe

1. **Fit LTE synthetic spectra to acetamide lines**: Grid of LTE synthetic spectra, best fit by minimum chi2, at the 1-beam-offset position  
  > "making a grid of synthetic spectra, assuming Local Thermodynamic Equilibrium (LTE), and determining the best fit model based on the minimum $\chi^{2}$." (4.1 Observations and analysis)
   - software: CASSIS
   - parameter: N scanned 5e14–5e15 cm-2 in steps of 1e14; Tex fixed at 100 or 300 K; line width 1 km/s; Vlsr 2.7 km/s  
  > "Other input parameters for the synthetic spectra are kept constant, such as the line width at 1 km s$^{-1}$ and $V_{\rm lsr}$ at 2.7 km s$^{-1}$." (4.1 Observations and analysis)
   - assumption: LTE; Tex fixed because the lines cover only Eup = 112–141 K  
  > "their upper state energies only cover a small region of $E_{\rm up}$ = 112 – 141 K." (4.2 Results)
   - fitting: _not stated_
   - validation: Lines checked for blending using JPL and CDMS catalogs  
  > "are used to check for contaminating lines." (4.1 Observations and analysis)

## Software

- **CASSIS** : spectral analysis  
  > "The CASSIS line analysis software[^3] is used to analyse the spectra." (4.1 Observations and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Acetamide column density, Tex=100 K | 9e14 | not stated | cm-2 | 1 | The best-fit column densities are found to be 9$\times$10$^{14}$ and 2.5$\times$10$^{15}$ cm$^{-2}$ for $T_{\rm ex}$ = 100 and 300 K, respectively |
| Acetamide column density, Tex=300 K | 2.5e15 | not stated | cm-2 | 1 | The best-fit column densities are found to be 9$\times$10$^{14}$ and 2.5$\times$10$^{15}$ cm$^{-2}$ for $T_{\rm ex}$ = 100 and 300 K, respectively |
| CH3NHCHO column density upper limit | <=1e15 | not stated | cm-2 | 1 | the column density is determined to be $\leq$1$\times$10$^{15}$ cm$^{-2}$ at $T_{\rm ex}$ of 100–300 K. |
| [CH3C(O)NH2]/[NH2CHO] | 0.09–0.25 | not stated | dimensionless | 1 | The resulting ratio of \[CH$_{3}$C(O)NH$_{2}$\] / \[NH$_{2}$CHO\] = 0.09–0.25 matches with abundances found towards high-mass YSOs. |

## Qualitative findings

- Acetamide tentatively detected (two unblended, two partially blended lines); N-methylformamide not detected  
  > "two unblended and two partially blended lines are identified belonging to CH$_{3}$C(O)NH$_{2}$" (4.2 Results)

## Claim tuples

- H: Acetamide is present in a low-mass protostar at abundances like high-mass sources | E: LTE fit of PILS spectra towards IRAS 16293B | R: Column density 9e14–2.5e15 cm-2; ratio to formamide 0.09–0.25 | F: Tentative detection with abundance comparable to high-mass sources | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lines are weak and sensitive to baseline fluctuations, so Tex cannot be fitted  
  > "The lines are low in intensity and therefore quite sensitive to baseline fluctuations." (4.2 Results)
- Caveat (inferred, ours): Tentative detection from few lines with fixed Tex
- Caveat (inferred, ours): Lab to observation comparison relies on adopted cross sections of other molecules

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Processing details of the PILS data
- Missing: Line list used
- Data volume (inferred): Large (PILS Bands 6 and 7 datasets, hundreds of GB)
- Score (inferred): 3/5, ALMA analysis is brief and partly inherited from PILS; lab part dominates.
- Rediscovery candidate: no, ALMA recipe is incomplete and the main results are laboratory data.

## Links

- Method: (cite: jorgensen2016) (PILS survey data and H2 column density)
- Companion: (cite: ligterink2017a) (Companion CH3NCO study)
- Related: PILS

## Checks

```json
{
 "quotes": 28,
 "quotes_ok": 28,
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
  "facts": 56,
  "stated": 19,
  "rate": 0.339
 },
 "evidence_ok": true
}
```
