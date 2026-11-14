# Passive galaxies in the early Universe: ALMA confirmation of z ∼ 3-5 candidates in the CANDELS GOODS-South field

`2019MNRAS.486..560S` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Santini, P. | arXiv: 1902.09548 | DOI: 10.1093/mnras/stz801

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Do ALMA archival continuum observations confirm the passive nature of z~3-5 passive galaxy candidates selected by SED fitting, i.e. rule out dusty star-forming contaminants?  
  > "ALMA data are used to verify the potential contamination from red, dusty but star–forming sources that could enter the sample due to similar optical–nearIR colours." (abstract)
- Target **30 passive candidates in CANDELS GOODS-South (26 with ALMA data)**: coordinates _not stated_; z/distance z~3-5 (photometric redshifts, e.g. 3.06-4.74 in Table)  
  > "found public observations for 26 out of 30 sources, belonging to a number of different programs" (3 ALMA observations and data analysis); distance from photometric redshift from SED fitting (M18)  
  > "found public observations for 26 out of 30 sources, belonging to a number of different programs" (3 ALMA observations and data analysis)

## Data provenance

- ALMA projects: 2012.1.00173.S, 2012.1.00869.S, 2013.1.00718.S, 2013.1.01292.S, 2015.1.00098.S, 2015.1.00543.S, 2015.1.00664.S, 2015.1.00870.S, 2015.1.01074.S, 2015.1.01495.S
- bands: Band 6 and Band 7  
  > "The observations have been carried out in Band 6 and Band 7, with different sensitivities, setups and configurations." (3 ALMA observations and data analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: >0.6 arcsec  
  > "producing images with spatial resolution $>0.6$$''$ (see Table [1](#tab:list_programs))" (3 ALMA observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: public archival observations from several programs  
  > "found public observations for 26 out of 30 sources, belonging to a number of different programs" (3 ALMA observations and data analysis)
- Other facility **Herschel**: FIR detections for 2 of 30 candidates, from M18  
  > "found detection for 2 out of 30 candidates, potentially caused by hot dust emission from an AGN hosted in these two galaxies" (1 Introduction)
- External data: Candidate sample, redshifts, stellar masses and SED-fit star-forming solutions  
  > "We briefly summarize here the strategy pursued in M18 to select candidate passive galaxies in the CANDELS GOODS-S field by means of SED fitting." (2 Candidates selection) [from Merlin et al. 2018 (cite: merlin18)]
- External data: Observed star-forming Main Sequence at the same redshifts from HST Frontier Fields  
  > "the observed (i.e., not corrected for the Eddington bias) MS of star–forming galaxies at the same redshifts as inferred from the HST Frontier Fields data by (cite: santini17)" (5.2 Validation of the whole population) [from (cite: santini17)]
- External data: Far-IR SED templates (M10, P08, E11, CE01, DH02, S18)  
  > "As reference model we used the average SED of (cite: michalowski10a) (M10), based on a sample of 76 SMGs at $0.01<z<3.6$ fitted with the GRASIL (cite: silva98) model." (4 ALMA predictions on the SFR) [from michalowski10a, pope08, elbaz11, ce01, dh02, schreiber18]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA using scripts provided by the ALMA project  
  > "Observations were calibrated with CASA (cite: mcmullin07) using scripts provided by the ALMA project." (3 ALMA observations and data analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, multi-frequency synthesis  
  > "Imaging was then performed using the multi-frequency synthesis algorithm implemented within the CASA task *CLEAN*." (3 ALMA observations and data analysis)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used "natural" weightings and *uv*-tapers when needed" (3 ALMA observations and data analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: fluxes read from primary-beam-corrected image  
  > "the flux of each candidate corresponds simply to the pixel value at its position in the primary beam-corrected ALMA image" (3 ALMA observations and data analysis)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Candidate selection by top-hat SFH SED fitting, P(chi2) criteria  
  > "We briefly summarize here the strategy pursued in M18 to select candidate passive galaxies in the CANDELS GOODS-S field by means of SED fitting." (2 Candidates selection) [from M18 (cite: merlin18)]
- Choice of >0.6 arcsec resolution and point-source assumption  
  > "This resolution was chosen following results from (cite: franco18)" (3 ALMA observations and data analysis) [from (cite: franco18)]
- SFR calibration from L_IR (3-1100 micron), converted to Salpeter IMF  
  > "adopting the calibration of (cite: kennicutt12), adjusted to a Salpeter IMF using their conversion factor" (4 ALMA predictions on the SFR) [from (cite: kennicutt12)]

### Not stated but needed to reproduce (our reading)

- Which ALMA products or scripts were used and the CASA version
- Clean parameters (threshold, niter, cell, image size, taper values per program)
- Treatment of continuum channel selection and line contamination
- Flux-scale uncertainty
- Source coordinates and catalogue from M18
- Exact redshift-dependent conversion from flux to L_IR for each template (normalisation, CMB correction)
- Details of stacking in the image plane vs flux-averaging
- Dust-temperature/IR8 recipes for S18 library

## Analysis recipe

1. **Find and image archival ALMA data**: Archive search at candidate positions; calibrate with ALMA scripts; image with CLEAN, natural weighting, tapering where needed  
  > "We used "natural" weightings and *uv*-tapers when needed, producing images with spatial resolution $>0.6$$''$" (3 ALMA observations and data analysis)
   - software: CASA
   - assumption: All sources are point-like  
  > "we could securely assume that all were point-like sources in our ALMA images." (3 ALMA observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes and noise**: Pixel value at candidate position in PB-corrected map; error as std of pixels with similar PB correction (+/-10%), excluding one FWHM around source, 3 sigma clipping  
  > "The associated flux error was measured by taking the standard deviation of all pixels in the map with similar coverage" (3 ALMA observations and data analysis)
   - fitting: _not stated_
   - validation: Number of 1-2 sigma detections consistent with normal noise distribution  
  > "the number of 1 and 2$\sigma$ detections is consistent with a normal distribution of the signal-to-noise ratio" (3 ALMA observations and data analysis)
3. **Combine and stack**: Weighted average of fluxes from different programs in same band; stack all sources by band and redshift bin (3<z<4, 4<z<5) and undetected only  
  > "we have stacked the inferred flux densities by averaging the fluxes measured from different programs weighting them with the associated errors" (3 ALMA observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert flux to SFR**: Scale far-IR templates to flux, get L_IR(3-1100 micron), apply Kennicutt & Evans SFR calibration; 1 sigma upper limits (3 sigma for individual validation)  
  > "The SFR has been computed from the total infrared luminosity between 3 and 1100 $\mu$m adopting the calibration of (cite: kennicutt12)" (4 ALMA predictions on the SFR)
   - parameter: Reference template M10; also P08, E11 MS/SB, CE01, DH02, S18 (R_SB=1, 4)  
  > "In the following we will refer to M10 as our reference model" (4 ALMA predictions on the SFR)
   - assumption: Old stellar heating neglected, so SFRs are conservative upper values  
  > "The true SFRs are therefore likely to be lower than those inferred by us" (4 ALMA predictions on the SFR)
   - assumption: Lambda-CDM H0=70, Om=0.3, OL=0.7; Salpeter IMF  
  > "we adopt the $\Lambda$-CDM concordance cosmological model (H$_0$=70 km/s/Mpc, $\Omega_M$=$0.3$ and $\Omega_{\Lambda}$=0.7)" (1 Introduction)
   - fitting: _not stated_
   - validation: Comparison across templates  
  > "The application of different models yields a range of resulting SFRs" (4 ALMA predictions on the SFR)
5. **Validate individually and statistically**: Compare ALMA SFR limits with SED-fit star-forming solutions (P>5%) at z 0-6; compare with star-forming Main Sequence at given stellar mass  
  > "We apply a criterion based on the requirement that all the star–forming solutions with $P$($\chi^2_{SF}$)\>5% are above the ALMA predictions." (5.1 Validation of robust individual candidates)
   - fitting: _not stated_
   - validation: Two tests give consistent results  
  > "the two analyses yield consistent results" (5.3 Final considerations)

## Software

- **CASA** : Calibration and imaging (CLEAN)  
  > "Observations were calibrated with CASA (cite: mcmullin07) using scripts provided by the ALMA project." (3 ALMA observations and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources with ALMA data | 26 of 30 | not stated | sources | 1 | found public observations for 26 out of 30 sources |
| Individually confirmed passive candidates | 9 of 26 (35%) | not stated | sources | 5 | We find that in 9 out of the total sample of 26 candidates (i.e., 35%) |
| Candidates at least 1 sigma below MS | 13 | not stated | sources | 5 | place 13 (6) candidates, 6 (4) of which belonging to the $S_1$ sample, at least 1$\sigma$ (3$\sigma$) below the MS |
| Stacked Band 6 SFR, 3<z<5 | 7.4 | 3.8 | Msun/yr | 4 | /  / 3.44 / 10.31$_{-0.11}^{+0.09}$ / 6 / Stack all Band 6 sources at 3\<z\<5 / 0.02 / 0.01 / 7.4$\pm$3.8 /  / |
| Typical SFR constraint with M10 | below 40-50 | not stated | Msun/yr | 4 | the ALMA observations constrain the SFR of our objects to be typically below 40-50 $M_\odot$/$yr$ |

## Qualitative findings

- No individual source detected above 3 sigma, nor in stacks  
  > "we found no high-confidence (i.e., $>$3$\sigma$) detection on ALMA images for any of the candidates." (3 ALMA observations and data analysis)

## Claim tuples

- H: The SED-selected candidates are truly passive rather than dusty star-forming | E: Compare ALMA-based SFR limits with star-forming SED solutions | R: 9 of 26 have all plausible SF solutions excluded at 3 sigma | F: These 9 are confirmed with high confidence | **supported**
- H: The sample is passive in a statistical sense | E: Stacking and Main Sequence comparison | R: At least half lie at least 1 sigma below MS; stacks undetected | F: Classification correct for at least half statistically | **partially**

## Reasoning

- Why this data: Herschel too shallow; ALMA is the only tool to validate passive solutions  
  > "Deep ALMA observations therefore provide, at present, the only tool for validating the passive solutions for our candidates." (2 Candidates selection)
- Why this method: _not stated_
- Alternative: S18 library rejected as likely inappropriate and overestimating SFR  
  > "we believe that the S18 library is likely inappropriate and overestimates the SFR for our candidates" (4 ALMA predictions on the SFR)
- How they decided it was enough: _not stated_
- Limitation (authors): Archival ALMA data not deep enough to confirm most candidates individually; FIR template choice spans nearly a decade in SFR  
  > "currently available ALMA archive observations are not deep enough to individually confirm most of our candidates with high confidence" (6 Summary and conclusions)
- Caveat (inferred, ours): Heterogeneous archival data with varied tapers and no stated clean details
- Caveat (inferred, ours): Results depend strongly on assumed dust SED template and temperature
- Caveat (inferred, ours): Point-source assumption at >0.6 arcsec
- Caveat (inferred, ours): Arbitrary 5% threshold for plausible SF solutions

## Reproducibility

- Data public (paper): Public archival ALMA observations  
  > "found public observations for 26 out of 30 sources" (3 ALMA observations and data analysis)
- Products in archive: _not stated_
- Missing: M18 candidate catalogue and SED-fit probabilities
- Missing: Source coordinates
- Missing: Imaging parameters and CASA version
- Missing: Exact template normalisation procedure
- Data volume (inferred): ~100-500 GB raw for 10 programs; much less if using archive products
- Score (inferred): 3/5, Data public and recipe outlined, but imaging parameters, catalogue and template handling are not fully specified.
- Rediscovery candidate: no, Depends on M18 catalogue and unspecified imaging/template details.

## Links

- Method: Merlin et al. 2018 (cite: merlin18) (Candidate selection method and sample)
- Method: (cite: franco18) (Justification for resolution and point-source assumption)
- Companion: Merlin et al. 2018 (cite: merlin18) (Original selection of the 30 candidates)
- Related: CANDELS GOODS-South
- Related: GOODS-S ALMA 1.1 mm survey (Franco et al. 2018)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 35,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
