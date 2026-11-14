# ALMA Images of the Orion Hot Core at 349 GHz

`2017ApJ...843...83W` | The Astrophysical Journal 2017 | first author: Wright, M. C. H. | arXiv: 1705.03957 | DOI: 10.3847/1538-4357/aa72e6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What do ALMA 349 GHz dust and molecular line images reveal about the structure and heating of the Orion Hot Core, and its relation to the Source I outflow and the BN/SrcI explosion?  
  > "suggest that the Hot Core may be heated in shocks by the outflow from Source I or from the BN/SrcI explosion." (abstract)
- Target **Orion Hot Core / Orion KL (Source I)**: coordinates Molecular ring center RA 05:35:14.535, Dec -05:22:32.7  
  > "The Kleinmann-Low (KL) Nebula in Orion, at a distance of 415 pc (cite: Menten2007; Kim2008)" (INTRODUCTION); "centered at RA = 05:35:14.535 DEC= -05:22:32.7 $\pm 0.1''$" (Molecular Ring); z/distance 415 pc  
  > "The Kleinmann-Low (KL) Nebula in Orion, at a distance of 415 pc (cite: Menten2007; Kim2008)" (INTRODUCTION); "centered at RA = 05:35:14.535 DEC= -05:22:32.7 $\pm 0.1''$" (Molecular Ring); distance from Menten2007; Kim2008  
  > "The Kleinmann-Low (KL) Nebula in Orion, at a distance of 415 pc (cite: Menten2007; Kim2008)" (INTRODUCTION); "centered at RA = 05:35:14.535 DEC= -05:22:32.7 $\pm 0.1''$" (Molecular Ring)

## Data provenance

- ALMA projects: 2012.1.00123.S
- bands: Band 7 (349 GHz)  
  > "absolute calibration uncertainties of $\pm~10$% for Band 7" (CONTINUUM IMAGES)
