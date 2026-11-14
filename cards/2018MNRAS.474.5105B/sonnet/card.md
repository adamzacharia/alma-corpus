# HD 169142 in the eyes of ZIMPOL/SPHERE

`2018MNRAS.474.5105B` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Bertrang, G. H.-M. | arXiv: 1711.09040 | DOI: 10.1093/mnras/stx3052

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What substructures and signs of planet-disc interaction appear in new SPHERE/ZIMPOL polarimetric images of the HD 169142 disc, and can radiative transfer and hydrodynamic models explain them?  
  > "we present our new SPHERE/ZIMPOL data on HD$\,$169142 which confirm the previously found gap structure as well as reveal yet undetected indications for planet-disc interactions" (Introduction)
- Target **HD 169142**: coordinates _not stated_; z/distance 117 ± 4 pc  
  > "is a well-studied object at a distance of only $117\pm 4\,$pc" (Introduction); distance from literature (Gaia, 2016A&A...595A...2G among cited)  
  > "is a well-studied object at a distance of only $117\pm 4\,$pc" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA band 7 (880 um) used for comparison; main data are VLT/SPHERE ZIMPOL  
  > "In the ALMA band 7 data, the bright inner ring appears significantly wider compared to the ZIMPOL data" (4 Radiative transfer model)
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
- Other facility **VLT/SPHERE ZIMPOL**: Polarimetric differential imaging at VBB, R and I filters (main data)  
  > "The data were taken during the nights of July 8 and 9, 2015, at the ESO Very Large Telescope situated on Cerro Paranal" (2 Observations and Data Reduction)
- Other facility **VLA**: 7 mm and 9 mm results from literature compared  
  > "A third, narrow gap at $\sim 85\,$au was detected in recent VLA observations at $7\,$mm and $9\,$mm" (Introduction)
- External data: ALMA 880 um image of HD 169142 compared with ZIMPOL; ALMA dust-gap constraints  
  > "This relatively narrow ring is more extended in the ALMA observation at $880\mu$m" (3 Results and Analysis) [from (cite: 2017A&A...600A..72F)]

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

- Correction of instrumental effects and double-ratio Stokes calculation  
  > "Instrumental effects (difference between ordinary and extraordinary beam) are corrected as described in the appendix of (cite: 2014ApJ...781...87A)" (2 Observations and Data Reduction) [from (cite: 2014ApJ...781...87A)]
- Radiative transfer model adopted from literature and manually refined  
  > "We adopted the literature model and manually optimised the parameters, especially the flaring parameters, to fit the SED as well as the spatially resolved data" (4 Radiative transfer model) [from (cite: 2014ApJ...791L..36O)]
- Gap-less initial density field for hydrodynamics  
  > "The choice for the gap-less density field was taken from (cite: 2017A&A...600A..72F)." (5.1 Disc, star, and planets setup) [from (cite: 2017A&A...600A..72F)]

### Not stated but needed to reproduce (our reading)

- ALMA project code, calibration and imaging details of the band 7 data
- Source of the ALMA image used
- Quantitative goodness-of-fit for the RT model
- Hydrodynamic run duration and planet setup details

## Analysis recipe

1. **Reduce ZIMPOL data to Q_phi/U_phi**: Standard preprocessing, remap to square pixels, double ratio Stokes Q,U, azimuthal transformation  
  > "the Stokes parameters $Q$ and $U$, representing linearly polarised intensities, are calculated using the double ratio method" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit offset of ring**: Grid search minimising rms of an inclined ring fit to radial maximum positions  
  > "we run a grid search with the aim to minimise the rms of the fit" (3 Results and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer model**: Manual optimisation of Mol3D model to SED, ZIMPOL and ALMA  
  > "we apply the 3D radiative transfer code *Mol3D*" (4 Radiative transfer model)
   - software: Mol3D
   - fitting: _not stated_
   - validation: _not stated_
4. **Hydrodynamics and scattered-light post-processing**: FARGO-ADSG simulation, then RADMC-3D at 0.7 um  
  > "we run RADMC-3D simulations at a wavelength of $0.7\,\mu$m" (5.2 Post-processing of the hydrodynamic simulation)
   - software: FARGO-ADSG, RADMC-3D
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Mol3D** : 3D radiative transfer model  
  > "we apply the 3D radiative transfer code *Mol3D*" (4 Radiative transfer model)
- **FARGO-ADSG** : hydrodynamic simulations  
  > "public two-dimensional hydrodynamic code FARGO-ADSG" (5 Hydrodynamic simulations)
- **RADMC-3D** : scattered light images from hydro output  
  > "we run RADMC-3D" (5.2 Post-processing of the hydrodynamic simulation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Bright ring peak position | 0.173 | not stated | arcsec | 1 | increases until its peak around $0.173\ensuremath{''}$ ($\sim20\,$au) |
| Inner ring offset from star | ~7.5 mas at P.A. 315 deg | not stated | mas | 2 | at a radial distance of $\sim7.5\,$mas |

## Qualitative findings

- Elliptical gap, offset ring and outer disc, substructures in the bright ring  
  > "The gap which separates the bright inner ring from the outer disc is of elliptical shape" (Conclusion)

## Claim tuples

- H: Planets explain the ring substructures and offsets | E: Hydrodynamic simulations with three planets | R: 10 MJ at 15 au and 1 MJ at 35 and 45 au reproduce ring, gap and offset | F: Ongoing planet-disc interaction | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: MRI dead-zone gap disfavoured because gaps formed by MRI follow the disc symmetry  
  > "gaps formed by MRI do typically follow the symmetry of the disc" (6.2 Gaps)
- How they decided it was enough: _not stated_
- Limitation (authors): Data not flux calibrated  
  > "The data are not flux calibrated" (3 Results and Analysis)
- Caveat (inferred, ours): Manual model fit with no uncertainties
- Caveat (inferred, ours): Hydro model generic, not fitted
- Caveat (inferred, ours): ALMA data not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data details
- Missing: model fit quality
- Data volume (inferred): small for ZIMPOL; ALMA not needed in detail
- Score (inferred): 2/5, ALMA is a minor comparison and the method is manual.
- Rediscovery candidate: no, ALMA role is minor and details are missing.

## Links

- Companion: (cite: 2017A&A...600A..72F) (ALMA observations and model of HD 169142)

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00799.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 20,
  "rate": 0.299
 },
 "evidence_ok": true
}
```
