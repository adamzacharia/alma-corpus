# JWST detection of extremely excited outflowing CO and H<SUB>2</SUB>O in VV 114 E SW: A possible rapidly accreting IMBH

`2024A&A...682A.182G` | Astronomy and Astrophysics 2024 | first author: González-Alfonso, Eduardo | arXiv: 2312.04914 | DOI: 10.1051/0004-6361/202348469

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the nature of the extremely excited, outflowing CO and H2O absorption bands detected with JWST in the SW-s2 clump of VV 114 E, and does it indicate an accreting IMBH?  
  > "Here we report and analyze the detection of extremely excited CO and H$_2$O, observed in absorption, in the local merger VV 114" (abstract)
- Target **VV 114 E (SW-s2 clump)**: coordinates _not stated_; z/distance 88 Mpc; z=0.02013  
  > "We adopt a distance to VV 114 of 88 Mpc." (1 Introduction); "we use the redshift of the bulk of the gas in SW-s2, $z=0.02013$, derived from the CO ($3-2$) line fit." (2.1 The CO v=1-0 band); distance from adopted, not stated where from (z from CO(3-2) fit)  
  > "We adopt a distance to VV 114 of 88 Mpc." (1 Introduction); "we use the redshift of the bulk of the gas in SW-s2, $z=0.02013$, derived from the CO ($3-2$) line fit." (2.1 The CO v=1-0 band)

## Data provenance

- ALMA projects: 2013.1.00740.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.14'' (~60 pc)  
  > "as seen with the ALMA angular resolution of $0.14''\approx60$ pc" (4.2 The origin of the bands)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival, PI T. Saito  
  > "We have also retrieved archival Atacama Large Millimeter/submillimeter Array (ALMA) observations" (2 Observations and results)
- Line: CO J=3-2 (not stated)
- Other facility **JWST (NIRSpec IFU, MIRI MRS/imaging, NIRCam), DD-ERS 1328**: Main data: CO v=1-0 and H2O nu2 absorption bands, mid-IR images and spectra  
  > "We have used the MIRI (imaging and MRS), NIRCam, and NIRSpec IFU data on VV 114 from the Director’s Discretionary Early Release Science (DD-ERS) Program #1328" (2 Observations and results)
- External data: HITRAN2020 spectroscopic parameters for CO and H2O  
  > "We take all spectroscopic parameters for CO and H$_2$O from the HITRAN2020 database" (1 Introduction) [from (cite: gor22)]
