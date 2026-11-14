# Deep ALMA search for CO gas in the HD 95086 debris disc

`2019MNRAS.482.3443B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Booth, Mark | arXiv: 1811.00412 | DOI: 10.1093/mnras/sty2993

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks
- Question: Is there CO gas in the HD 95086 debris disc, and is its level consistent with second-generation production rather than primordial gas?  
  > "In this paper we conduct a deep search for CO gas in the system HD 95086" (abstract)
- Target **HD 95086**: coordinates _not stated_; z/distance 86.4±0.2 pc  
  > "HD 95086 is located at a distance of 86.4$\pm$0.2 pc (cite: gaia18)" (Introduction); distance from Gaia (cite: gaia18)  
  > "HD 95086 is located at a distance of 86.4$\pm$0.2 pc (cite: gaia18)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00773.S, 2013.1.00612.S, 2016.A.00021.T
- bands: Bands 3, 6, 7  
  > "we search for CO emission lines in bands 3, 6 and 7" (abstract)
- frequencies and spectral setup: 3840 channels per line window; 0.63 km/s (band 6, band 3), 0.42 km/s (band 7)  
  > "with one spectral window, which has 3840 channels of width 0.63 km s$^{-1}$ or 0.49 MHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 6: compact configuration  
  > "the observations were taken in band 6 whilst the array was in a compact configuration." (Observations)
- baselines: _not stated_
- angular resolution: Band 6 1.5x1.3"; band 3 1.9x1.7"; band 7 0.8x0.5"  
  > "The angular resolution is $1.5\times1.3\ensuremath{''}$ for both data sets." (Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS per channel: band 6 combined 0.38 mJy/beam; band 3 2.2; band 7 4.8  
  > "the data cube of the combined data has an RMS per spectral channel of 0.38 mJy beam$^{-1}$" (Observations)
- time on source: Band 6 combined 9.1 h; band 3 55 min; band 7 6 min  
  > "The total on-source observation time for the combined data sets is 9.1 hours." (Observations); "The band 3 data were for a total on-source observing time of 55 minutes." (Observations); "The band 7 data were for a total on-source observing time of 6 minutes" (Observations)
- observing dates: _not stated_
- pi or archival as stated: Su (A), Booth (B), Ho DDT (band 3/7)  
  > "#2013.1.00773.S (PI: Su; hereafter referred to as data set A)" (Observations)
- Line: CO J=2-1 (230.538 GHz)
- Line: CO J=1-0 (115.271 GHz)
- Line: CO J=3-2 (345.796 GHz)
- External data: Disc inclination ~31 deg and PA ~98 deg  
  > "which are found to be around 31$\ensuremath{^\circ}$ and 98$\ensuremath{^\circ}$ respectively (cite: su17a)" (3.1 CO J=2-1 analysis) [from (cite: su17a)]
- External data: Stellar radial velocities 17±2 and 10.1±1.2 km/s  
  > "used Hipparcos astrometry to determine a radial velocity of 10.1$\pm$1.2 km s$^{-1}$" (3.1 CO J=2-1 analysis) [from (cite: moor13; madsen02)]
- External data: Stellar distance and luminosity from Gaia  
  > "with a luminosity of $L_\star=6.63\pm0.03$ L$_\odot$ (cite: gaia18)" (Introduction) [from (cite: gaia18)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline mode  
  > "We reduced both data sets using `casa` version 4.7.2 in pipeline mode." (Observations)
- casa version: CASA 4.7.2  
  > "We reduced both data sets using `casa` version 4.7.2 in pipeline mode." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "We then inverted the visibilities using `CLEAN` to create the data cube using natural weighting" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting to optimise the signal to noise ratio" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on line-free parts of spectral window  
  > "We subtracted the continuum from each data set using `uvcontsub` by fitting to the parts of the spectral window that do not include the line." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Continuum images smoothed to 2.5" for spectral index map  
  > "We smooth them all to a consistent 2.5$''$ resolution" (4 Resolved spectral index map)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Further observation details and continuum analysis of data sets A and B  
  > "Further details of the observations along with analysis of the continuum data can be found in (cite: su17a)." (Observations) [from (cite: su17a)]
- Spectro-spatial filtering technique  
  > "if we make use of spatial and spectral filters as (cite: matra15; matra17a) have done for Fomalhaut" (3.1 CO J=2-1 analysis) [from (cite: matra15; matra17a)]
- Band 7 data discussed in detail elsewhere  
  > "is discussed in detail in (cite: zapata18)" (Observations) [from (cite: zapata18)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub and fit order
- CLEAN cell size, image size, masks and threshold
- Whether Hanning smoothing was applied in the pipeline
- Exact continuum spectral windows used for the spectral index images
- Arkenberg et al. PHOENIX model details (in prep.)
- Details of the curve-fitting routine used
- Belt radius and width used in the CO+CO2 fraction calculation

## Analysis recipe

1. **Image CO cubes**: Pipeline calibration, uvcontsub, natural-weighted CLEAN cubes  
  > "We reduced both data sets using `casa` version 4.7.2 in pipeline mode." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Spectro-spatial filtering**: Shift each pixel's spectrum by Keplerian radial velocity (M*~1.6 Msun, i=31, PA=98) and sum over continuum region, for both rotation senses  
  > "Shifting the spectra in each pixel by the negative of its assigned radial velocity relative to that of the star and then summing spatially across the region where the continuum is detected" (3.1 CO J=2-1 analysis)
   - parameter: Pixels with continuum SNR >=10 summed for unshifted spectrum  
  > "summing over all pixels with a signal-to-noise ratio of at least 10 in the continuum image" (3.1 CO J=2-1 analysis)
   - assumption: Gas Keplerian with same inclination and PA as dust disc  
  > "We assume the gas disc has the same inclination and position angle as the dust disc" (3.1 CO J=2-1 analysis)
   - fitting: Gaussian fit to filtered spectrum; errors from covariance matrix  
  > "The uncertainties on these values are calculated from the square root of the diagonal of the covariance matrix output by the curve fitting algorithm." (3.1 CO J=2-1 analysis)
   - validation: Checked in both data sets separately; false-positive probability ~8%  
  > "The probability of one of these containing noise of at least this level is roughly 8%" (3.1 CO J=2-1 analysis)
3. **Upper limits for CO 3-2 and 1-0**: Same analysis on band 7 and band 3 data; 3 sigma limits at stellar velocity assuming 2-1 line width  
  > "we are only able to place a 3$\sigma$ upper limit of 190 mJy km s$^{-1}$ at the stellar velocity" (3.2 CO J=3-2 analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert line flux to CO mass**: Molecular excitation code of Matra et al., PHOENIX stellar UV, electron density 1e-4 to 1e10 cm-3, Tkin 10-250 K  
  > "we use electron densities between 10$^{-4}$ and 10$^{10}$ cm$^{-3}$ and kinetic temperatures between 10 and 250 K" (5.1 Gas production within the disc)
   - software: PHOENIX
   - assumption: Collisional partners are electrons (second generation gas)  
  > "assumed to be electrons for a second generation gas production scenario" (5.1 Gas production within the disc)
   - fitting: _not stated_
   - validation: Compared to Kral et al. model prediction ~6e-6 Mearth  
  > "This results in a predicted CO mass of $\sim6\times10^{-6}$ M$_\oplus$." (5.1 Gas production within the disc)
5. **Resolved spectral index map**: Seven naturally-weighted CLEAN continuum images smoothed to 2.5", per-pixel power-law fit  
  > "Then for each pixel we fit a power law to get the spectral index and its uncertainty" (4 Resolved spectral index map)
   - assumption: Draine06 astrosilicate approximations for size distribution slope  
  > "By using the analytic approximations of (cite: draine06), which assume an astrosilicate composition" (5.4 Size distribution)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Pipeline reduction, uvcontsub, CLEAN imaging  
  > "We reduced both data sets using `casa` version 4.7.2 in pipeline mode." (Observations)
- **Astropy** : Acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)
- **PHOENIX** : Stellar atmosphere model for UV field  
  > "modelled using a PHOENIX stellar atmosphere model" (5.1 Gas production within the disc)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO J=2-1 integrated line flux | 9.5 | 3.6 | mJy km/s | 2 | we find an integrated line flux of 9.5$\pm$3.6 mJy km s$^{-1}$ |
| CO line velocity | 8.5 | 0.2 | km/s | 2 | 8.5$\pm$0.2 km s$^{-1}$ |
| CO mass | (1.4–13)e-6 | not stated | Earth masses | 4 | CO mass of (1.4–13)$\times 10^{-6}$ M$_\oplus$ |
| CO+CO2 ice mass fraction | 5.7-35.7 | not stated | % | 4 | This results in a CO+CO$_2$ mass fraction in the exocomets of 5.7-35.7% |
| CO J=3-2 3sigma upper limit | 190 | not stated | mJy km/s | 3 | 3$\sigma$ upper limit of 190 mJy km s$^{-1}$ |
| CO J=1-0 3sigma upper limit | 46 | not stated | mJy km/s | 3 | The 3$\sigma$ upper limit of 46 mJy km s$^{-1}$ |
| Mean disc spectral index | 2.41 | 0.12 | dimensionless | 5 | results in a spectral index of 2.41$\pm$0.12 |
| Bright source peak spectral index | 3.6 | 0.3 | dimensionless | 5 | with a peak at 3.6$\pm$0.3 |
| Grain size distribution slope | 3.27 | 0.07 | dimensionless | 5 | size distribution slope of 3.27$\pm$0.07 |

## Qualitative findings

- Gas appears to move towards us on the East side; northern side of the disc is the near side  
  > "then we can say that the South side of the disc and the planet are inclined away from us and the North side is the near side" (Conclusions)

## Claim tuples

- H: CO gas is present in the HD 95086 disc | E: Spectro-spatial filtering of band 6 CO 2-1 data | R: Peak 4.3±1.4 mJy at 8.5 km/s, 3.05 sigma, ~8% false-positive probability | F: Tentative CO detection | **partially**
- H: Gas is second-generation rather than primordial | E: Convert flux to CO mass and compare with collisional-cascade model | R: Mass (1.4-13)e-6 Mearth vs predicted ~6e-6 | F: Consistent with collisional cascade | **supported**
- H: The bright compact continuum source is a background galaxy | E: CO limit at its location and spectral index map | R: No CO concentration; spectral index 3.6±0.3 vs 2.41±0.12 | F: Supports unrelated background source | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Spectro-spatial filtering boosts SNR for low-SNR CO emission  
  > "we can attempt to increase the SNR by taking into account the velocity and shifting the spectra in each pixel" (3.1 CO J=2-1 analysis)
- Alternative: A 4.6 sigma CO 3-2 line at 2.3 km/s judged noise, not associated with disc  
  > "All this strongly suggests that this line is not associated with the disc and so is most likely just noise." (3.2 CO J=3-2 analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Detection is tentative and needs further observations  
  > "further observations are clearly required to determine for sure whether any CO is present in this system" (3.1 CO J=2-1 analysis)
- Caveat (inferred, ours): 3 sigma significance with a posteriori choice of velocity window
- Caveat (inferred, ours): Assumed Keplerian velocity and dust geometry for gas
- Caveat (inferred, ours): Wide CO mass range from unknown excitation conditions

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data:" (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: Line-free channel selection
- Missing: Custom filtering code not released
- Missing: PHOENIX/excitation code inputs
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data and main steps described, but imaging parameters and code are missing and the result is low-significance.
- Rediscovery candidate: no, Recipe lacks key parameters and the main result is a marginal detection depending on custom code.

## Links

- Method: (cite: matra15; matra17a) (Spectro-spatial filtering and CO mass conversion)
- Companion: (cite: su17a) (Continuum analysis of the same band 6 data)
- Companion: (cite: zapata18) (Earlier CO limits and band 7 data)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
