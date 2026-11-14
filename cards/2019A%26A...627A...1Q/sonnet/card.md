# Formation of interstellar propanal and 1-propanol ice: a pathway involving solid-state CO hydrogenation

`2019A&A...627A...1Q` | Astronomy and Astrophysics 2019 | first author: Qasim, D. | arXiv: 1905.07801 | DOI: 10.1051/0004-6361/201935217

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can 1-propanol ice form via CO + H hydrogenation combined with C2H2 and propanal hydrogenation, and what upper limit on 1-propanol:propanal does ALMA place toward IRAS 16293-2422B?  
  > "we investigated in the laboratory whether 1-propanol ice can be formed along pathways possibly relevant to the prestellar core phase." (abstract)
- Target **IRAS 16293-2422B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01150.S
- bands: Band 6 (233-236 GHz)  
  > "in Band 6 at 233 - 236 GHz." (Astrophysical implications)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "We use the 12m array ALMA data from the work by (cite: taquet2018linking)" (Astrophysical implications)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: circular Gaussian beam fixed to 0.5"  
  > "These observations have a circular Gaussian beam fixed to 0.5” and with a 1$\sigma$ rms sensitivity" (Astrophysical implications)
- max recoverable scale: _not stated_
- sensitivity: 1.2-1.4 mJy/beam per 0.156 km/s channel (1 sigma)  
  > "1$\sigma$ rms sensitivity of 1.2 - 1.4 mJy beam$^{-1}$ per 0.156 km s$^{-1}$ channel" (Astrophysical implications)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: data from Taquet et al. 2018 (program 2016.1.01150.S)  
  > "We use the 12m array ALMA data from the work by (cite: taquet2018linking)" (Astrophysical implications)
- Line: 1-propanol deepest-constraint transition (236.138 GHz)
- External data: Propanal column density 2.2e15 cm-2 at 125 K toward IRAS 16293-2422B  
  > "propanal column density of $2.2 \times 10^{15}$ cm$^{-2}$ found by (cite: lykke2017alma) for 125 K" (Astrophysical implications) [from (cite: lykke2017alma)]
- External data: 1-propanol spectroscopic data  
  > "The spectroscopic data of the 1-propanol molecule are provided by (cite: kisiel2010determination)." (Astrophysical implications) [from (cite: kisiel2010determination)]

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
- continuum subtraction: baseline correction by fit over line-free regions around 236.138 GHz  
  > "obtained after a baseline correction through a fit over the line-free regions around 236.138 GHz." (Astrophysical implications)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data and spectra extraction position (1 beam SW of source B continuum)  
  > "The observed and predicted spectra of the four spectral windows towards the full-beam offset position are shown in the Appendix of (cite: taquet2018linking)." (Astrophysical implications) [from (cite: taquet2018linking)]
