# Revisiting the Extended Schmidt Law: The Important Role of Existing Stars in Regulating Star Formation

`2018ApJ...853..149S` | The Astrophysical Journal 2018 | first author: Shi, Yong | arXiv: 1801.00888 | DOI: 10.3847/1538-4357/aaa3e6

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Does the extended Schmidt law (SFR depending on gas and stellar mass surface density) hold across a wide range of environments, including outer disks of dwarfs, spirals, mergers, GMCs and high-z galaxies?  
  > "We find that these regions are distributed in a tight power-law as $\Sigma_{\rm       SFR}{\propto} ({\Sigma_{\rm
      star}^{0.5}}{\Sigma_{\rm  gas}})^{1.09}$" (abstract)
- Target **NGC 1614**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **IC 4687**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00182.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO 6-5 synthesized beam 0.26x0.20 arcsec^2 (NGC 1614)  
  > "as observed by ALMA (cite: Xu15) with a synthesized beam of 0.26$\times$0.20 arcsec$^{2}$" (NGC 1614)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; data retrieved from ALMA archive  
  > "We retrieved the data from the ALMA archive and obtained the intensity map by integrating the velocity from 4500 to 5000 km/s." (NGC 1614)
- Line: CO 6-5 (not stated)
- Line: CO J=2-1 (IC 4687) (not stated)
- Other facility **HI Nearby Galaxy Survey (VLA)**: HI gas for dwarfs and spirals  
  > "The HI data are from the H I Nearby Galaxy Survey (cite: Walter08)" (2.2 Local Spiral Galaxies)
- Other facility **CFHT MegaCam**: g and r imaging of three dwarfs  
  > "The optical observations of the above three dwarf galaxies were carried out at $g$ and $r$ band with the MegaCAM of CFHT" (2.1)
- Other facility **GALEX**: far-UV for SFR  
  > "The SFRs are the combinations of the far-UV from the GALEX archive" (2.2)
- Other facility **HST**: archival images for stellar masses of LIRGs  
  > "we retrieved the archived images of the *Hubble* Space Telescope in the filters of ACS-F435W" (NGC 1614)
- Other facility **VLA archive**: 8.4 and 4.86 GHz maps for NGC 1614 SFR  
  > "We retrieved the radio 8.4 GHz (X-band) and 4.86 GHz (C-band) intensity maps from the VLA archive" (NGC 1614)
- Other facility **SMA**: CO 3-2 and 880um for six (U)LIRGs, re-reduced  
  > "We retrieved the raw data from the SMA archive and re-reduced them." ((U)LIRG at 1'' resolution)
- Other facility **IRAM 30m**: CO(2-1) in M33  
  > "M33 was mapped with IRAM 30 m at CO (2-1)" (2.4)
- External data: IC 4687 SFR and gas mass measurements  
  > "The spatially resolved measurements of SFRs and gas masses of IC 4687 have been carried out in the literature study (cite: Pereira-Santaella16)." (IC 4687) [from (cite: Pereira-Santaella16)]
- External data: High-z galaxy SFRs, gas and stellar masses  
  > "adopted the integrated SFRs, gas masses and stellar masses as measured in the literature" (2.5) [from (cite: Tacconi13) and Table references]

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

- CO 6-5 to gas mass formula, modified with smaller X_CO  
  > "we used the formula in the literature (cite: Xu15) with a slightly smaller $X_{\rm  CO}$" (NGC 1614) [from (cite: Xu15)]
- Spiral measurements follow earlier approach  
  > "are carried out basically following the literature work (cite: Shi11; Bigiel08)" (2.2) [from (cite: Shi11; Bigiel08)]

### Not stated but needed to reproduce (our reading)

- ALMA reduction/calibration details and CASA version (archive products apparently used)
- Moment-map/clipping and region placement for NGC 1614 and IC 4687
- Distances and inclinations for each galaxy
- Exact SED-fitting setup for HST stellar masses

## Analysis recipe

