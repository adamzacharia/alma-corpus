# The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Bright-end of the Sub-millimeter Number Counts

`2015ApJ...807..128S` | The Astrophysical Journal 2015 | first author: Simpson, J. M. | arXiv: 1505.05152 | DOI: 10.1088/0004-637X/807/2/128

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How often are bright SCUBA-2 850 um sources blends of multiple SMGs, and what are the intrinsic bright-end number counts and the origin of the multiplicity?  
  > "We use the data to measure the multiplicity in the single-dish population, probe the bright–end of the number counts and investigate the number density of secondary SMGs." (1 Introduction)
- Target **30 SCUBA-2 S2CLS sources in the UKIDSS UDS field (e.g. UDS156, UDS286)**: coordinates Per-source RA/Dec in Table 1 (e.g. UDS156.0 02:18:24.14 -05:22:55.3)  
  > "From these earlier observations we selected 31 sources detected at $>$ 4 $\sigma$, and hence having observed 850–$\mu$m flux densities of $>$ 8mJy." (2.1 Sample Selection); z/distance not stated (no spectroscopic redshifts)  
  > "From these earlier observations we selected 31 sources detected at $>$ 4 $\sigma$, and hence having observed 850–$\mu$m flux densities of $>$ 8mJy." (2.1 Sample Selection); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00090.S
- bands: Band 7 (870 um)  
  > "We obtained ALMA 870 $\mu$m (Band 7) continuum imaging of all 30 targets from our sample on 2013 November 1" (2.2 Data Reduction)
- frequencies and spectral setup: single continuum setup, four basebands of 128 dual-polarization channels  
  > "We used a “single continuum” correlator setup with four basebands of 128 dual-polarization channels each." (2.2 Data Reduction)
- continuum bandwidth: 7.5 GHz centred at 344 GHz  
  > "All targets were observed using 7.5-GHz of bandwidth centered at 344 GHz (870 $\mu$m)" (2.2 Data Reduction)
- arrays: 26 12-m antennae  
  > "The observations were conducted using 26 12–m antennae with a range of baselines from 20 to 1250 m, and a median baseline of 200 m." (2.2 Data Reduction)
- configurations: _not stated_
- baselines: 20 to 1250 m, median 200 m  
  > "a range of baselines from 20 to 1250 m, and a median baseline of 200 m" (2.2 Data Reduction)
