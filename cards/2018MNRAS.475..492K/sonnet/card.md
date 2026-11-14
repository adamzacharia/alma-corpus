# ALMACAL - III. A combined ALMA and MUSE survey for neutral, molecular, and ionized gas in an H I-absorption-selected system

`2018MNRAS.475..492K` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Klitsch, A. | arXiv: 1712.00014 | DOI: 10.1093/mnras/stx3184

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, nearby_galaxies
- Question: What is the origin of the Lyα/LLS absorption at z=0.633 towards J0423-0130: which galaxies (and their molecular, ionised gas content) are associated with it?  
  > "The immediate aim of this study is to identify the origin of the absorption seen towards the quasar." (1 INTRODUCTION)
- Target **J0423-0130 field (absorber z=0.633; galaxies J0423A-D)**: coordinates 04h23m15.8s -01d20m33s  
  > "(04h23m15.8s −01d20m33s, _z_ = 0.915)" (2 OBSERVATIONS AND DATA REDUCTION); z/distance z_QSO = 0.915; absorber z = 0.633  
  > "(04h23m15.8s −01d20m33s, _z_ = 0.915)" (2 OBSERVATIONS AND DATA REDUCTION); distance from cosmology H0=70, OmegaM=0.3, OmegaL=0.7  
  > "(04h23m15.8s −01d20m33s, _z_ = 0.915)" (2 OBSERVATIONS AND DATA REDUCTION)

## Data provenance

- ALMA projects: 2015.1.00920.S, 2015.1.00262.S, 2012.1.00350.S, 2013.1.00403.S, 2013.1.00111.S, 2013.1.01175.S, 2013.1.01225.S, 2012.1.00146.S, 2015.1.00350.S, 2013.1.00198.S, 2013.1.01172.S, 2013.1.00815.S, 2013.1.00710.S, 2016.1.00724.S, 2016.1.00683.S, 2016.1.00627.S, 2016.1.01453.S, 2016.1.01262.S, 2015.1.00296.S, 2012.1.00650.S
- bands: Band 4 (12CO(2-1)) and Band 6 (12CO(3-2) and continuum)  
  > "Two observations are available in Band 4 covering the frequency of the redshifted 12CO(2–1) emission line and two observations in Band 6 covering the frequency of the redshifted 12CO(3–2) emission line." (2.1 ALMACAL)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.43" (Band 4), 0.70" (Band 6 cube), 0.75" (continuum) median  
  > "the median angular resolution of the final data cube is ∼ 0.70 ′′ . The r.m.s. noise level in the 1.2 mm continuum image is ∼ 96 mJy beam −1 km s −1 and the median angular resolution is ∼ 0.75 ′′ ." (2.1 ALMACAL)
- max recoverable scale: _not stated_
- sensitivity: 0.28 mJy/beam per 66 km/s (Band 4); 0.37 mJy/beam per 44 km/s (Band 6)  
  > "4 141.166 0.43 0.28 66 48" (Table 2)
- time on source: 1333 s in Band 4 and 605 s in Band 6 for the CO observations  
  > "The total integration time is 1333 s in Band 4 and 605 s in Band 6 for the observations covering the 12CO emission lines." (2.1 ALMACAL)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 12CO J=3-2 (not stated)
- Other facility **VLT/MUSE (DDT, ESO 298.A5017)**: IFU data identifying four galaxies at absorber redshift; [OII], [OIII], Hβ fluxes  
  > "under programme ESO 298.A5017 at the European Southern Observatory using MUSE at the Nasmyth focus of the 8.2 m Very Large Telescope UT4." (2.2 New MUSE Observations)
- Other facility **MDM 2.4m (Rao et al. 2011 images)**: B,R,I,J,H,K broad-band imaging for photometry and SED fitting  
  > "we use the broad-band imaging from Rao et al. (2011) to measure the broad-band photometry which we use as input for the spectral energy distribution (SED) fitting." (3.3 Broad-band Photometry and Stellar Mass)
- Other facility **Keck/HIRES**: high-resolution quasar spectrum (Churchill et al. 1996) for Voigt fitting  
  > "we use the quasar spectrum presented by Churchill et al. (1996) to fit the absorption lines" (Appendix B)
