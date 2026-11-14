# Gas Fraction and Depletion Time of Massive Star-forming Galaxies at z ~ 3.2: No Change in Global Star Formation Process out to z &gt; 3

`2016ApJ...833..112S` | The Astrophysical Journal 2016 | first author: Schinnerer, E. | arXiv: 1610.03656 | DOI: 10.3847/1538-4357/833/1/112

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How do the gas fraction and gas depletion time of massive main-sequence galaxies at z~3.2 compare with expected evolution, and does the star formation process change out to z>3?  
  > "The observed evolution of the gas fraction and its associated depletion time in main sequence (MS) galaxies provides insights on how star formation proceeds over cosmic time." (abstract)
- Target **86 massive star-forming galaxies in COSMOS (45 detected at 2.8<=z<3.7 used)**: coordinates _not stated_; z/distance median z = 3.2 (photometric/spectroscopic)  
  > "we selected a sample of massive star forming galaxies in the COSMOS field to be observed with ALMA." (2.1. Sample Selection); "the median redshift of our sample is z = 3.2 with the highest redshift being z = 3.8." (2.1. Sample Selection); distance from COSMOS2015 photo-z (Laigle et al. 2016) and spectroscopic redshifts (VUDS, zCOSMOS-deep)  
  > "we selected a sample of massive star forming galaxies in the COSMOS field to be observed with ALMA." (2.1. Sample Selection); "the median redshift of our sample is z = 3.2 with the highest redshift being z = 3.8." (2.1. Sample Selection)

## Data provenance

- ALMA projects: 2013.1.00151.S
- bands: _not stated_
- frequencies and spectral setup: 240 GHz continuum; TDM mode, four SPWs at 231, 233, 247, 249 GHz  
  > "using the correlator in TDM mode with the four spectral windows centered at 231 GHz, 233 GHz, 247 GHz, and 249 GHz yielding a total bandwidth of 7.5 GHz." (2.2. ALMA Data)
- continuum bandwidth: 7.5 GHz total  
  > "yielding a total bandwidth of 7.5 GHz" (2.2. ALMA Data)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.8"x1.1" (1.7"x1.1") for fields with (without) extra time  
  > "The resolution and rms achieved is 1.8”×1.1” (1.7”×1.1”) and 66 (71) µJy/beam" (2.2. ALMA Data)
- max recoverable scale: _not stated_
- sensitivity: 66 (71) µJy/beam for 24 (62) fields with (without) additional time, natural weighting  
  > "66 (71) µJy/beam for the 24 (62) fields with (without) additional observing time when using natural weighting." (2.2. ALMA Data)
- time on source: 2.0 min per field, 24 fields with additional 0.5 min  
  > "for a total of 2.0min on-source integration time, with 24 fields receiving an additional 0.5min on-source time." (2.2. ALMA Data)
- observing dates: 25-30 December 2014  
  > "observed with typically 38 antennas between 25 and 30 of December 2014" (2.2. ALMA Data)
- pi or archival as stated: Cycle 2 program, PI Schinnerer  
  > "ALMA Cycle 2 program (2013.1.00151.S, PI Schinnerer)" (2.2. ALMA Data)
- Other facility **Spitzer/MIPS 24um and Herschel/PACS 100um**: IR fluxes/upper limits for SFR  
  > "For all objects 24µm and 100µm fluxes or upper limits were extracted from" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
- Other facility **COSMOS2015 catalog / UltraVISTA, SPLASH**: Photometry and redshifts for SED fitting  
  > "we updated the photometry and redshift determination of this initial sample based on the COSMOS2015 catalog of Laigle et al. (2016)." (2.1. Sample Selection)
- Other facility **Chandra COSMOS Legacy survey**: AGN identification via X-ray  
  > "by cross-matching with the Chandra COSMOS Legacy survey (Civano et al. 2016)" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
- External data: Gas mass vs monochromatic IR luminosity calibration (high-mass sample, Tab. 6)  
  > "Here we adopt the relations for the high-mass sample, i.e. log(M ⋆ ) > 9.0 at rest-frame 250 and 350 µm (see Tab. 6 Groves et al. 2015)" (3.1. 240 GHz Continuum Detection and Gas Mass Measurements) [from Groves et al. 2015]
