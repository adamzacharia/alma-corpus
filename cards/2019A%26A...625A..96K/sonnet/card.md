# Using ALMA to resolve the nature of the early star-forming large-scale structure PLCK G073.4-57.5

`2019A&A...625A..96K` | Astronomy and Astrophysics 2019 | first author: Kneissl, Rüdiger | arXiv: 1804.06581 | DOI: 10.1051/0004-6361/201833252

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Which individual dusty star-forming galaxies cause the Planck/Herschel submm peak G073.4-57.5, and are they a proto-cluster (redshifts, SFRs, masses, gas content)?  
  > "we need to resolve and characterise the individual galaxies giving rise to the emission seen by Planck and Herschel, and to find out whether they constitute the progenitors of present-day, massive galaxy clusters." (abstract)
- Target **PLCK G073.4-57.5**: coordinates _not stated_; z/distance photometric redshifts z~1.5 and z~2.4 groups; CO z=1.54  
  > "We targeted the eight sources found in the SPIRE field that were consistent with a red colour, within the uncertainties, as defined above." (3. ALMA observation of G073.4 − 57.5); distance from EAZY/SEDeblend photo-z; CO(5-4) redshifts from ALMA and IRAM EMIR  
  > "We targeted the eight sources found in the SPIRE field that were consistent with a red colour, within the uncertainties, as defined above." (3. ALMA observation of G073.4 − 57.5)

## Data provenance

- ALMA projects: 2013.1.01173.S
- bands: Band 6 (1.3 mm), around 233 GHz  
  > "A standard Band 6 continuum setup around 233 GHz (1.3 mm) was used" (3. ALMA observation of G073.4 − 57.5)
- frequencies and spectral setup: four 1.78-GHz spectral windows, central frequencies 224, 226, 240, 242 GHz  
  > "with four 1.78-GHz spectral windows divided into the two receiver sidebands, separated by 16 GHz (i.e. central frequencies of 224, 226, 240, and 242 GHz)" (3. ALMA observation of G073.4 − 57.5)
- continuum bandwidth: _not stated_
- arrays: 34 antennas  
  > "34 antennas were available in the array configuration during the time of the observation" (3. ALMA observation of G073.4 − 57.5)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.56'' x 0.44'' (FWHM), PA -82.7 deg  
  > "the resulting synthesised beam achieved an angular resolution of 0.56′′ × 0.44′′ (FWHM) with a position angle of −82.7◦" (3. ALMA observation of G073.4 − 57.5)
- max recoverable scale: _not stated_
- sensitivity: ~0.06 mJy/beam central in all eight fields  
  > "The central sensitivity was approximately 0.06 mJy beam−1 in all eight fields" (3. ALMA observation of G073.4 − 57.5)
- time on source: 0.4 hours  
  > "We received 0.4 hours of on-source observing time on G073.4−57.5 with ALMA in Cycle 2" (3. ALMA observation of G073.4 − 57.5)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 5-4 (serendipitous) (not stated)
- Other facility **Herschel-SPIRE**: 250/350/500 um fluxes  
  > "G073.4−57.5 was observed with Herschel-SPIRE at 250, 350, and 500 µm" (4.2)
- Other facility **JCMT SCUBA-2**: 850 um map  
  > "G073.4−57.5 was observed at 850 µm" (4.3)
- Other facility **Spitzer-IRAC**: 3.6 and 4.5 um photometry  
  > "G073.4−57.5 was observed with Spitzer-IRAC in GO11 (PID 80238, PI H. Dole)" (4.4)
- Other facility **CFHT-WIRCam**: J and Ks photometry  
  > "G073.4−57.5 was observed by CFHT-WIRCam at 1.3 µm (J band) and 2.1 µm (Ks band)" (4.5)
- Other facility **IRAM 30m/EMIR**: CO(2-1) detection of ID 3  
  > "We used the 3-mm band (E090) to search for CO transitions." (6.2)
- External data: CO data for cluster and proto-cluster galaxies  
  > "we collected CO data from the literature for galaxies in clusters (62 galaxies in 11 clusters" (6.3) [from Wang et al. 2018; Rudnick et al. 2017; Stach et al. 2017 and others]
