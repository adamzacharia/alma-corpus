# On the Nature of the T Tauri Triple System

`2020ApJ...902..132B` | The Astrophysical Journal 2020 | first author: Beck, Tracy L. | arXiv: 2009.03861 | DOI: 10.3847/1538-4357/abb5f5

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What is the geometry of the T Tau triple system, its circumbinary material, and how its outflows relate to the Sa+Sb orbit?  
  > "In this paper, we present a new multi-wavelength investigation of the T Tauri triple to reveal the new observable characteristics of the system and its geometry." (Introduction)
- Target **T Tau (N, Sa, Sb)**: coordinates _not stated_; z/distance 143.7 pc (Gaia DR2) or 148.7 pc (VLBI)  
  > "143.7pc from Gaia DR2 (cite: bail18), or 148.7pc from VLBI measurements (cite: xu19)." (Introduction); distance from Gaia DR2 (cite: bail18); VLBI (cite: xu19)  
  > "143.7pc from Gaia DR2 (cite: bail18), or 148.7pc from VLBI measurements (cite: xu19)." (Introduction)

## Data provenance

- ALMA projects: 2016.1.01164.S
- bands: Band 6, 233 GHz (1.33 mm)  
  > "we improved the image processing in the 233GHz (1.33mm) data using phase self-calibration techniques" (Archival 1.3mm ALMA Continuum Imaging)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 47 12-m antennas, 21-3697 m  
  > "using 47 12-m antennas on baselines of 21$\sim$3697m" (Archival 1.3mm ALMA Continuum Imaging)
