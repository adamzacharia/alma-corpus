# ALMA Observations of HCN and Its Isotopologues on Titan

`2016AJ....152...42M` | The Astronomical Journal 2016 | first author: Molter, Edward M. | arXiv: 1606.00348 | DOI: 10.3847/0004-6256/152/2/42

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system
- Question: What are the abundances and isotopic ratios (12C/13C, 14N/15N, D/H) of HCN isotopologues in Titan's atmosphere, and can new isotopologues be detected, using archival ALMA calibration data?  
  > "We model high signal-to-noise observations of HCN, H$^{13}$CN, HC$^{15}$N, DCN, and H$^{13}$C$^{15}$N to derive abundances and infer the following isotopic ratios" (abstract)
- Target **Titan**: coordinates _not stated_; z/distance 8.93-9.36 AU (Table, per observation)  
  > "using the distance and radial velocity of Titan with respect to the observer given by JPL Horizons" (Observations and Data Processing); distance from JPL Horizons  
  > "using the distance and radial velocity of Titan with respect to the observer given by JPL Horizons" (Observations and Data Processing)

## Data provenance

- ALMA projects: 2012.1.00261.S, 2012.1.00453.S, 2012.1.00566.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams from 0.44x0.41 to 2.48x1.89 arcsec  
  > "HCN (1-0) | 88.631 | 2014-04-03 | 157 | 32 | 488 | 2.48 $\times$ 1.89" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about three minutes each (157-158 s)  
  > "relatively short integration times of around three minutes each" (Introduction)
- observing dates: 3 April to 8 July 2014  
  > "We downloaded publicly available ALMA datasets taken between 3 April and 8 July 2014 that used Titan as a flux calibration source." (Observations and Data Processing)
- pi or archival as stated: publicly available archival flux calibration observations  
  > "derived from publicly available ALMA flux calibration observations of Titan taken in early 2014" (abstract)
- Line: HCN 1-0 (88.631 GHz)
- Line: H13CN 3-2 (259.012 GHz)
- Line: HC15N 3-2 (258.157 GHz)
- Line: DCN 4-3 (362.045 GHz)
- Line: H13C15N 4-3 (334.891 GHz)
- Line: CO 2-1 (230.538 GHz)
- External data: Disk-averaged atmospheric temperature profile from CO (2-1) retrieval  
  > "We assume the disk-averaged atmospheric temperature profile derived by (cite: serigano16) using an April 2014 observation of the CO (2-1) line" (Spectral Line Modeling and Results) [from (cite: serigano16)]
- External data: Reference atmosphere and collision-induced absorption parameters  
  > "The reference atmosphere and collision-induced absorption parameters used in this paper are the same as in (cite: teanby13)" (Spectral Line Modeling and Results) [from (cite: teanby13)]
- External data: Line wavenumbers and intensities from CDMS-recommended laboratory data  
  > "Spectral line wavenumbers and intensities were taken from (cite: ahrens02), (cite: brunken04), and (cite: fuchs04)" (Spectral Line Modeling and Results) [from (cite: ahrens02), (cite: brunken04), (cite: fuchs04)]
- External data: Lorentz half-width 0.13 at 296 K and temperature exponent 0.75  
  > "The Lorentzian broadening half-width at 296 K ($\gamma$) was assumed to be 0.13 (cite: yang08)" (Spectral Line Modeling and Results) [from (cite: yang08), (cite: devi04)]

## Processing

### Calibration

- pipeline or manual: standard reduction by NAASC  
  > "Each dataset was flagged and calibrated by the North American ALMA Science Center using the standard data reduction procedures" (Observations and Data Processing)
