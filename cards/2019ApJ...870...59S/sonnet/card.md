# ALMA, ATCA, and Spitzer Observations of the Luminous Extragalactic Supernova SN 1978K

`2019ApJ...870...59S` | The Astrophysical Journal 2019 | first author: Smith, I. A. | arXiv: 1811.11267 | DOI: 10.3847/1538-4357/aaf1a3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies, other
- Question: What is the radio-millimeter spectrum of SN 1978K, and what do ALMA, ATCA and Spitzer data imply for the synchrotron emission and for warm and cold dust?  
  > "In Section [3](#sec:model), we use two different models to explain the combined radio-millimeter synchrotron spectrum." (Introduction)
- Target **SN 1978K**: coordinates _not stated_; z/distance ~4.4-4.6 Mpc  
  > "SN 1978K lies in the nearby late-type barred spiral galaxy NGC 1313. This appears to be an isolated galaxy at a distance of only $\sim 4.4 - 4.6$ Mpc (cite: Jacobs2009; Qing2015)." (Introduction); distance from Jacobs2009; Qing2015  
  > "SN 1978K lies in the nearby late-type barred spiral galaxy NGC 1313. This appears to be an isolated galaxy at a distance of only $\sim 4.4 - 4.6$ Mpc (cite: Jacobs2009; Qing2015)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00869.S
- bands: Bands 3, 4, 6, 7 (Cycle 3, 2016)  
  > "During Cycle 3 in 2016, ALMA observed SN 1978K in Bands 3, 4, 6, and 7." (2.1)