- External data: SCUBA-2 sources  
  > "Table 3 lists the sources identified in MacKenzie et al. (2017), as well as their peak flux densities." (4.3) [from MacKenzie et al. (2017)]

## Processing

### Calibration

- pipeline or manual: observatory standard calibration  
  > "The observatory standard calibration was used." (3. ALMA observation of G073.4 − 57.5)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (additional flux calibrator)  
  > "Ceres was observed as an additional flux calibrator." (3. ALMA observation of G073.4 − 57.5)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: standard CASA tasks incl. deconvolution; ImageFitter for flux  
  > "The data were reduced with standard CASA tasks (McMullin et al. 2007), including deconvolution" (3. ALMA observation of G073.4 − 57.5)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: S/N>5 mask on primary-beam-uncorrected maps, 2 sigma CLEAN threshold  
  > "A S/N > 5 mask was applied to the primary beam-uncorrected maps with a 2 σ CLEAN threshold" (3. ALMA observation of G073.4 − 57.5)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.56'' x 0.44''  
  > "The FWHM of the synthesised beam (0.56′′ × 0.44′′)" (Figure 10 caption)
- final rms: _not stated_

### Inherited from earlier work

- SEDeblend method  
  > "For more details on SEDeblend we refer to MacKenzie et al. (2017)." (5.2) [from MacKenzie et al. 2017]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean weighting/robust, cell and image size, deconvolver
- continuum-subtraction and line-free channels for cubes
- calibrator flux scale and uncertainty
- image-plane fit settings in ImageFitter
- EAZY and cmcirsed run configuration

## Analysis recipe

1. **Image and extract sources**: CLEAN continuum images, S/N>4.5 detection, ImageFitter for flux and size  
  > "The flux-density results were derived from applying ImageFitter to the CLEANed maps and integrating over each source." (3.)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Photometric redshifts and deblended fluxes**: EAZY photo-z then SEDeblend MCMC to deblend SPIRE/SCUBA-2, then re-run EAZY  
  > "we use a combination of a recently developed algorithm called SEDeblend (MacKenzie et al. 2017)" (5.2)
   - software: EAZY, SEDeblend
   - parameter: beta=2.0 fixed; Td uniform 10-100 K; 120,000 iterations, 20,000 burn-in  
  > "The chain was run for 120,000 iterations and the first 20,000 iterations were removed as the ‘burn-in’ sequence." (5.2)
   - fitting: MCMC with Gibbs sampling, Gaussian likelihood  
  > "a Markov chain Monte Carlo (MCMC) algorithm with Gibbs sampling and adaptive step-sizing was used to maximise a Gaussian likelihood function" (5.2)
   - validation: predicted SCUBA-2 total 58 mJy vs stack 56±11 mJy  
  > "best-fit SEDs give a total SCUBA2 flux of 58 mJy, in good agreement with the stacking result of (56±11) mJy" (5.2)
