# CO-DARK Star Formation and Black Hole Activity in 3C 368 at Z = 1.131: Coeval Growth of Stellar and Supermassive Black Hole Masses

`2017ApJ...836..123L` | The Astrophysical Journal 2017 | first author: Lamarche, C. | arXiv: 1701.03736 | DOI: 10.3847/1538-4357/836/1/123

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: How do star formation and AGN activity relate in the radio galaxy 3C 368 at z=1.131, and why is CO(2-1) undetected?  
  > "Here we investigate the relationship between star formation and AGN activity in the bright radio galaxy 3C 368 at redshift $z$ $=$ 1.131 ." (Introduction)
- Target **3C 368**: coordinates _not stated_; z/distance z = 1.131  
  > "the bright radio galaxy 3C 368 at redshift $z$ $=$ 1.131" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00426.S, 2013.1.01223.S
- bands: Band 3 (CO 2-1) and Band 9 ([N II] 205 um)  
  > "These band 9 observations were carried out on February 21 and April 13, 2014" (2.3 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 3.12" x 1.81"; Band 9: 0.41" x 0.29"  
  > "with a synthesized beam size of 3$\ensuremath{''}$12 $\times$ 1$\ensuremath{''}$81 (FWHM)" (2.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: Band 3: 134 uJy/beam; Band 9: 891 uJy/beam over 500 km/s  
  > "The 1$\sigma$ sensitivity for these observations is 134 $\mu$Jy beam$^{-1}$, over an assumed line width of 500 km s$^{-1}$." (2.3 ALMA)
- time on source: Band 3 ~37 min; Band 9 ~54 min  
  > "Our on-source integration time was $\sim$37 minutes." (2.3 ALMA)
- observing dates: Band 3: 2015 Jan 31; Band 9: 2014 Feb 21 and Apr 13  
  > "These band 3 observations were performed on January 31, 2015" (2.3 ALMA)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (not stated)
- Line: [N II] 205 um (not stated)
- Other facility **Herschel/PACS**: [O I] 63, [O III] 52 and 88, [O IV] 26 um line fluxes  
  > "The oxygen fine-structure lines were observed in 3C 368 using the *Photodetector Array Camera and Spectrometer* (*PACS*)" (2.1 Herschel/PACS)
- Other facility **PdBI**: CO(2-1) upper limit  
  > "The line was not detected, with a 3$\sigma$ upper limit" (2.2 PdBI)
- Other facility **Spitzer/IRS**: [Ne II], [Ne III], [Ne V] lines from CASSIS  
  > "were obtained from the Cornell Atlas of *Spitzer/IRS* Sources (CASSIS, Version 6)" (2.4 Spitzer/IRS)
- External data: [C II] 158 um flux  
  > "$^{a}$ (cite: Stacey2010CII)" (Table 1) [from (cite: Stacey2010CII)]
- External data: FIR luminosity/SED fit and SFR of 350 Msun/yr  
  > "obtaining a value of 350 $M_\odot$ yr$^{-1}$" (3.5 PDRs) [from (cite: Podigachoski2015)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.1 (Band 3); 4.2.1 (Band 9)  
  > "The data were reduced, imaged, and cleaned with CASA, version 4.2.1." (2.3 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (both bands)  
  > "we used Titan as a flux calibrator, at a distance of 41.7$^\circ$ from the source" (2.3 ALMA)
- flux scale uncertainty: ~10% Band 3; ~15% Band 9  
  > "Characteristic absolute flux calibrations with ALMA are accurate to $\sim$ 10% (ALMA Technical Handbook)." (2.3 ALMA)
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

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (weighting, robust, cell, image size)
- continuum subtraction and line-free channels
- channel width and spectral setup
- how upper limits and continuum fluxes were extracted
- masks and aperture for the Gaussian fit

## Analysis recipe

1. **CO(2-1) and [N II] upper limits**: 3 sigma limit over assumed 500 km/s width for source within beam (CO) or ~2 beams ([N II])  
  > "Presuming that the line source is extended over $\sim$ 2 beams" (2.3 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate alpha_CO limit**: Scoville2016 dust-based gas mass from 850 um, T_dust 35 K, with thermalized CO(2-1) limit  
  > "Assuming a dust temperature of 35 K, consistent with the SED fit from (cite: Podigachoski2015), we obtain a value of 1.57 $\times$ 10$^{11}$ M$_{\odot}$." (3.6 Where's the CO?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1 / 4.2.1: reduce, image and clean ALMA data; 2-D Gaussian fit to 205 um continuum  
  > "The data were reduced, imaged, and cleaned with the Common Astronomy Software Application (CASA)[^5], version 4.3.1." (2.3 ALMA)
- **GILDAS** : PdBI calibration and imaging  
  > "The data were calibrated and imaged using GILDAS[^3]" (2.2 PdBI)
- **HIPE** 13: Herschel PACS reduction  
  > "Herschel Interactive Processing Environment (HIPE, Version 13)" (2.1 Herschel/PACS)
- **PDR Toolbox** : PDR modeling of line ratios  
  > "together with the PDR Toolbox (cite: Kaufman2006), for our analysis" (3.5 PDRs)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) 3sigma upper limit (ALMA) | 0.201 | not stated | Jy km/s | 1 | yields an upper limit on the line intensity of 0.201 Jy km s$^{-1}$ |
| [N II] 205 um 3sigma upper limit | 3.78 | not stated | Jy km/s | 1 | the 3$\sigma$ upper limit is 3.78 Jy km s$^{-1}$ |
| Band 3 continuum, Northern lobe | 673 | 39 | uJy | 0 | the Northern lobe at 673 $\pm$ 39 $\mu$Jy |
| 205 um core continuum | 5.6 | 1.3 | mJy | 0 | with an integrated intensity of 5.6 $\pm$ 1.3 mJy |
| alpha_CO lower limit | 45.5 | not stated | Msun (K km/s pc^2)^-1 | 2 | we estimate an $\alpha_{CO}$  \> 45.5 M$_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ |

## Qualitative findings

- Starburst age ~6.5 Myr is comparable to the duration of the latest AGN episode (0.4-4 Myr)  
  > "we estimate the duration of the latest episode of AGN activity to be between 0.4 $-$ 4 Myr" (3.3 H ii Region Models)

## Claim tuples

- H: Is star formation in 3C 368 coeval with AGN activity? | E: HII region modeling of oxygen and neon lines | R: Starburst age ~6.5 Myr vs AGN 0.4-4 Myr | F: Supports a link between black hole and stellar growth | **supported**
- H: Is CO(2-1) detectable given the [C II] flux? | E: ALMA Band 3 observation | R: Not detected; [C II]/CO(2-1) > 7000, 12x expected | F: CO-dark star formation, likely fractionated ISM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Low metallicity rejected as unlikely given large stellar mass and main-sequence location  
  > "However, the low metallicity case is unlikely for 3C 368, which has a stellar mass of $\sim$ 3.6 $\times$ 10$^{11}$ $M_{\odot}$" (3.6 Where's the CO?)
- How they decided it was enough: _not stated_
- Limitation (authors): Fine-structure lines might originate from AGN-heated XDR rather than star formation  
  > "the observed \[C ii\] and \[O i\] lines may originate within the X-ray dominated region (XDR) surrounding the AGN of 3C 368" (3.5 PDRs)
- Caveat (inferred, ours): Upper limits depend on assumed 500 km/s line width and source size
- Caveat (inferred, ours): alpha_CO limit relies on dust-based gas mass with assumed T_dust
- Caveat (inferred, ours): Several line detections are marginal (2.4-3.8 sigma)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: spectral setup
- Missing: line-free channels and extraction method
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, ALMA parts give limits only, with few processing details; models rely on external codes.
- Rediscovery candidate: no, ALMA role is minor and processing details are missing.

## Links

- Method: (cite: Kaufman2006) (PDR Toolbox models)
- Method: (cite: Rubin1985) (HII region models)
- Companion: (cite: Stacey2010CII) (prior [C II] detection)
- Companion: (cite: Podigachoski2015) (SED and FIR luminosity)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 24,
  "rate": 0.393
 },
 "evidence_ok": true
}
```