- External data: HI column density log N(HI)=18.54 from HST/STIS  
  > "The HI column density was determined to be log( _N_ (HI)/ atoms cm −2 ) = 18.54" (2.3.2 Quasar Spectroscopy) [from Rao et al. (2006)]
- External data: Broad-band images of the field  
  > "we use the broad-band imaging from Rao et al. (2011) to measure the broad-band photometry" (3.3 Broad-band Photometry and Stellar Mass) [from Rao et al. (2011)]
- External data: HIRES quasar spectrum  
  > "we use the quasar spectrum presented by Churchill et al. (1996) to fit the absorption lines" (Appendix B) [from Churchill et al. (1996)]
- External data: Starburst template spectra used to derive LFIR  
  > "We use a set of template spectra for starburst galaxies from Polletta et al. (2007)" (3.5 Star-Formation Rates) [from Polletta et al. (2007)]

## Processing

### Calibration

- pipeline or manual: CASA calibration and reduction of ALMACAL calibrator data, additional interactive flagging in uv plane  
  > "We carry out the calibration and data reduction using the Common Astronomy Software Applications (CASA) software package version 4.7." (2.1 ALMACAL)
- casa version: CASA 4.7  
  > "software package version 4.7" (2.1 ALMACAL)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% on integrated line flux  
  > "to be 5% based on the expected accuracy of the flux calibration." (3.1 ALMA Source Detection and Flux Measurement)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "the imaging was done using the standard ‘clean’ algorithm." (2.1 ALMACAL)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "A ‘robust’ weighting scheme was applied, using a Briggs parameter of 0.5" (2.1 ALMACAL)
- uv taper: 0.5" outer taper in Band 4  
  > "therefore we use an outer taper of 0.5 ′′ to prevent too high a weighting of the higher resolution data." (2.1 ALMACAL)
- cell size: 0.15" Band 4; 0.24" Band 6 CO(3-2) cube; 0.15" Band 6 continuum  
  > "We use a pixel size of 0.15 ′′ in the Band 4 image cube, 0.24 ′′ in the Band 6 image cube covering the 12 CO(3–2) emission line" (2.1 ALMACAL)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub with linear fit to spectrum  
  > "We have subtracted the continuum from the image cube using the task imcontsub with a linear fit to the spectrum." (3.1 ALMA Source Detection and Flux Measurement)
- line free channels: _not stated_
- primary beam correction: impbcor on cube before spectral extraction  
  > "we perform a primary beam correction on the image cube using impbcor" (3.1 ALMA Source Detection and Flux Measurement)
- array combination: concatenate the two datasets in each band  
  > "Before the imaging, we concatenate the two datasets in each band." (2.1 ALMACAL)
- smoothing: channel width reduced to 15.625 kHz, Hanning smoothing (66 and 44 km/s)  
  > "We reduce the spectral resolution to a maximum of 15.625 kHz." (2.1 ALMACAL)
- final beam: _not stated_
- final rms: 0.28 mJy/beam (66 km/s) Band 4; 0.37 mJy/beam (44 km/s) Band 6; 96 mJy/beam km/s continuum  
  > "The r.m.s. noise level in the Band 6 image cube is ∼ 0.37 mJy beam −1 per 44 km s −1" (2.1 ALMACAL)

### Inherited from earlier work

- Retrieval and calibration of ALMACAL calibrator data  
  > "The retrieval and calibration of the ALMA calibrator data are described in detail by Oteo et al. (2016)." (2.1 ALMACAL) [from Oteo et al. (2016)]
- MUSE flux error ±10% based on previous experience  
  > "so we estimate the flux error to be ±10% based on our previous experience (Rahmani et al. 2017; P´eroux et al. 2017)." (2.2 New MUSE Observations) [from Rahmani et al. 2017; Péroux et al. 2017]

### Not stated but needed to reproduce (our reading)

- Exact clean parameters (niter, threshold, masks, deconvolver)
- Line-free channels used for continuum subtraction
- Whether continuum image weighting/robust differs and which channels excluded
- SoFiA parameter file details other than kernels and 4 sigma threshold
- Which ALMA datasets for each band are concatenated and calibrators/pipeline steps in ALMACAL (in Oteo et al. 2016)
- Dust-correction details (A_Halpha values) and Le Phare template set
- Polletta template selection for LFIR

## Analysis recipe

