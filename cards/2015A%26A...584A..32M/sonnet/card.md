# (Sub)millimetre interferometric imaging of a sample of COSMOS/AzTEC submillimetre galaxies. II. The spatial extent of the radio-emitting regions

`2015A&A...584A..32M` | Astronomy and Astrophysics 2015 | first author: Miettinen, O. | arXiv: 1509.07147 | DOI: 10.1051/0004-6361/201526589

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Are the radio-emitting sizes of COSMOS/AzTEC SMGs at 3 GHz comparable to their FIR sizes, and does cosmic-ray diffusion explain larger radio sizes?  
  > "To test this further here we present a study of radio sizes of SMGs from a well selected sample of SMGs in the Cosmic Evolution Survey (COSMOS; (cite: scoville2007)) deep field" (1 Introduction)
- Target **COSMOS/AzTEC SMGs AzTEC1-30 (39 components)**: coordinates listed in Table 1 (SMA/PdBI peak positions)  
  > "Our sample of 39 SMGs is listed in Table [1](#table:sample)." (2.1 Source sample); z/distance z=0.834-5.298 (spec, photo-z, radio/submm)  
  > "Our sample of 39 SMGs is listed in Table [1](#table:sample)." (2.1 Source sample); distance from literature (Miettinen et al. 2015 and references therein)  
  > "Our sample of 39 SMGs is listed in Table [1](#table:sample)." (2.1 Source sample)

## Data provenance

- ALMA projects: 2012.1.00978.S, 2013.1.00118.S
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
- Other facility **VLA-COSMOS 3 GHz Large Project**: 3 GHz continuum mosaic, 0.75'' beam, ~2.3 uJy/beam rms  
  > "The final $1\sigma$ root mean square (rms) noise level in our maps is typically about 2.3 $\mu$Jy beam$^{-1}$." (2.2 VLA 3 GHz radio continuum data)
- Other facility **SMA / PdBI / JCMT AzTEC**: sample selection and (sub)mm positions  
  > "The coordinates given in the table correspond to the (sub)mm peak positions determined in the aforementioned SMA and PdBI studies." (2.1 Source sample)
- External data: 1.4 GHz flux densities from COSMOS VLA Deep Catalogue  
  > "The 1.4 GHz flux densities were taken from the COSMOS VLA Deep Catalogue ((cite: schinnerer2010))" (4.2) [from (cite: schinnerer2010)]
- External data: Redshifts and (sub)mm positions  
  > "We refer to Miettinen et al. (2015 and references therein) for further details and discussion on the redshifts of our SMGs." (2.1 Source sample) [from (cite: miettinen2015)]

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
- weighting robust: robust = 0.5  
  > "Briggs or robust weighting was applied to the calibrated visibilities with a robust value of 0.5." (2.2)
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
- final beam: 0.75'' circular  
  > "The final mosaic was restored with a circular synthesised beam size (FWHM) of $\theta_{\rm maj}=\theta_{\rm min}=0.75\ensuremath{''}$" (2.2)
- final rms: _not stated_

### Inherited from earlier work

- VLA 3 GHz observations, reduction and imaging  
  > "Details of the observations, data reduction, and imaging can be found in Novak et al. (2015), Smolčić et al. (2015a), and V. Smolčić et al. (in prep.)." (2.2) [from Novak et al. (2015), Smolčić et al. (2015a)]

### Not stated but needed to reproduce (our reading)

- The ALMA data are only mentioned; no processing given (Miettinen et al. in prep.)
- VLA 3 GHz mosaic not public at time of paper

## Analysis recipe

1. **Measure deconvolved radio sizes**: 2D elliptical Gaussian fits in image plane with JMFIT  
  > "Two-dimensional elliptical Gaussian fits to the image plane data were made using the AIPS task `JMFIT`." (4.1)
   - software: AIPS
   - parameter: fit restricted to pixels >=2.5 sigma; resolved if FWHM > half beam  
  > "the fit was restricted to the pixel values of $\geq2.5\sigma$." (4.1)
   - fitting: _not stated_
   - validation: Simulated Gaussian sources injected into source-free map, recovered with JMFIT  
  > "we simulated SMGs with an assigned size and varying S/N ratio, and fit them in the same manner as the real sources." (4.1)