3. **FIR parameters and stellar masses**: single-temperature modified blackbody fits for LIR, Td, Md, SFR; Hyper-z for stellar mass  
  > "Fits were performed using the cmcirsed package (Casey 2012)" (5.3)
   - software: cmcirsed, Hyper-z
   - assumption: beta=2.0; SFR=9.5e-11 LIR (Kennicutt, Chabrier IMF); Bruzual & Charlot models  
  > "SFR[M⊙ yr−1] = 9.5 × 10−11 LIR [L⊙ ]" (5.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **CO line fits and gas masses**: Gaussian line fits to ALMA and EMIR spectra; L'CO; gas mass with alpha_CO and r54/10  
  > "we derive gas masses of (4.7 ± 0.8) α CO × 10 10 M ⊙ (ID 3)" (6.3)
   - software: CLASS/GILDAS
   - assumption: r54/10=0.32±0.05; alpha_CO=4.36 or 0.8  
  > "r54/10 = 0.32 ± 0.05 (the median brightness temperature ratio derived for SMGs by Bothwell et al. 2013)" (6.3)
   - fitting: _not stated_
   - validation: EMIR CO(2-1) 4.7 sigma detection near expected frequency  
  > "We note a significant (4.7 σ) detection very close (90 km s−1 separation) to the expected frequency of 90.674 GHz" (6.2)

## Software

- **CASA** : data reduction and imaging  
  > "The data were reduced with standard CASA tasks" (3.)
- **SExtractor** : IRAC and WIRCam source extraction  
  > "Source extraction in the IRAC mosaics was performed using SExtractor" (4.4)
- **EAZY** : photometric redshifts  
  > "the EAZY code (Brammer et al. 2008), to estimate source photometric redshifts" (5.2)
- **SEDeblend** : deblending SPIRE/SCUBA-2  
  > "SEDeblend reconstructs the Herschel-SPIRE 250-µm, 350-µm, and 500-µm images" (5.2)
- **cmcirsed** : modified blackbody FIR fits  
  > "Fits were performed using the cmcirsed package (Casey 2012)" (5.3)
- **Hyper-z** : stellar mass SED fits  
  > "using the Hyper-z code (Bolzonella et al. 2000)" (5.3)
- **GILDAS/CLASS** : IRAM EMIR data reduction  
  > "Data reduction was performed with the help of the CLASS package in GILDAS" (6.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| number of ALMA galaxies | 18 | not stated | sources | 1 | The final sample, containing 18 ALMA sources with flux densities > 0.3 mJy and S/N > 4.5 |
| source surface density | 1.6e4 | not stated | deg^-2 | 1 | the surface density is 8 / (0.75 × 6.6 × 10−4 deg2) = 1.6 × 104 deg−2 |
| SCUBA-2 stack | 56 | 11 | mJy | 0 | obtaining a significant signal of (56±11) mJy |
| total SFR z~1.5 structure | 840 | +120/-100 | Msun/yr | 3 | The total SFRs of these two structures are 840 |
| CO(5-4) redshift of ID 3 (joint fit) | 1.54229 | 0.00009 | dimensionless | 4 | 3 ALMA joint 6.4 ± 0.3 416 ± 28 1.54229 ± 0.00009 |
| mean dust temperature | 27 | 5 | K | 3 | ⟨ Td ⟩ = (27 ± 5) K |

## Qualitative findings

- Two line-of-sight structures at z~1.5 and z~2.4; most galaxies on the main sequence  
  > "the nature of G073.4−57.5 seems to be at least two line-of-sight structures at z ≃ 1.5 and z ≃ 2.4" (7. Discussion)

## Claim tuples

- H: Does the Planck peak consist of many resolved mm galaxies? | E: ALMA 1.3 mm pointings on 8 SPIRE sources | R: 18 galaxies, 8-30x average density | F: overdense region of moderately bright galaxies | **supported**
- H: Are there redshift groups? | E: photo-z with EAZY/SEDeblend | R: concentrations at z~1.5 and 2.4 | F: two superposed structures | **partially**
- H: Do serendipitous lines match photo-z? | E: line fits ALMA plus EMIR | R: CO(5-4) at z=1.54 for IDs 3 and 8 | F: consistent with z~1.5 structure | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Other CO transitions (J=4-3, 6-5, 7-6) and CI(2-1) considered for ID 3, less consistent with photo-z  
  > "On the other hand, CO(6–5) appears possible, though not favoured by the photometric redshifts within their errors." (6.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Photo-z uncertain; stellar-mass uncertainties likely underestimated  
  > "The reported uncertainties are likely to underestimated because they do not take into account the redshift uncertainty" (5.3)
- Caveat (inferred, ours): Only 0.4 h of ALMA data, 18 sources with photo-z dominated results
- Caveat (inferred, ours): Group membership from photo-z only
- Caveat (inferred, ours): Literature gas comparison samples heterogeneous

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Photometry tables for IRAC/WIRCam only in appendix
- Missing: EAZY run settings
- Data volume (inferred): ~10-50 GB (ALMA Cycle 2, 8 short pointings, plus public ancillary data)
- Score (inferred): 3/5, ALMA project code given and standard analysis, but imaging parameters and many multi-wavelength inputs are not fully specified.
- Rediscovery candidate: no, Imaging recipe incomplete and key results depend on non-ALMA data and complex SED fitting.

## Links

- Method: MacKenzie et al. (2017) (SEDeblend method)
- Companion: Planck Collab. XXXVII 2015 (Planck/Herschel sample)
- Related: Planck PHz catalogue
- Related: Herschel-SPIRE follow-up of Planck sources

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 42,
  "rate": 0.553
 },
 "evidence_ok": true
}
```
