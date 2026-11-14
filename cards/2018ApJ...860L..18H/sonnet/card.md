# Stellar and Molecular Gas Rotation in a Recently Quenched Massive Galaxy at z ∼ 0.7

`2018ApJ...860L..18H` | The Astrophysical Journal Letters 2018 | first author: Hunt, Qiana | arXiv: 1804.10216 | DOI: 10.3847/2041-8213/aaca9a

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: What do the stellar kinematics, age distribution and molecular gas kinematics of a massive post-starburst galaxy at z=0.747 say about how its star formation was quenched?  
  > "We look for indicators of star formation suppression mechanisms in the stellar kinematics and age distribution of the galaxy obtained from spatially resolved Gemini Integral-Field spectra and in the gas kinematics obtained from ALMA." (abstract)
- Target **SDSS J0912+1523**: coordinates _not stated_; z/distance z = 0.747  
  > "with z = 0.747 and i$_{AB}$ = 18.6 mag" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00126.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.7"x2.4" for CO(2-1)  
  > "With a spatial resolution of 1.7$\ensuremath{''}\times$2.4$\ensuremath{''}$, we do not know the spatial distribution of gas." (3.2 Kinematics)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 2-1 (not stated)
- Other facility **Gemini North GMOS-N IFU**: Spatially resolved optical IFU datacube used for stellar kinematics and Hdelta/Dn4000 indices  
  > "The target was observed using GMOS-N in one-slit IFU mode with the R400 grating" (2 Data)
- Other facility **SDSS**: Parent PSB sample and spectral indices for comparison  
  > "Our measurements are in agreement with the spectral indices obtained from the SDSS data in (cite: suess17)." (3.1 Spectral Indices)
- Other facility **LEGA-C**: Comparison sample of quiescent galaxies for rotational support  
  > "a sample of quiescent galaxies at 0.6 $<~z~<$ 1.0 from the LEGA-C spectroscopic survey (cite: vdWel16)" (3.2 Kinematics)
- External data: ALMA CO(2-1) data, gas mass (3.4±0.2)e10 Msun, gas fraction ~30%  
  > "Recent ALMA observations of SDSS J0912+1523 by (cite: suess17) uncovered a substantial amount of cold gas" (3.2 Kinematics) [from Suess et al. 2017 (cite: suess17)]
- External data: SFR of 2.1±0.8 Msun/yr from [OII]  
  > "low SFR of 2.1 $\pm$ 0.8 M$\rm _{\odot} ~yr^{-1}$ measured previously by (cite: suess17)" (3.1 Spectral Indices) [from Suess et al. 2017 (cite: suess17)]

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

- ALMA data and its reduction taken from Suess et al. 2017  
  > "the analysis of ALMA data first presented in (cite: suess17)" (Discussion and Conclusions) [from (cite: suess17)]