2. **Size statistics with censored data**: Kaplan-Meier / MLE survival analysis  
  > "we used the Kaplan-Meier (K-M) method to construct a model of the input data" (4.1)
   - software: NADA for R
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectral index and brightness temperature**: alpha between 1.4 and 3 GHz; Rayleigh-Jeans T_B  
  > "The 3 GHz Rayleigh-Jeans brightness temperature was calculated as $T_{\rm B}=c^2S_{\nu}/(2k_{\rm B}\nu^2 \Omega)$" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Cosmic-ray electron cooling and escape length**: Analytic cooling times from Murphy (2009)  
  > "we calculate the corresponding cooling times using the formulas from Murphy (2009; Sect. 2 therein)" (Appendix E)
   - assumption: B~100 uG; L_IR 1e12-1e13 Lsun; n_H=1e2-1e3 cm^-3  
  > "Assuming a typical average density range of $n_{\rm H}=10^2-10^3$ cm$^{-3}$" (Appendix E)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** : JMFIT size fitting  
  > "We used AIPS package to determine the deconvolved sizes of our 3 GHz sources." (4.1)
- **CASA** 4.3.1: simulating mock sources  
  > "we simulated sources using the `CASA` (release 4.3.1) Toolkit." (Appendix D)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 GHz detection fraction | 18/39 (~46%) | ±11% | dimensionless | 1 | i.e. 18/39 or $\sim46\%$ (with a Poisson error on counting statistics of $\pm11\%$) of our sources are 3 GHz-emitting SMGs. |
| Median deconvolved major axis FWHM | 0.54 | 0.11 | arcsec | 2 | Median $\theta_{\rm maj}$ / $0.54\ensuremath{''}\pm0.11\ensuremath{''}$ ($4.2\pm0.9$ kpc) |
| Median linear major axis | 4.2 | 0.9 | kpc | 2 | Median $\theta_{\rm maj}$ / $0.54\ensuremath{''}\pm0.11\ensuremath{''}$ ($4.2\pm0.9$ kpc) |
| Brightness temperature range | 1.4 to 75.9 K | ±0.7 to ±16.6 | K | 3 | The low values of $T_{\rm B}$, ranging from $1.4\pm0.7$ K to $75.9\pm16.6$ K |
| CR electron cooling time | 1.7e4 - 1.9e5 | not stated | yr | 4 | The individual timescales calculated above yield $\tau_{\rm cool}\sim  1.7\times10^4- 1.9\times10^5$ yr. |
| CR electron escape length | 22-135 | not stated | pc | 4 | the electrons can travel only $l_{\rm esc}\sim  22-135$ pc. |

## Qualitative findings

- No correlation of radio size with radio/submm flux or redshift; radio sizes comparable to CO and 1.4 GHz sizes but larger than FIR sizes  
  > "We found no obvious correlations between the FWHM radio-size and radio or submm flux density or redshift" (Summary and conclusions)

## Claim tuples

- H: Radio emission is powered by star formation, not AGN | E: Brightness temperature from 3 GHz sizes and fluxes | R: T_B 1.4-75.9 K | F: consistent with star formation | **supported**
- H: Cosmic-ray diffusion explains larger radio than FIR sizes | E: Cooling time and escape length estimate | R: escape length 22-135 pc | F: CR diffusion seems unlikely | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cosmic-ray diffusion (Simpson et al. 2015a) rejected in favour of merger-induced extended synchrotron emission or two-component ISM  
  > "Hence, the CR diffusion scenario proposed by Simpson et al. (2015a) seems unlikely" (6.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Comparisons of CO and radio sizes use different samples; subject to selection effects  
  > "these comparisons between CO and radio median sizes are, unfortunately, based on measurements obtained from different samples" (6.2)
- Caveat (inferred, ours): ALMA data barely used and not processed here
- Caveat (inferred, ours): Sizes compared across different samples and wavelengths
- Caveat (inferred, ours): Many upper limits

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: VLA-COSMOS 3 GHz mosaic details (in prep.)
- Missing: ALMA size measurements only in prep.
- Data volume (inferred): not applicable for ALMA; VLA mosaic is large (192 pointings)
- Score (inferred): 2/5, Main results rely on a VLA mosaic not described fully; ALMA minor.
- Rediscovery candidate: no, Main data are the VLA 3 GHz mosaic, not ALMA, and not public at the time.

## Links

- Method: Novak et al. (2015) (VLA 3 GHz observations/imaging)
- Companion: Miettinen et al. 2015 (cite: miettinen2015) (Paper I; PdBI 1.3 mm imaging of the sample)
- Related: VLA-COSMOS 3 GHz Large Project
- Related: COSMOS

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 23,
  "rate": 0.343
 },
 "evidence_ok": true
}
```
