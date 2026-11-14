# Submillimeter-HCN Diagram for Energy Diagnostics in the Centers of Galaxies

`2016ApJ...818...42I` | The Astrophysical Journal 2016 | first author: Izumi, Takuma | arXiv: 1512.03438 | DOI: 10.3847/0004-637X/818/1/42

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: Do AGNs show enhanced HCN(4-3)/HCO+(4-3) and HCN(4-3)/CS(7-6) ratios compared with starbursts, and is the cause abundance or excitation (non-LTE RADEX modeling)?  
  > "In this paper, we compile literature and archival data of HCN(4-3), HCO$^+$(4-3), and CS(7-6) emission lines of various AGNs and SB galaxies to improve the statistics of the submm-HCN diagram, and to explore the cause of the HCN-enhancement." (Introduction)
- Target **NGC 1068**: coordinates _not stated_; z/distance 14.4 Mpc  
  > "35 pc $\times$ 28 pc at the assumed distance of NGC 1068 = 14.4 Mpc" (Data); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00083.S
- bands: Band 7  
  > "we used ALMA band 7 data retrieved from the ALMA Science Archive" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5" x 0.4" (35 pc x 28 pc)  
  > "The synthesized beams and the rms noises in channel maps of the target emission lines were typically 0$''$.5 $\times$ 0$''$.4" (Data)
