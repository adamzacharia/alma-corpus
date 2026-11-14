# The First Millimeter Detection of a Non-Accreting Ultracool Dwarf

`2015ApJ...815...64W` | The Astrophysical Journal 2015 | first author: Williams, P. K. G. | arXiv: 1511.05559 | DOI: 10.1088/0004-637X/815/1/64

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics
- Question: Is the ultracool dwarf TVLM 513-46546 detectable at millimeter wavelengths with ALMA, and what emission mechanism and spectrum does this imply?  
  > "We argue that the emission is due to the synchrotron process, excluding thermal, free-free, and electron cyclotron maser emission as possible sources." (abstract)
- Target **TVLM 513-46546**: coordinates RA = 15:01:08.1463, Dec. = +22:50:01.224 (expected at time of ALMA observation)  
  > "the expected position of at the time of the ALMA observations was RA = 15:01:08.1463, Dec. = $+22$:50:01.224, with an approximate uncertainty of 1 mas." (3.1 ALMA); "precise trigonometric parallax implying a distance of $10.762 \pm 0.027$ pc (cite: fbr13)" (2 The ultracool dwarf TVLM 513-46546); z/distance 10.762 +/- 0.027 pc  
  > "the expected position of at the time of the ALMA observations was RA = 15:01:08.1463, Dec. = $+22$:50:01.224, with an approximate uncertainty of 1 mas." (3.1 ALMA); "precise trigonometric parallax implying a distance of $10.762 \pm 0.027$ pc (cite: fbr13)" (2 The ultracool dwarf TVLM 513-46546); distance from VLBI trigonometric parallax (Forbrich, Berger & Reid 2013)  
  > "the expected position of at the time of the ALMA observations was RA = 15:01:08.1463, Dec. = $+22$:50:01.224, with an approximate uncertainty of 1 mas." (3.1 ALMA); "precise trigonometric parallax implying a distance of $10.762 \pm 0.027$ pc (cite: fbr13)" (2 The ultracool dwarf TVLM 513-46546)

## Data provenance

- ALMA projects: 2013.1.00293.S
- bands: Band 3 (~95 GHz)  
  > "using the “band 3” receivers" (3.1 ALMA)
