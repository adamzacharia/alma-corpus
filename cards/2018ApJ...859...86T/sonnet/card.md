# ALMA Images of the Host Cloud of the Intermediate-mass Black Hole Candidate CO-0.40-0.22*: No Evidence for Cloud-Black Hole Interaction, but Evidence for a Cloud-Cloud Collision

`2018ApJ...859...86T` | The Astrophysical Journal 2018 | first author: Tanaka, Kunihiko | arXiv: 1804.03661 | DOI: 10.3847/1538-4357/aabd77

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, star_formation
- Question: Does re-analysis of the archival ALMA data of CO-0.40-0.22 support an IMBH gravitational-kick origin, or a cloud-cloud collision?  
  > "In this present paper, we re-examine the gravitational kick scenario by analyzing the same ALMA data used in Oka et al. (2017)." (1. INTRODUCTION)
- Target **CO-0.40-0.22 (CO-0.4) and continuum source MM1/CO-0.4***: coordinates _not stated_; z/distance foreground cloud G359.62-0.24 at 3.1 kpc (parallax); CO-0.4 distance not stated  
  > "for which the distance has been measured to be 3 . 1 [+2] − 0 [.] . [2] 9 [kpc] [through] [parallax]" (4.1.3. Continuum Source MM1/CO−0.4*); distance from Iwata et al. 2017 (water maser parallax), foreground cloud only  
  > "for which the distance has been measured to be 3 . 1 [+2] − 0 [.] . [2] 9 [kpc] [through] [parallax]" (4.1.3. Continuum Source MM1/CO−0.4*)

## Data provenance

