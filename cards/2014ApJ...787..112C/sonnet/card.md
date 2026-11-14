# Herschel Observations of Extraordinary Sources: Analysis of the HIFI 1.2 THz Wide Spectral Survey toward Orion KL. I. Methods

`2014ApJ...787..112C` | The Astrophysical Journal 2014 | first author: Crockett, Nathan R. | arXiv: 1405.2351 | DOI: 10.1088/0004-637X/787/2/112

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the molecular column densities, abundances and rotation temperatures toward the Orion KL components, derived from LTE/non-LTE modeling of the full HIFI 480-1907 GHz survey combined with IRAM 30 m data?  
  > "we model the molecular emission from the mm to the far-IR using the XCLASS program which assumes local thermodynamic equilibrium (LTE). Several molecules are also modeled with the MADEX non-LTE code." (abstract)
- Target **Orion KL**: coordinates ALMA phase center RA 5h35m14.35s, Dec -05d22m35s (J2000)  
  > "we assume an Orion KL distance of 420 pc (cite: menten07; hirota07)" (3.1 Description of Orion KL Components); "The phase center was pointed at coordinates $\alpha_{J2000} = 5^{h}35^{m}14^{s}.35$ and $\delta_{J2000} = -05^{\circ}22'35''$." (2.3 The ALMA Survey); z/distance 420 pc  
  > "we assume an Orion KL distance of 420 pc (cite: menten07; hirota07)" (3.1 Description of Orion KL Components); "The phase center was pointed at coordinates $\alpha_{J2000} = 5^{h}35^{m}14^{s}.35$ and $\delta_{J2000} = -05^{\circ}22'35''$." (2.3 The ALMA Survey); distance from menten07; hirota07  
  > "we assume an Orion KL distance of 420 pc (cite: menten07; hirota07)" (3.1 Description of Orion KL Components); "The phase center was pointed at coordinates $\alpha_{J2000} = 5^{h}35^{m}14^{s}.35$ and $\delta_{J2000} = -05^{\circ}22'35''$." (2.3 The ALMA Survey)

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (214-247 GHz)  
  > "covers a frequency range of 214 – 247 GHz at a spectral resolution of 0.488 MHz ($\sim$ 0.6 km/s at 231 GHz)" (2.3 The ALMA Survey)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 16 antennas of 12 m  
  > "The observations were obtained with an array of 16 antennas on 20 January 2012." (2.3 The ALMA Survey)
- configurations: _not stated_
- baselines: 13-202 kλ  
  > "projected baselines had lengths between 13 and 202 k$\lambda$" (2.3 The ALMA Survey)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 20 January 2012  
  > "The observations were obtained with an array of 16 antennas on 20 January 2012." (2.3 The ALMA Survey)
- pi or archival as stated: Public ALMA Science Verification data  
  > "This survey was observed as part of ALMA’s science verification (SV) phase" (2.3 The ALMA Survey)
- Line: OCS 20-19 (not stated)
- Line: CS 5-4 (not stated)
- Other facility **Herschel/HIFI**: 480-1907 GHz wide spectral survey, 1.1 MHz resolution (main dataset)  
  > "This survey spans a frequency range from 480 to 1907 GHz at a resolution of 1.1 MHz." (abstract)
- Other facility **IRAM 30 m**: mm line survey (80-280 GHz) constraining low-energy transitions  
  > "covers frequency ranges 200 – 280 GHz, 130 – 180 GHz, and 80 – 116 GHz" (2.2 The IRAM Survey)
- External data: H2 column densities per component from C18O  
  > "We obtained these values from (cite: plume12), who use C$^{18}$O lines within the Orion KL HIFI scan to derive total C$^{18}$O column densities" (3.3 XCLASS modeling) [from (cite: plume12)]
- External data: Isotopic ratios C, S, O from OCS/H2CS modeling  
  > "The C, S, and O ratios are taken from (cite: tercero10)" (4.2 Abundances) [from (cite: tercero10)]
