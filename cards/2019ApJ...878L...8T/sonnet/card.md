# Discovery of An au-scale Excess in Millimeter Emission from the Protoplanetary Disk around TW Hya

`2019ApJ...878L...8T` | The Astrophysical Journal Letters 2019 | first author: Tsukagoshi, Takashi | arXiv: 1905.07891 | DOI: 10.3847/2041-8213/ab224c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Is there small-scale (au-scale) non-axisymmetric substructure in the 1.3 mm dust continuum of the TW Hya disk, and what is its origin?  
  > "we report the results of our high-sensitivity observations at Band 6 using ALMA and the first finding of an au-scale substructure at a radius of 52 au in the PPD around TW Hya." (1 Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 59.5 pc  
  > "TW Hya is the nearest T Tauri star with a distance of 59.5 pc (cite: bib:gaia2016)." (1 Introduction); "The disk orientation is almost face-on with an inclination of 7$\ensuremath{^\circ}$ (cite: bib:qi2004)." (1 Introduction); distance from Gaia Collaboration 2016  
  > "TW Hya is the nearest T Tauri star with a distance of 59.5 pc (cite: bib:gaia2016)." (1 Introduction); "The disk orientation is almost face-on with an inclination of 7$\ensuremath{^\circ}$ (cite: bib:qi2004)." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00842.S, 2017.1.00520.S, 2015.1.00308.S, 2015.1.00686.S, 2016.1.00229.S, 2016.1.00311.S, 2016.1.00440.S, 2016.1.00464.S, 2016.1.00629.S, 2016.1.01495.S
- bands: Band 6 (233 GHz, 1.3 mm) new; Band 7 archival (center 325.4 GHz)  
  > "Our 233 GHz (1.3 mm) continuum observations at Band 6 toward TW Hya were carried out using ALMA" (2.1 Sensitive ALMA Observation at Band 6); "The center frequency of the concatenated data was 325.4 GHz." (2.2 Data Reduction of the Band 7 Archive Data)
- frequencies and spectral setup: four spectral windows centered at 225, 227, 239, 241 GHz  
  > "The four spectral windows were tuned to detect continuum emission centered at 225, 227, 239, and 241 GHz." (2.1 Sensitive ALMA Observation at Band 6)
- continuum bandwidth: 7.5 GHz total (4 x 1.875 GHz)  
  > "four spectral windows with a bandwidth of 1.875 GHz each, resulting a bandwidth of 7.5 GHz in total" (2.1 Sensitive ALMA Observation at Band 6)
- arrays: _not stated_
- configurations: C40-5 (2016.1.00842.S) and C43-8 (2017.1.00520.S)  
  > "with array configuration C40-5 (2016.1.00842.S) and in the period from 20 to 25 November 2017 with C43-8 (2017.1.00520.S)" (2.1 Sensitive ALMA Observation at Band 6)
- baselines: _not stated_
- angular resolution: Band 6: 46.88x41.56 mas (2.79x2.48 au), PA -78.9 deg  
  > "The spatial resolution of the CLEANed image was 46.88$\times$41.56 mas, full width at half maximum (FWHM) with a position angle of $-78.9^\circ$" (2.1 Sensitive ALMA Observation at Band 6)
- max recoverable scale: _not stated_
- sensitivity: Band 6 rms 9.1 uJy/beam; Band 7 rms 27.7 uJy/beam  
  > "The 1$\sigma$ root-mean-square (rms) noise level achieved was 9.1 $\mu$Jy beam$^{-1}$." (2.1 Sensitive ALMA Observation at Band 6); "The rms noise level of the resultant image is 27.7 $\mu$Jy beam$^{-1}$." (2.2 Data Reduction of the Band 7 Archive Data)
- time on source: ~12 min (C40-5) and ~200 min (C43-8)  
  > "The total on-source integration times were $\sim$12 and $\sim200$ minutes, respectively." (2.1 Sensitive ALMA Observation at Band 6)
- observing dates: 15 May 2017 and 20-25 November 2017 (Band 6); Band 7 high-res data December 2015  
  > "carried out using ALMA on 15 May 2017 with array configuration C40-5" (2.1 Sensitive ALMA Observation at Band 6)
- pi or archival as stated: _not stated_
- External data: Dust mass opacity 2.8 cm2/g at 870 um, beta ~0.5  
  > "determined from $\kappa_\nu$ of 2.8 cm$^2$ g$^{-1}$ at a wavelength of 870 $\mu$m (cite: bib:andrews2012)" (3 Results) [from (cite: bib:andrews2012)]
- External data: Dust temperature 18 K at 52 au  
  > "Assuming $T_\mathrm{dust}=18$ K (cite: bib:huang2018)" (3 Results) [from (cite: bib:huang2018)]
- External data: Proper motion of TW Hya system  
  > "according to the proper motion of the TW Hya system (cite: bib:gaia2016)" (3 Results) [from (cite: bib:gaia2016)]
- Simulation/model as data: Simple CPD flux model of Zhu et al. 2016 used to estimate mm flux of CPD around Neptune-mass planet vs alpha and accretion rate  
  > "We use a simple model by (cite: bib:zhu2016) to estimate the flux density at millimeter wavelengths from the CPD around a Neptune-mass planet." (4 Discussion)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline scripts  
  > "were performed using the pipeline scripts provided by ALMA" (2.1 Sensitive ALMA Observation at Band 6)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133, J1107-4449, or J1037-2934  
  > "flux scales were determined by observing J1058+0133, J1107-4449, or J1037-2934" (2.1 Sensitive ALMA Observation at Band 6)
- flux scale uncertainty: _not stated_
- self calibration: Applied to concatenated data (Band 6); iterative self-cal for Band 7  
  > "After that, self-calibration was applied for the concatenated data set." (2.1 Sensitive ALMA Observation at Band 6)

### Imaging

- task: CLEAN in CASA  
  > "the corrected data were concatenated and imaged by CLEAN" (2.1 Sensitive ALMA Observation at Band 6)
- deconvolver: _not stated_
- weighting robust: Band 6 Briggs robust 0.5; Band 7 robust -1.0  
  > "The CLEAN map was created by adopting Briggs weighting with a robust parameter of 0.5." (2.1 Sensitive ALMA Observation at Band 6); "we adopt Briggs weighting with a robust parameter of -1.0" (2.2 Data Reduction of the Band 7 Archive Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: Band 6 [0,42,126] mas; Band 7 [0,30,90] mas  
  > "multiscale CLEAN with scale parameters of \[0, 42, 126\] mas" (2.1 Sensitive ALMA Observation at Band 6); "Multiscale CLEAN with scale parameters of \[0, 30, 90\] mas was employed." (2.2 Data Reduction of the Band 7 Archive Data)
- continuum subtraction: _not stated_
- line free channels: Line-free channels used for Band 7 continuum (ranges not given)  
  > "Line free channels were used for making the map of continuum emission at Band 7." (2.2 Data Reduction of the Band 7 Archive Data)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Band 7 image smoothed to 50 mas with imsmooth  
  > "we have smoothed the final CLEANed image to 50 mas resolution using the *imsmooth* task on CASA" (2.2 Data Reduction of the Band 7 Archive Data)
- final beam: Band 6 46.88x41.56 mas; Band 7 36.4x28.9 mas, PA 69.9 deg (before smoothing)  
  > "The final CLEANed image had a synthesized beam size of 36.4$\times$28.9 mas (2.2$\times$1.7 au) with a position angle of 69.9$^\circ$." (2.2 Data Reduction of the Band 7 Archive Data)
- final rms: 9.1 uJy/beam (Band 6); 27.7 uJy/beam (Band 7)  
  > "The 1$\sigma$ root-mean-square (rms) noise level achieved was 9.1 $\mu$Jy beam$^{-1}$." (2.1 Sensitive ALMA Observation at Band 6)

### Inherited from earlier work

- Band 7 highest-resolution archival data from Andrews et al. 2016 included  
  > "The highest resolution data obtained by (cite: bib:andrews2016) is included" (2.2 Data Reduction of the Band 7 Archive Data) [from (cite: bib:andrews2016)]
- Band 7 reduction done in same manner as Band 6  
  > "Data reduction has been done in the same manner as for our Band 6 observations described above." (2.2 Data Reduction of the Band 7 Archive Data) [from Section 2.1]

### Not stated but needed to reproduce (our reading)

- Which of the listed Band 7 projects/execution blocks were used, and how they map to the eight datasets
- CASA version and pipeline version
- Self-calibration solution intervals, number of rounds and reference
- CLEAN threshold, masks, cell/image size, iterations
- Method and parameters of axisymmetric model subtraction in uv domain (radial profile used, center, inclination/PA)
- uvmodelfit starting parameters
- Line-free channel ranges for Band 7
- Flux calibrator flux values and which calibrator for which EB
- Stellar position/center determination

## Analysis recipe

1. **Image Band 6 and Band 7 continuum**: Pipeline calibration, concatenation, multiscale CLEAN with self-calibration  
  > "After flagging the bad data, the corrected data were concatenated and imaged by CLEAN." (2.1 Sensitive ALMA Observation at Band 6)
   - software: CASA
   - parameter: Band 6 robust 0.5, scales [0,42,126] mas  
  > "The CLEAN map was created by adopting Briggs weighting with a robust parameter of 0.5." (2.1 Sensitive ALMA Observation at Band 6)
   - fitting: _not stated_
   - validation: Total flux and gaps at 25 and 41 au consistent with previous works  
  > "The total flux density from the PPD and the known axisymmetric features, gaps at 25 and 41 au, are consistent with previous works" (3 Results)
2. **Measure excess relative to surrounding disk**: Compare peak intensity with mean of surrounding emission in azimuthal ranges; radial and azimuthal profiles  
  > "The average of the surrounding emission is measured to be 197.1 $\mu$Jy beam$^{-1}$ from position angles of 226–230$^\circ$ and 244–248$^\circ$" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Subtract axisymmetric disk and fit excess in uv domain**: Subtract axisymmetric emission in visibility domain, then least-squares single Gaussian fit with uvmodelfit  
  > "the emission feature is extracted by subtracting the axisymmetric background emission in the visibility (i.e., $u$-$v$) domain." (3 Results); "we performed a least squares fitting to the subtracted visibilities using the *uvmodelfit* task installed on CASA." (3 Results)
   - software: CASA uvmodelfit
   - parameter: Single Gaussian component  
  > "A single component described by a Gaussian function was assumed for the model." (3 Results)
   - fitting: Least-squares, single Gaussian  
  > "we performed a least squares fitting to the subtracted visibilities using the *uvmodelfit* task installed on CASA." (3 Results)
   - validation: Modeled visibilities converted to image with CLEAN and compared to residual  
  > "The modeled visibilities determined by the fitting were converted to an image using CLEAN with the same parameters as for the original image" (3 Results)
4. **Brightness temperature and dust mass**: Planck function brightness temperature; M = F d^2/(kappa B(T))  
  > "M_\mathrm{dust} = \frac{F_\nu d^2}{\kappa_\nu B(T_\mathrm{dust})}" (3 Results)
   - assumption: kappa = 2.3 cm2/g at 233 GHz (beta ~0.5), T_dust = 18 K, d = 59.5 pc, uniform background  
  > "We employ a dust mass opacity coefficient $\kappa_\nu$ of 2.3 cm$^2$ g$^{-1}$ at a frequency of 233 GHz" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Check against background-source hypothesis with Band 7**: Compare position of residual in Band 7 image (2 yr earlier) with Band 6 position versus expected proper motion  
  > "If the excess emission is a background source, the positional offset must be 136 mas for 2 yrs in the R.A. direction" (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Band 7 residual within ~50 mas  
  > "The positional deviation of the residual emission at Band 7 is within only $\sim$50 mas with respect to the emission feature at Band 6" (3 Results)

## Software

- **CASA** : Calibration, CLEAN imaging, uvmodelfit, imsmooth  
  > "The observed visibilities were reduced and calibrated using the Common Astronomical Software Application (CASA) package" (2.1 Sensitive ALMA Observation at Band 6)
- **astropy** : Listed in software section; use not specified  
  > "astropy, CASA," (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excess peak intensity | 308.4 | not stated | uJy/beam | 2 | The peak intensity at this feature is measured to be 308.4 $\mu$Jy beam$^{-1}$, corresponding to signal-to-noise (SN) ratio of 34. |
| Excess above surroundings | 111.5 | 9.1 | uJy/beam | 2 | hence the excess is calculated to be 111.5$\pm$9.1 $\mu$Jy beam$^{-1}$ ($\sim12\sigma$) |
| Radius of feature | 51.5 | 0.1 | au | 3 | or a radius of 51.5$\pm$0.1 au |
| Gaussian FWHM size | 4.4 x 1.0 | 0.2, 0.2 | au | 3 | corresponding to (4.4$\pm$0.2)$\times$(1.0$\pm$0.2) au |
| Total flux density of excess | 250 | 5 | uJy | 3 | The total intensity of the fitted Gaussian is 250$\pm$5 $\mu$Jy. |
| Brightness temperature | 11.6 | not stated | K | 4 | the brightness temperature at the position of the emission feature is converted using the Planck function to be 11.6 K |
| Dust mass of excess | 2.83e-2 | 0.06e-2 | Earth masses | 4 | the total dust mass of the emission feature is (2.83$\pm$0.06)$\times10^{-2}$ $M_\oplus$ |

## Qualitative findings

- Disk is mostly axisymmetric with gaps at 25 and 41 au; an au-scale azimuthally elongated excess is at 52 au SW  
  > "The overall structure is mostly axisymmetric, and there are apparent gaps at 25 and 41 au as previously reported." (abstract)

## Claim tuples

- H: Is there a small-scale non-axisymmetric excess in the TW Hya disk? | E: Deep Band 6 imaging at ~3 au resolution and uv-domain subtraction/fit | R: Excess at 52 au, 1.5x surroundings, ~12 sigma, 4.4x1.0 au, 250 uJy | F: A new au-scale excess is detected | **supported**
- H: The excess is a background source | E: Compare Band 7 archival image taken 2 yr earlier with Band 6 position | R: Offset ~50 mas, much smaller than expected 136 mas | F: Feature belongs to the disk | **supported**
- H: The excess is a dust clump in a vortex or a CPD of a forming planet | E: Compare size/aspect ratio with vortex theory and Zhu et al. CPD model | R: Aspect ratio ~4; CPD flux <~100 uJy for 1e-7 MNep/yr | F: Both vortex and CPD plausible; mm data cannot distinguish | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Background source rejected via proper-motion test  
  > "If the excess emission is a background source, the positional offset must be 136 mas for 2 yrs in the R.A. direction" (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Millimeter data alone cannot determine whether a planet exists; CPD may not fully account for the flux  
  > "However, it should be noted that the observed emission feature may not be fully accounted for by emission from a CPD." (4 Discussion)
- Caveat (inferred, ours): Band 7 detection is only marginal and elongated, so the proper-motion test is weak
- Caveat (inferred, ours): Axisymmetric subtraction may bias residual flux and size
- Caveat (inferred, ours): Single dust temperature and opacity assumed; mass uncertainty underestimated
- Caveat (inferred, ours): Statistical-only errors; no systematic or self-calibration artifact assessment

## Reproducibility

- Data public (paper): Archival ALMA data used are public; new data are ALMA project data  
  > "We also use the following public ALMA archive data" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Axisymmetric subtraction procedure details
- Missing: CASA version
- Missing: Which execution blocks included
- Data volume (inferred): Several hundred GB (many long-baseline EBs plus eight Band 7 datasets)
- Score (inferred): 3/5, Data are public and main steps are named with key imaging parameters, but self-cal and axisymmetric subtraction details are missing.
- Rediscovery candidate: yes, Public data, numeric results, and reasonably clear recipe, though the axisymmetric subtraction is underspecified.

## Links

- Companion: Tsukagoshi et al. 2016 (cite: bib:tsukagoshi2016) (Previous Cycle 3 Band 6 observations of TW Hya)
- Companion: Andrews et al. 2016 (cite: bib:andrews2016) (Source of highest-resolution Band 7 data)
- Companion: Huang et al. 2018 (cite: bib:huang2018) (Disk structure and temperature)

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 45,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
