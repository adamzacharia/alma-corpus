# ALMA detection of [C ii] 158 μm emission from a strongly lensed z = 2.013 star-forming galaxy

`2015A&A...576L...2S` | Astronomy and Astrophysics 2015 | first author: Schaerer, D. | arXiv: 1502.03842 | DOI: 10.1051/0004-6361/201425542

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the ISM/PDR properties ([CII]/FIR and [CII]/CO ratios) of a typical, IR-faint lensed star-forming galaxy at z=2.013, compared with nearby and high-z galaxies?  
  > "Our objectives are to determine the properties of the interstellar medium (ISM) and of star-formation in typical star-forming galaxies at high redshift." (abstract)
- Target **MACS J0451+0006 arc (southern part)**: coordinates _not stated_; z/distance z = 2.013  
  > "This magnification corresponds both to the mean magnification of the total arc (cf. Jones et al. 2010)" (2.1 ALMA observations and results); "Hα redshift from Richard et al. (2011)." (Table 1); distance from Hα redshift from Richard et al. (2011)  
  > "This magnification corresponds both to the mean magnification of the total arc (cf. Jones et al. 2010)" (2.1 ALMA observations and results); "Hα redshift from Richard et al. (2011)." (Table 1)

## Data provenance

- ALMA projects: 2011.0.00130.S
- bands: Band 9  
  > "Our source was observed by 25 antennas in band 9 during a ∼1h track including calibration scans on the 31st of December 2012." (2.1 ALMA observations and results)
- frequencies and spectral setup: 4 sub-bands of 2 GHz, 128 channels of 15.625 MHz, centered at 628.826, 630.520, 632.220, 648.234 GHz  
  > "The correlator was set up to obtain 4 spectral sub-bands of 2 GHz with 128 channels of 15.625 MHz." (2.1 ALMA observations and results)
- continuum bandwidth: _not stated_
- arrays: 25 antennas  
  > "Our source was observed by 25 antennas in band 9" (2.1 ALMA observations and results)
- configurations: _not stated_
- baselines: 13 to 376 m  
  > "Projected baseline lengths range from 13 to 376 meters." (2.1 ALMA observations and results)
- angular resolution: 0.33'' x 0.34'' (natural weighting); 0.5'' tapered for Fig. 1  
  > "With natural weighting the clean beam full width at half maximum (FWHM) is 0.33 ′′ × 0.34 ′′" (2.1 ALMA observations and results)
- max recoverable scale: _not stated_
- sensitivity: 9.8 mJy/beam in 14.9 km/s channels; continuum 0.84 mJy/beam  
  > "the noise RMS is σ = 9.8 mJy beam −1 in 14.9 km s −1 channels." (2.1 ALMA observations and results)
- time on source: ~1 h track including calibration  
  > "during a ∼1h track including calibration scans" (2.1 ALMA observations and results)
- observing dates: 31 December 2012  
  > "on the 31st of December 2012" (2.1 ALMA observations and results)
- pi or archival as stated: Cycle 0, PI Ellis  
  > "2011.0.00130.S (PI Ellis)" (Acknowledgements)
- Line: [CII] 158 µm (630.78 GHz at z=2.013 (observed))
- Other facility **PdBI**: CO(3-2) detection used for L_CO  
  > "The CO(3-2) line was detected with the PdBI by DessaugesZavadsky et al. (2014)." (2.2 Other observations)
- Other facility **Spitzer/Herschel**: IR SED and L_IR from Sklias et al. 2014  
  > "based on Spitzer and Herschel observations, has been studied in detail by Sklias et al. (2014)" (2.2 Other observations)
- Other facility **HST**: WFC3 F140W image for Fig. 1  
  > "HST/WFC3 image in the filter F140W" (Figure 1 caption)
- External data: Lens model/magnification and Hα redshift  
  > "adopting the magnification factor µ = 49 from the updated lens model of Richard et al. (2011)." (Table 1) [from Richard et al. (2011)]
