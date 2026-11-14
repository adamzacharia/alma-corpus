# Understanding the chemistry of the young stellar object G29.862-0.0044

`2024BAAA...65..173M` | Boletin de la Asociacion Argentina de Astronomia La Plata Argentina 2024 | first author: Martinez, N. C. | arXiv: 2406.02358 | DOI: 10.48550/arXiv.2406.02358

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What molecular species and physical conditions (rotational temperature, ionized gas) characterize the chemistry of the young stellar object G29.862-0.0044?  
  > "In this preliminary study, we present new chemical species observed in the region where the YSO is located, previously unidentified." (1 Introduction)
- Target **G29.862-0.0044 (G29)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01312.S
- bands: Band 6 (1.3 mm continuum)  
  > "continuum at 1.3 mm and molecular lines retrieved from the ALMA data archive (Project 2015.1.01312.S; PI: Fuller, G.; Band 6)" (2 Observations and data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.78" x 0.60"; spectral resolution 1.4 km/s  
  > "The angular and spectral resolution are 0$.\!\!^{\prime\prime}$78$\times$0$.\!\!^{\prime\prime}$60 and 1.4 km s$^{-1}$, respectively." (2 Observations and data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; PI G. Fuller  
  > "retrieved from the ALMA data archive (Project 2015.1.01312.S; PI: Fuller, G.; Band 6)" (2 Observations and data)
- Line: C17O 2–1 (224.714 GHz)
- Line: H2CO 3(1,2)–2(1,1) (225.697 GHz)
- Line: CN 2–1 J=5/2–3/2 F=5/2–3/2 (226.874 GHz)
- Line: HC3N 25–24 (227.418 GHz)
- Line: CH3CN 13–12 k=2 (239.119 GHz)
- Line: H2CS 7(0,7)–6(0,6) (240.267 GHz)
- Line: C34S 5–4 (241.016 GHz)
- Line: CH3OH 5(-1,5)–4(-1,4) (241.767 GHz)
- Other facility **JVLA**: 3 cm radio continuum, A configuration  
  > "Radio continuum observations at 3 cm were carried out using the Karl G. Jansky Very Large Array (JVLA) in A configuration (Project 22A-063; PI: M. Ortega)." (2 Observations and data)
- Other facility **Gemini-NIFS**: IFU NIR spectroscopy (Brγ)  
  > "we carried out IFU spectroscopic NIR observations using NIFS at Gemini North (project GN-2022A-Q-125; PI: S. Paron)." (2 Observations and data)
- Other facility **Gemini-NIRI**: JHKs NIR image  
  > "obtained with Gemini-NIRI (see (cite: areal20))" (1 Introduction)
- External data: Rest frequencies from Splatalogue; partition function from CDMS  
  > "Rest frequencies from the [Splatalogue Catalog](https://splatalogue.online)." (Table 1) [from Splatalogue; CDMS]

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

- Rotation-diagram formulation for interferometric data  
  > "see details in (cite: ortega23), Sect. 4.3.1" (3.1 New molecular species in YSO-G29) [from (cite: ortega23)]
- Population diagram method  
  > "by using the population diagram method (cite: goldsmith99)" (3.1 New molecular species in YSO-G29) [from (cite: goldsmith99)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (tclean parameters, weighting, masks)
- Continuum subtraction and line-free channels
- Integrated-intensity measurement regions and uncertainties for each K component
- Source distance and beam used in the rotation diagram
- Details of line identification
- Which K components were used and how uncertainties were handled in the fit

## Analysis recipe

1. **Map molecular line emission**: Integrate line emission between 95 and 105 km/s and overlay on Ks image  
  > "maps of the molecular line emission integrated between 95 and 105 km s$^{-1}$ (presented in red with white contours), superimposed to the Ks-emission" (3.1 New molecular species in YSO-G29)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CH3CN rotational temperature and column density**: Population diagram, linear fit of ln(Nu/gu) vs Eu for CH3CN J=13–12 K=0–6; Ntot from intercept with Qrot from CDMS  
  > "We performed a linear fitting to Eq. [\[RotDia\]](#RotDia) (see Fig.[3](#trot)), and from the slope, we determined ${\rm T_{rot}}$." (3.1 New molecular species in YSO-G29)
   - assumption: Optically thin lines, LTE  
  > "Assuming optical thin lines and Local Thermodynamic Equilibrium (LTE) conditions" (3.1 New molecular species in YSO-G29)
   - fitting: Linear least-squares fit (assumed)  
  > "We performed a linear fitting to Eq. [\[RotDia\]](#RotDia) (see Fig.[3](#trot)), and from the slope, we determined ${\rm T_{rot}}$." (Results)
   - validation: Compared with earlier Trot from four K components  
  > "employing the same methodology, albeit with only four CH$_{3}$CN *K* projections." (4 Discussion)

## Software

- **CASA** 5.8.0-105: Handling radio continuum and millimeter data  
  > "The radio continuum observations and the millimeter data were handled with CASA version 5.8.0-105." (2 Observations and data)
- **Gemini IRAF package** v1.14: NIFS data reduction  
  > "The standard NIFS tasks included in the Gemini IRAF package v1.14 were used for data reduction." (2 Observations and data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CN rotational temperature | 362 | ±176 | K | 2 | T$_{\rm rot} = 362\pm176$ K |
| CH3CN total column density | 7.3e15 | ±1.9e15 | cm^-2 | 2 | N$_{\rm tot}$ $= (7.3\pm1.9)\times10^{15}$ cm$^{-2}$ |

## Qualitative findings

- Eight new molecular species detected with distinct spatial distributions; C34S and CN/CH3OH suggest different outflow directions  
  > "We suggest that both species reveal the direction of an outflow that is not coincident in direction with the one described by the C$^{34}$S emission." (4 Discussion)
- A compact 3 cm radio source was discovered with JVLA  
  > "a compact radio continuum source at 3 cm, which we discovered using the JVLA observations" (3.2 Ionized gas in the region)

## Claim tuples

- H: G29 hosts a hot core | E: CH3CN rotation diagram | R: Trot = 362±176 K | F: Temperature consistent with a hot core, higher than earlier estimate | **supported**
- H: Molecular emission traces outflows | E: Compared line maps | R: C34S differs in orientation from CN and CH3OH | F: Two outflow directions suggested | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Preliminary results; further analysis in future work  
  > "In what follows, we present some preliminary results obtained from the mentioned multifrequency dataset." (2 Observations and data)
- Caveat (inferred, ours): Trot uncertainty is very large (~50%)
- Caveat (inferred, ours): LTE and optically thin assumption for CH3CN is not tested
- Caveat (inferred, ours): Outflow interpretation is qualitative
- Caveat (inferred, ours): Line identifications are not detailed

## Reproducibility

- Data public (paper): ALMA data retrieved from the archive  
  > "retrieved from the ALMA data archive (Project 2015.1.01312.S; PI: Fuller, G.; Band 6)" (2 Observations and data)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Integrated intensities per K component
- Missing: Line-free channels
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and a simple method, but few processing details are given.
- Rediscovery candidate: no, Imaging and fitting details are missing, and the paper has only two numeric results.

## Links

- Method: Goldsmith & Langer 1999 (cite: goldsmith99) (Population diagram method)
- Method: Ortega et al. 2023 (cite: ortega23) (Rotation diagram for interferometric data)
- Companion: Areal et al. 2020 (cite: areal20) (Earlier study of G29)

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 21,
  "rate": 0.344
 },
 "evidence_ok": true
}
```