- Excitation temperatures 300 and 125 K  
  > "excitation temperatures of 300 and 125 K, following previous ALMA observations of other COMs towards this source (cite: jorgensen2018alma)" (Astrophysical implications) [from (cite: jorgensen2018alma)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details of the ALMA data (in Taquet et al. 2018)
- Source position, linewidth and source size/beam filling used in LTE modelling
- Software used for the LTE spectral simulation
- Partition function and noise level used to define the upper limit
- Exact 1-propanol conformers included

## Analysis recipe

1. **Derive 1-propanol column density upper limit**: Simulate LTE optically thin 1-propanol spectrum and compare with observed spectrum; use synthetic transition at 236.138 GHz to set the highest column density consistent with non-detection  
  > "which are the highest column densities that still result in a non-detection of 1-propanol." (Astrophysical implications)
   - parameter: Tex = 300 and 125 K  
  > "assuming optically thin emission and excitation temperatures of 300 and 125 K" (Astrophysical implications)
   - assumption: LTE, optically thin emission  
  > "assuming conditions at the Local Thermal Equilibrium (LTE) and assuming optically thin emission" (Astrophysical implications)
   - fitting: _not stated_
   - validation: Checked that other bright 1-propanol lines are not detected  
  > "We verified that other “bright" 1-propanol lines are not detected in our observed spectrum" (Astrophysical implications)
2. **Compute 1-propanol:propanal ratio**: Divide upper limits by propanal column density from Lykke et al. 2017  
  > "this results in a 1-propanol:propanal upper limit of $< 0.55$ ($T_{\rm ex} = 300$ K) and $< 0.35$ ($T_{\rm ex} = 125$ K)." (Astrophysical implications)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1-propanol column density upper limit (Tex=300 K) | 1.2e15 | not stated | cm-2 | 1 | At 300 and 125 K, 1-propanol column densities of $1.2 \times 10^{15}$ cm$^{-2}$ and $7.6 \times 10^{14}$ cm$^{-2}$ are derived, respectively |
| 1-propanol column density upper limit (Tex=125 K) | 7.6e14 | not stated | cm-2 | 1 | At 300 and 125 K, 1-propanol column densities of $1.2 \times 10^{15}$ cm$^{-2}$ and $7.6 \times 10^{14}$ cm$^{-2}$ are derived, respectively |
| 1-propanol:propanal ratio upper limit | <0.55 (300 K), <0.35 (125 K) | not stated | dimensionless | 2 | 1-propanol:propanal upper limit of $< 0.55$ ($T_{\rm ex} = 300$ K) and $< 0.35$ ($T_{\rm ex} = 125$ K) |
| Activation energy HCO + C2H2 | 4290 | not stated | K | 0 | We find the activation energy for the reaction $\hbox{HCO + C$_2$H$_2$} \rightarrow \hbox{HCCHCHO}$ to be 4290 K |

## Qualitative findings

- Propanal forms from C2H2 + CO + H co-deposition at 10 K and hydrogenation of propanal yields 1-propanol  
  > "We show that the hydrogenation of propanal ice leads to 1-propanol formation." (Conclusions)

## Claim tuples

- H: 1-propanol can form via propanal hydrogenation and radical recombination in CO + C2H2 + H ices | E: TPD-QMS and RAIRS of ice experiments at 10 K | R: Propanal detected in C2H2+CO+H; 1-propanol clearly formed from propanal + H, only tentative from C2H2+CO+H | F: HCO + H2CCH / H3CCH2 most likely route | **supported**
- H: 1-propanol:propanal ratio in IRAS 16293-2422B is consistent with a barrier on propanal hydrogenation | E: LTE upper limit on 1-propanol from ALMA spectra compared to literature propanal | R: ratio <0.35-0.55 | F: consistent with experiments and theory | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radical–molecule reactions and propynal routes excluded due to high barriers  
  > "Radical–molecule reactions, such as those between the HCO radical and C$_2$H$_2$ or C$_2$H$_4$ molecules, can also be excluded due to their high activation barriers." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): 1-propanol detection from C2H2+CO+H is just at the detection limit  
  > "the detection of 1-propanol starting from a propanal-poor sample is just around the limit of our detection capabilities." (Results)
- Caveat (inferred, ours): Upper limit depends on assumed Tex and line blending; no formal noise-based limit described
- Caveat (inferred, ours): Propanal column from a different dataset/beam used for the ratio

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced ALMA data/spectra and LTE modelling code
- Missing: Detailed line-fit settings
- Data volume (inferred): tens to hundreds of GB for the full 2016.1.01150.S dataset
- Score (inferred): 3/5, ALMA part is small and relies on Taquet et al. 2018 processing; LTE parameters partly given.
- Rediscovery candidate: no, ALMA analysis details are incomplete, and the main results are lab-based.

## Links

- Method: (cite: taquet2018linking) (Source of ALMA data and spectra analysis)
- Method: (cite: jorgensen2018alma) (Excitation temperatures adopted)
- Companion: (cite: lykke2017alma) (Propanal column density for IRAS 16293-2422B)
- Related: ALMA-PILS

## Checks

```json
{
 "quotes": 28,
 "quotes_ok": 28,
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
  "facts": 58,
  "stated": 19,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
