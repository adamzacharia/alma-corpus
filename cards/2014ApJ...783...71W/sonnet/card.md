# Karl G. Jansky Very Large Array Observations of Cold Dust and Molecular Gas in Starbursting Quasar Host Galaxies at z ~ 4.5

`2014ApJ...783...71W` | The Astrophysical Journal 2014 | first author: Wagg, J. | arXiv: 1401.1213 | DOI: 10.1088/0004-637X/783/2/71

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the cold molecular gas content and the origin of the 44 GHz (rest-frame 250 GHz) continuum in the z~4.5 quasar host galaxies BR1202-0725 and BRI1335-0417?  
  > "In this work we present VLA observations of rest-frame 250 GHz continuum and redshifted CO *J*=2–1 line emission in the quasar host galaxies, BR1202-0725 and BRI1335-0417." (Introduction)
- Target **BR1202-0725**: coordinates _not stated_; z/distance z = 4.7  
  > "BR1202-0725 at $z = 4.7$ (a starburst galaxy and quasar pair)" (abstract); distance from _not stated_
- Target **BRI1335-0417**: coordinates _not stated_; z/distance z = 4.4  
  > "BRI1335-0417 at $z=4.4$ (also hosting a quasar)" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00006.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (VLA) (230.538 GHz)
- Other facility **VLA (Q-band)**: 44 GHz continuum and CO J=2-1 observations (project 13A-012)  
  > "Observations were carried out with 27 elements of the VLA on four dates in January and February of 2013" (Observations and data reduction)
- Other facility **Herschel SPIRE**: 250, 350, 500 um flux densities from archival maps  
  > "We use archival *Herschel* SPIRE submm-wavelength and lower frequency, 1.4 and 5 GHz VLA observations of our targets (project AC878)" (4.1 Continuum emission)
- External data: ALMA 340 GHz continuum and [CII] line profiles of BR1202-0725 (ALMA commissioning data)  
  > "we show the \[CII\] line profiles for the BR1202-0725 SMG and quasar host galaxy measured from recent ALMA commissioning observations" (Results) [from Wagg et al. 2012; Carilli et al. 2013; Lentati et al. 2013]

## Processing

### Calibration