- angular resolution: 0.12 arcsec  
  > "Band 6 at 0.$\ensuremath{''}$12 resolution" (Archival 1.3mm ALMA Continuum Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 18 August 2017  
  > "The observations of T Tau were obtained on 18 August 2017" (Archival 1.3mm ALMA Continuum Imaging)
- pi or archival as stated: Archival, PI Herczeg  
  > "PI= Herczeg; published in (cite: long19) and (cite: mana19)" (Archival 1.3mm ALMA Continuum Imaging)
- Other facility **Gemini North (GMOS, NIFS, Michelle)**: Optical Halpha imaging, IFU spectroscopy, near-IR IFU, mid-IR imaging  
  > "In this paper we present previously unpublished imaging, spectroscopy and imaging spectroscopy at optical, near-IR and mid-IR wavelengths." (Observations)
- Other facility **HST ACS**: Archival UV H2 imaging (F140LP, F165LP)  
  > "We re-analyzed archival data from the HST ACS ultraviolet imaging from project 10489" (Archival HST Ultraviolet Imaging)
- Other facility **Chandra**: Archival X-ray 0th order image  
  > "T Tau was observed with the Chandra X-ray Observatory from 01-03 January 2015 under program number 16672" (Archival Chandra X-Ray Imaging)
- External data: Orbit model and near-IR AO photometry/astrometry of Sa and Sb (27.2 yr period, periastron dates)  
  > "in the 27.2$\pm$0.7 year orbital period (cite: scha20)" (Infrared Variability of T Tau South) [from (cite: scha20)]
- External data: Archival H2 maps from 2002, 2004, 2005 for proper motions  
  > "we used the maps of (cite: herb07) from 2002, (cite: gust10) from 2004, (cite: beck08) from 2005" (Appendix 1: Tangential Motions from Four Epochs of H$_2$ Spectral Imaging) [from (cite: herb07; gust10; beck08)]

## Processing

### Calibration

- pipeline or manual: Archive pipeline products had artifacts; re-processed with phase self-calibration  
  > "The pipeline science data products in the archive had visible artifacts, so we improved the image processing" (Archival 1.3mm ALMA Continuum Imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal with 6 s smoothing time raised dynamic range 300 to 1600; amplitude self-cal 12 s gave no gain  
  > "The phase self calibration with 6sec smoothing time improved the dynamic range of the default calibrations from 300 to 1600." (Archival 1.3mm ALMA Continuum Imaging)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final rms: _not stated_

### Inherited from earlier work

- General ALMA program observations described elsewhere  
  > "The general program observations are described in (cite: mana19)." (Archival 1.3mm ALMA Continuum Imaging) [from (cite: mana19)]
- NIFS reduction described in earlier paper  
  > "the reduction process is described in detail in (cite: beck08)" (Near-IR Integral Field Spectroscopy) [from (cite: beck08)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details for self-calibration (solint, reference antenna, spw selection)
- Imaging parameters (weighting, cell, size, clean settings)
- uv_fit starting model, fit weights and error estimation
- Scaling used for residual map and its noise level
- Flux scale calibrator and uncertainty

## Analysis recipe

1. **self-calibrate archival 1.3 mm data**: Phase self-calibration (6 s) then amplitude self-cal (12 s, no gain)  
  > "An amplitude self calibration with 12sec smoothing time resulted in no further gain." (Archival 1.3mm ALMA Continuum Imaging)
   - fitting: _not stated_
   - validation: Dynamic range improved 300 to 1600  
  > "improved the dynamic range of the default calibrations from 300 to 1600" (Archival 1.3mm ALMA Continuum Imaging)
2. **fit circumstellar disk models in uv plane and make residual map**: Global fit to visibilities: elliptical Gaussians for N and Sa, point source for Sb; subtract model to image residual  
  > "We modeled the emission from T Tau N and Sa each by an elliptical Gaussian, and that from T Tau Sb by a point source." (4 Disks in the T Tau System)
   - software: GILDAS
   - parameter: position, intensity, sizes and orientation free  
  > "keeping the position, intensity and, where relevant, sizes and orientation of the model sources as free parameters" (4 Disks in the T Tau System)
   - fitting: UV_FIT in IMAGER  
  > "We used the UV\_FIT command in the ’IMAGER’ program of the GILDAS software tool" (4 Disks in the T Tau System)
   - validation: Compared to Manara et al. fits  
  > "The results for our disk fit for T Tau N are similar to those derived by (cite: mana19) from the same dataset." (4.1 The Circumstellar Disks)
3. **interpret residual as circumbinary ring and compare with line silhouettes**: Measure integrated residual flux; compare to dark lanes in UV H2, [OI], He I maps; convert peak brightness to Av  
  > "The total integrated flux of this emission across its spatial extent is 17$\pm$2 mJy." (4.2 A Circumbinary Ring Around T Tau Sa and Sb)
   - assumption: T_dust = 20 K, kappa_dust = 0.02 cm2/g  
  > "assuming T$_{dust}$ = 20 K and $\kappa_{dust}$ = 0.02 cm$^2$/g" (4.2 A Circumbinary Ring Around T Tau Sa and Sb)
   - fitting: _not stated_
   - validation: Agreement with Av~15-20 line-of-sight attenuation and silhouette orientation  
  > "the measured 1.3mm residual dust is in strong agreement with the magnitude of the attenuating line-of-sight circumbinary disk material" (4.2 A Circumbinary Ring Around T Tau Sa and Sb)

## Software

- **GILDAS (IMAGER)** : uv-plane fitting of ALMA 1.3 mm visibilities  
  > "We used the UV\_FIT command in the ’IMAGER’ program of the GILDAS software tool" (4 Disks in the T Tau System)
- **Gemini IRAF** : Reduction of GMOS, NIFS and Michelle data  
  > "The optical IFU data were processed using the standard routines in the Gemini GMOS IRAF package" (Optical Integral Field Spectroscopy)
- **DRAGONS** : Reduction of 2019 GMOS Halpha images  
  > "The DRAGONS data reduction package offered by the Gemini Observatory was used to process the images" (Optical Imaging)
- **Blender** v. 2.8: 3-D visualization of geometry  
  > "Blender v. 2.8 3-D Data Visualization and Animation package" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| T Tau N integrated 1.3 mm flux | 190.0 | 0.2 | mJy | 2 | / T Tau N / 190.0$\pm$0.2 / 18 / 28$\pm$1$^{\circ}$ / 89$\pm$1$^{\circ}$ / |
| T Tau Sa integrated 1.3 mm flux | 8.4 | 0.06 | mJy | 2 | / T Tau Sa / 8.4$\pm$0.06 / 3.5 / $>$70$^{\circ}$ / 4$\pm$2$^{\circ}$ / |
| T Tau Sb integrated 1.3 mm flux | 1.17 | 0.05 | mJy | 2 | / T Tau Sb / 1.17$\pm$0.05 / $<$2 / – / – / |
| Circumbinary residual 1.3 mm flux | 17 | 2 | mJy | 3 | The total integrated flux of this emission across its spatial extent is 17$\pm$2 mJy. |
| Average tangential motion of H2 knots | 38 | 9 | km/s | 0 | The average tangential motion of the outflowing knots from T Tau Sa+Sb is 38$\pm$9 km/s |
| T Tau N behind Sa+Sb | ~620 | not stated | AU | 0 | allows us to derive that T Tau N is located $\sim$620 AU behind the T Tau Sa+Sb binary in this geometry |

## Qualitative findings

- Dark lane in UV H2, [OI] and He I coincides with residual mm dust, tracing a circumbinary ring around T Tau S  
  > "the emission line maps clearly reveal the silhouette of the circumbinary ring material" (4.2 A Circumbinary Ring Around T Tau Sa and Sb)

## Claim tuples

- H: Is there a circumbinary ring around T Tau Sa+Sb? | E: Subtracted 3-disk model from ALMA 1.3 mm data and compared residual with UV/optical/IR line silhouettes | R: 17±2 mJy extended residual at PA~60 deg aligned with dark lanes | F: Residual dust is the circumbinary ring causing the foreground attenuation | **supported**
- H: Are southern outflow arcs launched at binary periastron? | E: Halpha arc positions and 2004-2019 proper motions traced back versus periastron dates | R: Arc A ejection within 1 month of 1996 periastron; arcs A-D span periastron dates | F: Ejections contemporaneous with, perhaps triggered by, periastron | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Direct mm detection of circumbinary dust is moderate significance; 13CO/C18O data unusable due to missing short spacings  
  > "Taken by itself, this direct detection of dust in a circumbinary distribution is unconvincing." (4.2 A Circumbinary Ring Around T Tau Sa and Sb)
- Caveat (inferred, ours): Residual could be over/under-subtraction artifact of the disk model
- Caveat (inferred, ours): Circumbinary Av estimate depends on assumed dust temperature and opacity
- Caveat (inferred, ours): Arc ejection timing uncertainties are large

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "we re-analyzed archival data from the Atacama Large MM Array (ALMA) from project 2016.1.01164.S" (Archival 1.3mm ALMA Continuum Imaging)
- Products in archive: _not stated_
- Missing: Self-calibration and imaging parameters
- Missing: UV_FIT initial parameters
- Data volume (inferred): ~50-100 GB for the ALMA Band 6 dataset
- Score (inferred): 3/5, ALMA public and fitting approach described, but few parameters given; most paper uses non-ALMA data.
- Rediscovery candidate: no, ALMA is a minor part and key processing parameters are missing.

## Links

- Companion: (cite: scha20) (Near-IR AO imaging and orbit model of T Tau Sa+Sb)
- Companion: (cite: mana19) (Earlier analysis of the same ALMA data)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 33,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
