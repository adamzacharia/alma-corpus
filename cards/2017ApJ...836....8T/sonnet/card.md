# ALMA Observations Show Major Mergers Among the Host Galaxies of Fast-growing, High-redshift Supermassive Black Holes

`2017ApJ...836....8T` | The Astrophysical Journal 2017 | first author: Trakhtenbrot, Benny | arXiv: 1612.00010 | DOI: 10.3847/1538-4357/836/1/8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Are major mergers important drivers of rapid early SMBH growth, as tested with ALMA continuum and [C II] observations of six z≃4.8 quasar hosts, three FIR-bright and three FIR-faint?  
  > "Our ALMA data therefore clearly support the idea that major mergers are important drivers for rapid early SMBH growth." (abstract)
- Target **Six SDSS quasars at z≃4.8 (J0331, J1341, J1511, J0923, J1328, J0935)**: coordinates SDSS names, e.g. SDSS J033119.67-074143.1 (Table 1)  
  > "The redshifts of the selected targets are in the range z = 4.658 − 4.729, with a median of z median = 4.6703 (as determined from the Mg II lines; see Section 3.2 for more details)." (2.1 Sample Selection and Properties); z/distance z = 4.658-4.729 (Mg II)  
  > "The redshifts of the selected targets are in the range z = 4.658 − 4.729, with a median of z median = 4.6703 (as determined from the Mg II lines; see Section 3.2 for more details)." (2.1 Sample Selection and Properties); distance from Mg II-based redshifts from Trakhtenbrot et al. 2011 (T11); [C II] redshifts in Table 3  
  > "The redshifts of the selected targets are in the range z = 4.658 − 4.729, with a median of z median = 4.6703 (as determined from the Mg II lines; see Section 3.2 for more details)." (2.1 Sample Selection and Properties)

## Data provenance

- ALMA projects: 2013.1.01153.S
- bands: Band 7  
  > "The six targets were observed in ALMA band-7, as part of cycle-2" (2.2.1 ALMA Observations)
