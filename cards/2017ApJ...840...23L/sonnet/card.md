# A Multi-ringed, Modestly Inclined Protoplanetary Disk around AA Tau

`2017ApJ...840...23L` | The Astrophysical Journal 2017 | first author: Loomis, Ryan A. | arXiv: 1704.02006 | DOI: 10.3847/1538-4357/aa6c63

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the dust and gas structure and inclination of the AA Tau disk, and how does it relate to the system's photometric variability?  
  > "we present ALMA observations of the disk around AA Tau that identify it for the first time as multi-ringed" (1 Introduction)
- Target **AA Tau**: coordinates _not stated_; z/distance 145 pc  
  > "assuming a distance of 145 pc to AA Tau" (1 Introduction); distance from assumed (cite: Bouvier_2013; Rodriguez_2015)  
  > "assuming a distance of 145 pc to AA Tau" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.01070.S, 2015.1.01017.S
- bands: Band 7 (0.87 mm), Band 6 (1.3 mm)  
  > "AA Tau was observed on 2015 July 25 in Band 7 and on 2015 Sept. 29 in Band 6" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2.7 GHz (Band 7); 4.47 GHz (Band 6)  
  > "The total continuum bandwidth was 4.47 GHz." (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 7: 12-1455 m; Band 6: 42-2065 m; 13CO Band 7: 12-1028 m  
  > "Band 6 observations included 30 antennas with projected baseline lengths between 42 and 2065 m (36-1850 k$\lambda$)." (2 Observations)
- angular resolution: 0.18''x0.12'' (robust 0); 0.15''x0.11'' (super-uniform)  
  > "yielding a synthesized beam of 0.18$''$$\times$0.12$''$ (26$\times$17 AU at 145 pc)" (3.1 Continuum Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 7 56 min; Band 6 61 min; 13CO 45 min  
  > "The total on-source integration time was 61 minutes." (2 Observations)
- observing dates: 2015 Jul 25 (B7), 2015 Sep 29 (B6), 2016 Jul 21 (13CO)  
  > "were taken on 2016 July 21 as part of the ALMA cycle 3 project 2015.1.01017.S" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCO+ 3-2 (not stated)
- Line: 13CO 3-2 (330.6 GHz)
- External data: Inner disk PA 93 deg from observed jet  
  > "we fix the PA to 93$^{\degree}$, constrained by the PA of the observed jet (cite: Cox_2013)" (3.2 Continuum modeling) [from (cite: Cox_2013)]
- External data: Inner disk inclination 75 deg from photopolarimetry modeling  
  > "the inclination to 75$^{\degree}$, constrained by photopolarimetry modeling (cite: OSullivan_2005)" (3.2 Continuum modeling) [from (cite: OSullivan_2005)]
- External data: Scattered-light inclination 71±1 deg  
  > "71$\pm$1$\degree$ previously fit to infrared scattered light emission (cite: Cox_2013)" (3.1 Continuum Observations) [from (cite: Cox_2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3 (self-calibration)  
  > "two rounds of phase-only self-calibration in CASA version 4.3." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: Delivered calibrated data used, with flux correction  
  > "While analyzing the delivered calibrated data, we discovered that the two flux calibrations are in conflict" (2 Observations)
- flux calibrator: J0510+1800 used for both bands after correcting Band 6 flux scaling (2.1 Jy derived vs 1.7 Jy catalog)  
  > "We correct for this conflict by using J0510+1800 as the flux calibrator for both the Band 6 and Band 7 observations" (2 Observations)
- flux scale uncertainty: Band 6 absolute flux substantially uncertain; precludes spectral index analysis  
  > "also introduces a substantial uncertainty in the absolute continuum flux of the Band 6 data." (2 Observations)
- self calibration: two rounds of phase-only self-calibration  
  > "we used the disk continuum emission to perform two rounds of phase-only self-calibration in CASA version 4.3." (2 Observations)

### Imaging

- task: CLEAN, multi-frequency synthesis, reference frequency 271.6 GHz; Band 6 and 7 concatenated  
  > "imaged using multi-frequency synthesis `CLEAN` with a reference frequency of 271.6 GHz" (3.1 Continuum Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0; also super-uniform weighting  
  > "with a robust parameter of 0" (3.1 Continuum Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: custom CLEAN mask per channel; clean to 3 sigma; natural weighting, 0.4 km/s channels  
  > "A custom `CLEAN` mask created for each channel to match the emission, and `CLEAN`ing was terminated when residuals reached 3$\sigma$." (3.3 Spectral line emission)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub for HCO+  
  > "continuum subtracted using `uvcontsub`" (3.3 Spectral line emission)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 44 uJy/beam (robust 0); 60 uJy/beam (super-uniform)  
  > "an rms noise of 44 $\mu$Jy bm$^{-1}$" (3.1 Continuum Observations)

### Not stated but needed to reproduce (our reading)

- Cell size and image size
- Line-free channels for uvcontsub
- Self-calibration solution intervals and reference antenna
- MCMC walkers, steps, burn-in and priors
- Exact Band 6 flux rescaling factor applied
- Rest frequencies and weighting for 13CO imaging
- Details of the dust streamer model
- Parametric Gaussian ring functional form

## Analysis recipe

1. **Image continuum**: Concatenate Band 6 and 7, MFS CLEAN, robust 0 and super-uniform  
  > "The Band 6 and 7 continuum observations were concatenated and imaged using multi-frequency synthesis `CLEAN`" (3.1 Continuum Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parametric ring model to visibilities**: Three Gaussian rings plus Gaussian inner disk, 29 parameters, fit to visibilities  
  > "This 29 parameter model was fit to the observed visibilities using the MCMC routine `emcee` (cite: Mackey_2013) and the visibility sampling routine `vis_sample`" (3.2 Continuum modeling)
   - software: emcee, vis_sample
   - parameter: inner disk PA fixed 93 deg, inclination fixed 75 deg  
  > "we fix the PA to 93$^{\degree}$" (3.2 Continuum modeling)
   - assumption: distance 145 pc  
  > "assuming a distance of 145 pc to AA Tau" (1 Introduction)
   - fitting: emcee MCMC, reduced chi2 1.02  
  > "yielding a final best-fit model with a reduced $\chi^{2}$ value of 1.02." (3.2 Continuum modeling)
   - validation: Simulated observations with simobserve and residual imaging; tested separate bands, two point sources, eccentric ring  
  > "we find structured residuals with a peak of $\sim$12 $\sigma$ ($\sigma$ = 44 $\mu$Jy bm$^{-1}$)" (3.2 Continuum modeling)
3. **Line moment and radial profile analysis**: HCO+ and 13CO imaged identically; deprojected azimuthal radial profiles using continuum PA and inclination; moment-1 map and PV diagram versus Keplerian curves for 59 and 40 deg  
  > "The position angle and inclination of the dust continuum were used for deprojection." (3.3 Spectral line emission)
   - software: CASA
   - assumption: stellar mass 0.85 Msun  
  > "a stellar mass of 0.85 M$_{\odot}$ are overlaid" (3.3 Spectral line emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3: self-calibration, CLEAN imaging, uvcontsub, simobserve  
  > "two rounds of phase-only self-calibration in CASA version 4.3." (2 Observations)
- **emcee** : MCMC fitting of ring model  
  > "using the MCMC routine `emcee` (cite: Mackey_2013)" (3.2 Continuum modeling)
- **vis_sample** : sampling model visibilities  
  > "the visibility sampling routine `vis_sample`" (3.2 Continuum modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring 1 radius | 48.7 | 0.1 | AU | 2 | The retrieved ring radii are 48.7$\pm$0.1, 94.9$\pm$0.2, and 142.6$\pm$0.6 AU |
| Ring 2 radius | 94.9 | 0.2 | AU | 2 | The retrieved ring radii are 48.7$\pm$0.1, 94.9$\pm$0.2, and 142.6$\pm$0.6 AU |
| Ring 3 radius | 142.6 | 0.6 | AU | 2 | The retrieved ring radii are 48.7$\pm$0.1, 94.9$\pm$0.2, and 142.6$\pm$0.6 AU |
| Mean ring inclination | 59.1 | 0.3 | deg | 2 | we constrain the ring inclinations to an average of 59.1$\degree\pm$0.3$\degree$ |
| Ring FWHM widths | 22.6, 28.7, 26.4 | 0.2, 0.7, 1.5 | AU | 2 | FHWM (AU) & 5.4$\pm$1.1 & 22.6$\pm$0.2 & 28.7$\pm$0.7 & 26.4$\pm$1.5 |
| Ring Band 7 fluxes | 61.0, 34.4, 8.5 | 0.2, 0.4, 0.3 | mJy | 2 | Flux Band 7 (mJy) & 2.2$\pm$0.05 & 61.0$\pm$0.2 & 34.4$\pm$0.4 & 8.5$\pm$0.3 |
| Peak residual after model subtraction | ~12 | not stated | sigma | 2 | structured residuals with a peak of $\sim$12 $\sigma$ |

## Qualitative findings

- HCO+ is bright interior to the innermost ring while 13CO is flat; HCO+ moment-1 is twisted ~10 deg inside the ring  
  > "with the emission misaligned by $\sim$10$\degree$ with respect to the continuum orientation" (3.3 Spectral line emission)

## Claim tuples

- H: Is the AA Tau disk viewed edge-on? | E: Visibility modeling of Band 6+7 continuum | R: Ring inclination 59.1±0.3 deg | F: Outer disk is modestly inclined, misaligned with the inner disk | **supported**
- H: Is eccentricity or point sources responsible for the azimuthal asymmetry? | E: Fitted alternative models | R: Residuals improved by ~4 sigma and ~1 sigma but remained structured | F: Eccentricity alone cannot explain it | **supported**
- H: Do gap-crossing streams explain the bridge and the HCO+ kinematics? | E: HCO+ moment-1 and PV compared with Keplerian profiles | R: Inner emission better fit by 40 deg than 59 deg | F: Warp or radial flow; streamers suggested but not confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Eccentric inner ring and two embedded point sources tested and found insufficient  
  > "suggesting that the responsible feature is resolved and not point-like." (3.2 Continuum modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 6 flux uncertain, precluding spectral index analysis  
  > "it does preclude an analysis of the spectral index and thus the grain size distribution across the AA Tau disk" (2 Observations)
- Caveat (inferred, ours): Band 6 flux rescaling is ad hoc and affects ring flux ratios
- Caveat (inferred, ours): Streamer interpretation is speculative and untested
- Caveat (inferred, ours): Misalignment inferred from channel maps that are not shown
- Caveat (inferred, ours): Parametric model fixes inner disk geometry from literature

## Reproducibility

- Data public (paper): Project codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01070.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: vis_sample publicly available on GitHub  
  > "`vis_sample` is publicly available at" (footnote 1)
- Missing: Exact flux rescaling factor
- Missing: MCMC setup and priors
- Missing: Imaging cell and image sizes
- Missing: Model code for ring parameterization
- Data volume (inferred): ~50-100 GB raw across three execution blocks
- Score (inferred): 3/5, Data identified and methods broadly described, but key imaging and MCMC settings and flux correction details are missing.
- Rediscovery candidate: yes, Data are ALMA archive projects, the recipe is moderately complete, and results are numeric ring parameters.

## Links

- Method: (cite: Mackey_2013) (emcee)
- Method: (cite: Wyatt_1999) (pericenter glow term in eccentric ring model)
- Companion: (cite: Cox_2013) (scattered light inclination and jet PA comparison)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 38,
  "rate": 0.585
 },
 "evidence_ok": true
}
```