- External data: Water abundances adopted  
  > "We adopt the abundances derived in (cite: neill13a) here." (5.32 H2O) [from (cite: neill13a)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (flux), J0607-085 (phase)  
  > "Callisto and the quasar J0607-085 were used as the absolute flux and phase calibrators, respectively." (2.3 The ALMA Survey)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA, same methodology as Neill et al. 2013a  
  > "The Common Astronomy Software Applications package, CASA, was used to produce the maps presented in this work using the same methodology as (cite: neill13a)." (2.3 The ALMA Survey)
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

- ALMA SV map production and data product  
  > "We used the same data product presented in (cite: neill13a) to make Fig. [9](#p-alma_maps)." (3.2 Hot Core South) [from (cite: neill13a)]
- HIFI data reduction procedure  
  > "The method we used to reduce the data is described in (cite: crockett14)." (2.1 The HIFI Survey) [from (cite: crockett14)]

### Not stated but needed to reproduce (our reading)

- CASA version, clean parameters, weighting and beam for ALMA maps
- Line-free channels and integration ranges for ALMA moment maps
- ALMA map noise and beam sizes
- Exact XCLASS/MADEX model input files (provided only online)

## Analysis recipe

1. **Fit LTE models per molecule**: XCLASS models fit by hand, with MAGIX Levenberg-Marquardt in some cases, to HIFI+IRAM spectra by component  
  > "The emission was then fit by varying the free parameters (i.e. $T_{\rm rot}$, $N_{\rm tot}$, v$_{\rm lsr}$, and $\Delta$v) by hand until good agreement, as assessed by eye" (3.3 XCLASS modeling)
   - software: XCLASS, MAGIX
   - parameter: Source sizes 10'' hot core/compact ridge, 30'' plateau, 180'' extended ridge  
  > "| Hot Core       |         10          |   3.1 $\times$ 10$^{23}$    |" (Table 2)
   - assumption: kappa_1.3mm=0.42 cm2/g, beta=2, dust-to-gas 0.01, NH2=2.5e24 cm-2 for dust opacity  
  > "We also set $\beta$ = 2 and $\chi_{\rm dust}$ = 0.01." (3.3 XCLASS modeling)
   - fitting: Mostly by-eye, MAGIX Levenberg-Marquardt for some  
  > "we derived most models by hand" (3.3 XCLASS modeling)
   - validation: Reduced chi-square over HIFI band  
  > "we computed a reduced $\chi^{2}$ metric (described in the Appendix) for each model across the entire HIFI band" (3.3 XCLASS modeling)
2. **Non-LTE modeling of subset**: MADEX LVG models with temperature/density sub-components  
  > "this non-LTE program solves the equations of statistical equilibrium assuming the large velocity gradient (LVG) approximation" (3.4 MADEX modeling)
   - software: MADEX
   - fitting: by hand  
  > "Just as with XCLASS, these parameters were varied by hand." (3.4 MADEX modeling)
   - validation: reduced chi-square  
  > "A reduced $\chi^{2}$ analysis indicates that models for most species reproduce the observed emission well." (Abstract)
3. **Compute abundances**: Ntot/NH2, with isotopic ratios for rare isotopologues  
  > "We compute molecular abundances by dividing the column densities in Tables [4](#t-xclass) and [5](#t-madex) by $N_{\rm H_{2}}$ values given in Table [2](#t-standard)." (4.2 Abundances)
   - fitting: _not stated_
   - validation: XCLASS vs MADEX agreement within factor 2-3  
  > "we see that XCLASS and MADEX abundances typically agree quite well with one another (within a factor of $\sim$ 2 – 3)" (4.2 Abundances)
4. **Map hot core south and compact ridge tracers in ALMA SV**: Integrated intensity maps of HDO, 13CH3OH, 13CH3CN, CH3OCHO, OCS, CS with continuum overlays  
  > "Fig. [9](#p-alma_maps) contains four panels each plotting an integrated intensity map (color scale) of a transition from one of these molecules." (3.2 Hot Core South)
   - software: CASA
   - parameter: 13CH3OH integrated 3-5 km/s; OCS/CS integrated 7.6-8.3 km/s  
  > "The $^{13}$CH$_{3}$OH map in Fig. [9](#p-alma_maps) is integrated in the velocity range 3 – 5 km/s" (3.2 Hot Core South)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **XCLASS** : LTE spectral modeling  
  > "All molecular species are modeled using XCLASS." (3.3 XCLASS modeling)
- **MADEX** : non-LTE LVG modeling  
  > "A subset of the molecules detected in the HIFI scan were also modeled using the MADEX code." (3.4 MADEX modeling)
- **MAGIX** : automated fitting of XCLASS  
  > "we employed the MAGIX program (cite: moller13)" (3.3 XCLASS modeling)
- **HIPE** 5.0, build 1648: HIFI pipeline processing  
  > "standard HIPE (cite: ott10) pipeline processing (version 5.0, build 1648)" (2.1 The HIFI Survey)
- **CASA** : ALMA SV maps  
  > "CASA, was used to produce the maps presented in this work" (2.3 The ALMA Survey)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecules detected | 39 molecules (79 isotopologues) | not stated | count | 1 | In total, we detect 79 isotopologues of 39 molecules. |
| Identified lines in HIFI survey | ~13,000 | not stated | count | 1 | we obtain a total of $\sim$ 13,000 identified lines in the Orion KL HIFI survey at or above 3 $\sigma$ |
| Unidentified line fraction | ~12% | not stated | percent | 1 | leading to a U line fraction of $\sim$ 12% |
| Tvib HCN nu2=1/nu=0 hot core | 270 | 20 | K | 1 | / HCN        / $\nu_{2}$=1 / $\nu$=0     / 270 $\pm$ 20 / ...          / |
| CH3CN Trot hot core | 260 | 10% | K | 1 | We derive $T_{\rm rot}$ = 260, 230, and 120 K for the hot core, compact ridge, and plateau, respectively. |

## Qualitative findings

- Hot core Trot distribution is much wider than other components, indicating most complex thermal structure  
  > "the spread in rotation temperature is much larger toward the hot core relative to the other spatial/velocity components" (6 Discussion)
- HDO and 13CH3OH trace a clump ~1'' south of the hot core continuum peak (hot core south)  
  > "HDO, as first pointed out by (cite: neill13a), traces a clump $\sim$ 1$''$ south of the continuum peak." (3.2 Hot Core South)

## Claim tuples

- H: Are LTE models adequate for complex organics? | E: Reduced chi-square of XCLASS fits across HIFI band | R: 47 of 80 models have chi2_red<=1.5; complex organics mostly low | F: LTE good for complex organics, implying n>1e6 cm-3 | **supported**
- H: Do LTE abundances agree with non-LTE? | E: Compare XCLASS and MADEX abundances | R: agree within factor ~2-3 | F: LTE abundances reliable | **supported**
- H: Is OCS/CS high Trot in compact ridge spatially distinct? | E: ALMA SV integrated maps vs methyl formate | R: OCS and CS peaks offset from MF1 and MF3 nearer LVF | F: Higher Trot may result from LVF-compact ridge interaction | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Automated fitting algorithms rejected as primary method  
  > "We found that automated fitting algorithms had difficulty reaching reasonable solutions" (3.3 XCLASS modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE, no radiative pumping, constant source size assumed; some species optically thick  
  > "both XCLASS and MADEX do not include radiative excitation effects which are likely important for some species" (4.1 The Full Band Model and Line Statistics)
- Caveat (inferred, ours): Fits done by eye, no formal parameter uncertainties
- Caveat (inferred, ours): NH2 for dust opacity inflated ad hoc
- Caveat (inferred, ours): ALMA role qualitative only

## Reproducibility

- Data public (paper): ALMA SV data and HIFI products publicly available  
  > "Both the line survey and continuum map can be downloaded from the ALMA SV website" (2.3 The ALMA Survey)
- Products in archive: _not stated_
- Missing: Model input files beyond online figure sets
- Missing: ALMA imaging parameters
- Data volume (inferred): HIFI products tens of MB; ALMA SV dataset tens of GB
- Score (inferred): 3/5, Main HIFI analysis is public and well described but fitting is by hand; ALMA part is minor and lacks imaging details.
- Rediscovery candidate: no, Hand-tuned fits and ALMA is minor.

## Links

- Method: (cite: crockett14) (HIFI data reduction)
- Method: (cite: neill13a) (ALMA SV map methodology)
- Companion: (cite: neill13a) (Water/HDO analysis)
- Companion: (cite: plume12) (H2 column densities)
- Related: HEXOS
- Related: ALMA Science Verification Orion KL
- Related: IRAM 30 m Orion KL survey

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 74,
  "stated": 40,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
