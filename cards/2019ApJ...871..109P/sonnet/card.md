# Multiband Optical and Near-Infrared Properties of Faint Submillimeter Galaxies with Serendipitous ALMA Detections

`2019ApJ...871..109P` | The Astrophysical Journal 2019 | first author: Patil, Pallavi | arXiv: 1812.04108 | DOI: 10.3847/1538-4357/aaf7a4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the optical/NIR properties, photometric redshifts and colors of faint SMGs serendipitously detected in archival ALMA data in the XMM-LSS field?  
  > "we study faint SMGs in the XMM Large Scale Structure (XMM-LSS) field with multi-band optical and infrared survey data that have serendipitous submm counterparts identified in archival ALMA observations." (1. INTRODUCTION)
- Target **XMM-LSS field faint SMGs (26 sources)**: coordinates see Table 1 (RA 02h16m-02h28m, Dec about -04 to -05.5 deg)  
  > "Our sample is drawn from the XMM-LSS field." (2.1 Optical and Infrared Data); z/distance photometric z 0.4-5.3, median 2.66  
  > "Our sample is drawn from the XMM-LSS field." (2.1 Optical and Infrared Data); distance from EAZY photometric redshifts from Tractor forced photometry  
  > "Our sample is drawn from the XMM-LSS field." (2.1 Optical and Infrared Data)

## Data provenance

