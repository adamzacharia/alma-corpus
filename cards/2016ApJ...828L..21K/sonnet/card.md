# A Resolved Map of the Infrared Excess in a Lyman Break Galaxy at z = 3

`2016ApJ...828L..21K` | The Astrophysical Journal Letters 2016 | first author: Koprowski, M. P. | arXiv: 1608.05080 | DOI: 10.3847/2041-8205/828/2/L21

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: _not stated_
- Target **SSA22a-C16 (detected) and nine other SSA22 LBGs**: coordinates SSA22a-C16: 22 17 31.95 +00 13 16.1 (J2000)  
  > "SSA22a-C16 22 17 31.95 +00 13 16.1 3.065" (Table 1); "Our sample is taken from the Steidel et al. (2003) LBG redshift survey of the SSA22 field" (2.1 Targets); z/distance z_spec = 3.065 (C16); sample z~3.1  
  > "SSA22a-C16 22 17 31.95 +00 13 16.1 3.065" (Table 1); "Our sample is taken from the Steidel et al. (2003) LBG redshift survey of the SSA22 field" (2.1 Targets); distance from Keck/LRIS spectroscopic redshifts  
  > "SSA22a-C16 22 17 31.95 +00 13 16.1 3.065" (Table 1); "Our sample is taken from the Steidel et al. (2003) LBG redshift survey of the SSA22 field" (2.1 Targets)

## Data provenance

- ALMA projects: 2013.1.00362.S
- bands: Band 7 (870 um)  
  > "The ALMA Band 7 observations were taken between 2014 June 30 and 2015 April 29" (2.2 Atacama Large Millimeter/Submillimeter Array)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~450-500 mas; beam 0.46" x 0.44"  
  > "The ALMA synthesized beam of 0 _._ 46 _[00]_ _⇥_ 0 _._ 44 _[00]_ (PA=-33.32 degrees)" (Figure 1 caption)
- max recoverable scale: _not stated_
- sensitivity: target 1 sigma = 50 uJy/beam  
  > "the target 1 _σ_ noise for a 1 _[00]_ beam was _σ_ = 50 _µ_ Jy beam _[−]_ [1] ." (2.2. Atacama Large Millimeter/Submillimeter Array)
- time on source: 1073 s per target, four SBs  
  > "The observations were split into four scheduling blocks (SBs) with each target being observed for 1073 seconds." (2.2 Atacama Large Millimeter/Submillimeter Array)
- observing dates: 2014 June 30 to 2015 April 29  
  > "The ALMA Band 7 observations were taken between 2014 June 30 and 2015 April 29" (2.2 Atacama Large Millimeter/Submillimeter Array)
- pi or archival as stated: _not stated_
- Other facility **HST ACS F814W**: rest-frame UV map  
  > "With Hubble Space Telescope Advanced Camera for Surveys I -band imaging we map the rest-frame UV emission on the same scale as the dust" (abstract)
- Other facility **CFHT, Subaru, Spitzer-IRAC**: UV to mid-IR photometry for SED fitting  
  > "including CFHT, Subaru (Hayashino et al. 2004; Matsuda et al. 2011; Yamada et al. 2012; Kubo et al. 2013) and Spitzer -IRAC (Webb et al. 2009) imaging" (3.1 Spectral energy distribution fitting)
- Other facility **Keck/LRIS**: spectroscopic redshifts  
  > "spectroscopic redshifts have been obtained using the Low Resolution Imaging Spectrometer (LRIS) on Keck" (2.1 Targets)
- External data: LBG sample and redshifts in SSA22  
  > "Our sample is taken from the Steidel et al. (2003) LBG redshift survey of the SSA22 field" (2.1 Targets) [from Steidel et al. (2003)]
- External data: Dust temperature 37 K from stacked Herschel+SCUBA-2 LBG SED  
  > "Our choice of _T_ d = 37 K is based on a stacked _Herschel_ +SCUBA-2 SED of 1000s of LBGs at _z_ _⇠_ 3 from Coppin et al. (2015)." (3.1. Spectral energy distribution fitting) [from Coppin et al. (2015)]
