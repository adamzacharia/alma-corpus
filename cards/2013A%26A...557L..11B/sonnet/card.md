# ALMA observations of the Red Rectangle, a preliminary analysis

`2013A&A...557L..11B` | Astronomy and Astrophysics 2013 | first author: Bujarrabal, V. | arXiv: 1307.5959 | DOI: 10.1051/0004-6361/201322232

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Do the Red Rectangle's rotating equatorial disk and axial outflow coexist, and what are the structure, dynamics and physical conditions of the outflow?  
  > "We aim to study equatorial disks in rotation and axial outflows in post-AGB objects, as to disclose the formation and shaping mechanisms in planetary nebulae." (abstract)
- Target **Red Rectangle**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00223.S
- bands: Band 7 (12CO and 13CO J=3-2) and Band 9 (12CO J=6-5)  
  > "using receiver bands 7, to map the $^{12}$CO and $^{13}$CO $J$=3$-$2 transitions, and 9, to map the CO $J$=6$-$5 transition" (2 Observations)
- frequencies and spectral setup: Band 7: 330.354-330.822, 333.152-333.620, 345.106-345.574, 345.562-346.030 GHz; Band 9: 673.540-674.477, 677.040-677.977, 687.805-688.742, 691.004-691.941 GHz; 0.21 km/s resolution  
  > "In band 9, we observed the intervals 673.540-674.477, 677.040-677.977, 687.805-688.742 and 691.004-691.941 GHz to image the $^{12}$CO $J$=6$-$5 line." (Appendix A); "The backends were set to achieve a spectral resolution of 0.21 km s$^{-1}$." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 21 to 24 antennas, extended up to 380 m  
  > "the array consisted of 21 to 24 antennas distributed in a configuration that extended up to 380 m." (2 Observations)
- baselines: _not stated_
- angular resolution: 0.48x0.44 arcsec (CO 3-2); 0.31x0.25 arcsec (CO 6-5)  
  > "a synthetic beam with a HPBW of 0$''$48$\times$0$''$44" (2 Observations); "with a synthetic beam of 0$''$31$\times$0$''$25" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 5 mJy/beam (CO 3-2 channels, 0.42 km/s), ~30 mJy/beam (CO 6-5); continuum 3 mJy/beam (band 7), 8 mJy/beam (band 9)  
  > "The resulting brightness *rms* is 5 mJy/beam in the CO $J$=3$-$2 channel maps, for a spectral resolution of 0.42 km s$^{-1}$" (2 Observations); "a brightness *rms* of 3 mJy/beam is obtained in band 7 and of 8 mJy/beam in band 9" (2 Observations)
- time on source: 71 min (band 7), 135 min (band 9)  
  > "which allowed accumulating a total of 135 min of correlations on source" (Appendix A)
- observing dates: Band 7: 21-22 Oct 2012; Band 9: 3-4 Nov 2012  
  > "Two observing runs were carried out in band 7 in October 21 and 22, 2012, of 80 and 100 min respectively" (Appendix A)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Line: 12CO J=6-5 (not stated)
- Other facility **HST (WFPC2/f622w)**: Optical image for comparison with CO data  
  > "A WFPC2/f622w optical image was obtained from the HST archive." (Appendix A)
- External data: Disk model parameters adopted from Paper I  
  > "We adopted the same disk model as that deduced in Paper I (where all parameters are discussed in detail)." (3 Results) [from Bujarrabal & Alcolea 2013, Paper I (cite: bujal13)]
- External data: Proper motion of the Red Rectangle from Hipparcos  
  > "$\delta_{\rm
  RA}$=$-$6.46$\pm$2.21 and $\delta_{\rm Dec}$=$-$22.74$\pm$2.03 mas yr$^{-1}$, van Leeuwen 2007" (Appendix A) [from van Leeuwen 2007 (cite: vlee07)]

## Processing

### Calibration

- pipeline or manual: Manual recalibration in CASA improving ALMA staff calibration; per-track calibration  
  > "Also, having identified different RF solutions for the different observed runs, an independent calibration was performed per track." (Appendix A)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (Ceres in one band 9 run); Butler-JPL-Horizons 2010 model  
  > "The flux calibration was based on the Butler-JPL-Horizons 2010 model for solar system bodies." (Appendix A)
- flux scale uncertainty: Intensities possibly overestimated by 10% in band 7 and 5-10% in band 9  
  > "could be slightly overestimated, by 10% in band 7, and by 5-10% in band 9." (Appendix A)
- self calibration: Self-calibration using the continuum emission  
  > "selfcalibration was carried out by using the bright and moderately extended continuum emission of the Red Rectangle." (Appendix A)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust weighting (threshold 1) for band 7; natural for band 9  
  > "The image deconvolution was made by using robust weighting (with a threshold of 1) for band 7 and natural weighting for band 9." (2 Observations)
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
- final rms: 5 mJy/beam (CO 3-2), ~30 mJy/beam (CO 6-5)  
  > "For $^{12}$CO $J$=6$-$5 maps the *rms* is $\sim$ 30 mJy/beam" (2 Observations)

