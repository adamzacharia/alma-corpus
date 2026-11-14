# Unveiling the gas phase H<SUB>2</SUB>NCO radical: Laboratory rotational spectroscopy and interstellar searches in the direction of IRAS 16293-2422

`2024A&A...687A.233M` | Astronomy and Astrophysics 2024 | first author: Martin-Drumel, Marie-Aline | arXiv: 2406.01796 | DOI: 10.1051/0004-6361/202449711

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can the gas-phase rotational spectrum of the H2NCO radical be measured in the laboratory and used to search for the radical toward IRAS 16293-2422 in PILS data?  
  > "In order to enable interstellar searches of , we have undertaken a mandatory laboratory characterisation of its pure rotational spectrum." (abstract)
- Target **IRAS 16293-2422 B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7 (329-363 GHz)  
  > "in band 7" (Astrochemical implications); "This survey, which covers the spectral range 329–363 GHz" (Astrochemical implications)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array and ACA  
  > "with the Atacama Large millimetre/submillimetre Array (ALMA) 12 m array and the Atacama Compact Array (ACA) in band 7" (Astrochemical implications)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 arcsec  
  > "It has a spatial resolution of $\sim$0.5$\ensuremath{''}$" (Astrochemical implications)
- max recoverable scale: _not stated_
- sensitivity: 4–5 mJy/beam per 1 km/s bin  
  > "a sensitivity of 4–5 mJy beam$^{-1}$ for a bin width of 1 km s$^{-1}$" (Astrochemical implications)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H2NCO a-type R-branch, N''=15(5,10/11) (342.957 and 343.059 GHz)
- Line: H2NCO N''(J'')=15(6,9/10)(15.5) (~343.109 GHz)
- External data: NH2CHO and HNCO column densities (1.0e16 and 2.7e16 cm-2) toward IRAS16293 B  
  > "found column densities of NH$_2$CHO and HNCO equal to 1.0 $\times$ 10$^{16}$ and 2.7 $\times$ 10$^{16}$ cm$^{-2}$, respectively" (Astrochemical implications) [from (cite: coutens2016:ALMAPILS)]
- External data: 12C/13C ratio of 68  
  > "a $^{12}$C/$^{13}$C ratio of 68 (cite: Milam2005)" (Astrochemical implications) [from (cite: Milam2005)]
- Simulation/model as data: Nautilus 3-phase chemical model of IRAS16293 B (cold core then collapse)  
  > "which uses the Nautilus code (cite: RN7545)—a 3-phase gas, dust grain ice surface, and dust grain ice mantle time dependent chemical model" (Astrochemical implications)

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

- PILS data, spectrum extraction position and LTE search follow earlier molecular studies  
  > "compared to the spectrum extracted at the same position as the previous molecular studies" (Astrochemical implications) [from (cite: coutens2016:ALMAPILS); (cite: Jorgensen2016)]
- Chemical model as used in earlier work, initial abundances and collapse phase from Manigand2021  
  > "the same initial abundances than in (cite: Manigand2021)" (Astrochemical implications) [from (cite: RN11273; Manigand2021)]

### Not stated but needed to reproduce (our reading)

- Exact offset coordinates of the extraction position
- ALMA calibration and imaging details of the PILS data (in Jorgensen2016)
- Noise rms used for upper limits and the criteria for the limits
- Beam-dilution treatment
- Whether the 12 m and ACA data were combined

## Analysis recipe

1. **LTE spectral search and upper limits**: LTE models from CASSIS compared to the PILS spectrum; brightest uncontaminated lines used for column density upper limits  
  > "Local thermodynamic equilibrium (LTE) models were produced with the CASSIS software" (Astrochemical implications)
   - software: CASSIS
   - parameter: linewidth 1 km/s, source size 0.5 arcsec, vLSR 2.7 km/s, Tex 125 and 300 K  
  > "The models assume a linewidth of 1 km s$^{-1}$, a source size of 0.5$\ensuremath{''}$ and a $\varv_{\rm LSR}$ of 2.7 km s$^{-1}$" (Astrochemical implications)
   - assumption: Tex between 125 K and 300 K  
  > "The excitation temperatures of complex organic molecules vary in this source between $\sim$125 K and 300 K" (Astrochemical implications)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare abundance limit with chemical model**: Compare upper limit with Nautilus model abundances  
  > "we compare the upper limit derived above to the calculated abundance obtained using the model" (Astrochemical implications)
   - software: Nautilus
   - parameter: density 2.5e4 cm-3, 10 K, Av 10 mag, zeta 1.3e-17 s-1  
  > "homogeneous gas with a density equal to $2.5\times10^4$ cm$^{-3}$; temperature of 10 K for both gas and dust" (Astrochemical implications)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : LTE modelling of PILS spectrum  
  > "Local thermodynamic equilibrium (LTE) models were produced with the CASSIS[^1] software" (Astrochemical implications)