1. **Image ALMACAL cubes and continuum**: CASA concatenation, Hanning smoothing, clean with Briggs weighting; Band 4 taper  
  > "A ‘robust’ weighting scheme was applied, using a Briggs parameter of 0.5" (2.1 ALMACAL)
   - software: CASA
   - parameter: robust 0.5; 0.5" taper in Band 4  
  > "we use an outer taper of 0.5 ′′ to prevent too high a weighting of the higher resolution data." (2.1 ALMACAL)
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind search for CO emission**: SoFiA Smooth+Clip finder on non-primary-beam-corrected cubes, within ±2000 km/s of absorber redshift  
  > "The detection threshold is 4σ for both data cubes." (3.1 ALMA Source Detection and Flux Measurement)
   - software: SoFiA
   - parameter: twelve spatial kernels 0.7"-4.2"; spectral kernels 66-990 km/s (B4), 44-660 km/s (B6)  
  > "We use twelve smoothing kernels between 0.7 ′′ and 4.2 ′′ in the spatial dimension" (3.1 ALMA Source Detection and Flux Measurement)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure line fluxes, redshift, size, luminosities**: Primary beam correction, continuum subtraction, integrate over 2x FWHM, 2D Gaussian size fit; L' via Solomon et al. 1992 equation  
  > "The flux is measured by integrating the spectra over two times the FWHM indicated by the yellow shaded region" (3.1 ALMA Source Detection and Flux Measurement)
   - software: CASA
   - parameter: flux error 5%  
  > "to be 5% based on the expected accuracy of the flux calibration." (3.1 ALMA Source Detection and Flux Measurement)
   - fitting: 2D Gaussian to integrated intensity maps  
  > "We determine the size of the emission by fitting a twodimensional Gaussian function to the integrated intensity mapdf." (3.1 ALMA Source Detection and Flux Measurement)
   - validation: _not stated_