- pipeline or manual: CASA pipeline (VLA data)  
  > "Standard calibration steps are carried out using a new set of *CASA* pipeline reduction procedures developed by NRAO staff." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C286 (VLA)  
  > "3C286 was used to calibrate the flux density and bandpass shape" (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (VLA)  
  > "we then use natural weighting and multi-frequency synthesis imaging to generate the continuum images" (Observations and data reduction)
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

- SED model: linear relations between SFR and synchrotron, free-free and dust components  
  > "Following Yun & Carilli (2002), we use the linear relationships between the total SFR and the three components" (4.1 Continuum emission) [from Yun & Carilli 2002; Condon 1992]
- Line luminosity definition  
  > "Following the definition of line luminosity given by Solomon et al.( 1992)" (4.2 CO J=2-1 Line Emission) [from Solomon et al. 1992]

### Not stated but needed to reproduce (our reading)

- Priors and ranges for the MultiNest SED fit
- ALMA 340 GHz data reduction and flux values used in the SED
- Beam size and rms of the ALMA map
- Flux calibration scale uncertainty
- CASA version
- Which pixels or apertures were used for SPIRE deblending

## Analysis recipe

1. **VLA imaging**: CASA pipeline calibration, natural weighting, MFS continuum from line-free spws, cubes resampled to 8 MHz  
  > "The spectral line maps are resampled to 8 MHz resolution" (Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit CO line**: Single Gaussian fit to extracted spectra for z, FWHM and integrated flux  
  > "calculated assuming the data can be decribed by a single Gaussian line profile" (Results)
   - fitting: Gaussian  
  > "which have been calculated assuming the data can be decribed by a single Gaussian line profile." (Results)
   - validation: Compared with previous CO and [CII] observations  
  > "The CO *J*=2–1 redshift and line width for the quasar BR1202-0725 South are in excellent agreement with previous observations of \[CII\] and CO line emission" (Results)
3. **SED fitting for SFR, Td, beta**: Three-component model (synchrotron, free-free alpha=-0.1, greybody) fit with MultiNest  
  > "We make use of the MultiNest algorithm to obtain our estimates of the posterior probability distributions for the spectral energy distribution parameters." (4.1 Continuum emission)
   - software: MultiNest
   - assumption: Total 350 um flux of North and South equals the SPIRE value  
  > "we impose the prior that the total 350 $\mu$m emission in BR1202-0725 North and South should be equal to the flux density measured by SPIRE" (4.1 Continuum emission)
   - fitting: Bayesian nested sampling, posterior means  
  > "We make use of the MultiNest algorithm to obtain our estimates of the posterior probability distributions for the spectral energy distribution parameters." (Analysis)
   - validation: Td priors of 40/50 K gave poor fits to 44 GHz fluxes, so free-floating fit adopted  
  > "we find that the resulting fits do a poor job of reproducing the measured 44 GHz flux densities" (4.1 Continuum emission)

## Software

- **CASA** : VLA calibration and imaging  
  > "The data reduction was performed using the *CASA* software package" (Observations and data reduction)
- **MultiNest** : SED posterior sampling  
  > "We make use of the MultiNest algorithm" (4.1 Continuum emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L'CO(2-1) BR1202-0725 North | 8.7e10 | 0.8e10 | K km s-1 pc2 | 2 | 8.7$\pm$0.8 |
| L'CO(2-1) BR1202-0725 South | 6.0e10 | 0.5e10 | K km s-1 pc2 | 2 | 6.0$\pm$0.5 |
| L'CO(2-1) BRI1335-0417 | 7.3e10 | 0.6e10 | K km s-1 pc2 | 2 | 7.3$\pm$0.6 |
| S44GHz BR1202-0725 North | 51 | 6 | uJy | 1 | 51$\pm$6 |
| S44GHz BRI1335-0417 | 40 | 7 | uJy | 1 | 40$\pm$7 |
| SFR BRI1335-0417 | 5040 | 1304 | Msun/yr | 3 | 5040$\pm$1304 |

## Qualitative findings

- 44 GHz continuum is dominated by thermal dust emission; free-free below ~20%, synchrotron up to 30%  
  > "the contribution from thermal free-free emission to the rest-frame 250 GHz continuum is" (Discussion)

## Claim tuples

- H: Is CO J=2-1 thermalized relative to CO J=5-4? | E: Compare VLA CO 2-1 luminosities with literature CO 5-4 | R: Luminosities are equal within errors | F: Line emission is thermalized | **supported**
- H: What dominates 44 GHz continuum? | E: Three-component SED fit | R: Dust 54-75% | F: Thermal dust dominates | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Flat-spectrum embedded AGN as 44 GHz source not modelled  
  > "another possibility is that the 44 GHz emission arises from a flat-spectrum AGN embedded in the starburst host galaxies" (4.1 Continuum emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Large SFR uncertainties and possible broad wings need more sensitive data  
  > "Although the uncertainties are large" (Discussion)
- Caveat (inferred, ours): SED is poorly constrained with few points; Td-beta degeneracy
- Caveat (inferred, ours): ALMA role is only comparison data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: MultiNest priors
- Missing: ALMA SV data details
- Data volume (inferred): VLA ~100s GB; ALMA SV small
- Score (inferred): 3/5, VLA-centred, SED fit priors unstated; ALMA minor.
- Rediscovery candidate: no, ALMA data are minor and the SED fit setup is incomplete.

## Links

- Method: Yun & Carilli 2002 (SED/SFR model)
- Companion: Carilli et al. 2013 (ALMA [CII] in BR1202-0725)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 24,
  "rate": 0.364
 },
 "evidence_ok": true
}
```