- **Nautilus** : gas-grain chemical model  
  > "which uses the Nautilus code (cite: RN7545)" (Astrochemical implications)
- **PGOPHER** : line search and assignment in lab spectra  
  > "We used the PGOPHER program (cite: western2017:PGOPHER) to search for, and assign, transitions" (Assignments and fit)
- **CALPGM (SPFIT/SPCAT)** : final fit and predictions  
  > "The final fit and spectral predictions were performed with the Pickett CALPGM suite of programs" (Assignments and fit)
- **Gaussian 16** Revision A.01: quantum chemical calculations  
  > "All calculations were performed using the GAUSSIAN 16 suite of electronic structure programs" (Quantum chemical calculations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2NCO column density upper limit, Tex~300 K | 1.7e14 | not stated | cm-2 | 1 | the upper limit is estimated to be about 1.7 $\times$ 10$^{14}$ cm$^{-2}$ |
| H2NCO column density upper limit, Tex~125 K | 8.0e13 | not stated | cm-2 | 1 | found a very close upper limit of 8.0 $\times$ 10$^{13}$ cm$^{-2}$ |
| NCO upper limit (300 K / 125 K) | 7e14 / 5e14 | not stated | cm-2 | 1 | an upper limit of 7 $\times$ 10$^{14}$ cm$^{-2}$ for $T_{\rm ex}$ = 300 K and 5 $\times$ 10$^{14}$ cm$^{-2}$ for $T_{\rm ex}$ = 125 K |
| Lab fit rms | 107 | not stated | kHz | 0 | The fit takes a root-mean-square value of 107 kHz and a reduced standard deviation of 0.84. |

## Qualitative findings

- H2NCO is not detected; abundance is at least 60 times below formamide and 160 times below HNCO, consistent with the chemical model  
  > "The inferred upper limit shows that abundance is at least 60 times below that of formamide and 160 times below that of HNCO in this source" (abstract)

## Claim tuples

- H: Is H2NCO detectable in PILS toward IRAS16293 B with the new catalogue? | E: LTE search with CASSIS at Tex 125-300 K | R: No lines above noise; N upper limits 8e13-1.7e14 cm-2 | F: Not detected; at least 60x less abundant than formamide | **supported**
- H: Is the non-detection consistent with a physico-chemical model? | E: Nautilus model comparison | R: Radicals are destroyed on grains before desorption | F: Consistent with model | **supported**

## Reasoning

- Why this data: IRAS16293 B is a source where formamide and related molecules were already detected  
  > "A search for the H$_2$NCO radical is consequently pertinent towards this source." (Astrochemical implications)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Upper limits rely on LTE and an assumed 0.5 arcsec source size
- Caveat (inferred, ours): Limits are derived without stated noise or uncertainty
- Caveat (inferred, ours): Lab catalogue accuracy is only 100 kHz

## Reproducibility

- Data public (paper): PILS ALMA data cited as project 2013.1.00278.S; catalogue in supplementary material  
  > "A spectral catalogue at 300 K (with fully resolved hyperfine structure) is available in the electronic supplementary material" (Assignments and fit)
- Products in archive: _not stated_
- Missing: Extraction position coordinates
- Missing: Noise level used for upper limits
- Missing: PILS calibration and imaging details
- Data volume (inferred): tens of GB (PILS cubes)
- Score (inferred): 3/5, ALMA analysis is brief but simple; the data are public and the settings are given, with some details missing.
- Rediscovery candidate: no, The ALMA part is a brief non-detection with limited numeric detail; the main results are laboratory.

## Links

- Method: (cite: Jorgensen2016) (PILS survey description)
- Companion: (cite: coutens2016:ALMAPILS) (formamide and HNCO columns toward IRAS16293 B)
- Related: PILS

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "stated": 23,
  "rate": 0.365
 },
 "evidence_ok": true
}
```
