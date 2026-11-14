# Deuterated methyl mercaptan (CH<SUB>3</SUB>SD): Laboratory rotational spectroscopy and search toward IRAS 16293-2422 B

`2019A&A...621A.114Z` | Astronomy and Astrophysics 2019 | first author: Zakharenko, Olena | arXiv: 1812.02454 | DOI: 10.1051/0004-6361/201834472

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: What are accurate spectroscopic parameters of CH3SD, and can it be detected toward IRAS 16293-2422 B in PILS data?  
  > "The aim of the present study is to obtain accurate spectroscopic parameters of the S-deuterated methyl mercaptan to facilitate astronomical observations by radio telescope arrays at (sub)millimeter wavelengths." (abstract)
- Target **IRAS 16293-2422 B**: coordinates _not stated_; z/distance ~141 pc  
  > "The binary is close-by at a distance of $\sim$141 pc (cite: 2018A&A...614A..20D)" (4 Observational results); distance from Dzib et al. 2018  
  > "The binary is close-by at a distance of $\sim$141 pc (cite: 2018A&A...614A..20D)" (4 Observational results)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7, 329.15-362.90 GHz  
  > "carried out in Band 7 of ALMA and covering 329.15$-$362.90 GHz at 0.244 MHz spectral resolution." (4 Observational results)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5"  
  > "at the high spatial resolution of the survey of $\sim$0.5$\ensuremath{''}$" (4 Observational results)
- max recoverable scale: _not stated_
- sensitivity: 7-10 mJy/beam/channel or 4-5 mJy/beam km/s  
  > "7$-$10 mJy beam$^{-1}$ channel$^{-1}$ or 4$-$5 mJy beam$^{-1}$ km s$^{-1}$" (4 Observational results)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Cologne mm/submm wave spectrometer**: Laboratory rotational spectra of CH3SD, 150-510 GHz  
  > "The rotational spectra have been measured in the frequency range from 150 up to 510 GHz using the Cologne mm/submm wave spectrometer." (2 Laboratory spectroscopic details)
- External data: CH3SH column density 4.8e15 cm-2 and deuteration of CH3SH ~0.05 per H atom  
  > "determined a column density of $4.8 \times 10^{15}$ cm$^{-2}$ ($\pm 0.48$)" (4 Observational results) [from (cite: 2018Drozdovskaya)]
- External data: Earlier microwave data and dipole moments of CH3SD  
  > "At the first step of our analysis, we fit the data from (cite: TSUNEKAWA198963) with the RAM36 code." (3 Spectroscopic results) [from (cite: TSUNEKAWA198963)]

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

- Survey details and data reduction of PILS  
  > "Details of the survey have been presented by (cite: 2016A&A...595A.117J)." (4 Observational results) [from (cite: 2016A&A...595A.117J)]
- Analysis approach and offset position (0.5" SW of source B) as in earlier PILS sulfur work  
  > "We analyzed the PILS data for lines of similarly to what (cite: 2018Drozdovskaya) did for ." (4 Observational results) [from (cite: 2018Drozdovskaya)]

### Not stated but needed to reproduce (our reading)

- Exact coordinates of the offset position
- Spectroscopic partition function used for CH3SD
- Software used for the column density upper limit
- Details of the PILS data reduction and continuum subtraction
- Method for deriving the upper limit (sigma level)

## Analysis recipe

1. **Fit lab rotational spectrum**: Global fit of 4905 transitions with the RAM36 rho-axis-method Hamiltonian  
  > "the rho-axis-method and the RAM36 code (cite: ILYUSHIN201026) were chosen" (3 Spectroscopic results)
   - software: RAM36
   - parameter: 78 parameters, weighted standard deviation 0.9  
  > "The full dataset has been fit using 78 parameters with overall weighted standard deviation 0.9." (3 Spectroscopic results)
   - assumption: mu_a = 1.289 D, mu_b = -0.749 D, positive D_ab  
  > "we finally adopted the choice with positive $D_{ab}$ value" (3 Spectroscopic results)
   - fitting: _not stated_
   - validation: Relative intensities compared experimentally for sign choice  
  > "The correctness of the adopted sign choice was verified experimentally by comparing the relative intensities" (3 Spectroscopic results)
2. **Upper limit on CH3SD column density in PILS**: Compare predicted line spectra with PILS data at position offset 0.5" SW from source B  
  > "A position offset by 0.5$\ensuremath{''}$ from source B in the SW direction was used in the analysis" (4 Observational results)
   - parameter: Tex = 125 K, source size 0.5", FWHM 1 km/s  
  > "We adopted an excitation temperature $T_{\rm ex} = 125$ K, a source size of 0.5$\ensuremath{''}$" (4 Observational results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive D/H upper limit**: Ratio of CH3SD upper limit to CH3SH column density, with a 1.14 dust-temperature correction  
  > "Our upper limit corresponds thus to a D/H ratio of less than $0.18 \pm 0.025$" (4 Observational results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RAM36** : Fit of torsion-rotation spectrum  
  > "We present modeling results of these data with the RAM36 program." (abstract)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3SD column density upper limit | <8.8e14 | ±0.88 | cm-2 | 2 | we derived an upper limit on its column density of $\textless 8.8 \times 10^{14}$ cm$^{-2}$ ($\pm 0.88$) |
| D/H ratio upper limit | <0.18 | ±0.025 | dimensionless | 3 | Our upper limit corresponds thus to a D/H ratio of less than $0.18 \pm 0.025$ |
| Assigned transitions | 4905 (4434 fitted frequencies) | not stated | transitions | 1 | Finally 4905 rotational transitions have been assigned for the ground, first and second excited torsional states of , which, due to blending, correspond to 4434 fitted line frequencies. |

## Qualitative findings

- CH3SD not detected in PILS; the limit is not very constraining  
  > "A first attempt to search for in the PILS data turned out to be negative." (5 Conclusion and outlook)

## Claim tuples

- H: CH3SD rotational spectrum can be modeled accurately to support astronomical searches | E: Measured 150-510 GHz spectra and fit with RAM36 | R: 4905 transitions fit with 78 parameters, weighted rms 0.9 | F: Predictions are reliable for astronomical use | **supported**
- H: CH3SD is detectable toward IRAS 16293-2422 B in PILS | E: Line search at offset position | R: No detection; N<8.8e14 cm-2 | F: D/H<~18%, not constraining versus ~5% per H in CH3SH | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Upper limit is not very constraining; deeper observations needed  
  > "Deeper interferometric observations are required in order to conclusively verify" (4 Observational results)
- Caveat (inferred, ours): Upper-limit criterion and partition function unspecified
- Caveat (inferred, ours): Assumed Tex and source size are not tested for sensitivity

## Reproducibility

- Data public (paper): PILS ALMA data cited with project ID; fit files at CDS and CDMS  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Lab line list is in CDS/CDMS but PILS reduction details are in a companion paper
- Data volume (inferred): Large (hundreds of GB for the full PILS data set; far less for a single spectrum)
- Score (inferred): 3/5, Lab part is well documented, but the ALMA analysis is brief and lacks method details.
- Rediscovery candidate: no, The ALMA recipe is incomplete and the result is only an upper limit.

## Links

- Method: (cite: 2016A&A...595A.117J) (PILS survey description)
- Method: (cite: ILYUSHIN201026) (RAM36 code)
- Companion: (cite: 2018Drozdovskaya) (CH3SH and sulfur column densities in PILS)
- Related: PILS

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 22,
  "rate": 0.349
 },
 "evidence_ok": true
}
```