1. **NGC 1614 gas surface density from ALMA CO 6-5**: Integrate CO 6-5 over 4500-5000 km/s, convert to Sigma_gas via 13.5 x f_CO(6-5)  
  > "$\Sigma_{\rm gas} = 13.5{\times}f_{\rm CO(6-5)},$" (NGC 1614)
   - parameter: CO6-5/2-1 brightness ratio 0.72; CO(2-1)/(1-0) factor 3.1  
  > "CO 6-5 is first converted to CO 2-1 by assuming a brightness temperature ratio of 0.72 between the two" (NGC 1614)
   - assumption: X_CO = 2e20 cm^-2 with factor 1.36 for helium  
  > "then used the conversion factor $X_{\rm  CO}$ = 2$\times$10$^{20}$ cm$^{-2}$ for CO 1-0 with an additional factor of 1.36 for the helium" (NGC 1614)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the extended Schmidt law to all regions**: Best-fit power law of SFR, gas and stellar surface densities; medians and scatter with bootstrap errors  
  > "The associated error bars were derived based on the bootstrap." (3)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit extended Schmidt law | Sigma_SFR = 10^-4.76 (Sigma_star^0.5 Sigma_gas)^1.09 | not stated | Msun/yr/kpc^2 | 2 | \Sigma_{\rm SFR} = 10^{-4.76}(\Sigma_{\rm star}^{0.5}\Sigma_{\rm gas})^{1.09} |
| Scatter of relation | 0.30 | not stated | dex | 2 | The 1-$\sigma$ apparent scatter of the relationship is about 0.30 dex. |
| Median offset of metal-poor regions, KS to extended Schmidt | factor 60 to factor 9 | not stated | dimensionless | 2 | with the median offset dropping from a factor of 60 in the Kennicutt-Schmidt plane to a factor of 9 in the extended Schmidt plane |
| Dwarf outer-disk median offset, extended Schmidt | -0.26 | 0.04 | dex | 2 | -0.26$\pm$0.04, 0.48$\pm$0.03 |

## Qualitative findings

- Mid-plane pressure is well approximated by Sigma_star^0.5 Sigma_gas, supporting a role for stellar gravity.  
  > "the mid-plane pressure is well approximated by the term ${\Sigma_{\rm
    star}^{0.5}}{\Sigma_{\rm  star}}$" (6)

## Claim tuples

- H: Stellar mass surface density regulates star formation in addition to gas. | E: Compiled SFR, gas and stellar mass surface densities for regions in dwarfs, spirals, LIRGs, M33 GMCs and high-z galaxies and fit the extended Schmidt law. | R: Single power law with slope 1.09 and 0.30 dex scatter. | F: Extended Schmidt law holds across environments. | **supported**
- H: Outer disks of dwarfs follow the extended Schmidt law while deviating from KS and Silk-Elmegreen. | E: Measured 114 regions in three dwarf galaxies and computed offsets. | R: Median offsets -0.26 (ES), -1.20 (KS), -1.92 (SE) dex. | F: Dwarf outer disks follow the extended Schmidt law with large scatter. | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Same X_CO adopted for all sources for simplicity; smaller values for starbursts would steepen the slopes.  
  > "As a result, we used the same factor for simplicity." (3)
- Caveat (inferred, ours): ALMA data are a small part of the sample; the result depends on heterogeneous SFR and mass tracers.
- Caveat (inferred, ours): Uniform X_CO and a fixed stellar mass-to-light ratio may bias slopes.

## Reproducibility

- Data public (paper): ALMA data retrieved from public archive  
  > "We retrieved the data from the ALMA archive" (NGC 1614)
- Products in archive: _not stated_
- Missing: Region lists and measured values for all samples
- Missing: Fitting method details for the power law
- Missing: ALMA data processing details
- Data volume (inferred): ~10-50 GB for the ALMA part; multi-survey ancillary data
- Score (inferred): 3/5, Formulas are given, but many data come from multiple archives and prior papers, and the fitting is not specified.
- Rediscovery candidate: no, The ALMA part is minor and the compilation depends on many external datasets and unspecified fitting.

## Links

- Method: (cite: Shi11) (Original extended Schmidt law)
- Method: (cite: Leroy08) (SFR and stellar mass conversion formulas)
- Method: (cite: Xu15) (NGC 1614 CO 6-5 data and gas mass formula)
- Companion: (cite: Pereira-Santaella16) (IC 4687 SFR and gas measurements)
- Related: HI Nearby Galaxy Survey (THINGS)
- Related: SINGS
- Related: GALEX
- Related: BIMA SONG

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
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
  "facts": 67,
  "stated": 21,
  "rate": 0.313
 },
 "evidence_ok": true
}
```