- ALMA projects: 2011.0.00115.S, 2011.0.00648.S, 2012.1.00934.S, 2011.0.00539.S, 2012.1.00326.S, 2012.1.00374.S, 2013.1.00815.S, 2013.A.00021.S, 2015.1.01105.S
- bands: Band 6 (211-275 GHz) and Band 7 (275-370 GHz); all but one project in Band 6  
  > "observations performed in Band 6 (211 −275 GHz) or Band 7 (275 −370 GHz)" (2.2 Archival ALMA Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.53'' to 1.46''  
  > "The angular resolutions of the archival data ranged from 0.53 ′′ to 1.46 ′′ ." (2.2 Archival ALMA Data)
- max recoverable scale: _not stated_
- sensitivity: Band 6 15-140 uJy/beam; Band 7 200-300 uJy/beam  
  > "are 15-140 µ Jy beam −1 and 200-300 µ Jy beam −1, respectively." (2.2 Archival ALMA Data)
- time on source: integration time longer than 150 s required  
  > "a source integration time longer than 150 seconds" (2.2 Archival ALMA Data)
- observing dates: _not stated_
- pi or archival as stated: Public archival data as of July 2017, 75 continuum maps from nine projects  
  > "Our search identified 75 continuum maps from nine different projects" (2.2 Archival ALMA Data)
- Other facility **Spitzer SERVS/DeepDrill**: IRAC 3.6 and 4.5 um imaging  
  > "deep Spitzer IRAC observations at 3.6 and 4.5 µ m" (2.1 Optical and Infrared Data)
- Other facility **VIDEO (VISTA)**: Z, Y, J, H, Ks near-infrared imaging  
  > "in the Z, Y, J, H, and Ks bands" (2.1 Optical and Infrared Data)
- Other facility **HSC-SSP and CFHTLS-W1**: grizy and u-band optical  
  > "HSC in the grizy filter set and data from CFHTLS-W1 in the u band" (2.1 Optical and Infrared Data)
- External data: Quiescent galaxy UVJ color cuts  
  > "The quiescent galaxy color cuts are taken from Williams et al. (2009)." (4.4 The UVJ color-color plot) [from Williams et al. 2009]
- External data: OIRTC color cuts  
  > "Chen et al. (2016b) have devised a selection technique to identify bright as well as faint SMGs" (4.3 Optical-NIR Triple Color Selection) [from Chen et al. 2016b]

## Processing

### Calibration

- pipeline or manual: Archive-provided calibration scripts run in CASA, with extra flagging checks  
  > "We ran the calibration scripts that are provided along with the raw data from the ALMA archive." (3.1.1 Calibration and Imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: One round of phase-only self-cal for maps with bright targets  
  > "Maps with bright targets were self calibrated (using one round of phase-only self calibration) and re-imaged." (3.1.1 Calibration and Imaging)

### Imaging

- task: CLEAN, MFS, nterms = 1, recommended ALMA parameters  
  > "CLEAN was run in multifrequency synthesis (MFS) mode with nterms = 1." (3.1.1 Calibration and Imaging)
- deconvolver: _not stated_
- weighting robust: Natural or Briggs robust 0.5, case by case  
  > "The weighting was either Natural or Briggs weighting with a robust parameter of 0.5, and was determined on a case by case basis." (3.1.1 Calibration and Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Source search on uncorrected maps; JMFIT on PB-corrected maps  
  > "All JMFIT measurements were based on the primary-beam-corrected ALMA images." (3.1.2 Source Extraction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Tractor forced-photometry strategy  
  > "We have adopted a strategy similar to that described in Nyland et al. (2017)" (3.2 Multi-band Forced Photometry) [from Nyland et al. 2017]
- CLEAN parameters recommended by the ALMA observatory  
  > "with the recommended parameters provided by the ALMA observatory" (3.1.1 Calibration and Imaging) [from ALMA observatory]

### Not stated but needed to reproduce (our reading)

- Per-map choice of natural vs Briggs weighting
- Image size, cell size, clean threshold and masks
- CASA version
- Tractor and EAZY version/configuration, priors, template set details
- Which maps were self-calibrated
- Number of negative-peak source counts per SNR bin beyond figure
- Stacking method details

## Analysis recipe

1. **Calibrate and image archival ALMA data**: Run archive scripts in CASA, CLEAN MFS imaging  
  > "We reduced the archival ALMA data using the Common Astronomy Software Applications (CASA; McMullin et al. 2007) package." (3.1.1 Calibration and Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract sources and measure fluxes**: PyBDSF positions with threshpix 3.5 sigma; JMFIT Gaussian fit fluxes on PB-corrected maps  
  > "we set the pixel threshold parameter to 3.5 σ instead of 5 σ" (3.1.2 Source Extraction)
   - software: PyBDSF, AIPS JMFIT
   - fitting: single-component 2D Gaussian  
  > "we used JMFIT to fit a two-dimensional, single-component Gaussian" (3.1.2 Source Extraction)
   - validation: Compared with Fujimoto et al. 2016 for 20 overlapping pointings  
  > "Those six sources are also detected in our sample." (3.1.4 Comparison with Previous Studies)
3. **Choose detection threshold**: Negative peak analysis on maps multiplied by -1  
  > "we multiplied each ALMA image by -1 and ran PyBDSF using the same input parameters" (3.1.3 Detection Threshold)
   - software: PyBDSF
   - parameter: threshold 3.9 sigma; 176 sources  
  > "we selected a detection threshold of 3.9 σ for the archival ALMA data." (3.1.3 Detection Threshold)
   - fitting: _not stated_
   - validation: Counterpart matching on negative catalog: 7/88 vs 26/176  
  > "found 7 out of 88 sources with optical-NIR counterparts." (3.1.3 Detection Threshold)
4. **13-band forced photometry**: Cross-match ALMA with VIDEO within 1'', Tractor forced photometry on 10'' cutouts, fiducial VIDEO Ks band  
  > "using a search radius of 1 ′′ ." (3.2 Multi-band Forced Photometry)
   - software: Tractor, Photutils
   - fitting: maximum likelihood flux per band, position/shape fixed  
  > "uses a maximum likelihood method to optimize the flux of each source in each band" (3.2 Multi-band Forced Photometry)
   - validation: Compared with UKIDSS-UDS DR8 photometry (Appendix B)  
  > "Overall, there is a good level of agreement between our photometry and the UDS photometry." (B. PHOTOMETRY CONSISTENCY CHECK)
5. **Photometric redshifts and rest-frame colors**: EAZY with default templates, zpeak, 95% intervals, 0<z<6  
  > "We select the photometric redshift of a given source at the value with the highest probability ( z peak )." (3.3 Photometric Redshifts)
   - software: EAZY
   - fitting: least-squares linear combination of templates  
  > "EAZY performs least square fitting with a linear combination of minimal template sets" (3.3 Photometric Redshifts)
   - validation: Compared with literature redshifts incl. 3 spectroscopic  
  > "In all the cases, the spectroscopic redshifts are well within the 95% confidence interval of our photometric redshifts." (4.2 Previously Identified Galaxies)
6. **Stack undetected >5 sigma sources in IRAC**: Stack DeepDrill IRAC at positions of 60 undetected >5 sigma sources, split by 1 mJy  
  > "we stacked the DeepDrill IRAC data at the positions of the >5 σ sources (60/176)." (4.5 Stacking of Undetected ALMA Sources)
   - software: Montage
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "We reduced the archival ALMA data using the Common Astronomy Software Applications (CASA; McMullin et al. 2007) package." (3.1.1 Calibration and Imaging)
- **PyBDSF** : source extraction  
  > "The Python Blob Detector and Source Finder (PyBDSF) tool was used to extract sources from the ALMA maps" (3.1.2 Source Extraction)
- **AIPS JMFIT** : flux measurement  
  > "we used the JMFIT task from the Astronomical Image Processing Software (AIPS) to measure source fluxes" (3.1.2 Source Extraction)
- **Tractor** : multi-band forced photometry  
  > "We then fit the source fluxes using the Tractor" (3.2 Multi-band Forced Photometry)
- **Photutils** : sky RMS and background by sigma clipping  
  > "using iterative sigma clipping with Photutils" (3.2 Multi-band Forced Photometry)
- **EAZY** : photometric redshifts and rest-frame colors  
  > "Photometric redshifts were estimated using the Easy and Accurate z p hot from Yale (EAZY; Brammer et al. 2008, 2011) software." (3.3 Photometric Redshifts)
- **Montage** : named in acknowledgments  
  > "We also used MONTAGE" (ACKNOWLEDGMENTS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA detection threshold | 3.9 | not stated | sigma | 3 | we selected a detection threshold of 3.9 σ for the archival ALMA data. |
| ALMA sources above threshold | 176 | not stated | sources | 3 | our ALMA catalog was reduced to 176 objects. |
| Sources with optical-NIR counterparts | 26 | not stated | sources | 4 | found 26 faint SMGs with counterparts within a search radius of 1 ′′ . |
| Median photometric redshift Band 6 | 2.72 | not stated | dimensionless | 5 | The median redshifts for bands 6 and 7 are ⟨z⟩ = 2.72 and 2.57, respectively. |
| Median photometric redshift Band 7 | 2.57 | not stated | dimensionless | 5 | The median redshifts for bands 6 and 7 are ⟨z⟩ = 2.72 and 2.57, respectively. |
| Galaxies in quiescent UVJ box | 5 of 26 | not stated | galaxies | 5 | Five out of 26 galaxies are located within the quiescent box |
| Faint SMG median flux | 0.57 | not stated | mJy | 2 | 16 faint SMGs ( S 1.1 mm < 1 mJy) with a median flux of 0.57 mJy |
| IRAC 4.5um stack of faint (<1 mJy) undetected sources | 0.34 uJy (AB=25.3) | not stated | uJy | 6 | at the level of 0.34 µ Jy ( AB = 25.3 ) |

## Qualitative findings

- Sample colors are bluer than bright SMGs; only 18% satisfy Ks-[3.6] OIRTC cut  
  > "Whereas only 47% and 18% of the faint SMG population satisfy the OIRTC [3.6] µm −[4.5] µm and K s −[3.6] µm color criteria, respectively." (4.3 Optical-NIR Triple Color Selection)

## Claim tuples

- H: Archival ALMA data can yield a sizable sample of faint SMGs with multiwavelength counterparts | E: Serendipitous source search in 75 maps and cross-match with optical/NIR | R: 26 SMGs with counterparts, 15 new; 16 below 1 mJy | F: Archival mining is effective for finding faint SMGs | **supported**
- H: Faint SMGs have different colors from bright SMGs | E: OIRTC and UVJ comparison | R: Most lie outside OIRTC cuts; most on star-forming UVJ track | F: Faint SMGs are bluer and consistent with main-sequence star-forming galaxies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Tractor forced photometry avoids IRAC blending problems  
  > "make the IRAC data prone to issues with source blending." (3.2 Multi-band Forced Photometry)
- Alternative: PyBDSF fluxes rejected due to overestimation for faint sources; JMFIT used  
  > "In order to avoid known issues with flux overestimation of faint sources with PyBDSF" (3.1.2 Source Extraction)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample incomplete and no completeness or number counts  
  > "Since we are limited by the availability of data in the archive, our sample will naturally be incomplete." (3.1.3 Detection Threshold)
- Caveat (inferred, ours): Photometric redshifts rely on default templates that may not fit dusty SMGs
- Caveat (inferred, ours): 3.9 sigma threshold gives contamination; fidelity relies on counterpart matching
- Caveat (inferred, ours): Heterogeneous depths and no completeness correction

## Reproducibility

- Data public (paper): Archival public ALMA data and public optical/NIR surveys  
  > "observations within the XMM-LSS field that were publicly available as of July 2017" (2.2 Archival ALMA Data)
- Products in archive: _not stated_
- Missing: Exact imaging parameters per map
- Missing: CASA version
- Missing: Tractor/EAZY configuration
- Missing: Per-source weighting choice
- Data volume (inferred): Moderate: 75 ALMA continuum pointings from 9 projects (~tens to a few hundred GB raw) plus survey cutouts
- Score (inferred): 3/5, Public data and named tools, but imaging and photometry settings are partly unspecified.
- Rediscovery candidate: yes, Public data, clear recipe and numeric results (threshold, counts, median z), though some settings are missing.

## Links

- Method: Nyland et al. 2017 (Tractor forced photometry strategy)
- Method: Lang et al. 2016 (Tractor code)
- Companion: Fujimoto et al. 2016 (Comparison archival ALMA sample)
- Related: SERVS
- Related: DeepDrill
- Related: VIDEO
- Related: CFHTLS
- Related: HSC-SSP

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 47,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