- frequencies and spectral setup: Four SPWs per band, 1.875 GHz each, 128 channels each  
  > "Each ALMA band is split into four spectral windows (SPWs) of bandwidth 1.875 GHz. Each SPW contains 128 channels." (2.1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Maximum baseline 1.8, 1.1, 0.7, 0.8 km for Bands 3, 4, 6, 7  
  > "| 3 | 2016-09-02 | 57633 | 13983 | 16.7 | 1.8 | 1.38 | 42.4 |" (Table 1)
- angular resolution: Beams 0.36-0.69 arcsec across bands  
  > "& All 4 & 233.0049 & 0.63 & 0.525 & 0.026\" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: Image rms 0.015-0.065 mJy/beam (all-4-SPW: 0.025, 0.015, 0.026, 0.030)  
  > "& All 4 & 145.0147 & 0.52 & 0.855 & 0.015\" (Table 2)
- time on source: 16.7, 21.2, 26.8, 70.4 min for Bands 3, 4, 6, 7  
  > "| 7 | 2016-06-16 | 57556 | 13906 | 70.4 | 0.8 | 0.72 | 44.1 |" (Table 1)
- observing dates: 2016-09-02 (B3), 2016-07-25 (B4), 2016-06-09 (B6), 2016-06-16 (B7)  
  > "| 4 | 2016-07-25 | 57594 | 13944 | 21.2 | 1.1 | 0.94 | 45.9 |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: Updated radio light curves and spectrum (1.33-9 GHz) with CABB  
  > "Details of the ATCA CABB observations are given in Table [\[table:atca\]](#table:atca)." (2.2)
- Other facility **Spitzer**: IRAC light curves and IRS spectrum for warm dust  
  > "On 2008-07-07 (MJD 54654, AOR 26536704), the InfraRed Spectrograph (IRS) on *Spitzer* (cite: Houck2004) made cryogenic observations" (2.3)
- External data: AKARI infrared points and dust models of SN 1978K  
  > "The *AKARI* infrared points show SN 1978K on 2006 December 03–04." (4.1) [from Tanaka2012]
- External data: GLEAM 200 MHz peak brightness 94 mJy/beam  
  > "shows a source at the location of SN 1978K with a peak brightness of 94 mJy/beam at 200 MHz" (5 Conclusions) [from Hurley-Walker2017]

## Processing

### Calibration

- pipeline or manual: Complete calibration pipeline reprocessing  
  > "All the observations were reprocessed using the complete calibration pipeline in CASA version 4.7.2 (cite: casa)." (2.1)
- casa version: CASA 4.7.2  
  > "All the observations were reprocessed using the complete calibration pipeline in CASA version 4.7.2 (cite: casa)." (2.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 (B3), J0519-4546 (B4, B6), Ceres (B7)  
  > "J0334–4008 (Band 3), J0519-4546 (Bands 4 and 6), and Ceres (Band 7) were used as amplitude calibrators" (2.1)
- flux scale uncertainty: _not stated_
- self calibration: None  
  > "The observations were short, and the source was not bright enough to merit doing phase or amplitude self calibration." (2.1)

### Imaging

- task: TCLEAN, Briggs weighting  
  > "The images were cleaned using the task TCLEAN with a Briggs weighting and `robust=0.5`." (2.1)
- deconvolver: mtmfs, nterms=2  
  > "Multi-frequency synthesis with the mtmfs deconvolver was used when combining channels to make continuum images; $\rm{nterms}=2$ was used" (2.1)
- weighting robust: robust = 0.5  
  > "The images were cleaned using the task TCLEAN with a Briggs weighting and `robust=0.5`." (2.1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied on restored images  
  > "Primary beam corrections were applied on the restored images." (2.1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Modified Montes et al. (1997) radio model parameters extended from the 2014 ATCA fit  
  > "In Figure 2 of (cite: Ryder2016) we modeled the 2014 ATCA radio and millimeter observations out to 94 GHz using a modified version of the (cite: Montes1997) model." (3.1) [from Ryder2016; Montes1997]
- ATCA processing following ATCA User Guide Sec. 4.3  
  > "using procedures outlined in Sec. 4.3 of the ATCA User Guide" (2.2) [from ATCA User Guide]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, masks, clean threshold for ALMA
- Method of flux extraction (point-source fit vs peak) and flux uncertainty/absolute calibration error for ALMA
- Which channels were flagged as bad
- Fitting method, priors and uncertainties for the broken power law and Montes model
- How power-law decay indices and their errors were fit
- Exact Montes model parameter names (lost in table conversion)

## Analysis recipe

1. **Image ALMA continuum and measure flux densities**: Pipeline calibration, mtmfs tclean per SPW, pairs and whole band; point-like source flux  
  > "Thus all the good channels were combined to obtain the continuum fluxes in the four separate SPW." (2.1)
   - software: CASA, tclean
   - parameter: robust=0.5, nterms=2  
  > "The images were cleaned using the task TCLEAN with a Briggs weighting and `robust=0.5`." (2.1)
   - fitting: _not stated_
   - validation: Compared SPW, paired and whole-band fluxes for consistency  
  > "However, the magenta points show this can be done without any problems." (2.1)
2. **Measure ATCA fluxes**: Miriad calibration, robust 0.5 imaging, Gaussian point-source fit; 16 cm band split into four 512 MHz sub-bands  
  > "Fitting a Gaussian point source at the location of SN 1978K yielded the flux densities shown in Table [\[table:atca\]](#table:atca)" (2.2)
   - software: Miriad
   - fitting: _not stated_
   - validation: _not stated_
3. **Spitzer IRAC photometry and light curves**: Point source photometry on CBCD with APEX in MOPEX using PRF map; handbook correction factors  
  > "Point source photometry was performed on the Corrected Basic Calibrated Data (CBCD) generated by the pipeline using APEX in the MOPEX package (cite: mopex)." (2.3)
   - software: MOPEX APEX
   - fitting: _not stated_
   - validation: Nearby stars of similar brightness remained constant  
  > "The fluxes of other nearby stars of similar brightness were consistent with remaining constant over the decade" (2.3)
4. **Model radio-millimeter spectrum**: Compare modified Montes+1997 parameterized model with a broken power law GRB fireball cooling-break model with wind scaling  
  > "Figure [5](#figure:atcaalma) combines the radio and millimeter observations of SN 1978K, and shows model fits from two possible interpretations for the radio-millimeter spectrum." (3)
   - parameter: Radio decay t^-1.53 gives p=2.373; indices -0.687 below and -1.187 above the break  
  > "The fireball model then requires that the spectral indices be $\nu^{(1-p)/2} = \nu^{-0.687}$ below $\nu_{\rm c}$ and $\nu^{-p/2} = \nu^{-1.187}$ above it." (3.2)
   - assumption: Generic fireball formalism with wind scaling; ISM scaling rejected  
  > "However, we can still adopt the generic fireball formalism here." (3.2)
   - fitting: _not stated_
   - validation: Temporal decay and spectral indices independently agree with the fireball expectations  
  > "The fact that both the radio temporal decay and the spectral indices independently agree with the fireball expectations make this a promising interpretation." (3.2)
5. **Assess warm and cold dust**: Extrapolate synchrotron models back to AKARI epoch, compare with Tanaka+2012 dust models, fit IRAC decay  
  > "The model curves from Figure [5](#figure:atcaalma) have been extrapolated back to this time." (4.1)
   - assumption: ALMA/ATCA points extrapolated back assuming fireball evolution  
  > "The ALMA and ATCA data points from Figure [5](#figure:atcaalma) have been extrapolated back assuming the fireball evolution." (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: ALMA calibration pipeline and tclean imaging  
  > "All the observations were reprocessed using the complete calibration pipeline in CASA version 4.7.2 (cite: casa)." (2.1)
- **Miriad** : ATCA data processing  
  > "The data were processed using the Miriad package (cite: miriad)" (2.2)
- **MOPEX** : Spitzer IRAC point source photometry (APEX)  
  > "using APEX in the MOPEX package (cite: mopex)" (2.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 3 flux density (all 4 SPW, 103.5 GHz) | 1.412 | rms 0.025 mJy/beam | mJy | 1 | & All 4 & & 0.59 & 1.412 & 0.025\ |
| ALMA Band 4 flux density (145 GHz) | 0.855 | rms 0.015 mJy/beam | mJy | 1 | & All 4 & 145.0147 & 0.52 & 0.855 & 0.015\ |
| ALMA Band 6 flux density (233 GHz) | 0.525 | rms 0.026 mJy/beam | mJy | 1 | & All 4 & 233.0049 & 0.63 & 0.525 & 0.026\ |
| ALMA Band 7 flux density (343.5 GHz) | 0.458 | rms 0.030 mJy/beam | mJy | 1 | & All 4 & 343.5020 & 0.36 & 0.458 & 0.030 |
| Radio decay index | -1.53 | not stated | dimensionless | 2 | the non-thermal radio continuum continues to decay as $t^{-1.53}$ |
| Electron spectral index p (wind fireball) | 2.373 | not stated | dimensionless | 4 | this implies $p=2.373$ |
| Change in spectral index at break | ~0.5 | not stated | dimensionless | 4 | the change in the spectral index appears to be $\sim 0.5$ |
| IRAC 3.6/4.5 micron decay index | -2.45 | not stated | dimensionless | 3 | The $t^{-2.45}$ power law decay in both channels is much faster than we have found in the radio |

## Qualitative findings

- The ALMA spectrum steepens at millimeter frequencies; SN 1978K is point-like in all bands.  
  > "Our ALMA observations in 2016 show that the spectrum appears to be steeper at higher frequencies." (5 Conclusions)

## Claim tuples

- H: Can a single absorbed power law (Montes) or a broken power law fireball explain the radio-mm spectrum? | E: Fit models to ATCA and ALMA data | R: Both broadly fit; Montes needs chromatic variability; fireball indices follow from the radio decay | F: Fireball cooling-break model is a promising interpretation | **partially**
- H: Is the warm dust emission fading? | E: Spitzer IRAC light curves 2006-2018 | R: t^-2.45 decay in both channels | F: Warm dust is likely being destroyed | **supported**
- H: Is there cold dust emission in the ALMA data? | E: Compare Band 7 with synchrotron models | R: Band 7 fits Montes but lies a little above the fireball curve | F: Cold dust upturn possible only if the fireball model is right | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fireball with ISM scaling rejected: gives p=3.04 and indices steeper than observed  
  > "A GRB fireball model with an ISM scaling for the external medium does not explain the SN 1978K observations." (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Combining whole-band data is less robust owing to beam changes and interpolation  
  > "it might be considered a little less robust to combine all the data for the whole band" (2.1)
- Caveat (inferred, ours): No quantitative goodness-of-fit or model comparison between the two models
- Caveat (inferred, ours): Few spectral points; individual SPW errors large
- Caveat (inferred, ours): Dust conclusions depend on extrapolating synchrotron models back to 2006
- Caveat (inferred, ours): Absolute flux scale uncertainties not discussed

## Reproducibility

- Data public (paper): ALMA project code printed; ATCA and Spitzer program numbers given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00869.S (P.I. I. Smith)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Image/cell size and masks
- Missing: Model fitting procedure and uncertainties
- Missing: Full Montes parameter table (conversion garbled)
- Data volume (inferred): ~10-50 GB for ALMA raw data across four bands
- Score (inferred): 3/5, ALMA recipe mostly specified (CASA 4.7.2, robust 0.5, mtmfs) and fluxes tabulated, but model fitting details are missing.
- Rediscovery candidate: yes, Public ALMA data, simple point-source continuum fluxes in a table can be reproduced.

## Links

- Method: Montes1997 (Parameterized radio supernova model used)
- Method: Granot2014 (GRB afterglow spectral break theory)
- Companion: Ryder2016 (Earlier ATCA/VLBI SN 1978K study and radio model)
- Companion: Tanaka2012 (AKARI/Spitzer dust study of SN 1978K)
- Related: ATCA program C184
- Related: GLEAM

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
