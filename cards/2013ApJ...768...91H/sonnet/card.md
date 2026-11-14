# An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: Source Catalog and Multiplicity

`2013ApJ...768...91H` | The Astrophysical Journal 2013 | first author: Hodge, J. A. | arXiv: 1304.4266 | DOI: 10.1088/0004-637X/768/1/91

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What are the interferometric 870um positions, fluxes and multiplicity of the LESS submillimeter sources, and how reliable are earlier single-dish positions and radio/mid-IR counterpart identifications?  
  > "The high resolution of these maps allows us to resolve sources that were previously blended and accurately identify the origin of the submillimeter emission." (abstract)
- Target **126 LESS submillimeter sources in the ECDFS (ALESS)**: coordinates Table 2 lists positions per LESS ID (e.g. LESS 1: 03:33:14.26 -27:56:11.2)  
  > "The 126 submillimeter sources we target were previously detected in the LABOCA ECDFS Submillimeter Survey" (1 Introduction); z/distance not stated (z=2.5 assumed for kpc scales; ALESS 007.1 z_phot=2.81)  
  > "The 126 submillimeter sources we target were previously detected in the LABOCA ECDFS Submillimeter Survey" (1 Introduction); distance from Wardlow et al. 2011 photometric redshift for ALESS 007.1  
  > "The 126 submillimeter sources we target were previously detected in the LABOCA ECDFS Submillimeter Survey" (1 Introduction)

## Data provenance

- ALMA projects: 2011.1.00294.S
- bands: Band 7, centered at 344 GHz (870 um)  
  > "We observed the LESS sources with ALMA’s Band 7 centered at 344 GHz (870$\mu$m)" (2.1 Observations)
- frequencies and spectral setup: single continuum mode, 4 x 128 dual-polarization channels over 8 GHz, 7.5 GHz usable  
  > "utilized the “single continuum” spectral mode, with 4 $\times$ 128 dual polarization channels over the full 8 GHz bandwidth, 7.5 GHz of which was usable after flagging edge channels." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 12-15 per SB  
  > "Number of antennas in that SB; 12–m only" (Table 1)
- configurations: Cycle 0 compact configuration, max baseline 125 m  
  > "The observations were taken in ALMA’s Cycle 0 compact configuration, which had a maximum baseline of 125m" (2.1 Observations)
- baselines: _not stated_
- angular resolution: median 1.6" x 1.15"  
  > "corresponding to a median angular resolution of 1.6$^{\prime\prime}$$\times$1.15$^{\prime\prime}$" (2.3 Final Maps)
- max recoverable scale: _not stated_
- sensitivity: median rms 0.4 mJy/beam (requested 0.4)  
  > "The median rms noise (at field center) of the maps is $\sigma = 0.4$ mJy beam$^{-1}$" (2.3 Final Maps)
- time on source: 120 s per field  
  > "each field was observed for 120 seconds" (2.1 Observations)
- observing dates: 18 Oct 2011 - 03 Nov 2011, 8 scheduling blocks  
  > "The ALMA observations were taken between 18 Oct 2011–03 Nov 2011" (2.1 Observations)
- pi or archival as stated: _not stated_
- Other facility **APEX/LABOCA (LESS)**: Original 870um single-dish source catalog and flux densities  
  > "previously detected in the LABOCA ECDFS Submillimeter Survey" (1 Introduction)
- Other facility **VLA 1.4 GHz**: Radio maps for astrometry and counterpart tests  
  > "ALESS SMGs in good quality maps with VLA 1.4 GHz counterparts" (3.4 Astrometry)
- External data: LESS source positions and deboosted LABOCA flux densities  
  > "The beam was centered on the catalogued positions of the LESS sources" (2.1 Observations) [from Weiß et al. 2009 (cite: 2009ApJ...707.1201W)]
- External data: Radio/MIR counterpart catalog (robust/tentative)  
  > "used radio and mid–infrared data from the Very Large Array and *Spitzer* to identify potential counterparts to the LESS sources" (5.5 Radio/MIR IDs) [from Biggs et al. 2011 (cite: 2011MNRAS.413.2314B)]