- max recoverable scale: _not stated_
- sensitivity: 2.5 mJy/beam channel rms  
  > "and 2.5 mJy beam$^{-1}$, respectively" (Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, previously presented by Garcia-Burillo et al. 2014 and Viti et al. 2014  
  > "Although this data was already presented extensively in (cite: 2014A&A...567A.125G) and (cite: 2014A&A...570A..28V), we re-analyzed the data" (Data)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: CS J=7-6 (342.883 GHz)
- Other facility **APEX, JCMT, SMA, ASTE, other ALMA projects**: Literature line ratios for other galaxies  
  > "we first compiled interferometric data of the target emission lines of extragalactic objects from literatures." (Data)
- External data: Line ratios for NGC 1097, NGC 7469, M82, NGC 253, NGC 1614, LMC, APEX sample, etc. (Table 1)  
  > "The resultant HCN(4-3)/HCO$^+$(4-3) and HCN(4-3)/CS(7-6) line ratios of each data point" (Data) [from Table 1 references (1)-(8)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 15% absolute flux uncertainty  
  > "We assume the absolute flux uncertainty to be 15%." (Data)
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

- MIRIAD reduction steps and calibration details for 2011.0.00083.S
- Line-integration velocity ranges and aperture/regions for AGN, E-knot, W-knot, CND-N, CND-S
- Continuum subtraction
- RADEX collision-rate files and linewidth assumed
- Ratio uncertainty propagation

## Analysis recipe

1. **Measure line ratios in NGC 1068 from ALMA data**: Re-analysis of archival Band 7 data to get integrated-intensity ratios at several positions  
  > "we re-analyzed the data to obtain high resolution values of the $R_{\rm HCN/HCO^+}$ and $R_{\rm HCN/CS}$" (Data)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: Rms and fluxes agree with published data  
  > "The rms noises and measured fluxes of these lines are in good agreement with the published data." (Data)
2. **Non-LTE modeling of line ratios**: RADEX grid over Tkin (50,100,200 K), nH2 (1e5, 5e6), abundance ratio (1,10), Tbg (2.73-60 K), N/dV; spherical escape probability  
  > "The cases of 50, 100, and 200 K are investigated." (4.1 Model description)
   - software: RADEX
   - assumption: Homogeneous single-phase spherical cloud; blackbody background  
  > "As for the cloud geometry, we assumed a spherical one." (4 Non-LTE Excitation Analysis)
   - fitting: No fitting; grid comparison with observed ratios  
  > "Note that we do not intend to mimic an environment of a specific galaxy here. Moreover, one line ratio can be reproduced by various combinations of parameters." (4.1 Model description)
   - validation: Compared with NGC 1097, NGC 1068, NGC 4418 and with LTE results in the literature  
  > "we briefly compare our model calculations with the observed $R_{\rm HCN/HCO^+}$ and/or $R_{\rm HCN/CS}$ of two instructive AGNs and one buried-AGN, namely NGC 1097, NGC 1068, and NGC 4418." (4.5 Comparison with real galaxies: Case study of NGC 1097, NGC 1068, and NGC 4418)

## Software

- **MIRIAD** : Re-analysis of NGC 1068 ALMA data  
  > "We used MIRIAD ((cite: 1995ASPC...77..433S)) for this analysis." (Data)
- **RADEX** : Non-LTE radiative transfer models  
  > "we ran non-LTE radiative transfer models with the RADEX code" (4 Non-LTE Excitation Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R_HCN/HCO+ NGC 1068 (AGN) | 1.53 | 0.34 | dimensionless | 1 | NGC 1068 (AGN)                / 14.4         / AGN        / ALMA          / 35                     / 1.53$\pm$0.34 |
| R_HCN/HCO+ NGC 1068 (W-knot) | 3.19 | 0.71 | dimensionless | 1 | NGC 1068 (W-knot)             / 14.4         / AGN        / ALMA          / 35                     / 3.19$\pm$0.71 |
| R_HCN/CS NGC 1068 (AGN) | 8.84 | 2.51 | dimensionless | 1 | 1.53$\pm$0.34           / 8.84$\pm$2.51 |

## Qualitative findings

- AGNs show higher HCN/HCO+ and/or HCN/CS (4-3) ratios than SBs at high resolution; model needs HCN abundance boosted by a few to >=10 in AGNs, though higher density is not excluded  
  > "one can find a clear trend that AGNs exhibit higher $R_{\rm HCN/HCO^+}$ and/or $R_{\rm HCN/CS}$ than SB galaxies" (3 Up-dated Submillimeter-HCN diagram)

## Claim tuples

- H: AGNs have enhanced submm HCN ratios vs SB | E: Compiled 16 high-resolution and 9 low-resolution ratios | R: AGNs higher in high-res sample; low-res AGNs (NGC 1365, 4945) look like SB | F: Diagram is a potential diagnostic needing high resolution | **supported**
- H: Abundance ratios drive the enhancement | E: RADEX grid models | R: X_HCN/X_HCO+ >~10 needed in AGNs vs ~3 in SB at n=1e5 | F: Abundance enhancement preferred but higher AGN density cannot be excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Systematically higher gas density in AGNs not discarded  
  > "we could not fully discard the possibility that the systematically higher gas density in AGNs than in SB galaxies is a cause of the HCN-enhancement" (Summary and conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple single-zone models; buried AGNs may be affected by absorption/IR pumping  
  > "the latter scenario was not fully discarded because of the simplified modelings in this work" (Summary and conclusion)
- Caveat (inferred, ours): Small sample; heterogeneous telescopes and apertures
- Caveat (inferred, ours): Model grid is not fit to data

## Reproducibility

- Data public (paper): NGC 1068 data from ALMA archive  
  > "we used ALMA band 7 data retrieved from the ALMA Science Archive" (Data)
- Products in archive: _not stated_
- Missing: MIRIAD processing details
- Missing: Line integration windows and regions
- Data volume (inferred): ~10-30 GB for one Band 7 project
- Score (inferred): 4/5, ALMA part is small and sparsely described; the RADEX grid is well specified.
- Rediscovery candidate: no, The ALMA reduction recipe is incomplete and most data come from the literature.

## Links

- Companion: (cite: 2013PASJ...65..100I) (Original submm-HCN diagram)
- Companion: (cite: 2015ApJ...811...39I) (NGC 7469 and NGC 1097 data)

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
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
  "facts": 57,
  "stated": 21,
  "rate": 0.368
 },
 "evidence_ok": true
}
```