- angular resolution: 0.35'' x 0.25'' (robust 0.5); tapered 0.8'' x 0.65''  
  > "The array configuration yields a synthesized beam of 0.35$''$ $\times$ 0.25$''$ using Briggs weighting (robust parameter = 0.5)" (2.2 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 1-sigma 0.19-0.24 mJy/beam (median 0.21); tapered median 0.26  
  > "The final maps have a range of 1–$\sigma_{870}$ depths from 0.19–0.24 mJy beam$^{-1}$ (median $\sigma_{870} =$ 0.21 mJy beam$^{-1}$)." (2.2 Data Reduction)
- time on source: 150 s per target (5 x 30 s)  
  > "In total each target was observed five times (total integration time of 150 s)" (2.2 Data Reduction)
- observing dates: 2013 November 1  
  > "on 2013 November 1, as part of the Cycle-1 project 2012.1.00090.S" (2.2 Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **SCUBA-2 / S2CLS (JCMT)**: 850 um maps used to select the 30 targets and for flux comparison  
  > "The sub-mm sources in this paper were selected from observations taken as part of the S2CLS programme at the JCMT." (2.1 Sample Selection)
- External data: ALESS/LESS ALMA number counts combined with this sample for double power-law fit  
  > "We now combine our sample with the ALESS survey (cite: Karim13), with the aim of providing a single parameterization of the intrinsic sub-mm number counts" (4.2 Number Counts) [from (cite: Karim13)]
- External data: Faint serendipitous ALMA counts at 1.2 and 1.3 mm converted to 870 um  
  > "we also include two studies that have used serendipitous detections of sources in deep targeted ALMA observations to measure the number counts of faint SMGs at 1.2 and 1.3 mm" (4.2 Number Counts) [from (cite: Ono14), (cite: Hatsukade13)]
- External data: Composite ALESS SMG SED at z=2.5 for flux conversion; S870-LFIR relation  
  > "We convert these counts to 870 $\mu$m using the composite SMG spectral energy distribution (SED) from the ALESS survey (see (cite: Swinbank13)), redshifted to $z$ = 2.5" (4.2 Number Counts) [from (cite: Swinbank13)]
- External data: Simulated single-dish/ALMA follow-up galform data  
  > "To determine the magnitude of this effect we use a simulation of single-dish observations of SMGs, presented by (cite: Cowley15)." (4.4 Origin of Multiplicity) [from (cite: Cowley15)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration and imaging; manual vs pipeline not stated  
  > "The calibration and imaging of our science targets, and calibrators, was performed using the Common Astronomy Software Application (casa version 4.2.1)." (2.2 Data Reduction)
- casa version: CASA 4.2.1 (4.2.2 gave no change)  
  > "We repeated the data reduction using the most recent version of casa (4.2.2) and found it had no effect on our final maps or source catalog." (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+166 (set at 0.59 Jy)  
  > "The absolute flux scale for each measurement set was derived from observations of J 0238+166" (2.2 Data Reduction)
- flux scale uncertainty: calibrator varies up to 10% day to day  
  > "the ALMA calibrator archive shows that this source has day–to–day variations of up to 10 $\%$" (2.2 Data Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "To image each target we first Fourier transform the $uv$–data to create a “dirty” map, using Briggs weighting (robust parameter = 0.5)." (2.2 Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "using Briggs weighting (robust parameter = 0.5)" (2.2 Data Reduction)
- uv taper: natural weighting plus 0.6'' Gaussian taper for detection maps  
  > "we repeated the imaging process using natural weighting, and applied a 0.6$''$ Gaussian taper in the $uv$–plane" (2.2 Data Reduction)
- cell size: 0.04''  
  > "Both the “detection” and higher resolution maps have a size of 36$''$ $\times$ 36$''$, and a pixel scale of 0.04$''$." (2.2 Data Reduction)
- image size: 36'' x 36''  
  > "Both the “detection” and higher resolution maps have a size of 36$''$ $\times$ 36$''$" (2.2 Data Reduction)
- masking: clean to 3 sigma; if >5 sigma source, tight clean box and clean to 1.5 sigma  
  > "If a source is detected at $>5$ $\sigma$ then we repeat the cleaning process but place a tight clean box around each $>5$ $\sigma$ source and clean the dirty map to $1.5$ $\sigma$." (2.2 Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: CASA primary beam model  
  > "The fluxes measured in both sets of maps are primary–beam corrected using the model of the primary beam response output by casa." (3 Source Extraction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.35'' x 0.25''; detection 0.8'' x 0.65''  
  > "These low–resolution “detection” maps have a median rms of $\sigma_{870} =$ 0.26 mJy beam$^{-1}$ and a median synthesized beam of 0.8 $'' \times$ 0.65$''$." (2.2 Data Reduction)
- final rms: median 0.21 mJy/beam (0.26 tapered)  
  > "median $\sigma_{870} =$ 0.21 mJy beam$^{-1}$" (2.2 Data Reduction)

### Inherited from earlier work

- Cleaning depth determined by presence of strong sources  
  > "Following  (cite: Hodge13) we determine the amount of cleaning required based on the presence of strong sources in the maps." (2.2 Data Reduction) [from (cite: Hodge13)]
- Tests that sources are resolved and size measurements  
  > "These are detailed in (cite: Simpson15), but we give a summary here." (3 Source Extraction) [from (cite: Simpson15)]

### Not stated but needed to reproduce (our reading)

- Flux model/setup for J0238+166 beyond 0.59 Jy and CASA calibration script details
- clean niter, threshold and mask details beyond sigma levels
- Exact parameters of spline flux deboosting fit
- Bootstrap procedure details
- Fit method (likelihood/sampler) for the double power law
- Ma et al. S870-LFIR relation used for luminosity/SFR
- SCUBA-2 beam model and 2014 August S2CLS catalog (Geach et al. in prep.)

## Analysis recipe

1. **Image ALMA data**: CASA clean with Briggs robust 0.5 and a tapered natural-weighted version for detection  
  > "we repeated the imaging process using natural weighting, and applied a 0.6$''$ Gaussian taper in the $uv$–plane" (2.2 Data Reduction)
   - software: CASA
   - parameter: clean to 3 sigma; 1.5 sigma with boxes around >5 sigma sources  
  > "clean the dirty map to $1.5$ $\sigma$" (2.2 Data Reduction)
   - fitting: _not stated_
   - validation: Calibration and imaging verified by Manchester ARC node  
  > "We thank Adam Avison and the Manchester ALMA ARC node for their assistance in verifying the calibration and imaging of our ALMA data." (Acknowledgements)
2. **Extract source catalog**: SExtractor on 0.8'' detection maps, >3 sigma peaks, integrated flux in 0.8'' radius aperture, 4% correction, 4 sigma cut  
  > "We search the low–resolution 0.8$''$ “detection” maps and identify all $>$ $3$ $\sigma$ “peaks” in the non–primary–beam corrected maps." (3 Source Extraction)
   - software: SExtractor, CASA imfit
   - parameter: 4 sigma threshold gives 52 SMGs  
  > "Applying a $4$ $\sigma$ cut to our source catalog yields 52 SMGs, within the FWHM primary beam of the 30 ALMA maps." (3 Source Extraction)
   - fitting: _not stated_
   - validation: Inverted maps give contamination of ~2% at 4 sigma  
  > "corresponding to a contamination of 2 %  when considering our entire catalog" (3 Source Extraction)
3. **Completeness and flux deboosting via simulations**: 2e4 simulated maps with injected sources (power-law index -2, sizes 0-0.5''); spline fit of median output/input flux in 0.25 sigma bins  
  > "we create 2 $\times$ 10$^{4}$ simulated ALMA maps." (3.1 Completeness & Reliability)
   - parameter: completeness 93% at >4 sigma, ~100% at 5.5 sigma  
  > "The completeness is 93 %  at $>$ 4 $\sigma$, rising to about 100 %  at 5.5 $\sigma$" (3.1 Completeness & Reliability)
   - fitting: spline  
  > "We fit a spline to the median of each bin" (3.1 Completeness & Reliability)
   - validation: slope varied within Karim13 1-sigma changes correction by 10%  
  > "changes the correction by $\pm$ 10%  at a detection limit of 4 $\sigma$" (3.1 Completeness & Reliability)
4. **Compare to SCUBA-2 (astrometry, flux recovery)**: Convolve ALMA SMG models with SCUBA-2 beam, compare positions and peak fluxes  
  > "convolve each ALMA model map with a model of the SCUBA–2 beam" (3.2 Astrometry and Flux Recovery)
   - fitting: _not stated_
   - validation: Separations consistent with Ivison07 positional uncertainty  
  > "70 %  of the separations are smaller than the predicted 1– $\sigma$ uncertainty on the single-dish position" (3.2 Astrometry and Flux Recovery)
5. **Measure multiplicity**: Count SMGs per ALMA map (S870>~1 mJy), compute multiple fraction with Poisson errors and brightest-component flux ratio  
  > "17 of the 28 SCUBA–2 detected sources fragment into $>$ 1 SMGs, a multiple fraction of $61^{+19}_{-15}$ %" (4.1 Multiplicity)
   - fitting: _not stated_
   - validation: Compared to ALESS after removing SMGs below ALESS threshold  
  > "yielding a multiplicity fraction of $37^{+15}_{-11}$ %" (4.1 Multiplicity)
6. **Number counts and double power-law fit**: Counts at S870>7.5 mJy with area correction for selection incompleteness; fit double power law to combined ALMA samples  
  > "we choose to construct the number counts from our ALMA source catalog at $S_{870}$ $>$ 7.5 mJy." (4.2 Number Counts)
   - parameter: faint counts converted using ALESS composite SED at z=2.5 (factors 2.4 and 3.1)  
  > "flux conversion factors are 2.4 $\times$ and 3.1 $\times$, at 1.2 mm and 1.3 mm, respectively" (4.2 Number Counts)
   - assumption: Salpeter IMF for SFR; S870-LFIR relation from ALESS  
  > "or a SFR of $\sim$10$^{3}$ $\mathrel{\rm M_{\odot}\,yr^{-1}}$ (for a Salpeter IMF)" (4.2 Number Counts)
   - fitting: Double power law; fitting method not stated  
  > "we choose to model the counts with a double–power law of the form" (4.2 Number Counts)
   - validation: Removing three possibly lensed SMGs changes parameters by less than 1 sigma  
  > "change by less than their associated 1–$\sigma$ uncertainties" (4.2 Number Counts)
7. **Secondary SMG number density vs blank field**: Use maps with an SMG >8 mJy, count secondaries >2 mJy over the primary-beam area, compare to blank-field counts; test selection bias with randomised galform simulation  
  > "the number density of the secondary sources in our maps is a factor of 80 $\pm$ 30 times higher than the blank field number counts" (4.4 Origin of Multiplicity)
   - fitting: _not stated_
   - validation: Randomised simulation gives only 1.75 +/- 0.75 times excess  
  > "The resulting cumulative number density of secondary SMGs is a factor of 1.75 $\pm$ 0.75 times higher than the blank-field number counts." (4.4 Origin of Multiplicity)

## Software

- **CASA** 4.2.1: calibration, imaging, imfit, primary beam model  
  > "casa version 4.2.1" (2.2 Data Reduction)
- **SExtractor** v2.8.6: source extraction  
  > "we use the source extraction package sextractor (v2.8.6; (cite: Bertin96))" (3 Source Extraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMGs detected at >4 sigma | 52 | not stated | count | 2 | We detect 52 sub-millimeter galaxies (SMGs) at $>$ 4 $\sigma$ significance in our 30 ALMA maps. |
| Multiplicity fraction | 61 | +19/-15 | % | 5 | a multiple fraction of $61^{+19}_{-15}$ % |
| Brightest SMG / SCUBA-2 flux | 0.80 | +0.06/-0.02 | dimensionless | 5 | 0.80$^{+0.06}_{-0.02}$ |
| Double power-law break S0 | 8.4 | +/-0.6 | mJy | 6 | $S_{0}$ = 8.4$_{-0.6}^{+0.6}$ mJy |
| Double power-law N0 | 390 | +110/-80 | deg^-2 | 6 | $N_{0}$ = 390$_{-80}^{+110}$ deg$^{-2}$ |
| Slopes alpha, beta | alpha=1.9, beta=10.5 | +/-0.2; +3.0/-3.2 | dimensionless | 6 | $\alpha$ = 1.9$_{-0.2}^{+0.2}$ and $\beta$ = 10.5$_{-3.2}^{+3.0}$ |
| Secondary SMG density (>2 mJy) | 5.5e4 | +2.2/-1.6 (x10^4) | deg^-2 | 7 | (5.5$_{-1.6}^{+2.2}$) $\times$ 10$^{4}$ deg$^{-2}$ |
| Overdensity of secondaries vs blank field | 80 | 30 | dimensionless | 7 | a factor of 80 $\pm$ 30 times higher than the blank field number counts |
| Median half-light radius | 1.2 | 0.1 | kpc | 0 | median half-light radius of 1.2 $\pm$ 0.1 kpc |

## Qualitative findings

- Counts decline strongly at the bright end with no sharp cut-off.  
  > "We detect bright SMGs in our survey and do not find evidence for a sharp cut–off in the counts." (4.2 Number Counts)

## Claim tuples

- H: Are bright single-dish sources blends of multiple SMGs? | E: ALMA 870um imaging of 30 SCUBA-2 sources | R: 61% of 28 detected sources contain >=2 SMGs | F: Multiplicity is common and boosts single-dish counts by 20% at >7.5 mJy and 60% at >12 mJy | **supported**
- H: Is there a physical cut-off in SMG flux (Eddington limit) at ~9 mJy? | E: Combined counts fit with a double power law | R: break at 8.4 mJy but no sharp cut-off | F: Counts decline steeply; the break implies SFR~10^3 Msun/yr and ~100 Msun/yr/kpc^2 | **partially**
- H: Is multiplicity from line-of-sight projection or physical association? | E: Compare secondary SMG density with blank-field counts, with selection-bias simulation | R: 80 +/- 30 times excess | F: Many secondaries are likely physically associated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Tapered maps used to avoid resolving out extended emission  
  > "to ensure that any extended flux from the SMGs is not resolved–out, and that we detect low surface–brightness, extended, sources" (2.2 Data Reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Small number statistics at both ends of the counts  
  > "the samples are small and are still dominated by small number statistics" (4.2 Number Counts)
- Limitation (authors): No spectroscopic redshifts to confirm association  
  > "Clearly, to conclusively confirm these physical associations requires spectroscopic redshifts." (4.4 Origin of Multiplicity)
- Caveat (inferred, ours): Absolute ALMA flux scale uncertain (calibrator variability up to 10%)
- Caveat (inferred, ours): Multiplicity fraction depends on the 1 mJy threshold and SCUBA-2 sample selection from an earlier shallower map
- Caveat (inferred, ours): Fit method and errors for the combined counts are poorly described

## Reproducibility

- Data public (paper): All data obtainable from the ALMA archive  
  > "All data used in this analysis can be obtained from the ALMA archive." (Acknowledgements)
- Products in archive: _not stated_
- Missing: SCUBA-2 S2CLS UDS maps/catalog (Geach et al. in prep.)
- Missing: galform simulation outputs
- Missing: Ma et al. in prep. luminosity relation
- Data volume (inferred): ~10-30 GB raw (30 short-integration targets, one night)
- Score (inferred): 3/5, Public ALMA data and clear imaging/extraction recipe, but SCUBA-2 data, simulations and some fit details are not available or are not stated.
- Rediscovery candidate: no, Needs unreleased SCUBA-2 catalog and simulations for key results, and the fit details are not stated.

## Links

- Method: (cite: Hodge13) (clean procedure and ALESS comparison)
- Method: (cite: Simpson15) (size measurement and resolution tests)
- Companion: (cite: Simpson15) (companion paper on sizes and properties of these SMGs)
- Related: S2CLS
- Related: ALESS
- Related: UKIDSS UDS

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 60,
  "rate": 0.741
 },
 "evidence_ok": true
}
```
