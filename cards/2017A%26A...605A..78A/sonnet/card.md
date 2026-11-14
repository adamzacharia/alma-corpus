# Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models

`2017A&A...605A..78A` | Astronomy and Astrophysics 2017 | first author: Alissandrakis, C. E. | arXiv: 1705.09008 | DOI: 10.1051/0004-6361/201730953

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: sun
- Question: To derive information on the temperature structure of the solar chromosphere and compare it with existing models.  
  > "To derive information on the temperature structure of the solar chromosphere and compare it with existing models." (abstract)
- Target **Quiet Sun / full solar disk**: coordinates _not stated_; z/distance not stated (radius reduced to 1 AU)  
  > "The TP antennas observed the full solar disk (FD) within three minutes." (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: 100 and 239 GHz (3 and 1.26 mm)  
  > "full-disk ALMA data at 100 and 239 GHz (3 and 1.26 mm respectively)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: compact array: twenty-two 12-m antennas, nine 7-m antennas; 12-m total power antennas for full-disk single-dish scans  
  > "The observations were carried out in a compact array configuration, which included twenty-two 12-m antennas and nine 7-m antennas." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: single-dish beam FWHM about 27'' at 239 GHz and 60'' at 100 GHz; sampling 3'' and 6''  
  > "The full with at half maximum (FWHM) of the single dish beam is about 27$''$ at 239 and 60$''$ at 100 GHz" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: each full-disk image within three minutes  
  > "The TP antennas observed the full solar disk (FD) within three minutes." (Observations)
- observing dates: 2015 December 16, 17, 18, 20  
  > "solar commissioning activities on 2015 December 16, 17, 18, and 20" (Observations)
- pi or archival as stated: ALMA Science Verification data  
  > "released as ALMA Science Verification data in early 2017" (Observations)
- Other facility **SDO/AIA**: 1600 and 304 Å images for comparison  
  > "very similar to the AIA 1600 and 304 Å images" (Results)
- Other facility **HMI and GONG**: magnetogram and Hα images  
  > "We also give H$\alpha$ and 1600 Å images as well as a magnetogram." (Observations)
- External data: 353 GHz (0.85 mm) center-to-limb measurements included in inversion  
  > "we included the measurements of Bastian et al. (1993) at 353 GHz (0.85 mm) in our data set." (Inversion of the center-to-limb curve) [from Bastian et al. (1993)]
- External data: Standard atmospheric models (FAL93 A, C, F; Avrett & Loeser 2008) compared with results  
  > "we plotted $T_e(\tau)$ curves computed from standard atmospheric models" (Inversion of the center-to-limb curve) [from Fontenla et al. 1993; Avrett and Loeser (2008)]

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
- masking: pixels too bright (plage) or too dark (sunspot, filament channels) masked for CLV  
  > "after masking out the pixels that were either too bright (plage) or too dark (sunspot and filament channels)" (Results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Procedure for solar observations with ALMA  
  > "The procedure for solar observations with ALMA is described in White et al. (2017)." (Observations) [from White et al. (2017)]

### Not stated but needed to reproduce (our reading)

- Calibration and image reconstruction details of the Science Verification full-disk images (CASA version, procedure)
- Absolute flux scale/uncertainty
- Pixel size and how limb irregularities and the ellipticity were corrected
- Voigt fit parameters for diffuse-light correction
- Exact mask thresholds
- Details of the Fig 4 CLV binning and elliptical radius fitting
- Handling of 230 vs 239 GHz naming and the extracted Tb at 353 GHz

## Analysis recipe

1. **Select stable full-disk images**: Compared repeated 100 GHz images and dropped the first Dec 16 image, which was 3.3% brighter  
  > "the first image of the same day was 3.3% brighter and we preferred to ignore it in our analysis" (Observations)
   - fitting: _not stated_
   - validation: Total flux RMS of 0.2% across four 100 GHz images  
  > "The total flux of the sun was remarkably stable, with an RMS of 0.2%." (Observations)
2. **Measure center-to-limb Tb curves**: Tb as function of distance from disk center after masking bright and dark features; disk ellipticity taken into account  
  > "we calculated the brightness temperature, $T_b$, as a function of distance from the disk center, $r$" (Results)
   - fitting: _not stated_
   - validation: Compared with high-resolution images near east limb (100 GHz) and south pole (239 GHz); reliable up to r~960''  
  > "we are safe in using measurements up to $r\simeq960$$''$" (Results)
3. **Correct for diffuse light**: Fit Voigt function to CLV derivative near limb; deconvolve with Voigt, reconvolve with Gaussian core  
  > "we deconvolved with the Voigt function and reconvolved with the Gaussian core" (Results)
   - fitting: Voigt function fit to derivative of CLV  
  > "this was better fitted with a Voigt function rather than with a Gaussian" (Results)
   - validation: _not stated_
4. **Invert CLV to Te(tau)**: Assumed Te = a1 + a2 ln tau; Tb(mu)=a1+a2(ln mu - gamma); least-squares fit; data reduced to common reference frequency using f^-2 absorption  
  > "The coefficients $a_1$ and $a_2$ can be determined by least square fit of the observations." (Inversion of the center-to-limb curve)
   - parameter: ALMA data used up to theta~70 deg  
  > "we used ALMA measurements up to $\theta\simeq70$$^\circ$" (Inversion of the center-to-limb curve)
   - assumption: LTE thermal free-free and H- absorption proportional to f^-2  
  > "both the free-free and the H$^-$ absorption coefficients are proportional to $f^{-2}$" (Inversion of the center-to-limb curve)
   - fitting: Least squares on logarithmic form; residual RMS ~60 K  
  > "The fit was very good, with an RMS of residuals of $\sim60$ K" (Inversion of the center-to-limb curve)
   - validation: Adding a quadratic term did not change results; power series unstable; compared with Eddington-Barbier and models  
  > "the addition of a quadratic term in ([\[logform\]](#logform)) did not change appreciably either the data fit or the inversion results" (Inversion of the center-to-limb curve)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central Tb at 239 GHz | 6180 | dispersion 100 K | K | 2 | The brightness temperature at the center of the disk is 6180 and 7250 K at 239 and 100 GHz respectively |
| Central Tb at 100 GHz | 7250 | dispersion 170 K | K | 2 | with dispersions of 100 and 170 K |
| Solar radius at 239 GHz (1 AU) | 961.1 | 2.5 | arcsec | 2 | $961.1\pm2.5$$''$ and $964.1\pm4.5$$''$ at 239 and 100 GHz |
| Solar radius at 100 GHz (1 AU) | 964.1 | 4.5 | arcsec | 2 | $961.1\pm2.5$$''$ and $964.1\pm4.5$$''$ at 239 and 100 GHz |
| 239/100 GHz intensity ratio mean | 0.87 | dispersion 0.01 | dimensionless | 2 | The average value of the ratio is 0.87, with a dispersion of 0.01. |
| Global inversion slope a2 | -608 | not stated | K | 4 | The global inversion gave a slope of $a_2=-608$ K. |
| Slopes per band (100, 239, 343 GHz) | -608, -519, -818 | not stated | K | 4 | with slopes of $-608$, $-519$ and $-818$ K at 100, 239 and 343 GHz respectively |
| Tb beyond the limb at r=1200'' | 100 (239 GHz), 93 (100 GHz) | not stated | K | 2 | it has a value of 100 K at 239 and 93 K at 100 GHz |

## Qualitative findings

- ALMA images closely resemble AIA 1600 Å images; plage stands out in the 239/100 GHz ratio while faculae and filament lanes do not  
  > "The ALMA images are very similar to AIA images at 1600 Å." (abstract)

## Claim tuples

- H: Does the electron temperature vary with optical depth consistent with chromospheric models? | E: Inverted CLV curves at 100 and 239 GHz plus Bastian 353 GHz with a logarithmic Te(tau) | R: Linear in ln tau for 0.34<tau100<12, slope -608 K; ~5% below FAL93 model C | F: Te is consistent with the average quiet-Sun model C and not with the cell-interior models | **supported**
- H: Is limb brightening present at mm wavelengths? | E: CLV curves from full-disk images | R: Slow but statistically significant increase toward the limb | F: Slight limb brightening at both frequencies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: A parametric logarithmic form is more stable than direct numerical inversion  
  > "which is a more stable procedure than a direct numerical inversion" (Inversion of the center-to-limb curve)
- Alternative: Power series expansion of Te(tau) needed at least six terms and gave oscillatory, unphysical inversions  
  > "it gave an oscillatory (hence unphysical) inversion result" (Inversion of the center-to-limb curve)
- How they decided it was enough: _not stated_
- Limitation (authors): 100 GHz results 30-55'' from the limb may be affected by the 60'' beam  
  > "which may have been affected by the 60$''$ antenna beam" (Summary and conclusions)
- Caveat (inferred, ours): Beam size at 100 GHz may be underestimated, as the authors suspect
- Caveat (inferred, ours): Diffuse light correction is ad hoc
- Caveat (inferred, ours): Only one epoch of data, no uncertainty on a2

## Reproducibility

- Data public (paper): Released as ALMA Science Verification data  
  > "released as ALMA Science Verification data in early 2017" (Observations)
- Products in archive: _not stated_
- Missing: Processing of full-disk images
- Missing: Voigt fit parameters
- Missing: Mask thresholds
- Missing: Bastian 353 GHz data values
- Data volume (inferred): A few GB or less (full-disk maps)
- Score (inferred): 3/5, Public SV data and clear inversion formulae, but processing, masking and correction parameters are not specified.
- Rediscovery candidate: no, Recipe lacks key parameters for imaging and the diffuse light correction.

## Links

- Method: White et al. (2017) (Procedure for solar observations with ALMA)
- Related: ALMA Science Verification solar commissioning data

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 30,
  "rate": 0.462
 },
 "evidence_ok": true
}
```
