# GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies

`2018A&A...620A.152F` | Astronomy and Astrophysics 2018 | first author: Franco, M. | arXiv: 1803.00157 | DOI: 10.1051/0004-6361/201832928

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Which galaxies does a blind, contiguous 69 arcmin2 ALMA 1.1 mm survey of GOODS-South detect, and what are their counterparts (including HST-dark galaxies), redshifts, masses, AGN fraction and number counts?  
  > "In this study we present an unbiased view of a large (69 arcmin$^2$) region of the sky, without prior or a posteriori selection based on already known galaxies" (1 Introduction)
- Target **GOODS-South ALMA mosaic (AGS1-AGS23)**: coordinates RA 03h32m30.0s, Dec -27d48m00s (J2000)  
  > "centred at $\alpha$ = 3$^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$ , $\delta$ = -27$\degree$ 48$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000; 2015.1.00543.S; PI: D. Elbaz)" (2.1 Survey description); z/distance median z = 2.92 for 17 sources with redshifts  
  > "centred at $\alpha$ = 3$^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$ , $\delta$ = -27$\degree$ 48$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000; 2015.1.00543.S; PI: D. Elbaz)" (2.1 Survey description); distance from ZFOURGE catalogue photometric redshifts, spectroscopic where available  
  > "centred at $\alpha$ = 3$^{\rm h}$ 32$^{\rm m}$ 30.0$^{\rm s}$ , $\delta$ = -27$\degree$ 48$\ensuremath{'}$ 00$\ensuremath{''}$ (J2000; 2015.1.00543.S; PI: D. Elbaz)" (2.1 Survey description)

## Data provenance

- ALMA projects: 2015.1.00543.S
- bands: Band 6, 1.1 mm (264.9 GHz)  
  > "optimised the setup for continuum detection at 264.9 GHz ($\lambda$ = $1.13$ mm)" (2.1 Survey description)
- frequencies and spectral setup: four 1875 MHz spectral windows centred at 255.9, 257.9, 271.9, 273.9 GHz; TDM mode, 128 channels per window  
  > "using four 1875 MHz-wide spectral windows centered at 255.9 GHz, 257.9 GHz, 271.9 GHz and 273.9 GHz, covering a total bandwidth of $7.5\,$GHz" (2.1 Survey description)
- continuum bandwidth: 7.5 GHz total  
  > "covering a total bandwidth of $7.5\,$GHz" (2.1 Survey description)
- arrays: _not stated_
- configurations: C40-5, max baseline ~1500 m, ~40 antennae  
  > "in configuration C40-5 with a maximum baseline of $\sim\,$1500 m" (2.1 Survey description)