- External data: 2-SFM model predictions and main sequence compilation  
  > "empirical predictions for main sequence galaxies (at our target redshift) from the 2-SFM model (Sargent et al. 2014)" (3.2. Gas Fraction and Gas Depletion Time) [from Sargent et al. 2014]
- External data: Literature gas fractions and depletion times for comparison  
  > "literature values for larger samples (Genzel et al. 2015; Bethermin et al. 2015; Scoville et al. 2016)" (3.2.2. Time Evolution) [from Genzel et al. 2015; Bethermin et al. 2015; Scoville et al. 2016]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA-provided calibrated data products used  
  > "We used the calibrated data products provided by the ALMA project." (2.2. ALMA Data)
- flux calibrator: J1058+0133, J0750+1231, J0854+201, J0825+0309, J1037-295, Ganymede, Callisto (bandpass and flux); J1010-0200 phase  
  > "for bandpass and flux calibration J1058+0133, J0750+1231, J0854+201, J0825+0309, J1037-295, Ganymede, and Callisto were observed." (2.2. ALMA Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in 'mfs' mode, all four SPWs together  
  > "We CLEANed all four spectral windows together using the ’mfs’ mode down to 3σ without setting a CLEAN box and using up to 1,000 iterations." (2.2. ALMA Data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "when using natural weighting" (2.2. ALMA Data)
- uv taper: _not stated_
- cell size: 0.18"  
  > "with a pixel size of 0.18”" (2.2. ALMA Data)
- image size: 39"x39"  
  > "The final images cover an area of 39”×39”" (2.2. ALMA Data)
- masking: no CLEAN box; clean to 3σ, up to 1,000 iterations  
  > "down to 3σ without setting a CLEAN box and using up to 1,000 iterations." (2.2. ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.8"x1.1" / 1.7"x1.1"  
  > "1.8”×1.1” (1.7”×1.1”)" (2.2. ALMA Data)
- final rms: 66 / 71 µJy/beam  
  > "66 (71) µJy/beam" (2.2. ALMA Data)

### Inherited from earlier work

- Source extraction and flux measurement method  
  > "we use the source extraction software of Karim et al. (2013) that was developed for continuum source extraction in ALMA imaging data." (3.1. 240 GHz Continuum Detection and Gas Mass Measurements) [from Karim et al. (2013)]
- PSF-fitting deblending of MIPS24/PACS100 fluxes  
  > "using the PSF fitting method of Magnelli et al. (2013)" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation) [from Magnelli et al. (2013)]
- IR stacking and dust SED fit methodology  
  > "We use the methodology of Magnelli et al. (2014) as used for Genzel et al. (2015)" (3.1. 240 GHz Continuum Detection and Gas Mass Measurements) [from Magnelli et al. (2014); Genzel et al. (2015)]

### Not stated but needed to reproduce (our reading)

- Exact MagPhys priors/configuration and the version of the high-z code
- Sample catalog with target IDs, positions and redshifts
- Karim et al. (2013) extraction parameters beyond the 2.5σ threshold
- Handling of CMB contrast and flux-calibration uncertainty
- Details of the main-sequence offset compensation and median error calculation
- How the high-mass Groves coefficients were interpolated beyond the given equation, and K-correction of the 240 GHz flux
- Stacking details for the IR SED (apertures, bins)

## Analysis recipe

1. **Image ALMA 240 GHz continuum**: CLEAN of ALMA-calibrated data, all SPWs in mfs mode, natural weighting  
  > "We CLEANed all four spectral windows together using the ’mfs’ mode down to 3σ" (2.2. ALMA Data)
   - software: CASA (implied; not named)
   - parameter: pixel 0.18", image 39"x39", up to 1000 iterations  
  > "The final images cover an area of 39”×39” with a pixel size of 0.18”" (2.2. ALMA Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect sources and measure fluxes**: Blind extraction identifying sources at >=2.5σ with 3- vs 6-parameter Gaussian fits; integrated fluxes from 6-parameter fit; detections at >=3σ peak  
  > "The software automatically identifies sources at ≥ 2.5σ and determines the flux based on a comparison of a three (assuming an unresolved source) and six parameter (assuming a resolved source) Gauss fit in the image plane." (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
   - software: Karim et al. (2013) extraction software
   - fitting: Gaussian fits in image plane  
  > "comparison of a three (assuming an unresolved source) and six parameter (assuming a resolved source) Gauss fit in the image plane" (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
   - validation: Checked consistency for unresolved sources, Gaussian fits at optical/NIR positions, and spurious source probability  
  > "We further tested that Gaussian fits at the position of the optical/near-IR sources result in similar values." (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
3. **Derive stellar mass and SFR**: MagPhys SED fits to COSMOS2015 3" photometry plus IR+ALMA fluxes; ALMA non-detections and PACS as upper limits; MIPS24 excluded  
  > "including our measured IR+ALMA fluxes and assuming the best available redshifts, with the MagPhys code (da Cunha et al. 2008)" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
   - software: MagPhys
   - parameter: Bruzual & Charlot (2003) libraries, high-z MagPhys version  
  > "we use the Bruzual & Charlot (2003) stellar libraries and the latest ”high z” version of the code" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
   - assumption: Chabrier IMF; H0=70, OmegaM=0.3, OmegaL=0.7  
  > "use a Chabrier initial mass function for the stellar mass and SFR determination." (1. Introduction)
   - fitting: Bayesian SED fitting  
  > "The use of the Bayesian SED fitting code MagPhys" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
   - validation: Average SFR and SED consistent with stacked IR SED  
  > "We verified that our average SFR is consistent with the mean and median SFR determined from the stacked IR SED" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
4. **Convert 240 GHz flux to gas mass**: Groves et al. (2015) monochromatic luminosity-gas mass relation, coefficients interpolated to rest-frame wavelength (Eq. 1)  
  > "linearly interpolate the coefficients to match the observed" (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
   - parameter: high-mass sample, log(M*)>9.0, 250 and 350 µm relations  
  > "the relations for the high-mass sample, i.e. log(M ⋆ ) > 9.0 at rest-frame 250 and 350 µm" (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
   - assumption: Metallicities of massive galaxies at z~3 consistent with local objects of similar mass  
  > "we assume that the metallicities of massive galaxies at our epoch of interest are broadly consistent with local objects of similar masses." (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
   - fitting: _not stated_
   - validation: Compared with Scoville et al. (2014) gas masses and with stacked IR SED gas masses (Magnelli 2014 method, Draine & Li model, Leroy 2011 dust-to-gas)  
  > "We verified that gas masses derived using the Scoville et al. (2014) prescription are consistent with our results within the (systematic) uncertainties." (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
5. **Compute gas fraction and depletion time and compare with 2-SFM**: mu_gas = Mgas/M*, t_depl = Mgas/SFR for 45 detections at 2.8<=z<4; medians with 1σ error on median; compare to 2-SFM, literature, and MS offset  
  > "gas fraction, defined as µ gas = M gas /M ⋆ and gas depletion time, defined as t depl. = M gas /SFR." (3.2. Gas Fraction and Gas Depletion Time)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MagPhys** high-z version: Stellar mass and SFR from SED fitting  
  > "with the MagPhys code (da Cunha et al. 2008)" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
- **LePhare** : Photometric redshifts and masses (catalog)  
  > "The photometric redshifts are determined using the template-fitting LePhare code" (2.1. Sample Selection)
- **Karim et al. (2013) source extraction software** : Blind continuum source extraction in ALMA images  
  > "we use the source extraction software of Karim et al. (2013)" (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ALMA detections at >=3σ among 86 targets | 47 | not stated | sources | 2 | A total of 47 of our 86 targeted |
| Median gas fraction mu_gas | 1.65 | +0.19/-0.18 | dimensionless | 5 | median gas fraction of µ gas = M gas /M ⋆ = 1.65 |
| Median depletion time | 0.68 | +0.08/-0.07 | Gyr | 5 | median gas depletion time t depl. (Gyr) = M gas /SFR = 0.68 |
| Mean log gas mass, IR-SED stacking vs monochromatic | 10.89 vs 10.84 | not stated | log(Msun) | 4 | is remarkably similar to the mean gas mass from the mono-chromatic |
| Mean log stellar mass of 45 sample | 10.7 | not stated | log(Msun) | 3 | a mean stellar mass of ⟨log(M ⋆ [M ⊙ ])⟩ = 10.7 |
| Mean log sSFR | -8.6 | not stated | log(yr^-1) | 3 | log(sSFR[yr [−][1] ]) = −8.6 |
| 3σ gas mass completeness limit at z~3.2 | 10.48 | not stated | log(Msun) | 4 | log(M gas [M ⊙ ]) = 10.48 |

## Qualitative findings

- Gas fraction and depletion time flatten beyond z~2.5, consistent with the 2-SFM prediction; z~3 MS galaxies follow the same SFR-gas mass relation as lower redshift galaxies.  
  > "consistent with the expected flattening of the µ gas (z) curve at z ≳ 2.5 in the 2-SFM model" (3.2.2. Time Evolution)

## Claim tuples

- H: Gas fractions and depletion times of z~3.2 MS galaxies follow the flattening predicted by the 2-SFM | E: 240 GHz dust continuum gas masses with MagPhys M* and SFR for 45 galaxies | R: median mu_gas=1.65, t_depl=0.68 Gyr | F: Consistent with 2-SFM flattening | **supported**
- H: A single SFR-gas mass relation holds out to z>3 | E: Placed detections on the SFR vs gas mass plane | R: z~3 MS galaxies occupy same space as 1.2<z<2.5 objects | F: No change in global star formation process out to z>3 for MS galaxies | **supported**
- H: Gas fraction depends on location within the MS while depletion time does not strongly | E: Compared mu_gas and t_depl with sSFR offset | R: Clear trend of mu_gas, mild trend of t_depl | F: Consistent with previous studies and 2-SFM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust continuum allows sizable samples quickly, since CO would require long integrations  
  > "The only possibility to quickly assemble sizable samples is to use the large bandwidth available for continuum detections" (1. Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Metallicity evolution could make gas masses underestimated by ~0.3 dex  
  > "our determinations for the gas mass of our sample are likely underestimated (by approximately 0.3 dex)" (3.1. 240 GHz Continuum Detection and Gas Mass Measurements)
- Limitation (authors): Individual SFRs have systematic uncertainties from poor rest-frame IR sampling  
  > "the SFRs of individual sources will suffer from the usual (systematic) uncertainties" (2.3. Stellar Mass and Star Formation Rate (SFR) Estimation)
- Caveat (inferred, ours): Only detections are used, causing selection bias toward high gas mass
- Caveat (inferred, ours): Gas masses rely on local calibration and an assumed local metallicity
- Caveat (inferred, ours): Sparse IR SED sampling makes individual SFRs uncertain
- Caveat (inferred, ours): Single-band 240 GHz continuum, no CO validation

## Reproducibility

- Data public (paper): Data cited with ALMA project code; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00151.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Target list with coordinates and IDs
- Missing: MagPhys configuration
- Missing: Exact Karim et al. extraction settings
- Missing: Photometry catalog subset and IR flux remeasurements
- Data volume (inferred): ~10-50 GB for 86 short continuum fields; plus public COSMOS catalogs
- Score (inferred): 3/5, ALMA project given and simple imaging, but SED fitting setup, target catalog and extraction parameters are not given.
- Rediscovery candidate: no, Results depend on MagPhys SED fits and ancillary multi-wavelength photometry that are not fully specified.

## Links

- Method: Groves et al. 2015 (Gas mass vs monochromatic IR luminosity calibration)
- Method: Karim et al. 2013 (ALMA source extraction software)
- Method: da Cunha et al. 2008 (MagPhys SED fitting)
- Companion: Sargent et al. 2014 (2-SFM framework compared against)
- Companion: Scoville et al. 2016 (Comparable dust continuum gas mass results)
- Related: COSMOS
- Related: VUDS
- Related: KINGFISH

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 78,
  "stated": 51,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