4. **Molecular gas mass**: M_mol = alpha_CO x L'CO(1-0), with L'(2-1)/L'(1-0)=0.9 and LIRG alpha_CO=0.6; Milky Way alpha_CO=4.3 for range  
  > "we use α CO = 0.6M⊙(K km s −1 pc 2 ) −1, appropriate for LIRGs derived by Papadopoulos et al. (2012b) including a factor of 1.36 to account for the presence of helium." (3.4 Molecular Gas Mass)
   - assumption: LIRG-type excitation ratio 0.9 and alpha_CO=0.6; MW alpha_CO=4.3 incl. helium  
  > "we adopt a conversion factor of L CO ′ (2−1) / L CO ′ (1−0) = 0.9" (3.4 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: Compared with MW-type alpha_CO to bracket mass  
  > "so we adopt a molecular gas mass of 1 − 9 × 10 10 M⊙." (3.4 Molecular Gas Mass)
5. **Continuum flux and FIR-based SFR**: Combine Band 6 datasets lacking CO(3-2); scale Polletta starburst templates to 1.2 mm flux, integrate 8-1000 µm, apply Kennicutt (1998)  
  > "The fitted spectrum is then integrated in the wavelength range from 8 - 1000 µm to obtain the total far-infrared luminosity" (3.5 Star-Formation Rates)
   - assumption: median SFR from set of template spectra  
  > "we use the median SFR from a set of template spectra which we scale to the flux at 1.2 mm." (3.5 Star-Formation Rates)
   - fitting: template scaling  
  > "We use a set of template spectra for starburst galaxies from Polletta et al. (2007) which we scale to the observed 1.2 mm flux converted to the rest wavelength." (3.5 Star-Formation Rates)
   - validation: Compared with dust-uncorrected [OII] SFR (13-25 times lower)  
  > "This is 13 - 25 times lower than the SFR inferred from the far-infrared luminosity." (3.5 Star-Formation Rates)
6. **Detect MUSE galaxies, stellar masses, SFRs, kinematics, metallicity**: MUSELET source finding; Le Phare SED fitting; Galfit and GalPaK3D on [OIII]; R23 / mass-metallicity relation; VPFIT of absorber  
  > "This broad-band photometry is used as input for the SED fitting with Le Phare" (3.3 Broad-band Photometry and Stellar Mass)
   - software: MUSELET/MPDAF, SExtractor, Le Phare, Galfit, GalPaK3D, VPFIT
   - parameter: GalPaK3D MCMC chain of 15,000 runs, 10 parameters  
  > "It probes the posterior possibility density distribution via an MCMC chain of 15, 000 runs" (Appendix A)
   - fitting: chi2 minimisation (Le Phare, VPFIT); MCMC (GalPaK3D)  
  > "filter functions and a χ [2] minimization is performed." (3.3 Broad-band Photometry and Stellar Mass)
   - validation: Galfit vs GalPaK3D PA comparable within errors  
  > "Comparing the PA derived with Galpak 3D with the PA from the 2D fitting with Galfit we find that they are comparable within the errors." (Appendix A)
7. **Group dynamics and absorber origin**: Projected mass estimator and zero-velocity surface radius; outflow travel time at 300 km/s  
  > "we use the ‘projected mass estimator’ (Heisler et al. 1985)" (4.3 The Nature of the Absorbing Gas)
   - assumption: group age 7.5 Gyr; wind speed 300 km/s; group centre = most massive galaxy  
  > "We assume that the age of the group is 7.5 Gyr, which is the age of the universe at the redshift of the group." (4.3 The Nature of the Absorbing Gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: calibration, imaging, impbcor, imcontsub, immoments  
  > "Common Astronomy Software Applications (CASA) software package version 4.7." (2.1 ALMACAL)
- **SoFiA** : source finding in ALMA cubes  
  > "using the Source Finding Application ( SoFiA ) 1 (Serra et al. 2015)" (3.1 ALMA Source Detection and Flux Measurement)
- **ESO MUSE pipeline** v1.6.1: MUSE data reduction  
  > "We reduce the data with v1.6.1 of the ESO MUSE pipeline" (2.2 New MUSE Observations)
- **ZAP** : sky subtraction  
  > "use the Zurich Atmosphere Purge (ZAP) code for the sky subtraction (Soto et al. 2016)" (2.2 New MUSE Observations)
- **MUSELET/MPDAF** : MUSE source detection  
  > "MUSELET source finding algorithm included in MPDAF" (3.2 MUSE Source detection and Flux Measurement)
- **SExtractor** : source finding and photometry  
  > "The apparent magnitudes of the detected galaxies are determined using SExtractor" (3.3 Broad-band Photometry and Stellar Mass)
- **Le Phare** : SED fitting for stellar masses  
  > "SED fitting with Le Phare" (3.3 Broad-band Photometry and Stellar Mass)
- **Galfit** : Sersic fit of [OIII] pseudo-narrow-band image  
  > "we perform a Sersic-fit of the [OIII] pdfeudo-narrow-band image using Galfit" (Appendix A)
- **GalPaK3D** : 3D morpho-kinematic fit of [OIII] cube  
  > "to perform a 3D morphokinematic fit to the [OIII] emission line cube." (Appendix A: Morphology and Kinematics)
- **VPFIT** v.10.2: Voigt profile fits of absorption lines  
  > "profiles using VPFIT 4 v.10.2." (Appendix B)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (ACKNOWLEDGEMENTS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO(2-1) integrated flux of J0423B | 3.6 | 0.2 | Jy km/s | 3 | 12 CO(2–1) 0.63317 8.4 ± 0.7 3.6 ± 0.2 1.9 ± 0.1 590 ± 30 |
| 12CO(3-2) integrated flux of J0423B | 5.2 | 0.3 | Jy km/s | 3 | 12 CO(3–2) 0.63335 10 ± 1 5.2 ± 0.3 1.2 ± 0.1 610 ± 40 |
| 1.2 mm continuum total flux density | 0.8 | 0.2 | mJy | 5 | The total flux density at 1.2 mm is (0.8 ± 0.2) mJy |
| L'CO(3-2)/L'CO(2-1) | 0.63 | 0.09 | dimensionless | 3 | The ratio of L CO ′ (3−2) / L CO ′ (2−1) is 0.63 ± 0.09 |
| Molecular gas mass (LIRG alpha_CO) | 1.27e10 | 0.07e10 | Msun | 4 | This yields a molecular gas mass of M mol = (1.27 ± 0.07) × 10 10 M⊙. |
| FIR-based SFR of J0423B | 50 | 10 | Msun/yr | 5 | we estimate a SFR of (50 ± 10) M⊙ yr −1 |
| Dust-uncorrected [OII] SFR of J0423B | 2.7 | 0.3 | Msun/yr | 6 | We derive a SFR of 2.7 ± 0.3 M⊙ yr −1 from the [OII] emission. |
| Dynamical mass of group | 10^12.9 | not stated | Msun | 7 | This yields a dynamical mass of the group of 10 12.9 M⊙. |
| Zero-velocity surface radius | 1.2 | not stated | Mpc | 7 | This yields a radius of the zerovelocity surface of 1.2 Mpc. |
| MUSE limiting SFR (field / at quasar) | 0.2 / 0.3 | not stated | Msun/yr | 6 | This yields a non-dust-corrected limiting SFR of 0.3 M⊙ yr −1 . |
| Stellar mass of J0423B | 11.2 | 0.1 | log Msun | 6 | J0423B 0.63312 ± 0.00048 50 ± 10 11.2 ± 0.1 9.1 ± 0.9 b |

## Qualitative findings

- The CO source J0423B is the most massive of four galaxies at the absorber redshift forming a group, likely a LIRG.  
  > "The 12 CO emission line detections originate from the most massive galaxy in this group." (abstract)

## Claim tuples

- H: Is the CO-detected galaxy a LIRG-like ISM? | E: CO line ratio and FIR vs [OII] SFR comparison | R: L'(3-2)/L'(2-1)=0.63±0.09; FIR SFR 13-25 times [OII] SFR | F: J0423B is likely a LIRG | **supported**
- H: Could an undetected galaxy near the sightline cause the absorption? | E: MUSE [OII] limiting SFR | R: limit 0.2 (field) and 0.3 Msun/yr at quasar | F: cannot be ruled out completely but unlikely | **partially**
- H: Does the absorber trace an outflow or intra-group gas? | E: Kinematic alignment, outflow travel time, group dynamics | R: all galaxies within ±250 km/s; travel time ~430 Myr | F: intra-group gas is the most probable explanation, outflow also possible | **partially**

## Reasoning

- Why this data: Source chosen because two CO lines are detected in ALMACAL data.  
  > "We choose this source for our pilot study, because we detect two 12 CO emission lines in our ALMACAL data." (2 OBSERVATIONS AND DATA REDUCTION)
- Why this method: _not stated_
- Alternative: Milky Way-type CO excitation and alpha_CO considered but LIRG-type preferred  
  > "we believe that the LIRG-type conversion factor is more appropriate." (3.4 Molecular Gas Mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity resolution coarse for molecular absorption; kinematic velocity field sampled by only three resolution elements  
  > "The velocity field is sampled with only three resolution elements across the major axis" (Appendix A)
- Caveat (inferred, ours): Single system; conclusions on absorber origin are qualitative
- Caveat (inferred, ours): FIR SFR depends on template choice with a single 1.2 mm point
- Caveat (inferred, ours): CO(3-2) at 19.4" lies beyond Band 6 primary beam FWHM, large correction
- Caveat (inferred, ours): alpha_CO uncertainty gives order-of-magnitude mass range

## Reproducibility

- Data public (paper): ALMA calibrator data from archive; MUSE from ESO programme  
  > "In §2 we describe our dataset from the ALMA archive, the new MUSE observations" (1 INTRODUCTION)
- Products in archive: _not stated_
- Missing: Rao et al. 2011 broad-band images (provided privately)
- Missing: Reduced HIRES spectrum (provided privately)
- Missing: ALMACAL calibration details
- Missing: clean parameters
- Data volume (inferred): ~50-200 GB for the ALMA calibrator datasets (20 projects, mostly short scans)
- Score (inferred): 3/5, ALMA data public and main steps described, but imaging details and some inputs (private images/spectrum, ALMACAL pipeline) are missing.
- Rediscovery candidate: no, Requires ALMACAL processing from other paper and non-public ancillary data.

## Links

- Method: Oteo et al. (2016) (ALMACAL survey retrieval and calibration)
- Method: Serra et al. (2015) (SoFiA source finder)
- Method: Bouché et al. (2015) (GalPaK3D)
- Companion: Oteo et al. (2016) (ALMACAL I survey description)
- Related: ALMACAL
- Related: COS-Halos

## Checks

```json
{
 "quotes": 102,
 "quotes_ok": 102,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 20,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 65,
  "rate": 0.691
 },
 "evidence_ok": true
}
```
