# Morphology and kinematics of the gas envelope of the Mira binary W Aquilae

`2016RAA....16..106H` | Research in Astronomy and Astrophysics 2016 | first author: Hoai, Do Thi | arXiv: 1601.01439 | DOI: 10.1088/1674-4527/16/7/106

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What are the morphology and kinematics of the CO(3-2) gas envelope of the Mira binary W Aql, from spatially resolved Doppler velocity spectra?  
  > "The present work presents an analysis of these data, which provide for the first time spatially resolved Doppler velocity spectra." (Introduction)
- Target **W Aql**: coordinates _not stated_; z/distance ~400 pc (adopted; literature range 230-610 pc)  
  > "The distance from Earth is poorly known, with values between 230 pc and 610 pc being quoted in the literature" (Introduction); "Retaining a distance of $\sim$400 pc, the projected distance between the central star and its companion is of the order of $\sim$200 AU." (Introduction); distance from literature, indirectly from luminosity-period relation  
  > "The distance from Earth is poorly known, with values between 230 pc and 610 pc being quoted in the literature" (Introduction); "Retaining a distance of $\sim$400 pc, the projected distance between the central star and its companion is of the order of $\sim$200 AU." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: CO(3-2), 2 km/s bins between -55.5 and 4.5 km/s  
  > "The line Doppler velocity spectra, are available in each case in bins of $2$ km s$^{-1}$ between $-55.5$ km s$^{-1}$ and $4.5$ km s$^{-1}$." (2 Observations)
- continuum bandwidth: 15.8 GHz  
  > "Also available are continuum flux densities averaged over a 15.8 GHz interval." (2 Observations)
- arrays: ALMA normal array and ACA (compact array)  
  > "one with the normal array (ALMA) and the other with the compact array (ACA)" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.1''x1.0'' (ALMA), 4.9''x2.6'' (ACA)  
  > "configurations giving beams of respective angular dimensions of $1.1''$$\times$$1.0''$ and $4.9''$$\times$$2.6''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: five minutes each  
  > "each of five minutes duration" (2 Observations)
- observing dates: 6 and 20 March 2014  
  > "Two sets of observations were made on March 6$^{\text{th}}$ and 20$^{\text{th}}$, 2014" (2 Observations)
- pi or archival as stated: public ALMA data retrieved via JVO portal  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ" (footnote 1)
- Line: CO J=3-2 (not stated)
- Other facility **APEX**: single-dish CO spectrum (Ramstedt et al. 2009) for comparison  
  > "The latter corresponds to the APEX single dish observation of Ramstedt et al. (2009)" (2 Observations)
- Other facility **HST**: B-band 435 nm image showing companion  
  > "A high-resolution Hubble Space Telescope[^2] B-band image taken in 2004 at 435 nm" (Introduction)
- External data: UV dissociation distance of CO r1/2 ~1.5e17 cm  
  > "From Mamon et al. (1988) we obtain an effective UV dissociation distance for CO molecules $r_{1/2}\sim$ 1.5 10$^{17}$ cm" (4 Large distances) [from Mamon et al. (1988)]