- External data: SFR calibration constants K_UV and K_8-1000  
  > "following Madau & Dickinson (2014), with SFR UV = _K_ UV _⇥_ _L_ 1500" (3.2. Infrared Excess) [from Madau & Dickinson (2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.4.0  
  > "The data were reduced and imaged using the Common Astronomy Software Application ( CASA ) version 4.4.0" (2.2 Atacama Large Millimeter/Submillimeter Array)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune or J2148+0657; 5-10% absolute flux uncertainty  
  > "Neptune or quasar J2148+0657 were used as flux calibrators (with a 5-10% uncertainty on the absolute flux calibration)" (2.2 Atacama Large Millimeter/Submillimeter Array)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "To image the visibilities we used the CASA clean task with natural weighting to maximize the signal-to-noise." (2.2 Atacama Large Millimeter/Submillimeter Array)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "To image the visibilities we used the CASA clean task with natural weighting to maximize the signal-to-noise." (2.2 Atacama Large Millimeter/Submillimeter Array)
- uv taper: 0.8" taper for the stack  
  > "bilities are imaged using same clean procedure as above, but applying a 0.8 _[00]_ taper." (2.2. Atacama Large Millimeter/Submillimeter Array)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.46" x 0.44", PA -33.32 deg  
  > "The ALMA synthesized beam of 0 _._ 46 _[00]_ _⇥_ 0 _._ 44 _[00]_ (PA=-33.32 degrees)" (Figure 1 caption)
- final rms: _not stated_

### Inherited from earlier work

- SFR conversion factors  
  > "following Madau & Dickinson (2014), with SFR UV = _K_ UV _⇥_ _L_ 1500" (3.2. Infrared Excess) [from Madau & Dickinson (2014)]
- Thermal dust emission model  
  > "thermal dust emission uses the model of Casey et al. (2012)" (3.1 Spectral energy distribution fitting) [from Casey et al. (2012)]

### Not stated but needed to reproduce (our reading)

- Phase/bandpass calibrator names other than J2148+0657 and which SBs used which flux calibrator
- Clean threshold, niter, cell and image size, masking
- Method for measuring integrated flux density and uncertainty (aperture or fit)
- Stacking method details and weights
- Photometry values and CIGALE module parameters (burst ages, metallicity, etc.)
- UV luminosity measurement and conversion of HST flux per pixel
- Array configuration/baseline range and number of antennas
- Spectral setup and continuum bandwidth

## Analysis recipe

1. **Calibrate and image ALMA Band 7 data**: CASA calibration, natural-weighted clean; detect one target at 4 sigma  
  > "Only one target is detected (SSA22a-C16 at z = 3.065 ) with a peak significance of 4 σ ." (2.2 Atacama Large Millimeter/Submillimeter Array)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack non-detections and test resolution**: uv-plane stack of nine non-detections with 0.8" taper; amplitude vs uv-distance fit by Gaussian vs flat  
  > "We stack the nine non-detections in the uv -plane to measure the average flux density of these sources." (2.2 Atacama Large Millimeter/Submillimeter Array)
   - software: CASA
   - parameter: bins of 150 kλ  
  > "evaluated in bins of 150 k λ ." (Figure 2 caption)
   - fitting: Gaussian FWHM 0.94" vs flat profile  
  > "The χ 2 difference between the Gaussian model and a flat profile corresponds to 4.7 σ ." (2.2 Atacama Large Millimeter/Submillimeter Array)
   - validation: 4.7 sigma preference for Gaussian  
  > "The χ 2 difference between the Gaussian model and a flat profile corresponds to 4.7 σ ." (2.2 Atacama Large Millimeter/Submillimeter Array)
3. **SED fitting for L_IR and beta**: CIGALE fit to UV-mid-IR photometry plus ALMA flux; BC03, double-burst SFH, Chabrier IMF, Calzetti extinction, Casey et al. dust  
  > "We use stellar population templates from Bruzual & Charlot (2003) with the double-burst star formation history and a Chabrier (2003) initial mass function." (3.1 Spectral energy distribution fitting)
   - software: CIGALE
   - parameter: alpha=2.0, gamma=1.6, Td=37 K fixed  
  > "were fixed at 2.0, 1.6 and 37 K respectively" (3.1 Spectral energy distribution fitting)
   - assumption: Dust parameters varied alpha=1.5-2.5, gamma=1.2-2.0, Td=27-47 K for systematic of 0.14 dex  
  > "This resulted in the additional systematic uncertainty of 0.14 dex in the integrated infrared luminosity." (3.1 Spectral energy distribution fitting)
   - fitting: CIGALE best-fit, reduced chi2 = 0.49 for C16  
  > "with reduced χ 2 = 0.49 (black solid line)" (Figure 3)
   - validation: _not stated_
4. **Derive integrated IRX, SFR and beta**: L_FIR = 0.57 x L_8-1000; IRX = L_FIR/L_UV; beta from SED slope over rest 1250-2500 A; SFRs from Madau & Dickinson calibrations  
  > "with _L_ FIR = (4 _._ 8 _±_ 1 _._ 3) _⇥_ 10 [10] L _⊙_ (= 0 _._ 57 _⇥_ _L_ 8 _−_ 1000 )" (3.2. Infrared Excess)
   - fitting: _not stated_
   - validation: _not stated_
5. **Build resolved IRX map**: Grid ALMA and HST to same scale, convolve HST with ALMA beam, convert pixel fluxes to L_IR and L_UV using integrated best-fit SED as scale, take ratio  
  > "Individual pixel fluxes are converted to IR and UV luminosities using the best-fit (galaxy integrated) SED as a scale." (3.2 Infrared Excess)
   - parameter: pixel size 0.05"  
  > "The IRX map with a pixel size of 0.05 _[00]_ ." (Figure 1 caption)
   - assumption: HST/ACS PSF negligible versus ALMA beam  
  > "we have confirmed that the HST /ACS PSF is negligible compared to the ALMA beam" (3.2 Infrared Excess)
   - fitting: _not stated_
   - validation: Monte Carlo of 1000 realizations shifting ALMA map by Gaussian offsets sigma=0.2" for astrometric systematics  
  > "We varied the relative positions of the _HST_ and ALMA maps 1000 times by shifting the phase center of the ALMA map by a random offset sampled from a gaussian distribution with _σ_ = 0 _._ 2 _[00]_ ." (3.2. Infrared Excess)

## Software

- **CASA** 4.4.0: calibration and imaging  
  > "The data were reduced and imaged using the Common Astronomy Software Application ( CASA ) version 4.4.0" (2.2 Atacama Large Millimeter/Submillimeter Array)
- **CIGALE** : SED fitting  
  > "We then fit the spectral energy distributions (SEDs) using CIGALE" (3.1 Spectral energy distribution fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S870 of SSA22a-C16 | 192 | 57 | uJy | 1 | We measure an integrated flux density of S 870 = 192 ± 57 µJy for the source. |
| S870 of stack | 67 | 23 | uJy | 2 | We detect a 3 σ signal at the phase centre with flux density S 870 = 67 ± 23 µJy. |
| L_8-1000 of C16 | 8.4e10 | 2.3e10 (+0.14 dex systematic) | Lsun | 3 | _L_ 8 _−_ 1000 = (8 _._ 4 _±_ 2 _._ 3) _⇥_ 10 [10] L _⊙_ for the detection |
| L_8-1000 of stack | 2.9e10 | 0.9e10 | Lsun | 3 | (2 _._ 9 _±_ 0 _._ 9) _⇥_ 10 [10] L _⊙_ for the stack |
| IRX of C16 | 0.56 | 0.15 | dimensionless | 4 | The corresponding infrared excess is thus (IRX) = 0.56 ± 0.15 |
| UV slope beta of C16 | -1.25 | 0.03 | dimensionless | 4 | β = − 1.25 ± 0.03 |
| Total SFR of C16 | 34 | 4 | Msun/yr | 4 | giving a total SFR = 34 ± 4 M ⊙ yr − 1 |
| Gaussian FWHM of C16 uv-profile | 0.94 | not stated | arcsec | 2 | is better fit by a Gaussian profile (FWHM of 0.94 _[00]_ ) |
| Resolved IRX range | peaks ~1.5, falls to <~0.5 | not stated | dimensionless | 5 | The IRX peaks at _'_ 1.5 and decreases to .0.5 across the LBG |

## Qualitative findings

- Dust emission is offset from UV clumps, sitting at the saddle between two UV clumps; morphology resembles a merger or chain galaxy  
  > "The submillimeter emission sits at the ‘saddle’ between two clumps of bright UV emission" (3.2 Infrared Excess)

## Claim tuples

- H: Does the LBG follow the local MHC99 IRX-beta relation? | E: ALMA 870um detection and SED-derived IRX and beta | R: IRX=0.56±0.15, beta=-1.25±0.03 | F: Galaxy lies a factor ~10 below the MHC99 relation | **supported**
- H: Does IRX vary within a single high-z galaxy? | E: Resolved IRX map from ALMA and HST at ALMA resolution | R: IRX varies by more than a factor of 3 | F: Complex dust/UV morphology drives much of the IRX-beta scatter | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No resolved beta map; beta from seeing-limited photometry  
  > "we do not have a resolved map of β (the F814W band image is our only high-resolution optical image" (3.2 Infrared Excess)
- Limitation (authors): Insensitive to dust extended beyond ~500 mas beam  
  > "we are less sensitive to submillimeter emission in the LBGs if the dust is extended on scales larger than the delivered _⇠_ 500 mas beam" (2.2. Atacama Large Millimeter/Submillimeter Array)
- Caveat (inferred, ours): Only one 4 sigma detection; resolved map is low S/N
- Caveat (inferred, ours): Dust temperature fixed from a single FIR photometric point
- Caveat (inferred, ours): Pixel SED scaling assumes uniform SED across the galaxy
- Caveat (inferred, ours): Single object limits generality

## Reproducibility

- Data public (paper): ALMA project code given; data from Cycle 2 program  
  > "ADS/JAO.ALMA#2013.1.00362.S" (4. DISCUSSION & SUMMARY)
- Products in archive: _not stated_
- Missing: CIGALE photometry and module settings
- Missing: HST image handling details
- Missing: clean parameters
- Data volume (inferred): ~ tens of GB raw (four SBs, Band 7, 10 targets)
- Score (inferred): 3/5, Public ALMA data and a simple recipe, but photometry, SED settings and imaging parameters are incomplete.
- Rediscovery candidate: no, Key results depend on HST and ground photometry and CIGALE settings that are not fully specified.

## Links

- Method: Casey et al. (2012) (dust emission model)
- Method: Madau & Dickinson (2014) (SFR calibrations)
- Companion: Hine et al. 2016, MNRAS, 455, 2363 (possible merger nature of the LBG)
- Companion: Coppin et al. (2015) (stacked LBG FIR fluxes guiding the observations)
- Related: SSA22 field LBG survey (Steidel et al. 2003)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 76,
  "stated": 42,
  "rate": 0.553
 },
 "evidence_ok": true
}
```