- Gemini data reduction procedure  
  > "using the procedure described by (cite: lena14)" (2 Data) [from (cite: lena14)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging, and CASA version
- How the CO(2-1) velocity field was derived (moment method, channel width, S/N cut)
- Frequency setup, array configuration, integration time of ALMA data
- Gas-mass conversion assumptions (alpha_CO)

## Analysis recipe

1. **Fit stellar kinematics per Voronoi bin**: pPXF fit of SSP templates to median spectrum of each Voronoi bin; uncertainties from 100 Monte Carlo resamplings  
  > "The uncertainties in velocity and $\sigma$ are derived using 100 iterations of Monte Carlo resampling" (2.1 Spatially Resolved Kinematics)
   - software: pPXF
   - parameter: Voronoi target S/N = 6; spaxel S/N threshold 0.3  
  > "We set the target S/N of the spatial bins to 6." (2 Data)
   - assumption: Solar metallicity templates  
  > "We assume solar metallicity and mask the strong telluric features in the galaxy spectrum." (2.1 Spatially Resolved Kinematics)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit smooth rotation curve and rotational support**: Kinemetry on 2D velocity field; compute |V5|/sigma0 and compare with LEGA-C  
  > "we calculate rotational support ($\rm|V_{5}|$/$\sigma_{0}$)" (3.2 Kinematics)
   - software: Kinemetry
   - fitting: _not stated_
   - validation: Compared with LEGA-C; beam smearing simulated on CALIFA cubes  
  > "estimate that our measured $\rm|V_{5}|$/$\sigma_{0}$ of SDSS J0912+1523 (green star) will underestimate the intrinsic value by a factor of $\sim$1.3" (3.2 Kinematics)

## Software

- **pPXF** : stellar kinematics  
  > "is used to extract stellar kinematics from each Voronoi bin" (2.1 Spatially Resolved Kinematics)
- **Kinemetry** : smooth velocity field  
  > "using `Kinemetry` in IDL (cite: kraj06)" (3.2 Kinematics)
- **lick_ew (EZ_Ages)** : Hdelta_A equivalent width  
  > "with the `lick_ew` routine from the IDL EZ_Ages package" (2.2 Measuring Age-Sensitive Spectral Indices)
- **Gemini IRAF** : Gemini data reduction  
  > "We reduced the data with `gemtools` and `gmos` in the Gemini `IRAF` package" (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| central Hdelta_A | ~8.3 | ~0.7 typical | Angstrom | 0 | We measure a central H$\delta_{A}$ of $\sim$8.3 Å and D$_n$4000 of  $\sim$1.18. |
| central sigma0 | 301 | 16 | km/s | 1 | we measure $\sigma_{0}$ = 301 $\pm$ 16 km s$^{-1}$ and V$_{5}$ = 88 $\pm$ 5 km s$^{-1}$ |
| V5 | 88 | 5 | km/s | 2 | V$_{5}$ = 88 $\pm$ 5 km s$^{-1}$ |
| V10 | 213 | 11 | km/s | 2 | When measured at 10 kpc, V$_{10}$ = 213 $\pm$ 11 km s$^{-1}$. |

## Qualitative findings

- Molecular gas is aligned with stars and shows no evidence of strong outflows  
  > "The molecular gas is aligned with the stellar component, and we see no evidence of strong gas outflows." (abstract)

## Claim tuples

- H: Does the PSB retain stellar rotation and an age gradient? | E: Gemini IFU pPXF and Hdelta analysis | R: Significant rotation, flat Hdelta_A within 5 kpc | F: Rotating galaxy with no age gradient | **supported**
- H: Is the gas aligned with stars? | E: Compare ALMA CO(2-1) velocity field with stellar field | R: Similar amplitudes and rotation | F: Gas and stars likely aligned, resolution coarse | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas resolution too coarse to know its spatial distribution  
  > "With a spatial resolution of 1.7$\ensuremath{''}\times$2.4$\ensuremath{''}$, we do not know the spatial distribution of gas." (3.2 Kinematics)
- Caveat (inferred, ours): Gas-stellar alignment judged by eye from low-resolution maps
- Caveat (inferred, ours): No ALMA processing details given
- Caveat (inferred, ours): Seeing limits Hdelta gradient conclusion

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA reduction and moment map details (in Suess et al. 2017)
- Missing: Conroy SSP templates not public (Bezanson et al. in prep)
- Data volume (inferred): ALMA ~ few GB; Gemini cube small
- Score (inferred): 2/5, ALMA part is only a figure from earlier work; the Gemini analysis is the main content.
- Rediscovery candidate: no, ALMA role is minor and key templates are unpublished.

## Links

- Method: Suess et al. 2017 (cite: suess17) (ALMA observations and gas properties)
- Companion: Bezanson et al. 2018 (cite: bez2018) (LEGA-C rotational support comparison)
- Related: LEGA-C
- Related: CALIFA

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
 "codes_not_in_obscore": [
  "2016.1.00126.S"
 ],
 "obscore_codes_not_in_card": [
  "2016.1.01126.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 21,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