- External data: Space velocity V_LSR=21.6±4.1 km/s of W Aql  
  > "the space velocity of W Aql is $V_{LSR}=21.6\pm4.1$ km s$^{-1}$" (5 Discussion) [from Mayer et al. (2013) (cite: May2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Data reduced by ALMA staff to clean maps  
  > "The data have been reduced by the ALMA staff to clean maps using pixel sizes of $0.1''\times0.1''$ (ALMA) and $0.8''\times0.8''$ (ACA) respectively." (2 Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1'' (ALMA), 0.8'' (ACA)  
  > "using pixel sizes of $0.1''\times0.1''$ (ALMA) and $0.8''\times0.8''$ (ACA) respectively" (2 Observations)
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

- CASA/pipeline version and calibrators
- Imaging parameters (weighting, deconvolver, masks) of the delivered maps
- Continuum subtraction and line-free channels
- Rest frequency adopted and exact velocity reference
- Fit method/uncertainties for sine and exponential fits
- Exact data product file names and whether ALMA and ACA were combined

## Analysis recipe

1. **Select usable radii and velocities**: Compare azimuthally averaged flux vs R for ALMA and ACA to find short-spacing cutoff; restrict ALMA to R<4'' and velocities -14 to 18 km/s  
  > "Accordingly, in what follows, we restrict the analysis of the ALMA data to angular distances from the central star not exceeding $4''$" (2 Observations)
   - parameter: V_x* = 3.2 km/s mean velocity of selected sample  
  > "The mean velocity of the selected sample of observations is $V_x^{\ast}$=3.2 km s$^{-1}$." (2 Observations)
   - fitting: _not stated_
   - validation: Compared ACA profile with APEX single-dish profile  
  > "While the line profile observed by ACA is in good agreement with that observed in the single dish APEX data" (2 Observations)
2. **Map flux and mean velocity vs azimuth**: Average flux and mean Doppler velocity in R bins and 15 deg phi bins; fit sine waves V0+V1cos(phi-phi0)  
  > "Sine wave fits of the form $<V_x -V_ x^\ast>=V_0 +V_ 1 \cos(\varphi-\varphi_0)$" (3 Morphology)
   - fitting: sine wave fit, method not stated  
  > "Sine wave fits of the form $<V_x -V_ x^\ast>=V_0 +V_ 1 \cos(\varphi-\varphi_0)$ give $V_0 =0.87$ km s$^{-1}$, $V_1 =0.75$ km s$^{-1}$ and $\varphi_0 =176^\circ$ for $R<2''$" (Morphology and kinematics of the CSE at short distances ($R<4''$))
   - validation: fit quality noted poor for 2''<R<4''  
  > "However, the quality of the fit is poor in the latter case" (3 Morphology)
3. **Radial profile and elongation direction**: Exponential fit A0 exp(-R/R0) for R<3''; elongation angles maximizing flux-weighted cos^2 and velocity asymmetry in 0.5'' R bins  
  > "directions of elongation are defined as the values of angle $\varphi_0$ that maximize the mean values of $\cos^2(\varphi-\varphi_0)$" (3 Morphology)
   - fitting: exponential fit, method not stated  
  > "An exponential fit of the form $A_0 e^{-R/R_0}$ for $R<3''$ gives $A_0=4.18$ Jy km s$^{-1}$ arcsec$^{-2}$ and $R_0=1.08''$." (Morphology and kinematics of the CSE at short distances ($R<4''$))
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sine fit R<2'': V0, V1, phi0 | V0=0.87, V1=0.75 km/s, phi0=176 deg | not stated | km/s, deg | 2 | $V_0 =0.87$ km s$^{-1}$, $V_1 =0.75$ km s$^{-1}$ and $\varphi_0 =176^\circ$ for $R<2''$ |
| Sine fit 2''<R<4'': V0, V1, phi0 | V0=-1.23, V1=1.71 km/s, phi0=128 deg | not stated | km/s, deg | 2 | $V_0 =-1.23$ km s$^{-1}$, $V_1 =1.71$ km s$^{-1}$ and $\varphi_ 0 =128^\circ$ for $2''<R<4''$ |
| Exponential fit amplitude A0 | 4.18 | not stated | Jy km/s arcsec^-2 | 3 | $A_0=4.18$ Jy km s$^{-1}$ arcsec$^{-2}$ and $R_0=1.08''$ |
| Exponential scale length R0 | 1.08 | not stated | arcsec | 3 | $A_0=4.18$ Jy km s$^{-1}$ arcsec$^{-2}$ and $R_0=1.08''$ |
| Line profile slope in central region | ~2 | not stated | % per km/s | 1 | the red-shifted side being enhanced with respect to the blue-shifted side by $\sim2$% per km s$^{-1}$ |
| Velocity offset R<2'' vs 2''<R<4'' | ~2.1 | not stated | km/s | 2 | the $R<2''$ region is red-shifted with respect to the $2''<R<4''$ region by $\sim2.1$ km s$^{-1}$ |
| ACA extended emission level | ~32 | not stated | mJy km/s arcsec^-2 | 1 | extending up to at least $22''$ at a typical level of $\sim32$ mJy km s$^{-1}$ arcsec$^{-2}$ |

## Qualitative findings

- Emission is elongated NE/SW with a velocity gradient perpendicular to the star-companion line; elongation and velocity gradient rotate with radius.  
  > "one evolves from a morphology elongated along the east/west direction with a velocity gradient directed along this same direction to a morphology elongated along the north-east/south-west direction" (3 Morphology)

## Claim tuples

- H: Is the CSE of W Aql asymmetric in morphology and kinematics at short distances? | E: Azimuthal analysis of ALMA CO(3-2) maps for R<4'' | R: Flux enhancements and velocity asymmetry with sine-wave amplitudes ~0.75-1.7 km/s, direction evolving with R | F: Complex, non-spherical wind structure; expansion vs rotation interpretation cannot be distinguished | **supported**
- H: Does CO emission extend to large distances consistent with dust? | E: ACA flux vs phi in R bins 5-20'' | R: Enhancements west for 5-10'' and at ±60° from east for 15-20'' | F: Consistent with far-IR dust emission, but details such as a spiral are not revealed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Short observing time, single CO line, optical depth effects unmodelled, short-spacing problem in ALMA data  
  > "longer observation times, preferably including lines associated with several CO excitations, are needed" (5 Discussion)
- Caveat (inferred, ours): No uncertainties on fits
- Caveat (inferred, ours): No radiative transfer despite likely optical thickness
- Caveat (inferred, ours): Distance poorly known
- Caveat (inferred, ours): Offset correction and binning choices arbitrary
- Caveat (inferred, ours): Only five-minute snapshots

## Reproducibility

- Data public (paper): Public ALMA data retrieved via JVO  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ" (footnote 1)
- Products in archive: _not stated_
- Missing: Fit procedures and weights
- Missing: Exact data products used
- Missing: Software used
- Data volume (inferred): <1 GB (clean maps/cubes)
- Score (inferred): 4/5, Public data and simple analysis, but unspecified products, software and fitting details.
- Rediscovery candidate: no, Recipe lacks software, product and fitting detail, though data are public.

## Links

- Companion: Mayer et al. (2013) (cite: May2013) (Dust CSE structure and space velocity of W Aql)
- Companion: Ramstedt et al. (2009) (cite: Ram2009) (APEX single-dish CO comparison)
- Related: COSAS programme

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 27,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