- ALMA projects: 2012.1.00940.S
- bands: _not stated_
- frequencies and spectral setup: three windows at 230, 250, 265 GHz; 230/265 ~900 MHz bandwidth, ~200 kHz channels; 250 GHz ~2 GHz bandwidth, 15 MHz channels  
  > "The spectral data were taken in three frequency windows centered at 230 GHz, 250 GHz, and 265 GHz." (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA); "The 250-GHz data was taken with a broad band mode with a ∼ 2 GHz bandwidth and a 15 MHz channel width, and lacks 7-m array data." (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- continuum bandwidth: _not stated_
- arrays: 12-m and 7-m arrays  
  > "observed with both the 12-m and 7-m arrays" (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: line beams 1.75x1.02 (230), 1.35x0.60 (265), 1.42x0.59 arcsec (250 GHz)  
  > "265 line 12+7 1 _._ 35 _×_ 0 _._ 60 69.8" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: July 2013 to January 2015  
  > "observed with different antenna-array configurations from July 2013 to January 2015" (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: HCN J=3-2 (265.886 GHz)
- Other facility **ASTE 10-m**: single-dish 13CO J=3-2 and HCN J=4-3 maps (Tanaka et al. 2014)  
  > "obtained with the ASTE 10-m telescope (Tanaka et al. 2014)" (Figure 12 caption)
- External data: 34.25 GHz non-detection 3-sigma upper limit 0.285 mJy  
  > "3- _σ_ upper limit of 0.285 mJy (Ravi et al. 2017)" (4.1.3. Continuum Source MM1/CO−0.4*) [from Ravi et al. 2017]
- External data: Collisional rate coefficients and partition functions  
  > "The rate coefficients and partition functions are taken from the Leiden Atomic and Molecular Database" (3.3. Heating Sources Inside or Near the −80-km s−1 Filament) [from LAMDA (Schöier et al. 2005), CDMS (Muller et al. 2001), Motoki et al. (2014)]

## Processing

### Calibration

- pipeline or manual: ALMA observatory reduction script in CASA  
  > "calibration of the visibility data were performed using the reduction script provided by the ALMA observatory" (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: self-cal cycles using moment-0 CO and HCN images, per dataset  
  > "We refined the image quality by performing self-calibration cycles using the moment-0 CO and HCN images independently for each dataset." (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)

### Imaging

- task: TCLEAN mosaic  
  > "We performed mosaic imaging using the `TCLEAN` task." (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- deconvolver: _not stated_
- weighting robust: Briggs robust=1 for 230 GHz line; natural for 250 and 265 GHz line  
  > "Briggs weighting with a robustness parameter of 1 was applied for the 230-GHz band line data, and the natural weighting was applied for the 250- and 265-GHz line data." (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- uv taper: 1 arcsec taper for continuum  
  > "robustness of 1 and a _uv_ -taper at the 1 _[′′]_ angular scale were applied" (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB for 230/265 GHz; not possible for 250 GHz  
  > "Continuum subtraction was not possible for the 250-GHz band data due to the extreme crowdedness of the emission lines." (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12+7 m combined for 230 and 265 GHz  
  > "230 continuum 12+7 2 _._ 03 _×_ 1 _._ 24 74.6" (Table 3)
- smoothing: MM1 images smoothed to 2 arcsec FWHM; uv range 20-1500 kλ  
  > "We further smoothed the images so that they both have an effective beam size of 2 _[′′]_ FWHM" (4.1.3. Continuum Source MM1/CO−0.4*)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Same ALMA dataset as Oka et al. 2017  
  > "by analyzing the same ALMA data used in Oka et al. (2017)" (1. INTRODUCTION) [from Oka et al. (2017)]
- Dendrogram method  
  > "by means of the dendrogram method (Rosolowsky et al. 2008)" (3.2.1. Three Velocity Components) [from Rosolowsky et al. 2008]

### Not stated but needed to reproduce (our reading)

- CASA version
- Self-calibration solution intervals and mask choices
- Line-free channels for UVCONTSUB
- Cell size, image size, clean thresholds and masks
- Dendrogram parameters beyond 3 sigma digitization (min_value, min_delta, min_npix)
- Non-LTE code and likelihood details, and the column density prior
- Regions and apertures used for the five-position spectra
- How topocentric-to-LSR frequency correction was done in concatenation

## Analysis recipe

1. **Reduce and image archival data**: ALMA script calibration, UVCONTSUB, self-cal, tclean mosaics; 08JUL2013 excluded  
  > "We excluded the `08JUL2013` data from the final imaging" (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
   - software: CASA
   - fitting: _not stated_
   - validation: Reproduced the Oka et al. broad emission by merging in topocentric frame  
  > "We confirmed that a PV diagram almost identical to that presented in Oka et al. (2017) is obtained from this incorrectly merged data" (4.1.2. The 110-km s−1-Wide Emission)
2. **Extract cloud structure and velocity components**: Dendrogram of HCN cube smoothed to 2.5 km/s, in 3sigma units (sigma=13 mJy); six main branches; moment maps and PV diagrams  
  > "smoothed into 2 _._ 5 km s _[−]_ [1] velocity bins and digitized in units of 3 _σ_ intensities ( _σ_ = 13 mJy)" (Appendix)
   - software: astrodendro-like dendrogram (Rosolowsky et al. 2008)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure MM1 spectral index**: Continuum images from uv 20-1500 kλ, smoothed to 2 arcsec, flux in 1 arcsec radius circle  
  > "measured for the 1 _[′′]_ -radius circle (the black solid line)" (Figure 10 caption)
   - software: CASA
   - fitting: _not stated_
   - validation: Extended emission gives similar alpha = 2.5 +/- 0.4  
  > "gives a similar value of _α_ = 2 _._ 5 _±_ 0 _._ 4" (4.1.3. Continuum Source MM1/CO−0.4*)
4. **Derive physical conditions of filament**: LTE population diagrams and non-LTE Bayesian analysis of methanol lines with flat priors on Tkin and nH2  
  > "assuming a prior function that is flat for 1 < T kin /K < 1000 and 1 < n H 2 /cm −3 < 10 7 and zero otherwise" (3.3. Heating Sources Inside or Near the −80-km s−1 Filament)
   - assumption: Dust temperature 20 K, emissivity index 1.5 for H2 column from 265 GHz dust  
  > "assuming a dust temperature of 20 K and dustemissivity index of 1.5" (3.3. Heating Sources Inside or Near the −80-km s−1 Filament)
   - fitting: Bayesian grid-like credible intervals, flat prior  
  > "Figure 9(b) shows the simultaneous credible intervals for T kin and n H 2, calculated from a Bayesian analysis assuming a prior function that is flat for 1 < T kin / K < 1000" (3.3. Heating Sources Inside or Near the −80-km s−1 Filament)
   - validation: Consistent with earlier HCN non-LTE analysis  
  > "This result is also consistent with that from a non-LTE analysis using HCN lines (Tanaka et al. 2014)." (3.3. Heating Sources Inside or Near the −80-km s−1 Filament)

## Software

- **CASA** : calibration, tclean, uvcontsub, concat  
  > "using the Common Astronomy Software Applications (CASA) package developed by the National Radio Astronomy Observatory (NRAO)" (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MM1 flux density at 230 GHz | 8.6 | 0.2 | mJy | 3 | The corrected flux densities are 8 _._ 6 _±_ 0 _._ 2 mJy and 13 _._ 2 _±_ 0 _._ 4 mJy |
| MM1 flux density at 265 GHz | 13.2 | 0.4 | mJy | 3 | The corrected flux densities are 8 _._ 6 _±_ 0 _._ 2 mJy and 13 _._ 2 _±_ 0 _._ 4 mJy |
| MM1 spectral index alpha | 3.0 | 0.3 (0.4 in summary) | dimensionless | 3 | which gives a spectral index of _α_ = 3 _._ 0 _±_ 0 _._ 3 |
| CH3OH rotational temperature (warm) | ~70 | not stated | K | 4 | warm gas with a CH 3 OH rotational temperature _T_ rot _∼_ 70 K |
| CH2NH rotational temperature (cold) | ~24 | not stated | K | 4 | cold gas with a CH 2 NH rotational temperature _T_ rot _∼_ 24 K |
| Post-shock nH2 | >~1e6 | lower limit | cm-3 | 4 | this analysis indicates that _n_ H 2 ≳ 10 [6] cm _[−]_ [3], unless an unrealistically high _T_ kin of _>_ 10 [3] K is assumed |
| Fractional abundances CH2NH and CH3OH | 2e-8 and 1e-7 | not stated | dimensionless | 4 | We calculated the fractional abundances of CH 2 NH and CH 3 OH to be 2 _×_ 10 _[−]_ [8] and 1 _×_ 10 _[−]_ [7], respectively |

## Qualitative findings

- Cloud consists of -40, -60 (broad) and -80 km/s components bridged in PPV, with V-shaped PV across the -80 km/s filament  
  > "Along both cuts, the PV diagrams show characteristic V-shapes" (3.2.3. V-Shaped Velocity Gradient Across the −80-km s−1 Filament)

## Claim tuples

- H: Is the 110 km/s-wide clump real evidence of an IMBH kick? | E: Re-reduce data, excluding 08JUL2013 and respecting topocentric frame; compare with incorrect merge | R: Extremely broad emission only reproduced in incorrectly merged data; real width 40 km/s | F: The broad feature is an artifact | **supported**
- H: Is MM1 self-absorbed synchrotron from an IMBH (alpha~1)? | E: Beam-matched flux measurement at 230 and 265 GHz | R: alpha = 3.0 +/- 0.3 | F: Consistent with thermal dust, likely foreground | **supported**
- H: Is CO-0.4 a cloud-cloud collision? | E: Dendrogram, moment maps, PV diagrams, comparison with 13CO | R: Two narrow components bridged by broad emission; V-shaped PV | F: Consistent with a CCC between dissimilar clouds | **supported**
- H: Does the shock compress gas to star-forming densities? | E: Non-LTE methanol analysis | R: nH2 >~1e6 cm-3 | F: CCC can compress gas quickly; no SF evidence found | **partially**

## Reasoning

- Why this data: Re-examine the same ALMA data used by Oka et al. (2017)  
  > "we re-examine the gravitational kick scenario by analyzing the same ALMA data used in Oka et al. (2017)" (1. INTRODUCTION)
- Why this method: _not stated_
- Alternative: Ravi et al. 2017 collision with infrared dark cloud G359.62-0.24 not supported  
  > "PV patterns indicative of physical interactions between G359.62 − 0 . 24 and CO–0.4 are not identified" (4.3. Other Hypotheses)
- How they decided it was enough: _not stated_
- Limitation (authors): Degeneracy between Tkin and nH2 not resolved; MM1 flux contaminated by background  
  > "Although the degeneracy between _T_ kin and _n_ H 2 is not resolved" (3.3. Heating Sources Inside or Near the −80-km s−1 Filament)
- Caveat (inferred, ours): Nature of MM1 is not firmly determined
- Caveat (inferred, ours): CCC interpretation is qualitative, no kinematic model fit
- Caveat (inferred, ours): Non-LTE results are degenerate and use only a flat prior
- Caveat (inferred, ours): Exclusion of 08JUL2013 data relies on judgement

## Reproducibility

- Data public (paper): Obtained from the ALMA science archive  
  > "which we obtained from the ALMA science archive (id: 2012.1.00940.S)" (2. RE-ANALYSIS OF THE ALMA ARCHIVAL DATA)
- Products in archive: _not stated_
- Missing: CASA version and exact scripts
- Missing: Self-cal and masking details
- Missing: Dendrogram and non-LTE code parameters
- Data volume (inferred): ~100-300 GB raw across seven executions
- Score (inferred): 3/5, Public data and key settings given, but versions, self-cal, masks and fitting details missing.
- Rediscovery candidate: yes, Public data, numeric results such as the spectral index and fluxes can be redone, though some details are missing.

## Links

- Method: Rosolowsky et al. 2008 (dendrogram method)
- Companion: Oka et al. (2017) (original analysis of same ALMA data)
- Companion: Ravi et al. (2017) (34.25 GHz non-detection of CO-0.4*)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 35,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