- frequencies and spectral setup: 4 spectral windows, 3840 x 0.488 MHz channels, 2 polarizations  
  > "Spectral line data were obtained with $3840 \times 0.488$ MHz channels in 2 polarizations in each of 4 spectral windows." (OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.2 arcsec  
  > "The Orion Hot Core was imaged with ALMA at 349 GHz with $\sim$0.2$''$ angular resolution." (SUMMARY)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 July  
  > "The ALMA observations at 349 GHz, made in 2014 July" (OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: HC3N not stated (354.6975 GHz)
- Line: HCN v2=1 not stated (354.4604 and 356.2556 GHz)
- Line: SO2 not stated (342.7616 GHz)
- Other facility **CARMA**: 229 GHz continuum and 86 GHz SiO v=0 images for comparison  
  > "comparing these with CARMA images of the 229 GHz dust emission and the 86 GHz SiO v=0 outflow" (INTRODUCTION)
- External data: Compact dust source positions marked on Figure 1  
  > "The compact sources identified by (cite: Hirota2015) are marked by crosses in Figure 1." (CONTINUUM IMAGES) [from (cite: Hirota2015)]
- External data: CARMA 86 GHz SiO v=0 image  
  > "the CARMA image of the 86 GHz SiO line in the ground vibrational state (cite: Plambeck2009)" (CONTINUUM IMAGES) [from (cite: Plambeck2009)]

## Processing

### Calibration

- pipeline or manual: ALMA-supplied scripts with CASA  
  > "The visibility data were calibrated using ALMA-supplied scripts and the CASA software package." (OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ±10% (Band 7)  
  > "absolute calibration uncertainties of $\pm~10$% for Band 7, as given by the ALMA Cycle 1 Technical Handbook" (CONTINUUM IMAGES)
- self calibration: Phase self-cal on line-free continuum, baselines >250 kλ  
  > "The antenna-based phase corrections were derived only from visibilities with projected baselines greater than 250 k$\lambda$" (OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: Miriad; CLEAN, multifrequency synthesis across 4 spws  
  > "combined using multifrequency synthesis to avoid bandwidth smearing at the edge of the images" (CONTINUUM IMAGES)
- deconvolver: _not stated_
- weighting robust: robust=0.5, baselines >40 kλ  
  > "using all baselines $>$40 k$\lambda$, with `robust=0.5` weighting." (CONTINUUM IMAGES)
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

- ALMA observation details  
  > "Details of the ALMA observations are given in (cite: Plambeck2016) Table 1." (OBSERVATIONS AND DATA REDUCTION) [from (cite: Plambeck2016)]
- Self-calibration procedure  
  > "As described in (cite: Plambeck2016), the data were then self calibrated using continuum images generated from the line-free spectral channels." (OBSERVATIONS AND DATA REDUCTION) [from (cite: Plambeck2016)]
- CARMA 229 GHz calibration  
  > "The 229 GHz calibration is described in (cite: Plambeck2013)." (CONTINUUM IMAGES) [from (cite: Plambeck2013)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (cell, image size, masks, threshold, iterations)
- Line-free channels used for continuum
- Continuum subtraction method for line cubes
- Final beam and rms values
- Primary beam correction
- Spectral window frequencies and calibrators

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA scripts in CASA, export to Miriad, phase self-cal on line-free continuum  
  > "The calibrated CASA measurement sets then were written out in FITS format and imported into `Miriad`." (OBSERVATIONS AND DATA REDUCTION)
   - software: CASA, Miriad
   - fitting: _not stated_
   - validation: _not stated_
2. **Make continuum images and compare with CARMA**: MFS CLEAN, robust=0.5, >40 kλ; compare with 229 GHz CARMA and Hirota sources  
  > "The image was deconvolved using the `CLEAN` algorithm." (CONTINUUM IMAGES)
   - software: Miriad
   - fitting: _not stated_
   - validation: Visual agreement of 229 and 349 GHz images and with Hirota2015  
  > "There is good agreement between the 229 and 349 GHz emission" (CONTINUUM IMAGES)
3. **Make line channel images**: 1 km/s channels from -40 to +40 km/s, robust=0.5, >40 kλ, overlaid on SiO  
  > "We made spectral line images at 1 $\rm km~s^{-1}$ resolution in the velocity range -40 to +40 $\rm km~s^{-1}$" (SPECTRAL LINES)
   - software: Miriad
   - fitting: _not stated_
   - validation: _not stated_
4. **Energetics and ring estimates**: Blackbody luminosity, outflow mechanical luminosity, ring dynamical age and mass estimates  
  > "An expansion velocity $\sim$ 2 $\rm km~s^{-1}$ with a ring radius $\sim$ 300 AU gives a dynamical age $\sim$ 700 yr" (Molecular Ring)
   - assumption: Hot Core dust 100-150 K, ~1000 AU radius spherical blackbody  
  > "Modeling it as a spherical black body with $\sim ~1000$ AU radius, its luminosity is (0.4-2) $\times 10^4$ $\hbox{L}_\odot$." (Energetics)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration with ALMA scripts  
  > "The visibility data were calibrated using ALMA-supplied scripts and the CASA software package." (OBSERVATIONS AND DATA REDUCTION)
- **Miriad** : Self-calibration and imaging  
  > "All further processing was done with `Miriad`" (OBSERVATIONS AND DATA REDUCTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular ring diameter | ~2.6 x 1.9 arcsec (~600 AU) | not stated | arcsec | 4 | The ring presents an almost complete shell with a diameter $\sim  2.6 \times 1.9''$ |
| Ring dynamical age | ~700 | not stated | yr | 4 | gives a dynamical age $\sim$ 700 yr |
| Ring equilibrium mass | ~0.2 | not stated | Msun | 4 | gives an equilibrium mass $\sim$ 0.2 $\hbox{M}_\odot$ |
| Hot Core luminosity | (0.4-2)e4 | not stated | Lsun | 4 | its luminosity is (0.4-2) $\times 10^4$ $\hbox{L}_\odot$ |

## Qualitative findings

- Dust clumps form an arc ~1 arcsec east of SrcI and a chain toward IRc7, lying along the edges of the SiO outflow  
  > "Many of these filaments trace the SiO outflow from Source I, and lie along the edges of the dust emission." (abstract)

## Claim tuples

- H: Hot Core is heated externally by shocks | E: Compare line and dust images with SiO outflow | R: High-excitation lines at >10 km/s trace outflow edges; mechanical luminosity sufficient but needs high efficiency | F: Shocks from SrcI outflow or BN/SrcI explosion heat the Hot Core | **partially**
- H: A molecular ring exists south of SrcI | E: Line imaging in HC3N, HCN v2=1, SO2 | R: Ring ~600 AU diameter | F: Possibly from impact of BN/SrcI ejecta on a dust clump | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Poorly sampled large-scale structure gives deep sidelobes  
  > "very confused picture with deep sidelobes resulting from the poorly sampled large scale structures" (SPECTRAL LINES)
- Caveat (inferred, ours): Shock-heating interpretation is qualitative, no modelling
- Caveat (inferred, ours): Ring origin speculative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CLEAN settings
- Missing: Plambeck2016 details for calibration
- Missing: Line-free channels
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified and key imaging settings given, but many details deferred to Plambeck2016 and results mostly qualitative.
- Rediscovery candidate: no, Results mainly qualitative images.

## Links

- Method: (cite: Plambeck2016) (ALMA observations and self-calibration details)
- Companion: (cite: Plambeck2016) (Source I continuum analysis of same dataset)

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
  "facts": 66,
  "stated": 29,
  "rate": 0.439
 },
 "evidence_ok": true
}
```