- External data: L_CO = (5.1 ± 1.5)e4 Lsun  
  > "From DessaugesZavadsky et al. (2014)." (Table 1) [from Dessauges-Zavadsky et al. (2014)]
- External data: L_IR of southern arc  
  > "IR luminosity of the S of the arc (cf. Sklias et al. 2014)." (Table 1) [from Sklias et al. (2014)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration and cleaning; mode not stated  
  > "The visibilities were calibrated and the image cleaned with the CASA software." (2.1 ALMA observations and results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013, extrapolated from band 3 and band 7 observations  
  > "Passband, flux and phase calibrations used the quasar J0423-013, extrapolating from ALMA" (2.1 ALMA observations and results)
- flux scale uncertainty: ~25%  
  > "which leads to a relatively large uncertainty for the flux calibration, of the order of ∼ 25%." (2.1 ALMA observations and results)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "With natural weighting the clean beam full width at half maximum (FWHM) is 0.33 ′′ × 0.34 ′′" (2.1 ALMA observations and results)
- uv taper: tapered to 0.5'' resolution for Fig. 1  
  > "the ALMA data were tapered and the resolution is 0.5 ′′" (Figure 1 caption)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: bad channels flagged and [CII] line masked; 4 sub-bands integrated for continuum  
  > "Flagging bad channels and masking out the [C ii] 158µm line we integrate the 4 sub-bands to produce a continuum map" (2.1 ALMA observations and results)
- primary beam correction: applied to spectra and continuum flux  
  > "Integrating the spectra corrected for the primary beam in the same spatial box we clearly detect the [C ii] 158µm line" (2.1 ALMA observations and results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.33'' x 0.34''  
  > "clean beam full width at half maximum (FWHM) is 0.33 ′′ × 0.34 ′′" (2.1 ALMA observations and results)
- final rms: 9.8 mJy/beam per 14.9 km/s channel; continuum 0.84 mJy/beam  
  > "obtaining a noise of σ cont = 0.84 mJy beam −1" (2.1 ALMA observations and results)

### Inherited from earlier work

- Magnification µ=49 from updated lens model  
  > "as determined from an updated version of the lensing model by Richard et al. (2011) and recent updates to it." (2.1 ALMA observations and results) [from Richard et al. (2011)]
- CO(3-2) to CO(1-0) conversion r31 = 0.57  
  > "assuming a factor r 3,1 = 0.57 between the CO(3-2) and CO(1-0) line luminosities" (2.2 Other observations) [from Dessauges-Zavadsky et al. (2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual scripts were used
- clean parameters (threshold, masks, niter, cell, image size, taper value)
- box coordinates for spectrum integration
- continuum-subtraction/line-free channels
- conversion from flux to luminosity formula
- how the L_FIR range was obtained
- flux scaling of J0423-013 values

## Analysis recipe

1. **calibrate and image cube**: Calibrate visibilities and clean with CASA, natural weighting  
  > "The visibilities were calibrated and the image cleaned with the CASA software." (2.1 ALMA observations and results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **continuum limit**: Mask line, integrate 4 sub-bands, sum flux in box, primary beam correct, quote 3σ upper limit  
  > "we obtain a 3 σ upper limit of < 27 mJy, which is compatible with the SPIRE 500 µm band" (2.1 ALMA observations and results)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with SPIRE 500 µm  
  > "which is compatible with the SPIRE 500 µm band" (2.1 ALMA observations and results)
3. **measure [CII] line flux and luminosity**: Integrate primary-beam-corrected spectrum in box over 630.5-631.0 GHz; divide by magnification  
  > "The flux integrated in the range 630.5-631.0 GHz is S CII = 37.7 ± 3.7 Jy km s −1" (2.1 ALMA observations and results)
   - parameter: µ = 49 ± 5  
  > "We estimate an uncertainty of µ = 49 ± 5." (2.1 ALMA observations and results)
   - assumption: Missing short-spacing flux negligible  
  > "Therefore, the flux lost due to missing short spacings should be small" (2.1 ALMA observations and results)
   - fitting: _not stated_
   - validation: _not stated_
4. **compare [CII]/FIR and [CII]/CO with literature**: Place source on L_CII/L_FIR vs L_FIR and L_CII/L_FIR vs L_CO/L_FIR diagrams with literature samples; compare to SFR-L_CII relation  
  > "The [C ii] 158µm and CO line strengths, both normalized to L FIR, are shown in Fig. 4 and compared to available data from nearby and distant galaxies and AGN." (3.2 Normal [CII]/CO emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and cleaning of visibilities  
  > "The visibilities were calibrated and the image cleaned with the CASA software." (2.1 ALMA observations and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S_CII | 37.7 | ± 3.7 | Jy km/s | 3 | S CII b 37.7 ± 3.8 Jy km/s |
| Intrinsic L_CII | 1.21e8 | ± 0.12e8 (formal, excl. ~25% calibration) | Lsun | 3 | (1.21 ± 0.12) × 10 [8] L ⊙ |
| [CII] frequency | 630.743 | ± 0.015 | GHz | 3 | ν CII 630.743 ± 0.015 GHz |
| Continuum 3σ upper limit | <27 | not stated | mJy | 2 | we obtain a 3 σ upper limit of < 27 mJy |
| L_CII/L_FIR | (1.2-2.4)e-3 | not stated | dimensionless | 4 | L [CII] / L FIR ≈ (1.2 − 2.4) × 10 [−][3] |
| L_CII/L_CO | 2.3e3 | not stated | dimensionless | 4 | L [CII] / L CO = 2.3 × 10 [3] |

## Qualitative findings

- Source is the IR-faintest galaxy detected in [CII] at z>1; L_CII/L_FIR similar to nearby galaxies despite high dust temperature  
  > "our source is currently the IR-faintest galaxy detected in [C ii] 158µm at z - 1, namely a faint LIRG." (3.1 Carbon emission from a z = 2, faint LIRG)

## Claim tuples

- H: Does the cold ISM of a typical, IR-faint z~2 galaxy resemble that of local star-forming galaxies? | E: ALMA band 9 [CII] observation of lensed arc, compared with literature [CII]/FIR and [CII]/CO | R: L_CII/L_FIR ≈ (1.2-2.4)e-3 and L_CII/L_CO = 2.3e3, similar to nearby galaxies | F: Cold ISM of typical high-z galaxies resembles normal local star-forming galaxies; larger samples needed | **partially**

## Reasoning

- Why this data: Lensing allows probing typical lower-luminosity galaxies  
  > "Gravitationally lensed sources offer a unique chance to sample this regime." (1. Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Delivered data did not meet requested sensitivity; ~25% flux calibration uncertainty  
  > "Although the delivered data did not meet our requested sensitivity, it is sufficient to examine the average ISM/PDR properties" (2.1 ALMA observations and results)
- Caveat (inferred, ours): Single source; no spatial/kinematic analysis
- Caveat (inferred, ours): Flux calibration extrapolated from bands 3/7, ~25% uncertainty
- Caveat (inferred, ours): Possible AGN contamination of metallicity and ratios
- Caveat (inferred, ours): Different L_FIR ranges between abstract and text

## Reproducibility

- Data public (paper): Project code and PI given; public status not stated  
  > "This paper makes use of the following ALMA data: 2011.0.00130.S (PI Ellis)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and cleaning parameters
- Missing: integration box definition
- Missing: lens model details
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Simple measurement and public Cycle 0 data, but processing details are sparse.
- Rediscovery candidate: yes, Cycle 0 data likely public, single integrated flux and luminosity are numeric; recipe is simple though lacking some details.

## Links

- Companion: Dessauges-Zavadsky et al. (2014) (CO(3-2) PdBI data)
- Companion: Sklias et al. (2014) (IR SED and stellar properties)
- Companion: Richard et al. (2011) (Lens model and redshift)
- Related: Herschel Lensing Survey

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 68,
  "stated": 41,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
