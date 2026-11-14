# A search for millimeter emission from the coldest and closest brown dwarf with ALMA

`2020A&A...642A..96P` | Astronomy and Astrophysics 2020 | first author: Petry, Dirk | arXiv: 2009.05414 | DOI: 10.1051/0004-6361/202038587

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, exoplanets
- Question: Does the coldest known brown dwarf W0855 emit steady or pulsed millimeter radio emission at ~93 GHz, and what does this imply for radio astrometry and its magnetic field?  
  > "Our goal is to determine the millimeter radio properties of W0855 with deep observations around 93 GHz (3.2 mm) in order to investigate whether radio astrometry of this object is feasible" (abstract)
- Target **W0855**: coordinates 08:55:05.639915, -07:14:36.19233 (J2000) at start of first execution  
  > "$\alpha$=08:55:05.639915, $\delta$=$-$07:14:36.19233 (J2000) at the beginning of the first block execution" (2.1 Band 3 observations in December 2019); "located at only $\approx$2.2 pc form the Sun" (abstract); z/distance ≈2.2 pc  
  > "$\alpha$=08:55:05.639915, $\delta$=$-$07:14:36.19233 (J2000) at the beginning of the first block execution" (2.1 Band 3 observations in December 2019); "located at only $\approx$2.2 pc form the Sun" (abstract); distance from _not stated_
- Target **3C 209**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00202.S
- bands: Band 3 (~93 GHz, 3.2 mm)  
  > "at 93 GHz (Band 3)" (Introduction)
- frequencies and spectral setup: TDM, four spectral windows of 128 channels of 15.625 MHz; 85.1382-100.8618 GHz  
  > "four spectral windows of 128 channels of 15.625 MHz width each." (2.1 Band 3 observations in December 2019)
- continuum bandwidth: 7 GHz effective (first and last 8 channels per window discarded)  
  > "leaving a total effective bandwidth of 7 GHz in the range from 85.1382 GHz to 100.8618 GHz." (2.1 Band 3 observations in December 2019)
- arrays: 44 ALMA 12 m antennas  
  > "with 44 of the ALMA 12 m antennas" (2.1 Band 3 observations in December 2019)
- configurations: nominally C43-2  
  > "The configuration was nominally C43-2." (2.1 Band 3 observations in December 2019)
- baselines: 15 m to 313 m  
  > "The longest baseline was 313 m, and the shortest baseline was 15 m long." (2.1 Band 3 observations in December 2019)
- angular resolution: 3.081"x2.559" synthesised beam  
  > "The synthesised beam of the observation was measured to be 3.081$\ensuremath{''}$$\times$2.559$\ensuremath{''}$." (2.2 Data analysis)
- max recoverable scale: _not stated_
- sensitivity: 7.3 uJy/beam steady; 88 uJy per 30 s  
  > "noise RMS of 7.3 $\mu$Jy/beam for steady emission and of 88 $\mu$Jy for 30 s pulses" (abstract)
- time on source: 94 min (two 47 min execution blocks)  
  > "Two ALMA execution blocks with 47 min on-source time each were carried out, yielding a total on-source time of 94 min." (2.1 Band 3 observations in December 2019)
- observing dates: 2019-12-24, 5:01-7:15 UT  
  > "The observations were carried out between 2019-12-24, 5:01:06 UT and 2019-12-24, 7:15:23 UT" (2.1 Band 3 observations in December 2019)
- pi or archival as stated: _not stated_
- External data: VLA 4-8 GHz upper limit on W0855 steady flux of 7.2 uJy, plotted for comparison  
  > "reported for W0855 a VLA 4-8 GHz upper limit on the steady flux of 7.2 $\mu$Jy" (Introduction) [from (cite: 2019MNRAS.487.1994K)]
- External data: TVLM 513 detection at 56±12 uJy with ALMA, used for flux scaling  
  > "has been detected with ALMA at the 56$\pm$12 $\mu$Jy level by (cite: 2015ApJ...815...64W)" (Introduction) [from (cite: 2015ApJ...815...64W)]