- External data: Photometric redshift and SFR for ALESS 007.1  
  > "photometric redshift estimate of $z_{\rm phot}=2.81\pm^{0.18}_{0.07}$" (5.1 Source sizes) [from Wardlow et al. 2011 (cite: 2011MNRAS.415.1479W)]
- External data: VLA 1.4 GHz ECDFS maps (DR1 and DR2)  
  > "Recently, (cite: 2013arXiv1301.7004M) also released another re–reduction of the (cite: 2008ApJS..179..114M) data" (3.4 Astrometry) [from Miller et al. 2008, 2013]

## Processing

### Calibration

- pipeline or manual: Manual CASA calibration per SB  
  > "The data were reduced and imaged using the Common Astronomy Software Application (casa) version 3.4.0" (2.2 Data Reduction)
- casa version: CASA 3.4.0  
  > "Common Astronomy Software Application (casa) version 3.4.0" (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars or Uranus; B0537-441 bandpass; B0402-362 phase  
  > "Depending on the SB, either Mars or Uranus served to set the absolute flux density scale. The quasar B0537-441 was used for bandpass calibration." (2.1 Observations)
- flux scale uncertainty: ~15%, not included in SMG error bars  
  > "The absolute flux calibration has an uncertainty of $\sim$15%, and this uncertainty is not included in the error bars for individual SMG flux densities." (2.2 Data Reduction)
- self calibration: None; no source bright enough  
  > "No sources were deemed bright enough to reliably self–calibrate." (2.2 Data Reduction)

### Imaging

- task: CASA clean  
  > "using the clean algorithm and natural weighting" (2.2 Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using the clean algorithm and natural weighting" (2.2 Data Reduction)
- uv taper: _not stated_
- cell size: 0.2"  
  > "The images are 25.6$^{\prime\prime}$ (128 pixels) per side and have a pixel scale of 0.2$^{\prime\prime}$." (2.2 Data Reduction)
- image size: 128 pixels (25.6") per side  
  > "The images are 25.6$^{\prime\prime}$ (128 pixels) per side" (2.2 Data Reduction)
- masking: BOXIT finds >5 sigma sources; tight clean boxes; clean to 1.5 sigma; otherwise clean to 3 sigma  
  > "We then used the task BOXIT to automatically identify significant ($>$5$\sigma$) sources." (2.2 Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Maps not pb-corrected; catalog gives pb-corrected fluxes  
  > "These maps have not been corrected for the response of the primary beam" (2.3 Final Maps)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: median 0.4 mJy/beam; 85% < 0.6  
  > "We find that 85% of the maps achieve an rms noise of $\sigma < 0.6$ mJy beam$^{-1}$." (2.3 Final Maps)

### Inherited from earlier work

- Completeness, spurious fraction and reliability of source extraction  
  > "The result, presented in a companion paper (Karim et al. 2012), is that the source extraction recovers $\sim$99% of all sources above 3.5$\sigma$" (3.2 Completeness and Reliability) [from Karim et al. 2012 (cite: Karim_aless)]
- Error estimation for elliptical Gaussian fits in correlated noise  
  > "We adopt those findings for error estimates for our measured source parameters" (Error determination) [from Condon 1997 (cite: 1997PASP..109..166C)]

### Not stated but needed to reproduce (our reading)

- Source extraction code is custom IDL and not released; MCMC step sizes, chain length and box-size choices not given
- Which SBs used Mars vs Uranus and flux values adopted
- Exact clean iteration counts and masks
- Rule for primary-beam correction of fluxes
- Simulation details of fake-source flux distribution
- Details of the random separation simulation

## Analysis recipe

1. **Calibrate and image**: Manual CASA calibration (Tsys, WVR, bandpass, phase, flux) then clean with natural weighting, boxes around >5 sigma sources  
  > "The $uv$–data were Fourier–transformed and the resulting “dirty" image was deconvolved from the point spread function" (2.2 Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Calibrated calibrators inspected; process repeated if inadequate  
  > "If the calibration was deemed inadequate (based on inspection of the calibrated calibrators) then more data was flagged and the process was repeated." (2.2 Data Reduction)
2. **Extract sources**: Iterative pixel-peak (>2.5 sigma) fitting of elliptical Gaussians with MH-MCMC in 2"x2" boxes; 3-parameter point-source and 6-parameter fits; subtract model and repeat  
  > "we determined the elliptical Gaussian that best described the underlying signal distribution using an idl-implemented Metropolis-Hastings Markov chain Monte Carlo (MH-MCMC) algorithm" (3.1 Source Extraction)
   - software: IDL custom code
   - parameter: detection threshold 3.5 sigma in good maps  
  > "We will therefore take 3.5$\sigma$ as our source detection threshold in the good quality maps" (3.2 Completeness and Reliability)
   - fitting: MH-MCMC, posterior mean as best fit, ~30% acceptance  
  > "On average, we reached an acceptance probability of 30% after an initial and sufficiently long thermalization phase." (Details of the source extraction)
   - validation: Compared with CASA imfit for >4 sigma sources: (S_IMFIT - S_SOURCE)/S_SOURCE = 0.001 +/- 0.09  
  > "(S$_{\rm IMFIT}$ $-$ S$_{\rm SOURCE}$)/S$_{\rm SOURCE}$ $=$ 0.001 $\pm$ 0.09" (3.1 Source Extraction)
3. **Completeness, reliability, flux scale and astrometry checks**: Fake-source insertion; extraction on inverted maps; ALMA maps convolved to 19" compared with LABOCA; comparison with VLA, MIPS and IRAC positions  
  > "We then determined what flux would be measured by a telescope with a 19$^{\prime\prime}$ beam, the FWHM of LABOCA, by convolving the maps to the LABOCA resolution." (3.3 Absolute Flux Scale)
   - fitting: _not stated_
   - validation: Flux ratio consistent with unity at 3 sigma threshold  
  > "deriving a median flux density ratio of" (3.3 Absolute Flux Scale)
4. **Define samples and multiplicity**: MAIN: rms<0.6, axis ratio<2, inside primary beam FWHM, S/N>3.5; supplementary samples with S/N>4; count SMGs per LESS source; compare separations to random simulation  
  > "These 99 SMGs are the most reliable SMGs, coming from within the primary beam FWHM of the good–quality maps" (4.1 Sample Definitions)
   - assumption: z = 2.5 for projected separations  
  > "assuming a typical SMG redshift of $z=2.5$" (5.2 Multiplicity)
   - fitting: _not stated_
   - validation: 100 random simulations of separations  
  > "We repeated this simulation 100 times to increase statistics" (5.2 Multiplicity)
5. **Test LABOCA position uncertainty and radio/MIR counterparts**: Fit offset vs S/N relation (Ivison 2007) for k; compare ALESS SMGs to Biggs et al. counterparts; stack VLA DR2 cutouts  
  > "we find $k = 0.66\pm0.03$" (5.4 LABOCA Positional Offsets)
   - fitting: Function fit to median offsets in S/N bins with sqrt(2) radial correction  
  > "Fitting a function to the median data points of the form given in Equation" (5.4 LABOCA Positional Offsets)
   - validation: _not stated_

## Software

- **CASA** 3.4.0: Data reduction, imaging, imfit checks  
  > "Common Astronomy Software Application (casa) version 3.4.0" (2.2 Data Reduction)
- **BOXIT** : Identify >5 sigma sources for clean boxes  
  > "We then used the task BOXIT to automatically identify significant ($>$5$\sigma$) sources." (2.2 Data Reduction)
- **IDL custom source extraction (MH-MCMC)** : Source detection and fitting  
  > "We used custom–written idl–based source extraction software to identify and extract sources from the final, cleaned ALMA maps." (3.1 Source Extraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median rms noise | 0.4 | not stated | mJy/beam | 1 | The median rms noise (at field center) of the maps is $\sigma = 0.4$ mJy beam$^{-1}$ |
| MAIN sample size | 99 | not stated | SMGs | 4 | These 99 SMGs are the most reliable SMGs |
| Median S_ALMA/S_LABOCA (3 sigma threshold) | 0.97 | +0.07/-0.04 | dimensionless | 3 | S$_{\rm ALMA}$/S$_{\rm LABOCA}$ $=$ 0.97$\pm^{0.07}_{0.04}$ |
| LESS sources split into multiple MAIN SMGs | 24 of 69 | not stated | sources | 4 | we find that 24 of 69 LESS sources split into two or more MAIN ALESS SMGs |
| Non-detections in good quality maps | 17/88 (~19%) | 4% | fraction | 4 | We therefore find that 17/88 ($\sim$19%$\pm$4%) of the LESS sources with high–quality ALMA coverage are non–detections. |
| Positional offset normalization k (all) | 0.66 | 0.03 | dimensionless | 5 | we find $k = 0.66\pm0.03$ |
| ALESS 007.1 intrinsic size | (1.1")x(0.7") | 0.3" / 0.2" | arcsec | 2 | (1.1$^{\prime\prime}$$\pm$0.3$^{\prime\prime}$)$\times$(0.7$^{\prime\prime}$$\pm$0.2$^{\prime\prime}$) |
| Radio/MIR robust counterpart completeness | ~45% (55% incl. tentative) | not stated | fraction | 5 | completeness of only $\sim$45%, but a reliability of $\sim$80% |

## Qualitative findings

- Most SMGs are unresolved point sources; no excess of SMG pairs at small separations.  
  > "Therefore, the ALESS SMGs show no evidence for an excess of sources at small separations." (5.2 Multiplicity)

## Claim tuples

- H: Do single-dish LESS sources break into multiple SMGs? | E: Count MAIN/supplementary SMGs per LESS field in good maps | R: 24/69 (MAIN) and 32/71 split into multiples | F: At least 35% (up to 50%) of LESS sources are multiples; brighter ones preferentially | **supported**
- H: Are previously predicted radio/MIR counterparts complete and reliable? | E: Match ALESS SMGs to Biggs et al. counterparts | R: 45 of 99 robust, 9 more tentative; reliability ~80% | F: 45% of SMGs were missed | **supported**
- H: Are the ALMA and LABOCA flux scales consistent? | E: Convolve ALMA model maps to LABOCA resolution | R: ratio 0.97 | F: No overall systematic bias | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Some reliability estimates are lower limits; several maps are poor quality due to low elevation observations.  
  > "these reliability estimates are likely lower limits." (3.2 Completeness and Reliability)
- Caveat (inferred, ours): Multiplicity fraction depends on 3.5 sigma threshold and nonuniform map quality
- Caveat (inferred, ours): Radio astrometric offsets vary between reductions
- Caveat (inferred, ours): Non-detection explanation as faint multiples is speculative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Project 2011.1.00294.S data in ALMA archive; catalog released with paper and on ALESS website  
  > "The ALESS catalog can be found accompanying this paper or from the ALESS website" (4.2 Using the Catalog)
- Missing: Custom IDL extraction code
- Missing: Fake source simulation specifics
- Missing: Per-SB flux calibrator values
- Data volume (inferred): ~10-30 GB raw (8 SBs, Cycle 0 continuum)
- Score (inferred): 3/5, Data public and calibration/imaging well described, but custom unreleased source extraction code and companion-paper completeness inputs.
- Rediscovery candidate: yes, Public data, simple imaging recipe, numeric results (rms, source counts, fluxes).

## Links

- Method: Condon 1997 (cite: 1997PASP..109..166C) (Error estimates for Gaussian fits)
- Companion: Karim et al. 2012 (cite: Karim_aless) (Completeness, number counts)
- Companion: Swinbank et al. 2012 (cite: 2012MNRAS.427.1066S) (z~4 SMG number density)
- Related: LESS
- Related: ECDFS

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00294.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 51,
  "rate": 0.699
 },
 "evidence_ok": true
}
```
