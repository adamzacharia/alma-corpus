# The Effect of Binarity on Circumstellar Disk Evolution

`2019ApJ...878...45B` | The Astrophysical Journal 2019 | first author: Barenfeld, Scott A. | arXiv: 1906.04878 | DOI: 10.3847/1538-4357/ab1e50

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How does the presence of stellar companions affect disk evolution in 5-11 Myr old Upper Sco, compared with 1-2 Myr old Taurus?  
  > "In this paper, we consider how the influence of stellar companions has impacted the evolution of these disks to their current state." (Introduction)
- Target **Upper Scorpius disk sample (113 stars, G2-M5)**: coordinates _not stated_; z/distance ~145 pc (mean of sample, 145±11 pc)  
  > "Distances to the stars in the sample are taken from the catalog of (cite: BailerJones2018), inferred from *Gaia* parallaxes using a Bayesian distance prior." (2 Sample and Observations); distance from Bailer-Jones et al. 2018 (Gaia parallaxes)  
  > "Distances to the stars in the sample are taken from the catalog of (cite: BailerJones2018), inferred from *Gaia* parallaxes using a Bayesian distance prior." (2 Sample and Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA 880 μm continuum (Band 7) and 12CO J=3-2, taken from Barenfeld et al. 2016  
  > "Figure [6](#fig:ALMA_Images) shows ALMA 880 $\mu$m continuum images of the 26 systems with companions for which we have ALMA data (cite: Barenfeld2016)." (4.1 Properties of Upper Sco Systems with Disks and Companions)
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
- Line: CO J=3-2 (not stated)
- Other facility **Keck II NIRC2**: AO imaging and nonredundant aperture masking for companion search  
  > "We obtained AO imaging and aperture masking observations of the remaining 86 stars using the NIRC2 AO imager (instrument PI: Keith Matthews) on the 10 m Keck II telescope." (2 Sample and Observations)
- Other facility **Gaia DR2**: Distances, positions, proper motions, wide companions  
  > "we used the *Gaia* DR2 Catalog to identify any sources within 1$\ensuremath{'}$ of a target star in our Upper Sco disk sample." (3.4 Candidate Wide Companions with Gaia)
- External data: ALMA 0.88 mm flux densities and CO fluxes of Upper Sco disks  
  > "0.88 mm continuum flux density measured by (cite: Barenfeld2016)." (Table 1 notes) [from (cite: Barenfeld2016)]
- External data: Taurus 1.3 mm flux densities compilation  
  > "we used the compilation of 1.3 millimeter flux densities of infrared-identified Class II Taurus systems from (cite: Akeson2019)" (5.2 Millimeter Emission and Multiplicity) [from (cite: Akeson2019)]
- External data: Diskless Upper Sco comparison sample companions  
  > "Our comparison sample is composed of the 77 Upper Sco stars without such disks surveyed for stellar companions by (cite: Kraus2008)" (4.2) [from (cite: Kraus2008)]

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

- ALMA data reduction and flux measurements  
  > "ALMA 880 $\mu$m continuum images of the 26 systems with companions for which we have ALMA data (cite: Barenfeld2016)." (4.1) [from (cite: Barenfeld2016)]
- Aperture masking reduction procedure  
  > "Reduction of the aperture masking observations followed the procedure described in Kraus et al. (2008" (2.2) [from Kraus et al. 2008]
- Taurus flux scaling to 0.88 mm with factor 2.55  
  > "have been scaled to 0.88 mm using the scaling factor of 2.55 assumed for Taurus disks by (cite: Andrews2013)" (5.2) [from (cite: Andrews2013)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes, calibration and imaging details (in Barenfeld 2016/2017)
- Exact ALMA beam sizes and sensitivities
- Taurus sample membership list after cuts

## Analysis recipe

1. **Detect companions in AO images**: VIP detection routine with S/N>=5, PCA PSF subtraction, visual inspection  
  > "Using this technique, we found 170 potential sources with an S/N greater than or equal to five." (3.1 Imaging)
   - software: VIP, photutils
   - parameter: 13 principal components (no coronagraph), 7 (coronagraph)  
  > "We used 13 principal components and a library of 48 reference frames for images taken without the coronagraph." (3.1 Imaging)
   - fitting: _not stated_
   - validation: Fake companion injection for contrast limits  
  > "This routine injects fake companions with a range of separations and contrasts relative to the primary into the stacked, PSF-subtracted frames for each target." (3.1 Imaging)
2. **Select candidate companions**: Candidates are sources with K<15 and separation <2 arcsec, based on TRILEGAL field-star density  
  > "We therefore consider any sources brighter than $K=15$ and within 2$\ensuremath{''}$ of a target star likely to be a candidate bound companion." (3.3 Selection of Candidate Companions)
   - software: TRILEGAL
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare companion fractions and mm fluxes**: Fisher exact test; Kaplan-Meier with log-rank and Peto-Peto tests  
  > "These distributions were calculated using the Kaplan-Meier product-limit estimator to account for the sources without a millimeter detection." (5.2)
   - software: R
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **VIP** : AO image reduction, detection, PCA, contrast curves  
  > "The NIRC2 Preprocessing and Vortex Image Processing (VIP) packages" (2.1)
- **R** : Statistical tests  
  > "according to the $\chi^{2}$ test implemented with the *R Project for Statistical Computing*" (4.2)
- **photutils** : Photometry and astrometry  
  > "measured using the Python package *photutils*" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Companion fraction, disk hosts G0-M3 | 7 of 50 | not stated | systems | 3 | only seven out of 50 systems with disks include companions. |
| Companion fraction, diskless | 35 of 75 | not stated | systems | 3 | 35 out of 75 stars without disks have at least one companion. |
| Fisher p-value disks vs diskless | 2e-4 | not stated | dimensionless | 3 | is due to chance is $2\times10^{-4}$ |
| Close (<=40 au) companion fraction comparison, Taurus vs Upper Sco p-value | 0.83 | not stated | dimensionless | 3 | with a $p$-value of 0.83 |

## Qualitative findings


## Claim tuples


## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single epoch, so no common proper motion confirmation  
  > "With only a single epoch of observations, we cannot use common proper motion to rule out the chance alignment of a field star." (3.3)
- Caveat (inferred, ours): Marginal significance for primordial disks (p=0.04)
- Caveat (inferred, ours): Comparison sample used different observing conditions and spectral type coverage

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA reductions from Barenfeld 2016
- Missing: Taurus sample list
- Data volume (inferred): Small if using published flux tables; ALMA data already reduced in earlier papers
- Score (inferred): 3/5, The ALMA part is inherited from earlier papers, and the AO analysis is described but needs the Keck data.
- Rediscovery candidate: no, The main results come from Keck data and the ALMA role is minor.

## Links

- Method: (cite: Kraus2008) (Aperture masking and companion selection)
- Method: (cite: Barenfeld2016) (ALMA data reduction)
- Companion: (cite: Barenfeld2017) (Upper Sco dust disk sizes)
- Related: Upper Sco ALMA survey

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00526.S",
  "2013.1.00395.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 21,
  "rate": 0.323
 },
 "evidence_ok": true
}
```