- baselines: _not stated_
- angular resolution: native ~0.24 arcsec; tapered to 0.29 and 0.60 arcsec circular beams  
  > "a homogeneous and circular synthesized beam of $0\ensuremath{''}29$ Full Width Half Maximum" (2.2 Data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.18 mJy/beam in 0.60 arcsec mosaic  
  > "We adopt a general value of rms sensitivity $\sigma$ = 0.18 mJy.beam$^{-1}$." (2.3 Building of the noise map)
- time on source: ~60 s per pointing; 843.55 min on target total  
  > "yielding a total on-source integration time of $\sim\,$60 seconds per pointing" (2.1 Survey description)
- observing dates: 1 August to 2 September 2016  
  > "Observations were taken between the 1$^{\rm{st}}$ of August and the $2^{\rm{nd}}$ of September 2016" (2.1 Survey description)
- pi or archival as stated: PI D. Elbaz, Cycle 3, 846-pointing mosaic in six sub-mosaics  
  > "we designed a 846-pointing mosaic, each pointing being separated by $0.8$ times the antenna Half Power Beam Width" (2.1 Survey description)
- Other facility **HST CANDELS**: H-band and optical imaging, counterpart catalogue (Guo2013)  
  > "The 5-$\sigma$ detection depth for a point-source reaches a magnitude of 28.16 for the $H_{160}$ filter" (2.4.1 Optical/near-infrared imaging)
- Other facility **ZFOURGE (Magellan FourStar)**: stellar masses and redshifts  
  > "We use the stellar masses and redshifts from the ZFOURGE catalogue, except when spectroscopic redshifts are available." (2.4.1 Optical/near-infrared imaging)
- Other facility **Spitzer IRAC/MIPS, Herschel**: mid/far-IR counterparts and SEDs  
  > "Data in the mid and far-IR are provided by the Infrared Array Camera" (2.4.2 Mid/far-infrared imaging)
- Other facility **Chandra 7 Ms CDF-S**: X-ray AGN identification  
  > "We will use this X-ray catalogue to identify candidate X-ray active galactic nuclei (AGN) among our ALMA detections." (2.4.5 X-ray)
- Other facility **VLA 5 cm**: radio fluxes  
  > "We also use radio imaging at 5 cm from the Karl G. Jansky Very Large Array (VLA)." (2.4.4 Radio imaging)
- Other facility **Pan-STARRS DR1 and GAIA DR1**: reference astrometry to correct HST positions  
  > "we compared the HST source positions with detections from the Panoramic Survey Telescope and Rapid Response System (Pan-STARRS)" (4.3 Astrometric correction)
- External data: HUDF 1.3 mm ALMA catalogue for cross-checking detections  
  > "The ALMA image of the full HUDF reaches a $\sigma_{1.3mm}$ = 35 $\mu$Jy (cite: Dunlop2017)" (2.4.3 Complementary ALMA data) [from (cite: Dunlop2017)]
- External data: Redshifts and stellar masses from ZFOURGE  
  > "We use the stellar masses and redshifts from the ZFOURGE catalogue, except when spectroscopic redshifts are available." (2.4.1 Optical/near-infrared imaging) [from (cite: Straatman2016)]
- External data: X-ray catalogue and AGN classification  
  > "We find an X-ray counterpart for 65% of them (13/20) in the 7 Msec X-ray survey of GOODS–*South* with *Chandra* (cite: Luo2017)." (7.3 AGN) [from (cite: Luo2017)]
- External data: SIDES simulation number counts for comparison  
  > "We compare our results with an empirical model that predicts the number counts at far-IR and millimetre wavelengths, developed by (cite: Bethermin2017)." (5.4 Cumulative and differential number counts) [from (cite: Bethermin2017)]

## Processing

### Calibration

- pipeline or manual: ALMA project calibration scripts with a few extra flags  
  > "All EBs were calibrated with CASA (cite: McMullin2007) using the scripts provided by the ALMA project." (2.2 Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 (flux), J0348-2749 (phase), J0522-3627 or J0238+1636 (bandpass)  
  > "J0334-4008 and J0348-2749 (VLBA calibrator and hence has a highly precise position) were systematically used as flux and phase calibrators, respectively." (2.1 Survey description)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, multi-frequency synthesis; dirty map used  
  > "Imaging was done in CASA using the multi-frequency synthesis algorithm implemented within the task `CLEAN`." (2.2 Data reduction)
- deconvolver: no cleaning; dirty map used (clean noise differs <1%)  
  > "we decided to work with the dirty map." (2.2 Data reduction)
- weighting robust: _not stated_
- uv taper: per-sub-mosaic u,v tapers to circular 0.29 and 0.60 arcsec beams  
  > "we applied different $u$, $v$ tapers to each sub-mosaic." (2.2 Data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied separately to each sub-mosaic; combined by noise-map weighted mean  
  > "Sub-mosaics were produced and primary beam corrected separately, to finally be combined using a weighted mean based on their noise maps." (2.2 Data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.60 arcsec circular (mean 614x587 mas) and 0.29 arcsec  
  > "a second mosaic with an homogeneous and circular synthesized beam of $0\ensuremath{''}60$ FWHM" (2.2 Data reduction)
- final rms: 0.176 mJy/beam median, adopted 0.18 mJy/beam  
  > "The median value of the standard deviation is 0.176 mJy.beam$^{-1}$." (2.3 Building of the noise map)

### Inherited from earlier work

- Peak flux of Blobcat corrected for peak bias  
  > "refers to the peak of the surface brightness corrected for peak bias (see (cite: Hales2012))" (4.1 Creation of the catalogue) [from (cite: Hales2012)]
- Minimum reliable size limit for interferometers  
  > "Following (cite: Marti-Vidal2012), the reliable size measurement limit for an interferometer is:" (4.5 Galaxy sizes) [from (cite: Marti-Vidal2012)]
- Spectroscopic redshifts for AGS1,2,3,9,12,13,18  
  > "determined by (cite: Kurk2013), and recently confirmed by (cite: Barro2017), (cite: Momcheva2016)" (6.1 Redshift distribution) [from (cite: Kurk2013)]
- Dust SED scaling of other surveys' fluxes to 1.1 mm  
  > "These values have also been chosen to be consistent with (cite: Hatsukade2016)." (5.4 Cumulative and differential number counts) [from (cite: Hatsukade2016)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Exact CLEAN/tclean parameters (cell, image size, uv-taper values, weighting)
- Primary-beam cutoff and sub-mosaic combination details
- Exact BLOBCAT settings beyond sigma_p and sigma_f
- Flux scale uncertainty and self-calibration
- Details of FAST/EAZY fits (templates, priors)
- Astrometric offset table for each galaxy

## Analysis recipe

1. **Calibrate, average and image the mosaics**: CASA calibration with ALMA scripts, average to 120 s and 8 channels, CLEAN MFS dirty maps per slice with u,v tapers, combine with noise-weighted mean  
  > "we time- and frequency-averaged our calibrated EBs over 120 seconds and 8 channels, respectively." (2.2 Data reduction)
   - software: CASA
   - parameter: tapered beams 0.29 and 0.60 arcsec  
  > "We also applied this tapering method to create a second mosaic with an homogeneous and circular synthesized beam of $0\ensuremath{''}60$ FWHM" (2.2 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build noise map**: k-sigma clipping std in 100x100 pixel box every 4 pixels, 3 iterations, 3 sigma clip  
  > "In steps of 4 pixels on the image map, the standard deviation was computed in a square of 100 $\times$ 100 pixels around the central pixel." (2.3 Building of the noise map)
   - fitting: _not stated_
   - validation: Gaussian fit of unclipped map gives 0.182 mJy/beam vs median 0.176  
  > "the Gaussian fit of the unclipped map gives a standard deviation of 0.182 mJy.beam$^{-1}$." (2.3 Building of the noise map)
3. **Detect sources and set thresholds**: BLOBCAT flood fill on SNR map of 0.60 arcsec mosaic; scan sigma_p 4-6 and sigma_f 2.5-4; require purity (Np-Nn)/Np >= 0.8 from inverted map  
  > "This leads to $\sigma_p$ = 4.8 $\sigma$ when fixing the value of $\sigma_f$ = 2.7 $\sigma$" (3 Source Detection)
   - software: BLOBCAT
   - parameter: sigma_p = 4.8, sigma_f = 2.7  
  > "Hence we decided to set $\sigma_p$ = 4.8 $\sigma$ and $\sigma_f$ = 2.7 $\sigma$ to produce our catalogue of ALMA detections." (3 Source Detection)
   - fitting: _not stated_
   - validation: Positive vs negative detections; HST counterpart fraction as a check  
  > "The difference between positive and negative detections for each pair of ($\sigma_p$, $\sigma_f$) values provides the expected number of real sources." (3 Source Detection)
4. **Measure fluxes and sizes**: Blobcat peak, Galfit PSF fitting, PyBDSM, uvmodelfit; stacking; point-source assumption with corrections for AGS17 and AGS18  
  > "we compared different flux extraction methods and softwares: `PyBDSM` (cite: Mohan2015); `Galfit` (cite: Peng2010); `Blobcat` (cite: Hales2012)." (4.1 Creation of the catalogue)
   - software: BLOBCAT, Galfit, PyBDSM, CASA uvmodelfit
   - assumption: sources point-like in 0.60 arcsec mosaic  
  > "we assume that the galaxies detected in the 0$''$60-mosaic are point-like." (4.1 Creation of the catalogue)
   - fitting: Galfit PSF fits in 5x5 arcsec box; Sersic index fixed to 1 in comparison fits  
  > "the Sersic index was frozen to n = 1" (4.5 Galaxy sizes)
   - validation: Consistency of methods; residuals below 3 sigma for 21/23  
  > "The residuals of 21/23 detections do not have a peak greater than 3 $\sigma$ in a radius of 1$''$ around the source." (4.5 Galaxy sizes)
5. **Correct HST astrometry and identify counterparts**: Cross-match Guo2013 with Pan-STARRS/GAIA within 0.5 arcsec, subtract median offset iteratively 3 times, then match counterparts within 0.6 arcsec; Monte Carlo chance-association probability  
  > "Cross-matching was done within a radius of 0$''$5." (4.3 Astrometric correction)
   - fitting: _not stated_
   - validation: Consistent with Rujopakarn2016 offsets  
  > "This offset is consistent with that found by (cite: Rujopakarn2016)" (4.3 Astrometric correction)
6. **Completeness, flux boosting, effective area, number counts**: Inject 300 artificial sources per run, 100 runs per flux 0.5-2.4 mJy, sizes FWHM 0.2-0.9 arcsec; deboost; correct purity, completeness and effective area; fit DPL and Schechter functions  
  > "We inject 300 artificial sources of a given flux, and repeat this procedure 100 times for each flux density." (5.1 Completeness)
   - assumption: ALMA sizes 1.4 times smaller than HST H-band sizes  
  > "We took the hypothesis that ALMA sizes are 1.4 times smaller than the size measured in HST $H$-band" (5.1 Completeness)
   - fitting: least squares with Trust Region Reflective algorithm  
  > "We use a least squares method with the Trust Region Reflective algorithm for these two fitted-functions." (5.4 Cumulative and differential number counts)
   - validation: Comparison with SIDES and literature counts  
  > "The (cite: Bethermin2017) prediction is in good agreement with the number counts derived in this study, for the two bins with the lowest fluxes." (5.4 Cumulative and differential number counts)
7. **Derive galaxy properties and AGN fraction**: Redshift and mass distributions from ZFOURGE; UVJ selection of SFGs; X-ray AGN criteria; EAZY and FAST for AGS4  
  > "either *(i)* L$_{X,int}$ $>$  10$^{43}$ erg.s$^{-1}$ (luminous X-ray sources) or *(ii)* $\Gamma$ $<$ 1.0 (hard X-ray sources)." (7.3 AGN)
   - software: EAZY, FAST, Le PHARE
   - assumption: Salpeter IMF, flat LCDM H0=70, Om=0.7  
  > "we adopt a spatially flat $\Lambda$CDM cosmological model with H$_0$ = 70 kms$^{-1}$Mpc$^{-1}$, $\Omega_m$ = 0.7 and $\Omega_{\Lambda}$ = 0.3." (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, CLEAN imaging, uvmodelfit, fitsky  
  > "All EBs were calibrated with CASA (cite: McMullin2007)" (2.2 Data reduction)
- **BLOBCAT** : source extraction and peak fluxes  
  > "To identify the galaxies present on the image, we use BLOBCAT (cite: Hales2012)." (3 Source Detection)
- **PyBDSM** : flux comparison  
  > "`PyBDSM` (cite: Mohan2015)" (4.1 Creation of the catalogue)
- **Galfit** : PSF/Gaussian/Sersic flux fits and HST deblending  
  > "We use `Galfit` (cite: Peng2010) on the 0$''$60-mosaic." (4.5 Galaxy sizes)
- **EAZY** : photometric redshifts for AGS4 components  
  > "The redshifts were estimated using `EAZY`." (7 HST-dark galaxies)
- **FAST** : stellar mass of AGS4  
  > "The stellar mass of the ALMA galaxy was then computed with `FAST` (cite: Kriek2009)" (7 HST-dark galaxies)
- **Le PHARE** : redshift of AGS17 neighbour  
  > "the redshift determination of 0.92$_{-0.18}^{+0.04}$ by `Le PHARE`" (7 HST-dark galaxies)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of main-catalogue detections | 20 | not stated | sources | 3 | we obtain a total of 20 detections down to a flux density limit of $S_{1.1mm}$ $\approx$ 880 $\mu$Jy |
| Expected spurious sources | 4 | ±2 | sources | 3 | suggests the presence of 4$\pm$2 |
| Median redshift | 2.92 | ±0.20 | dimensionless | 7 | The median redshift of our sample is 2.92$\pm$0.20 |
| Mean redshift | 3.03 | ±0.17 | dimensionless | 7 | The mean redshift of the sample is $z$ = 3.03$\pm$0.17 |
| Median stellar mass | 1.1e11 | ±0.4e11 | Msun | 7 | M$_{\star}$ = (1.1$\pm$0.4) $\times$ 10$^{11}$ M$_\ensuremath{\odot}$ |
| HST-dark fraction | 20% (4/20) | not stated | percent | 5 | we have detected 20% HST–dark galaxies (4 out of 20 robust detections) |
| AGN fraction in mass-z box for ALMA sources | 50% (8/16) vs 14% (23/160) | not stated | percent | 7 | we find that 50% of the ALMA sources host an AGN (8/16) as compared to only 14% (23/160) |
| Median HST-ALMA astrometric offset | -94 mas RA, +262 mas Dec | ±42, ±50 mas | mas | 5 | corrected by $-$94$\pm$42 mas in right ascension, $\alpha$, and 262$\pm$50 mas in declination |
| Completeness at 1.2 mJy for point sources | 94 | ±1% | percent | 6 | at 1.2 mJy, our sample is 94$\pm$1% complete for point sources |
| EBL fraction resolved at 0.8 mJy | 13.5 | +9.0/-8.6 | percent | 6 | We have resolved only 13.5$_{-8.6}^{+9.0}$% of the EBL into individual galaxies at 0.8 mJy. |
| Median compact size from uvmodelfit | 0.18 | not stated | arcsec FWHM | 4 | The median size of our sample of 20 galaxies is 0$''$18 |

## Qualitative findings

- Wide area gives lower bright-end counts than single-dish surveys affected by confusion  
  > "The wide area of our ALMA survey provides lower values at the bright end of number counts than single-dish telescopes affected by confusion." (abstract)

## Claim tuples

- H: Does the survey find a reliable blind sample at ≥80% purity? | E: Tapered 0.60 arcsec mosaic, BLOBCAT with thresholds from positive/negative detection counts | R: 20 detections >0.7 mJy with purity >80%; 3 likely spurious | F: Robust blind catalogue of 20 sources | **supported**
- H: Do ALMA blind surveys reveal HST-dark galaxies? | E: Counterpart search in HST, ZFOURGE and IRAC | R: 4 of 20 HST-dark with IRAC counterparts | F: ~20% of sources are HST-dark, two likely at z>4 | **partially**
- H: Does a larger area probe higher redshift massive galaxies? | E: Redshift and mass distributions vs deeper smaller surveys | R: Median z=2.92, median mass 1.1e11 | F: Area is key for high-z massive detections | **supported**
- H: Is the AGN fraction higher among ALMA-detected galaxies? | E: Chandra 7 Ms matches with luminosity/hardness criteria | R: ≥40% host X-ray AGN vs ~14% control | F: Excess AGN fraction | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Tapering reduces independent beams and spurious detections, and optimises point-source sensitivity  
  > "to reduce the number of independent beams – thus reducing the number of purely statistical spurious detections – and optimize the sensitivity to point sources" (abstract)
- Alternative: Mosaics with coarser resolution than 0.60 arcsec rejected owing to sensitivity and beam degradation  
  > "Mosaics with even coarser spatial resolution could not be created because of drastic sensitivity and synthesized beam shape degradations." (2.2 Data reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Cosmic variance not included in count errors; the HST-dark status of three sources needs further investigation  
  > "Cosmic variance was not taken into account in the calculation of the errors." (5.4 Cumulative and differential number counts)
- Caveat (inferred, ours): Dirty map used without CLEAN; point-source assumption affects fluxes and completeness
- Caveat (inferred, ours): Counts depend on assumed ALMA/HST size ratio of 1.4
- Caveat (inferred, ours): Counterpart identification depends on a custom HST astrometric offset

## Reproducibility

- Data public (paper): ALMA data acknowledged under project 2015.1.00543.S; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00543.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Full tclean/CLEAN parameters and taper values
- Missing: Astrometric correction offset maps
- Missing: Photometric catalogue inputs from ZFOURGE and CANDELS
- Data volume (inferred): Large: 18 execution blocks of a 846-pointing mosaic; hundreds of GB raw
- Score (inferred): 3/5, Public project and detection thresholds given, but imaging parameters and CASA version are missing
- Rediscovery candidate: yes, Data from a single project and detection recipe (taper, BLOBCAT thresholds) are stated, with numeric catalogue results

## Links

- Method: (cite: Hales2012) (BLOBCAT source extraction)
- Method: (cite: Marti-Vidal2012) (minimum size limit)
- Companion: Franco et al. (in prep) (further properties such as the main sequence position and SEDs)
- Related: CANDELS
- Related: ZFOURGE
- Related: HUDF ALMA (Dunlop2017)
- Related: ASPECS
- Related: JWST GTO

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 66,
  "rate": 0.71
 },
 "evidence_ok": true
}
```