- frequencies and spectral setup: Two sidebands centered at 91.46 GHz (LSB) and 103.49 GHz (USB), 4 GHz each  
  > "two sidebands centered on 91.46 GHz (lower sideband, LSB) and 103.49 GHz (upper sideband, USB), each having a total bandwidth of 4 GHz" (3.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: image rms 9 uJy (full band)  
  > "higher than the image rms (9 ) because it includes covariances with the source positions" (3.1 ALMA)
- time on source: 2.15 hr on source, just under 4 hr total  
  > "The observations lasted just under 4 hours, with the total on-source integration time being 2.15 hr." (3.1 ALMA)
- observing dates: UT 2015 Apr 03  
  > "was observed with ALMA on UT date 2015 Apr 03" (3.1 ALMA)
- pi or archival as stated: Proposal 2013.1.00293.S, PI Casewell  
  > "proposal 2013.1.00293.S, PI: Casewell" (3.1 ALMA)
- Other facility **VLA**: Unpublished archival 2010 data at 1.57, 6.10, 19.75 GHz (TRSR0033, PI Hallinan)  
  > "project ID TRSR0033, PI: Hallinan" (3.2 Archival VLA Data)
- Other facility **Liverpool Telescope**: i' band optical monitoring on 2015 Aug 5 to time optical maximum  
  > "We used the Sloan Digital Sky Survey (SDSS) $i'$ filter with exposure times of 60 seconds." (3.3 Liverpool Telescope)
- External data: Astrometric parameters (parallax/distance, proper motion) used for expected position  
  > "Using the astrometric parameters reported by (cite: fbr13)" (3.1 ALMA) [from (cite: fbr13)]
- External data: Combined radio/optical ephemeris predicting optical maximum BMJD 57150.028 and rotation period  
  > "The combined radio/optical ephemeris described in that work predicts an optical maximum at $\text{BMJD} = 57150.028$" (3.3 Liverpool Telescope) [from (cite: wr14)]
- External data: Published cm-band flux densities used in the broadband spectrum  
  > "fit to our ALMA data and the measurements of (cite: ohbr06)" (4.2 The Broadband Radio Spectrum) [from (cite: ohbr06)]

## Processing

### Calibration

- pipeline or manual: ALMA data reduced by EARC staff; calibrated visibilities provided  
  > "Calibrated visibilities and a preliminary image were provided to us by the European ALMA Regional Centre (EARC) after reduction by their staff." (3.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Examined, no lingering problems found; re-imaged  
  > "We examined the data and identified no lingering problems." (3.1 ALMA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: Somewhat larger field of view than EARC analysis  
  > "using a somewhat larger field of view than the EARC analysis" (3.1 ALMA)
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

- Light curve extraction technique from visibilities  
  > "using the technique described in (cite: wbz13)" (3.1 ALMA) [from (cite: wbz13)]
- VLA flux density scale (preliminary 2010 version)  
  > "set the flux density scale using the preliminary, 2010 version of the scale defined by (cite: pb13)" (3.2 Archival VLA Data) [from (cite: pb13)]
- Gyrosynchrotron model equations  
  > "a standard gyrosynchrotron model based on the equations of (cite: d85)" (4.2 The Broadband Radio Spectrum) [from (cite: d85)]

### Not stated but needed to reproduce (our reading)

- CASA version and ALMA calibration details performed by EARC
- Weighting/robust, cell size, image size, deconvolution settings
- ALMA flux calibrator and flux-scale uncertainty
- Details of the source-model fit (task, model)
- Details of flare likelihood-ratio and Bayes factor simulations (priors, flare shape)
- Gyrosynchrotron model parameters beyond B and delta (density, size, angle)
- Details of the spectral index confidence calculation

## Analysis recipe

1. **Image ALMA data and measure source flux**: Re-imaged calibrated visibilities; fitted a source model to the image  
  > "Fitting a source model to the image, we measure a flux density of $56 \pm 12$" (3.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Position consistent with expected proper-motion position at 0.2 sigma  
  > "The positions are consistent to 0.2$\sigma$" (3.1 ALMA)
2. **Measure ALMA spectral index from sidebands**: Imaged LSB and USB separately and derived spectral index  
  > "We imaged the two ALMA sidebands separately to assess the spectral index of at millimeter wavelengths." (3.1 ALMA)
   - assumption: Thermal emission defined as alpha >= 1.5  
  > "thermal emission, defined here as $\alpha \ge 1.5$ (cite: aw05)" (3.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract and test ALMA light curve for variability**: Visibility-based light curves with other source subtracted; likelihood ratio test of constant vs exponentially fading flare, plus Bayes factor  
  > "A simple likelihood ratio test comparing a constant model and one with an exponentially fading flare yields an empirical $p$-value" (4.3 Phased Millimeter and Optical Variability?)
   - parameter: 2 s raw cadence, 102 s bins  
  > "The resulting raw light curves have a sampling cadence of 2 s." (3.1 ALMA)
   - fitting: _not stated_
   - validation: Empirical p-value from simulated realizations of constant model  
  > "in about 7% of simulated realizations of the constant model" (4.3 Phased Millimeter and Optical Variability?)
4. **Calibrate and measure archival VLA fluxes**: CASA calibration, aoflagger RFI flagging, point-source fits to images in three bands  
  > "From fitting a point-source model to images generated from data in the three bands, we obtain the flux densities" (3.2 Archival VLA Data)
   - software: CASA, aoflagger
   - fitting: _not stated_
   - validation: L band consistent with prior observations  
  > "The flux density measurement in L band is marginal but consistent with prior observations" (3.2 Archival VLA Data)
5. **Time optical maximum from LT photometry**: Aperture photometry with comparison stars; sinusoid fit with period fixed to literature  
  > "by fitting a sinusoid to the data, constraining the period to match the value determined by (cite: wr14)" (3.3 Liverpool Telescope)
   - parameter: Apertures 1.6 times seeing; two brightest of four comparison stars used  
  > "apertures whose sizes were scaled to 1.6 times the measured seeing in each image" (3.3 Liverpool Telescope)
   - fitting: Sinusoid fit, period fixed  
  > "by fitting a sinusoid to the data, constraining the period to match the value determined by (cite: wr14)" (Liverpool Telescope)
   - validation: _not stated_
6. **Assess emission mechanism and broadband spectrum**: Rule out thermal, free-free (X-ray based estimate) and ECMI (cyclotron frequency field requirement); compare gyrosynchrotron model with data  
  > "Here we fixed $B = 100$ G and the electron energy spectral index $\delta = 2$" (4.2 The Broadband Radio Spectrum)
   - parameter: B = 100 G, delta = 2  
  > "Here we fixed $B = 100$ G and the electron energy spectral index $\delta = 2$" (4.2 The Broadband Radio Spectrum)
   - assumption: Free-free scaling S = 1e6 Jy * f_X for active low-mass stars  
  > "Assuming parameters appropriate for active low-mass stars, they find that $S_{\nu,\text{ff}} = (10^6\text{ Jy}) f_X$" (4.1 Emission Mechanism)
   - fitting: _not stated_
   - validation: Authors caution non-contemporaneous data not for quantitative analysis  
  > "We emphasize that these examples connect observations made years apart and so should not be used for quantitative analysis." (4.2 The Broadband Radio Spectrum)

## Software

- **CASA** : VLA calibration and imaging  
  > "We calibrated the data using standard procedures in the CASA software system" (3.2 Archival VLA Data)
- **aoflagger** : Automatic RFI flagging of VLA data  
  > "We used the aoflagger tool to automatically flag radio-frequency interference" (3.2 Archival VLA Data)
- **Astropy** : Python analysis package acknowledged  
  > "Astropy, a community-developed core Python package for astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 95 GHz flux density (full band) | 56 | 12 | uJy | 1 | we measure a flux density of $56 \pm 12$ |
| Detection significance | 6.2 | not stated | sigma | 1 | a source that is 6.2$\sigma$ above the background noise |
| LSB flux density (91.46 GHz) | 66 | 8 | uJy | 2 | the flux density of the source is $66 \pm 8$ |
| USB flux density (103.49 GHz) | 31 | 18 | uJy | 2 | it is $31\pm18$ |
| ALMA-only spectral index | -5 | 4 | dimensionless | 2 | $\amm \approx -5 \pm 4$ |
| Optical maximum time (LT) | 57150.049 | 0.001 | BMJD | 5 | $\text{BMJD} = 57150.049 \pm 0.001$ |
| VLA 6.10 GHz flux density | 214 | 18 | uJy | 4 | / 6.10      /      / $214$ / $\pm 18$  / 55546.50  / VLA      / |
| Flare likelihood-ratio empirical p-value | about 7% | not stated | percent | 3 | in about 7% of simulated realizations of the constant model |

## Qualitative findings

- Detection is first mm detection of a non-accreting ultracool dwarf; emission attributed to synchrotron; no significant mm variability found.  
  > "makes it the first non-accreting ultracool dwarf to be detected at millimeter wavelengths." (5 Conclusions)

## Claim tuples

- H: Is TVLM 513 detectable at mm wavelengths? | E: ALMA Band 3 imaging | R: 6.2 sigma source, 56 +/- 12 uJy at the expected position | F: First mm detection of a non-accreting ultracool dwarf | **supported**
- H: What is the emission mechanism? | E: Compare spectral index, free-free estimate and required ECMI field | R: Thermal, free-free and ECMI excluded | F: Synchrotron/gyrosynchrotron origin | **supported**
- H: Is mm emission variable and phased with optical maximum? | E: Light curve and likelihood ratio test | R: p-value ~7%; constant model not rejected | F: Hint of phased flare, not significant | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal, free-free and ECMI origins rejected; UKR-like spectrum excluded by ALMA data  
  > "Although the preexisting data could have been consistent with such a spectral shape, the ALMA data exclude it." (4.2 The Broadband Radio Spectrum)
- How they decided it was enough: _not stated_
- Limitation (authors): Radio data are non-contemporaneous and the source is variable, so broadband spectrum inferences are uncertain  
  > "confident inferences based on the broadband radio spectrum of are precluded because the ALMA observations were not obtained contemporaneously" (5 Conclusions)
- Caveat (inferred, ours): Detection is only ~6 sigma and USB is 2.6 sigma, so spectral index is weakly constrained
- Caveat (inferred, ours): Gyrosynchrotron model has fixed B and delta, not fitted
- Caveat (inferred, ours): Flare significance rests on simulations with unspecified details

## Reproducibility

- Data public (paper): ALMA and VLA data are archival  
  > "We also analyzed unpublished archival observations of performed with the Karl G. Jansky Very Large Array (VLA)." (3.2 Archival VLA Data)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Flare test and simulation details
- Missing: Gyrosynchrotron model parameters
- Data volume (inferred): ~10-50 GB (one ALMA Band 3 track plus small VLA dataset)
- Score (inferred): 5/5, Public data and simple measurements, but imaging, fitting and flare-test settings are unspecified.
- Rediscovery candidate: yes, Public data, a single point-source flux measurement with numeric results; recipe is simple though some settings are missing.

## Links

- Method: (cite: wbz13) (Visibility-based light curve extraction)
- Method: (cite: pb13) (VLA flux density scale)
- Companion: (cite: wr14) (Radio/optical ephemeris and rotation period)
- Companion: (cite: ohbr06) (Prior multi-frequency radio spectrum)
- Related: VLA TRSR0033

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