- External data: Collisional rates for CO-H2 and H2O-H2  
  > "using the rates by (cite: yan10) for collisional excitation of CO with H$_2$, and those by (cite: dan11) for H$_2$O with H$_2$" (3.2 The best fit) [from (cite: yan10); (cite: dan11)]

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
- continuum subtraction: 345 GHz continuum extracted from line-free channels; CO(3-2) shown as continuum-subtracted moment 0  
  > "The images of the continuum-subtracted CO ($3-2$) emission (moment 0) and 345 GHz continuum (extracted from line-free channels) are shown in Fig. 1a-b" (2 Observations and results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA CO(3-2) and continuum images follow earlier publication of the data  
  > "345 GHz continuum (extracted from line-free channels) are shown in Fig. 1a-b (cite: sai15)." (2 Observations and results) [from (cite: sai15)]
- JWST data reduction details  
  > "All details of the reduction procedure are given in (cite: gber23) and (cite: per23)." (Data reduction) [from (cite: gber23); (cite: per23)]
- Radiative transfer code for bands  
  > "We use the code described in (cite: gon98), which assumes spherical symmetry." (3.2 The best fit) [from (cite: gon98)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters (robust, beam, rms) for CO(3-2) and continuum
- Aperture centre coordinates of the extraction
- Line-free channels used for the 345 GHz continuum
- Flux conversion details for CO(3-2) mass beyond alpha_CO value
- Source code of the radiative transfer model

## Analysis recipe

1. **Fit CO(3-2) profile and set upper limit for hot component**: 3-component Gaussian fit to CO(3-2) profile with one component fixed at -160 km/s, from aperture r=0.162''  
  > "A 3-components Gaussian fit to the CO ($3-2$) profile, fixing the central velocity of one component at $-160$ km s$^{-1}$" (2.1 The CO v=1-0 band)
   - assumption: alpha_CO3-2 ≈ 0.8 Msun/(K km/s pc^2)  
  > "using $\alpha_{\mathrm{CO3-2}}\approx0.8\,M_{\odot}/(\mathrm{K\,km\,s^{-1}\,pc^2})$" (2.1 The CO v=1-0 band)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Paris-Durham shock code** : C- and J-type shock models  
  > "We have used the Paris-Durham shock code (cite: god19) to generate both $C-$type and $J-$type shock models" (3.2.1)
- **JWST Calibration pipeline** 11.16.20: NIRSpec IFU reduction  
  > "The observations were processed using the JWST Calibration pipeline (version 11.16.20)." (Data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) flux of central component | 17.4 | 0.1 | Jy km/s | 1 | The central velocity component has a CO ($3-2$) flux of $(17.4\pm0.1)$  Jy km s$^{-1}$ |
| Upper limit CO(3-2) flux of hot component | <0.35 | not stated | Jy km/s | 1 | upper limit for the flux of the $H_C$ in CO ($3-2$) of $<0.35$ Jy km s$^{-1}$ |
| Gas mass SW-s2 | ~3e7 | not stated | Msun | 1 | $M_{\mathrm{gas}}(\mathrm{SW-s2})\sim3\times10^7\,M_{\odot}$ |
| BH mass | 4.5e4 exp(tau-2.5) | 2.4e4 | Msun | 0 | $$M_{\mathrm{BH}}=(4.5\pm2.4)\times10^4
\exp\{\tau_{\mathrm{6\mu m}}^{\mathrm{ext}}-2.5\}\,M_{\odot}, |

## Qualitative findings

- CO and H2O bands are radiatively excited by a ~550 K mid-IR blackbody and outflow at ~180 km/s  
  > "the rotational levels of the ground vibrational state of CO and H$_2$O are radiatively excited by the mid-IR continuum" (4.2)

## Claim tuples

- H: SW-s2 hosts an accreting IMBH | E: Modelled JWST CO and H2O bands, compared with ALMA CO(3-2) | R: L_IR ~1e10 Lsun in a sub-pc source; M_BH ~4.5e4 Msun, super-Eddington | F: SW-s2 is a possible rapidly accreting IMBH | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Collisional excitation by shocks rejected as it fails to reproduce the required column densities  
  > "but failed to reproduce the required column densities of warm molecular gas." (3.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Source size not directly measured; IR surface density relies on assumed connected structure  
  > "is not based on direct measurements of the source size." (4.2)
- Caveat (inferred, ours): Hot component not detected in ALMA; ALMA role is minor and cannot test the model
- Caveat (inferred, ours): BH mass depends on assumed lifetime and extinction

## Reproducibility

- Data public (paper): ALMA data retrieved from the archive; JWST data from MAST  
  > "We have also retrieved archival Atacama Large Millimeter/submillimeter Array (ALMA) observations" (2 Observations and results)
- Products in archive: _not stated_
- Missing: Radiative transfer code not released
- Missing: ALMA processing details
- Data volume (inferred): ~10-50 GB (ALMA Band 7 archival plus JWST)
- Score (inferred): 2/5, ALMA role minor with few details; analysis relies on an unreleased code.
- Rediscovery candidate: no, Main results come from JWST modelling with an unreleased code.

## Links

- Companion: (cite: per23) (Similar JWST CO band analysis in NGC 3256)
- Related: JWST DD-ERS 1328

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
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
  "stated": 20,
  "rate": 0.345
 },
 "evidence_ok": true
}
```
