# Deuterated Molecules in Orion KL from Herschel/HIFI

`2013ApJ...777...85N` | The Astrophysical Journal 2013 | first author: Neill, Justin L. | arXiv: 1308.5203 | DOI: 10.1088/0004-637X/777/2/85

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: What are the abundances and deuterium fractionation of NH2D, HDCO, CH2DOH and CH3OD in the Orion KL Hot Core and Compact Ridge, from the Herschel/HIFI fullband survey?  
  > "We present a comprehensive study of the deuterated molecules detected in the fullband HIFI survey of the Orion KL region." (abstract)
- Target **Orion KL**: coordinates HIFI pointing: RA(J2000) 05h35m14.3s, Dec -05d22m33.7s  
  > "with a pointing position of $\alpha_{\textnormal{J2000}} = 05^\textnormal{h} 35^\textnormal{m} 14^\textnormal{s}.3$, $\delta_{\textnormal{J2000}} = -05^\circ 22'33.7''$" (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: ALMA Science Verification survey, 214–247 GHz; NH2D 239.848 GHz and 13CH3OH 235.881 GHz images  
  > "An Atacama Large Millimeter/Submillimeter Array (ALMA) survey of Orion KL (214–247 GHz) collected as part of its Science Verification" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: NH2D image 1.76'' x 1.16''; 13CH3OH image 1.66'' x 0.94''; continuum 1.86'' x 1.37''  
  > "The spectral resolution of the NH$_2$D image was $1.76'' \times 1.16''$, and $1.66'' \times 0.94''$ for the $^{13}$CH$_3$OH image." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: NH2D 3_22^- - 3_12^+ (ortho) (239848.1 MHz)
- Line: 13CH3OH not stated (235.881 GHz)
- Other facility **Herschel/HIFI (HEXOS)**: Fullband 480–1280 GHz survey of Orion KL used for all abundance derivations  
  > "The HIFI survey of Orion KL used in this work covers the frequency ranges 480–1280, 1426–1535, and 1573–1906 GHz." (Observations)
- Other facility **NRAO 12 m Turner 2 mm survey**: J=2-1 H2CO and H2 13CO lines to break excitation degeneracy  
  > "we also include in our models the three $J = 2-1$ transitions of both H$_2$CO and H$_2$$^{13}$CO measured by the Turner 2 mm (130–170 GHz) survey program" (Formaldehyde)
- External data: HDO/H2O ratios in Hot Core and Compact Ridge  
  > "In this table the HDO/H$_2$O ratios derived for the Hot Core and Compact Ridge from (cite: neill13) are also included." (Discussion) [from (cite: neill13)]
- External data: NH3 centimeter inversion line data for column density  
  > "we use the centimeter inversion transitions, which have been observed going over a wide range in $J$ and $K$" (Ammonia) [from (cite: hermsen88b; wilson93)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Full calibrated measurement set from the ALMA science verification site used  
  > "The full calibrated measurement set is available at <https://almascience.nrao.edu/alma-data/science-verification>." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: CLEAN, Briggs robust = 0.0  
  > "the CLEAN algorithm with robust weighting and a Briggs parameter of 0.0 was used for deconvolution" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum estimated from line-free channels near each transition  
  > "the continuum emission as estimated from line-free channels near each transition was subtracted" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation details and HIFI data reduction  
  > "Further details of the observation can be found in, e.g., (cite: fortman12b; neill13)." (Observations) [from (cite: fortman12b; neill13); Crockett et al. (2013b, in preparation)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (cell, image size, mask, niter)
- line-free channel ranges
- ALMA configuration and integration time
- Fullband HIFI model (Crockett 2013b) unpublished
- CH3OD spectroscopy unpublished

## Analysis recipe

1. **Fit Gaussian line parameters in HIFI spectra**: Multi-Gaussian fits to line profiles, with blends removed using a fullband model  
  > "the contributions of different components are separated by summing multiple Gaussians to model the observed lineshapes" (Modeling approaches)
   - software: HIPE
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive column densities and D/H**: Optically thin upper-level column densities for NH2D with RADEX correction factor; RADEX non-LTE for H2CO/HDCO; XCLASS LTE for methanol  
  > "This factor is calculated on the basis of non-LTE statistical equilibrium calculations with the RADEX code" (Ammonia)
   - software: RADEX, XCLASS
   - parameter: NH2D: Tkin 200 K, n(H2) 1e8 cm-3 for correction factor  
  > "A kinetic temperature of 200 K and a H$_2$ density of $10^8$ cm$^{-3}$ are used for the correction factor calculation" (Ammonia)
   - assumption: 12C/13C = 60; H2CO ortho:para 3:1  
  > "we assume a $^{12}$C/$^{13}$C ratio of 60 (cite: persson07), and an *ortho*:*para* ratio of 3:1" (Formaldehyde)
   - fitting: _not stated_
   - validation: ALMA NH2D map compared against HIFI population diagram trend  
  > "the transition detected with ALMA shown in Figure 3 broadly follows the trend in a population diagram of the HIFI transitions" (Ammonia)

## Software

- **CLEAN** : Deconvolution of ALMA images  
  > "the CLEAN algorithm with robust weighting and a Briggs parameter of 0.0 was used for deconvolution" (Observations)
- **HIPE** 5.0: HIFI data processing  
  > "All data presented here were processed with HIPE (cite: ott10) version 5.0" (Observations)
- **RADEX** : Non-LTE excitation modeling  
  > "non-LTE statistical equilibrium calculations with the RADEX code (cite: vandertak07)" (Ammonia)
- **XCLASS** : LTE modeling of methanol  
  > "we use LTE modeling in XCLASS to derive the column densities in each of these species" (Methanol)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total NH2D column density, Hot Core | 8.8e15 | 1.7e15 | cm-2 | 2 | or a total column density of $(8.8 \pm 1.7) \times 10^{15}$ cm$^{-2}$ |
| [NH2D]/[NH3] Hot Core | 6.8e-3 | 2.4e-3 | dimensionless | 2 | This yields a \[NH$_2$D\]/\[NH$_3$\] ratio of $(6.8 \pm 2.4) \times 10^{-3}$ in the Hot Core. |
| [CH2DOH]/[CH3OD] Compact Ridge | 1.2 | 0.3 | dimensionless | 2 | The \[CH$_2$DOH\]/\[CH$_3$OD\] ratio in the Compact Ridge is found to be $1.2 \pm 0.3$. |

## Qualitative findings

- Hot Core generally has lower deuterium fractionation than the Compact Ridge  
  > "The Hot Core generally has lower deuterium fractionation than the Compact Ridge, suggesting a slightly warmer origin" (abstract)

## Claim tuples

- H: Do water and organics have similar D/H in Orion KL? | E: HIFI multi-transition abundances of deuterated species | R: Compact Ridge D/H of (2-8)e-3 for water, formaldehyde, methanol | F: Similar fractionation, consistent with grain-mantle origin | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): NH3 collisional rates used as proxy for NH2D; approximate  
  > "This treatment is only approximate because of the significant differences in the energy level structures and allowed selection rules for NH$_2$D and NH$_3$" (Ammonia)
- Caveat (inferred, ours): ALMA used only for qualitative maps
- Caveat (inferred, ours): LTE/optically thin assumptions and source sizes drive uncertainties

## Reproducibility

- Data public (paper): ALMA SV measurement set public  
  > "The full calibrated measurement set is available at <https://almascience.nrao.edu/alma-data/science-verification>." (Observations)
- Products in archive: _not stated_
- Missing: Crockett 2013b fullband model
- Missing: ALMA imaging parameters
- Data volume (inferred): ALMA SV ms tens of GB; HIFI spectra small
- Score (inferred): 2/5, ALMA minor and HIFI-based analysis depends on unpublished fullband model.
- Rediscovery candidate: no, Main results rely on HIFI data and unpublished models, not ALMA.

## Links

- Companion: (cite: neill13) (HDO and H2O abundances in Orion KL from HIFI and ALMA)
- Related: HEXOS
- Related: ALMA Science Verification Orion KL

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 24,
  "rate": 0.387
 },
 "evidence_ok": true
}
```
