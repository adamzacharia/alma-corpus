# Resolving Linear Polarization due to Emission and Extinction of Aligned Dust Grains on NGC 1333 IRAS4A with JVLA and ALMA

`2020ApJ...889..172K` | The Astrophysical Journal 2020 | first author: Ko, Chia-Lin | arXiv: 1909.09628 | DOI: 10.3847/1538-4357/ab5e79

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Which mechanisms produce multi-wavelength dust linear polarization in the Class 0 protostar IRAS4A, and why do JVLA and ALMA position angles differ by ~90 degrees in the inner 100 AU?  
  > "To further understand the polarization mechanisms of dust on various sizescales and wavelengths, we observed NGC1333 IRAS4A using Karl G. Jansky Very Large Array (JVLA)" (Introduction)
- Target **NGC1333 IRAS4A**: coordinates RA 03h29m10.550s, Dec +31d13m31.0s (J2000), pointing center  
  > "It has at least two components IRAS4A1 and IRAS4A2 separated by 1.8$''$ (527 AU)" (Introduction); "The pointing center for our target source was R.A.=03$^{\mbox{\scriptsize{h}}}$29$^{\mbox{\scriptsize{m}}}$10.550$^{\mbox{\scriptsize{s}}}$ (J2000), Decl.=+31$^{\circ}$13$'$31$''$.0 (J2000)." (2.1 JVLA Observations); z/distance 1.8'' separation = 527 AU (implies ~293 pc)  
  > "It has at least two components IRAS4A1 and IRAS4A2 separated by 1.8$''$ (527 AU)" (Introduction); "The pointing center for our target source was R.A.=03$^{\mbox{\scriptsize{h}}}$29$^{\mbox{\scriptsize{m}}}$10.550$^{\mbox{\scriptsize{s}}}$ (J2000), Decl.=+31$^{\circ}$13$'$31$''$.0 (J2000)." (2.1 JVLA Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01089.S, 2015.1.00546.S
- bands: ALMA Band 6 (1.28 mm, 234 GHz) and Band 7 (0.87 mm, 344 GHz); JVLA K, Ka, Q  
  > "at Band 6 (1.28 mm, 234 GHz) and Band 7 (0.87 mm, 344 GHz) using ALMA" (2.2 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA C40-5 (Band 6), C36-6 (Band 7); JVLA B (K, Ka), C and D (Q)  
  > "The ALMA configurations for the 1.28 mm and 0.87 mm observations are C40-5" (2.2 ALMA Observations); "in the B array configuration, and at Q band in the C and D array configuration" (2.1 JVLA Observations)
- baselines: uv range 9-865 kλ (Band 6), 14-2910 kλ (Band 7)  
  > "C40-5 with the $uv$ distance range from 9 to 865 k$\lambda$, and C36-6 with the $uv$ distance range from 14 to 2910 k$\lambda$" (2.2 ALMA Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA Band 6 2016 Nov 4; Band 7 2016 Sep 6; JVLA Q D-array 2015 Dec 21; K/Ka B-array mid-late 2016  
  > "The D array configuration observations at Q band were carried out on 2015 December 21" (2.1 JVLA Observations)
- pi or archival as stated: ALMA PIs Ching (2016.1.01089.S) and Lai (2015.1.00546.S); JVLA PI Liu  
  > "2016.1.01089.S, PI: Tao-Chung Ching" (2.2 ALMA Observations)
- Other facility **JVLA**: Full Stokes polarization at K, Ka, Q bands (projects 15B-049, 16A-109, plus Q-band C-array from Liu2016)  
  > "The B array configuration observations at K and Ka band were carried out from mid to late 2016 (project code: 16A-109, PI: Hauyu Baobab Liu)." (2.1 JVLA Observations)
- External data: Dust temperature ~20 K, optical depth ~1 envelope and >45 K background from SED fitting  
  > "Based on the SED fittings, (cite: Li2017) suggested that the envelope component has a dust temperature $T_{\mbox{\scriptsize dust}}\sim$20 K" (4 Discussion) [from (cite: Li2017)]
- External data: Outflow position angle ~-9 deg  
  > "approximately consistent with the outflow position angles of $\sim-9^{\circ}$ (cite: Ching2016)" (4 Discussion) [from (cite: Ching2016)]
- External data: JVLA Q-band C-array observations  
  > "The C array configuration observations at Q band have been introduced in (cite: Liu2016)." (2.1 JVLA Observations) [from (cite: Liu2016)]

## Processing

### Calibration

- pipeline or manual: JVLA: manual standard calibration in CASA; ALMA: calibrated by ARC  
  > "We manually followed the standard data calibration strategy using the Common Astronomy Software Applications (cite: McMullin2007) package release 5.3.0." (2.1 JVLA Observations)
- casa version: JVLA CASA 5.3.0; ALMA ARC calibration CASA 4.6.0  
  > "We utilized the $uv$ data calibrated by the ALMA Regional Center (ARC) using the CASA version 4.6.0." (2.2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: ALMA uv data calibrated by ARC used  
  > "We utilized the $uv$ data calibrated by the ALMA Regional Center (ARC)" (2.2 ALMA Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 3 iterations of phase self-cal for Q-band D array only; not for K/Ka  
  > "we performed 3 iterations of gain phase self-calibrations for the D array configuration observations at Q band" (2.1 JVLA Observations)

### Imaging

- task: CASA tclean (5.3.0)  
  > "We imaged the calibrated data using the `tclean` task of the CASA version 5.3.0." (2.3 Polarization Images)
- deconvolver: _not stated_
- weighting robust: Natural (robust 2) for main images; robust -1 (JVLA Q) and -2 (ALMA Band 6) for higher-resolution images  
  > "we made additional images using the same visibility range but with a robust = $-$1 for the JVLA Q band data and robust = $-$2 for the ALMA Band 6 data." (3 Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to 0.72'' (main) and 0.45'' (higher-resolution)  
  > "we used visibilities in the $uv$ range of 22–865 $k\lambda$ and smoothed all images to 0.72$''$ resolution." (3 Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- JVLA Q-band C-array data introduced in earlier paper  
  > "The C array configuration observations at Q band have been introduced in (cite: Liu2016)." (2.1 JVLA Observations) [from (cite: Liu2016)]
- Two-component model temperatures/opacities motivated by SED fitting  
  > "We assumed that the background component (e.g., the disk) has a $>$45 K dust temperature ($T^{bg}_{\mbox{\scriptsize dust}}$) distribution, which was also motivated by the SED fittings of (cite: Li2017)." (4 Discussion) [from (cite: Li2017)]

### Not stated but needed to reproduce (our reading)

- tclean cell size, image size, deconvolver, masking, threshold
- Gridding/weighting for natural images in individual bands, final noise levels (in a table not reproduced)
- Flux calibrators and polarization calibrators for ALMA and JVLA
- Spectral windows/continuum channels used
- How the 22-865 klambda uv-range cut was applied
- Distance adopted

## Analysis recipe

1. **Calibrate JVLA data**: Manual standard CASA calibration including polarization leakage and position angle calibration; self-cal for Q D-array  
  > "performed complex gain calibration, cross-hand delay fitting, polarization leakage calibration, and polarization position angle referencing." (2.1 JVLA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image Stokes I, Q, U and form polarization maps**: tclean images; immath for PI, P, PA; PI debiased; values kept where I and PI >3 sigma  
  > "We evaluated $PA$ as 0.5 $\arctan$ ($U$/$Q$) and $P$ as ($PI/I$)$\times$100% from where the $I$ and $PI$ intensities were both detected at $>$3 $\sigma$ significance." (2.3 Polarization Images)
   - software: CASA tclean, CASA immath
   - parameter: uv range 22-865 klambda, natural weighting, smoothed to 0.72''  
  > "we used visibilities in the $uv$ range of 22–865 $k\lambda$ and smoothed all images to 0.72$''$ resolution." (3 Results)
   - assumption: sigma_PI taken as average noise of Q and U maps  
  > "where $\sigma_{PI}$ is assumed to be the average noise level determined from the stoke $Q$ and $U$ maps for simplicity" (2.3 Polarization Images)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate optical depth from brightness temperature ratio**: TB = Tdust(1-exp(-tau)), tau scaling with wavelength with beta  
  > "We derive the optical depth ($\tau$) at 6.9 mm by assuming that the brightness temperature of dust emission is $T_{B}$ = $T_{\mbox{\scriptsize dust}} (1 - e^{-\tau})$" (4 Discussion)
   - assumption: dust opacity index beta = 2.0  
  > "where the dust opacity index $\beta$ is assumed to be 2.0" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model polarization fraction vs brightness with simple two-component model**: Analytic model with envelope tau^E, tau^B (alpha=5%) and an obscured background with Tbg varied; compared to P vs TB at 0.87 mm  
  > "This simple two components model can qualitatively explain the observed trends of $P$ at 345 GHz." (4 Discussion)
   - parameter: Tdust = 20 K x tau^0.5; alpha = 5%; foreground ~20 K, tau~1; background >45 K  
  > "We assume $\alpha$ to be a 5% constant." (4 Discussion)
   - assumption: Singular isothermal sphere, r^-1/2 temperature  
  > "Assuming that the mass volume density around IRAS4A1 can be approximated by a singular isothermal sphere" (4 Discussion)
   - fitting: No detailed fitting; curves by varying tau or Tbg  
  > "We did not intend to perform detailed fitting due to the uncertainty in the assumption of $\alpha$" (4 Discussion)
   - validation: _not stated_

## Software

- **CASA** 5.3.0 (imaging, JVLA calibration); 4.6.0 (ALMA ARC calibration): Calibration, tclean imaging, immath polarization maps  
  > "We imaged the calibrated data using the `tclean` task of the CASA version 5.3.0." (2.3 Polarization Images)
- **Numpy** : Listed in software  
  > "CASA (cite: McMullin2007), Numpy (cite: vanderWalt2011), APLpy (cite: Robitaille2012)" (Software)
- **APLpy** : Listed in software (plotting)  
  > "CASA (cite: McMullin2007), Numpy (cite: vanderWalt2011), APLpy (cite: Robitaille2012)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| TB ratio 6.9mm/0.87mm in inner 100 AU of IRAS4A1 | ~0.6 | not stated | dimensionless | 3 | our observed brightness temperature ratio $T_{B}^{\mbox{\scriptsize 6.9 mm}}$/$T_{B}^{\mbox{\scriptsize 0.87 mm}}$ is $\sim$0.6 |
| tau at 6.9 mm | ~0.92 | not stated | dimensionless | 3 | The corresponding value of $\tau^{\mbox{\scriptsize\,6.9 mm}}$ in the innermost $\sim$100 AU region of IRAS4A1 is $\sim$0.92 |
| tau at 0.87 mm | ~58 | not stated | dimensionless | 3 | the corresponding value of $\tau^{\mbox{\scriptsize\,0.87 mm}}$ is $\sim$58 |
| Inferred B-field position angle in IRAS4A1 center | ~-22 | not stated | degrees | 0 | the inferred magnetic field position angle based on the 90$^{\circ}$ rotated at 6.3–7.9 mm in the central peak of IRAS4A1 is $\sim-22^{\circ}$ |
| Band 7 polarization percentage in inner 100 AU of IRAS4A1 | ~4% | not stated | percent | 2 | the polarization percentage stops decreasing and climbs back to $\sim$4% |

## Qualitative findings

- Polarization angles at all bands agree beyond ~150 AU, tracing an hourglass field; inside ~100 AU JVLA and ALMA angles are ~90 deg offset  
  > "In the central 150 AU around IRAS4A1, the polarization position angles detected with JVLA are nearly 90$^\circ$ offset from those detected with ALMA." (3 Results)

## Claim tuples

- H: Does the 90 deg offset arise from optical depth differences (emission vs extinction by aligned grains)? | E: Compared multi-band polarization angles and brightness-temperature-based optical depths in the inner 100 AU | R: tau~0.92 at 6.9 mm vs ~58 at 0.87 mm; angles offset by ~90 deg | F: JVLA traces emission; ALMA traces extinction of background by aligned grains | **supported**
- H: Is self-scattering the polarization mechanism? | E: Argued from grain-size limits and expected polarization fractions | R: max grain size likely <100 um, scattering polarization <~1% | F: Self-scattering is probably not significant | **partially**
- H: Does polarization percentage vs brightness at Band 7 follow absorption of unpolarized warm background? | E: Two-component analytic model | R: Qualitatively reproduces P rising with TB in IRAS4A1 | F: Consistent with foreground extinction of warm background | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radiative alignment disfavored because it predicts no polarization at the central location  
  > "we disfavor the radiative alignment due to that it predicts no polarization at the central location" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Polarization percentages may be biased by beam smearing  
  > "We caution that the measurements of polarization percentage may be biased by the beam smearing." (3 Results)
- Limitation (authors): Model is not fitted in detail due to uncertainties  
  > "We did not intend to perform detailed fitting due to the uncertainty in the assumption of $\alpha$" (4 Discussion)
- Caveat (inferred, ours): Model is qualitative with fixed assumed alpha, temperatures and tau
- Caveat (inferred, ours): Scattering and radiative alignment not quantitatively excluded
- Caveat (inferred, ours): Missing flux and beam depolarization can affect P
- Caveat (inferred, ours): Mixed array and uv-range matching needed for comparison

## Reproducibility

- Data public (paper): ALMA data cited by project code; table of measurements published machine-readable  
  > "is published in its entirety in the machine-readable format." (Polarization measurements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, clean thresholds, masks)
- Missing: Calibrator details
- Missing: JVLA data access details beyond project codes
- Data volume (inferred): ~100-300 GB (two ALMA polarization datasets plus JVLA)
- Score (inferred): 3/5, Data identified and recipe broad, but imaging details are sparse and analysis is largely qualitative.
- Rediscovery candidate: no, Imaging settings incomplete and main results are mostly qualitative/model comparisons.

## Links

- Companion: (cite: Liu2016) (Earlier JVLA Q-band observations of IRAS4A)
- Companion: (cite: Li2017) (SED fitting providing temperatures and opacities)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 73,
  "stated": 39,
  "rate": 0.534
 },
 "evidence_ok": true
}
```