- External data: Proper motion of W0855 used for phase centre  
  > "taking the proper motion as measured by (cite: 2016AJ....152...78L) into account" (2.1 Band 3 observations in December 2019) [from (cite: 2016AJ....152...78L)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline (standard QA)  
  > "using the calibration pipeline 42866 (cite: almapipe) based on the CASA data analysis package version 5.6.1-8" (2.2 Data analysis)
- casa version: CASA 5.6.1-8  
  > "CASA data analysis package version 5.6.1-8" (2.2 Data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: QSO J0725-0054 (also bandpass)  
  > "As bandpass and flux calibrator served QSO J0725-0054, as phase calibrator QSO J0847-0703." (2.1 Band 3 observations in December 2019)
- flux scale uncertainty: better than 10% in Band 3  
  > "The typical systematic uncertainty on the standard ALMA flux calibration is better than 10% in Band 3" (2.1 Band 3 observations in December 2019)
- self calibration: _not stated_

### Imaging

- task: CASA tclean, mfs mode  
  > "imaged with the tclean task of the same CASA package in mfs mode" (2.2 Data analysis)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "a pixel size of 0.4$\ensuremath{''}$ and natural weighting" (2.2 Data analysis)
- uv taper: _not stated_
- cell size: 0.4 arcsec  
  > "a pixel size of 0.4$\ensuremath{''}$ and natural weighting" (2.2 Data analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: W0855 field mosaicked with 3C 209 check-source field to deconvolve sidelobes  
  > "re-imaged the target by combining the check-source field containing 3C 209 with the target field as a mosaic" (2.2 Data analysis)
- smoothing: _not stated_
- final beam: 3.081"x2.559"  
  > "3.081$\ensuremath{''}$$\times$2.559$\ensuremath{''}$" (2.2 Data analysis)
- final rms: 7.3 uJy (11.8 uJy before mosaic)  
  > "reduced the noise RMS in the region around the nominal position of W0855 to 7.3 $\mu$Jy" (2.2 Data analysis)

### Inherited from earlier work

- 3-sigma upper limit prescription (3 x noise RMS)  
  > "we follow the prescription of (cite: 2019MNRAS.487.1994K) (who simply multiplied the measured noise RMS by a factor 3)" (2.3 Derivation of an upper limit on the steady flux) [from (cite: 2019MNRAS.487.1994K)]
- 30 s bin size from minimum pulse structure duration in TVLM 513  
  > "Based on the minimum duration of the pulse structures seen in TVLM 513 (cite: 2007ApJ...663L..25H), we divided our dataset into 30 s time bins" (2.4 Search for pulsed emission) [from (cite: 2007ApJ...663L..25H)]

### Not stated but needed to reproduce (our reading)

- Masking/clean threshold and iteration count for tclean
- Mosaic details (phase centres, weighting of the 3C 209 field, gridder)
- Method for measuring flux in the beam-shaped region of the 30 s images
- Whether 3C 209 was imaged with same deconvolver (hogbom assumed not stated)
- Image size
- Pipeline flagging beyond standard

## Analysis recipe

1. **Image W0855 field alone**: tclean mfs, natural weighting, single field  
  > "only the W0855 data were imaged as a single field with a pixel size of 0.4$\ensuremath{''}$ and natural weighting" (2.2 Data analysis)
   - software: CASA tclean
   - parameter: pixel 0.4"; RMS 11.8 uJy vs expected 8 uJy  
  > "noise RMS in the central region of the image of 11.8 $\mu$Jy, significantly worse than the expected 8 $\mu$Jy" (2.2 Data analysis)
   - fitting: _not stated_
   - validation: compared to expected sensitivity  
  > "significantly worse than the expected 8 $\mu$Jy" (2.2 Data analysis)
2. **Remove 3C 209 sidelobes via mosaic**: Re-image combining 3C 209 field and target field as mosaic  
  > "This permitted us to remove the sidelobes of 3C 209 in the deconvolution" (2.2 Data analysis)
   - software: CASA tclean
   - fitting: _not stated_
   - validation: noise reduced to 7.3 uJy  
  > "reduced the noise RMS in the region around the nominal position of W0855 to 7.3 $\mu$Jy" (2.2 Data analysis)
3. **Steady-emission upper limit**: 3 x noise RMS  
  > "With our noise RMS of 7.3 $\mu$Jy from above, we obtain an upper limit of 21.9 $\mu$Jy." (2.3 Derivation of an upper limit on the steady flux)
   - fitting: _not stated_
   - validation: _not stated_
4. **Search for pulsed emission**: 188 images of 30 s bins; flux measured in a beam-shaped region at W0855 position; light curve; Gaussian distribution check  
  > "Measuring the flux in a beam-shaped region around the W0855 position in each of the 188 images, we derived a light curve" (2.4 Search for pulsed emission)
   - software: CASA
   - parameter: 30 s bins  
  > "we divided our dataset into 30 s time bins for which we obtained individual images" (2.4 Search for pulsed emission)
   - fitting: Gaussian consistency of flux distribution  
  > "The distribution of the 30 s fluxes is consistent with a Gaussian with zero average and RMS 82 $\mu$Jy" (2.4 Search for pulsed emission)
   - validation: RMS 82 uJy consistent with image noise 88 uJy  
  > "which in turn is consistent with the noise RMS of 88 $\mu$Jy that we measured on average in the individual 30 s images" (2.4 Search for pulsed emission)

## Software

- **CASA** 5.6.1-8: calibration pipeline and tclean imaging  
  > "The calibrated data were then imaged with the tclean task of the same CASA package in mfs mode" (2.2 Data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Noise RMS, steady (mosaic image) | 7.3 | not stated | uJy/beam | 2 | reduced the noise RMS in the region around the nominal position of W0855 to 7.3 $\mu$Jy |
| 3-sigma upper limit on steady flux | 21.9 | not stated | uJy | 3 | we obtain an upper limit of 21.9 $\mu$Jy |
| 3-sigma upper limit on pulsed flux (30 s) | 264 | not stated | uJy | 4 | can be placed at 264 $\mu$Jy |
| 30 s image noise RMS | 88 | not stated | uJy | 4 | noise RMS of 88 $\mu$Jy that we measured on average in the individual 30 s images |

## Qualitative findings

- No steady or pulsed emission from W0855 detected; the object is neither radio-loud nor magnetospherically particularly active.  
  > "confirm that the object is neither radio-loud nor magnetospherically particularly active." (abstract)

## Claim tuples

- H: W0855 emits steady or pulsed mm radio emission like TVLM 513 | E: 94 min ALMA Band 3 imaging and 30 s light curve | R: No detection; 3-sigma limits 21.9 uJy steady, 264 uJy pulsed | F: W0855 not radio-loud or magnetospherically active at the observed time | **supported**
- H: Radio astrometry of W0855 is feasible | E: Compare limits to expected fluxes | R: Limits well below ~1 mJy scaling estimates | F: W0855 is not a prime candidate for radio study | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Mosaic with 3C 209 to remove sidelobes and improve sensitivity  
  > "We suspected that the loss in sensitivity was due to the sidelobes of the relatively bright nearby object 3C 209" (2.2 Data analysis)
- Alternative: More conservative upper-limit method (Masci) not used, to compare with Kao et al.  
  > "because we wish to plot our result together with theirs; see (cite: masciul) for an alternative, more conservative method" (2.3 Derivation of an upper limit on the steady flux)
- How they decided it was enough: _not stated_
- Limitation (authors): Limits are less constraining than the 4-8 GHz limits given the expected spectral index; only a single few-hour epoch.  
  > "they are less constraining because the power-law spectrum measured in similar objects such as TVLM 513" (Summary and conclusions)
- Caveat (inferred, ours): Single epoch of 94 min; variability on longer timescales untested
- Caveat (inferred, ours): Upper limits via simple 3x RMS
- Caveat (inferred, ours): Pulsed limit applies only to Stokes I; no Stokes V analysis

## Reproducibility

- Data public (paper): Project code given in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00202.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters and mosaic settings
- Missing: Flux-measurement procedure in 30 s images
- Data volume (inferred): ~10-30 GB for two TDM execution blocks
- Score (inferred): 4/5, Simple dataset and workflow with key numbers stated; some imaging parameters missing.
- Rediscovery candidate: yes, Single project, standard pipeline, numeric noise and upper limits to reproduce.

## Links

- Method: (cite: 2019MNRAS.487.1994K) (Upper-limit prescription)
- Companion: (cite: 2015ApJ...815...64W) (ALMA mm detection of TVLM 513 used as comparison)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 69,
  "stated": 44,
  "rate": 0.638
 },
 "evidence_ok": true
}
```