### Inherited from earlier work

- Disk model (and parameters) adopted from Paper I  
  > "We adopted the same disk model as that deduced in Paper I (where all parameters are discussed in detail)." (3 Results) [from Paper I (cite: bujal13)]
- Modeling code similar to earlier code, LTE excitation  
  > "We used a code very similar to that described by Bujarrabal et al. (2005)." (3 Results) [from Bujarrabal et al. (2005) (cite: bujetal05)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Self-calibration solution intervals and number of iterations
- Cell and image size, and clean masks
- Model code and the full parameter values of the outflow
- Source distance and inclination
- Spectral-window to line mapping details

## Analysis recipe

1. **Calibrate and image**: Recalibrate in CASA with per-track calibration, spline bandpass, self-calibration; image in GILDAS  
  > "The bandpass was calibrated by fitting cubic splines." (Appendix A)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Model 12CO J=3-2 maps with disk plus expanding outflow**: LTE model of Paper I disk (density decreased by factor 2) plus a new symmetric expanding component; compare synthetic maps with data  
  > "We only decreased the disk density by factor 2, because the predicted line emission from this component was stronger than observed." (3 Results)
   - parameter: Outflow temperature constant at 200 K  
  > "the temperature of the outflow is assumed to be constant and equal to 200 K." (3 Results)
   - assumption: LTE excitation valid for low-J high-opacity transitions  
  > "the excitation is described by an LTE approximation, which is valid for low-$J$ high-opacity transitions" (3 Results)
   - fitting: Best-fit by comparison of synthetic and observed maps; method not stated  
  > "We have performed a simple model fitting of our $^{12}$CO $J$=3$-$2 maps." (Results, simple modeling of our ALMA maps)
   - validation: Visual comparison of synthetic maps with observations  
  > "As we see, the model prediction is satisfactory." (3 Results)

## Software

- **CASA** : Calibration  
  > "Calibration was made with the CASA software package" (2 Observations)
- **GILDAS** : Imaging and data analysis  
  > "for the imaging and data analysis we used GILDAS" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 continuum flux range | 0.59-0.66 | not stated | Jy | 1 | The integrated continuum flux varies, because of the source spectral index, in the ranges 0.59-0.66 and 3.2-3.6 Jy, respectively for bands 7 and 9. |
| Band 9 continuum flux range | 3.2-3.6 | not stated | Jy | 1 | The integrated continuum flux varies, because of the source spectral index, in the ranges 0.59-0.66 and 3.2-3.6 Jy, respectively for bands 7 and 9. |
| Outflow velocity | ~10 | not stated | km/s | 2 | The velocity of the outflow is moderate, $\sim$ 10 km s$^{-1}$ |
| Outflow density range | 10^3 to 10^5 | not stated | cm^-3 | 2 | with values between 10$^3$ and 10$^5$ cm$^{-3}$ |

## Qualitative findings

- An X-shaped expanding molecular component tracing the optical nebula lobes is mapped for the first time, alongside the rotating disk.  
  > "an X-shaped structure delineating the lobes of the optical nebula (mostly its inner part) are mapped in molecular emission for the first time." (3 Results)

## Claim tuples

- H: Do a rotating disk and an outflow coexist in the Red Rectangle? | E: ALMA CO 3-2 and 6-5 mapping | R: Disk plus X-shaped expanding component detected | F: Both coexist; likely common in low-mass post-AGB binaries | **supported**
- H: Previously known disk properties hold and outflow properties can be derived | E: Simple LTE modeling of 12CO 3-2 | R: Model reproduces the data with disk density halved and an outflow at 200 K | F: Disk confirmed; outflow described at ~10 km/s | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model is preliminary, LTE only, symmetric, and applied to 12CO 3-2 only  
  > "Our modeling is preliminary, but we think that it yields the main results that can be extracted from our data" (3 Results)
- Caveat (inferred, ours): Model fit is qualitative with no uncertainties
- Caveat (inferred, ours): Outflow temperature fixed, not fitted

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model code and outflow parameters
- Missing: Imaging parameters and self-calibration details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified and calibration outlined, but imaging and modeling details are sparse.
- Rediscovery candidate: no, Modeling recipe is incomplete and results are mostly qualitative.

## Links

- Method: Bujarrabal et al. 2005 (cite: bujetal05) (Modeling code)
- Companion: Bujarrabal & Alcolea 2013, Paper I (cite: bujal13) (Disk model)
- Companion: Bujarrabal et al. 2013, Paper II (cite: bujetal13) (CO profiles in similar post-AGB sources)

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
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 29,
  "rate": 0.483
 },
 "evidence_ok": true
}
```