- frequencies and spectral setup: TDM mode, four spectral windows of 1875 MHz each, 128 channels, ~30 km/s resolution; one window centred on the expected [C II] peak, one adjacent, two others ~12 GHz away  
  > "We chose to use the TDM correlator mode, providing four spectral windows, each covering an effective bandwidth of 1875 MHz" (2.2.1 ALMA Observations); "This spectral range is sampled by 128 channels, providing a spectral resolution of ∼ 30kms −1 ." (2.2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12m antennas, 29-38 per execution  
  > "the data presented here were collected with a varying number of 12m antennas, between 29-38." (2.2.1 ALMA Observations)
- configurations: C34-4  
  > "The observations were set up to use the extended C34-4 configuration" (2.2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: ~0.3 arcsec at 330 GHz (~2 kpc); beams 0.38-0.54 x 0.29-0.31 arcsec  
  > "which provides a resolution of about 0.′′ 3 at 330 GHz (corresponding to about 2 kpc at z ≃ 4.8)." (2.2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: (4.2-9.2)x10^-2 mJy/beam rms  
  > "The ALMA band-7 flux densities reach a depth of F ν ≃ (4.2 − 9.2) × 10 −2 mJy/beam (rms)." (2.2.1 ALMA Observations)
- time on source: 697-3230 s per target  
  > "SDSS J134134.20+014157.7 35 697 5.6 × 10 −2" (Table 1)
- observing dates: 2014 July 18 to 2015 June 13  
  > "during the period 2014 July 18 to 2015 June 13." (2.2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 µm fine-structure line (λ 157.74 µm)
- Other facility **Herschel/SPIRE**: FIR photometry and stacking used for SFR comparison and SEDs  
  > "which were individually detected in previous Herschel /SPIRE observations" (abstract)
- Other facility **VLT/SINFONI**: near-IR Mg II spectroscopy for redshifts and BH masses (T11)  
  > "In practice, this implies that the NIR data for all the six quasars studied here were obtained with the VLT/SINFONI." (2.1 Sample Selection and Properties)
- Other facility **Spitzer/IRAC**: 3.6 and 4.5 µm data giving positional priors and checks for companions  
  > "These data were used to derive positional priors that allowed us to de-blend the low-resolution Herschel /SPIRE data." (2.1 Sample Selection and Properties)
- External data: Mg II-based redshifts, BH masses and bolometric luminosities  
  > "b Mg II λ 2798-based redshifts taken from T11." (Table 3) [from Trakhtenbrot et al. 2011 (T11)]
- External data: SDSS-based redshifts  
  > "a SDSS-based redshifts taken from Hewett & Wild (2010)." (Table 3) [from Hewett & Wild (2010)]
- External data: Herschel/SPIRE measurements and stacking  
  > "For all three FIR-faint systems (bottom row), we adopted the measurements of the stacked Herschel signal (N14)." (Figure 8 caption) [from Netzer et al. 2014 (N14)]
- External data: [C II]/FIR comparison compilation  
  > "The compilation, adapted from Cicone et al. (2015), includes inactive star forming galaxies at low and intermediate redshifts" (3.2 [C II] emission line properties) [from Cicone et al. (2015)]
- External data: local elliptical galaxy BH-bulge masses  
  > "a sample of z ≃ 0 elliptical galaxies (taken from Kormendy & Ho 2013, black circles)" (Figure 9 caption) [from Kormendy & Ho 2013]

## Processing

### Calibration

- pipeline or manual: Observatory-provided scripts used to generate visibilities  
  > "The scripts provided by the observatory were used to generate the visibilities." (2.2.2 Data Reduction and Spectral Measurements)
- casa version: CASA 4.5.0  
  > "Data reduction was performed using CASA package, version 4.5.0 (Mcmullin et al. 2007)." (2.2.2 Data Reduction and Spectral Measurements)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Not implemented; did not improve S/N for brightest sources  
  > "We note that self calibration for the brightest sources did not improve the signal-to-noise ratios and therefore was not implemented." (2.2.2 Data Reduction and Spectral Measurements)

### Imaging

- task: CLEAN  
  > "We then applied the CLEAN algorithm, using a “natural” weighting to determine the noise level" (2.2.2 Data Reduction and Spectral Measurements)
- deconvolver: _not stated_
- weighting robust: Natural for noise estimates; Briggs robust = 0.5 for science images  
  > "using a “briggs” weighting (with robustness parameter set to 0.5), to obtain images with the best possible spatial resolution." (2.2.2 Data Reduction and Spectral Measurements)
- uv taper: _not stated_
- cell size: 0.06 arcsec  
  > "SDSS J033119.67-074143.1 29 792 9.2 × 10 −2 0.41 × 0.31 0.06" (Table 1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum images from the two highest-frequency line-free windows; the other two windows continuum-subtracted in the uv plane  
  > "Continuum emission images were constructed using the two highest frequency, linefree spectral windows." (2.2.2 Data Reduction and Spectral Measurements); "[C II ] emission line images were constructed by subtracting the continuum emission from the other" (2.2.2 Data Reduction and Spectral Measurements)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Sample selection and ancillary data details  
  > "refer the reader to our previous papers (T11, M12, N14) for additional details." (2.1 Sample Selection and Properties) [from T11, M12, N14]
- Gray-body SED (Td = 47 K, beta = 1.6) following other high-z quasar host studies  
  > "we adopted the procedure used in several recent studies of FIR emission in high-redshift quasar hosts (e.g., Willott et al. 2015; Venemans et al. 2016, and references therein)" (3.3.1 FIR SEDs and SFRs) [from Willott et al. 2015; Venemans et al. 2016]
- Dynamical mass prescription for an inclined rotating disk  
  > "we employ the same prescription as used in several recent studies of [C II ] (and CO) emission in high-redshift sources" (3.3.2 Host and companion galaxy masses) [from Wang et al. 2013; Willott et al. 2015; Venemans et al. 2016]
- Dust opacity kappa = 0.77 (850 µm/λ)^β  
  > "following Dunne et al. 2000, for consistency with Venemans et al. 2016" (3.3.2 Host and companion galaxy masses) [from Dunne et al. 2000]
- BH masses with McLure & Dunlop (2004) calibration  
  > "These M BH estimates used the calibration by McLure & Dunlop (2004)." (3.3.3 SMBH-host galaxy relations) [from T11; McLure & Dunlop 2004]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: deconvolver, threshold, masks, iterations, image size
- Line-free channels and exact spectral windows used for continuum subtraction
- Flux calibrator and flux scale uncertainty
- Whether pipeline or manual calibration scripts were used and which pipeline version
- Aperture and fitting details for the 2D Gaussian fits
- How inclinations were bounded for unresolved sources
- Primary beam correction treatment
- Uncertainties of L_TIR and SFR

## Analysis recipe

1. **Image continuum and [C II] cubes**: Observatory scripts for visibilities, then CLEAN with Briggs robust 0.5; continuum from two upper windows; uv continuum subtraction for [C II] from the lower two  
  > "[C II ] emission line images were constructed by subtracting the continuum emission from the other two, lower frequency spectral windows, in the UV space" (2.2.2 Data Reduction and Spectral Measurements)
   - software: CASA
   - parameter: robust = 0.5  
  > "with robustness parameter set to 0.5" (2.2.2 Data Reduction and Spectral Measurements)
   - fitting: _not stated_
   - validation: Checked for no residual continuum in line images  
  > "We verified that the resulting [C II ] emission line images have no residual continuum signal in them." (2.2.2 Data Reduction and Spectral Measurements)
2. **Measure sizes, line fluxes, widths and redshifts**: 2D Gaussian fits to continuum and moment-0 images; 1D spectra from Gaussian-based apertures (1.5-2 sigma) fitted with a single Gaussian; the spatial fluxes adopted  
  > "We then fitted the emission line profiles with a simple model of a single Gaussian, from which we obtained the" (2.2.2 Data Reduction and Spectral Measurements)
   - software: CASA
   - fitting: 2D Gaussian fits and 1D Gaussian line fits; line centres free  
  > "We stress that the centers of the [C II ] line profiles were treated as free parameters" (2.2.2 Data Reduction and Spectral Measurements)
   - validation: Spatial and spectral fluxes agree within 0.1 dex (median 0.05 dex)  
  > "with differences of no more than 0.1 dex for the six quasar hosts (median difference of 0.05 dex)" (2.2.2 Data Reduction and Spectral Measurements)
3. **Derive FIR luminosities, TIR and SFR**: Gray-body SED (Td=47 K, beta=1.6) and Chary & Elbaz 2001 templates anchored to ALMA continuum; SFR = L_TIR(8-1000 µm)/10^10 Lsun  
  > "SFR /M ⊙ yr −1 = L TIR (8 − 1000 µ m) / 10 10 L ⊙ (following the assumed Chabrier IMF)." (3.3.1 FIR SEDs and SFRs)
   - parameter: L_FIR integrated over 42.5-122.5 µm; TIR over 8-1000 µm  
  > "These scaled SEDs are then used to calculate the integrated luminosity between 42.5 − 122.5 µ m" (3.2 [C II] emission line properties)
   - assumption: AGN contribution to FIR neglected (<~10%); Chabrier IMF  
  > "we choose to neglect the (small) possible AGN contribution to the FIR SEDs of our sources." (3.3.1 FIR SEDs and SFRs)
   - fitting: Templates with no free parameters; best-matching template chosen by monochromatic luminosity  
  > "As the templates have no free parameters [2], we have simply" (3.3.1 FIR SEDs and SFRs)
   - validation: Compared with Herschel SPIRE data and alternative temperatures (40, 50, 55, 60, 65 K)  
  > "We have also experimented with both colder and warmer gray-body SEDs, always “anchored” to the new ALMA data." (3.3.1 FIR SEDs and SFRs)
4. **Dynamical, dust and gas masses**: M_dyn = 9.8e8 (D_[CII]/kpc)(FWHM/100 km/s)^2 / sin^2(i) Msun, with cos(i) = a_min/a_maj; dust mass from optically thin dust; gas mass via gas-to-dust 100  
  > "Rough estimates of gas masses can then be inferred by assuming a (uniform) gas-to-dust ratio of 100." (3.3.2 Host and companion galaxy masses)
   - assumption: Inclined rotating disk, v_circ = 0.75 FWHM/sin i; Td=47 K, beta=1.6; gas-to-dust 100  
  > "in which the circular velocity is given by v circ = 0.75 × FWHM / sin ( i )." (3.3.2 Host and companion galaxy masses)
   - fitting: _not stated_
   - validation: Caveats discussed; no independent check  
  > "Such dynamical mass estimates carry significant uncertainties due to the different assumptions required to derive them" (3.3.2 Host and companion galaxy masses)
5. **Compare with SF main sequence and BH-host relations; assess mergers**: Compare SFR vs M_dyn with the main-sequence relation; BH growth rate from L_bol with eta=0.1; compare M_BH/M_dyn with local ellipticals; identify companions via continuum and [C II] redshift  
  > "the radiative efficiency is assumed to be η = 0.1." (3.3.3 SMBH-host galaxy relations)
   - software: MATLAB package for astronomy and astrophysics
   - assumption: Host mass grows only via star formation at CE01-based SFR  
  > "we assume that the mass grows only due to the formation of new stars at a rate determined by the CE01-based SFRs" (3.3.3 SMBH-host galaxy relations)
   - fitting: _not stated_
   - validation: Chance-coincidence estimates from deep-survey number counts  
  > "cannot be attributed to chance coincidence" (3.1 Source detection and identification)

## Software

- **CASA** 4.5.0: Data reduction, CLEAN imaging, uv continuum subtraction, moment maps  
  > "Data reduction was performed using CASA package, version 4.5.0 (Mcmullin et al. 2007)." (2.2.2 Data Reduction and Spectral Measurements)
- **MATLAB package for astronomy and astrophysics (Ofek 2014)** : Acknowledged as used in the work  
  > "This work made use of the MATLAB package for astronomy and astrophysics (Ofek 2014)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Companion SMGs detected | 3 of 6 quasars (separations ~14-45 kpc) | not stated | count | 2 | separated by ∼ 14 − 45kpc and < 450kms −1 from the quasar hosts |
| [C II] FWHM of quasar hosts | 240-510 | ~10% | km/s | 2 | FWHM [C II ] ∼ 240 − 510kms −1 |
| L[CII]/LFIR of quasar hosts | (2.1-9.4)e-4 | not stated | dimensionless | 3 | the L [C II ] /L FIR ratio is in the range of (2.1 − 9.4) × 10 −4 |
| SFR of quasar hosts (gray-body) | 260-3040 | not stated | Msun/yr | 3 | span a wide range of ∼ 260 − 3040 M ⊙ yr −1 for the gray-body SEDs |
| Dust masses of quasar hosts | (0.4-4.8)e8 | not stated | Msun | 4 | The dust masses we derive are in the range M dust ∼ (0.4 − 4.8) × 10 8 M ⊙ for the quasar hosts |
| Inclination-corrected M_dyn of quasar hosts | (3.7-7.5)e10 | not stated | Msun | 4 | we obtain dynamical masses of M dyn ≃ (3.7 − 7.5) × 10 10 M ⊙ for the quasar hosts |
| M_BH/M_dyn | 1/260 to 1/10 | not stated | dimensionless | 5 | which are in the range M BH /M dyn ∼ 1/260 − 1/10 |

## Qualitative findings

- Quasar hosts show smooth velocity gradients consistent with rotation-dominated outer gas, even in FIR-bright systems.  
  > "we cautiously conclude that the outer parts of the [C II ]-emitting regions in all sources are dominated by rotation, with v/σ v > 1." (3.2 [C II] emission line properties)

## Claim tuples

- H: Are major mergers common among hosts of fast-growing z~4.8 SMBHs? | E: ALMA band-7 continuum and [C II] mapping of six quasars; companion search and mass comparison | R: Three of six quasars have [C II]-confirmed companions at 14-45 kpc with |dv|<450 km/s and comparable M_dyn | F: A significant fraction (50% of the small sample) are interacting major mergers | **supported**
- H: Are mergers the only driver of fast SMBH growth? | E: Companion occurrence by FIR-bright/faint class and kinematics | R: Two of three interacting systems are FIR-faint; FIR-bright systems without companions show rotation | F: Other processes may also fuel the SMBHs and star formation | **supported**
- H: Is ALMA continuum consistent with Herschel-based SFRs? | E: Gray-body and CE01 SEDs anchored to ALMA continuum, compared with Herschel | R: Good agreement except J0331 | F: ALMA confirms intense SF | **supported**
- H: Do the hosts follow the local BH-host mass ratio? | E: Compare M_BH with [C II] M_dyn | R: Four of six have M_BH/M_dyn >~1/90, above the local ratio | F: Dynamical host masses are generally lower than expected from local ratios | **partially**

## Reasoning

- Why this data: Sub-mm interferometry probes hosts in a regime uncontaminated by AGN, with resolution to test mergers  
  > "has enabled the direct observation of the hosts of high-redshift quasars in a spectral regime that is mostly uncontaminated by the AGN emission." (1. Introduction)
- Why this method: _not stated_
- Alternative: Hotter (65 K) and colder (40 K) gray-body SEDs tested; 65 K needed to match Herschel for J0331 but deemed beyond typical temperatures  
  > "However, this high temperature is beyond what is typically observed, even among the most luminous FIR sources" (3.3.1 FIR SEDs and SFRs)
- How they decided it was enough: _not stated_
- Limitation (authors): M_dyn is uncertain: extended emission missed, inclination from marginally resolved sizes, beam smearing  
  > "our ALMA data may not be able to detect the more extended lower surface brightness [C II ]-emitting regions, thus underestimating D [C II ]" (3.3.2 Host and companion galaxy masses)
- Limitation (authors): Small sample limits interpretation  
  > "The small size of our sample naturally limits the scope of our interpretation" (3.4 Major mergers among hosts of fast-growing SMBHs)
- Caveat (inferred, ours): Six objects only; merger fraction has large Poisson uncertainty
- Caveat (inferred, ours): M_dyn depends on uncertain sizes and inclinations at ~2 kpc resolution
- Caveat (inferred, ours): Single-temperature SED and the neglect of an AGN contribution may bias SFRs
- Caveat (inferred, ours): Companion association rests on 3-4 sigma continuum and 3.5 sigma [C II] detections for some

## Reproducibility

- Data public (paper): ALMA project code given and acknowledged as ADS/JAO.ALMA#2013.1.01153.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01153.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full CLEAN parameters and masks
- Missing: Line-free channel ranges
- Missing: Fitting uncertainty treatment
- Missing: Herschel and T11 data tables from other papers
- Data volume (inferred): ~50-150 GB for six Band 7 TDM datasets
- Score (inferred): 3/5, Data are public and the main steps are described, but CLEAN settings and flux calibration are missing, and some inputs come from earlier papers.
- Rediscovery candidate: yes, Data are public, the recipe is mostly clear, and the main results (fluxes, FWHM, SFR, M_dyn) are numeric.

## Links

- Method: Chary & Elbaz 2001 (FIR SED templates)
- Method: Venemans et al. 2016 (analysis prescription for high-z quasar hosts)
- Companion: Trakhtenbrot et al. 2011 (T11) (parent sample, Mg II redshifts and BH masses)
- Companion: Netzer et al. 2014 (N14) (Herschel/SPIRE campaign of the same quasars)
- Companion: Mor et al. 2012 (M12) (Herschel/SPIRE campaign of the same quasars)
- Related: Herschel/SPIRE campaign of z≃4.8 quasars
- Related: ALMA cycle-4 band-7 follow-up of 12 additional quasars

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
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
  "facts": 82,
  "stated": 57,
  "rate": 0.695
 },
 "evidence_ok": true
}
```