- casa version: CASA 4.5.0  
  > "NRAO’s CASA software version 4.5.0" (Observations and Data Processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Butler-JPL-Horizons 2012 model  
  > "The observed continuum level was scaled to match the Butler-JPL-Horizons 2012 flux model" (Observations and Data Processing)
- flux scale uncertainty: within 15%  
  > "which is expected to be accurate to within 15% (see ALMA Memo #594)" (Observations and Data Processing)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Hogbom  
  > "Deconvolution of the ALMA point-spread function was performed using the Hogbom algorithm with natural visibility weighting." (Observations and Data Processing)
- weighting robust: natural weighting  
  > "Hogbom algorithm with natural visibility weighting" (Observations and Data Processing)
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

- Data processing procedure  
  > "The data processing procedure we used was very similar to that of (cite: cordiner15)." (Observations and Data Processing) [from (cite: cordiner15)]
- Ethyl cyanide interloper modeled with 300 km step function  
  > "This interloping line is modeled using a 300 km step function for the vertical profile as recommended by (cite: cordiner15)." (Spectral Line Modeling and Results) [from (cite: cordiner15)]
- Limb-brightening disk-averaging method  
  > "We follow the method described in the Appendix of (cite: teanby13)" (Spectral Line Modeling and Results) [from (cite: teanby13)]
- HCN saturation law  
  > "We assume the same HCN saturation law as (cite: marten02) and (cite: gurwell04)" (Spectral Line Modeling and Results) [from (cite: marten02), (cite: gurwell04)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA execution blocks/scheduling blocks per line
- Extraction region radius per dataset
- Line-free window used for continuum rescaling
- A priori HCN profile
- Mask and clean threshold/iterations, cell and image size
- Whether the continuum was subtracted
- NEMESIS version and configuration files

## Analysis recipe

1. **Extract disk-averaged spectra**: Integrate each channel within a circular region covering pixels above 3 sigma; Doppler correct to Titan rest frame; convert to radiance using Horizons distance and velocity  
  > "A disk-averaged spectrum was extracted from each data cube by integrating each channel within a circular region around the center of Titan" (Observations and Data Processing)
   - software: CASA
   - assumption: Seasonal changes negligible over the period  
  > "we assume in our analysis that seasonal temperature and gas abundance changes are negligible" (Observations and Data Processing)
   - fitting: _not stated_
   - validation: _not stated_
2. **Retrieve HCN vertical abundance profile**: NEMESIS iterative chi-square minimization on the HCN (1-0) line with limb-brightening weighted sum, fixed temperature profile  
  > "NEMESIS uses an iterative $\chi ^2$ minimization technique that relies on both the level of deviation from the a priori setup and the quality of the fit to the data." (Spectral Line Modeling and Results)
   - software: NEMESIS
   - parameter: A priori error 200%, smoothing three scale heights; 72 averaging points  
  > "The error on the a priori profile is taken to be 200% with a smoothing parameter of three scale heights." (Spectral Line Modeling and Results); "Seventy-two averaging points are sufficient to accurately model the spectrum for the strongest observed lines." (Spectral Line Modeling and Results)
   - assumption: Isothermal 160 K above 500 km; relax to Huygens below 80 km; HCN saturation below ~80 km  
  > "above 500 km an isothermal 160 K atmosphere is assumed in absence of firm temperature constraints" (Spectral Line Modeling and Results)
   - fitting: NEMESIS optimal estimation, chi-square  
  > "NEMESIS uses an iterative $\chi ^2$ minimization technique that relies on both the level of deviation from the a priori setup and the quality of the fit to the data." (Spectral Line Modeling and Results)
   - validation: Perturbed a priori profile by two orders of magnitude in each direction; similar solution recovered  
  > "we found that in all cases NEMESIS derived a vertical profile similar to the original best-fit solution" (Spectral Line Modeling and Results)
3. **Derive isotopic ratios**: Retrieve scaling factor of the HCN profile shape for each isotopologue line; ratio equals the scale factor  
  > "The vertical profiles for the isotopologues were constrained to have the same shape as the vertical profile derived for HCN." (Spectral Line Modeling and Results)
   - software: NEMESIS
   - parameter: Line strength uncertainty 2%; gamma and tau errors <10%  
  > "We conservatively assume an uncertainty in each of the intrinsic line strengths of 2% (cite: maki95)." (Spectral Line Modeling and Results)
   - assumption: Constant isotopic ratio with altitude; same gamma and tau for all isotopologues  
  > "The assumption that $\gamma$ and $\tau$ have the same value for every isotopologue is also imperfect" (Spectral Line Modeling and Results)
   - fitting: _not stated_
   - validation: Errors added in quadrature; DCN checked with 200 and 400 km step interloper models  
  > "We assume all of these errors are uncorrelated and add them in quadrature to our final error estimate." (Spectral Line Modeling and Results)

## Software

- **CASA** 4.5.0: Calibration and imaging  
  > "NRAO’s CASA software version 4.5.0" (Observations and Data Processing)
- **NEMESIS** : Line-by-line radiative transfer and retrieval  
  > "line-by-line radiative transfer module of the NEMESIS atmospheric retrieval code (cite: irwin08)" (Spectral Line Modeling and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12C/13C in HCN | 89.8 | 2.8 | dimensionless | 3 | $^{12}$C/$^{13}$C = 89.8 $\pm$ 2.8 |
| 14N/15N in HCN | 72.3 | 2.2 | dimensionless | 3 | $^{14}$N/$^{15}$N = 72.3 $\pm$ 2.2 |
| D/H in HCN | 2.5e-4 | 0.2e-4 | dimensionless | 3 | D/H = (2.5 $\pm$ 0.2)$\times$10$^{-4}$ |
| HCN/H13C15N | 5800 | 270 | dimensionless | 3 | HCN/H$^{13}$C$^{15}$N = 5800 $\pm$ 270 |
| NEMESIS continuum offset | ~3% | not stated | percent | 0 | The continuum emission from Titan modeled by NEMESIS is $\sim$3% less than the continuum level of the data |

## Qualitative findings

- First detection of H13C15N on Titan; DCN detection confirmed  
  > "We report the detection of a new HCN isotopologue on Titan, H$^{13}$C$^{15}$N, and confirm an earlier report of detection of DCN." (abstract)

## Claim tuples

- H: Does HCN on Titan show nitrogen fractionation relative to N2? | E: Retrieve 14N/15N from HC15N vs HCN | R: 14N/15N = 72.3 ± 2.2 | F: Factor ~2.3 lower than in N2; no evidence of altitude fractionation | **supported**
- H: Is carbon fractionated in HCN? | E: Retrieve 12C/13C | R: 89.8 ± 2.8 | F: No fractionation from the protosolar value | **supported**
- H: Is D enriched in HCN relative to CH4? | E: Retrieve D/H from DCN | R: (2.5 ± 0.2)e-4 | F: Factor ~2 enrichment vs methane | **supported**

## Reasoning

- Why this data: ALMA flux calibration observations of Titan are abundant in the archive  
  > "a wealth of observations of the moon covering different parts of the submillimeter spectrum are available in the ALMA Science Archive" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Unquantified systematic errors may remain  
  > "Unquantified systematic errors in the derived vertical profile and isotopic ratios may remain." (Spectral Line Modeling and Results)
- Caveat (inferred, ours): Disk-averaged modeling ignores spatial variation
- Caveat (inferred, ours): Lines observed on different dates with different temperatures and configurations
- Caveat (inferred, ours): HCN abundance above 500 km unconstrained
- Caveat (inferred, ours): Constant isotopic ratio with altitude assumed

## Reproducibility

- Data public (paper): publicly available ALMA datasets  
  > "We downloaded publicly available ALMA datasets taken between 3 April and 8 July 2014" (Observations and Data Processing)
- Products in archive: _not stated_
- Missing: NEMESIS configuration and a priori profile
- Missing: Extraction aperture sizes
- Missing: Line-free window for continuum scaling
- Data volume (inferred): tens of GB
- Score (inferred): 6/5, Public data and a clear recipe, but NEMESIS setup details and several choices are missing.
- Rediscovery candidate: yes, Data are public, the recipe is mostly described and the results are numeric.

## Links

- Method: (cite: irwin08) (NEMESIS retrieval code)
- Method: (cite: teanby13) (Limb-brightening method and reference atmosphere)
- Companion: (cite: cordiner15) (Similar processing of ALMA Titan data)
- Companion: (cite: serigano16) (Temperature profile from CO)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
